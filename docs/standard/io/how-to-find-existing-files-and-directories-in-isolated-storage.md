---
title: 'Cómo: Buscar archivos y directorios existentes en almacenamiento aislado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
ms.openlocfilehash: ebd2ae6684e7b3390b29aeebeb2552b4616a69f3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830732"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Cómo: Buscar archivos y directorios existentes en almacenamiento aislado

Para buscar un directorio en el almacenamiento aislado, use el método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType>. Este método adopta una cadena que representa un patrón de búsqueda. Puede usar caracteres comodín de un solo carácter (?) y de varios caracteres (\*) en el patrón de búsqueda, pero los caracteres comodín deben aparecer en la parte final del nombre. Por ejemplo, `directory1/*ect*` es una cadena de búsqueda válida, pero `*ect*/directory2` no lo es.  
  
 Para buscar un archivo, use el método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType>. La restricción de caracteres comodín en cadenas de búsqueda que se aplica a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> también se aplica a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.  
  
 Ninguno de estos métodos es recursivo; la clase <xref:System.IO.IsolatedStorage.IsolatedStorageFile> no proporciona ningún método para enumerar todos los directorios o archivos en el almacén. Sin embargo, los métodos recursivos se muestran en el ejemplo de código siguiente.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo crear archivos y directorios en un almacén aislado. En primer lugar, un almacén aislado para usuarios, dominios y ensamblados se recupera y se coloca en la variable `isoStore`. El método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> se usa para configurar algunos directorios distintos y el constructor <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> crea algunos archivos en estos directorios. El código pasa por los resultados del método `GetAllDirectories`. Este método usa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> para buscar todos los nombres de directorio en el directorio actual. Estos nombres se almacenan en una matriz y, a continuación, `GetAllDirectories` se llama a sí mismo, pasando cada directorio que ha encontrado. Como resultado, se devuelven todos los nombres de directorio en una matriz. A continuación, el código llama al método `GetAllFiles`. Este método llama a `GetAllDirectories` para averiguar los nombres de todos los directorios y, a continuación, comprueba cada directorio de archivos mediante el uso del método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>. El resultado se devuelve en una matriz para su presentación.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Vea también

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Almacenamiento aislado](isolated-storage.md)

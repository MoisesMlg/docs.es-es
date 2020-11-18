---
title: Firmas criptográficas
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET], signatures
- security [.NET], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
ms.openlocfilehash: 453e9d887012826da3f64d199e15a05fd0661191
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831135"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="eec85-102">Firmas criptográficas</span><span class="sxs-lookup"><span data-stu-id="eec85-102">Cryptographic Signatures</span></span>

<span data-ttu-id="eec85-103">Las firmas digitales criptográficas usan algoritmos de clave pública para mantener la integridad de los datos.</span><span class="sxs-lookup"><span data-stu-id="eec85-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="eec85-104">Si firma datos con una firma digital, otra persona puede comprobar la firma y confirmar que los datos provienen de usted y que no se han modificado después de ser firmados.</span><span class="sxs-lookup"><span data-stu-id="eec85-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="eec85-105">Para más información sobre firmas digitales, vea [Cryptographic Services](cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="eec85-105">For more information about digital signatures, see [Cryptographic Services](cryptographic-services.md).</span></span>

<span data-ttu-id="eec85-106">En este tema se explica cómo generar y comprobar firmas digitales mediante clases en el espacio de nombres <xref:System.Security.Cryptography> .</span><span class="sxs-lookup"><span data-stu-id="eec85-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="eec85-107">Generación de firmas</span><span class="sxs-lookup"><span data-stu-id="eec85-107">Generating Signatures</span></span>

<span data-ttu-id="eec85-108">Las firmas digitales suelen aplicarse a valores hash que representan datos de mayor volumen.</span><span class="sxs-lookup"><span data-stu-id="eec85-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="eec85-109">En el siguiente ejemplo se aplica una firma digital a un valor hash.</span><span class="sxs-lookup"><span data-stu-id="eec85-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="eec85-110">Primero se crea una instancia de la clase <xref:System.Security.Cryptography.RSA> para generar un par de claves pública y privada.</span><span class="sxs-lookup"><span data-stu-id="eec85-110">First, a new instance of the <xref:System.Security.Cryptography.RSA> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="eec85-111">Después se pasa <xref:System.Security.Cryptography.RSA> a una nueva instancia de la clase <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> .</span><span class="sxs-lookup"><span data-stu-id="eec85-111">Next, the <xref:System.Security.Cryptography.RSA> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="eec85-112">Con esto se transfiere la clave privada a <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, que es el que realmente realiza la firma digital.</span><span class="sxs-lookup"><span data-stu-id="eec85-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="eec85-113">Antes de poder firmar el código hash, hay que especificar el algoritmo hash que se usará.</span><span class="sxs-lookup"><span data-stu-id="eec85-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="eec85-114">En este ejemplo se usa el algoritmo SHA1.</span><span class="sxs-lookup"><span data-stu-id="eec85-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="eec85-115">Por último, se llama al método <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> para realizar el proceso de firma.</span><span class="sxs-lookup"><span data-stu-id="eec85-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="eec85-116">Debido a problemas de colisión con SHA1, se recomienda SHA256 o superior.</span><span class="sxs-lookup"><span data-stu-id="eec85-116">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As RSA = RSA.Create()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSA instance to transfer the private key.
        Dim rsaFormatter As New RSAPKCS1SignatureFormatter(rsa)

        'Set the hash algorithm to SHA1.
        rsaFormatter.SetHashAlgorithm("SHA1")

        'Create a signature for hashValue and assign it to
        'signedHashValue.
        signedHashValue = rsaFormatter.CreateSignature(hashValue)
    End Sub
End Module
```

```csharp
using System;
using System.Security.Cryptography;

class Class1
{
   static void Main()
   {
      //The hash value to sign.
      byte[] hashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};

      //The value to hold the signed value.
      byte[] signedHashValue;

      //Generate a public/private key pair.
      RSA rsa = RSA.Create();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSA instance to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

## <a name="verifying-signatures"></a><span data-ttu-id="eec85-117">Comprobación de firmas</span><span class="sxs-lookup"><span data-stu-id="eec85-117">Verifying Signatures</span></span>

<span data-ttu-id="eec85-118">Para comprobar que alguien en concreto firmó los datos, es necesaria la información siguiente:</span><span class="sxs-lookup"><span data-stu-id="eec85-118">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="eec85-119">La clave pública del firmante de los datos.</span><span class="sxs-lookup"><span data-stu-id="eec85-119">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="eec85-120">La firma digital.</span><span class="sxs-lookup"><span data-stu-id="eec85-120">The digital signature.</span></span>

- <span data-ttu-id="eec85-121">Los datos que se firmaron.</span><span class="sxs-lookup"><span data-stu-id="eec85-121">The data that was signed.</span></span>

- <span data-ttu-id="eec85-122">El algoritmo de hash usado por el firmante.</span><span class="sxs-lookup"><span data-stu-id="eec85-122">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="eec85-123">Para comprobar una firma realizada por la clase <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> , use la clase <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> .</span><span class="sxs-lookup"><span data-stu-id="eec85-123">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="eec85-124">A la clase <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> debe proporcionársele la clave pública del firmante.</span><span class="sxs-lookup"><span data-stu-id="eec85-124">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="eec85-125">Para RSA, necesitará los valores del módulo y el exponente para especificar la clave pública.</span><span class="sxs-lookup"><span data-stu-id="eec85-125">For RSA, you will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="eec85-126">(La entidad que generó el par de claves pública y privada debe proporcionar estos valores). En primer lugar <xref:System.Security.Cryptography.RSA> , cree un objeto que contenga la clave pública que comprobará la firma y, a continuación, inicialice una <xref:System.Security.Cryptography.RSAParameters> estructura a los valores de módulo y exponente que especifican la clave pública.</span><span class="sxs-lookup"><span data-stu-id="eec85-126">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSA> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="eec85-127">En el código siguiente se muestra la creación de una estructura <xref:System.Security.Cryptography.RSAParameters> .</span><span class="sxs-lookup"><span data-stu-id="eec85-127">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="eec85-128">La propiedad `Modulus` se establece en el valor de una matriz de bytes denominada `modulusData` y la propiedad `Exponent` se establece en el valor de una matriz de bytes denominada `exponentData`.</span><span class="sxs-lookup"><span data-stu-id="eec85-128">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

```vb
Dim rsaKeyInfo As RSAParameters
rsaKeyInfo.Modulus = modulusData
rsaKeyInfo.Exponent = exponentData
```

```csharp
RSAParameters rsaKeyInfo;
rsaKeyInfo.Modulus = modulusData;
rsaKeyInfo.Exponent = exponentData;
```

<span data-ttu-id="eec85-129">Una vez creado el <xref:System.Security.Cryptography.RSAParameters> objeto, puede inicializar una nueva instancia de la <xref:System.Security.Cryptography.RSA> clase de implementación con los valores especificados en <xref:System.Security.Cryptography.RSAParameters> .</span><span class="sxs-lookup"><span data-stu-id="eec85-129">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSA> implementation class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="eec85-130"><xref:System.Security.Cryptography.RSA>A su vez, la instancia se pasa al constructor de un <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> para transferir la clave.</span><span class="sxs-lookup"><span data-stu-id="eec85-130">The <xref:System.Security.Cryptography.RSA> instance is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="eec85-131">El ejemplo siguiente ilustra este proceso.</span><span class="sxs-lookup"><span data-stu-id="eec85-131">The following example illustrates this process.</span></span> <span data-ttu-id="eec85-132">En este ejemplo, `hashValue` y `signedHashValue` son matrices de bytes que proporciona una parte remota.</span><span class="sxs-lookup"><span data-stu-id="eec85-132">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="eec85-133">La parte remota firmó el `hashValue` mediante el algoritmo SHA1, produciendo así la firma digital `signedHashValue`.</span><span class="sxs-lookup"><span data-stu-id="eec85-133">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="eec85-134">El <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> método comprueba que la firma digital es válida y que se usó para firmar el `hashValue` .</span><span class="sxs-lookup"><span data-stu-id="eec85-134">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

<span data-ttu-id="eec85-135">Debido a problemas de colisión con SHA1, se recomienda SHA256 o superior.</span><span class="sxs-lookup"><span data-stu-id="eec85-135">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>  <span data-ttu-id="eec85-136">Sin embargo, si se utilizó SHA1 para crear la firma, debe utilizar SHA1 para comprobar la firma.</span><span class="sxs-lookup"><span data-stu-id="eec85-136">However, if SHA1 was used to create the signature, you have to use SHA1 to verify the signature.</span></span>

```vb
Dim rsa As RSA = RSA.Create()
rsa.ImportParameters(rsaKeyInfo)
Dim rsaDeformatter As New RSAPKCS1SignatureDeformatter(rsa)
rsaDeformatter.SetHashAlgorithm("SHA1")
If rsaDeformatter.VerifySignature(hashValue, signedHashValue) Then
   Console.WriteLine("The signature is valid.")
Else
   Console.WriteLine("The signature is not valid.")
End If
```

```csharp
RSA rsa = RSA.Create();
rsa.ImportParameters(rsaKeyInfo);
RSAPKCS1SignatureDeformatter rsaDeformatter = new RSAPKCS1SignatureDeformatter(rsa);
rsaDeformatter.SetHashAlgorithm("SHA1");
if(rsaDeformatter.VerifySignature(hashValue, signedHashValue))
{
   Console.WriteLine("The signature is valid.");
}
else
{
   Console.WriteLine("The signature is not valid.");
}
```

<span data-ttu-id="eec85-137">Este fragmento de código mostrará "`The signature is valid`" si la firma es válida y "`The signature is not valid`" si no lo es.</span><span class="sxs-lookup"><span data-stu-id="eec85-137">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="eec85-138">Vea también</span><span class="sxs-lookup"><span data-stu-id="eec85-138">See also</span></span>

- [<span data-ttu-id="eec85-139">servicios criptográficos</span><span class="sxs-lookup"><span data-stu-id="eec85-139">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="eec85-140">Modelo de criptografía</span><span class="sxs-lookup"><span data-stu-id="eec85-140">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="eec85-141">Criptografía multiplataforma</span><span class="sxs-lookup"><span data-stu-id="eec85-141">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="eec85-142">ASP.NET Core protección de datos</span><span class="sxs-lookup"><span data-stu-id="eec85-142">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)

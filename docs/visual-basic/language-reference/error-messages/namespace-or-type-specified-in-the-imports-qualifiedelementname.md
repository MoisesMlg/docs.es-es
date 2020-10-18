---
title: El espacio de nombres o tipo especificado en las importaciones '<qualifiedelementname>' no contiene miembros públicos o no se encuentra
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 284a8c71fee8835f78ca5435932819fded1b1f30
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160137"
---
# <a name="bc40056-namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="122d2-102">BC40056: el espacio de nombres o tipo especificado en las importaciones ' \<qualifiedelementname> ' no contiene ningún miembro público o no se encuentra</span><span class="sxs-lookup"><span data-stu-id="122d2-102">BC40056: Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="122d2-103">El espacio de nombres o tipo especificado en las importaciones ' \<qualifiedelementname> ' no contiene ningún miembro público o no se encuentra.</span><span class="sxs-lookup"><span data-stu-id="122d2-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="122d2-104">Asegúrese de que el espacio de nombres o el tipo estén definidos y que contenga al menos un miembro público.</span><span class="sxs-lookup"><span data-stu-id="122d2-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="122d2-105">Asegúrese de que el nombre de alias no contenga otros alias.</span><span class="sxs-lookup"><span data-stu-id="122d2-105">Make sure the alias name doesn't contain other aliases.</span></span>

<span data-ttu-id="122d2-106">Una `Imports` instrucción especifica un elemento contenedor que no se puede encontrar o no define ningún `Public` miembro.</span><span class="sxs-lookup"><span data-stu-id="122d2-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

<span data-ttu-id="122d2-107">Un *elemento contenedor* puede ser un espacio de nombres, una clase, una estructura, un módulo, una interfaz o una enumeración.</span><span class="sxs-lookup"><span data-stu-id="122d2-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="122d2-108">El elemento contenedor contiene miembros, como variables, procedimientos u otros elementos contenedores.</span><span class="sxs-lookup"><span data-stu-id="122d2-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

<span data-ttu-id="122d2-109">El propósito de la importación es permitir que el código tenga acceso a los miembros de espacio de nombres o de tipo sin tener que calificarlos.</span><span class="sxs-lookup"><span data-stu-id="122d2-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="122d2-110">Es posible que el proyecto también tenga que agregar una referencia al espacio de nombres o al tipo.</span><span class="sxs-lookup"><span data-stu-id="122d2-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="122d2-111">Para obtener más información, vea "importar elementos contenedores" en [referencias a elementos declarados](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="122d2-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="122d2-112">Si el compilador no encuentra el elemento contenedor especificado, no puede resolver las referencias que lo usan.</span><span class="sxs-lookup"><span data-stu-id="122d2-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="122d2-113">Si encuentra el elemento pero el elemento no expone ningún `Public` miembro, no se puede realizar ninguna referencia correctamente.</span><span class="sxs-lookup"><span data-stu-id="122d2-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="122d2-114">En cualquier caso, no tiene sentido importar el elemento.</span><span class="sxs-lookup"><span data-stu-id="122d2-114">In either case it is meaningless to import the element.</span></span>

<span data-ttu-id="122d2-115">Tenga en cuenta que si importa un elemento contenedor y le asigna un alias de importación, no puede usar ese alias de importación para importar otro elemento.</span><span class="sxs-lookup"><span data-stu-id="122d2-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="122d2-116">El código siguiente genera un error del compilador.</span><span class="sxs-lookup"><span data-stu-id="122d2-116">The following code generates a compiler error.</span></span>

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

<span data-ttu-id="122d2-117">**Identificador de error:** BC40056</span><span class="sxs-lookup"><span data-stu-id="122d2-117">**Error ID:** BC40056</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="122d2-118">Para corregir este error</span><span class="sxs-lookup"><span data-stu-id="122d2-118">To correct this error</span></span>

1. <span data-ttu-id="122d2-119">Compruebe que el elemento contenedor es accesible desde el proyecto.</span><span class="sxs-lookup"><span data-stu-id="122d2-119">Verify that the containing element is accessible from your project.</span></span>

2. <span data-ttu-id="122d2-120">Compruebe que la especificación del elemento contenedor no incluye ningún alias de importación de otra importación.</span><span class="sxs-lookup"><span data-stu-id="122d2-120">Verify that the specification of the containing element does not include any import alias from another import.</span></span>

3. <span data-ttu-id="122d2-121">Compruebe que el elemento contenedor expone al menos un `Public` miembro.</span><span class="sxs-lookup"><span data-stu-id="122d2-121">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="122d2-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="122d2-122">See also</span></span>

- [<span data-ttu-id="122d2-123">Instrucción Imports (Tipo y espacio de nombres de .NET)</span><span class="sxs-lookup"><span data-stu-id="122d2-123">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="122d2-124">Namespace (Instrucción)</span><span class="sxs-lookup"><span data-stu-id="122d2-124">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="122d2-125">Público</span><span class="sxs-lookup"><span data-stu-id="122d2-125">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="122d2-126">Espacios de nombres en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="122d2-126">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="122d2-127">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="122d2-127">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

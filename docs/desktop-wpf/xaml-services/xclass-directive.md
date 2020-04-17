---
title: x:Class (Directiva)
ms.date: 03/30/2017
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
ms.openlocfilehash: f589fa70c2ee1c56544fa0f0152990478aa3761f
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2020
ms.locfileid: "81433281"
---
# <a name="xclass-directive"></a><span data-ttu-id="904a8-102">x:Class (Directiva)</span><span class="sxs-lookup"><span data-stu-id="904a8-102">x:Class Directive</span></span>
<span data-ttu-id="904a8-103">Configura la compilación de marcado XAML para unir clases parciales entre el marcado y el código subyacente.</span><span class="sxs-lookup"><span data-stu-id="904a8-103">Configures XAML markup compilation to join partial classes between markup and code-behind.</span></span> <span data-ttu-id="904a8-104">La clase parcial de código se define en un archivo de código independiente en un lenguaje de especificación de lenguaje común (CLS), mientras que la clase parcial de marcado se crea normalmente mediante la generación de código durante la compilación XAML.</span><span class="sxs-lookup"><span data-stu-id="904a8-104">The code partial class is defined in a separate code file in a Common Language Specification (CLS) language, whereas the markup partial class is typically created by code generation during XAML compilation.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="904a8-105">Uso de atributos XAML</span><span class="sxs-lookup"><span data-stu-id="904a8-105">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname"...>
  ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="904a8-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="904a8-106">XAML Values</span></span>

|||
|-|-|
|`namespace`|<span data-ttu-id="904a8-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="904a8-107">Optional.</span></span> <span data-ttu-id="904a8-108">Especifica un espacio de nombres CLR `classname`que contiene la clase parcial identificada por .</span><span class="sxs-lookup"><span data-stu-id="904a8-108">Specifies a CLR namespace that contains the partial class identified by `classname`.</span></span> <span data-ttu-id="904a8-109">Si `namespace` se especifica, un punto (.) separa `namespace` y `classname`.</span><span class="sxs-lookup"><span data-stu-id="904a8-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span> <span data-ttu-id="904a8-110">Vea la sección Comentarios.</span><span class="sxs-lookup"><span data-stu-id="904a8-110">See Remarks.</span></span>|
|`classname`|<span data-ttu-id="904a8-111">Necesario.</span><span class="sxs-lookup"><span data-stu-id="904a8-111">Required.</span></span> <span data-ttu-id="904a8-112">Especifica el nombre CLR de la clase parcial que conecta el XAML cargado y el código subyacente para ese XAML.</span><span class="sxs-lookup"><span data-stu-id="904a8-112">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="904a8-113">Dependencias</span><span class="sxs-lookup"><span data-stu-id="904a8-113">Dependencies</span></span>

<span data-ttu-id="904a8-114">`x:Class`solo se puede especificar en el elemento raíz de una producción XAML.</span><span class="sxs-lookup"><span data-stu-id="904a8-114">`x:Class` can only be specified on the root element of a XAML production.</span></span> <span data-ttu-id="904a8-115">`x:Class`no es válido en ningún objeto que tenga un elemento primario en la producción XAML.</span><span class="sxs-lookup"><span data-stu-id="904a8-115">`x:Class` is invalid on any object that has a parent in the XAML production.</span></span> <span data-ttu-id="904a8-116">Para obtener más información, consulte [ \[MS-XAML\] Sección 4.3.1.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="904a8-116">For more information, see [\[MS-XAML\] Section 4.3.1.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="remarks"></a><span data-ttu-id="904a8-117">Observaciones</span><span class="sxs-lookup"><span data-stu-id="904a8-117">Remarks</span></span>

<span data-ttu-id="904a8-118">El `namespace` valor puede contener puntos adicionales para organizar espacios de nombres relacionados en jerarquías de nombres, que es una técnica común en la programación de .NET.</span><span class="sxs-lookup"><span data-stu-id="904a8-118">The `namespace` value may contain additional dots to organize related namespaces into name hierarchies, which is a common technique in .NET programming.</span></span> <span data-ttu-id="904a8-119">Solo el último punto `x:Class` de una cadena `namespace` de `classname.` valores se interpreta `x:Class` para separar y la clase que se utiliza como no puede ser una clase anidada.</span><span class="sxs-lookup"><span data-stu-id="904a8-119">Only the last dot in a string of `x:Class` values is interpreted to separate `namespace` and `classname.` The class that is used as `x:Class` cannot be a nested class.</span></span> <span data-ttu-id="904a8-120">Las clases anidadas no están permitidas `x:Class` porque determinar el significado de los puntos para las cadenas es ambiguo si se permiten las clases anidadas.</span><span class="sxs-lookup"><span data-stu-id="904a8-120">Nested classes are not allowed because determining the meaning of dots for `x:Class` strings is ambiguous if nested classes are permitted.</span></span>

<span data-ttu-id="904a8-121">En los modelos `x:Class`de `x:Class` programación existentes que usan , es opcional en el sentido de que es totalmente válido tener una página XAML que no tiene código subyacente.</span><span class="sxs-lookup"><span data-stu-id="904a8-121">In existing programming models that use `x:Class`, `x:Class` is optional in the sense that it is entirely valid to have a XAML page that has no code-behind.</span></span> <span data-ttu-id="904a8-122">Sin embargo, esa capacidad interactúa con las acciones de compilación implementadas por marcos que usan XAML.</span><span class="sxs-lookup"><span data-stu-id="904a8-122">However, that capability interacts with the build actions as implemented by frameworks that use XAML.</span></span> <span data-ttu-id="904a8-123">`x:Class`la funcionalidad también está influenciada por los roles que varias clasificaciones de contenido especificado por XAML tienen en un modelo de aplicación y en las acciones de compilación correspondientes.</span><span class="sxs-lookup"><span data-stu-id="904a8-123">`x:Class` capability is also influenced by the roles that various classifications of XAML-specified content have in an application model and in the corresponding build actions.</span></span> <span data-ttu-id="904a8-124">Si el XAML declara valores de atributo de control de eventos o crea instancias de elementos `x:Class` personalizados donde las clases de definición están en la clase de código subyacente, debe proporcionar la referencia de directiva (o [x:Subclass](xsubclass-directive.md)) a la clase adecuada para el código subyacente.</span><span class="sxs-lookup"><span data-stu-id="904a8-124">If your XAML declares event-handling attribute values or instantiates custom elements where the defining classes are in the code-behind class, you have to provide the `x:Class` directive reference (or [x:Subclass](xsubclass-directive.md)) to the appropriate class for code-behind.</span></span>

<span data-ttu-id="904a8-125">El valor `x:Class` de la directiva debe ser una cadena que especifique el nombre completo <xref:System.Type.FullName%2A?displayProperty=nameWithType>de una clase pero sin ninguna información de ensamblado (equivalente a la ).</span><span class="sxs-lookup"><span data-stu-id="904a8-125">The value of the `x:Class` directive must be a string that specifies the fully qualified name of a class but without any assembly information (equivalent to the <xref:System.Type.FullName%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="904a8-126">Para aplicaciones sencillas, puede omitir la información del espacio de nombres CLR si el código subyacente también está estructurado de esa manera (la definición de código comienza en el nivel de clase).</span><span class="sxs-lookup"><span data-stu-id="904a8-126">For simple applications, you can omit CLR namespace information if the code-behind is also structured in that manner (code definition starts at the class level).</span></span>

<span data-ttu-id="904a8-127">El archivo de código subyacente para una definición de página o aplicación debe estar dentro de un archivo de código que se incluye como parte del proyecto que genera una aplicación compilada e implica la compilación de marcado.</span><span class="sxs-lookup"><span data-stu-id="904a8-127">The code-behind file for a page or application definition must be within a code file that is included as part of the project that produces a compiled application and involves markup compilation.</span></span> <span data-ttu-id="904a8-128">Debe seguir las reglas de nombre para las clases CLR.</span><span class="sxs-lookup"><span data-stu-id="904a8-128">You must follow name rules for CLR classes.</span></span> <span data-ttu-id="904a8-129">Para obtener más información, consulte [Directrices](../../../api/index.md)de diseño de marco .</span><span class="sxs-lookup"><span data-stu-id="904a8-129">For more information, see [Framework Design Guidelines](../../../api/index.md).</span></span> <span data-ttu-id="904a8-130">De forma predeterminada, la clase `public`de código subyacente debe ser ; sin embargo, puede definirlo en un nivel de acceso diferente mediante la [directiva x:ClassModifier](xclassmodifier-directive.md).</span><span class="sxs-lookup"><span data-stu-id="904a8-130">By default, the code-behind class must be `public`; however, you can define it at a different access level by using the [x:ClassModifier Directive](xclassmodifier-directive.md).</span></span>

<span data-ttu-id="904a8-131">Esta interpretación `x:Class` del atributo solo se aplica a una implementación XAML basada en CLR, en particular a los servicios XAML de .NET.</span><span class="sxs-lookup"><span data-stu-id="904a8-131">This interpretation of the `x:Class` attribute applies only to a CLR-based XAML implementation, in particular to .NET XAML Services.</span></span> <span data-ttu-id="904a8-132">Otras implementaciones XAML que no se basan en CLR y que no usan servicios XAML de .NET podrían usar una fórmula de resolución diferente para conectar el marcado XAML y respaldar el código en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="904a8-132">Other XAML implementations that are not based on CLR and that do not use .NET XAML Services might use a different resolution formula for connecting XAML markup and backing run-time code.</span></span> <span data-ttu-id="904a8-133">Para obtener más información acerca `x:Class`de las interpretaciones más generales de , vea [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="904a8-133">For more information about more general interpretations of `x:Class`, see [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

<span data-ttu-id="904a8-134">En un cierto nivel de `x:Class` arquitectura, el significado de es indefinido en los servicios XAML de .NET.</span><span class="sxs-lookup"><span data-stu-id="904a8-134">At a certain level of architecture, the meaning of `x:Class` is undefined in .NET XAML Services.</span></span> <span data-ttu-id="904a8-135">Esto se debe a que los servicios XAML de .NET no especifican el modelo de programación por el que se conectan el código de marcado y respaldo XAML.</span><span class="sxs-lookup"><span data-stu-id="904a8-135">This is because .NET XAML Services does not specify the programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="904a8-136">Los usos `x:Class` adicionales de la directiva pueden implementarse mediante marcos específicos que usan modelos de programación o modelos de aplicación para definir cómo conectar el marcado XAML y el código subyacente basado en CLR.</span><span class="sxs-lookup"><span data-stu-id="904a8-136">Additional uses of the `x:Class` directive might be implemented by specific frameworks that use programming models or application models to define how to connect XAML markup and CLR-based code-behind.</span></span> <span data-ttu-id="904a8-137">Cada marco de trabajo puede tener sus propias acciones de compilación que habilitan algunos de los componentes específicos o de comportamiento que se deben incluir en el entorno de compilación.</span><span class="sxs-lookup"><span data-stu-id="904a8-137">Each framework can have its own build actions that enable some of the behavior or specific components that must be included in the build environment.</span></span> <span data-ttu-id="904a8-138">Dentro de un marco de trabajo, las acciones de compilación también pueden variar en función del lenguaje CLR específico que se usa para el código subyacente.</span><span class="sxs-lookup"><span data-stu-id="904a8-138">Within a framework, build actions can also vary depending on the specific CLR language that is used for the code-behind.</span></span>

## <a name="xclass-in-the-wpf-programming-model"></a><span data-ttu-id="904a8-139">x:Clase en el modelo de programación WPF</span><span class="sxs-lookup"><span data-stu-id="904a8-139">x:Class in the WPF Programming Model</span></span>

<span data-ttu-id="904a8-140">En las aplicaciones WPFWPF `x:Class` y el modelo de aplicación WPFWPF, se puede declarar como un atributo para cualquier elemento que `Page` es la raíz <xref:System.Windows.Application> de un archivo XAML y se está compilando (donde el XAML se incluye en un proyecto de aplicación WPF WPF con acción de compilación) o para la raíz en la definición de aplicación de una aplicación WPF compilada.</span><span class="sxs-lookup"><span data-stu-id="904a8-140">In WPF applications and the WPF application model, `x:Class` can be declared as an attribute for any element that is the root of a XAML file and is being compiled (where the XAML is included in a WPF application project with `Page` build action), or for the <xref:System.Windows.Application> root in the application definition of a compiled WPF application.</span></span> <span data-ttu-id="904a8-141">Declarar `x:Class` en un elemento que no sea una raíz de página o raíz de aplicación, o en un archivo XAML de WPF que no se compila, produce un error en tiempo de compilación en el compilador XAML de .NET Framework 3.0 y .NET Framework 3.5 WPF.</span><span class="sxs-lookup"><span data-stu-id="904a8-141">Declaring `x:Class` on an element other than a page root or application root, or on a WPF XAML file that is not compiled, causes a compile-time error under the .NET Framework 3.0 and .NET Framework 3.5 WPF XAML compiler.</span></span> <span data-ttu-id="904a8-142">Para obtener información acerca `x:Class` de otros aspectos del control en WPFWPF, vea [Código subyacente y XAML en WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="904a8-142">For information about other aspects of `x:Class` handling in WPF, see [Code-Behind and XAML in WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).</span></span>

## <a name="xclass-for-windows-workflow-foundation"></a><span data-ttu-id="904a8-143">x:Class for Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="904a8-143">x:Class for Windows Workflow Foundation</span></span>
<span data-ttu-id="904a8-144">Para Windows Workflow `x:Class` Foundation, asigna un nombre a la clase de una actividad personalizada compuesta por completo en XAML o la clase parcial de la página XAML para un diseñador de actividades con código subyacente.</span><span class="sxs-lookup"><span data-stu-id="904a8-144">For Windows Workflow Foundation, `x:Class` names the class of a custom activity composed entirely in XAML, or names the partial class of the XAML page for  an activity designer with code-behind.</span></span>

## <a name="silverlight-usage-notes"></a><span data-ttu-id="904a8-145">Notas de uso de Silverlight</span><span class="sxs-lookup"><span data-stu-id="904a8-145">Silverlight Usage Notes</span></span>

<span data-ttu-id="904a8-146">`x:Class`para Silverlight se documenta por separado.</span><span class="sxs-lookup"><span data-stu-id="904a8-146">`x:Class` for Silverlight is documented separately.</span></span> <span data-ttu-id="904a8-147">Para obtener más información, vea [Espacio de nombres XAML (x:) Características del idioma (Silverlight).](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95))</span><span class="sxs-lookup"><span data-stu-id="904a8-147">For more information, see [XAML Namespace (x:) Language Features (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).</span></span>

## <a name="see-also"></a><span data-ttu-id="904a8-148">Consulte también</span><span class="sxs-lookup"><span data-stu-id="904a8-148">See also</span></span>

- [<span data-ttu-id="904a8-149">x:Subclass (Directiva)</span><span class="sxs-lookup"><span data-stu-id="904a8-149">x:Subclass Directive</span></span>](xsubclass-directive.md)
- [<span data-ttu-id="904a8-150">Clases XAML y personalizadas para WPF</span><span class="sxs-lookup"><span data-stu-id="904a8-150">XAML and Custom Classes for WPF</span></span>](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [<span data-ttu-id="904a8-151">x:ClassModifier (Directiva)</span><span class="sxs-lookup"><span data-stu-id="904a8-151">x:ClassModifier Directive</span></span>](xclassmodifier-directive.md)
- [<span data-ttu-id="904a8-152">Tipos migrados de WPF a System.Xaml</span><span class="sxs-lookup"><span data-stu-id="904a8-152">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
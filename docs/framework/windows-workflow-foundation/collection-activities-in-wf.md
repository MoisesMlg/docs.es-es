---
title: Actividades de colección en WF
ms.date: 03/30/2017
ms.assetid: 2680c3e2-9902-4968-b98d-cab776103dbe
ms.openlocfilehash: ff6bfdff7c05d996be66af508307f2087d8bfc76
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250338"
---
# <a name="collection-activities-in-wf"></a><span data-ttu-id="a0e3f-102">Actividades de colección en WF</span><span class="sxs-lookup"><span data-stu-id="a0e3f-102">Collection Activities in WF</span></span>

<span data-ttu-id="a0e3f-103">Las actividades de colección se usan para trabajar con objetos de colección en un flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-103">Collection activities are used to work with collection objects in a workflow.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="a0e3f-104">tiene actividades proporcionadas por el sistema para agregar y quitar elementos de una colección, probar la existencia de un elemento en una colección y borrar una colección.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-104">has system-provided activities for adding and removing items from a collection, testing for the existence of an item in a collection, and clearing a collection.</span></span> <span data-ttu-id="a0e3f-105">`ExistsInCollection` y `RemoveFromCollection` tienen un <xref:System.Activities.OutArgument%601> de tipo <xref:System.Boolean> , que indica el resultado.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-105">`ExistsInCollection` and `RemoveFromCollection` have an <xref:System.Activities.OutArgument%601> of type <xref:System.Boolean>, which indicates the result.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a0e3f-106">Si se ejecuta una actividad de colección antes de establecer el objeto de colección subyacente, se inicia una excepción <xref:System.InvalidOperationException> y se produce un error en la actividad.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-106">If a collection activity is executed before setting the underlying collection object, an <xref:System.InvalidOperationException> is thrown and the activity faults.</span></span>  
  
## <a name="collection-activities"></a><span data-ttu-id="a0e3f-107">Actividades de colección</span><span class="sxs-lookup"><span data-stu-id="a0e3f-107">Collection activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.AddToCollection%601>|<span data-ttu-id="a0e3f-108">Agrega un elemento a una colección especificada.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-108">Adds an item to a specified collection.</span></span>|  
|<xref:System.Activities.Statements.ClearCollection%601>|<span data-ttu-id="a0e3f-109">Borra todos los elementos de una colección especificada.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-109">Clears all items from a specified collection.</span></span>|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|<span data-ttu-id="a0e3f-110">Devuelve `true` si un elemento ya existe en una colección.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-110">Returns `true` if an item exists in a collection.</span></span>|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|<span data-ttu-id="a0e3f-111">Quita un elemento de una colección especificada y devuelve `true` si el elemento se quitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-111">Removes an item from a specified collection and returns `true` if the item was successfully removed.</span></span>|  
  
## <a name="using-collection-activities"></a><span data-ttu-id="a0e3f-112">Usar actividades de colección</span><span class="sxs-lookup"><span data-stu-id="a0e3f-112">Using collection activities</span></span>  

 <span data-ttu-id="a0e3f-113">El siguiente ejemplo de código muestra cómo interactuar con un colección declarada como una variable de flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-113">The following code example demonstrates how to interact with a collection declared as a workflow variable.</span></span> <span data-ttu-id="a0e3f-114">La colección usada es una <xref:System.Collections.Generic.List%601> de objetos <xref:System.String> denominada `fruitList`.</span><span class="sxs-lookup"><span data-stu-id="a0e3f-114">The collection used is a <xref:System.Collections.Generic.List%601> of <xref:System.String> objects named `fruitList`.</span></span>  
  
```csharp  
Variable<ICollection<string>> fruitList = new Variable<ICollection<string>>  
{  
    Default = new VisualBasicValue<ICollection<string>>("New List(Of String) From {\"Apple\", \"Orange\"}"),  
    Name = "FruitList"  
};  
  
Variable<bool> result = new Variable<bool>  
{  
    Name = "Result"  
};  
  
Activity wf = new Sequence  
{  
    Variables = { fruitList, result },  
  
    Activities =
    {  
        new If  
        {  
            Condition = new ExistsInCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Pear"  
            },  
            Then = new AddToCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Pear"  
            },  
            Else = new RemoveFromCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Apple"  
            }  
        },  
  
        new RemoveFromCollection<string>  
        {  
            Collection = fruitList,  
            Item = "Apple",  
            Result = result  
        },  
        new If  
        {  
            Condition = result,  
            Then = new ClearCollection<string>  
            {  
                Collection = fruitList,  
            }  
        }  
    }  
};  
```  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
    <x:Reference>__ReferenceID1</x:Reference>  
  </Sequence.Variables>  
  <If>  
    <If.Condition>  
      <InArgument  
         x:TypeArguments="x:Boolean">  
        <ExistsInCollection  
           x:TypeArguments="x:String"  
           Item="Pear">  
          <ExistsInCollection.Result>  
            <OutArgument  
               x:TypeArguments="x:Boolean" />  
          </ExistsInCollection.Result>  
          <InArgument  
             x:TypeArguments="scg:ICollection(x:String)">  
            <VariableValue  
               x:TypeArguments="scg:ICollection(x:String)">  
              <VariableValue.Result>  
                <OutArgument  
                   x:TypeArguments="scg:ICollection(x:String)" />  
              </VariableValue.Result>  
              <VariableValue.Variable>  
                <Variable  
                   x:TypeArguments="scg:ICollection(x:String)"  
                   x:Name="__ReferenceID0"  
                   Default="[New List(Of String) From {"Apple", "Orange"}]"  
                   Name="FruitList" />  
              </VariableValue.Variable>  
            </VariableValue>  
          </InArgument>  
        </ExistsInCollection>  
      </InArgument>  
    </If.Condition>  
    <If.Then>  
      <AddToCollection  
         x:TypeArguments="x:String"  
         Item="Pear">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </AddToCollection>  
    </If.Then>  
    <If.Else>  
      <RemoveFromCollection  
         x:TypeArguments="x:String"  
         Item="Apple"  
         Result="{x:Null}">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </RemoveFromCollection>  
    </If.Else>  
  </If>  
  <RemoveFromCollection  
     x:TypeArguments="x:String"  
     Item="Apple">  
    <RemoveFromCollection.Result>  
      <OutArgument  
         x:TypeArguments="x:Boolean">  
        <VariableReference  
           x:TypeArguments="x:Boolean">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(x:Boolean)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="x:Boolean"  
               x:Name="__ReferenceID1"  
               Name="Result" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </RemoveFromCollection.Result>  
    <InArgument  
       x:TypeArguments="scg:ICollection(x:String)">  
      <VariableValue  
         x:TypeArguments="scg:ICollection(x:String)"  
         Variable="{x:Reference __ReferenceID0}">  
        <VariableValue.Result>  
          <OutArgument  
             x:TypeArguments="scg:ICollection(x:String)" />  
        </VariableValue.Result>  
      </VariableValue>  
    </InArgument>  
  </RemoveFromCollection>  
  <If>  
    <If.Condition>  
      <InArgument  
         x:TypeArguments="x:Boolean">  
        <VariableValue  
           x:TypeArguments="x:Boolean"  
           Variable="{x:Reference __ReferenceID1}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="x:Boolean" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </If.Condition>  
    <If.Then>  
      <ClearCollection  
         x:TypeArguments="x:String">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </ClearCollection>  
    </If.Then>  
  </If>  
</Sequence>  
```  
  
 <span data-ttu-id="a0e3f-115">Los ejemplos de código anteriores también se pueden crear mediante <xref:Microsoft.CSharp.Activities.CSharpValue%601> en lugar de <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601></span><span class="sxs-lookup"><span data-stu-id="a0e3f-115">The above code samples can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601></span></span>  
  
```csharp
Variable<ICollection<string>> fruitList = new Variable<ICollection<string>>  
{  
    Default = new CSharpValue<ICollection<string>>("new List<String> From {\"Apple\", \"Orange\"};"),  
    Name = "FruitList"  
};  
  
Variable<bool> result = new Variable<bool>  
{  
    Name = "Result"  
};  
  
Activity wf = new Sequence  
{  
    Variables = { fruitList, result },  
  
    Activities =
    {  
        new If  
        {  
            Condition = new ExistsInCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Pear"  
            },  
            Then = new AddToCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Pear"  
            },  
            Else = new RemoveFromCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Apple"  
            }  
        },  
  
        new RemoveFromCollection<string>  
        {  
            Collection = fruitList,  
            Item = "Apple",  
            Result = result  
        },  
        new If  
        {  
            Condition = result,  
            Then = new ClearCollection<string>  
            {  
                Collection = fruitList,  
            }  
        }  
    }  
};  
```  
  
```xml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
    <x:Reference>__ReferenceID1</x:Reference>  
  </Sequence.Variables>  
  <If>  
    <If.Condition>  
      <InArgument  
         x:TypeArguments="x:Boolean">  
        <ExistsInCollection  
           x:TypeArguments="x:String"  
           Item="Pear">  
          <ExistsInCollection.Result>  
            <OutArgument  
               x:TypeArguments="x:Boolean" />  
          </ExistsInCollection.Result>  
          <InArgument  
             x:TypeArguments="scg:ICollection(x:String)">  
            <VariableValue  
               x:TypeArguments="scg:ICollection(x:String)">  
              <VariableValue.Result>  
                <OutArgument  
                   x:TypeArguments="scg:ICollection(x:String)" />  
              </VariableValue.Result>  
              <VariableValue.Variable>  
                <Variable  
                   x:TypeArguments="scg:ICollection(x:String)"  
                   x:Name="__ReferenceID0"  
                   Default="[new List<String> From {"Apple", "Orange"};]"  
                   Name="FruitList" />  
              </VariableValue.Variable>  
            </VariableValue>  
          </InArgument>  
        </ExistsInCollection>  
      </InArgument>  
    </If.Condition>  
    <If.Then>  
      <AddToCollection  
         x:TypeArguments="x:String"  
         Item="Pear">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </AddToCollection>  
    </If.Then>  
    <If.Else>  
      <RemoveFromCollection  
         x:TypeArguments="x:String"  
         Item="Apple"  
         Result="{x:Null}">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </RemoveFromCollection>  
    </If.Else>  
  </If>  
  <RemoveFromCollection  
     x:TypeArguments="x:String"  
     Item="Apple">  
    <RemoveFromCollection.Result>  
      <OutArgument  
         x:TypeArguments="x:Boolean">  
        <VariableReference  
           x:TypeArguments="x:Boolean">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(x:Boolean)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="x:Boolean"  
               x:Name="__ReferenceID1"  
               Name="Result" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </RemoveFromCollection.Result>  
    <InArgument  
       x:TypeArguments="scg:ICollection(x:String)">  
      <VariableValue  
         x:TypeArguments="scg:ICollection(x:String)"  
         Variable="{x:Reference __ReferenceID0}">  
        <VariableValue.Result>  
          <OutArgument  
             x:TypeArguments="scg:ICollection(x:String)" />  
        </VariableValue.Result>  
      </VariableValue>  
    </InArgument>  
  </RemoveFromCollection>  
  <If>  
    <If.Condition>  
      <InArgument  
         x:TypeArguments="x:Boolean">  
        <VariableValue  
           x:TypeArguments="x:Boolean"  
           Variable="{x:Reference __ReferenceID1}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="x:Boolean" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </If.Condition>  
    <If.Then>  
      <ClearCollection  
         x:TypeArguments="x:String">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </ClearCollection>  
    </If.Then>  
  </If>  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0e3f-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="a0e3f-116">See also</span></span>

- [<span data-ttu-id="a0e3f-117">Crear flujos de trabajo, actividades y expresiones mediante código imperativo</span><span class="sxs-lookup"><span data-stu-id="a0e3f-117">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)

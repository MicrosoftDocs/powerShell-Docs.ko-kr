---
ms.date: 09/13/2016
ms.topic: reference
title: 동적 매개 변수를 선언하는 방법
description: 동적 매개 변수를 선언하는 방법
ms.openlocfilehash: 0f5a8f249b414663aa9702a908ea5c8ca24755ff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667082"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="ec6e8-103">동적 매개 변수를 선언하는 방법</span><span class="sxs-lookup"><span data-stu-id="ec6e8-103">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="ec6e8-104">이 예에서는 런타임에 cmdlet에 추가 되는 동적 매개 변수를 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ec6e8-104">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="ec6e8-105">이 예제에서 `Department` 매개 변수는 사용자가 스위치 매개 변수를 지정할 때마다 cmdlet에 추가 됩니다 `Employee` .</span><span class="sxs-lookup"><span data-stu-id="ec6e8-105">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="ec6e8-106">동적 매개 변수에 대 한 자세한 내용은 [Cmdlet 동적 매개 변수](./cmdlet-dynamic-parameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ec6e8-106">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="ec6e8-107">동적 매개 변수를 정의 하려면</span><span class="sxs-lookup"><span data-stu-id="ec6e8-107">To define dynamic parameters</span></span>

1. <span data-ttu-id="ec6e8-108">Cmdlet 클래스 선언에서 표시 된 대로 [Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) 인터페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec6e8-108">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="ec6e8-109">[Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) 메서드를 호출 합니다 .이 메서드는 동적 매개 변수가 정의 된 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec6e8-109">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="ec6e8-110">이 예제에서는 매개 변수가 지정 될 때 메서드가 호출 됩니다 `Employee` .</span><span class="sxs-lookup"><span data-stu-id="ec6e8-110">In this example, the method is called when the `Employee` parameter is specified.</span></span>

   ```csharp
   public object GetDynamicParameters()
   {
       if (employee)
       {
         context= new SendGreetingCommandDynamicParameters();
         return context;
       }
       return null;
   }
   private SendGreetingCommandDynamicParameters context;
   ```

3. <span data-ttu-id="ec6e8-111">추가할 동적 매개 변수를 정의 하는 클래스를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec6e8-111">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="ec6e8-112">정적 cmdlet 매개 변수를 선언 하는 데 사용 된 특성을 사용 하 여 동적 매개 변수를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec6e8-112">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

   ```csharp
   public class SendGreetingCommandDynamicParameters
   {
     [Parameter]
     [ValidateSet ("Marketing", "Sales", "Development")]
     public string Department
     {
       get { return department; }
       set { department = value; }
     }
     private string department;
   }
   ```

## <a name="example"></a><span data-ttu-id="ec6e8-113">예제</span><span class="sxs-lookup"><span data-stu-id="ec6e8-113">Example</span></span>

<span data-ttu-id="ec6e8-114">이 예제에서 매개 변수는 `Department` 사용자가 매개 변수를 지정할 때마다 추가 됩니다 `Employee` .</span><span class="sxs-lookup"><span data-stu-id="ec6e8-114">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="ec6e8-115">`Department`매개 변수는 선택적 매개 변수 이며, ValidateSet 특성을 사용 하 여 허용 되는 인수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec6e8-115">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;     // PowerShell assembly.

namespace SendGreeting
{
  // Declare the cmdlet class that supports the
  // IDynamicParameters interface.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet, IDynamicParameters
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    [Parameter]
    [Alias ("FTE")]
    public SwitchParameter Employee
    {
      get { return employee; }
      set { employee = value; }
    }
    private Boolean employee;

    // Implement GetDynamicParameters to
    // retrieve the dynamic parameter.
    public object GetDynamicParameters()
    {
      if (employee)
      {
        context= new SendGreetingCommandDynamicParameters();
        return context;
      }
      return null;
   }
   private SendGreetingCommandDynamicParameters context;

    // Overide the ProcessRecord method to process the
    // supplied user name and write out a greeting to
    // the user by calling the WriteObject method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "! ");
      if (employee)
      {
        WriteObject("Department: " + context.Department);
      }
    }
  }

  // Define the dynamic parameters to be added
  public class SendGreetingCommandDynamicParameters
  {
    [Parameter]
    [ValidateSet ("Marketing", "Sales", "Development")]
    public string Department
    {
      get { return department; }
      set { department = value; }
    }
    private string department;
  }
}
```

## <a name="see-also"></a><span data-ttu-id="ec6e8-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec6e8-116">See Also</span></span>

[<span data-ttu-id="ec6e8-117">Runtimedefinedparameterdictionary.</span><span class="sxs-lookup"><span data-stu-id="ec6e8-117">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="ec6e8-118">Idynamicparameters. Getdynamicparameters \*</span><span class="sxs-lookup"><span data-stu-id="ec6e8-118">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="ec6e8-119">Cmdlet 동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ec6e8-119">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="ec6e8-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ec6e8-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

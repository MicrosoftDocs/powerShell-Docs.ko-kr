---
title: 동적 매개 변수를 선언 하는 방법 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8839aa8841bf94a9b7f8f930ca315fe0ccedb30
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784183"
---
# <a name="how-to-declare-dynamic-parameters"></a>동적 매개 변수를 선언하는 방법

이 예에서는 런타임에 cmdlet에 추가 되는 동적 매개 변수를 정의 하는 방법을 보여 줍니다. 이 예제에서 `Department` 매개 변수는 사용자가 스위치 매개 변수를 지정할 때마다 cmdlet에 추가 됩니다 `Employee` . 동적 매개 변수에 대 한 자세한 내용은 [Cmdlet 동적 매개 변수](./cmdlet-dynamic-parameters.md)를 참조 하세요.

## <a name="to-define-dynamic-parameters"></a>동적 매개 변수를 정의 하려면

1. Cmdlet 클래스 선언에서 표시 된 대로 [Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) 인터페이스를 추가 합니다.

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. [Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) 메서드를 호출 합니다 .이 메서드는 동적 매개 변수가 정의 된 개체를 반환 합니다. 이 예제에서는 매개 변수가 지정 될 때 메서드가 호출 됩니다 `Employee` .

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

3. 추가할 동적 매개 변수를 정의 하는 클래스를 선언 합니다. 정적 cmdlet 매개 변수를 선언 하는 데 사용 된 특성을 사용 하 여 동적 매개 변수를 선언할 수 있습니다.

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

## <a name="example"></a>예제

이 예제에서 매개 변수는 `Department` 사용자가 매개 변수를 지정할 때마다 추가 됩니다 `Employee` . `Department`매개 변수는 선택적 매개 변수 이며, ValidateSet 특성을 사용 하 여 허용 되는 인수를 지정 합니다.

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

## <a name="see-also"></a>참고 항목

[Runtimedefinedparameterdictionary.](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[Idynamicparameters. Getdynamicparameters *](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Cmdlet 동적 매개 변수](./cmdlet-dynamic-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)

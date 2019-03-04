---
title: 동적 매개 변수를 선언 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857659"
---
# <a name="how-to-declare-dynamic-parameters"></a>동적 매개 변수를 선언하는 방법

이 예제에서는 런타임에 cmdlet에 추가 되는 동적 매개 변수를 정의 하는 방법을 보여 줍니다. 이 예제에서는 합니다 `Department` 때마다 사용자 지정 cmdlet 매개 변수는 추가 `Employee` 스위치 매개 변수입니다. 동적 매개 변수에 대 한 자세한 내용은 참조 하십시오 [cmdlet은 동적 매개 변수](./cmdlet-dynamic-parameters.md)합니다.

## <a name="to-define-dynamic-parameters"></a>동적 매개 변수를 정의 하려면

1. Cmdlet 클래스 선언에 추가 합니다 [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) 표시 된 것 처럼 인터페이스입니다.

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. 호출 된 [System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) 동적 매개 변수 정의 되는 개체를 반환 하는 메서드. 이 예는 메서드를 호출한 경우는 `Employee` 매개 변수를 지정 합니다.

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

3. 추가 동적 매개 변수를 정의 하는 클래스를 선언 합니다. 동적 매개 변수를 선언 하려면 정적 cmdlet 매개 변수를 선언 하는 데는 특성을 사용할 수 있습니다.

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

이 예제에서는 합니다 `Department` 때마다 사용자 지정 매개 변수를 추가 합니다 `Employee` 매개 변수입니다. `Department` 매개 변수는 선택적 매개 변수 이며 ValidateSet 특성 허용 된 인수를 지정 하는 데 사용 됩니다.

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

[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Cmdlet은 동적 매개 변수](./cmdlet-dynamic-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
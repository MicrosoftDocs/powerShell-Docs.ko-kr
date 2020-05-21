---
title: 간단한 Cmdlet을 작성 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 9bd72e8f97c194c98adb1049f5a966549113fd12
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563898"
---
# <a name="how-to-write-a-cmdlet"></a>Cmdlet을 작성 하는 방법

이 문서에서는 cmdlet을 작성 하는 방법을 보여 줍니다. `Send-Greeting`Cmdlet은 단일 사용자 이름을 입력으로 사용 하 고 해당 사용자에 게 인사말을 작성 합니다. Cmdlet은 많은 작업을 수행 하지 않지만이 예에서는 cmdlet의 주요 섹션을 보여 줍니다.

## <a name="steps-to-write-a-cmdlet"></a>Cmdlet을 작성 하는 단계

1. 클래스를 cmdlet으로 선언 하려면 **cmdlet** 특성을 사용 합니다. **Cmdlet** 특성은 cmdlet 이름에 대 한 동사와 명사를 지정 합니다.

   **Cmdlet** 특성에 대 한 자세한 내용은 [cmdletattribute 선언](cmdlet-attribute-declaration.md)을 참조 하세요.

2. 클래스의 이름을 지정 합니다.

3. 다음 클래스 중 하나에서 cmdlet이 파생 되도록 지정 합니다.

   * [System.object.](/dotnet/api/System.Management.Automation.Cmdlet)
   * [PSCmdlet.](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Cmdlet에 대 한 매개 변수를 정의 하려면 **매개 변수** 특성을 사용 합니다. 이 경우 필수 매개 변수를 하나만 지정 합니다.

   **Parameter** 특성에 대 한 자세한 내용은 [parameterattribute 선언](parameter-attribute-declaration.md)을 참조 하세요.

5. 입력을 처리 하는 입력 처리 메서드를 재정의 합니다. 이 경우에는 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드가 재정의 되 고,

6. 인사말을 작성 하려면 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)메서드를 사용 합니다.
   인사말이 다음과 같은 형식으로 표시 됩니다.

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a>예제

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>참조

[System.object.](/dotnet/api/System.Management.Automation.Cmdlet)

[PSCmdlet.](/dotnet/api/System.Management.Automation.PSCmdlet)

[ProcessRecord입니다.](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[WriteObject입니다.](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[CmdletAttribute 선언](cmdlet-attribute-declaration.md)

[ParameterAttribute 선언](parameter-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](writing-a-windows-powershell-cmdlet.md)

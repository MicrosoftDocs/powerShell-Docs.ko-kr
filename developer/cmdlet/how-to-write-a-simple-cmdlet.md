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
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251458"
---
# <a name="how-to-write-a-cmdlet"></a>Cmdlet을 작성 하는 방법

이 문서에는 cmdlet을 작성 하는 방법을 보여 줍니다. `Send-Greeting` cmdlet를 단일 사용자 이름 입력으로 받아 다음 해당 사용자에 게 인사말을 기록 합니다. Cmdlet에서는 가능한 한 많은 작업을 수행 하지 않지만이 예제에서는 cmdlet의 주요 섹션을 보여 줍니다.

## <a name="steps-to-write-a-cmdlet"></a>Cmdlet을 작성 하는 단계

1. Cmdlet으로 클래스를 선언 하려면 사용 합니다 **Cmdlet** 특성입니다. 합니다 **Cmdlet** 동사와 명사는 cmdlet 이름에 대 한 특성을 지정 합니다.

   에 대 한 자세한 내용은 합니다 **Cmdlet** 특성을 참조 하십시오 [CmdletAttribute 선언의](cmdlet-attribute-declaration.md)합니다.

2. 클래스의 이름을 지정 합니다.

3. Cmdlet은 다음 클래스 중 하나에서 파생 되는 것을 지정 합니다.

   * [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Cmdlet에 대 한 매개 변수를 정의 하려면 사용 합니다 **매개 변수** 특성입니다. 이 경우 하나의 매개 변수를 지정 해야 합니다.

   에 대 한 자세한 내용은 합니다 **매개 변수** 특성을 참조 하십시오 [ParameterAttribute 선언](parameter-attribute-declaration.md)합니다.

5. 입력 처리 입력을 처리 하는 메서드를 재정의 합니다. 이 경우에 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 합니다.

6. 인사말을 쓸 메서드를 사용 하 여 [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)합니다.
   인사말은 다음 형식으로 표시 됩니다.

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

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[CmdletAttribute 선언](cmdlet-attribute-declaration.md)

[ParameterAttribute 선언](parameter-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet](writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
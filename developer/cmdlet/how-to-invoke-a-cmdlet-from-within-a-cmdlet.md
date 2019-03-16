---
title: Cmdlet 내에서 Cmdlet을 호출 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055906"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Cmdlet 내에서 Cmdlet을 호출하는 방법

이 예제에서는 호출된 cmdlet의 기능을 개발 하는 cmdlet에 추가할 수 있는 다른 cmdlet 내에서 cmdlet을 호출 하는 방법을 보여 줍니다. 이 예제는 `Get-Process` cmdlet은 로컬 컴퓨터에서 실행 되는 프로세스를 가져오려면 호출 됩니다. 에 대 한 호출을 `Get-Process` cmdlet은 다음 명령과 동일 합니다. 이 명령은 이름이 "a"부터 "t" 문자로 시작 하는 모든 프로세스를 검색 합니다.

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> 직접 파생 되는 cmdlet에만 호출할 수 있습니다 합니다 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 클래스입니다. 파생 되는 cmdlet를 호출할 수 없습니다는 [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스입니다.

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Cmdlet 내에서 cmdlet을 호출 하려면

1. Cmdlet이 호출을 정의 하는 어셈블리를 참조 하는지 확인 하 고 적절 한 `using` 문을 추가 합니다. 이 예제에서는 다음 네임 스페이스 추가 됩니다.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. Cmdlet의 메서드를 처리 하는 입력을 호출할 cmdlet의 새 인스턴스를 만듭니다. 이 예제에서는 형식의 개체로 [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) cmdlet 호출 될 때 사용 되는 인수를 포함 하는 문자열과 함께 만들어집니다.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. 호출 된 [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 메서드를 호출 하는 `Get-Process` cmdlet.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>예제

이 예는 `Get-Process` cmdlet 내에서 호출 되는 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) cmdlet의 메서드.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

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

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

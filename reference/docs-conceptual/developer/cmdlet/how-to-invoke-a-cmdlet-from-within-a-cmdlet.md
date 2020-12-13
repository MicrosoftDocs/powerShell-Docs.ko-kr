---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 내에서 Cmdlet을 호출하는 방법
description: Cmdlet 내에서 Cmdlet을 호출하는 방법
ms.openlocfilehash: d137ac895f66000329de76a2c16a74b02c0e82ca
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667048"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Cmdlet 내에서 Cmdlet을 호출하는 방법

이 예에서는 다른 cmdlet 내에서 cmdlet을 호출 하는 방법을 보여 줍니다 .이 cmdlet을 사용 하면 호출 되는 cmdlet의 기능을 개발 중인 cmdlet에 추가할 수 있습니다. 이 예제에서는 cmdlet을 `Get-Process` 호출 하 여 로컬 컴퓨터에서 실행 중인 프로세스를 가져옵니다. Cmdlet에 대 한 호출은 `Get-Process` 다음 명령과 동일 합니다. 이 명령은 이름이 "a"에서 "t" 까지의 문자로 시작 하는 모든 프로세스를 검색 합니다.

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> [System.object](/dotnet/api/System.Management.Automation.Cmdlet) 클래스에서 직접 파생 되는 cmdlet만 호출할 수 있습니다. [PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스에서 파생 된 cmdlet을 호출할 수 없습니다.

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Cmdlet에서 cmdlet을 호출 하려면

1. 호출할 cmdlet을 정의 하는 어셈블리가 참조 되 고 적절 한 `using` 문이 추가 되었는지 확인 합니다. 이 예제에서는 다음 네임 스페이스를 추가 합니다.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. Cmdlet의 입력 처리 메서드에서 호출할 cmdlet의 새 인스턴스를 만듭니다. 이 예제에서는 cmdlet을 호출할 때 사용 되는 인수를 포함 하는 문자열과 함께 [Microsoft. PowerShell. Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) 형식의 개체가 생성 됩니다.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Cmdlet을 호출 하려면 [system.web. invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 메서드를 호출 합니다. `Get-Process`

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>예제

이 예제에서 cmdlet은 `Get-Process` cmdlet의 system.object를 실행 하는 [프로세스](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 에서 호출 됩니다.

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

## <a name="see-also"></a>관련 항목

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)

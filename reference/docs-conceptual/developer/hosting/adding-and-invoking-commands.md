---
ms.date: 09/13/2016
ms.topic: reference
title: 명령 추가 및 호출
description: 명령 추가 및 호출
ms.openlocfilehash: f539172eaf119fe5774e158c77a00276c8ba9e0a
ms.sourcegitcommit: 880b00218708724a76503000c9eca181f4e00891
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2021
ms.locfileid: "99049428"
---
# <a name="adding-and-invoking-commands"></a>명령 추가 및 호출

Runspace를 만든 후에는 파이프라인에 Windows PowerShellcommands 및 스크립트를 추가한 다음 파이프라인을 동기적 또는 비동기적으로 호출할 수 있습니다.

## <a name="creating-a-pipeline"></a>파이프라인 만들기

[System.object](/dotnet/api/system.management.automation.powershell) 클래스는 파이프라인에 명령, 매개 변수 및 스크립트를 추가 하는 여러 메서드를 제공 합니다. [System.object](/dotnet/api/System.Management.Automation.PowerShell.Invoke) 의 오버 로드를 호출 하 여 파이프라인을 동기적으로 호출 하거나, [system.object](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) 의 오버 로드를 호출 하 여 비동기적으로 파이프라인을 호출 하거나, 그런 다음, system.web. x m n [* 메서드를](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) 호출할 수 있습니다.

### <a name="addcommand"></a>AddCommand

1. System.web. [Powershell](/dotnet/api/system.management.automation.powershell) 개체를 만듭니다.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. 실행할 명령을 추가 합니다.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. 명령을 호출 합니다.

   ```csharp
   ps.Invoke();
   ```

[System.object](/dotnet/api/System.Management.Automation.PowerShell.Invoke) 를 호출 하기 [전에 system.object를](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) 두 번 이상 호출 하는 경우에는 첫 번째 명령의 결과가 두 번째로 파이프 되는 식으로, 두 번째 명령의 결과가 차례로 표시 됩니다. 이전 명령의 결과를 명령에 파이프 하지 않으려면 대신 System.web. n a m a. n a m a [*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 를 호출 하 여 추가 합니다.

### <a name="addparameter"></a>AddParameter

 이전 예제에서는 매개 변수 없이 단일 명령을 실행 합니다. 명령을 사용 하 여 명령에 매개 변수를 추가할 수 있습니다 [. Addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 메서드 예를 들어 다음 코드는 `PowerShell` 컴퓨터에서 실행 되는 명명 된 모든 프로세스 목록을 가져옵니다.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

[System.object](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 를 호출 하 여 매개 변수를 더 추가할 수 있습니다.

```csharp
PowerShell.Create().AddCommand("Get-Command")
                   .AddParameter("Name", "Get-VM")
                   .AddParameter("Module", "Hyper-V")
                   .Invoke();
```

또한 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) 를 호출 하 여 매개 변수 이름 및 값의 사전을 추가할 수 있습니다.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "Get-VM");

parameters.Add("Module", "Hyper-V");
PowerShell.Create().AddCommand("Get-Command")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

파이프라인의 끝에 문을 추가 하는 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 를 사용 하 여 일괄 처리를 시뮬레이션할 수 있습니다. 다음 코드는 이름이 인 실행 중인 프로세스 목록을 가져온 `PowerShell` 다음 실행 중인 서비스 목록을 가져옵니다.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

기존 스크립트는 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 를 호출 하는 방법으로 실행할 수 있습니다. 다음 예제에서는 스크립트를 파이프라인에 추가 하 고 실행 합니다. 이 예에서는 라는 폴더에 라는 스크립트가 이미 있다고 가정 `MyScript.ps1` `D:\PSScripts` 합니다.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(File.ReadAllText(@"D:\PSScripts\MyScript.ps1")).Invoke();
```

또한 라는 부울 매개 변수를 사용 하는 버전의 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 와 함께를 `useLocalScope` 사용 합니다. 이 매개 변수를로 설정 하면 `true` 스크립트는 로컬 범위에서 실행 됩니다. 다음 코드에서는 로컬 범위에서 스크립트를 실행 합니다.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(File.ReadAllText(@"D:\PSScripts\MyScript.ps1"), true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>동기적으로 파이프라인 호출

파이프라인에 요소를 추가한 후에는 호출 합니다. 파이프라인을 동기적으로 호출 하려면 [system.object](/dotnet/api/System.Management.Automation.PowerShell.Invoke) 의 오버 로드를 호출 합니다. 다음 예제에서는 파이프라인을 동기적으로 호출 하는 방법을 보여 줍니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a>비동기식으로 파이프라인 호출

[시스템](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) 의 오버 로드를 호출 하 여 [IAsyncResult](/dotnet/api/system.iasyncresult) 개체를 만든 다음,이 메서드를 호출 하 여 파이프라인을 비동기식으로 호출할 수 [있습니다.](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)

 다음 예제에서는 파이프라인을 비동기식으로 호출 하는 방법을 보여 줍니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult asyncpl = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(asyncpl))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a>참고 항목

 [InitialSessionState 만들기](./creating-an-initialsessionstate.md)

 [제한된 runspace 만들기](./creating-a-constrained-runspace.md)

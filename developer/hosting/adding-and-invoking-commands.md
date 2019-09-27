---
title: 명령 추가 및 호출 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: f776f13fe743a3f5f67de0d94883e3f754040ffc
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323477"
---
# <a name="adding-and-invoking-commands"></a>명령 추가 및 호출

Runspace를 만든 후에는 파이프라인에 Windows PowerShellcommands 및 스크립트를 추가한 다음 파이프라인을 동기적 또는 비동기적으로 호출할 수 있습니다.

## <a name="creating-a-pipeline"></a>파이프라인 만들기

 [System.object](/dotnet/api/system.management.automation.powershell) 클래스는 파이프라인에 명령, 매개 변수 및 스크립트를 추가 하는 여러 메서드를 제공 합니다. [System.object](/dotnet/api/System.Management.Automation.PowerShell.Invoke) 의 오버 로드를 호출 하 여 파이프라인을 동기적으로 호출 하거나, [시스템](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) 의 오버 로드를 호출 하 여 비동기적으로 파이프라인을 호출할 수 있습니다. 그런 다음, [이 메서드를 클릭 합니다.](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)

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

 이전 예제에서는 매개 변수 없이 단일 명령을 실행 합니다. 명령을 사용 하 여 명령에 매개 변수를 추가할 수 있습니다 [. addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 메서드 예를 들어 다음 코드는 컴퓨터에서 실행 되는 명명 `PowerShell` 된 모든 프로세스 목록을 가져옵니다.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 [System.object](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 를 호출 하 여 매개 변수를 더 추가할 수 있습니다.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 또한 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) 를 호출 하 여 매개 변수 이름 및 값의 사전을 추가할 수 있습니다.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 파이프라인의 끝에 문을 추가 하는 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 를 사용 하 여 일괄 처리를 시뮬레이션할 수 있습니다. 다음 코드는 이름이 `PowerShell`인 실행 중인 프로세스 목록을 가져옵니다. 그런 다음 실행 중인 서비스 목록을 가져옵니다.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 기존 스크립트는 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 를 호출 하는 방법으로 실행할 수 있습니다. 다음 예제에서는 스크립트를 파이프라인에 추가 하 고 실행 합니다. 이 예에서는 라는 `MyScript.ps1` `D:\PSScripts`폴더에 라는 스크립트가 이미 있다고 가정 합니다.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 또한 라는 `useLocalScope`부울 매개 변수를 사용 하는 버전의 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 와 함께를 사용 합니다. 이 매개 변수를로 `true`설정 하면 스크립트는 로컬 범위에서 실행 됩니다. 다음 코드에서는 로컬 범위에서 스크립트를 실행 합니다.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
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

 [시스템](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) 의 오버 로드를 호출 하 여 [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) 개체를 만든 다음, system.object를 호출 하 여 파이프라인을 비동기식으로 호출 합니다. [ *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) 메서드입니다.

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
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
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

## <a name="see-also"></a>관련 항목

 [InitialSessionState 만들기](./creating-an-initialsessionstate.md)

 [제한 된 runspace 만들기](./creating-a-constrained-runspace.md)

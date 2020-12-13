---
ms.date: 09/12/2016
ms.topic: reference
title: Windows PowerShell 호스트 빠른 시작
description: Windows PowerShell 호스트 빠른 시작
ms.openlocfilehash: 4cb7dae60342abb40bd7a989a27a692826b360e5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657423"
---
# <a name="windows-powershell-host-quickstart"></a>Windows PowerShell 호스트 빠른 시작

응용 프로그램에서 Windows PowerShell을 호스팅하려면 [system.web. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) 클래스를 사용 합니다.
이 클래스는 명령의 파이프라인을 만든 다음 runspace에서 해당 명령을 실행 하는 메서드를 제공 합니다.
호스트 응용 프로그램을 만드는 가장 간단한 방법은 기본 runspace를 사용 하는 것입니다.
기본 runspace는 모든 핵심 Windows PowerShell 명령을 포함 합니다.
응용 프로그램에서 Windows PowerShell 명령의 하위 집합만 노출 하도록 하려면 사용자 지정 runspace를 만들어야 합니다.

## <a name="using-the-default-runspace"></a>기본 runspace 사용

먼저 기본 runspace를 사용 하 고 [, 클래스의](/dotnet/api/System.Management.Automation.PowerShell) 메서드를 사용 하 여 명령, 매개 변수, 문 및 스크립트를 파이프라인에 추가 합니다.

### <a name="addcommand"></a>AddCommand

파이프라인에 명령을 추가 하는 데는 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) 를 사용 합니다.
예를 들어, 컴퓨터에서 실행 중인 프로세스 목록을 가져오려고 한다고 가정 합니다.
이 명령을 실행 하는 방법은 다음과 같습니다.

1. System.web. [PowerShell](/dotnet/api/System.Management.Automation.PowerShell) 개체를 만듭니다.

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

[System.object](/dotnet/api/System.Management.Automation.PowerShell.Invoke) 를 호출 하기 전에 addcommand 메서드를 두 번 이상 호출 하는 경우 첫 번째 명령의 결과는 두 번째로 파이프 됩니다.
이전 명령의 결과를 명령에 파이프 하지 않으려는 경우에는 대신 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 를 호출 하 여 명령에 추가 합니다.

### <a name="addparameter"></a>AddParameter

이전 예제에서는 매개 변수 없이 단일 명령을 실행 합니다.
명령을 사용 하 여 매개 변수를 추가할 수 있습니다. [AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 메서드.
예를 들어 다음 코드는 `PowerShell` 컴퓨터에서 실행 되는 이라는 모든 프로세스 목록을 가져옵니다.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

AddParameter 메서드를 반복 해 서 호출 하 여 추가 매개 변수를 추가할 수 있습니다.

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

또한, 매개 변수 이름 및 값의 사전은 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) 를 호출 하 여 추가할 수 있습니다.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

파이프라인의 끝에 문을 추가 하는 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 를 사용 하 여 일괄 처리를 시뮬레이션할 수 있습니다.
다음 코드는 이름이 인 실행 중인 프로세스 목록을 가져온 `PowerShell` 다음 실행 중인 서비스 목록을 가져옵니다.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

[System.object](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 메서드를 호출 하 여 기존 스크립트를 실행할 수 있습니다.
다음 예제에서는 스크립트를 파이프라인에 추가 하 고 실행 합니다.
이 예에서는 라는 폴더에 라는 스크립트가 이미 있다고 가정 `MyScript.ps1` `D:\PSScripts` 합니다.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

라는 부울 매개 변수를 사용 하는 AddScript 메서드의 버전도 있습니다 `useLocalScope` .
이 매개 변수를로 설정 하면 `true` 스크립트는 로컬 범위에서 실행 됩니다.
다음 코드에서는 로컬 범위에서 스크립트를 실행 합니다.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>사용자 지정 runspace 만들기

이전 예제에서 사용 된 기본 runspace는 모든 핵심 Windows PowerShell 명령을 로드 하지만 모든 명령의 지정 된 하위 집합만 로드 하는 사용자 지정 runspace를 만들 수 있습니다.
이 작업을 수행 하 여 성능을 향상 시키거나 (많은 수의 명령을 로드 하 여 성능이 저하 됨) 사용자가 작업을 수행 하는 기능을 제한할 수 있습니다.
제한 된 개수의 명령만 노출 하는 runspace를 제한 된 runspace 라고 합니다.
제한 된 runspace를 만들려면 [runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) 및 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 클래스를 사용 합니다.

### <a name="creating-an-initialsessionstate-object"></a>InitialSessionState 개체 만들기

사용자 지정 runspace를 만들려면 먼저 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체를 만들어야 합니다.
다음 예제에서는 기본 InitialSessionState 개체를 만든 후 [runspace. RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) 를 사용 하 여 runspace를 만듭니다.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Runspace 제한

이전 예제에서는 기본 제공 핵심 Windows PowerShell을 모두 로드 하는 기본 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체를 만들었습니다.
[System.Management.Automation.Runspaces.Iniinitialsessionstate.createdefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) 메서드를 호출 하 여 tialSessionState 스냅인의 명령만 로드 하는 InitialSessionState 개체를 만들 수도 있습니다.
더 제한 된 runspace를 만들려면 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) 메서드를 호출 하 여 빈 InitialSessionState 개체를 만든 다음 InitialSessionState에 명령을 추가 해야 합니다.

지정 하는 명령만 로드 하는 runspace를 사용 하면 성능이 크게 향상 됩니다.

[Runspace](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) 의 메서드를 사용 하 여 초기 세션 상태에 대 한 cmdlet을 정의 합니다.
다음 예에서는 빈 초기 세션 상태를 만든 다음 및 명령을 정의 하 고 `Get-Command` `Import-Module` 초기 세션 상태에 추가 합니다.
그런 다음 해당 초기 세션 상태에 의해 제한 되는 runspace를 만들고 해당 runspace에서 명령을 실행 합니다.

초기 세션 상태를 만듭니다.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

초기 세션 상태에 명령을 정의 하 고 추가 합니다.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Runspace를 만들고 엽니다.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

명령을 실행 하 고 결과를 표시 합니다.

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

실행 하는 경우이 코드의 출력은 다음과 같습니다.

```powershell
Get-Command
Import-Module
```

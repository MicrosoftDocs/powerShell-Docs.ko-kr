---
title: Windows PowerShell 호스트 빠른 시작 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: cc014487a680747ad59437052f79d4576154a1cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082552"
---
# <a name="windows-powershell-host-quickstart"></a>Windows PowerShell 호스트 빠른 시작

응용 프로그램에서 Windows PowerShell 호스트를 사용 하 여 [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) 클래스입니다. 이 클래스는 명령의 파이프라인 만들기 및 runspace에 명령을 실행 하 여 다음 메서드를 제공 합니다. 호스트 응용 프로그램을 만드는 가장 간단한 방법은 기본 runspace를 사용 하는 것입니다. 기본 runspace 모든 핵심 Windows PowerShell 명령이 포함 됩니다. Windows PowerShell 명령의 하위 집합만 노출 하도록 응용 프로그램을 원하는 경우 사용자 지정 runspace를 만들어야 합니다.

## <a name="using-the-default-runspace"></a>기본 runspace를 사용 하 여

를 시작 하려면에서는 기본 runspace를 사용 하 고의 메서드를 사용 합니다 [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) 파이프라인에 명령, 매개 변수, 문 및 스크립트를 추가 하는 클래스입니다.

### <a name="addcommand"></a>AddCommand

사용할 합니다 [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) 메서드는 [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) 파이프라인에 명령을 추가 하는 클래스입니다. 예를 들어 컴퓨터에서 실행 중인 프로세스 목록을 가져오려고 한다고 가정 합니다. 이 명령을 실행 하는 방법은 다음과 같습니다.

1. 만들기는 [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) 개체입니다.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. 실행 하려는 명령을 추가 합니다.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. 명령을 호출 합니다.

   ```csharp
   ps.Invoke();
   ```

호출 하는 경우는 [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) 메서드를 호출 하기 전에 두 번 이상 합니다 [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) 메서드, 결과 첫 번째 명령은 두 번째, 및 등으로 파이프 됩니다. 명령에는 이전 명령의 결과 파이프 하려면 호출 하 여 추가 합니다 [System.Management.Automation.Powershell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 대신 합니다.

### <a name="addparameter"></a>AddParameter

이전 예제에서는 단일 매개 변수 없이 명령을 실행합니다. 사용 하 여 명령에 매개 변수를 추가할 수는 [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 메서드 예를 들어, 다음 코드의 목록을 가져옵니다 모든 명명 된 프로세스 `PowerShell` 에서 실행 되는 컴퓨터입니다.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

호출 하 여 추가 매개 변수를 추가할 수 있습니다 [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 반복적으로 합니다.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

호출 하 여 매개 변수 이름 및 값의 사전을 추가할 수도 있습니다는 [System.Management.Automation.PowerShell.AddParameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) 메서드.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

사용 하 여 일괄 처리를 시뮬레이션할 수 있습니다 합니다 [System.Management.Automation.PowerShell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 는 추가 문을 다음 코드는 이름을 사용 하 여 실행 중인 프로세스 목록을 가져옵니다 파이프라인의 끝에 추가 하는 메서드 `PowerShell`, 한 다음 실행 중인 서비스 목록을 가져옵니다.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

호출 하 여 기존 스크립트를 실행할 수 있습니다 합니다 [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 메서드. 다음 예제에서는 파이프라인에 스크립트를 추가 하 고 실행 합니다. 이 예제에서는 라는 스크립트를 이미 있다고 가정 `MyScript.ps1` 라는 폴더에 `D:\PSScripts`입니다.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

버전을 [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 라는 부울 매개 변수를 갖는 메서드의 `useLocalScope`합니다. 이 매개 변수가 설정 된 경우 `true`, 다음 스크립트를 로컬 범위에서 실행 됩니다. 다음 코드를 로컬 범위에는 스크립트를 실행 합니다.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>사용자 지정 runspace 만들기

앞의 예제에 사용 되는 기본 runspace 핵심 Windows PowerShell 명령을 모두 로드 하는 동안에 모든 명령의 지정 된 하위 집합만 로드 하는 사용자 지정 runspace를 만들 수 있습니다. 성능 향상을 위해이 작업을 수행 하는 것이 좋습니다 (성능 저하는 많은 명령 로드), 또는 작업을 수행 하는 사용자의 기능을 제한 합니다. 제한 된 수의 명령 노출 하는 runspace가 제한 된 runspace를 라고 합니다. 사용 제한 된 runspace를 만들려면 합니다 [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) 하 고 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 클래스입니다.

### <a name="creating-an-initialsessionstate-object"></a>InitialSessionState 개체 만들기

Runspace를 만드는 사용자 지정을 먼저 만들어야 합니다는 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체입니다. 다음 예에서는 사용 된 [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) runspace를 만드는 기본값을 만든 후 [System.Management.Automation.Runspaces.InitialSessionState ](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체입니다.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>제한 된 runspace

기본값 이전 예에서 만들었습니다 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 모든 기본 제공 핵심 Windows PowerShell을 로드 하는 개체입니다. 에서는 호출할 수도 있습니다. 또한 합니다 [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) InitialSessionState 개체는 Microsoft.PowerShell.Core의 명령만 로드를 만드는 방법 스냅인입니다. 빈 더 제한 된 runspace를 만들려면 만들어야 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 를 호출 하 여 개체를 [ System.Management.Automation.Runspaces.InitialSessionState.Create*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) 메서드를 다음 명령에는 InitialSessionState을 추가 합니다.

지정 하는 명령만 로드 하는 runspace를 사용 하 여 성능이 크게 향상 됩니다.

메서드를 사용 합니다 [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) 초기 세션 상태에 대 한 cmdlet을 정의 하는 클래스입니다. 다음 예제에서는 빈 초기 세션 상태를 다음 정의 만들고 추가 합니다 `Get-Command` 및 `Import-Module` 초기 세션 상태에 명령 합니다. 그런 다음 해당 초기 세션 상태에 의해 제한 된 runspace 만들고 해당 runspace에서 명령을 실행 합니다.

초기 세션 상태를 만듭니다.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

정의 하 고 초기 세션 상태에 명령을 추가 합니다.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

만들고 runspace를 엽니다.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

명령을 실행 하 고 결과 표시 합니다.

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

를 실행 하는 경우이 코드의 출력 다음과 같이 표시 됩니다.

```powershell
Get-Command
Import-Module
```

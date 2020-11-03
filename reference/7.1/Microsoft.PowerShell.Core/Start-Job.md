---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 02133562cb0ecbc75fe64ca5406751b03af4bd9a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217001"
---
# Start-Job

## 개요
PowerShell 백그라운드 작업을 시작 합니다.

## SYNTAX

### ComputerName (기본값)

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### Build.definitionname

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [-WorkingDirectory <String>] [<CommonParameters>]
```

### FilePathComputerName

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### LiteralFilePathComputerName

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

## 설명

`Start-Job`Cmdlet은 로컬 컴퓨터에서 PowerShell 백그라운드 작업을 시작 합니다.

PowerShell 백그라운드 작업은 현재 세션과 상호 작용 하지 않고 명령을 실행 합니다. 백그라운드 작업을 시작 하면 작업을 완료 하는 데 오랜 시간이 소요 되는 경우에도 작업 개체가 즉시 반환 됩니다. 작업이 실행되는 동안 중단 없이 세션에서 작업을 계속할 수 있습니다.

작업 개체에는 작업에 대 한 유용한 정보가 포함 되어 있지만 작업 결과는 포함 되어 있지 않습니다.
작업이 완료 되 면 cmdlet을 사용 `Receive-Job` 하 여 작업의 결과를 가져옵니다. 백그라운드 작업에 대한 자세한 내용은 [about_Jobs](./About/about_Jobs.md)를 참조하세요.

원격 컴퓨터에서 백그라운드 작업을 실행 하려면 많은 cmdlet에서 사용할 수 있는 **AsJob** 매개 변수를 사용 하거나 cmdlet을 사용 `Invoke-Command` 하 여 `Start-Job` 원격 컴퓨터에서 명령을 실행 합니다. 자세한 내용은 [about_Remote_Jobs](./About/about_Remote_Jobs.md)를 참조 하세요.

PowerShell 3.0부터는 `Start-Job` 예약 된 작업과 같은 사용자 지정 작업 유형의 인스턴스를 시작할 수 있습니다. 를 사용 하 여 사용자 지정 형식으로 작업을 시작 하는 방법에 대 한 자세한 내용은 `Start-Job` 작업 유형 기능에 대 한 도움말 문서를 참조 하세요.

PowerShell 6.0부터 앰퍼샌드 () 백그라운드 연산자를 사용 하 여 작업을 시작할 수 있습니다 `&` . 백그라운드 연산자의 기능은와 비슷합니다 `Start-Job` . 작업을 시작 하는 두 가지 방법 모두 **Psremo로 작업** 작업 개체를 만듭니다. 앰퍼샌드 ()를 사용 하는 방법에 대 한 자세한 내용은 `&` [about_Operators](./about/about_operators.md#background-operator-)를 참조 하세요.

PowerShell 7에는 백그라운드 작업의 초기 작업 디렉터리를 지정 하는 **WorkingDirectory** 매개 변수가 도입 되었습니다. 매개 변수가 지정 되지 않은 경우는 기본적으로 `Start-Job` 작업을 시작한 호출자의 현재 작업 디렉터리입니다.

> [!NOTE]
> Powershell `Start-Job` Azure Functions와 같은 다른 응용 프로그램에서 powershell을 호스팅하는 시나리오에서는를 사용 하 여 out-of-process 백그라운드 작업을 만들 수 없습니다.
>
> 이것은 `Start-Job` `pwsh` 에서 사용할 수 있는 실행 파일을 사용 하 여 out-of-process 백그라운드 작업을 시작 하기 때문에 의도 된 것 `$PSHOME` 이지만 응용 프로그램이 powershell을 호스트 하는 경우 powershell NuGet SDK 패키지를 직접 사용 하는 것 이며 `pwsh` 함께 제공 되지 않기 때문입니다.
>
> 해당 시나리오의 대체는 `Start-ThreadJob` 모듈 **[threadjob](https://www.powershellgallery.com/packages/ThreadJob)** 에서 가져온 것입니다.

## 예제

### 예제 1: 백그라운드 작업 시작

이 예제에서는 로컬 컴퓨터에서 실행 되는 백그라운드 작업을 시작 합니다.

```powershell
Start-Job -ScriptBlock { Get-Process -Name pwsh }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name pwsh
```

`Start-Job`**ScriptBlock** 매개 변수를 사용 하 여 `Get-Process` 백그라운드 작업으로 실행 합니다. **Name** 매개 변수는 PowerShell 프로세스를 찾도록 지정 합니다 `pwsh` . 작업 정보가 표시 되 고 백그라운드에서 작업이 실행 되는 동안 PowerShell에서 프롬프트로 돌아갑니다.

작업의 출력을 보려면 cmdlet을 사용 `Receive-Job` 합니다. 예들 들어 `Receive-Job -Id 1`입니다.

### 예 2: background 연산자를 사용 하 여 백그라운드 작업 시작

이 예에서는 앰퍼샌드 ( `&` ) 백그라운드 연산자를 사용 하 여 로컬 컴퓨터에서 백그라운드 작업을 시작 합니다. 작업은 예제 1과 동일한 결과를 가져옵니다 `Start-Job` .

```powershell
Get-Process -Name pwsh &
```

```Output
Id    Name   PSJobTypeName   State       HasMoreData     Location      Command
--    ----   -------------   -----       -----------     --------      -------
5     Job5   BackgroundJob   Running     True            localhost     Microsoft.PowerShell.Man...
```

`Get-Process`**Name** 매개 변수를 사용 하 여 PowerShell 프로세스를 지정 `pwsh` 합니다. 앰퍼샌드 ( `&` )는 명령을 백그라운드 작업으로 실행 합니다. 작업 정보가 표시 되 고 백그라운드에서 작업이 실행 되는 동안 PowerShell에서 프롬프트로 돌아갑니다.

작업의 출력을 보려면 cmdlet을 사용 `Receive-Job` 합니다. 예들 들어 `Receive-Job -Id 5`입니다.

### 예 3: Invoke-Command을 사용 하 여 작업 시작

이 예제에서는 여러 컴퓨터에서 작업을 실행 합니다. 작업은 변수에 저장 되며 PowerShell 명령줄에서 변수 이름을 사용 하 여 실행 됩니다.

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

를 사용 하는 작업 `Invoke-Command` 은 변수에 생성 되어 저장 됩니다 `$jobWRM` . `Invoke-Command`**ComputerName** 매개 변수를 사용 하 여 작업이 실행 되는 컴퓨터를 지정 합니다. `Get-Content` 파일에서 서버 이름을 가져옵니다 `C:\Servers.txt` .

**ScriptBlock** 매개 변수는 `Get-Service` **WinRM** 서비스를 가져오는 명령을 지정 합니다. **JobName** 매개 변수는 작업의 친숙 한 이름 ( **WinRM** )을 지정 합니다. **ThrottleLimit** 매개 변수는 동시 명령 수를 16으로 제한 합니다. **AsJob** 매개 변수는 서버에서 명령을 실행 하는 백그라운드 작업을 시작 합니다.

### 예제 4: 작업 정보 가져오기

이 예에서는 작업에 대 한 정보를 가져오고 로컬 컴퓨터에서 실행 된 완료 된 작업의 결과를 표시 합니다.

```powershell
$j = Start-Job -ScriptBlock { Get-WinEvent -Log System } -Credential Domain01\User01
$j | Select-Object -Property *
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-WinEvent -Log System
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : 27ce3fd9-40ed-488a-99e5-679cd91b9dd3
Id            : 18
Name          : Job18
ChildJobs     : {Job19}
PSBeginTime   : 8/8/2019 14:41:57
PSEndTime     : 8/8/2019 14:42:07
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

`Start-Job` 는 **ScriptBlock** 매개 변수를 사용 하 여 `Get-WinEvent` **시스템** 로그를 가져오도록를 지정 하는 명령을 실행 합니다. **Credential** 매개 변수는 컴퓨터에서 작업을 실행할 수 있는 권한이 있는 도메인 사용자 계정을 지정 합니다. 작업 개체는 변수에 저장 됩니다 `$j` .

변수의 개체는 `$j` 파이프라인에서로 전송 됩니다 `Select-Object` . **Property** 매개 변수는 `*` 모든 작업 개체의 속성을 표시 하는 별표 ()를 지정 합니다.

### 예 5: 백그라운드 작업으로 스크립트 실행

이 예에서는 로컬 컴퓨터의 스크립트가 백그라운드 작업으로 실행 됩니다.

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

`Start-Job`**FilePath** 매개 변수를 사용 하 여 로컬 컴퓨터에 저장 된 스크립트 파일을 지정 합니다.

### 예제 6: 백그라운드 작업을 사용 하 여 프로세스 가져오기

이 예제에서는 백그라운드 작업을 사용 하 여 지정 된 프로세스를 이름으로 가져옵니다.

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

`Start-Job`**name** 매개 변수를 사용 하 여 친숙 한 작업 이름 **pshelljob** 을 지정 합니다. **ScriptBlock** 매개 변수는 `Get-Process` 이름이 **PowerShell** 인 프로세스를 가져오도록 지정 합니다.

### 예 7: 백그라운드 작업을 사용 하 여 데이터 수집 및 저장

이 예에서는 많은 양의 지도 데이터를 수집 하 여 파일에 저장 하는 작업을 시작 `.tif` 합니다.

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif }
```

`Start-Job`**name** 매개 변수를 사용 하 여 친숙 한 작업 이름인 **GetMappingFiles** 를 지정 합니다. **또한 initializationscript** 매개 변수는 **mapfunctions** 모듈을 가져오는 스크립트 블록을 실행 합니다. **ScriptBlock** 매개 변수는 `Get-Map` `Set-Content` **Path** 매개 변수에서 지정한 위치에 데이터를 실행 하 고 저장 합니다.

### 예 8: 백그라운드 작업에 입력 전달

이 예에서는 자동 변수를 사용 하 여 `$input` 입력 개체를 처리 합니다. `Receive-Job`를 사용 하 여 작업의 출력을 볼 수 있습니다.

```powershell
Start-Job -ScriptBlock { Get-Content $input } -InputObject "C:\Servers.txt"
Receive-Job -Name Job45 -Keep
```

```Output
Server01
Server02
Server03
Server04
```

`Start-Job`**ScriptBlock** 매개 변수를 사용 하 여 `Get-Content` `$input` 자동 변수와 함께 실행 합니다. `$input`변수는 **InputObject** 매개 변수에서 개체를 가져옵니다. `Receive-Job`**Name** 매개 변수를 사용 하 여 작업을 지정 하 고 결과를 출력 합니다. **Keep** 매개 변수는 PowerShell 세션 중에 다시 볼 수 있도록 작업 출력을 저장 합니다.

### 예 9: 백그라운드 작업에 대 한 작업 디렉터리 설정

**WorkingDirectory** 를 사용 하면 스크립트를 실행 하거나 파일을 열 수 있는 작업에 대 한 대체 디렉터리를 지정할 수 있습니다. 이 예제에서 백그라운드 작업은 현재 디렉터리 위치와 다른 작업 디렉터리를 지정 합니다.

```
PS C:\Test> Start-Job -WorkingDirectory C:\Test\Scripts { $PWD } | Receive-Job -AutoRemoveJob -Wait

Path
----
C:\Test\Scripts
```

이 예제의 현재 작업 디렉터리는 `C:\Test` 입니다. `Start-Job`**WorkingDirectory** 매개 변수를 사용 하 여 작업의 작업 디렉터리를 지정 합니다. **ScriptBlock** 매개 변수는 `$PWD` 를 사용 하 여 작업의 작업 디렉터리를 표시 합니다. `Receive-Job` 백그라운드 작업의 출력을 표시 합니다.
**AutoRemoveJob** 는 작업을 삭제 하 고 **Wait** 는 모든 결과가 수신 될 때까지 명령 프롬프트를 표시 하지 않습니다.

### 예 10: ArgumentList 매개 변수를 사용 하 여 배열 지정

이 예제에서는 **Argumentlist** 매개 변수를 사용 하 여 인수의 배열을 지정 합니다. 배열은 쉼표로 구분 된 프로세스 이름 목록입니다.

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

`Start-Job`Cmdlet은 **ScriptBlock** 매개 변수를 사용 하 여 명령을 실행 합니다. `Get-Process`**Name** 매개 변수를 사용 하 여 자동 변수를 지정 합니다 `$args` . **Argumentlist** 매개 변수는 프로세스 이름 배열을에 전달 `$args` 합니다. Powershell, pwsh 및 notepad 프로세스 이름은 로컬 컴퓨터에서 실행 되는 프로세스입니다.

작업의 출력을 보려면 cmdlet을 사용 `Receive-Job` 합니다. 예들 들어 `Receive-Job -Id 1`입니다.

### 예 11: Windows PowerShell 5.1에서 작업 실행

이 예제에서는 값이 **5.1** 인 **PSVersion** 매개 변수를 사용 하 여 Windows PowerShell 5.1 세션에서 작업을 실행 합니다.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Patch  PreReleaseLabel BuildLabel
-----  -----  -----  --------------- ----------
7      0      0      rc.1
```

```powershell
$job = Start-Job { $PSVersionTable.PSVersion } -PSVersion 5.1
Receive-Job $job
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  3383
```

## PARAMETERS

### -ArgumentList

**FilePath** 매개 변수로 지정 된 스크립트 또는 **ScriptBlock** 매개 변수를 사용 하 여 지정 된 명령에 대 한 인수 또는 매개 변수 값의 배열을 지정 합니다.

인수는 **Argumentlist** 에 단일 차원 배열 인수로 전달 해야 합니다. 예를 들어 쉼표로 구분 된 목록입니다. **Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -인증

사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- 기본값
- Basic
- Credssp
- 다이제스트
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

기본값은 Default입니다.

CredSSP 인증은 windows Vista, Windows Server 2008 이상 버전의 Windows 운영 체제 에서만 사용할 수 있습니다.

이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하십시오.

> [!CAUTION]
> 사용자의 자격 증명이 인증을 위해 원격 컴퓨터로 전달되는 CredSSP(자격 증명 보안 지원 공급자) 인증은 둘 이상의 리소스에서 인증이 필요한 명령(예: 원격 네트워크 공유 액세스)에 사용됩니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다. **Credential** 매개 변수를 지정 하지 않으면 명령은 현재 사용자의 자격 증명을 사용 합니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefinitionName

이 cmdlet이 시작 하는 작업의 정의 이름을 지정 합니다. 이 매개 변수를 사용하여 예약된 작업과 같이 정의 이름이 있는 사용자 지정 작업 유형을 시작합니다.

`Start-Job`를 사용 하 여 예약 된 작업의 인스턴스를 시작 하면 작업 트리거 또는 작업 옵션에 관계 없이 작업이 즉시 시작 됩니다. 결과 작업 인스턴스는 예약 된 작업 이지만 트리거된 예약 된 작업 처럼 디스크에 저장 되지 않습니다. 의 **Argumentlist** 매개 변수를 사용 `Start-Job` 하 여 예약 된 작업에서 실행 되는 스크립트의 매개 변수에 대 한 값을 제공할 수 없습니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefinitionPath

이 cmdlet이 시작 되는 작업 정의의 경로를 지정 합니다. 정의 경로를 입력합니다. **Definitionpath** 및 **definitionpath** 매개 변수의 값 연결은 작업 정의의 정규화 된 경로입니다. 이 매개 변수를 사용하여 예약된 작업과 같이 정의 경로가 있는 사용자 지정 작업 유형을 시작합니다.

예약 된 작업의 경우 **Definitionpath** 매개 변수의 값은 `$home\AppData\Local\Windows\PowerShell\ScheduledJob` 입니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

백그라운드 작업으로 실행 되는 로컬 스크립트를 지정 합니다 `Start-Job` . 스크립트의 경로와 파일 이름을 입력 하거나 파이프라인을 사용 하 여 스크립트 경로를로 보냅니다 `Start-Job` . 스크립트는 로컬 컴퓨터에 있거나 로컬 컴퓨터에서 액세스할 수 있는 폴더에 있어야 합니다.

이 매개 변수를 사용 하는 경우 PowerShell은 지정 된 스크립트 파일의 내용을 스크립트 블록으로 변환 하 고 스크립트 블록을 백그라운드 작업으로 실행 합니다.

```yaml
Type: System.String
Parameter Sets: FilePathComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -또한 initializationscript

작업을 시작하기 전에 실행되는 명령을 지정합니다. 스크립트 블록을 만들려면 명령을 중괄호 ()로 묶습니다 `{}` .

이 매개 변수를 사용하여 작업이 실행되는 세션을 준비할 수 있습니다. 예를 들어 이 매개 변수를 사용하여 함수, 스냅인 및 모듈을 세션에 추가할 수 있습니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

명령에 대한 입력을 지정합니다. 개체가 포함된 변수를 입력하거나 개체를 생성하는 명령 또는 식을 입력하세요.

**ScriptBlock** 매개 변수 값에서 `$input` 자동 변수를 사용 하 여 입력 개체를 나타냅니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

이 cmdlet이 백그라운드 작업으로 실행 되는 로컬 스크립트를 지정 합니다. 로컬 컴퓨터에서 스크립트의 경로를 입력 합니다.

`Start-Job`**LiteralPath** 매개 변수의 값을 입력 된 대로 정확 하 게 사용 합니다. 어떠한 문자도 와일드카드 문자로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

새 작업의 이름을 지정합니다. 이 이름을 사용 하 여 cmdlet과 같은 다른 작업 cmdlet에 대 한 작업을 식별할 수 있습니다 `Stop-Job` .

기본 이름은 이며 `Job#` , 여기서 `#` 은 각 작업에 대해 증가 하는 서 수입니다.

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSVersion

작업을 실행 하는 데 사용할 PowerShell 버전을 지정 합니다.
**PSVersion** 의 값이 **5.1** 인 경우 작업이 Windows PowerShell 5.1 세션에서 실행 됩니다.
다른 값의 경우에는 현재 버전의 PowerShell을 사용 하 여 작업이 실행 됩니다.

이 매개 변수는 PowerShell 7에서 추가 되었으며 Windows 에서만 작동 합니다.

```yaml
Type: System.Version
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -체제가 있어도 runas32

PowerShell 7부터 **체제가 있어도 runas32** 매개 변수는 64 비트 PowerShell ()에서 작동 하지 않습니다 `pwsh` .
**체제가 있어도 runas32** 이 64 비트 PowerShell에 지정 된 경우에서 `Start-Job` 종료 예외 오류를 throw 합니다.
체제가 있어도 runas32를 사용 하 여 32 비트 PowerShell ( `pwsh` ) 프로세스 **RunAs32** 를 시작 하려면 32 비트 powershell이 설치 되어 있어야 합니다.

32 비트 PowerShell에서 **체제가 있어도 runas32** 은 64 비트 운영 체제 에서도 강제로 32 비트 프로세스에서 작업을 실행 하도록 합니다.

64 비트 버전의 Windows 7 및 Windows Server 2008 r 2에서 `Start-Job` 명령에 **체제가 있어도 runas32** 매개 변수가 포함 된 경우 **Credential** 매개 변수를 사용 하 여 다른 사용자의 자격 증명을 지정할 수 없습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

백그라운드 작업에서 실행할 명령을 지정합니다. 스크립트 블록을 만들려면 명령을 중괄호 ()로 묶습니다 `{}` . `$input`자동 변수를 사용 하 여 **InputObject** 매개 변수의 값에 액세스 합니다. 이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type

에서 시작한 작업의 사용자 지정 형식을 지정 합니다 `Start-Job` . 사용자 지정 작업 유형 이름(예: 예약된 작업의 경우 PSScheduledJob 또는 워크플로 작업의 경우 PSWorkflowJob)을 입력합니다. 이 매개 변수는 표준 백그라운드 작업에 유효 하지 않습니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkingDirectory

백그라운드 작업의 초기 작업 디렉터리를 지정 합니다. 매개 변수가 지정 되지 않은 경우 작업은 기본 위치에서 실행 됩니다. 기본 위치는 작업을 시작한 호출자의 현재 작업 디렉터리입니다.

이 매개 변수는 PowerShell 7에서 도입 되었습니다.

 ```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $HOME on Unix (macOS, Linux) and $HOME\Documents on Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

파이프라인을 사용 하 여 **name** 속성이 있는 개체를 **name** 매개 변수로 보낼 수 있습니다. 예를 들어, **FileInfo** 개체를에서로 파이프라인 할 수 있습니다 `Get-ChildItem` `Start-Job` .

## 출력

### System.web. a p.

`Start-Job` 시작 된 작업을 나타내는 **Psremotingjob** 개체를 반환 합니다.

## 참고

백그라운드에서 실행 하려면는 `Start-Job` 현재 세션에서 자체 세션으로 실행 됩니다. Cmdlet을 사용 `Invoke-Command` 하 여 `Start-Job` 원격 컴퓨터의 세션에서 명령을 실행할 경우는 `Start-Job` 원격 세션의 세션에서 실행 됩니다.

## 관련 링크

[about_Arrays](./about/about_arrays.md)

[about_Automatic_Variables](./about/about_automatic_variables.md)

[about_Jobs](./About/about_Jobs.md)

[about_Job_Details](./About/about_Job_Details.md)

[about_Remote_Jobs](./About/about_Remote_Jobs.md)

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)

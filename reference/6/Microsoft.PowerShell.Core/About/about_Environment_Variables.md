---
description: PowerShell에서 Windows 환경 변수에 액세스 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Environment_Variables
ms.openlocfilehash: 2a477c9e343be2c4e26096fe1a0a73544b5e91bf
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221682"
---
# <a name="about-environment-variables"></a>환경 변수 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 Windows 환경 변수에 액세스 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

환경 변수는 운영 체제 환경에 대 한 정보를 저장 합니다. 이 정보에는 운영 체제 경로, 운영 체제에서 사용 하는 프로세서 수 및 임시 폴더의 위치와 같은 정보가 포함 됩니다.

환경 변수는 운영 체제 및 기타 프로그램에서 사용 하는 데이터를 저장 합니다. 예를 `WINDIR` 들어 환경 변수는 Windows 설치 디렉터리의 위치를 포함 합니다. 프로그램은이 변수의 값을 쿼리하여 Windows 운영 체제 파일이 있는 위치를 확인할 수 있습니다.

PowerShell은 지원 되는 운영 체제 플랫폼에서 환경 변수를 액세스 하 고 관리할 수 있습니다. PowerShell 환경 공급자는 환경 변수를 쉽게 확인 하 고 변경할 수 있도록 하 여이 프로세스를 간소화 합니다.

PowerShell의 다른 변수와 달리 환경 변수는 자식 프로세스 (예: 로컬 백그라운드 작업 및 모듈 멤버가 실행 되는 세션)에서 상속 됩니다. 이렇게 하면 환경 변수가 부모 및 자식 프로세스에 필요한 값을 저장 하는 데 적합 합니다.

## <a name="using-and-changing-environment-variables"></a>환경 변수 사용 및 변경

Windows에서는 환경 변수를 다음과 같은 세 가지 범위로 정의할 수 있습니다.

- 컴퓨터 (또는 시스템) 범위
- 사용자 범위
- 프로세스 범위

_프로세스_ 범위는 현재 프로세스 또는 PowerShell 세션에서 사용할 수 있는 환경 변수를 포함 합니다. 이 변수 목록은 부모 프로세스에서 상속 되며 _컴퓨터_ 및 _사용자_ 범위의 변수에 의해 생성 됩니다. Unix 기반 플랫폼에는 _프로세스_ 범위만 있습니다.

환경 공급자와 함께 변수 구문을 사용 하 여 cmdlet을 사용 하지 않고 환경 변수의 값을 표시 하 고 변경할 수 있습니다. 환경 변수의 값을 표시 하려면 다음 구문을 사용 합니다.

```
$Env:<variable-name>
```

예를 들어 환경 변수의 값을 표시 하려면 `WINDIR` PowerShell 명령 프롬프트에서 다음 명령을 입력 합니다.

```powershell
$Env:windir
```

이 구문에서 달러 기호 ()는 `$` 변수를 나타내고 drive name ()은 `Env:` 환경 변수와 변수 이름 ()을 나타냅니다 `windir` .

PowerShell에서 환경 변수를 변경 하는 경우 변경 내용은 현재 세션에만 영향을 줍니다. 이 동작은 `Set` Windows 명령 셸에서 명령의 동작과 비슷하며 `Setenv` UNIX 기반 환경의 명령입니다. 컴퓨터 또는 사용자 범위에서 값을 변경 하려면 **system.object** 클래스의 메서드를 사용 해야 합니다.

컴퓨터 범위 변수를 변경 하려면에도 권한이 있어야 합니다. 충분 한 권한이 없는 상태에서 값을 변경 하려고 하면 명령이 실패 하 고 PowerShell에서 오류가 표시 됩니다.

다음 구문을 사용 하 여 cmdlet을 사용 하지 않고 변수 값을 변경할 수 있습니다.

```powershell
$Env:<variable-name> = "<new-value>"
```

예를 들어 `;c:\temp` 환경 변수 값에를 추가 하려면 `Path` 다음 구문을 사용 합니다.

```powershell
$Env:Path += ";c:\temp"
```

Linux 또는 MacOS에서 명령의 콜론 ( `:` )은 목록에서 앞에 나오는 경로와 새 경로를 분리 합니다.

```powershell
$Env:PATH += ":/usr/local/temp"
```

항목 cmdlet (예:, 및)을 사용 `Set-Item` `Remove-Item` `Copy-Item` 하 여 환경 변수 값을 변경할 수도 있습니다. 예를 들어 cmdlet을 사용 하 여 `Set-Item` `;c:\temp` 환경 변수 값에 추가 하려면 `Path` 다음 구문을 사용 합니다.

```powershell
Set-Item -Path Env:Path -Value ($Env:Path + ";C:\Temp")
```

이 명령에서 값은 단위로 해석 되도록 괄호로 묶여 있습니다.

## <a name="environment-variables-that-store-preferences"></a>기본 설정을 저장 하는 환경 변수

PowerShell 기능은 환경 변수를 사용 하 여 사용자 기본 설정을 저장할 수 있습니다.
이러한 변수는 기본 설정 변수 처럼 작동 하지만 생성 된 세션의 자식 세션에서 상속 됩니다. 기본 설정 변수에 대 한 자세한 내용은 [about_preference_variables](about_Preference_Variables.md)를 참조 하세요.

기본 설정을 저장 하는 환경 변수는 다음과 같습니다.

- PSExecutionPolicyPreference

  현재 세션에 대 한 실행 정책 집합을 저장 합니다. 이 환경 변수는 단일 세션에 대 한 실행 정책을 설정 하는 경우에만 존재 합니다.
  두 가지 방법으로이 작업을 수행할 수 있습니다.

  - **Set-executionpolicy** 매개 변수를 사용 하 여 명령줄에서 세션을 시작 하 여 세션에 대 한 실행 정책을 설정 합니다.

  - `Set-ExecutionPolicy` cmdlet을 사용합니다. 값이 "Process" 인 Scope 매개 변수를 사용 합니다.

    자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조하세요.

- PSModuleAnalysisCachePath

  PowerShell에서는 모듈 및 해당 cmdlet에 대 한 데이터를 캐시 하는 데 사용 되는 파일을 제어할 수 있습니다. 명령을 검색 하는 동안 시작할 때 캐시를 읽고 모듈을 가져온 후 백그라운드 스레드에 기록 합니다.

  캐시의 기본 위치는 다음과 같습니다.

  - Windows PowerShell 5.1: `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`
  - PowerShell 6.0 이상: `$env:LOCALAPPDATA\Microsoft\PowerShell`
  - 비 Windows 기본값: `~/.cache/powershell`

  캐시의 기본 파일 이름은 `ModuleAnalysisCache` 입니다. PowerShell 인스턴스를 여러 개 설치한 경우 파일 이름에는 설치 당 고유한 파일 이름이 있도록 16 진수 접미사가 포함 됩니다.

  > [!NOTE]
  > 명령 검색이 제대로 작동 하지 않는 경우 (예: Intellisense에 존재 하지 않는 명령이 표시 되는 경우) 캐시 파일을 삭제할 수 있습니다. 다음에 PowerShell을 시작할 때 캐시가 다시 만들어집니다.

  캐시의 기본 위치를 변경 하려면 PowerShell을 시작 하기 전에 환경 변수를 설정 합니다. 이 환경 변수에 대 한 변경 내용은 자식 프로세스에만 영향을 줍니다. PowerShell이 파일을 만들고 쓸 수 있는 전체 경로(파일 이름 포함)를 값으로 지정해야 합니다.

  파일 캐시를 사용하지 않도록 설정하려면 이 값을 다음과 같은 잘못된 위치로 설정합니다.

  ```powershell
  # `NUL` here is a special device on Windows that cannot be written to,
  # on non-Windows you would use `/dev/null`
  $env:PSModuleAnalysisCachePath = 'NUL'
  ```

  이렇게 하면 **NUL** 장치에 대 한 경로가 설정 됩니다. PowerShell에서 경로에 쓸 수 없지만 오류가 반환 되지 않습니다. 추적 프로그램을 사용 하 여 보고 된 오류를 볼 수 있습니다.

  ```powershell
  Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
  ```

- PSDisableModuleAnalysisCacheCleanup

  모듈 분석 캐시를 작성할 때 PowerShell은 불필요 하 게 큰 캐시를 방지 하기 위해 더 이상 존재 하지 않는 모듈을 확인 합니다. 이러한 검사를 사용 하지 않는 것이 좋습니다 .이 경우이 환경 변수 값을로 설정 하 여 해제할 수 있습니다 `1` .

  이 환경 변수를 설정 하면 현재 프로세스에 즉시 적용 됩니다.

- PSModulePath

  `$env:PSModulePath`환경 변수는 모듈 및 리소스를 찾기 위해 검색 되는 폴더 위치 목록을 포함 합니다.

  기본적으로에 할당 되는 유효 위치는 `$env:PSModulePath` 다음과 같습니다.

  - 시스템 전체 위치: 이러한 폴더에는 PowerShell과 함께 제공 되는 모듈이 포함 되어 있습니다. 모듈은 위치에 저장 됩니다 `$PSHOME\Modules` . 또한 Windows 관리 모듈이 설치 되는 위치입니다.

  - 사용자가 설치한 모듈: 사용자가 설치 하는 모듈입니다.
    `Install-Module` 에는 현재 사용자 또는 모든 사용자에 대해 모듈이 설치 되어 있는지 여부를 지정할 수 있는 **범위** 매개 변수가 있습니다. 자세한 내용은 [모듈 설치](xref:PowerShellGet.Install-Module)를 참조 하세요.

    - Windows에서 사용자 관련 **CurrentUser** 범위의 위치는 `$HOME\Documents\PowerShell\Modules` 폴더입니다. **AllUsers** 범위의 위치는 `$env:ProgramFiles\PowerShell\Modules` 입니다.
    - 비 Windows 시스템에서 사용자 관련 **CurrentUser** 범위의 위치는 `$HOME/.local/share/powershell/Modules` 폴더입니다. **AllUsers** 범위의 위치는 `/usr/local/share/powershell/Modules` 입니다.

  또한 Program Files 디렉터리와 같은 다른 디렉터리에 모듈을 설치 하는 설치 프로그램은 해당 위치를의 값에 추가할 수 있습니다 `$env:PSModulePath` .

  자세한 내용은 [about_PSModulePath](about_PSModulePath.md)를 참조 하세요.

## <a name="managing-environment-variables"></a>환경 변수 관리

PowerShell은 환경 변수를 관리 하는 여러 가지 방법을 제공 합니다.

- 환경 공급자 드라이브
- 항목 cmdlet
- .NET **System. Environment** 클래스
- Windows에서 시스템 제어판

### <a name="using-the-environment-provider"></a>환경 공급자 사용

각 환경 변수는 **DictionaryEntry** 클래스의 인스턴스로 표시 됩니다. 각 **DictionaryEntry** 개체에서 환경 변수의 이름은 사전 키입니다. 변수 값은 사전 값입니다.

PowerShell에서 환경 변수를 나타내는 개체의 속성 및 메서드를 표시 하려면 cmdlet을 사용 합니다 `Get-Member` . 예를 들어 드라이브의 모든 개체에 대 한 메서드 및 속성을 표시 하려면 `Env:` 다음을 입력 합니다.

```powershell
Get-Item -Path Env:* | Get-Member
```

PowerShell 환경 공급자를 통해 PowerShell 드라이브 (드라이브)의 환경 변수에 액세스할 수 있습니다 `Env:` . 이 드라이브는 파일 시스템 드라이브와 매우 비슷합니다. 드라이브로 이동 하려면 `Env:` 다음을 입력 합니다.

```powershell
Set-Location Env:
```

콘텐츠 cmdlet을 사용 하 여 환경 변수 값을 가져오거나 설정 합니다.

```powershell
PS Env:\> Set-Content -Path Test -Value 'Test value'
PS Env:\> Get-Content -Path Test
Test value
```

다른 PowerShell 드라이브에서 드라이브의 환경 변수를 볼 수 있으며 `Env:` , `Env:` 드라이브로 이동 하 여 환경 변수를 확인 하 고 변경할 수 있습니다.

### <a name="using-item-cmdlets"></a>항목 cmdlet 사용

환경 변수를 참조 하는 경우 `Env:` 드라이브 이름 뒤에 변수 이름을 입력 합니다. 예를 들어 환경 변수의 값을 표시 하려면 `COMPUTERNAME` 다음을 입력 합니다.

```powershell
Get-ChildItem Env:Computername
```

모든 환경 변수의 값을 표시 하려면 다음을 입력 합니다.

```powershell
Get-ChildItem Env:
```

환경 변수에는 자식 항목이 없으므로 및의 출력은 `Get-Item` `Get-ChildItem` 동일 합니다.

기본적으로 PowerShell은 검색 되는 순서 대로 환경 변수를 표시 합니다. 환경 변수 목록을 변수 이름별로 정렬 하려면 명령의 출력을 `Get-ChildItem` cmdlet으로 파이프 합니다 `Sort-Object` . 예를 들어 모든 PowerShell 드라이브에서 다음을 입력 합니다.

```powershell
Get-ChildItem Env: | Sort Name
```

`Env:`Cmdlet을 사용 하 여 드라이브로 이동할 수도 있습니다 `Set-Location` .

```powershell
Set-Location Env:
```

드라이브에 있는 경우 `Env:` `Env:` 경로에서 드라이브 이름을 생략할 수 있습니다. 예를 들어 모든 환경 변수를 표시 하려면 다음을 입력 합니다.

```powershell
PS Env:\> Get-ChildItem
```

`COMPUTERNAME`드라이브 내에서 변수의 값을 표시 하려면 `Env:` 다음을 입력 합니다.

```powershell
PS Env:\> Get-ChildItem ComputerName
```

### <a name="saving-changes-to-environment-variables"></a>환경 변수에 대 한 변경 내용 저장

Windows에서 환경 변수를 영구적으로 변경 하려면 시스템 제어판을 사용 합니다. **고급 시스템 설정** 을 선택 합니다. **고급** 탭에서 **환경 변수 ...** 를 클릭 합니다. **사용자** 및 **시스템** (컴퓨터) 범위에서 기존 환경 변수를 추가 하거나 편집할 수 있습니다. Windows는 세션 및 시스템 다시 시작 간에 유지 되도록 레지스트리에 이러한 값을 기록 합니다.

또는 PowerShell 프로필에서 환경 변수를 추가 하거나 변경할 수 있습니다. 이 방법은 모든 버전의 PowerShell에서 지원 되는 플랫폼에 대해 작동 합니다.

### <a name="using-systemenvironment-methods"></a>System.object 메서드 사용

**System.object** 클래스는 변수의 범위를 지정할 수 있는 **GetEnvironmentVariable** 및 **SetEnvironmentVariable** 메서드를 제공 합니다.

다음 예제에서는 **GetEnvironmentVariable** 메서드를 사용 하 여의 컴퓨터 설정을 가져오고 `PSModulePath` **SetEnvironmentVariable** 메서드를 사용 하 여 `C:\Program Files\Fabrikam\Modules` 값에 경로를 추가 합니다.

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable("PSModulePath", $newpath, 'Machine')
```

**System.object** 클래스의 메서드에 대 한 자세한 내용은 [환경 메서드](/dotnet/api/system.environment)를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [환경 (공급자)](../About/about_Environment_Provider.md)
- [about_Modules](about_Modules.md)

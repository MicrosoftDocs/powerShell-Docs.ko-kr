---
description: PowerShell에 대 한 구성 파일로, 레지스트리 구성을 대체 합니다.
Locale: en-US
ms.date: 03/12/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Config
ms.openlocfilehash: 1ba0472e52ff6fc810a0b357fb7fa60c008d0de2
ms.sourcegitcommit: 2560a122fe3a85ea762c3af6f1cba9e237512b2d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103412947"
---
# <a name="about-powershell-config"></a>PowerShell 구성 정보

## <a name="short-description"></a>간단한 설명
레지스트리 구성을 대체 하는 PowerShell Core에 대 한 구성 파일입니다.

## <a name="long-description"></a>자세한 설명

이 `powershell.config.json` 파일에는 PowerShell Core에 대 한 구성 설정이 포함 되어 있습니다. PowerShell은 시작할 때이 구성을 로드 합니다. 설정은 런타임에 수정할 수도 있습니다. 이전에는 이러한 설정이 PowerShell 용 Windows 레지스트리에 저장 되었지만 이제 macOS 및 Linux에서 구성을 사용 하기 위해 파일에 포함 되어 있습니다.

> [!WARNING]
> 구성 파일의 인식할 수 없는 키 또는 잘못 된 값은 자동으로 무시 됩니다. 파일에 `powershell.config.json` 잘못 된 JSON이 포함 되어 있으면 PowerShell에서 대화형 세션을 시작할 수 없습니다. 이 경우 구성 파일을 수정 해야 합니다.

### <a name="allusers-shared-configuration"></a>AllUsers (공유) 구성

`powershell.config.json`디렉터리의 파일은 `$PSHOME` 해당 powershell core 설치에서 실행 되는 모든 powershell core 세션의 구성을 정의 합니다.

> [!NOTE]
> `$PSHOME`위치는 실행 중인 System.Management.Automation.dll 어셈블리와 동일한 디렉터리로 정의 됩니다. 이는 호스트 된 PowerShell SDK 인스턴스에도 적용 됩니다.

### <a name="currentuser-per-user-configurations"></a>CurrentUser (사용자 단위) 구성

사용자 범위 구성 디렉터리에 파일을 배치 하 여 사용자 별로 PowerShell을 구성할 수도 있습니다. 명령을 사용 하 여 플랫폼에서 사용자 구성 디렉터리를 찾을 수 있습니다 `Split-Path $PROFILE.CurrentUserCurrentHost` .

## <a name="general-configuration-settings"></a>일반 구성 설정

### <a name="executionpolicy"></a>ExecutionPolicy

> [!IMPORTANT]
> 이 구성은 Windows 플랫폼에만 적용 됩니다.

PowerShell 세션에 대 한 실행 정책을 구성 하 여 실행할 수 있는 스크립트를 결정 합니다. 기본적으로 PowerShell은 기존 실행 정책을 사용 합니다.

AllUsers 구성의 경우이는 **LocalMachine** 실행 정책을 설정 합니다.
CurrentUser 구성의 경우 **currentuser** 실행 정책을 설정 합니다.

> [!NOTE]
> Cmdlet은를 사용 하 여 [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy) 호출할 때 AllUsers 구성 파일에서이 설정을 수정 `-Scope LocalMachine` 하 고를 사용 하 여 호출할 때 CurrentUser 구성 파일에서이 설정을 수정 `-Scope CurrentUser` 합니다.

```Schema
"<shell-id>:ExecutionPolicy": "<execution-policy>"
```

위치:

- `<shell-id>` 현재 PowerShell 호스트의 ID를 참조 합니다. 일반적인 PowerShell Core의 경우 `Microsoft.PowerShell` 입니다. PowerShell 세션에서를 사용 하 여 검색할 수 있습니다 `$ShellId` .
- `<execution-policy>` 가 유효한 실행 정책 이름을 참조 하는 경우

다음 예에서는 PowerShell의 실행 정책을로 설정 합니다 `RemoteSigned` .

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "RemoteSigned"
}
```

Windows에서는 및의에서 해당 하는 레지스트리 키를 찾을 수 있습니다 `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` `HKEY_LOCAL_MACHINE` `HKEY_CURRENT_USER` .

### <a name="psmodulepath"></a>PSModulePath

`PSModulePath`이 PowerShell 세션의 설정을 재정의 합니다. 현재 사용자에 대 한 구성 인 경우 **CurrentUser** 모듈 경로를 설정 합니다. 모든 사용자 용으로 구성 된 경우는 **AllUsers** 모듈 경로를 설정 합니다.

> [!WARNING]
> 여기에서 **AllUsers** 또는 **CurrentUser** 모듈 경로를 구성 해도 PowerShellGet cmdlet에 대 한 범위 지정 설치 위치 [(예: Install-module)](/powershell/module/powershellget/install-module)는 변경 되지 않습니다. 이러한 cmdlet은 항상 _기본_ 모듈 경로를 사용 합니다.

값을 설정 하지 않으면 PowerShell은 해당 모듈 경로 설정에 기본값을 사용 합니다. 이러한 기본값에 대 한 자세한 내용은 [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath)를 참조 하세요.

이 설정을 사용 하면 `%` `"%HOME%\Documents\PowerShell\Modules"` CMD에서 허용 하는 것과 같은 방식으로 환경 변수를 문자 간에 포함 하 여 사용할 수 있습니다. 이 구문은 Linux 및 macOS에도 적용 됩니다. 예제는 아래를 참조 하세요.

```Schema
"PSModulePath": "<ps-module-path>"
```

위치:

- `<ps-module-path>` 는 모듈 디렉터리의 절대 경로입니다. 모든 사용자 구성에서는 AllUsers 공유 모듈 디렉터리입니다. 현재 사용자 구성의 경우 CurrentUser 모듈 디렉터리입니다.

이 예제에서는 `PSModulePath` Windows 환경에 대 한 구성을 보여 줍니다.

```json
{
  "PSModulePath": "C:\\Program Files\\PowerShell\\6\\Modules"
}
```

이 예제에서는 `PSModulePath` macOS 또는 Linux 환경에 대 한 구성을 보여 줍니다.

```json
{
  "PSModulePath": "/opt/powershell/6/Modules"
}
```

이 예제에서는 구성에 환경 변수를 포함 하는 방법을 보여 줍니다 `PSModulePath` . `HOME`환경 변수와 `/` 디렉터리 구분 기호를 사용 하면 Windows, macos 및 Linux에서 작동 합니다.

```json
{
  "PSModulePath": "%HOME%/Documents/PowerShell/Modules"
}
```

이 예제에서는 `PSModulePath` macOS 및 Linux 에서만 작동 하는 구성에 환경 변수를 포함 하는 방법을 보여 줍니다.

```json
{
  "PSModulePath": "%XDG_CONFIG_HOME%/powershell/Modules"
}
```

> [!NOTE]
> PowerShell 변수는 구성에 포함 될 수 없습니다 `PSModulePath` .
> `PSModulePath` Linux 및 macOS의 구성은 대/소문자를 구분 합니다. `PSModulePath`구성에서 플랫폼에 대 한 올바른 디렉터리 구분 기호를 사용 해야 합니다. MacOS 및 Linux에서이는를 의미 `/` 합니다. Windows에서는 `/` 및가 모두 `\` 작동 합니다.

### <a name="experimentalfeatures"></a>ExperimentalFeatures

PowerShell에서 사용할 수 있는 실험적 기능의 이름입니다. 기본적으로는 실험적 기능을 사용할 수 없습니다. 기본값은 빈 배열입니다.

```Schema
"ExperimentalFeatures": ["<experimental-feature-name>", ...]
```

위치:

- `<experimental-feature-name>` 사용할 수 있는 실험적 기능의 이름입니다.

다음 예에서는 PowerShell이 시작 될 때 **Psimplicitremoting** 및 **PSUseAbbreviationExpansion** 실험적 기능을 사용 하도록 설정 합니다.

```json
{
  "ExperimentalFeatures": [
    "PSImplicitRemotingBatching",
    "PSUseAbbreviationExpansion"
  ]
}
```

실험적 기능에 대 한 자세한 내용은 [실험적 기능 사용](/powershell/scripting/learn/experimental-features)을 참조 하세요.

## <a name="non-windows-logging-configuration"></a>비 Windows 로깅 구성

> [!IMPORTANT]
> 이 섹션의 구성 옵션은 macOS 및 Linux에만 적용 됩니다.
> Windows에 대 한 로깅은 Windows 이벤트 뷰어에서 관리 합니다.

PowerShell 구성 파일에서 macOS 및 Linux에 대 한 PowerShell의 로깅을 구성할 수 있습니다. 비 Windows 시스템에 대 한 PowerShell 로깅에 대 한 전체 설명은 [로깅 정보](./about_Logging_Non-Windows.md)를 참조 하세요.

### <a name="logidentity"></a>LogIdentity

> [!IMPORTANT]
> 이 설정은 macOS 및 Linux 에서만 사용할 수 있습니다.

시스템 로그에 쓰는 데 사용 되는 id 이름을 설정 합니다. 기본값은 "powershell"입니다.

```Schema
"LogIdentity": "<log-identity>"
```

위치:

- `<log-identity>` PowerShell에서 syslog에 쓰는 데 사용 해야 하는 문자열 id입니다.

> [!NOTE]
> 설치한 각 PowerShell 인스턴스에 대해 서로 다른 **Logidentity** 값을 사용할 수 있습니다.

이 예제에서는 PowerShell의 미리 보기 릴리스에 대 한 **Logidentity** 를 구성 합니다.

```json
{
  "LogIdentity": "powershell-preview"
}
```

### <a name="loglevel"></a>LogLevel

> [!IMPORTANT]
> 이 설정은 macOS 및 Linux 에서만 사용할 수 있습니다.

PowerShell에서 기록해 야 하는 최소 심각도 수준을 지정 합니다.

```Schema
"LogLevel": "<log-level>|default"
```

위치:

- `<log-level>`는 다음 중 하나입니다.
  - 항상
  - 위험
  - 오류
  - 경고
  - 정보 제공
  - 자세히
  - 디버그

> [!NOTE]
> 로그 수준을 설정 하면 상위 로그 수준을 모두 사용할 수 있습니다.

이 설정을 **기본값으로** 설정 하면 기본값으로 해석 됩니다.
기본값은 **정보 제공** 입니다.

다음 예에서는 값을 **Verbose** 로 설정 합니다.

```json
{
  "LogLevel": "Verbose"
}
```

### <a name="logchannels"></a>LogChannels

> [!IMPORTANT]
> 이 설정은 macOS 및 Linux 에서만 사용할 수 있습니다.

사용할 수 있는 로깅 채널을 결정 합니다.

```Schema
"LogChannels": "<log-channel>,..."
```

위치:

- `<log-channel>`는 다음 중 하나입니다.
  - 운영-PowerShell 작업에 대 한 기본 정보를 기록 합니다.
  - 분석-자세한 진단 정보를 기록 합니다.

기본값은 **작동** 입니다. 두 채널을 모두 사용 하려면 두 값을 쉼표로 구분 된 단일 문자열로 포함 합니다. 예를 들어:

```json
{
  "LogChannels": "Operational,Analytic"
}
```

### <a name="logkeywords"></a>LogKeywords

> [!IMPORTANT]
> 이 설정은 macOS 및 Linux 에서만 사용할 수 있습니다.

로깅할 PowerShell 부분을 결정 합니다. 기본적으로 모든 로그 키워드를 사용할 수 있습니다. 여러 키워드를 사용 하도록 설정 하려면 쉼표로 구분 된 단일 문자열에서 값을 나열 합니다.

```Schema
"LogKeywords": "<log-keyword>,..."
```

위치:

- `<log-keyword>`는 다음 중 하나입니다.
  - Runspace-runspace 관리
  - 파이프라인 파이프라인 작업
  - 프로토콜-통신 프로토콜 처리 (예: PSRP)
  - 전송-전송 계층 지원 (예: SSH)
  - 호스트-PowerShell 호스트 기능 (예: 콘솔 상호 작용)
  - Cmdlet-PowerShell builtin cmdlet
  - Serializer-serialization 논리
  - 세션-PowerShell 세션 상태
  - ManagedPlugin-WSMan 플러그 인

> [!NOTE]
> PowerShell의 알려진 부분에서 특정 동작을 진단 하려고 하지 않는 한이 값을 설정 하지 않으면 일반적으로이 값을 설정 하지 않는 것이 좋습니다. 이 값을 변경 하면 기록 되는 정보의 양만 줄어듭니다.

이 예에서는 로그를 runspace 작업, 파이프라인 논리 및 cmdlet 사용으로 제한 합니다. 다른 모든 로깅은 생략 됩니다.

```json
"LogKeywords": "Runspace,Pipeline,Cmdlets"
```

<!--

## Group policy configuration

### ScriptExecution

### ScriptBlockLogging

### ProtectedEventLogging

### Transcription

### UpdateableHelp

### ConsoleSessionConfiguration

-->

## <a name="more-example-configurations"></a>추가 예제 구성

### <a name="example-windows-configuration"></a>Windows 구성 예

이 구성에는 명시적으로 설정 된 추가 설정이 있습니다.

- 이 PowerShell 설치에 대 한 실행 정책은 `AllSigned`
- CurrentUser 모듈 경로를 공유 드라이브의 모듈 디렉터리로 설정 합니다.
- `PSImplicitRemotingBatching`실험적 기능을 사용할 수 있습니다.

> [!NOTE]
> `ExecutionPolicy`여기에 나와 있는 및 `PSModulePath` 설정은 모듈 경로에서 `\` 및 구분 문자를 사용 하 `;` 고 실행 정책이 `Unrestricted` (UNIX와 비슷한 플랫폼에서 유일 하 게 허용 되는 정책)가 아니기 때문에 Windows 플랫폼 에서만 작동 합니다.

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "AllSigned",
  "PSModulePath": "Z:\\Marisol's Shared Drive\\Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
}
```

### <a name="example-non-windows-configuration"></a>예: 비 Windows 구성

이 구성은 macOS 또는 Linux 에서만 작동 하는 여러 옵션을 설정 합니다.

- CurrentUser 모듈 경로는의 사용자 지정 모듈 디렉터리로 설정 됩니다. `$HOME`
- **Psimplicitremo의 일괄 처리** 실험적 기능을 사용할 수 있습니다.
- 자세한 로깅을 위해 PowerShell 로깅 수준이 **Verbose** 로 설정 됩니다.
- 이 PowerShell 설치는 **홈 powershell** id를 사용 하 여 로그에 기록 합니다.

```json
{
  "PSModulePath": "%HOME%/.powershell/Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
  "LogLevel": "Verbose",
  "LogIdentity": "home-powershell"
}
```

## <a name="see-also"></a>참조

[실행 정책 정보](./about_Execution_Policies.md)

[자동 변수 정보](./about_Automatic_Variables.md)

---
description: PowerShell의 동작을 사용자 지정 하는 변수입니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_preference_variables?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Preference_Variables
ms.openlocfilehash: 6f23e016131901ed78b223a4d23dfa12416d970b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221370"
---
# <a name="about-preference-variables"></a>기본 설정 변수 정보

## <a name="short-description"></a>간단한 설명

PowerShell의 동작을 사용자 지정 하는 변수입니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell에는 해당 동작을 사용자 지정할 수 있는 변수 집합이 포함 되어 있습니다. 이러한 기본 설정 변수는 GUI 기반 시스템의 옵션과 같은 방식으로 작동 합니다.

기본 설정 변수는 PowerShell 운영 환경 및 환경에서 실행 되는 모든 명령에 영향을 줍니다. 대부분의 경우 cmdlet에는 특정 명령의 기본 설정 동작을 재정의 하는 데 사용할 수 있는 매개 변수가 있습니다.

다음 표에서는 기본 설정 변수와 해당 기본값을 보여 줍니다.

|             변수             |       기본값       |
| -------------------------------- | ------------------------- |
| `$ConfirmPreference`             | 높음                      |
| `$DebugPreference`               | SilentlyContinue          |
| `$ErrorActionPreference`         | 계속                  |
| `$ErrorView`                     | NormalView                |
| `$FormatEnumerationLimit`        | 4                         |
| `$InformationPreference`         | SilentlyContinue          |
| `$LogCommandHealthEvent`         | False (로깅되지 않음)        |
| `$LogCommandLifecycleEvent`      | False (로깅되지 않음)        |
| `$LogEngineHealthEvent`          | True (기록 됨)             |
| `$LogEngineLifecycleEvent`       | True (기록 됨)             |
| `$LogProviderLifecycleEvent`     | True (기록 됨)             |
| `$LogProviderHealthEvent`        | True (기록 됨)             |
| `$MaximumHistoryCount`           | 4096                      |
| `$OFS`                           | (공백 문자 ( `" "` )) |
| `$OutputEncoding`                | **UTF8Encoding** 개체   |
| `$ProgressPreference`            | 계속                  |
| `$PSDefaultParameterValues`      | (없음-빈 해시 테이블) |
| `$PSEmailServer`                 | (없음)                    |
| `$PSModuleAutoLoadingPreference` | 모두                       |
| `$PSSessionApplicationName`      | wsman                     |
| `$PSSessionConfigurationName`    | `http://schemas.microsoft.com/powershell/Microsoft.PowerShell` |
| `$PSSessionOption`               | [$PSSessionOption](#pssessionoption) 참조 |
| `$Transcript`                    | (없음)                    |
| `$VerbosePreference`             | SilentlyContinue          |
| `$WarningPreference`             | 계속                  |
| `$WhatIfPreference`              | 거짓                     |

PowerShell은 사용자 기본 설정을 저장 하는 다음과 같은 환경 변수를 포함 합니다. 이러한 환경 변수에 대 한 자세한 내용은 [about_Environment_Variables](about_Environment_Variables.md)를 참조 하세요.

- `env:PSExecutionPolicyPreference`
- `$env:PSModulePath`

> [!NOTE]
> 기본 설정 변수에 대 한 변경 내용은 해당 스크립트나 함수가 기본 설정이 사용 된 범위와 동일한 범위에서 정의 된 경우에만 스크립트 및 함수에 적용 됩니다. 자세한 내용은 [about_Scopes](about_Scopes.md)를 참조 하세요.

## <a name="working-with-preference-variables"></a>기본 설정 변수 작업

이 문서에서는 각 기본 설정 변수에 대해 설명 합니다.

특정 기본 설정 변수의 현재 값을 표시 하려면 변수의 이름을 입력 합니다. 예를 들어 다음 명령은 변수의 값을 표시 합니다 `$ConfirmPreference` .

```powershell
 $ConfirmPreference
```

```Output
High
```

변수의 값을 변경 하려면 대입문을 사용 합니다. 예를 들어 다음 문은 `$ConfirmPreference` 매개 변수의 값을 **Medium** 로 변경 합니다.

```powershell
$ConfirmPreference = "Medium"
```

사용자가 설정 하는 값은 현재 PowerShell 세션에만 적용 됩니다. 모든 PowerShell 세션에서 변수를 유효 하 게 만들려면 PowerShell 프로필에 추가 합니다. 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.

## <a name="working-remotely"></a>원격으로 작업

원격 컴퓨터에서 명령을 실행 하는 경우 원격 명령은 원격 컴퓨터의 PowerShell 클라이언트에 설정 된 기본 설정에만 적용 됩니다. 예를 들어 원격 명령을 실행 하는 경우 원격 컴퓨터의 변수 값은 PowerShell에서 `$DebugPreference` 디버깅 메시지에 응답 하는 방법을 결정 합니다.

원격 명령에 대 한 자세한 내용은 [about_Remote](about_Remote.md)를 참조 하세요.

### <a name="confirmpreference"></a>\$ConfirmPreference

Cmdlet 또는 함수를 실행 하기 전에 PowerShell에서 자동으로 확인 메시지를 표시할지 여부를 결정 합니다.

`$ConfirmPreference`변수의 유효한 값은 **높음** , **보통** 또는 **낮음** 입니다. Cmdlet 및 함수에는 **높음** , **중간** 또는 **낮음** 의 위험이 할당 됩니다. `$ConfirmPreference`변수 값이 cmdlet 또는 함수에 할당 된 위험 보다 작거나 같으면 PowerShell에서 cmdlet 또는 함수를 실행 하기 전에 확인 메시지를 자동으로 표시 합니다.

`$ConfirmPreference`변수 값이 **None** 이면 PowerShell에서 cmdlet 또는 함수를 실행 하기 전에 자동으로 메시지를 표시 하지 않습니다.

세션의 모든 cmdlet 및 함수에 대 한 확인 동작을 변경 하려면 `$ConfirmPreference` 변수의 값을 변경 합니다.

`$ConfirmPreference`단일 명령에 대 한를 재정의 하려면 cmdlet의 또는 함수의 **Confirm** 매개 변수를 사용 합니다. 확인을 요청 하려면를 사용 `-Confirm` 합니다. 확인을 표시 하지 않으려면를 사용 `-Confirm:$false` 합니다.

유효한 값 `$ConfirmPreference` :

- **없음** : PowerShell에서 자동으로 프롬프트가 표시 되지 않습니다. 특정 명령에 대 한 확인을 요청 하려면 cmdlet 또는 함수의 **Confirm** 매개 변수를 사용 합니다.
- **낮음** : PowerShell을 실행 하기 전에 확인 메시지를 표시 하거나 낮음, 중간 또는 높은 위험으로 함수를 실행 합니다.
- **보통** : PowerShell에서 중간 또는 높은 위험으로 cmdlet 또는 함수를 실행 하기 전에 확인 메시지를 표시 합니다.
- **High** : cmdlet을 실행 하기 전에 PowerShell에서 확인 메시지를 표시 하거나 높은 위험 수준으로 함수를 실행 합니다.

#### <a name="detailed-explanation"></a>자세한 설명

PowerShell에서 작업을 수행 하기 전에 확인 메시지를 자동으로 표시할 수 있습니다. 예를 들어 cmdlet 또는 함수가 시스템에서 데이터를 삭제 하거나 많은 양의 시스템 리소스를 사용 하는 데 상당한 영향을 줄 수 있습니다.

```powershell
Remove-Item -Path C:\file.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\file.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"):
```

위험도의 예측은 해당 기능에 **영향을 주는** cmdlet 또는 함수의 특성입니다. 이 설정은 사용자가 변경할 수 없습니다.

시스템에 위험을 초래할 수 있는 cmdlet 및 함수에는 단일 명령에 대 한 확인을 요청 하거나 표시 하지 않는 **확인** 매개 변수가 있습니다.

대부분의 cmdlet 및 함수는 기본 위험 값을 사용 하기 때문에 **중간** 의 기능 및 **기본값을 사용** 하므로 `$ConfirmPreference` 자동 **High** 확인이 거의 발생 하지 않습니다. 그러나의 값을 `$ConfirmPreference` **보통** 또는 **낮음** 으로 변경 하 여 자동 확인을 활성화할 수 있습니다.

#### <a name="examples"></a>예

이 예에서는 `$ConfirmPreference` 변수의 기본값 **높음** 이 미치는 영향을 보여 줍니다. **높은** 값은 높은 위험 수준의 cmdlet 및 함수를 확인 합니다. 대부분의 cmdlet과 함수는 보통 위험 하므로 자동으로 확인 되 고 `Remove-Item` 파일을 삭제 하지 않습니다. `-Confirm`명령에를 추가 하면 사용자에 게 확인 메시지가 표시 됩니다.

```powershell
$ConfirmPreference
```

```Output
High
```

```powershell
Remove-Item -Path C:\temp1.txt
```

`-Confirm`확인을 요청 하는 데 사용 합니다.

```powershell
Remove-Item -Path C:\temp2.txt -Confirm
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

다음 예에서는의 값을 보통으로 변경 하는 경우의 효과를 보여 줍니다 `$ConfirmPreference` . **Medium** 대부분의 cmdlet과 함수는 보통 위험 하므로 자동으로 확인 됩니다. 단일 명령에 대 한 확인 메시지를 표시 하지 않으려면 **Confirm** 매개 변수를 값으로 사용 `$false` 합니다.

```powershell
$ConfirmPreference = "Medium"
Remove-Item -Path C:\temp2.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

```powershell
Remove-Item -Path C:\temp3.txt -Confirm:$false
```

### <a name="debugpreference"></a>\$DebugPreference

PowerShell에서 스크립트, cmdlet 또는 공급자에 의해 생성 된 디버깅 메시지에 응답 하는 방법 또는 명령줄에서 명령을 통해 응답 하는 방법을 결정 합니다 `Write-Debug` .

일부 cmdlet은 프로그래머 및 기술 지원 전문가 용으로 설계 된 기술 메시지를 표시 하는 디버깅 메시지를 표시 합니다. 기본적으로 디버깅 메시지는 표시 되지 않지만의 값을 변경 하 여 디버깅 메시지를 표시할 수 있습니다 `$DebugPreference` .

Cmdlet의 **Debug** 일반 매개 변수를 사용 하 여 특정 명령에 대 한 디버깅 메시지를 표시 하거나 숨길 수 있습니다. 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조하세요.

유효한 값은 다음과 같습니다.

- **Stop** : 디버그 메시지를 표시 하 고 실행을 중지 합니다. 콘솔에 오류를 기록 합니다.
- **Inquire** : 디버그 메시지를 표시 하 고 계속할지 여부를 묻는 메시지를 표시 합니다. 명령에 **Debug** 일반 매개 변수를 추가 하 여 디버깅 메시지를 생성 하도록 명령이 구성 된 경우 변수 값을 `$DebugPreference` **Inquire** 로 변경 합니다.
- **Continue** : 디버그 메시지를 표시 하 고 실행을 계속 합니다.
- **SilentlyContinue** : (기본값) 아무런 영향도 주지 않습니다. 디버그 메시지는 표시 되지 않으며 중단 없이 계속 실행 됩니다.

#### <a name="examples"></a>예

다음 예에서는 명령줄 `$DebugPreference` 에서 명령을 입력 하는 경우의 값을 변경할 경우의 결과를 보여 줍니다 `Write-Debug` .
변경 내용은 cmdlet 및 스크립트에 의해 생성 된 메시지를 포함 하 여 모든 디버깅 메시지에 영향을 줍니다. 예제에서는 단일 명령과 관련 된 디버깅 메시지를 표시 하거나 숨기는 **Debug** 매개 변수를 보여 줍니다.

이 예에서는 `$DebugPreference` 변수의 기본값 **SilentlyContinue** 의 효과를 보여 줍니다. 기본적으로 `Write-Debug` cmdlet의 디버그 메시지가 표시 되지 않고 처리가 계속 됩니다. **디버그** 매개 변수를 사용 하는 경우 단일 명령에 대 한 기본 설정을 재정의 합니다. 디버그 메시지가 표시 됩니다.

```powershell
$DebugPreference
```

```Output
SilentlyContinue
```

```powershell
Write-Debug -Message "Hello, World"
```

```powershell
Write-Debug -Message "Hello, World" -Debug
```

```Output
DEBUG: Hello, World
```

이 예에서는 Continue 값을 사용한 결과를 보여 줍니다 `$DebugPreference` . **Continue** 디버그 메시지가 표시 되 고 명령이 계속 처리 됩니다.

```powershell
$DebugPreference = "Continue"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
```

이 예제에서는 값이 인 **Debug** 매개 변수 `$false` 를 사용 하 여 단일 명령에 대 한 메시지를 표시 하지 않습니다. 디버그 메시지가 표시 되지 않습니다.

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

이 예에서는 `$DebugPreference` **중지** 값으로 설정 되는 결과를 보여 줍니다. 디버그 메시지가 표시 되 고 명령이 중지 됩니다.

```powershell
$DebugPreference = "Stop"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
Write-Debug : The running command stopped because the preference variable
 "DebugPreference" or common parameter is set to Stop: Hello, World
At line:1 char:1
+ Write-Debug -Message "Hello, World"
```

이 예제에서는 값이 인 **Debug** 매개 변수 `$false` 를 사용 하 여 단일 명령에 대 한 메시지를 표시 하지 않습니다. 디버그 메시지가 표시 되지 않고 처리가 중지 되지 않습니다.

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

이 예에서는 `$DebugPreference` **Inquire** 값으로 설정 되는 결과를 보여 줍니다. 디버그 메시지가 표시 되 고 사용자에 게 확인 메시지를 표시 합니다.

```powershell
$DebugPreference = "Inquire"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

이 예제에서는 값이 인 **Debug** 매개 변수 `$false` 를 사용 하 여 단일 명령에 대 한 메시지를 표시 하지 않습니다. 디버그 메시지가 표시 되지 않고 처리가 계속 됩니다.

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

### <a name="erroractionpreference"></a>\$ErrorActionPreference

PowerShell이 종료 되지 않는 오류에 응답 하는 방법, 즉 cmdlet 처리를 중지 하지 않는 오류를 결정 합니다. 예를 들어, 명령줄 또는 cmdlet에 의해 생성 된 오류와 같은 스크립트, cmdlet 또는 공급자에 `Write-Error` 있습니다.

Cmdlet의 **Erroraction** 일반 매개 변수를 사용 하 여 특정 명령에 대 한 기본 설정을 재정의할 수 있습니다.

유효한 값은 다음과 같습니다.

- **Continue** : (기본값) 오류 메시지를 표시 하 고 계속 실행 합니다.
- **Ignore** : 오류 메시지를 표시 하지 않고 계속 해 서 명령을 실행 합니다. **무시** 값은 명령 당 사용을 위한 것 이며 저장 된 기본 설정으로 사용 되지 않습니다. **Ignore** 는 변수의 올바른 값이 아닙니다 `$ErrorActionPreference` .
- **Inquire** : 오류 메시지를 표시 하 고 계속할지 여부를 묻는 메시지를 표시 합니다.
- **SilentlyContinue** : 영향을 주지 않습니다. 오류 메시지가 표시 되지 않으며 중단 없이 계속 실행 됩니다.
- **Stop** : 오류 메시지를 표시 하 고 실행을 중지 합니다. 오류를 생성 하는 것 외에도 **Stop** 값은 오류 스트림에 ActionPreferenceStopException 개체를 생성 합니다.
  스트림(stream)
- **Suspend** : 추가 조사를 허용 하도록 워크플로 작업을 자동으로 일시 중단 합니다. 조사 후 워크플로를 다시 시작할 수 있습니다. **일시 중단** 값은 저장 된 기본 설정으로 사용 되지 않고 명령 당 사용을 위한 것입니다. **Suspend** 는 변수의 올바른 값이 아닙니다 `$ErrorActionPreference` .

`$ErrorActionPreference`**Erroraction** 매개 변수는 PowerShell이 cmdlet 처리를 중지 하는 종료 오류에 응답 하는 방법에 영향을 주지 않습니다. **Erroraction** 일반 매개 변수에 대 한 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조 하세요.

#### <a name="examples"></a>예

이 예에서는 변수 값이 다른 값의 영향을 보여 줍니다 `$ErrorActionPreference` . **Erroraction** 매개 변수는 값을 재정의 하는 데 사용 됩니다 `$ErrorActionPreference` .

이 예에서는 `$ErrorActionPreference` 기본값인 **Continue** 를 표시 합니다. 종료 되지 않는 오류가 생성 됩니다. 메시지가 표시 되 고 처리가 계속 됩니다.

```powershell
# Change the ErrorActionPreference to 'Continue'
$ErrorActionPreference = 'Continue'
# Generate a non-terminating error and continue processing the script.
Write-Error -Message  'Test Error' ; Write-Host 'Hello World'
```

```Output
Write-Error -Message  'Test Error' ; Write-Host 'Hello World' : Test Error
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

Hello World
```

이 예에서는 `$ErrorActionPreference` 기본 값인 **Inquire** 를 보여 줍니다. 오류가 생성 되 고 동작에 대 한 프롬프트가 표시 됩니다.

```powershell
# Change the ErrorActionPreference to 'Inquire'
$ErrorActionPreference = 'Inquire'
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
```

```Output
Confirm
Test Error
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

이 예에서는를 `$ErrorActionPreference` **SilentlyContinue** 로 설정 하는 방법을 보여 줍니다.
오류 메시지는 표시 되지 않습니다.

```powershell
# Change the ErrorActionPreference to 'SilentlyContinue'
$ErrorActionPreference = 'SilentlyContinue'
# Generate an error message
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
# Error message is suppressed and script continues processing
```

```Output
Hello World
```

이 예에서는 `$ErrorActionPreference` **Stop** 으로 설정 된를 보여 줍니다. 변수에 생성 된 추가 개체도 보여 줍니다 `$Error` .

```powershell
# Change the ErrorActionPreference to 'Stop'
$ErrorActionPreference = 'Stop'
# Error message is is generated and script stops processing
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'

# Show the ActionPreferenceStopException and the error generated
$Error[0]
$Error[1]
```

```Output
Write-Error -Message 'Test Error' ; Write-Host 'Hello World' : Test Error
At line:1 char:1
+ Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

The running command stopped because the preference variable "ErrorActionPreference"
or common parameter is set to Stop: Test Error

Write-Error -Message 'Test Error' ; Write-Host 'Hello World' : Test Error
At line:1 char:1
+ Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

### <a name="errorview"></a>\$ErrorView

PowerShell에서 오류 메시지의 표시 형식을 결정 합니다.

유효한 값은 다음과 같습니다.

- 기본 **보기** : (기본값) 대부분의 사용자를 위해 설계 된 상세 뷰입니다. 오류에 대 한 설명 및 오류와 관련 된 개체의 이름으로 구성 됩니다.
- **Categoryview** : 프로덕션 환경을 위해 설계 된 간결한 구조화 된 뷰입니다. 형식은 다음과 같습니다.

  {Category}: ({TargetName}: {TargetType}): [{Activity}], {Reason}

**Categoryview** 의 필드에 대 한 자세한 내용은 [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) 클래스를 참조 하세요.

#### <a name="examples"></a>예

이 예에서는의 값이 `$ErrorView` 기본값인 **normalview** 인 경우 오류를 표시 하는 방법을 보여 줍니다. `Get-ChildItem` 존재 하지 않는 파일을 찾는 데 사용 됩니다.

```powershell
Get-ChildItem -Path C:\nofile.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\nofile.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path C:\nofile.txt
```

이 예에서는의 값 `$ErrorView` 이 **categoryview** 로 변경 될 때 동일한 오류가 표시 되는 방법을 보여 줍니다.

```powershell
$ErrorView = "CategoryView"
Get-ChildItem -Path C:\nofile.txt
```

```Output
ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem], ItemNotFoundException
```

이 예에서는의 값이 `$ErrorView` 오류 표시에만 영향을 줍니다. 자동 변수에 저장 된 오류 개체의 구조는 변경 되지 않습니다 `$Error` . 자동 변수에 대 한 자세한 내용은 `$Error` [about_automatic_variables](about_Automatic_Variables.md)를 참조 하세요.

다음 명령은 오류 배열에서 가장 최근 오류와 연결 된 **ErrorRecord** 개체, **요소 0** 을 사용 하 고 목록에 있는 모든 error 개체의 속성에 대 한 형식을 지정 합니다.

```powershell
$Error[0] | Format-List -Property * -Force
```

```Output
PSMessageDetails      :
Exception             : System.Management.Automation.ItemNotFoundException:
                          Cannot find path 'C:\nofile.txt' because it does
                          not exist.
                        at System.Management.Automation.SessionStateInternal.
                          GetChildItems(String path, Boolean recurse, UInt32
                          depth, CmdletProviderContext context)
                        at System.Management.Automation.ChildItemCmdlet
                          ProviderIntrinsics.Get(String path, Boolean
                          recurse, UInt32 depth, CmdletProviderContext context)
                        at Microsoft.PowerShell.Commands.GetChildItemCommand.
                          ProcessRecord()
TargetObject          : C:\nofile.txt
CategoryInfo          : ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem],
                          ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,
                          Microsoft.PowerShell.Commands.GetChildItemCommand
ErrorDetails          :
InvocationInfo        : System.Management.Automation.InvocationInfo
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo : {0, 1}
```

### <a name="formatenumerationlimit"></a>\$FormatEnumerationLimit

표시에 포함 되는 열거 된 항목 수를 결정 합니다. 이 변수는 기본 개체에는 영향을 주지 않으며 표시 되는 경우에만 적용 됩니다. 의 값 `$FormatEnumerationLimit` 이 열거 된 항목 수보다 적으면 PowerShell은 `...` 표시 되지 않는 항목을 나타내기 위해 줄임표 ()를 추가 합니다.

**유효한 값** : 정수 ( `Int32` )

**기본값** : 4

#### <a name="examples"></a>예

이 예제에서는 변수를 사용 하 여 `$FormatEnumerationLimit` 열거 된 항목의 표시를 개선 하는 방법을 보여 줍니다.

이 예제의 명령은 **실행 중인** 서비스와 **중지** 된 서비스용으로 하나씩, 두 그룹의 컴퓨터에서 실행 되는 모든 서비스를 나열 하는 테이블을 생성 합니다. 명령을 사용 하 여 `Get-Service` 모든 서비스를 가져온 다음 파이프라인을 통해 결과를 cmdlet에 보냅니다 `Group-Object` .이 cmdlet은 서비스 상태별로 결과를 그룹화 합니다.

결과는 **이름** 열의 상태와 **그룹** 열의 프로세스를 나열 하는 테이블입니다. 열 레이블을 변경 하려면 해시 테이블을 사용 하십시오. [about_Hash_Tables](about_Hash_Tables.md)를 참조 하십시오. 자세한 내용은 [형식-테이블](xref:Microsoft.PowerShell.Utility.Format-Table)의 예제를 참조 하세요.

의 현재 값을 찾습니다 `$FormatEnumerationLimit` .

```powershell
$FormatEnumerationLimit
```

```Output
4
```

**상태별** 로 그룹화 된 모든 서비스를 나열 합니다. 의 값은 4 이기 때문에 각 상태에 대 한 **그룹** 열에는 최대 4 개의 서비스가 나열 됩니다 `$FormatEnumerationLimit` . **4**

```powershell
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv...}
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart...}
```

나열 된 항목 수를 늘리려면 값을 `$FormatEnumerationLimit` **1000** 로 늘립니다. `Get-Service`및 `Group-Object` 를 사용 하 여 서비스를 표시 합니다.

```powershell
$FormatEnumerationLimit = 1000
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec...
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc...
```

`Format-Table` **Wrap** 매개 변수와 함께 사용 하 여 서비스 목록을 표시 합니다.

```powershell
Get-Service | Group-Object -Property Status | Format-Table -Wrap
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec,
                  Client for NFS, CryptSvc, DcomLaunch, Dhcp, dmserver,
                  Dnscache, ERSvc, Eventlog, EventSystem, FwcAgent, helpsvc,
                  HidServ, IISADMIN, InoRPC, InoRT, InoTask, lanmanserver,
                  lanmanworkstation, LmHosts, MDM, Netlogon, Netman, Nla,
                  NtLmSsp, PlugPlay, PolicyAgent, ProtectedStorage, RasMan,
                  RemoteRegistry, RpcSs, SamSs, Schedule, seclogon, SENS,
                  SharedAccess, ShellHWDetection, SMT PSVC, Spooler,
                  srservice, SSDPSRV, stisvc, TapiSrv, TermService, Themes,
                  TrkWks, UMWdf, W32Time, W3SVC, WebClient, winmgmt, wscsvc,
                  wuauserv, WZCSVC, zzInterix}

41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc,
                  ClipSrv, clr_optimization_v2.0.50727_32, COMSysApp,
                  CronService, dmadmin, FastUserSwitchingCompatibility,
                  HTTPFilter, ImapiService, Mapsvc, Messenger, mnmsrvc,
                  MSDTC, MSIServer, msvsmon80, NetDDE, NetDDEdsdm, NtmsSvc,
                  NVSvc, ose, RasAuto, RDSessMgr, RemoteAccess, RpcLocator,
                  SCardSvr, SwPrv, SysmonLog, TlntSvr, upnphost, UPS, VSS,
                  WmdmPmSN, Wmi, WmiApSrv, xmlprov}
```

### <a name="informationpreference"></a>\$InformationPreference

`$InformationPreference`변수를 사용 하면 사용자에 게 표시할 정보 스트림 기본 설정을 지정할 수 있습니다. 특히 [쓰기 정보](xref:Microsoft.PowerShell.Utility.Write-Information) cmdlet을 추가 하 여 명령 또는 스크립트에 추가한 정보 메시지입니다. **Informationaction** 매개 변수를 사용 하는 경우 해당 값은 변수의 값을 재정의 `$InformationPreference` 합니다. `Write-Information` 는 PowerShell 5.0에서 도입 되었습니다.

유효한 값은 다음과 같습니다.

- **Stop** : 명령이 발생 하면 명령이 나 스크립트를 중지 합니다. `Write-Information`
- **Inquire** : 명령에 지정 하는 정보 메시지를 표시 `Write-Information` 한 다음 계속할지 여부를 묻는 메시지를 표시 합니다.
- **Continue** : 정보 메시지를 표시 하 고 계속 실행 합니다.
- **일시 중단** 은 PowerShell 6 이상에서 지원 되지 않는 워크플로에 대해서만 사용할 수 있습니다.
- **SilentlyContinue** : (기본값) 아무런 영향도 주지 않습니다. 정보 메시지는 표시 되지 않으며 스크립트는 중단 없이 계속 됩니다.

### <a name="logevent"></a>\$Log * 이벤트

**Log * 이벤트** 기본 설정 변수는 이벤트 뷰어의 PowerShell 이벤트 로그에 기록 되는 이벤트 유형을 결정 합니다. 기본적으로 엔진 및 공급자 이벤트만 로깅됩니다. 그러나 **log * 이벤트** 기본 설정 변수를 사용 하 여 로그를 사용자 지정할 수 있습니다 (예: 명령에 대 한 로깅 이벤트).

**Log * 이벤트** 기본 설정 변수는 다음과 같습니다.

- `$LogCommandHealthEvent`: 명령 초기화 및 처리에서 오류 및 예외를 기록 합니다. 기본값은 `$false` (로깅되지 않음)입니다.
- `$LogCommandLifecycleEvent`: 명령 검색에서 명령 및 명령 파이프라인의 시작과 중지 및 보안 예외를 기록 합니다. 기본값은 `$false` (로깅되지 않음)입니다.
- `$LogEngineHealthEvent`: 세션의 오류 및 실패를 기록 합니다. 기본값은 `$true` (기록)입니다.
- `$LogEngineLifecycleEvent`: 세션의 열기 및 닫기를 로깅합니다. 기본값은 `$true` (기록)입니다.
- `$LogProviderHealthEvent`: 읽기 및 쓰기 오류, 조회 오류, 호출 오류 등의 공급자 오류를 기록 합니다. 기본값은 `$true` (기록)입니다.
- `$LogProviderLifecycleEvent`: PowerShell 공급자 추가 및 제거를 기록 합니다. 기본값은 `$true` (기록)입니다. PowerShell 공급자에 대 한 자세한 내용은 [about_Providers](about_Providers.md)를 참조 하세요.

**Log * 이벤트** 를 사용 하도록 설정 하려면 값이 인 변수를 입력 합니다 `$true` . 예를 들면 다음과 같습니다.

```powershell
$LogCommandLifeCycleEvent = $true
```

이벤트 유형을 사용 하지 않도록 설정 하려면 값이 인 변수를 입력 합니다 `$false` . 예를 들면 다음과 같습니다.

```powershell
$LogCommandLifeCycleEvent = $false
```

사용 하도록 설정 하는 이벤트는 현재 PowerShell 콘솔에만 적용 됩니다. 모든 콘솔에 구성을 적용 하려면 변수 설정을 PowerShell 프로필에 저장 합니다. 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.

### <a name="maximumhistorycount"></a>\$MaximumHistoryCount

현재 세션에 대 한 명령 기록에 저장 되는 명령 수를 결정 합니다.

**유효한 값** : 1-32768 ( `Int32` )

**기본값** : 4096

명령 기록에 현재 저장 된 명령의 수를 확인 하려면 다음을 입력 합니다.

```powershell
(Get-History).Count
```

세션 기록에 저장 된 명령을 보려면 cmdlet을 사용 합니다 `Get-History` . 자세한 내용은 [about_History](about_History.md)를 참조 하세요.

### <a name="ofs"></a>\$OFS

출력 필드 구분 기호 (.OFS)는 문자열로 변환 된 배열의 요소를 구분 하는 문자를 지정 합니다.

**유효한 값** : 모든 문자열

**기본값** : Space

기본적으로 변수는 `$OFS` 존재 하지 않으며 출력 파일 구분 기호는 공백 이지만이 변수를 추가 하 고 임의의 문자열로 설정할 수 있습니다. 을 `$OFS` 입력 하 여 세션의 값을 변경할 수 있습니다 `$OFS="<value>"` .

> [!NOTE]
> `" "`스크립트, 모듈 또는 구성 출력에 공백 ()의 기본값이 필요한 경우 `$OFS` 코드의 다른 위치에서 기본값이 변경 되지 않은 것으로 주의 하세요.

#### <a name="examples"></a>예

이 예제에서는 배열이 문자열로 변환 될 때 공백을 사용 하 여 값을 구분 하는 방법을 보여 줍니다. 이 경우 정수 배열이 변수에 저장 된 다음 변수가 문자열로 캐스팅 됩니다.

```powershell
$array = 1,2,3,4
[string]$array
```

```Output
1 2 3 4
```

구분 기호를 변경 하려면 값을 `$OFS` 할당 하 여 변수를 추가 합니다.
변수에 이름을 지정 해야 합니다 `$OFS` .

```powershell
$OFS = "+"
[string]$array
```

```Output
1+2+3+4
```

기본 동작을 복원 하려면 값에 공백 ()을 할당 `" "` `$OFS` 하거나 변수를 삭제할 수 있습니다. 다음 명령은 변수를 삭제 한 다음 구분 기호가 공백 인지 확인 합니다.

```powershell
Remove-Variable OFS
[string]$array
```

```Output
1 2 3 4
```

### <a name="outputencoding"></a>\$OutputEncoding

다른 응용 프로그램에 텍스트를 보낼 때 PowerShell에서 사용 하는 문자 인코딩 방법을 결정 합니다.

예를 들어 응용 프로그램이 유니코드 문자열을 PowerShell로 반환 하는 경우 문자를 올바르게 보내기 위해 값을 **UnicodeEncoding** 로 변경 해야 할 수 있습니다.

유효한 값은 **ASCIIEncoding** , **SBCSCodePageEncoding** , **UTF7Encoding** , **UTF8Encoding** , **UTF32Encoding** 및 **UnicodeEncoding** 와 같이 Encoding 클래스에서 파생 된 개체입니다.

**기본값** : UTF8Encoding 개체 (UTF8Encoding)

#### <a name="examples"></a>예

이 예제에서는 유니코드 문자를 사용 하는 언어 (예: 중국어)로 지역화 된 컴퓨터에서 Windows **findstr.exe** 명령을 PowerShell에서 작동 하 게 하는 방법을 보여 줍니다.

첫 번째 명령은의 값을 찾습니다 `$OutputEncoding` . 이 값은 인코딩 개체 이므로 해당 **EncodingName** 속성만 표시 합니다.

```powershell
$OutputEncoding.EncodingName
```

이 예제에서는 **findstr.exe** 명령을 사용 하 여 파일에 있는 두 개의 중국어 문자를 검색 `Test.txt` 합니다. 이 **findstr.exe** 명령이 Windows 명령 프롬프트 ( **cmd.exe** )에서 실행 되는 경우 **findstr.exe** 는 텍스트 파일에서 문자를 찾습니다. 그러나 PowerShell에서 동일한 **findstr.exe** 명령을 실행 하는 경우 Powershell에서 유니코드 텍스트가 아닌 ASCII 텍스트의 **findstr.exe** 으로 보내기 때문에 문자를 찾을 수 없습니다.

```powershell
findstr <Unicode-characters>
```

PowerShell에서 명령을 작동 하도록 하려면의 값을 `$OutputEncoding` 콘솔의 **outputencoding** 속성 값으로 설정 합니다 .이 속성은 Windows에 대해 선택한 로캘을 기반으로 합니다. **Outputencoding** 이 콘솔의 정적 속성 이므로 명령에 이중 콜론 ()을 사용 `::` 합니다.

```powershell
$OutputEncoding = [console]::OutputEncoding
$OutputEncoding.EncodingName
```

```Output
OEM United States
```

인코딩이 변경 된 후 **findstr.exe** 명령은 유니코드 문자를 찾습니다.

```powershell
findstr <Unicode-characters>
```

```Output
test.txt:         <Unicode-characters>
```

### <a name="progresspreference"></a>\$ProgressPreference

PowerShell에서 스크립트, cmdlet 또는 공급자에 의해 생성 된 진행률 업데이트 (예: [쓰기 진행률](xref:Microsoft.PowerShell.Utility.Write-Progress) cmdlet에 의해 생성 된 진행률 표시줄)에 응답 하는 방법을 결정 합니다.
`Write-Progress`Cmdlet은 명령의 상태를 표시 하는 진행률 표시줄을 만듭니다.

유효한 값은 다음과 같습니다.

- **중지** : 진행률 표시줄을 표시 하지 않습니다. 대신 오류 메시지를 표시 하 고 실행을 중지 합니다.
- **Inquire** : 진행률 표시줄을 표시 하지 않습니다. 계속할 수 있는 권한을 요청 합니다. 또는로 회신 하 `Y` `A` 는 경우 진행률 표시줄이 표시 됩니다.
- **Continue** : (기본값) 진행률 표시줄을 표시 하 고 실행을 계속 합니다.
- **SilentlyContinue** : 명령을 실행 하지만 진행률 표시줄을 표시 하지 않습니다.

### <a name="psemailserver"></a>\$PSEmailServer

전자 메일 메시지를 보내는 데 사용 되는 기본 전자 메일 서버를 지정 합니다. 이 기본 설정 변수는 [send-mailmessage](xref:Microsoft.PowerShell.Utility.Send-MailMessage) cmdlet과 같은 전자 메일을 보내는 cmdlet에 사용 됩니다.

### <a name="psdefaultparametervalues"></a>\$PSDefaultParameterValues

Cmdlet 및 고급 함수의 매개 변수에 대 한 기본값을 지정 합니다.
값은 `$PSDefaultParameterValues` 키가 cmdlet 이름 및 콜론 ()으로 구분 된 매개 변수 이름으로 구성 되는 해시 테이블입니다 `:` . 값은 사용자가 지정 하는 사용자 지정 기본값입니다.

`$PSDefaultParameterValues` 는 PowerShell 3.0에서 도입 되었습니다.

이 기본 설정 변수에 대 한 자세한 내용은 [about_Parameters_Default_Values](about_Parameters_Default_Values.md)를 참조 하세요.

### <a name="psmoduleautoloadingpreference"></a>\$PSModuleAutoloadingPreference

세션에서 모듈 자동 가져오기를 사용 하거나 사용 하지 않도록 설정 합니다. **All** 이 기본값입니다. 변수 값에 관계 [없이 import-module을 사용 하](xref:Microsoft.PowerShell.Core.Import-Module) 여 모듈을 가져올 수 있습니다.

유효한 값은 다음과 같습니다.

- **All** : 처음 사용할 때 자동으로 모듈을 가져옵니다. 모듈을 가져오려면 모듈에서 명령을 가져오거나 사용 합니다. 예를 들면 `Get-Command`를 사용합니다.
- **ModuleQualified** : 사용자가 모듈의 명령에 대 한 모듈의 정규화 된 이름을 사용 하는 경우에만 모듈을 자동으로 가져옵니다. 예를 들어 사용자가 형식이 면 `MyModule\MyCommand` PowerShell에서 **MyModule** 모듈을 가져옵니다.
- **없음** : 모듈 자동 가져오기가 세션에서 사용 하지 않도록 설정 되어 있습니다. 모듈을 가져오려면 cmdlet을 사용 `Import-Module` 합니다.

모듈 자동 가져오기에 대 한 자세한 내용은 [about_Modules](about_Modules.md)를 참조 하세요.

### <a name="pssessionapplicationname"></a>\$PSSessionApplicationName

WS-MANAGEMENT (관리용 웹 서비스) 기술을 사용 하는 원격 명령의 기본 응용 프로그램 이름을 지정 합니다. 자세한 내용은 [Windows 원격 관리 정보](/windows/win32/winrm/about-windows-remote-management)를 참조 하세요.

시스템 기본 응용 프로그램 이름은 이지만 `WSMAN` 이 기본 설정 변수를 사용 하 여 기본값을 변경할 수 있습니다.

응용 프로그램 이름은 연결 URI의 마지막 노드입니다. 예를 들어 다음 샘플 URI의 응용 프로그램 이름은 `WSMAN` 입니다.

`http://Server01:8080/WSMAN`

기본 응용 프로그램 이름은 원격 명령에서 연결 URI 또는 응용 프로그램 이름을 지정 하지 않을 때 사용 됩니다.

**WinRM** 서비스는 응용 프로그램 이름을 사용 하 여 연결 요청을 처리 하는 수신기를 선택 합니다. 매개 변수의 값은 원격 컴퓨터에 있는 수신기의 **Urlprefix** 속성 값과 일치 해야 합니다.

시스템 기본값과이 변수의 값을 재정의 하 고 특정 세션에 대해 다른 응용 프로그램 이름을 선택 하려면 [새-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-Pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession)또는 [Invoke 명령](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlet의 **connectionuri** 또는 **ApplicationName** 매개 변수를 사용 합니다.

`$PSSessionApplicationName`기본 설정 변수는 로컬 컴퓨터에 설정 되지만 원격 컴퓨터의 수신기를 지정 합니다. 지정 하는 응용 프로그램 이름이 원격 컴퓨터에 존재 하지 않는 경우 세션을 설정 하는 명령이 실패 합니다.

### <a name="pssessionconfigurationname"></a>\$PSSessionConfigurationName

현재 세션에서 생성 된 **pssessions** 에 사용 되는 기본 세션 구성을 지정 합니다.

이 기본 설정 변수는 로컬 컴퓨터에 설정 되지만 원격 컴퓨터에 있는 세션 구성을 지정 합니다.

변수의 값은 정규화 된 `$PSSessionConfigurationName` 리소스 URI입니다.

기본값은 `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` 원격 컴퓨터의 **Microsoft PowerShell** 세션 구성을 나타냅니다.

구성 이름만 지정 하는 경우 다음 스키마 URI가 앞에 표시 됩니다.

`http://schemas.microsoft.com/PowerShell/`

, 또는 cmdlet의 **ConfigurationName** 매개 변수를 사용 하 여 기본값을 재정의 하 고 특정 세션에 대해 다른 세션 구성을 선택할 수 있습니다 `New-PSSession` `Enter-PSSession` `Invoke-Command` .

언제 든 지이 변수의 값을 변경할 수 있습니다. 이 작업을 수행 하는 경우 선택한 세션 구성이 원격 컴퓨터에 존재 해야 합니다. 그렇지 않으면 세션 구성을 사용 하는 세션을 만드는 명령이 실패 합니다.

이 기본 설정 변수는 원격 사용자가이 컴퓨터에 연결 되는 세션을 만들 때 사용 되는 로컬 세션 구성을 결정 하지 않습니다.
그러나 로컬 세션 구성에 대 한 사용 권한을 사용 하 여 사용자가 사용할 수 있는 사용자를 결정할 수 있습니다.

### <a name="pssessionoption"></a>\$PSSessionOption

원격 세션의 고급 사용자 옵션에 대 한 기본값을 설정 합니다.
이러한 옵션 기본 설정은 세션 옵션에 대 한 시스템 기본값을 재정의 합니다.

`$PSSessionOption`변수는 **Pssessionoption** 개체를 포함 합니다. 자세한 내용은 System.web. n a m p. n a m a [옵션](/dotnet/api/system.management.automation.remoting.pssessionoption)을 참조 하십시오.
개체의 각 속성은 session 옵션을 나타냅니다. 예를 들어 **Nocompression** 속성은 세션 중에 데이터 압축을 해제 합니다.

기본적으로이 `$PSSessionOption` 변수는 아래와 같이 모든 옵션에 대 한 기본값을 포함 하는 **Pssessionoption** 개체를 포함 합니다.

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
IncludePortInSPN                  : False
OutputBufferingMode               : None
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : -00:00:00.0010000
```

이러한 옵션에 대 한 설명 및 자세한 내용은 [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)을 참조 하세요. 원격 명령 및 세션에 대 한 자세한 내용은 [about_Remote](about_Remote.md) 및 [about_PSSessions](about_PSSessions.md)를 참조 하세요.

기본 설정 변수의 값을 변경 하려면 `$PSSessionOption` cmdlet을 사용 하 여 `New-PSSessionOption` 원하는 옵션 값을 사용 하 여 **pssessionoption** 개체를 만듭니다. 출력을 이라는 변수에 저장 `$PSSessionOption` 합니다.

```powershell
$PSSessionOption = New-PSSessionOption -NoCompression
```

`$PSSessionOption`모든 powershell 세션에서 기본 설정 변수를 사용 하려면 `New-PSSessionOption` `$PSSessionOption` powershell 프로필에 변수를 만드는 명령을 추가 합니다. 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.

특정 원격 세션에 대 한 사용자 지정 옵션을 설정할 수 있습니다. 설정 하는 옵션은 시스템 기본값 및 기본 설정 변수의 값 보다 우선 적용 `$PSSessionOption` 됩니다.

사용자 지정 세션 옵션을 설정 하려면 cmdlet을 사용 `New-PSSessionOption` 하 여 **Pssessionoption** 개체를 만듭니다. 그런 다음 세션을 만드는 cmdlet의 **sessionoption** 매개 변수 값으로 **pssessionoption** 개체를 사용 합니다 (예: `New-PSSession` , 및) `Enter-PSSession` `Invoke-Command` .

### <a name="transcript"></a>$Transcript

에서 기록 `Start-Transcript` 파일의 이름과 위치를 지정 하는 데 사용 됩니다. **Path** 매개 변수의 값을 지정 하지 않으면는 `Start-Transcript` 전역 변수 값의 경로를 사용 합니다 `$Transcript` . 이 변수를 만들지 않은 경우는 `Start-Transcript` 디렉터리에 있는 기록을 파일로 저장 합니다 `$Home\My Documents` `\PowerShell_transcript.<time-stamp>.txt` .

### <a name="verbosepreference"></a>\$VerbosePreference

PowerShell에서 스크립트, cmdlet 또는 공급자에 의해 생성 된 자세한 정보 메시지 (예: [쓰기 세부 정보](xref:Microsoft.PowerShell.Utility.Write-Verbose) cmdlet에 의해 생성 된 메시지)에 응답 하는 방법을 결정 합니다.
자세한 정보 메시지는 명령을 실행 하기 위해 수행 된 작업을 설명 합니다.

기본적으로 자세한 정보 표시 메시지는 표시 되지 않지만 값을 변경 하 여이 동작을 변경할 수 있습니다 `$VerbosePreference` .

Cmdlet의 **verbose** 일반 매개 변수를 사용 하 여 특정 명령에 대 한 자세한 정보 메시지를 표시 하거나 숨길 수 있습니다. 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조하세요.

유효한 값은 다음과 같습니다.

- **Stop** : 자세한 정보 메시지와 오류 메시지를 표시 한 후 실행을 중지 합니다.
- **Inquire** : 자세한 정보 표시 메시지를 표시 한 다음 계속할지 여부를 묻는 프롬프트를 표시 합니다.
- **Continue** : 자세한 정보 메시지를 표시 한 다음 실행을 계속 합니다.
- **SilentlyContinue** : (기본값)는 자세한 정보 메시지를 표시 하지 않습니다. 계속 실행 합니다.

#### <a name="examples"></a>예

이러한 예제에서는의 여러 값 `$VerbosePreference` 과 **Verbose** 매개 변수를 통해 기본 설정 값을 재정의 하는 결과를 보여 줍니다.

이 예에서는 기본값 인 **SilentlyContinue** 값의 효과를 보여 줍니다. 이 명령은 **message** 매개 변수를 사용 하지만 PowerShell 콘솔에는 메시지를 쓰지 않습니다.

```powershell
Write-Verbose -Message "Verbose message test."
```

**Verbose** 매개 변수를 사용 하면 메시지가 기록 됩니다.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose
```

```Output
VERBOSE: Verbose message test.
```

이 예에서는 **Continue** 값의 효과를 보여 줍니다. `$VerbosePreference`변수가 **Continue** 로 설정 되 고 메시지가 표시 됩니다.

```powershell
$VerbosePreference = "Continue"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
```

이 예에서는 Continue 값을 재정의 하는 값을 사용 하 여 **Verbose** 매개 변수를 사용 `$false` 합니다. **Continue** 메시지가 표시 되지 않습니다.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

이 예에서는 **Stop** 값의 효과를 보여 줍니다. `$VerbosePreference`변수가 **Stop** 으로 설정 되 고 메시지가 표시 됩니다. 명령이 중지 되었습니다.

```powershell
$VerbosePreference = "Stop"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
Write-Verbose : The running command stopped because the preference variable
  "VerbosePreference" or common parameter is set to Stop: Verbose message test.
At line:1 char:1
+ Write-Verbose -Message "Verbose message test."
```

이 예에서는 Stop 값을 재정의 하는 값을 사용 하 여 **Verbose** 매개 변수를 사용 `$false` 합니다. **Stop** 메시지가 표시 되지 않습니다.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

이 예에서는 **Inquire** 값의 효과를 보여 줍니다. `$VerbosePreference`변수가 **Inquire** 로 설정 됩니다. 메시지가 표시 되 고 사용자에 게 확인 메시지를 표시 합니다.

```powershell
$VerbosePreference = "Inquire"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

이 예에서는 Inquire 값을 재정의 하는 값을 사용 하 여 **Verbose** 매개 변수를 사용 `$false` 합니다. **Inquire** 사용자에 게 메시지가 표시 되지 않고 메시지가 표시 되지 않습니다.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

### <a name="warningpreference"></a>\$WarningPreference

PowerShell에서 스크립트, cmdlet 또는 공급자에 의해 생성 된 경고 메시지 (예: [쓰기-경고](xref:Microsoft.PowerShell.Utility.Write-Warning) cmdlet에 의해 생성 된 메시지)에 응답 하는 방법을 결정 합니다.

기본적으로 경고 메시지가 표시 되 고 실행이 계속 되지만의 값을 변경 하 여이 동작을 변경할 수 있습니다 `$WarningPreference` .

Cmdlet의 **WarningAction** 일반 매개 변수를 사용 하 여 PowerShell이 특정 명령의 경고에 응답 하는 방법을 결정할 수 있습니다. 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조하세요.

유효한 값은 다음과 같습니다.

- **Stop** : 경고 메시지와 오류 메시지를 표시 한 다음 실행을 중지 합니다.
- **Inquire** : 경고 메시지를 표시 한 다음 사용 권한을 계속 하 라는 메시지를 표시 합니다.
- **Continue** : (기본값) 경고 메시지를 표시 한 다음 실행을 계속 합니다.
- **SilentlyContinue** : 경고 메시지를 표시 하지 않습니다. 계속 실행 합니다.

#### <a name="examples"></a>예

이러한 예제에서는의 다른 값에 대 한 결과를 보여 줍니다 `$WarningPreference` .
**WarningAction** 매개 변수는 기본 설정 값을 재정의 합니다.

이 예에서는 기본 값인 **Continue** 를 보여 줍니다.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
```

이 예제에서는 값이 **SilentlyContinue** 인 **WarningAction** 매개 변수를 사용 하 여 경고를 표시 하지 않습니다. 메시지가 표시 되지 않습니다.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

이 예에서는 `$WarningPreference` 변수를 **SilentlyContinue** 값으로 변경 합니다. 메시지가 표시 되지 않습니다.

```powershell
$WarningPreference = "SilentlyContinue"
$m = "This action can delete data."
Write-Warning -Message $m
```

이 예에서는 **WarningAction** 매개 변수를 사용 하 여 경고가 생성 되 면 중지 합니다.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Stop
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m -WarningAction Stop
```

이 예에서는 `$WarningPreference` 변수를 **Inquire** 값으로 변경 합니다. 사용자에 게 확인 메시지를 표시 합니다.

```powershell
$WarningPreference = "Inquire"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

이 예제에서는 값이 **SilentlyContinue** 인 **WarningAction** 매개 변수를 사용 합니다. 명령은 계속 실행 되며 메시지가 표시 되지 않습니다.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

이 예에서는 `$WarningPreference` 값을 **중지** 로 변경 합니다.

```powershell
$WarningPreference = "Stop"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m
```

이 예에서는 **WarningAction** 를 **Inquire** 값과 함께 사용 합니다. 경고가 발생 하면 사용자에 게 메시지가 표시 됩니다.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Inquire
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

### <a name="whatifpreference"></a>\$방식으로 whatifpreference

이를 지 원하는 모든 명령에 대해 **WhatIf** 를 자동으로 사용할지 여부를 결정 합니다. **WhatIf** 를 사용 하는 경우 cmdlet은 명령의 예상 효과를 보고 하지만 명령을 실행 하지는 않습니다.

유효한 값은 다음과 같습니다.

- **False** ( **0** , 사용 안 함): (기본값) **WhatIf** 가 자동으로 사용 하도록 설정 되어 있지 않습니다. 수동으로 사용 하도록 설정 하려면 cmdlet의 **WhatIf** 매개 변수를 사용 합니다.
- **True** ( **1** , enabled): **WhatIf** 는이를 지 원하는 모든 명령에서 자동으로 사용 하도록 설정 됩니다. 사용자는 값이 **False** 인 **WhatIf** 매개 변수를 사용 하 여와 같이 수동으로 비활성화할 수 있습니다 `-WhatIf:$false` .

#### <a name="examples"></a>예

이러한 예제에서는의 다른 값에 대 한 결과를 보여 줍니다 `$WhatIfPreference` .
**WhatIf** 매개 변수를 사용 하 여 특정 명령에 대 한 기본 설정 값을 재정의 하는 방법을 보여 줍니다.

이 예에서는 `$WhatIfPreference` 변수를 기본값인 **False** 로 설정 하는 결과를 보여 줍니다. `Get-ChildItem`파일이 있는지 확인 하는 데 사용 합니다.
`Remove-Item` 파일을 삭제 합니다. 파일이 삭제 된 후에는를 사용 하 여 삭제를 확인할 수 있습니다 `Get-ChildItem` .

```powershell
Get-ChildItem -Path .\test.txt
Remove-Item -Path ./test.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           9/13/2019    10:53             10 test.txt
```

```powershell
Get-ChildItem -Path .\test.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -File test.txt
```

이 예에서는의 값이 **WhatIf** `$WhatIfPreference` **False** 인 경우 WhatIf 매개 변수를 사용 하는 경우의 효과를 보여 줍니다.

파일이 있는지 확인하십시오.

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

**WhatIf** 매개 변수를 사용 하 여 파일을 삭제 하려는 시도의 결과를 확인 합니다.

```powershell
Remove-Item -Path .\test2.txt -WhatIf
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
``````

파일이 삭제 되지 않았는지 확인 합니다.

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

이 예에서는 `$WhatIfPreference` 변수 값을 **True** 로 설정 하는 결과를 보여 줍니다. 를 사용 하 여 파일을 삭제 하면 파일 `Remove-Item` 의 경로가 표시 되지만 파일은 삭제 되지 않습니다.

파일을 삭제 하려고 합니다. `Remove-Item`가 실행 되었지만 파일이 삭제 되지 않은 경우 발생 하는 상황에 대 한 메시지가 표시 됩니다.

```powershell
$WhatIfPreference = "True"
Remove-Item -Path .\test2.txt
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
```

`Get-ChildItem`를 사용 하 여 파일이 삭제 되지 않았는지 확인 합니다.

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

이 예에서는의 값이 True 일 때 파일을 삭제 하는 방법을 보여 줍니다 `$WhatIfPreference` . **True** 이 메서드는 값이 인 **WhatIf** 매개 변수를 사용 `$false` 합니다. `Get-ChildItem`파일이 삭제 되었는지 확인 하는 데 사용 합니다.

```powershell
Remove-Item -Path .\test2.txt -WhatIf:$false
Get-ChildItem -Path .\test2.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test2.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path .\test2.txt
```

다음은 whatif `Get-Process` 를 지원 하지 **WhatIf** 않고 `Stop-Process` **whatif** 를 지 원하는 cmdlet의 예입니다. `$WhatIfPreference`변수의 값이 **True** 입니다.

`Get-Process` 는 **WhatIf** 를 지원 하지 않습니다. 명령이 실행 되 면 **winword.exe** 프로세스를 표시 합니다.

```powershell
Get-Process -Name Winword
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    130   119.84     173.38       8.39   15024   4 WINWORD
```

`Stop-Process` 는 **WhatIf** 를 지원 합니다. **Winword.exe** 프로세스가 중지 되지 않습니다.

```powershell
Stop-Process -Name Winword
```

```Output
What if: Performing the operation "Stop-Process" on target "WINWORD (15024)".
```

`Stop-Process`값과 함께 **whatif** 매개 변수를 사용 하 여 **whatif** 동작을 재정의할 수 있습니다 `$false` . **Winword.exe** 프로세스가 중지 됩니다.

```powershell
Stop-Process -Name Winword -WhatIf:$false
```

**Winword.exe** 프로세스가 중지 되었는지 확인 하려면를 사용 `Get-Process` 합니다.

```powershell
Get-Process -Name Winword
```

```Output
Get-Process : Cannot find a process with the name "Winword".
  Verify the process name and call the cmdlet again.
At line:1 char:1
+ Get-Process -Name Winword
```

## <a name="see-also"></a>참고 항목

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_CommonParameters](about_CommonParameters.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[about_Variables](about_Variables.md)

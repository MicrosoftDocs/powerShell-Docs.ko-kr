---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA 역할 기능
description: 역할 기능은 연결하는 사용자에게 제공되어야 하는 모든 cmdlet, 함수, 공급자 및 외부 프로그램을 나열하는 PowerShell 데이터 파일이며 확장명은 .psrc입니다.
ms.openlocfilehash: 233d9081f4a8f977f0959addb5573c4566f885d0
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499997"
---
# <a name="jea-role-capabilities"></a>JEA 역할 기능

JEA 엔드포인트를 만들 때 사용자가 JEA 세션에서 수행할 수 있는 작업을 설명하는 하나 이상의 역할 기능을 정의해야 합니다. 역할 기능은 연결하는 사용자에게 제공되어야 하는 모든 cmdlet, 함수, 공급자 및 외부 프로그램을 나열하는 PowerShell 데이터 파일로서 확장명은 `.psrc`입니다.

## <a name="determine-which-commands-to-allow"></a>허용할 명령 결정

역할 기능 파일을 만드는 첫 번째 단계는 사용자가 액세스해야 하는 항목을 고려하는 것입니다. 이 요구 사항 수집 프로세스는 시간이 약간 걸릴 수 있지만, 중요한 프로세스입니다. 사용자에게 너무 적은 cmdlet 및 함수에 대한 액세스 권한을 부여하면 사용자가 작업을 수행하지 못할 수 있습니다. 너무 많은 cmdlet 및 함수에 액세스를 허용하면 사용자가 의도한 것보다 더 많은 작업을 수행할 수 있으며 보안 태세를 약화시킬 수 있습니다.

이 프로세스를 진행하는 방법은 조직과 목표에 따라 달라집니다. 다음 팁이 올바른 경로인지 확인하는 데 도움을 줍니다.

1. **식별** : 사용자가 작업을 수행하는 데 사용하는 명령을 식별합니다. 이 과정에는 IT 직원을 대상으로 설문 조사를 진행하거나 자동화 스크립트를 확인하거나 PowerShell 세션 기록 및 로그를 분석하는 작업이 포함될 수 있습니다.
2. 최상의 감사 및 JEA 사용자 지정 환경을 위해 가능한 경우 PowerShell에 해당하는 명령줄 도구를 **업데이트** 합니다. 외부 프로그램은 JEA의 네이티브 PowerShell cmdlet 및 함수만큼 세부적으로 제한할 수 없습니다.
3. 특정 매개 변수 또는 매개 변수 값만 허용하도록 cmdlet의 범위를 **제한** 합니다. 이는 사용자가 시스템의 일부만 관리해야 하는 경우에 특히 중요합니다.
4. 복잡한 명령이나 JEA에서 제한하기 어려운 명령을 대체할 사용자 지정 함수를 **만듭니다** . 복잡한 명령을 래핑하거나 추가 유효성 검사 논리를 적용하는 간단한 함수는 관리자 및 최종 사용자의 편의를 위한 추가 제어를 제공할 수 있습니다.
5. 사용자 또는 자동화 서비스로 허용되는 명령의 범위가 지정된 목록을 **테스트** 하고 필요에 따라 조정합니다.

### <a name="examples-of-potentially-dangerous-commands"></a>잠재적으로 위험한 명령의 예

JEA 엔드포인트에서 사용자가 자신의 권한을 상승시킬 수 없도록 하려면 명령을 신중하게 선택하는 것이 중요합니다.

> [!IMPORTANT]
> JEA 세션의 사용자 successCommands에 필요한 필수 정보는 승격된 권한으로 실행되는 경우가 많습니다.

다음 표에는 비제한 상태에서 허용되는 경우 악의적으로 사용될 수 있는 명령의 예가 나와 있습니다. 이는 전체 목록이 아니며 경고성 시작 지점으로만 사용되어야 합니다.

|                                            위험                                            |                                예제                                |                                                                              관련 명령                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 연결하는 사용자에게 JEA를 바이패스할 수 있는 관리자 권한 부여                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`                                                                                                        |
| 맬웨어, 익스플로잇 또는 보호를 바이패스하는 사용자 지정 스크립트와 같은 임의의 코드 실행 | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>역할 기능 파일 만들기

[New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile) cmdlet을 사용하여 새 PowerShell 역할 기능 파일을 만들 수 있습니다.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

역할에 필요한 명령을 허용하도록 결과 역할 기능 파일을 편집해야 합니다. PowerShell 도움말 문서에는 파일을 구성하는 방법의 몇 가지 예제가 포함되어 있습니다.

### <a name="allowing-powershell-cmdlets-and-functions"></a>PowerShell cmdlet 및 함수 허용

사용자에게 PowerShell cmdlet 또는 함수를 실행할 수 있는 권한을 부여하려면 VisibleCmdlets 또는 VisibleFunctions 필드에 cmdlet 또는 함수 이름을 추가합니다. 명령이 cmdlet인지 또는 함수인지 확실하지 않은 경우 `Get-Command <name>`을 실행하고 출력에서 **CommandType** 속성을 확인하면 됩니다.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

때때로 특정 cmdlet 또는 함수의 범위는 사용자의 요구 사항보다 너무 광범위합니다. 예를 들어 DNS 관리자는 DNS 서비스를 다시 시작할 수 있는 권한만 필요할 수 있습니다. 다중 테넌트 환경에서 테넌트는 셀프 서비스 관리 도구에 액세스할 수 있습니다. 테넌트는 자신의 리소스를 관리하는 것으로 제한되어야 합니다. 이러한 경우 cmdlet 또는 함수에서 노출되는 매개 변수를 제한할 수 있습니다.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

보다 고급 시나리오에서는 사용자가 이러한 매개 변수에 사용할 수 있는 값을 제한해야 할 수도 있습니다. 역할 기능을 통해 허용되는 입력을 결정하는 값 세트 또는 정규식 패턴을 정의할 수 있습니다.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> [common PowerShell parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters)(일반적인 PowerShell 매개 변수)는 사용할 수 있는 매개 변수를 제한하는 경우에도 항상 허용됩니다.
> 그러나 Parameters 필드에 해당 매개 변수를 명시적으로 나열해서는 안 됩니다.

아래 표에는 표시되는 cmdlet 또는 함수를 사용자 지정할 수 있는 다양한 방법이 설명되어 있습니다.
**VisibleCmdlets** 필드에 다음 중 하나를 조합하여 일치시킬 수 있습니다.

|                                           예제                                           |                                                             사용 사례                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` 또는 `@{ Name = 'My-Func' }`                                                      | 사용자는 매개 변수에 대한 제한 없이 `My-Func`를 실행할 수 있습니다.                                                      |
| `'MyModule\My-Func'`                                                                        | 사용자는 매개 변수에 대한 제한 없이 `MyModule` 모듈에서 `My-Func`를 실행할 수 있습니다.                           |
| `'My-*'`                                                                                    | 사용자는 동사 `My`가 포함된 모든 cmdlet 또는 함수를 실행할 수 있습니다.                                                                 |
| `'*-Func'`                                                                                  | 사용자는 명사 `Func`가 포함된 모든 cmdlet 또는 함수를 실행할 수 있습니다.                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | 사용자는 `Param1` 및 `Param2` 매개 변수를 사용하여 `My-Func`를 실행할 수 있습니다. 매개 변수에 아무 값이나 제공할 수 있습니다.          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | 사용자는 `Param1` 매개 변수를 사용하여 `My-Func`를 실행할 수 있습니다. 매개 변수에 "Value1" 및 "Value2"만 제공할 수 있습니다.        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | 사용자는 `Param1` 매개 변수를 사용하여 `My-Func`를 실행할 수 있습니다. 매개 변수에 "contoso"로 시작하는 모든 값을 제공할 수 있습니다. |

> [!WARNING]
> 최상의 보안 방식을 위해 표시되는 cmdlet 또는 함수를 정의할 때 와일드카드는 사용하지 않는 것이 좋습니다. 대신 신뢰할 수 있는 각 명령을 명시적으로 나열하여 같은 이름 지정 체계를 공유하는 다른 명령에 의도치 않게 권한이 부여되지 않도록 해야 합니다.

동일한 cmdlet 또는 함수에 **ValidatePattern** 과 **ValidateSet** 를 둘 다 적용할 수는 없습니다.

둘 다 적용할 경우 **ValidatePattern** 이 **ValidateSet** 를 재정의합니다.

**ValidatePattern** 에 대한 자세한 내용은 [이 *Hey, Scripting Guy!* 게시물](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) 및 [PowerShell 정규식](/powershell/module/microsoft.powershell.core/about/about_regular_expressions) 참조 콘텐츠를 확인하세요.

### <a name="allowing-external-commands-and-powershell-scripts"></a>외부 명령 및 PowerShell 스크립트 허용

사용자가 JEA 세션에서 실행 파일 및 PowerShell 스크립트(.ps1)를 실행할 수 있게 하려면 **VisibleExternalCommands** 필드에 각 프로그램의 전체 경로를 추가해야 합니다.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

PowerShell cmdlet 및 함수에서 허용되는 매개 변수를 제어할 수 있으므로, 가능한 경우 권한을 부여하는 외부 실행 파일에 대해 해당 PowerShell cmdlet 또는 함수를 사용할 수 있습니다.

많은 실행 파일을 통해 현재 상태를 읽은 다음, 다른 매개 변수를 제공하여 변경할 수 있습니다.

예를 들어 시스템에서 호스팅되는 네트워크 공유를 관리하는 파일 서버 관리자의 역할을 고려합니다. 공유를 관리하는 한 가지 방법은 `net share`를 사용하는 것입니다. 그러나 사용자가 명령을 사용하여 `net group Administrators unprivilegedjeauser /add`로 관리자 권한을 얻을 수 있으므로 **net.exe** 를 허용하는 것은 위험합니다. 더 안전한 옵션은 [Get-SmbShare](/powershell/module/smbshare/get-smbshare)를 허용하는 것으로, 결과는 동일하지만 범위는 훨씬 제한적입니다.

JEA 세션에서 사용자가 외부 명령을 사용할 수 있게 하려면 항상 실행 파일의 전체 경로를 지정합니다. 이렇게 하면 시스템의 다른 위치에 있는 이름이 비슷하거나 잠재적으로 악의적인 프로그램이 실행되는 것을 방지합니다.

### <a name="allowing-access-to-powershell-providers"></a>PowerShell 공급자에 대한 액세스 허용

기본적으로 JEA 세션에서는 PowerShell 공급자를 사용할 수 없습니다. 이렇게 하면 중요한 정보 및 구성 설정이 연결하는 사용자에게 공개되는 위험이 줄어듭니다.

필요한 경우 `VisibleProviders` 명령을 사용하여 PowerShell 공급자에 대한 액세스를 허용할 수 있습니다. 전체 공급자 목록을 보려면 `Get-PSProvider`를 실행합니다.

```powershell
VisibleProviders = 'Registry'
```

파일 시스템, 레지스트리, 인증서 저장소 또는 기타 중요 공급자에 액세스해야 하는 간단한 작업의 경우, 사용자를 대신하여 공급자가 작동하는 사용자 지정 함수 작성을 고려합니다. JEA 세션에서 사용할 수 있는 함수, cmdlet 및 외부 프로그램은 JEA와 동일한 제약 조건이 적용되지 않습니다. 기본적으로 모든 공급자에 액세스할 수 있습니다. 또한 JEA 엔드포인트 간에 파일을 복사해야 하는 경우 [사용자 드라이브](session-configurations.md#user-drive) 사용을 고려하세요.

### <a name="creating-custom-functions"></a>사용자 지정 함수 만들기

역할 기능 파일에서 사용자 지정 함수를 작성하여 최종 사용자에 대한 복잡한 작업을 간소화할 수 있습니다. 사용자 지정 함수는 cmdlet 매개 변수 값에 대한 고급 유효성 검사 논리가 필요한 경우에도 유용합니다. **FunctionDefinitions** 필드에서 간단한 함수를 작성할 수 있습니다.

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> JEA 사용자가 사용자 지정 함수를 실행할 수 있도록 사용자 지정 함수의 이름을 **VisibleFunctions** 필드에 잊지 말고 추가하세요.

사용자 지정 함수의 본문(스크립트 블록)은 시스템에 대한 기본 언어 모드에서 실행되며 JEA의 언어 제약 조건이 적용되지 않습니다. 즉, 함수는 파일 시스템 및 레지스트리에 액세스하고 역할 기능 파일에 표시되도록 설정되지 않은 명령을 실행할 수 있습니다. 매개 변수를 사용할 때 임의의 코드가 실행되지 않도록 주의하세요. 사용자 입력을 `Invoke-Expression`과 같은 cmdlet에 직접 연결하지 마세요.

위 예제에서 축약형 `Select-Object` 대신 FQMN(정규화된 모듈 이름) `Microsoft.PowerShell.Utility\Select-Object`가 사용되었다는 것을 알 수 있습니다.
역할 기능 파일에 정의된 함수에는 여전히 JEA 세션의 범위가 적용되며 여기에는 JEA가 기존 명령을 제한하기 위해 만드는 프록시 함수가 포함됩니다.

기본적으로 `Select-Object`는 개체에 대한 임의 속성을 선택할 수 없게 하는, 모든 JEA 세션의 제한된 cmdlet입니다. 함수에서 비제한 `Select-Object`를 사용하려면 FQMN을 사용하여 전체 구현을 명시적으로 요청해야 합니다. JEA 세션에서 제한된 cmdlet에는 함수에서 호출될 때 동일한 제약 조건이 있습니다. 자세한 내용은 [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)를 참조하세요.

여러 개의 사용자 지정 함수를 작성하는 경우 PowerShell 스크립트 모듈에 배치하는 것이 더 편리합니다. 기본 제공 및 타사 모듈을 사용할 때처럼 **VisibleFunctions** 필드를 사용하여 JEA 세션에서 해당 함수를 표시할 수 있습니다.

JEA 세션에서 탭 완료가 제대로 작동하려면 **VisibleFunctions** 목록에 기본 제공 함수 `tabexpansion2`를 포함해야 합니다.

## <a name="make-the-role-capabilities-available-to-a-configuration"></a>구성에서 역할 기능을 사용할 수 있도록 설정

PowerShell 6 이전의 경우 PowerShell에서 역할 기능 파일을 찾으려면 역할 기능 파일을 PowerShell 모듈의 **RoleCapabilities** 폴더에 저장해야 합니다. 모듈은 `$env:PSModulePath` 환경 변수에 포함된 모든 폴더에 저장할 수 있지만, `$env:SystemRoot\System32` 또는 신뢰할 수 없는 사용자가 파일을 수정할 수 있는 폴더에 배치해서는 안 됩니다.

다음 예에서는 역할 기능 파일을 호스트하기 위해 `$env:ProgramFiles` 경로에 **ContosoJEA** 라는 PowerShell 스크립트 모듈을 만듭니다.

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

PowerShell 모듈에 대한 자세한 내용은 [PowerShell 모듈 이해](/powershell/scripting/developer/windows-powershell)를 참조하세요.

PowerShell 6부터 **RoleDefinitions** 속성이 세션 구성 파일에 추가되었습니다. 이 속성을 사용하여 역할 정의에 대한 역할 구성 파일의 위치를 지정할 수 있습니다. [New-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile)의 예를 참조하세요.

## <a name="updating-role-capabilities"></a>역할 기능 업데이트

역할 기능 파일을 편집하여 언제든지 설정을 업데이트할 수 있습니다. 역할 기능이 업데이트된 후 시작되는 모든 새 JEA 세션은 수정된 기능을 반영합니다.

그러므로 역할 기능 폴더에 대한 액세스를 제어하는 것은 매우 중요합니다. 매우 신뢰할 수 있는 관리자만 역할 기능 파일을 변경할 수 있어야 합니다. 신뢰할 수 없는 사용자가 역할 기능 파일을 변경할 수 있는 경우 자신의 권한을 상승시킬 수 있는 cmdlet에 대한 액세스 권한을 쉽게 부여할 수 있습니다.

역할 기능에 대한 액세스를 제한하려는 관리자의 경우 로컬 시스템에 역할 기능 파일 및 포함하는 모듈에 대한 읽기 권한이 있는지 확인합니다.

## <a name="how-role-capabilities-are-merged"></a>역할 기능 병합 방법

JEA 세션을 입력할 때 [세션 구성 파일](session-configurations.md)의 일치하는 모든 역할 기능에 대한 액세스 권한이 사용자에게 부여됩니다. JEA는 모든 역할에서 허용되는 가장 허용적인 명령 세트를 사용자에게 제공하려고 합니다.

### <a name="visiblecmdlets-and-visiblefunctions"></a>VisibleCmdlets 및 VisibleFunctions

가장 복잡한 병합 논리는 JEA에서 제한된 매개 변수 및 매개 변수 값을 가질 수 있는 cmdlet 및 함수에 영향을 줍니다.

규칙은 다음과 같습니다.

1. cmdlet이 한 역할에서만 표시되도록 설정된 경우 적용 가능한 모든 매개 변수 제약 조건이 적용된 상태로 사용자에게 표시됩니다.
2. cmdlet이 둘 이상의 역할에서 표시되도록 설정된 경우 각 역할의 cmdlet에 대한 제약 조건이 같으면 cmdlet은 해당 제약 조건이 적용된 상태로 사용자에게 표시됩니다.
3. cmdlet이 둘 이상의 역할로 표시되고 각 역할에서 서로 다른 매개 변수 세트를 허용하는 경우, cmdlet 및 모든 역할에서 정의된 모든 매개 변수가 사용자에게 표시됩니다.
   한 역할에 매개 변수에 대한 제약 조건이 없는 경우 모든 매개 변수가 허용됩니다.
4. 한 역할은 cmdlet 매개 변수에 대한 유효성 검사 집합 또는 유효성 검사 패턴을 정의하고 다른 역할은 매개 변수를 허용하지만 매개 변수 값을 제한하지 않는 경우 유효성 검사 집합 또는 패턴이 무시됩니다.
5. 유효성 검사 집합이 둘 이상의 역할에서 같은 cmdlet 매개 변수에 대해 정의된 경우 모든 유효성 검사 집합의 모든 값이 허용됩니다.
6. 유효성 검사 패턴이 둘 이상의 역할에서 같은 cmdlet 매개 변수에 대해 정의된 경우 임의 패턴과 일치하는 모든 값이 허용됩니다.
7. 유효성 검사 집합이 하나 이상의 역할에서 정의된 경우 같은 cmdlet 매개 변수에 대한 다른 역할에 유효성 검사 패턴이 정의되어 있으면 유효성 검사 집합이 무시되고 나머지 유효성 검사 패턴에는 규칙 (6)이 적용됩니다.

다음은 이러한 규칙에 따라 역할이 병합되는 방식의 예입니다.

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a>VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess

역할 기능 파일의 다른 모든 필드는 허용되는 외부 명령, 별칭, 공급자 및 시작 스크립트의 누적 집합에 추가됩니다. 한 역할에서 사용할 수 있는 모든 명령, 별칭, 공급자 또는 스크립트는 JEA 사용자에게 제공됩니다.

한 역할 기능의 공급자와 다른 역할 기능의 cmdlet/함수/명령이 결합된 집합에서 사용자가 시스템 리소스에 의도치 않게 액세스할 수 있게 하지 않도록 주의해야 합니다.
예를 들어 한 역할에서 `Remove-Item` cmdlet을 허용하고 다른 역할에서 `FileSystem` 공급자를 허용하는 경우 JEA 사용자가 컴퓨터의 임의 파일을 삭제할 수 있는 위험이 있습니다. 사용자의 유효 권한을 식별하는 방법에 대한 자세한 내용은 [JEA 감사](audit-and-report.md) 문서에서 확인할 수 있습니다.

## <a name="next-steps"></a>다음 단계

[세션 구성 파일 만들기](session-configurations.md)

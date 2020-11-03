---
description: PowerShell의 범위에 대 한 개념을 설명 하 고 요소의 범위를 설정 하 고 변경 하는 방법을 보여 줍니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: 3e165867be5887ae15890f795531b5a3048c4550
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221202"
---
# <a name="about-scopes"></a>범위 정보

## <a name="short-description"></a>간단한 설명
PowerShell의 범위에 대 한 개념을 설명 하 고 요소의 범위를 설정 하 고 변경 하는 방법을 보여 줍니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell은 읽고 변경할 수 있는 위치를 제한 하 여 변수, 별칭, 함수 및 PowerShell 드라이브 (PSDrives)에 대 한 액세스를 보호 합니다. PowerShell에서는 범위 규칙을 사용 하 여 변경 되지 않아야 하는 항목을 실수로 변경 하지 않도록 합니다.

다음은 범위의 기본 규칙입니다.

- 범위는 중첩할 수 있습니다. 외부 범위를 부모 범위 라고 합니다. 중첩 된 범위는 해당 부모의 자식 범위입니다.

- 항목을 명시적으로 전용으로 설정 하지 않는 한 항목은 생성 된 범위와 모든 자식 범위에 표시 됩니다. 변수, 별칭, 함수 또는 PowerShell 드라이브를 하나 이상의 범위에 둘 수 있습니다.

- 범위 내에서 만든 항목은 다른 범위를 명시적으로 지정 하지 않는 한 해당 항목을 만든 범위 에서만 변경할 수 있습니다.

범위에 항목을 만들고 항목의 이름을 다른 범위의 항목과 공유 하는 경우 원래 항목이 새 항목에서 숨겨질 수 있지만 재정의 되거나 변경 되지 않습니다.

## <a name="powershell-scopes"></a>PowerShell 범위

PowerShell은 다음과 같은 범위를 지원 합니다.

- Global: PowerShell이 시작 될 때 적용 되는 범위입니다. PowerShell이 시작 될 때 제공 되는 변수 및 함수는 자동 변수 및 기본 설정 변수와 같은 전역 범위에 생성 됩니다. PowerShell 프로필의 변수, 별칭 및 함수도 전역 범위에 만들어집니다.

- Local: 현재 범위입니다. 로컬 범위는 전역 범위 또는 다른 범위 일 수 있습니다.

- 스크립트: 스크립트 파일을 실행 하는 동안 생성 되는 범위입니다. 스크립트의 명령만 스크립트 범위에서 실행 됩니다. 스크립트의 명령에 대 한 스크립트 범위는 로컬 범위입니다.

> [!NOTE]
> **Private** 이 범위가 아닙니다. 항목이 정의 된 범위를 벗어난 항목의 표시 유형을 변경 하는 [옵션](#private-option) 입니다.

## <a name="parent-and-child-scopes"></a>부모 및 자식 범위

스크립트나 함수를 실행 하거나, 세션을 만들거나, PowerShell의 새 인스턴스를 시작 하 여 새 범위를 만들 수 있습니다. 새 범위를 만들 때 결과는 부모 범위 (원래 범위)와 자식 범위 (만든 범위)입니다.

PowerShell에서 모든 범위는 전역 범위의 자식 범위 이지만 많은 범위와 많은 재귀 범위를 만들 수 있습니다.

항목을 비공개로 명시적으로 설정 하지 않으면 부모 범위의 항목을 자식 범위에서 사용할 수 있습니다. 그러나 항목을 만들 때 범위를 명시적으로 지정 하지 않는 한 자식 범위에서 만들고 변경 하는 항목은 부모 범위에 영향을 주지 않습니다.

## <a name="inheritance"></a>상속

자식 범위는 부모 범위에서 변수, 별칭 및 함수를 상속 하지 않습니다. 항목이 개인 항목이 아닌 경우 자식 범위에서 부모 범위의 항목을 볼 수 있습니다. 부모 범위를 명시적으로 지정 하 여 항목을 변경할 수 있지만 항목은 자식 범위의 일부가 아닙니다.

그러나 항목 집합을 사용 하 여 자식 범위를 만듭니다. 일반적으로 **AllScope** 옵션을 포함 하는 모든 별칭을 포함 합니다. 이 옵션은이 문서의 뒷부분에서 설명 합니다. **AllScope** 옵션을 포함 하는 모든 변수와 일부 자동 변수를 포함 합니다.

특정 범위의 항목을 찾으려면 또는의 범위 매개 변수를 사용 `Get-Variable` `Get-Alias` 합니다.

예를 들어 로컬 범위의 모든 변수를 가져오려면 다음을 입력 합니다.

```powershell
Get-Variable -Scope local
```

전역 범위의 모든 변수를 가져오려면 다음을 입력 합니다.

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a>범위 한정자

변수, 별칭 또는 함수 이름에는 다음과 같은 선택적 범위 한정자 중 하나가 포함 될 수 있습니다.

- `global:` -이름이 **전역** 범위에 존재 하도록 지정 합니다.
- `local:` -이름이 **로컬** 범위에 있는지 여부를 지정 합니다. 현재 범위는 항상 **로컬** 범위입니다.
- `private:` -이름이 **Private** 이며 현재 범위에만 표시 되도록 지정 합니다.
- `script:` -이름이 **스크립트** 범위에 존재 하도록 지정 합니다.
  **스크립트** 범위는 가장 가까운 상위 스크립트 파일의 범위 이거나 가장 가까운 상위 스크립트 파일이 없는 경우 **전역** 입니다.
- `using:` -및와 같은 cmdlet을 통해 스크립트를 실행 하는 동안 다른 범위에 정의 된 변수에 액세스 하는 데 사용 `Start-Job` `Invoke-Command` 됩니다.
- `workflow:` -이름이 워크플로 내에 존재 하도록 지정 합니다. 참고: 워크플로는 PowerShell Core에서 지원 되지 않습니다.
- `<variable-namespace>` -PowerShell PSDrive 공급자가 만든 한정자입니다.
  다음은 그 예입니다. 

  |  네임스페이스  |                    Description                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | 현재 범위에 정의 된 별칭               |
  | `Env:`      | 현재 범위에 정의 된 환경 변수 |
  | `Function:` | 현재 범위에 정의 된 함수             |
  | `Variable:` | 현재 범위에 정의 된 변수             |

스크립트의 기본 범위는 스크립트 범위입니다. 함수 및 별칭의 기본 범위는 스크립트에서 정의 된 경우에도 로컬 범위입니다.

### <a name="using-scope-modifiers"></a>범위 한정자 사용

새 변수, 별칭 또는 함수의 범위를 지정 하려면 범위 한정자를 사용 합니다.

변수의 범위 한정자에 대 한 구문은 다음과 같습니다.

```
$[<scope-modifier>:]<name> = <value>
```

함수의 범위 한정자에 대 한 구문은 다음과 같습니다.

```
function [<scope-modifier>:]<name> {<function-body>}
```

범위 한정자를 사용 하지 않는 다음 명령은 현재 또는 **지역** 범위에서 변수를 만듭니다.

```powershell
$a = "one"
```

**전역** 범위에서 동일한 변수를 만들려면 범위 한정자를 사용 합니다 `global:` .

```powershell
$global:a = "one"
```

**스크립트** 범위에서 동일한 변수를 만들려면 범위 한정자를 사용 합니다 `script:` .

```powershell
$script:a = "one"
```

범위 한정자를 함수와 함께 사용할 수도 있습니다. 다음 함수 정의는 **전역** 범위에서 함수를 만듭니다.

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

범위 한정자를 사용 하 여 다른 범위의 변수를 참조할 수도 있습니다.
다음 명령은 `$test` 먼저 로컬 범위에서 변수를 참조 한 다음 전역 범위에서 변수를 참조 합니다.

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a>`Using:`범위 한정자

Using은 원격 명령의 지역 변수를 식별 하는 특수 범위 한정자입니다. 한정자가 없으면 PowerShell은 원격 세션에서 원격 명령의 변수를 정의할 것으로 예상 합니다.

`Using`범위 한정자는 PowerShell 3.0에서 도입 되었습니다.

세션에서 실행 되지 않는 스크립트나 명령의 경우 범위 한정자를 사용 하 여 `Using` 호출 세션 범위의 변수 값을 포함 해야 합니다. 이렇게 하면 세션 외부 코드에서 해당 값에 액세스할 수 있습니다. `Using`범위 한정자는 다음 컨텍스트에서 지원 됩니다.

- 원격으로 실행 되는 명령, `Invoke-Command` **ComputerName** , **HostName** , **SSHConnection** 또는 **Session** 매개 변수를 사용 하 여 시작 (원격 세션)
- 백그라운드 작업, 시작 `Start-Job` (out-of-process 세션)
- 를 통해 시작 되는 스레드 작업 `Start-ThreadJob` (별도 스레드 세션)

컨텍스트에 따라 포함 된 변수 값은 호출자의 범위에 있는 데이터의 독립적인 복사본 이거나이에 대 한 참조입니다. 원격 및 out-of-process 세션에서 항상 독립적인 복사본입니다.

자세한 내용은 [about_Remote_Variables](about_Remote_Variables.md)를 참조 하세요.

스레드 세션에서는 참조로 전달 됩니다. 즉, 다른 스레드에서 호출 범위 변수를 수정할 수 있습니다. 변수를 안전 하 게 수정 하려면 스레드를 동기화 해야 합니다.

자세한 내용은 다음을 참조하세요.

- [Start-ThreadJob](xref:ThreadJob.Start-ThreadJob)

#### <a name="serialization-of-variable-values"></a>변수 값의 Serialization

원격으로 실행 되는 명령 및 백그라운드 작업은 out-of-process로 실행 됩니다.
Out-of-process 세션은 XML 기반 serialization 및 deserialization을 사용 하 여 프로세스 경계를 넘어 변수 값을 사용할 수 있도록 합니다. Serialization 프로세스는 개체를 원래 개체 속성이 있지만 메서드는 포함 하지 않는 **PSObject** 로 변환 합니다.

제한 된 형식 집합의 경우 deserialization 리하이드레이션 할 개체를 원래 형식으로 다시 설정 합니다. 원래 개체 인스턴스의 복사본입니다.
형식 속성 및 메서드를 포함 합니다. **System.object** 와 같은 단순 형식의 경우 복사본은 정확 합니다. 복합 형식의 경우 복사본은 아직까지 완벽입니다. 예를 들어, 공개 된 인증서 개체에는 개인 키가 포함 되지 않습니다.

다른 모든 형식의 인스턴스는 **PSObject** 인스턴스입니다. **PSTypeNames** 속성에는 **deserialize** (예:Deserialized.System) 접두사가 붙은 원래 형식 이름이 포함 **됩니다. 데이터 DataTable**

### <a name="the-allscope-option"></a>AllScope 옵션

변수와 별칭에는 **AllScope** 값을 사용할 수 있는 **Option** 속성이 있습니다. **AllScope** 속성을 포함 하는 항목은 부모 범위에서 상속 소급 되지 않지만 사용자가 만드는 모든 자식 범위의 일부가 됩니다.

**AllScope** 속성이 있는 항목은 자식 범위에 표시 되 고 해당 범위의 일부입니다. 모든 범위에서 항목을 변경 하면 변수가 정의 된 모든 범위에 영향을 줍니다.

### <a name="managing-scope"></a>범위 관리

여러 cmdlet에는 특정 범위의 항목을 가져오거나 설정 (생성 및 변경) 할 수 있도록 하는 **범위** 매개 변수가 있습니다. 다음 명령을 사용 하 여 **범위** 매개 변수가 있는 세션의 모든 cmdlet을 찾습니다.

```powershell
Get-Help * -Parameter scope
```

특정 범위에 표시 되는 변수를 찾으려면 `Scope` 의 매개 변수를 사용 `Get-Variable` 합니다. 표시 되는 변수에는 전역 변수, 부모 범위의 변수 및 현재 범위의 변수가 포함 됩니다.

예를 들어 다음 명령은 로컬 범위에 표시 되는 변수를 가져옵니다.

```powershell
Get-Variable -Scope local
```

특정 범위에서 변수를 만들려면의 범위 한정자 나 **범위** 매개 변수를 사용 `Set-Variable` 합니다. 다음 명령은 전역 범위에서 변수를 만듭니다.

```powershell
New-Variable -Scope global -Name a -Value "One"
```

, 또는 cmdlet의 범위 매개 변수를 사용 `New-Alias` 하 여 범위를 지정할 수도 있습니다 `Set-Alias` `Get-Alias` . 다음 명령은 전역 범위에서 별칭을 만듭니다.

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

특정 범위의 함수를 가져오려면 `Get-Item` 범위 내에 있는 경우 cmdlet을 사용 합니다. `Get-Item`Cmdlet에 **범위** 매개 변수가 없습니다.

> [!NOTE]
> **Scope** 매개 변수를 사용 하는 cmdlet의 경우 숫자를 기준으로 범위를 참조할 수도 있습니다. 이 숫자는 한 범위의 상대 위치를 다른 범위에 대해 설명 합니다. 범위 0은 현재 또는 지역 범위를 나타냅니다. 범위 1은 직계 부모 범위를 나타냅니다. 범위 2는 부모 범위의 부모를 나타냅니다. 번호가 매겨진 범위는 많은 재귀 범위를 만든 경우 유용 합니다.

### <a name="using-dot-source-notation-with-scope"></a>범위에 점 소스 표기법 사용

스크립트 및 함수는 모든 범위의 규칙을 따릅니다. 이를 특정 범위에서 만들면 cmdlet 매개 변수나 범위 한정자를 사용 하 여 해당 범위를 변경 하지 않는 한 해당 범위에만 영향을 줍니다.

그러나 점 원본 표기법을 사용 하 여 현재 범위에 스크립트나 함수를 추가할 수 있습니다. 그런 다음 현재 범위에서 스크립트를 실행할 때 스크립트에서 만드는 모든 함수, 별칭 및 변수를 현재 범위에서 사용할 수 있습니다.

현재 범위에 함수를 추가 하려면 함수 호출에서 함수의 경로와 이름 앞에 점 (.)과 공백을 입력 합니다.

예를 들어 스크립트 범위의 C:\Scripts 디렉터리 (스크립트의 기본값)에서 Sample.ps1 스크립트를 실행 하려면 다음 명령을 사용 합니다.

```powershell
c:\scripts\sample.ps1
```

로컬 범위에서 Sample.ps1 스크립트를 실행 하려면 다음 명령을 사용 합니다.

```powershell
. c:\scripts.sample.ps1
```

Call 연산자 (&)를 사용 하 여 함수 또는 스크립트를 실행 하는 경우 현재 범위에 추가 되지 않습니다. 다음 예에서는 call 연산자를 사용 합니다.

```powershell
& c:\scripts.sample.ps1
```

[About_operators](about_operators.md)에서 호출 연산자에 대 한 자세한 내용을 확인할 수 있습니다.

Sample.ps1 스크립트에서 만드는 모든 별칭, 함수 또는 변수는 현재 범위에서 사용할 수 없습니다.

## <a name="restricting-without-scope"></a>범위 없이 제한

몇 가지 PowerShell 개념은 범위를 포함 하거나 범위와 상호 작용 하는 것과 비슷합니다. 이러한 개념은 범위 또는 범위 동작과 혼동 될 수 있습니다.

세션, 모듈 및 중첩 된 프롬프트는 독립적인 환경 이지만 세션에서 전역 범위의 자식 범위가 아닙니다.

### <a name="sessions"></a>세션

세션은 PowerShell을 실행 하는 환경입니다. 원격 컴퓨터에서 세션을 만들 때 PowerShell은 원격 컴퓨터에 대 한 영구 연결을 설정 합니다. 영구 연결을 사용 하면 여러 관련 명령에 세션을 사용할 수 있습니다.

세션은 포함 된 환경 이기 때문에 자체 범위를 갖지만 세션이 만들어진 세션의 자식 범위가 아닙니다. 세션은 고유한 전역 범위를 사용 하 여 시작 합니다. 이 범위는 세션의 전역 범위와는 독립적입니다. 세션에서 자식 범위를 만들 수 있습니다. 예를 들어 스크립트를 실행 하 여 세션에서 자식 범위를 만들 수 있습니다.

### <a name="modules"></a>모듈

Powershell 모듈을 사용 하 여 PowerShell 도구를 공유 하 고 제공할 수 있습니다. 모듈은 cmdlet, 스크립트, 함수, 변수, 별칭 및 기타 유용한 항목을 포함할 수 있는 단위입니다. 명시적으로 정의 되지 않은 경우 모듈의 항목은 모듈 외부에서 액세스할 수 없습니다. 따라서 세션에 모듈을 추가 하 고 다른 항목이 세션의 cmdlet, 스크립트, 함수 및 기타 항목을 재정의할 수 있는 걱정 없이 공용 항목을 사용할 수 있습니다.

기본적으로 모듈은 현재 _범위가_ 아닌 현재 _세션 상태의_ 최상위 수준에 로드 됩니다. 현재 세션 상태는 모듈 세션 상태 또는 전역 세션 상태일 수 있습니다. 세션에 모듈을 추가 해도 범위는 변경 되지 않습니다. 전역 범위에 있으면 모듈이 전역 세션 상태에 로드 됩니다. 모든 내보내기는 전역 테이블에 배치 됩니다.
Module1 _내_ 에서 module2를 로드 하는 경우 module2는 전역 세션 상태가 아닌 module1의 세션 상태로 로드 됩니다. Module2에서의 모든 내보내기는 module1 세션 상태의 맨 위에 배치 됩니다. 를 사용 하는 경우 `Import-Module -Scope local` 내보내기는 최상위 수준 대신 현재 범위 개체에 배치 됩니다. _모듈에_ 있고 `Import-Module -Scope global` (또는)를 사용 하 여 `Import-Module -Global` 다른 모듈을 로드 하는 경우 해당 모듈 및 내보내기는 모듈의 로컬 세션 상태 대신 전역 세션 상태로 로드 됩니다. 이 기능은 모듈을 조작 하는 모듈을 작성 하기 위해 설계 되었습니다. **Windowscompatibility** 모듈은이를 통해 프록시 모듈을 전역 세션 상태로 가져옵니다.

세션 상태 내에서 모듈은 고유한 범위를 가집니다. 다음 모듈을 참조 `C:\temp\mod1.psm1` 하세요.

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

이제 전역 변수 `$a` 를 만들고 값을 지정 하 고 **foo** 함수를 호출 합니다.

```powershell
$a = "Goodbye"
foo
```

모듈은 모듈 범위에서 변수를 선언 하 `$a` 고 함수 **foo** 는 두 범위 모두에서 변수 값을 출력 합니다.

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a>중첩 프롬프트

중첩 된 프롬프트에는 고유한 범위가 없습니다. 중첩 된 프롬프트를 입력 하는 경우 중첩 된 프롬프트는 환경의 하위 집합입니다. 그러나 로컬 범위 내에 남아 있습니다.

스크립트에는 고유한 범위가 있습니다. 스크립트를 디버깅 하는 경우 스크립트의 중단점에 도달 하면 스크립트 범위를 입력 합니다.

### <a name="private-option"></a>개인 옵션

별칭 및 변수에는 **Private** 값을 사용할 수 있는 **Option** 속성이 있습니다. **개인** 옵션을 포함 하는 항목은 생성 된 범위에서 표시 하 고 변경할 수 있지만 해당 범위 외부에서 보거나 변경할 수는 없습니다.

예를 들어 전역 범위에 개인 옵션을 포함 하는 변수를 만든 다음 스크립트를 실행 하는 경우 `Get-Variable` 스크립트의 명령은 private 변수를 표시 하지 않습니다. 이 인스턴스에서 전역 범위 한정자를 사용 해도 전용 변수가 표시 되지 않습니다.

,, 및 cmdlet의 option 매개 변수를 사용 `New-Variable` `Set-Variable` 하 여 `New-Alias` `Set-Alias` option 속성의 값을 Private으로 설정할 수 있습니다.

### <a name="visibility"></a>가시 거리

변수 또는 별칭의 **Visibility** 속성은 컨테이너가 만들어진 컨테이너 외부에서 항목을 볼 수 있는지 여부를 결정 합니다. 컨테이너는 모듈, 스크립트 또는 스냅인 일 수 있습니다. 표시 유형은 **Option** 속성의 **전용** 값이 범위에 대해 디자인 된 것과 동일한 방식으로 컨테이너를 위해 설계 되었습니다.

**Visibility** 속성은 **Public** 및 **Private** 값을 사용 합니다. 비공개 표시를 포함 하는 항목은 해당 항목을 만든 컨테이너 에서만 보고 변경할 수 있습니다. 컨테이너를 추가 하거나 가져올 경우 개인 표시 유형을 포함 하는 항목을 보거나 변경할 수 없습니다.

표시 유형은 컨테이너를 위해 설계 되었으므로 범위에서 다르게 작동 합니다.

- 전역 범위에서 비공개로 표시 되는 항목을 만드는 경우 모든 범위에서 항목을 보거나 변경할 수 없습니다.
- 전용 표시 유형이 있는 변수의 값을 보거나 변경 하려고 하면 PowerShell에서 오류 메시지를 반환 합니다.

및 cmdlet을 사용 `New-Variable` `Set-Variable` 하 여 개인 표시 유형을 포함 하는 변수를 만들 수 있습니다.

## <a name="examples"></a>예

### <a name="example-1-change-a-variable-value-only-in-a-script"></a>예제 1: 스크립트 에서만 변수 값 변경

다음 명령은 스크립트의 변수 값을 변경 합니다 `$ConfirmPreference` . 변경 내용은 전역 범위에 영향을 주지 않습니다.

먼저 `$ConfirmPreference` 로컬 범위에서 변수의 값을 표시 하려면 다음 명령을 사용 합니다.

```
PS>  $ConfirmPreference
High
```

다음 명령을 포함 하는 Scope.ps1 스크립트를 만듭니다.

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

스크립트를 실행합니다. 스크립트는 변수의 값을 변경한 `$ConfirmPreference` 다음 스크립트 범위에서 해당 값을 보고 합니다. 출력은 다음 출력과 유사 합니다.

```output
The value of $ConfirmPreference is Low.
```

다음으로 `$ConfirmPreference` 현재 범위에서 변수의 현재 값을 테스트 합니다.

```
PS>  $ConfirmPreference
High
```

이 예에서는 스크립트 범위의 변수 값에 대 한 변경 내용이 부모 범위의 변수 값에 영향을 주지 않는다는 것을 보여 줍니다.

### <a name="example-2-view-a-variable-value-in-different-scopes"></a>예 2: 다른 범위에서 변수 값 보기

범위 한정자를 사용 하 여 로컬 범위와 부모 범위에서 변수의 값을 볼 수 있습니다.

먼저 `$test` 전역 범위에서 변수를 정의 합니다.

```powershell
$test = "Global"
```

다음으로 변수를 정의 하는 Sample.ps1 스크립트를 만듭니다 `$test` . 스크립트에서 범위 한정자를 사용 하 여 변수의 전역 또는 로컬 버전을 참조 `$test` 합니다.

Sample.ps1:

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

Sample.ps1를 실행 하는 경우 출력은 다음 출력과 유사 합니다.

```output
The local value of $test is Local.
The global value of $test is Global.
```

스크립트가 완료 되 면 세션에의 전역 값만 `$test` 정의 됩니다.

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a>예 3: 부모 범위에서 변수 값 변경

개인 옵션 또는 다른 방법을 사용 하 여 항목을 보호 하지 않는 한 부모 범위에서 변수 값을 보고 변경할 수 있습니다.

먼저 `$test` 전역 범위에서 변수를 정의 합니다.

```powershell
$test = "Global"
```

다음으로 변수를 정의 하는 Sample.ps1 스크립트를 만듭니다 `$test` . 스크립트에서 범위 한정자를 사용 하 여 변수의 전역 또는 로컬 버전을 참조 `$test` 합니다.

Sample.ps1:

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

스크립트가 완료 되 면의 전역 값 `$test` 이 변경 됩니다.

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a>예제 4: 전용 변수 만들기

Private 변수는 값이 *private* 인 **Option** 속성이 있는 변수입니다. *Private* 변수는 자식 범위에 의해 상속 되지만 해당 변수는 생성 된 범위 에서만 보거나 변경할 수 있습니다.

다음 명령은 로컬 범위에서 이라는 private 변수를 만듭니다 `$ptest` .

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

로컬 범위에서 값을 표시 하 고 변경할 수 있습니다 `$ptest` .

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

다음 명령을 포함 하는 Sample.ps1 스크립트를 만듭니다. 명령은를 표시 하 고 값을 변경 하려고 `$ptest` 합니다.

Sample.ps1:

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

`$ptest`변수는 스크립트 범위에 표시 되지 않으며 출력은 비어 있습니다.

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a>예 5: 원격 명령에서 지역 변수 사용

로컬 세션에서 만든 원격 명령의 변수에는 `Using` 범위 한정자를 사용 합니다. PowerShell에서는 원격 명령의 변수가 원격 세션에서 만들어진 것으로 가정 합니다.

구문은 다음과 같습니다.

```
$Using:<VariableName>
```

예를 들어 다음 명령은 `$Cred` 로컬 세션에서 변수를 만든 다음 `$Cred` 원격 명령에 변수를 사용 합니다.

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

Using 범위는 PowerShell 3.0에서 도입 되었습니다. PowerShell 2.0에서 로컬 세션에 변수가 생성 되었음을 나타내려면 다음 명령 형식을 사용 합니다.

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a>참고 항목

[about_Variables](about_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Functions](about_Functions.md)

[about_Script_Blocks](about_Script_Blocks.md)

[Start-ThreadJob](/powershell/module/ThreadJob/Start-ThreadJob)

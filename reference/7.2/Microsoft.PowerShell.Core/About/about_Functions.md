---
description: PowerShell에서 함수를 만들고 사용 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 02/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions
ms.openlocfilehash: d51c4d0bbf728bb23b4a5452d5192a262b722758
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602685"
---
# <a name="about-functions"></a>함수 정보

## <a name="short-description"></a>간단한 설명

PowerShell에서 함수를 만들고 사용 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

함수는 사용자가 지정 하는 이름을 가진 PowerShell 문의 목록입니다. 함수를 실행 하는 경우 함수 이름을 입력 합니다. 명령 프롬프트에서 입력 한 것 처럼 목록의 문이 실행 됩니다.

함수는 다음과 같이 간단할 수 있습니다.

```powershell
function Get-PowerShellProcess { Get-Process PowerShell }
```

함수는 cmdlet 또는 응용 프로그램 처럼 복잡할 수도 있습니다.

Cmdlet과 마찬가지로 함수에는 매개 변수를 사용할 수 있습니다. 매개 변수 이름, 위치, 스위치 또는 동적 매개 변수를 지정할 수 있습니다. 함수 매개 변수는 명령줄 이나 파이프라인에서 읽을 수 있습니다.

함수는 표시 하거나 변수에 할당 하거나 다른 함수 또는 cmdlet에 전달할 수 있는 값을 반환할 수 있습니다. 키워드를 사용 하 여 반환 값을 지정할 수도 있습니다 `return` . `return`키워드는 함수에서 반환 된 다른 출력에 영향을 주거나 표시 하지 않습니다. 그러나 키워드는 `return` 해당 줄에서 함수를 종료 합니다. 자세한 내용은 [about_Return](about_Return.md)를 참조 하세요.

함수의 문 목록에는, 및 키워드를 사용 하는 다양 한 유형의 문 목록이 포함 될 수 있습니다 `Begin` `Process` `End` . 이러한 문은 파이프라인의 핸들 입력을 다르게 나열 합니다.

필터는 키워드를 사용 하는 특수 한 종류의 함수입니다 `Filter` .

함수는 cmdlet 처럼 동작할 수도 있습니다. 프로그래밍을 사용 하지 않고 cmdlet과 마찬가지로 작동 하는 함수를 만들 수 있습니다 `C#` . 자세한 내용은 [about_Functions_Advanced](about_Functions_Advanced.md)를 참조 하세요.

## <a name="syntax"></a>Syntax

다음은 함수에 대 한 구문입니다.

```
function [<scope:>]<name> [([type]$parameter1[,[type]$parameter2])]
{
  param([type]$parameter1 [,[type]$parameter2])
  dynamicparam {<statement list>}
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

함수에는 다음 항목이 포함 됩니다.

- `Function`키워드
- 범위 (선택 사항)
- 선택한 이름
- 임의의 수의 명명 된 매개 변수 (선택 사항)
- 하나 이상의 PowerShell 명령이 중괄호로 묶여 있습니다. `{}`

`Dynamicparam`함수의 키워드 및 동적 매개 변수에 대 한 자세한 내용은 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)를 참조 하세요.

## <a name="simple-functions"></a>간단한 함수

함수는 유용 하지 않아도 됩니다. 가장 간단한 함수는 다음과 같은 형식입니다.

```
function <function-name> {statements}
```

예를 들어 다음 함수는 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다.

```powershell
function Start-PSAdmin {Start-Process PowerShell -Verb RunAs}
```

함수를 사용 하려면 다음을 입력 합니다. `Start-PSAdmin`

함수에 문을 추가 하려면 각 문을 별도의 줄에 입력 하거나 세미콜론을 사용 `;` 하 여 문을 구분 합니다.

예를 들어 다음 함수는 `.jpg` 시작 날짜 이후 변경 된 현재 사용자의 디렉터리에 있는 모든 파일을 찾습니다.

```powershell
function Get-NewPix
{
  $start = Get-Date -Month 1 -Day 1 -Year 2010
  $allpix = Get-ChildItem -Path $env:UserProfile\*.jpg -Recurse
  $allpix | Where-Object {$_.LastWriteTime -gt $Start}
}
```

유용한 작은 기능의 도구 상자를 만들 수 있습니다. 이 항목의 뒷부분에 나오는 [about_Profiles](about_Profiles.md) 에 설명 된 대로 PowerShell 프로필에 이러한 함수를 추가 합니다.

## <a name="function-names"></a>함수 이름

함수에 임의의 이름을 지정할 수 있지만 다른 사용자와 공유 하는 함수는 모든 PowerShell 명령에 대해 설정 된 명명 규칙을 따라야 합니다.

함수 이름은 동사가 함수에서 수행 하는 작업을 식별 하는 동사-명사 쌍으로 구성 되어야 하며, 명사는 cmdlet이 해당 동작을 수행 하는 항목을 식별 합니다.

함수는 모든 PowerShell 명령에 대해 승인 된 표준 동사를 사용 해야 합니다. 이러한 동사는 사용자가 쉽게 이해할 수 있도록 명령 이름을 간단 하 고 일관 된 상태로 유지 하는 데 도움이 됩니다.

표준 PowerShell 동사에 대 한 자세한 내용은 Microsoft Docs에서 [승인 된 동사](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) 를 참조 하세요.

## <a name="functions-with-parameters"></a>매개 변수가 있는 함수

명명 된 매개 변수, 위치 매개 변수, 스위치 매개 변수 및 동적 매개 변수를 포함 하 여 함수에 매개 변수를 사용할 수 있습니다. 함수의 동적 매개 변수에 대 한 자세한 내용은 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)를 참조 하세요.

### <a name="named-parameters"></a>명명된 매개 변수

원하는 수의 명명 된 매개 변수를 정의할 수 있습니다. 이 항목의 뒷부분에 설명 된 대로 명명 된 매개 변수에 대 한 기본값을 포함할 수 있습니다.

다음 샘플 구문과 같이 키워드를 사용 하 여 중괄호 안에 매개 변수를 정의할 수 있습니다 `Param` .

```
function <name> {
  param ([type]$parameter1[,[type]$parameter2])
  <statement list>
}
```

`Param`다음 샘플 구문에서와 같이 키워드 없이 중괄호 외부에 매개 변수를 정의할 수도 있습니다.

```powershell
function <name> [([type]$parameter1[,[type]$parameter2])] {
  <statement list>
}
```

다음은이 대체 구문의 예입니다.

```powershell
Function Add-Numbers($one, $two) {
    $one + $two
}
```

첫 번째 방법은 기본 설정 이지만 이러한 두 방법의 차이점은 없습니다.

함수를 실행 하면 매개 변수에 대해 제공 하는 값이 매개 변수 이름을 포함 하는 변수에 할당 됩니다. 이 변수의 값은 함수에서 사용할 수 있습니다.

다음 예제는 라는 함수입니다 `Get-SmallFiles` . 이 함수에는 `$Size` 매개 변수가 있습니다. 함수는 매개 변수 값 보다 작은 모든 파일 `$Size` 을 표시 하 고 디렉터리를 제외 합니다.

```powershell
function Get-SmallFiles {
  Param($Size)
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

함수에서 `$Size` 매개 변수에 대해 정의 된 이름인 변수를 사용할 수 있습니다.

이 함수를 사용 하려면 다음 명령을 입력 합니다.

```powershell
Get-SmallFiles -Size 50
```

매개 변수 이름 없이 명명 된 매개 변수에 대 한 값을 입력할 수도 있습니다.
예를 들어 다음 명령은 **Size** 매개 변수의 이름을 나타내는 명령과 동일한 결과를 제공 합니다.

```powershell
Get-SmallFiles 50
```

매개 변수의 기본값을 정의 하려면 다음 예제의 변형에 표시 된 것 처럼 매개 변수 이름 뒤에 등호와 값을 입력 합니다 `Get-SmallFiles` .

```powershell
function Get-SmallFiles ($Size = 100) {
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

값 없이를 입력 하 `Get-SmallFiles` 는 경우 함수는 100를에 할당 `$size` 합니다. 값을 제공 하는 경우 함수는 해당 값을 사용 합니다.

필요에 따라 매개 변수 설명에 **psdefaultvalue** 특성을 추가 하 고 **psdefaultvalue** 의 **help** 속성을 지정 하 여 매개 변수의 기본값을 설명 하는 간단한 도움말 문자열을 제공할 수 있습니다. 함수에서 **Size** 매개 변수의 기본값 (100)을 설명 하는 도움말 문자열을 제공 하려면 `Get-SmallFiles` 다음 예제와 같이 **psdefaultvalue** 특성을 추가 합니다.

```powershell
function Get-SmallFiles {
  param (
      [PSDefaultValue(Help = '100')]
      $Size = 100
  )
}
```

**Psdefaultvalue** 특성 클래스에 대 한 자세한 내용은 [Psdefaultvalue 특성 멤버](/dotnet/api/system.management.automation.psdefaultvalueattribute)를 참조 하십시오.

### <a name="positional-parameters"></a>위치 매개 변수

위치 매개 변수는 매개 변수 이름이 없는 매개 변수입니다. PowerShell은 매개 변수 값 순서를 사용 하 여 각 매개 변수 값을 함수의 매개 변수와 연결 합니다.

위치 매개 변수를 사용 하는 경우 함수 이름 뒤에 하나 이상의 값을 입력 합니다. 위치 매개 변수 값은 `$args` 배열 변수에 할당 됩니다.
함수 이름 다음에 오는 값은 배열의 첫 번째 위치에 할당 됩니다 `$args` `$args[0]` .

다음 `Get-Extension` 함수는 사용자가 `.txt` 제공 하는 파일 이름에 파일 이름 확장명을 추가 합니다.

```powershell
function Get-Extension {
  $name = $args[0] + ".txt"
  $name
}
```

```powershell
Get-Extension myTextFile
```

```Output
myTextFile.txt
```

### <a name="switch-parameters"></a>스위치 매개 변수

스위치는 값이 필요 없는 매개 변수입니다. 대신 함수 이름, 스위치 매개 변수 이름을 차례로 입력 합니다.

스위치 매개 변수를 정의 하려면 `[switch]` 다음 예제와 같이 매개 변수 이름 앞에 유형을 지정 합니다.

```powershell
function Switch-Item {
  param ([switch]$on)
  if ($on) { "Switch on" }
  else { "Switch off" }
}
```

`On`함수 이름 뒤에 switch 매개 변수를 입력 하면 함수는 "switch on"을 표시 합니다. 스위치 매개 변수를 사용 하지 않으면 "Switch off"가 표시 됩니다.

```powershell
Switch-Item -on
```

```Output
Switch on
```

```powershell
Switch-Item
```

```Output
Switch off
```

또한 다음 예제와 같이 함수를 실행할 때 스위치에 **부울** 값을 할당할 수 있습니다.

```powershell
Switch-Item -on:$true
```

```Output
Switch on
```

```powershell
Switch-Item -on:$false
```

```Output
Switch off
```

## <a name="using-splatting-to-represent-command-parameters"></a>스 플랫를 사용 하 여 명령 매개 변수 표시

스 플랫를 사용 하 여 명령의 매개 변수를 나타낼 수 있습니다. 이 기능은 Windows PowerShell 3.0에서 도입 되었습니다.

세션에서 명령을 호출 하는 함수에서이 방법을 사용 합니다. 명령 매개 변수를 선언 또는 열거 하거나 명령 매개 변수가 변경 될 때 함수를 변경 하지 않아도 됩니다.

다음 샘플 함수는 cmdlet를 호출 합니다 `Get-Command` . 명령은를 사용 `@Args` 하 여의 매개 변수를 나타냅니다 `Get-Command` .

```powershell
function Get-MyCommand { Get-Command @Args }
```

`Get-Command`함수를 호출할 때의 모든 매개 변수를 사용할 수 있습니다 `Get-MyCommand` . 매개 변수 및 매개 변수 값은를 사용 하 여 명령에 전달 됩니다 `@Args` .

```powershell
Get-MyCommand -Name Get-ChildItem
```

```Output
CommandType     Name                ModuleName
-----------     ----                ----------
Cmdlet          Get-ChildItem       Microsoft.PowerShell.Management
```

`@Args`이 기능은 선언 되지 `$Args` 않은 cmdlet 매개 변수와 나머지 인수 값을 나타내는 자동 매개 변수를 사용 합니다.

스 플랫에 대 한 자세한 내용은 [about_Splatting](about_Splatting.md)를 참조 하세요.

## <a name="piping-objects-to-functions"></a>함수에 개체 파이핑

모든 함수는 파이프라인에서 입력을 가져올 수 있습니다. 함수에서 `Begin` , 및 키워드를 사용 하 여 파이프라인의 입력을 처리 하는 방법을 제어할 수 있습니다 `Process` `End` . 다음 샘플 구문에서는 세 가지 키워드를 보여 줍니다.

```
function <name> {
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

`Begin`문 목록은 함수 시작 부분에서 한 번만 실행 됩니다.

> [!IMPORTANT]
> 함수에서 또는 블록을 정의 하는 경우 `Begin` `Process` `End` 모든 코드는 해당 블록 내에 상주해 야 합니다. 블록 *을 정의 하는 경우 블록* 외부에서 코드가 인식 되지 않습니다.

`Process`문 목록은 파이프라인의 각 개체에 대해 한 번씩 실행 됩니다.
`Process`블록이 실행 되는 동안 각 파이프라인 개체는 `$_` 한 번에 하나의 파이프라인 개체와 자동 변수에 할당 됩니다.

함수는 파이프라인의 모든 개체를 수신 하 고 나면 `End` 문 목록이 한 번 실행 됩니다. `Begin`, `Process` 또는 키워드를 사용 하지 않으면 `End` 모든 문이 문 목록 처럼 처리 됩니다 `End` .

다음 함수는 키워드를 사용 합니다 `Process` . 함수는 파이프라인의 예제를 표시 합니다.

```powershell
function Get-Pipeline
{
  process {"The value is: $_"}
}
```

이 함수를 보여 주기 위해 다음 예제와 같이 쉼표로 구분 된 숫자 목록을 입력 합니다.

```powershell
1,2,4 | Get-Pipeline
```

```Output
The value is: 1
The value is: 2
The value is: 4
```

파이프라인에서 함수를 사용 하는 경우 함수로 파이프 된 개체가 `$input` 자동 변수에 할당 됩니다. 함수는 `Begin` 파이프라인에서 개체를 가져오도록 키워드를 사용 하 여 문을 실행 합니다. 함수는 `End` 파이프라인에서 모든 개체를 받은 후 키워드를 사용 하 여 문을 실행 합니다.

다음 예에서는 `$input` 및 키워드가 있는 자동 변수를 보여 줍니다 `Begin` `End` .

```powershell
function Get-PipelineBeginEnd
{
  begin {"Begin: The input is $input"}
  end {"End:   The input is $input" }
}
```

파이프라인을 사용 하 여이 함수를 실행 하면 다음과 같은 결과가 표시 됩니다.

```powershell
1,2,4 | Get-PipelineBeginEnd
```

```Output
Begin: The input is
End:   The input is 1 2 4
```

`Begin`문이 실행 될 때 함수는 파이프라인의 입력을 포함 하지 않습니다. `End`함수는 함수 값을 포함 한 후 실행 됩니다.

함수에 키워드가 있는 경우 `Process` 의 각 개체 `$input` 는에서 제거 되 `$input` 고에 할당 됩니다 `$_` . 다음 예제에는 `Process` 문 목록이 있습니다.

```powershell
function Get-PipelineInput
{
  process {"Processing:  $_ " }
  end {"End:   The input is: $input" }
}
```

이 예제에서 함수로 파이프 된 각 개체는 문 목록으로 전송 됩니다 `Process` . `Process`문은 각 개체에서 한 번에 하나의 개체에 대해 실행 됩니다. `$input`함수가 키워드에 도달 하면 자동 변수가 비어 `End` 있습니다.

```powershell
1,2,4 | Get-PipelineInput
```

```Output
Processing:  1
Processing:  2
Processing:  4
End:   The input is:
```

자세한 내용은 [열거자 사용](about_Automatic_Variables.md#using-enumerators) 을 참조 하세요.

## <a name="filters"></a>필터

필터는 파이프라인의 각 개체에 대해 실행 되는 함수 유형입니다. 필터는 블록의 모든 문을 포함 하는 함수와 유사 `Process` 합니다.

필터의 구문은 다음과 같습니다.

```
filter [<scope:>]<name> {<statement list>}
```

다음 필터는 파이프라인에서 로그 항목을 가져온 다음 전체 항목이 나 항목의 메시지 부분만 표시 합니다.

```powershell
filter Get-ErrorLog ([switch]$message)
{
  if ($message) { Out-Host -InputObject $_.Message }
  else { $_ }
}
```

## <a name="function-scope"></a>함수 범위

함수가 생성 된 범위에 있습니다.

함수가 스크립트의 일부인 경우 해당 스크립트 내의 문에서 함수를 사용할 수 있습니다. 기본적으로 스크립트의 함수는 명령 프롬프트에서 사용할 수 없습니다.

함수의 범위를 지정할 수 있습니다. 예를 들어 함수는 다음 예제에서 전역 범위에 추가 됩니다.

```powershell
function global:Get-DependentSvs {
  Get-Service | Where-Object {$_.DependentServices}
}
```

함수가 전역 범위에 있으면 스크립트, 함수 및 명령줄에서 함수를 사용할 수 있습니다.

함수는 일반적으로 범위를 만듭니다. 함수에서 생성 된 항목 (예: 변수)은 함수 범위에만 존재 합니다.

PowerShell의 범위에 대 한 자세한 내용은 [about_Scopes](about_Scopes.md)를 참조 하세요.

## <a name="finding-and-managing-functions-using-the-function-drive"></a>함수를 사용 하 여 함수 찾기 및 관리: 드라이브

PowerShell의 모든 함수와 필터가 자동으로 드라이브에 저장 됩니다 `Function:` . 이 드라이브는 PowerShell **함수** 공급자에 의해 노출 됩니다.

드라이브를 참조할 때 `Function:` 컴퓨터의 또는 드라이브를 참조할 때와 마찬가지로 **함수** 뒤에 콜론을 입력 `C` `D` 합니다.

다음 명령은 PowerShell의 현재 세션에 있는 모든 함수를 표시 합니다.

```powershell
Get-ChildItem function:
```

함수의 명령은 함수의 정의 속성에 스크립트 블록으로 저장 됩니다. 예를 들어 PowerShell과 함께 제공 되는 도움말 함수의 명령을 표시 하려면 다음을 입력 합니다.

```powershell
(Get-ChildItem function:help).Definition
```

다음 구문을 사용할 수도 있습니다.

```powershell
$function:help
```

드라이브에 대 한 자세한 내용은 `Function:` **함수** 공급자에 대 한 도움말 항목을 참조 하십시오. `Get-Help Function`.

## <a name="reusing-functions-in-new-sessions"></a>새 세션에서 함수 다시 사용

PowerShell 명령 프롬프트에서 함수를 입력 하면 함수가 현재 세션의 일부가 됩니다. 세션이 종료 될 때까지 사용할 수 있습니다.

모든 PowerShell 세션에서 함수를 사용 하려면 PowerShell 프로필에 함수를 추가 합니다. 프로필에 대한 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조하세요.

PowerShell 스크립트 파일에 함수를 저장할 수도 있습니다. 텍스트 파일에 함수를 입력 한 다음 파일 이름 확장명을 사용 하 여 파일을 저장 `.ps1` 합니다.

## <a name="writing-help-for-functions"></a>함수에 대 한 도움말 작성

`Get-Help`Cmdlet은 함수 및 cmdlet, 공급자 및 스크립트에 대 한 도움말을 가져옵니다. 함수에 대 한 도움말을 보려면를 입력 한 `Get-Help` 다음 함수 이름을 입력 합니다.

예를 들어 함수에 대 한 도움말을 보려면 `Get-MyDisks` 다음을 입력 합니다.

```powershell
Get-Help Get-MyDisks
```

다음 두 가지 방법 중 하나를 사용 하 여 함수에 대 한 도움말을 작성할 수 있습니다.

- 함수에 대 한 Comment-Based 도움말

  주석에 특수 키워드를 사용 하 여 도움말 항목을 만듭니다. 함수에 대 한 주석 기반 도움말을 만들려면 주석을 함수 본문의 시작 또는 끝 이나 함수 키워드 앞의 줄에 배치 해야 합니다. 주석 기반 도움말에 대 한 자세한 내용은 [about_Comment_Based_Help](about_Comment_Based_Help.md)를 참조 하세요.

- 함수에 대 한 XML-Based 도움말

  일반적으로 cmdlet에 대해 생성 되는 형식과 같은 XML 기반 도움말 항목을 만듭니다. 도움말 항목을 여러 언어로 지역화 하는 경우에는 XML 기반 도움말이 필요 합니다.

  함수를 XML 기반 도움말 항목과 연결 하려면 `.ExternalHelp` 주석 기반 도움말 키워드를 사용 합니다. 이 키워드가 없으면 `Get-Help` 함수 도움말 항목을 찾을 수 없습니다 `Get-Help` . 함수에 대 한 호출은 자동 생성 된 도움말만 반환 합니다.

  키워드에 대 한 자세한 내용은 `ExternalHelp` [about_Comment_Based_Help](about_Comment_Based_Help.md)를 참조 하세요. XML 기반 도움말에 대 한 자세한 내용은 [Cmdlet 도움말을 작성 하는 방법](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Parameters](about_Parameters.md)

[about_Profiles](about_Profiles.md)

[about_Scopes](about_Scopes.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Function_provider](about_Function_provider.md)

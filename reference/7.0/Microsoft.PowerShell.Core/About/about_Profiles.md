---
description: PowerShell 프로필을 만들고 사용 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Profiles
ms.openlocfilehash: 3fe32a83ad1a63d64d293559c79f1465828d0a0a
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195001"
---
# <a name="about-profiles"></a>프로필 정보

## <a name="short-description"></a>간단한 설명
PowerShell 프로필을 만들고 사용 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell 프로필을 만들어 환경을 사용자 지정하고 시작하는 모든 PowerShell 세션에 세션별 요소를 추가할 수 있습니다.

PowerShell 프로필은 PowerShell이 시작될 때 실행되는 스크립트입니다. 프로필을 로그온 스크립트로 사용 하 여 환경을 사용자 지정할 수 있습니다. 명령, 별칭, 함수, 변수, 스냅인, 모듈 및 PowerShell 드라이브를 추가할 수 있습니다. 또한 다른 세션 관련 요소를 프로필에 추가 하 여 해당 요소를 가져오거나 다시 만들지 않고도 모든 세션에서 사용할 수 있습니다.

PowerShell은 사용자 및 호스트 프로그램에 대해 여러 프로필을 지원 합니다. 그러나 프로필을 만들지는 않습니다. 이 항목에서는 프로필에 대해 설명 하 고 컴퓨터에서 프로필을 만들고 유지 관리 하는 방법을 설명 합니다.

PowerShell 콘솔 (PowerShell.exe)의 **Noprofile** 매개 변수를 사용 하 여 프로필 없이 powershell을 시작 하는 방법을 설명 합니다. 또한 프로필에 대 한 PowerShell 실행 정책의 영향을 설명 합니다.

## <a name="the-profile-files"></a>프로필 파일

PowerShell은 여러 프로필 파일을 지원 합니다. 또한 PowerShell 호스트 프로그램은 고유한 호스트 특정 프로필을 지원할 수 있습니다.

예를 들어 PowerShell 콘솔은 다음과 같은 기본 프로필 파일을 지원 합니다. 프로필은 우선 순위에 따라 나열 됩니다. 첫 번째 프로필은 우선 순위가 가장 높습니다.

|설명               | 경로                                          |
|--------------------------|-----------------------------------------------|
|모든 사용자, 모든 호스트      |$PSHOME \\Profile.ps1                           |
|모든 사용자, 현재 호스트   |$PSHOME \\Microsoft.PowerShell_profile.ps1      |
|현재 사용자, 모든 호스트   |$Home \\ [My] 문서 \\ PowerShell \\Profile.ps1 |
|현재 사용자, 현재 호스트|$Home \\ [My] 문서 \\ PowerShell\\<br>Microsoft.PowerShell_profile.ps1 |

프로필 경로에는 다음 변수가 포함 됩니다.

- `$PSHOME`PowerShell의 설치 디렉터리를 저장 하는 변수
- `$Home`현재 사용자의 홈 디렉터리를 저장 하는 변수입니다.

또한 PowerShell을 호스트 하는 다른 프로그램은 자신의 프로필을 지원할 수 있습니다. 예를 들어 Visual Studio Code는 다음과 같은 호스트 특정 프로필을 지원 합니다.

|설명               | 경로                                     |
|--------------------------|------------------------------------------|
|모든 사용자, 현재 호스트   |$PSHOME \\Microsoft.VSCode_profile.ps1|
|현재 사용자, 현재 호스트|$Home \\ [My] 문서 \\ PowerShell\\<br>Microsoft.VSCode_profile.ps1|

PowerShell 도움말에서 "CurrentUser, Current Host" 프로필은 가장 흔히 "PowerShell 프로필" 이라고 하는 프로필입니다.

## <a name="the-profile-variable"></a>$PROFILE 변수

`$PROFILE`자동 변수는 현재 세션에서 사용할 수 있는 PowerShell 프로필에 대 한 경로를 저장 합니다.

프로필 경로를 보려면 변수 값을 표시 `$PROFILE` 합니다. `$PROFILE`명령에서 변수를 사용 하 여 경로를 나타낼 수도 있습니다.

`$PROFILE`변수는 "현재 사용자, 현재 호스트" 프로필에 대 한 경로를 저장 합니다. 다른 프로필은 변수의 메모 속성에 저장 됩니다 `$PROFILE` .

예를 들어 `$PROFILE` 변수는 Windows PowerShell 콘솔에서 다음 값을 갖습니다.

|설명                |Name                              |
|---------------------------|----------------------------------|
|현재 사용자, 현재 호스트 |`$PROFILE`                        |
|현재 사용자, 현재 호스트 |`$PROFILE.CurrentUserCurrentHost` |
|현재 사용자, 모든 호스트    |`$PROFILE.CurrentUserAllHosts`    |
|모든 사용자, 현재 호스트    |`$PROFILE.AllUsersCurrentHost`    |
|모든 사용자, 모든 호스트       |`$PROFILE.AllUsersAllHosts`       |

변수의 값이 `$PROFILE` 각 사용자와 각 호스트 응용 프로그램에 대해 변경 되기 때문에 사용 하는 각 PowerShell 호스트 응용 프로그램에 프로필 변수의 값을 표시 해야 합니다.

변수의 현재 값을 확인 하려면 `$PROFILE` 다음을 입력 합니다.

```powershell
$PROFILE | Get-Member -Type NoteProperty
```

`$PROFILE`많은 명령에서 변수를 사용할 수 있습니다. 예를 들어 다음 명령은 메모장에서 "현재 사용자, 현재 호스트" 프로필을 엽니다.

```powershell
notepad $PROFILE
```

다음 명령은 로컬 컴퓨터에서 "모든 사용자, 모든 호스트" 프로필을 만들었는지 여부를 결정 합니다.

```powershell
Test-Path -Path $PROFILE.AllUsersAllHosts
```

## <a name="how-to-create-a-profile"></a>프로필을 만드는 방법

PowerShell 프로필을 만들려면 다음 명령 형식을 사용 합니다.

```powershell
if (!(Test-Path -Path <profile-name>)) {
  New-Item -ItemType File -Path <profile-name> -Force
}
```

예를 들어 현재 PowerShell 호스트 응용 프로그램에서 현재 사용자에 대 한 프로필을 만들려면 다음 명령을 사용 합니다.

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

이 명령에서 `If` 문은 기존 프로필을 덮어쓰는 것을 방지 합니다. 자리 표시자의 값을 \<profile-path\> 만들려는 프로필 파일의 경로로 바꿉니다.

> [!NOTE]
> Windows Vista 및 이후 버전의 Windows에서 "모든 사용자" 프로필을 만들려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.

## <a name="how-to-edit-a-profile"></a>프로필을 편집 하는 방법

메모장과 같은 텍스트 편집기에서 PowerShell 프로필을 열 수 있습니다.

메모장의 현재 PowerShell 호스트 응용 프로그램에서 현재 사용자의 프로필을 열려면 다음을 입력 합니다.

```powershell
notepad $PROFILE
```

다른 프로필을 열려면 프로필 이름을 지정 합니다. 예를 들어 모든 호스트 응용 프로그램의 모든 사용자에 대 한 프로필을 열려면 다음을 입력 합니다.

```powershell
notepad $PROFILE.AllUsersAllHosts
```

변경 내용을 적용 하려면 프로필 파일을 저장 한 다음 PowerShell을 다시 시작 합니다.

## <a name="how-to-choose-a-profile"></a>프로필을 선택 하는 방법

여러 호스트 응용 프로그램을 사용 하는 경우 모든 호스트 응용 프로그램에서 사용 하는 항목을 프로필에 저장 `$PROFILE.CurrentUserAllHosts` 합니다. 호스트 응용 프로그램에 대 한 배경색을 설정 하는 명령 (예: 호스트 응용 프로그램에 해당 하는 프로필)에서 호스트 응용 프로그램과 관련 된 항목을 배치 합니다.

여러 사용자를 위해 PowerShell을 사용자 지정 하는 관리자의 경우 다음 지침을 따르세요.

- 프로필에 공통 항목 저장 `$PROFILE.AllUsersAllHosts`
- 호스트 응용 프로그램과 관련 된 프로필의 호스트 응용 프로그램과 관련 된 항목을 저장 `$PROFILE.AllUsersCurrentHost` 합니다.
- 특정 사용자에 대 한 항목을 사용자 특정 프로필에 저장

PowerShell 프로필의 특별 한 구현에 대해서는 호스트 응용 프로그램 설명서를 참조 하세요.

## <a name="how-to-use-a-profile"></a>프로필을 사용 하는 방법

PowerShell에서 만드는 대부분의 항목과 대부분의 명령은 현재 세션에만 영향을 줍니다. 세션을 종료 하면 항목이 삭제 됩니다.

세션 관련 명령 및 항목에는 변수, 기본 설정 변수, 별칭, 함수, 명령 ( [set-executionpolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)제외) 및 세션에 추가 하는 PowerShell 모듈이 포함 됩니다.

이러한 항목을 저장 하 고 이후의 모든 세션에서 사용할 수 있게 하려면 PowerShell 프로필에 추가 합니다.

프로필의 또 다른 일반적인 용도는 자주 사용 하는 함수, 별칭 및 변수를 저장 하는 것입니다. 프로필에 항목을 저장 하는 경우 해당 항목을 다시 만들지 않고 해당 세션에서 사용할 수 있습니다.

## <a name="how-to-start-a-profile"></a>프로필을 시작 하는 방법

프로필 파일을 열면 비어 있습니다. 그러나 자주 사용 하는 변수, 별칭 및 명령으로 채울 수 있습니다.

다음은 시작 하기 위한 몇 가지 제안 사항입니다.

### <a name="add-commands-that-make-it-easy-to-open-your-profile"></a>프로필을 쉽게 열 수 있도록 하는 명령 추가

"현재 사용자, 현재 호스트" 프로필 이외의 프로필을 사용 하는 경우 특히 유용 합니다. 예를 들어 다음 명령을 추가 합니다.

```powershell
function Pro {notepad $PROFILE.CurrentUserAllHosts}
```

### <a name="add-a-function-that-lists-the-aliases-for-any-cmdlet"></a>모든 cmdlet에 대 한 별칭을 나열 하는 함수를 추가 합니다.

```powershell
function Get-CmdletAlias ($cmdletname) {
  Get-Alias |
    Where-Object -FilterScript {$_.Definition -like "$cmdletname"} |
      Format-Table -Property Definition, Name -AutoSize
}
```

### <a name="customize-your-console"></a>콘솔 사용자 지정

```powershell
function Color-Console {
  $Host.ui.rawui.backgroundcolor = "white"
  $Host.ui.rawui.foregroundcolor = "black"
  $hosttime = (Get-ChildItem -Path $PSHOME\PowerShell.exe).CreationTime
  $hostversion="$($Host.Version.Major)`.$($Host.Version.Minor)"
  $Host.UI.RawUI.WindowTitle = "PowerShell $hostversion ($hosttime)"
  Clear-Host
}
Color-Console
```

### <a name="add-a-customized-powershell-prompt"></a>사용자 지정 된 PowerShell 프롬프트 추가

```powershell
function Prompt
{
$env:COMPUTERNAME + "\" + (Get-Location) + "> "
}
```

PowerShell 프롬프트에 대 한 자세한 내용은 [about_Prompts](about_Prompts.md)를 참조 하세요.

## <a name="the-noprofile-parameter"></a>NoProfile 매개 변수

프로필 없이 PowerShell을 시작 하려면 PowerShell을 시작 하는 프로그램인 **PowerShell.exe** 의 **noprofile** 매개 변수를 사용 합니다.

시작 하려면 PowerShell을 시작할 수 있는 프로그램 (예: Cmd.exe 또는 PowerShell)을 엽니다. Windows에서 실행 대화 상자를 사용할 수도 있습니다.

유형:

```
PowerShell -NoProfile
```

PowerShell.exe 매개 변수의 전체 목록을 보려면 다음을 입력 하십시오.

```
PowerShell -?
```

## <a name="profiles-and-execution-policy"></a>프로필 및 실행 정책

PowerShell 실행 정책은 프로필을 포함 하 여 스크립트를 실행 하 고 구성 파일을 로드할 수 있는지 여부를 결정 합니다. **제한** 된 실행 정책이 기본값입니다. 프로필을 포함 하 여 모든 스크립트가 실행 되지 않도록 합니다. "제한 됨" 정책을 사용 하는 경우 프로필이 실행 되지 않으며 해당 콘텐츠가 적용 되지 않습니다.

`Set-ExecutionPolicy`명령은 실행 정책을 설정 하 고 변경 합니다. 이 값은 레지스트리에 저장 되기 때문에 모든 PowerShell 세션에서 적용 되는 몇 가지 명령 중 하나입니다. 콘솔을 열 때 설정할 필요는 없으며, `Set-ExecutionPolicy` 프로필에 명령을 저장할 필요가 없습니다.

## <a name="profiles-and-remote-sessions"></a>프로필 및 원격 세션

PowerShell 프로필은 원격 세션에서 자동으로 실행 되지 않으므로 프로필이 추가 하는 명령이 원격 세션에 존재 하지 않습니다. 또한 `$PROFILE` 자동 변수는 원격 세션에서 채워지지 않습니다.

세션에서 프로필을 실행 하려면 [Invoke Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlet을 사용 합니다.

예를 들어 다음 명령은의 세션에서 로컬 컴퓨터의 "현재 사용자, 현재 호스트" 프로필을 실행 합니다 `$s` .

```powershell
Invoke-Command -Session $s -FilePath $PROFILE
```

다음 명령은의 세션에 있는 원격 컴퓨터에서 "현재 사용자, 현재 호스트" 프로필을 실행 합니다 `$s` . `$PROFILE`변수가 채워지지 않으므로 명령은 프로필에 대 한 명시적 경로를 사용 합니다. 사용자의 범위가 아니라 원격 컴퓨터의 현재 범위에서 프로필이 실행 되도록 점 소싱 연산자를 사용 합니다.

```powershell
Invoke-Command -Session $s -ScriptBlock {
  . "$HOME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

이 명령을 실행 한 후 프로필을 세션에 추가 하는 명령은에서 사용할 수 있습니다 `$s` .

## <a name="see-also"></a>참고 항목

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Prompts](about_Prompts.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Signing](about_Signing.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

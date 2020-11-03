---
description: 함수에 대해 설명 하 `Prompt` 고 사용자 지정 함수를 만드는 방법을 보여 줍니다 `Prompt` .
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_prompts?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Prompts
ms.openlocfilehash: 3e1496c84fa528b4673a770b5b2777fc3d31dc34
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220665"
---
# <a name="about-prompts"></a>프롬프트 정보

## <a name="short-description"></a>간단한 설명
함수에 대해 설명 하 `Prompt` 고 사용자 지정 함수를 만드는 방법을 보여 줍니다 `Prompt` .

## <a name="long-description"></a>자세한 설명입니다.

PowerShell 명령 프롬프트는 PowerShell이 명령을 실행할 준비가 되었음을 나타냅니다.

```
PS C:\>
```

PowerShell 프롬프트는 기본 제공 함수에 의해 결정 됩니다 `Prompt` . 사용자 고유의 함수를 만들고 `Prompt` PowerShell 프로필에 저장 하 여 프롬프트를 사용자 지정할 수 있습니다.

## <a name="about-the-prompt-function"></a>Prompt 함수 정보

`Prompt`함수는 PowerShell 프롬프트의 모양을 결정 합니다.
PowerShell은 기본 제공 함수와 함께 제공 `Prompt` 되지만 사용자 고유의 함수를 정의 하 여 재정의할 수 있습니다 `Prompt` .

함수에는 `Prompt` 다음 구문이 있습니다.

```powershell
function Prompt { <function-body> }
```

`Prompt`함수는 개체를 반환 해야 합니다. 문자열 또는 문자열로 형식이 지정 된 개체를 반환 하는 것이 가장 좋습니다. 권장 되는 최대 길이는 80 자입니다.

예를 들어 다음 `Prompt` 함수는 "Hello, 세계" 문자열, 오른쪽 꺾쇠 괄호 ()를 차례로 반환 합니다 `>` .

```powershell
PS C:\> function prompt {"Hello, World > "}
Hello, World >
```

### <a name="getting-the-prompt-function"></a>프롬프트 함수 가져오기

함수를 가져오려면 `Prompt` cmdlet을 사용 `Get-Command` 하거나 `Get-Item` 함수 드라이브에서 cmdlet을 사용 합니다.

다음은 그 예입니다. 

```powershell
PS C:\> Get-Command Prompt

CommandType     Name      ModuleName
-----------     ----      ----------
Function        prompt
```

프롬프트의 값을 설정 하는 스크립트를 가져오려면 점 메서드를 사용 하 여 함수의 **ScriptBlock** 속성을 가져옵니다 `Prompt` .

다음은 그 예입니다. 

```powershell
(Get-Command Prompt).ScriptBlock
```

```Output
"PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
# .Link
# https://go.microsoft.com/fwlink/?LinkID=225750
# .ExternalHelp System.Management.Automation.dll-help.xml
```

모든 함수와 마찬가지로 함수는 `Prompt` 드라이브에 저장 됩니다 `Function:` .
현재 함수를 만드는 스크립트를 표시 하려면 `Prompt` 다음을 입력 합니다.

```powershell
(Get-Item function:prompt).ScriptBlock
```

### <a name="the-default-prompt"></a>기본 프롬프트

기본 프롬프트는 `Prompt` 함수가 오류를 생성 하거나 개체를 반환 하지 않는 경우에만 표시 됩니다.

기본 PowerShell 프롬프트는 다음과 같습니다.

```
PS>
```

예를 들어 다음 명령은 함수를 잘못 된로 설정 합니다 `Prompt` `$null` . 따라서 기본 프롬프트가 표시 됩니다.

```powershell
PS C:\> function prompt {$null}
PS>
```

PowerShell에는 기본 제공 프롬프트가 제공 되므로 일반적으로 기본 프롬프트가 표시 되지 않습니다.

### <a name="built-in-prompt"></a>기본 제공 프롬프트

PowerShell에는 기본 제공 함수가 포함 되어 있습니다 `Prompt` .

```powershell
function prompt {
    $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
      else { '' }) + 'PS ' + $(Get-Location) +
        $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

함수는 cmdlet을 사용 하 여 `Test-Path` 자동 변수가 채워졌는지 여부를 확인 합니다 `$PSDebugContext` . `$PSDebugContext`가 채워지면 디버깅 모드에 있으며 다음과 `[DBG]:` 같이 프롬프트에 추가 됩니다.

```Output
[DBG]: PS C:\ps-test>
```

`$PSDebugContext`가 채워지지 않은 경우 함수는 `PS` 프롬프트에를 추가 합니다.
그리고 함수는 cmdlet을 사용 하 여 `Get-Location` 현재 파일 시스템 디렉터리 위치를 가져옵니다. 그런 다음 오른쪽 꺾쇠 괄호 ()를 추가 `>` 합니다.

다음은 그 예입니다. 

```Output
PS C:\ps-test>
```

중첩 된 프롬프트에 있는 경우 함수는 두 개의 꺾쇠 괄호 ( `>>` )를 프롬프트에 추가 합니다. `$NestedPromptLevel`자동 변수 값이 1 보다 크면 중첩 된 프롬프트가 표시 됩니다.

예를 들어, 중첩 된 프롬프트에서 디버깅 하는 경우 프롬프트는 다음과 같이 표시 됩니다.

```Output
[DBG] PS C:\ps-test>>>
```

### <a name="changes-to-the-prompt"></a>프롬프트에 대 한 변경 내용

`Enter-PSSession`Cmdlet은 원격 컴퓨터의 이름을 현재 함수 앞에 앞에 추가할 수 `Prompt` 있습니다. Cmdlet을 사용 하 여 `Enter-PSSession` 원격 컴퓨터에서 세션을 시작 하는 경우 명령 프롬프트는 원격 컴퓨터의 이름을 포함 하도록 변경 됩니다. 다음은 그 예입니다. 

```Output
PS Hello, World> Enter-PSSession Server01
[Server01]: PS Hello, World>
```

다른 PowerShell 호스트 응용 프로그램 및 대체 셸에는 고유한 사용자 지정 명령 프롬프트가 있을 수 있습니다.

및 자동 변수에 대 한 자세한 내용은 `$PSDebugContext` `$NestedPromptLevel` [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.

### <a name="how-to-customize-the-prompt"></a>프롬프트를 사용자 지정 하는 방법

프롬프트를 사용자 지정 하려면 새 함수를 작성 `Prompt` 합니다. 함수는 보호 되지 않으므로 덮어쓸 수 있습니다.

함수를 작성 하려면 `Prompt` 다음을 입력 합니다.

```powershell
function prompt { }
```

그런 다음 중괄호 사이에 프롬프트를 생성 하는 문자열이 나 명령을 입력 합니다.

예를 들어 다음 프롬프트에는 컴퓨터 이름이 포함 됩니다.

```powershell
function prompt {"PS [$env:COMPUTERNAME]> "}
```

Server01 컴퓨터에서 프롬프트는 다음과 같이 표시 됩니다.

```Output
PS [Server01] >
```

다음 `Prompt` 함수는 현재 날짜 및 시간을 포함 합니다.

```powershell
function prompt {"$(Get-Date)> "}
```

프롬프트는 다음 프롬프트와 유사 합니다.

```Output
03/15/2012 17:49:47>
```

또한 기본 함수를 변경할 수 있습니다 `Prompt` .

예를 들어 다음 수정 된 `Prompt` 함수는 `[ADMIN]:` **관리자 권한으로 실행** 옵션을 사용 하 여 powershell을 열 때 기본 제공 powershell 프롬프트에를 추가 합니다.

```powershell
function prompt {
  $identity = [Security.Principal.WindowsIdentity]::GetCurrent()
  $principal = [Security.Principal.WindowsPrincipal] $identity
  $adminRole = [Security.Principal.WindowsBuiltInRole]::Administrator

  $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
    elseif($principal.IsInRole($adminRole)) { "[ADMIN]: " }
    else { '' }
  ) + 'PS ' + $(Get-Location) +
    $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

**관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 하는 경우 다음과 같은 프롬프트가 표시 됩니다.

```Output
[ADMIN]: PS C:\ps-test>
```

다음 `Prompt` 함수는 다음 명령의 기록 ID를 표시 합니다. 명령 기록을 보려면 cmdlet을 사용 합니다 `Get-History` .

```powershell
function prompt {
   # The at sign creates an array in case only one history item exists.
   $history = @(Get-History)
   if($history.Count -gt 0)
   {
      $lastItem = $history[$history.Count - 1]
      $lastId = $lastItem.Id
   }

   $nextCommand = $lastId + 1
   $currentDirectory = Get-Location
   "PS: $nextCommand $currentDirectory >"
}
```

다음 프롬프트는 및 cmdlet을 사용 하 여 `Write-Host` `Get-Random` 색을 임의로 변경 하는 프롬프트를 만듭니다. 는 `Write-Host` 현재 호스트 응용 프로그램에 기록 하지만 개체를 반환 하지 않기 때문에이 함수에는 문이 포함 됩니다 `Return` . 없는 경우 PowerShell은 기본 프롬프트를 사용 `PS>` 합니다.

```powershell
function prompt {
    $color = Get-Random -Min 1 -Max 16
    Write-Host ("PS " + $(Get-Location) +">") -NoNewLine `
     -ForegroundColor $Color
    return " "
}
```

### <a name="saving-the-prompt-function"></a>프롬프트 함수 저장

함수와 마찬가지로 `Prompt` 함수는 현재 세션에만 존재 합니다. `Prompt`이후 세션을 위해 함수를 저장 하려면 PowerShell 프로필에 추가 합니다. 프로필에 대한 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Get-History](xref:Microsoft.PowerShell.Core.Get-History)

[Get-Random](xref:Microsoft.PowerShell.Utility.Get-Random)

[Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host)

[about_Profiles](about_Profiles.md)

[about_Functions](about_Functions.md)

[about_Scopes](about_Scopes.md)

[about_Debuggers](about_Debuggers.md)

[about_Automatic_Variables](about_Automatic_Variables.md)

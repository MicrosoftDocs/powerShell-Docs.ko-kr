---
description: 명령 기록에서 명령을 가져오고 실행 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_history?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_History
ms.openlocfilehash: b9e8ab09553f8cd6452f4a891ecbaa1b914af895
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222265"
---
# <a name="about-history"></a>기록 정보

## <a name="short-description"></a>간단한 설명
명령 기록에서 명령을 가져오고 실행 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

명령 프롬프트에서 명령을 입력 하면 PowerShell에서 명령 기록에 명령을 저장 합니다. 기록의 명령을 작업 레코드로 사용할 수 있습니다. 명령 기록에서 명령을 회수 하 고 실행할 수 있습니다.

PowerShell에는 기본 제공 기록과 **Psreadline** 모듈에서 관리 하는 기록과 같은 두 가지 기록 공급자가 있습니다. 기록은 별도로 관리 되지만 **Psreadline** 이 로드 된 세션에서 두 기록을 모두 사용할 수 있습니다.

## <a name="using-the-psreadline-history"></a>PSReadLine 기록 사용

PSReadLine 기록은 모든 PowerShell 세션에서 사용 되는 명령을 추적 합니다.
기록은 호스트 당 중앙 파일에 기록 됩니다. 모든 세션에서 기록 파일을 사용할 수 있으며 모든 과거 기록을 포함 합니다. 세션이 종료 되 면 기록이 삭제 되지 않습니다. 또한 cmdlet으로 해당 기록을 관리할 수 없습니다 `*-History` . 자세한 내용은 [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.

## <a name="using-the-built-in-session-history"></a>기본 제공 세션 기록 사용

기본 제공 기록은 현재 세션에 사용 된 명령만 추적 합니다. 다른 세션에서 기록을 사용할 수 없으며 세션이 종료 될 때 삭제 됩니다.

### <a name="history-cmdlets"></a>기록 Cmdlet

PowerShell에는 명령 기록을 관리 하는 cmdlet 집합이 있습니다.

| cmdlet           | Alias  | 설명                                |
| ---------------- | ------ | ------------------------------------------ |
| `Get-History`    | `h`    | 명령 기록을 가져옵니다.                  |
| `Invoke-History` | `r`    | 명령 기록에서 명령을 실행 합니다.     |
| `Add-History`    |        | 명령 기록에 명령을 추가 합니다.     |
| `Clear-History`  | `clhy` | 명령 기록에서 명령을 삭제 합니다. |

### <a name="keyboard-shortcuts-for-managing-history"></a>기록 관리를 위한 바로 가기 키

PowerShell 콘솔에서 다음 바로 가기를 사용 하 여 명령 기록을 관리할 수 있습니다.

- <kbd>Uparrow</kbd> -이전 명령을 표시 합니다.
- <kbd>아래쪽 화살표</kbd> -다음 명령을 표시 합니다.
- <kbd>F7</kbd> -명령 기록을 표시 합니다.
- <kbd>ESC</kbd> -기록을 숨깁니다.
- <kbd>F8</kbd> -명령을 찾습니다. 하나 이상의 문자를 입력 한 다음 <kbd>f8</kbd>키를 누릅니다. 다음 인스턴스로 <kbd>F8</kbd> 키를 다시 누릅니다.
- <kbd>F9</kbd> -기록 ID로 명령을 찾습니다. 기록 ID를 입력 하 고 <kbd>f9</kbd>키를 누릅니다. <kbd>F7</kbd> 키를 눌러 ID를 찾습니다.
- <kbd>#</kbd>`<string>`</kbd>의 기록을 <kbd>탭</kbd> 하 여 검색 `*<string>*` 하 고 가장 최근의 일치 항목을 반환 합니다. <kbd>Tab</kbd> 키를 반복 해 서 누르면 기록에서 일치 하는 항목을 순환 합니다.

> [!NOTE]
> 이러한 키 바인딩은 콘솔 호스트 응용 프로그램에 의해 구현 됩니다. Visual Studio Code 또는 Windows Terminal와 같은 다른 응용 프로그램은 다른 키 바인딩을 가질 수 있습니다. 이 바인딩은 PSReadLine 모듈에 의해 재정의 될 수 있습니다. PSReadLine은 PowerShell 세션을 시작할 때 자동으로 로드 됩니다.
> PSReadLine이 로드 된 상태에서 <kbd>F7</kbd> 및 <kbd>F9</kbd> 는 함수에 바인딩되지 않습니다. PSReadLine은 동등한 기능을 제공 하지 않습니다. 자세한 내용은 [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.

### <a name="maximumhistorycount"></a>MaximumHistoryCount

`$MaximumHistoryCount`기본 설정 변수는 PowerShell이 명령 기록에 저장 하는 최대 명령 수를 결정 합니다. 기본값
4096.

예를 들어 다음 명령은 `$MaximumHistoryCount` 를 100 명령으로 줄입니다.

```powershell
$MaximumHistoryCount = 100
```

설정을 적용 하려면 PowerShell을 다시 시작 합니다.

모든 PowerShell 세션에 대 한 새 변수 값을 저장 하려면 PowerShell 프로필에 할당 문을 추가 합니다. 프로필에 대한 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조하세요.

기본 설정 변수에 대 한 자세한 내용은 `$MaximumHistoryCount` [about_Preference_Variables](about_Preference_Variables.md)를 참조 하세요.

### <a name="order-of-commands-in-the-history"></a>기록의 명령 순서

명령을 입력 하는 경우가 아니라 명령이 실행을 완료 하면 기록에 명령이 추가 됩니다. 명령을 완료 하는 데 시간이 오래 걸리고 명령이 중첩 된 프롬프트에서 실행 되는 경우 해당 명령은 기록에서 순서가 잘못 된 것 처럼 보일 수 있습니다. 중첩 된 프롬프트에서 실행 되는 명령은 프롬프트 수준을 종료 하는 경우에만 완료 됩니다.

## <a name="see-also"></a>참고 항목

- [about_Line_Editing](about_Line_Editing.md)
- [about_Preference_Variables](about_Preference_Variables.md)
- [about_Profiles](about_Profiles.md)
- [about_Variables](about_Variables.md)
- [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)

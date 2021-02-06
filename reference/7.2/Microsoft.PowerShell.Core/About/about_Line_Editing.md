---
description: PowerShell 명령 프롬프트에서 명령을 편집 하는 방법에 대해 설명 합니다.
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_line_editing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Line_Editing
ms.openlocfilehash: 2b9a320b92bc0a61efc9f9ed75078b17cdd9cbc9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601832"
---
# <a name="about-line-editing"></a>줄 편집 정보

## <a name="short-description"></a>간단한 설명

PowerShell 명령 프롬프트에서 명령을 편집 하는 방법에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

Powershell 콘솔에는 PowerShell 명령 프롬프트에서 명령을 편집 하는 데 도움이 되는 몇 가지 유용한 바로 가기 키가 있습니다.

### <a name="add-a-line"></a>선 추가

줄을 추가 하려면 <kbd>Shift</kbd> + <kbd>enter</kbd>를 누릅니다.

여러 줄을 추가할 수 있습니다. 각 추가 줄 `>>` 은 연속 프롬프트로 시작 합니다. <kbd>Enter</kbd> 키를 눌러 명령을 실행 합니다.

### <a name="move-left-and-right"></a>왼쪽 및 오른쪽으로 이동

커서를 한 문자 왼쪽으로 이동 하려면 <kbd>왼쪽 화살표</kbd>를 누릅니다.

커서를 한 단어 왼쪽으로 이동 하려면 <kbd>Ctrl</kbd> + <kbd>왼쪽 화살표</kbd>를 누릅니다.

커서를 한 문자 오른쪽으로 이동 하려면 <kbd>오른쪽 화살표</kbd>를 누릅니다.

커서를 한 단어 오른쪽으로 이동 하려면 <kbd>Ctrl</kbd> + <kbd>오른쪽 화살표</kbd>를 누릅니다.

### <a name="move-to-a-lines-beginning-or-end"></a>줄의 시작 또는 끝으로 이동

줄의 시작 부분으로 이동 하려면 <kbd>Home</kbd>키를 누릅니다.

줄의 끝으로 이동 하려면 <kbd>end</kbd>를 누릅니다.

줄이 추가 된 경우 <kbd>Home</kbd> 또는 <kbd>end</kbd> 를 두 번 눌러 줄의 시작 또는 끝으로 이동 합니다.

### <a name="delete-characters"></a>문자 삭제

커서 위치 뒤의 문자를 삭제 하려면 <kbd>백스페이스</kbd>키를 누릅니다.

커서의 위치에서 문자를 삭제 하려면 <kbd>delete</kbd>키를 누릅니다.

### <a name="delete-characters-from-a-line"></a>줄에서 문자 삭제

커서의 위치에서 줄의 끝까지 모든 문자를 삭제 하려면 <kbd>Ctrl</kbd> + <kbd>end</kbd>를 누릅니다.

커서 위치에서 줄의 시작 부분까지 모든 문자를 삭제 하려면 <kbd>ctrl</kbd> + <kbd>Home</kbd>을 누릅니다.

줄이 추가 되 면 현재 줄에서 문자를 삭제 하 고 추가 된 줄을 삭제 합니다.

### <a name="insert-and-overstrike-mode"></a>Insert 및 겹쳐쓰기 모드

덮어쓰기 모드로 변경 하려면 <kbd>Insert</kbd>키를 누릅니다. 삽입 모드로 돌아가려면 <kbd>insert</kbd> 를 다시 누릅니다.

### <a name="tab-completion"></a>탭 완성

Cmdlet 이름, 매개 변수 또는 경로를 완료 하려면 <kbd>tab</kbd> 키를 누릅니다. 값 목록을 스크롤하려면 <kbd>tab</kbd> 키를 다시 누릅니다.

## <a name="see-also"></a>참고 항목

[about_Command_Syntax](about_Command_Syntax.md)

[about_Path_Syntax](about_Path_Syntax.md)

[about_PSReadline](../../PSReadline/About/about_PSReadline.md)


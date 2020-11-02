---
ms.date: 01/02/2020
title: 스크립트 창 및 콘솔 창에서 탭 완성 기능을 사용하는 방법
description: 스크립트 창 및 콘솔 창에서 탭 완성 기능을 사용하는 방법
ms.openlocfilehash: d59a324ef5ca8eb882814c51bd9b7780b5916e81
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663678"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>스크립트 창 및 콘솔 창에서 탭 완성 기능을 사용하는 방법

탭 완성 기능은 스크립트 창이나 명령 창에 텍스트를 입력할 때 자동 도움말을 제공합니다. 이 기능을 활용하려면 다음 단계를 따르세요.

## <a name="to-automatically-complete-a-command-entry"></a>명령 입력을 자동으로 완성하려면

명령 창이나 스크립트 창에서 명령의 일부 문자를 입력한 다음 <kbd>Tab</kbd> 키를 눌러 원하는 완성 텍스트를 선택합니다. 처음에 입력한 텍스트로 시작하는 항목이 여러 개이면 원하는 항목이 나타날 때까지 계속 <kbd>Tab</kbd> 키를 누릅니다. 탭 완성 기능을 사용하면 cmdlet 이름, 매개 변수 이름, 변수 이름, 개체 속성 이름 또는 파일 경로를 쉽게 입력할 수 있습니다.

> [!NOTE]
> 스크립트 창에서는 `.ps1`, `.psd1` 또는 `.psm1` 파일을 편집하고 있는 경우에만 <kbd>Tab</kbd> 키를 눌러 명령을 자동으로 완성할 수 있습니다. 명령 창에서 입력하는 경우에는 탭 완성 기능이 항상 작동합니다.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>cmdlet 매개 변수 입력을 자동으로 완성하려면

명령 창이나 스크립트 창에서 cmdlet 뒤에 대시를 입력한 다음, <kbd>Tab</kbd> 키를 누릅니다.

예를 들어 `Get-Process -`를 입력한 다음, <kbd>Tab</kbd> 키를 눌러 여러 번 해당 cmdlet에 대한 각 매개 변수를 차례로 표시합니다.

## <a name="see-also"></a>참고 항목

- [Windows PowerShell ISE 소개](Introducing-the-Windows-PowerShell-ISE.md)
- [PowerShell 탭을 만드는 방법](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)

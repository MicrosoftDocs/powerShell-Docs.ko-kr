---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell ISE에서 콘솔 창을 사용하는 방법
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 5bbbdd3b1f0324ff1a4f2298459f58640c4dc9a6
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403127"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Windows PowerShell ISE에서 콘솔 창을 사용하는 방법

Windows PowerShell ISE(통합 스크립팅 환경)의 콘솔 창은 독립 실행형 Windows PowerShell ISE 콘솔 창과 똑같이 작동합니다.

콘솔 창에서 명령을 실행하려면 명령을 입력한 다음 Enter 키를 누릅니다. 연속해서 실행할 여러 명령을 입력하려면 명령 사이에 Shift+Enter를 입력합니다. 명령 입력에 대한 도움말은 [스크립트 창 및 콘솔 창에서 탭 완성 기능을 사용하는 방법](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)을 참조하세요.

명령을 중지하려면 도구 모음에서 **작업 중지**를 클릭하거나 Ctrl+Break를 누릅니다. 컨텍스트가 명확한 경우에는 Ctrl+C를 사용하여 명령을 중지할 수도 있습니다. 예를 들어 현재 창에서 일부 텍스트를 선택한 경우 Ctrl+C는 복사 작업에 매핑됩니다.

Windows PowerShell v3부터 출력 창이 콘솔 창과 결합되었습니다. 이렇게 하면 독립 실행형 Windows PowerShell 콘솔처럼 동작하는 이점이 있으며, 서로 별개일 때 필요한 절차의 차이점이 제거됩니다. 다음을 수행할 수 있습니다.

- 다른 창에 붙여넣기 위해 콘솔 창에서 텍스트를 선택하여 클립보드로 복사합니다. 텍스트를 선택하려면 출력 창에서 마우스를 클릭하고 누른 채 캡처할 텍스트 위로 마우스를 끕니다. **Shift** 키를 누른 채 커서 화살표 키를 사용하여 텍스트를 선택할 수도 있습니다. 그런 다음 Ctrl+C를 누르거나 도구 모음에서 **복사** 아이콘을 클릭합니다.

- 선택한 텍스트를 현재 커서 위치에 붙여넣습니다. 도구 모음에서 **붙여넣기** 아이콘을 클릭합니다.

- 콘솔 창에서 모든 텍스트를 지웁니다. 콘솔 창을 지우려면 도구 모음에서 **콘솔 창 지우기** 아이콘을 클릭하거나 **Clear-Host** 명령 또는 해당 별칭인 **cls**를 실행할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [Windows PowerShell ISE 소개](Introducing-the-Windows-PowerShell-ISE.md)
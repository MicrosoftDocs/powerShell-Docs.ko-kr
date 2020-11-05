---
ms.date: 08/14/2018
title: Windows PowerShell ISE 소개
description: PowerShell ISE는 단일 Windows 기반 그래픽 사용자 인터페이스에서 명령을 실행하고 스크립트를 작성, 테스트, 디버그할 수 있는 Windows PowerShell의 호스트 애플리케이션입니다.
ms.openlocfilehash: ab2b11e5d81933b166d404c0b24c96aa73253895
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663606"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell ISE(통합 스크립팅 환경)는 Windows PowerShell의 호스트 애플리케이션입니다. ISE에서는 단일 Windows 기반 그래픽 사용자 인터페이스에서 명령을 실행하고, 스크립트를 작성, 테스트 및 디버그할 수 있습니다. 이 ISE는 여러 줄 편집, 탭 완성, 구문 색 지정, 선택적 실행, 상황에 맞는 도움말 및 오른쪽에서 왼쪽으로 쓰는 언어 지원을 제공합니다. 메뉴 항목 및 바로 가기 키가 Windows PowerShell 콘솔에서 수행하는 것과 동일한 많은 작업에 매핑됩니다. 예를 들어 ISE에서 스크립트를 디버그할 때 편집 창에서 코드 줄을 마우스 오른쪽 단추로 클릭하여 중단점을 설정할 수 있습니다.

## <a name="support"></a>지원

ISE는 Windows PowerShell V2에 처음 도입되었고 PowerShell V3에서 다시 디자인되었습니다. ISE는 Windows PowerShell V5.1 이하의 모든 지원되는 Windows PowerShell 버전에서 지원됩니다.

> [!NOTE]
> PowerShell ISE는 더 이상 활성 기능 개발에 필요하지 않습니다. Windows의 배송 구성 요소로서 보안 및 우선 순위가 높은 서비스 수정 사항을 위해 공식적으로 계속 지원됩니다.
> 현재 Windows에서 ISE를 제거할 계획은 없습니다.
>
> PowerShell v6 이상에서는 ISE가 지원되지 않습니다. ISE를 대체하려는 사용자는 [PowerShell 확장](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)을 통해 [Visual Studio Code](https://code.visualstudio.com/)를 사용해야 합니다.

## <a name="key-features"></a>주요 기능

Windows PowerShell ISE의 주요 기능은 다음과 같습니다.

- 여러 줄 편집: 명령 창에서 현재 줄 아래에 빈 줄을 삽입하려면 <kbd>SHIFT</kbd>+<kbd>ENTER</kbd> 키를 누릅니다.
- 선택적 실행: 스크립트의 일부를 실행하려면 실행할 텍스트를 선택한 다음, **스크립트 실행** 단추를 클릭합니다. 또는 <kbd>F5</kbd> 키를 누릅니다.
- 상황에 맞는 도움말: `Invoke-Item`을 입력하고 <kbd>F1</kbd> 키를 누릅니다. 도움말 파일이 `Invoke-Item` cmdlet에 대한 문서로 열립니다.

Windows PowerShell ISE를 사용하여 해당 모양의 일부 측면을 사용자 지정할 수 있습니다. 또한 자체 Windows PowerShell 프로필 스크립트도 있습니다.

## <a name="to-start-the-windows-powershell-ise"></a>Windows PowerShell ISE를 시작하려면

**시작** 을 클릭하고 **Windows PowerShell** 을 선택한 후 고 **Windows PowerShell ISE** 를 클릭합니다.
또는 임의 명령 셸이나 실행 상자에 `powershell_ise.exe`를 입력할 수 있습니다.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Windows PowerShell ISE에서 도움말을 가져오려면

**도움말** 메뉴에서 **Windows PowerShell 도움말** 을 클릭합니다. 또는 <kbd>F1</kbd> 키를 누릅니다. 열린 파일에는 `Get-Help` cmdlet에서 사용 가능한 모든 도움말을 비롯하여 Windows PowerShell ISE 및 Windows PowerShell이 설명되어 있습니다.

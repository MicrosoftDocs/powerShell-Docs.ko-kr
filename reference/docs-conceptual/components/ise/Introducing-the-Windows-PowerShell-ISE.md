---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 소개
ms.openlocfilehash: 09a28b295855fd2a3c62bba8a681399dae3454f8
ms.sourcegitcommit: 3402a478cf118c11a5642038eb117bc76553e3ab
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411585"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell ISE(통합 스크립팅 환경)는 Windows PowerShell의 호스트 애플리케이션입니다. ISE에서 명령 및 작성, 테스트, 실행 하 고 단일 Windows 기반 그래픽 사용자 인터페이스에서 스크립트를 디버그할 수 있습니다. ISE는 오른쪽에서 왼쪽 언어에 대 한 여러 줄 편집, 탭 완성, 구문 색 지정, 선택적 실행, 상황에 맞는 도움말 및 지원을 제공합니다. 메뉴 항목 및 바로 가기 키가 Windows PowerShell 콘솔에서 수행하는 것과 동일한 많은 작업에 매핑됩니다. 예를 들어, ISE에서 스크립트를 디버그할 때 중단점을 설정 하려면 편집 창의 코드 줄에 단추로 합니다.

## <a name="support"></a>Support(지원)

ISE는 Windows PowerShell V2를 사용 하 여 처음으로 도입 및 PowerShell V3을 사용 하 여 다시 설계 되었습니다. ISE는 Windows PowerShell을 설치 하 고 포함 하 여 Windows PowerShell v5.1이 지원 되는 모든 버전에서 지원 됩니다. 그러나 ISE, maintennce 모드 이므로 추가할 수 있는 새 기능이 없습니다.
또한 PowerShell v6 이상 ISE에 대 한 지원은 없습니다. 사용자를 PowerShell scrips 등을 관리 하는 그래픽 도구를 원하는 것이 좋습니다 [Visual Studio Code](https://code.visualstudio.com/)합니다.

## <a name="key-features"></a>주요 기능

Windows PowerShell ISE에서 주요 기능은 다음과 같습니다.

- 여러 줄 편집: 명령 창에서 현재 줄 아래에 빈 줄을 삽입하려면 Shift+Enter를 누릅니다.
- 선택적 실행: 스크립트의 일부를 실행하려면 실행할 텍스트를 선택한 다음, **스크립트 실행** 단추를 클릭합니다. 또는 F5 키를 누릅니다.
- 상황에 맞는 도움말: **Invoke-Item**을 입력한 다음, F1 키를 누릅니다. 도움말 파일이 **Invoke-Item** cmdlet에 대한 문서로 열립니다.

Windows PowerShell ISE를 사용하여 해당 모양의 일부 측면을 사용자 지정할 수 있습니다. 또한 자체 Windows PowerShell 프로필 스크립트도 있습니다.

## <a name="to-start-the-windows-powershell-ise"></a>Windows PowerShell ISE를 시작하려면

**시작**을 클릭하고 **Windows PowerShell**을 선택한 후 고 **Windows PowerShell ISE**를 클릭합니다.
또는 임의 명령 셸이나 실행 상자에 `powershell_ise.exe`를 입력할 수 있습니다.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Windows PowerShell ISE에서 도움말을 가져오려면

**도움말** 메뉴에서 **Windows PowerShell 도움말**을 클릭합니다. 또는 F1 키를 누릅니다. 열린 파일에는 Get-Help cmdlet에서 사용 가능한 모든 도움말을 비롯하여 Windows PowerShell ISE 및 Windows PowerShell이 설명되어 있습니다.

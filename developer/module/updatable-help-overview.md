---
title: 업데이트 가능한 도움말 개요 | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: 4e962890fa1d5c282a02a89f0ae2e263844c635e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856969"
---
# <a name="updatable-help-overview"></a>업데이트 가능한 도움말 개요

이 문서에서는 디자인 및 Windows PowerShell 업데이트할 수 있는 도움말 기능 작업에 대 한 기본적인 소개를 제공 합니다. 모듈 작성자 및 다른 사용자에 게 Windows PowerShell 도움말 항목을 제공 하는 것에 대 한 설계 되었습니다.

## <a name="introduction"></a>소개

Windows PowerShell 도움말 항목은 Windows PowerShell 환경의 필수적인 부분입니다. Windows PowerShell 모듈과 마찬가지로 도움말 항목 지속적으로 업데이트 되 고 작성자 및 Windows PowerShell 사용자 커뮤니티의 기여를 향상 합니다.

합니다 *업데이트할 수 있는 도움말* Windows PowerShell 3.0에 도입 된 기능을 통해 사용자 도움말 항목의 최신 버전도 기본 제공 Windows PowerShell 명령에 대 한 명령 프롬프트에서 새 모듈을 다운로드 하지 않고 또는 Windows 업데이트를 실행 합니다. 업데이트 가능한 도움말을 손쉽게 업데이트 인터넷에서 도움말 항목의 최신 버전을 다운로드 하 고 사용자의 로컬 컴퓨터에 올바른 하위 디렉터리에 설치 하는 cmdlet을 제공 하 여 합니다. 방화벽 뒤도 사용자는 내부 파일 공유에서 업데이트 된 도움말을 보려면 새로운 cmdlet을 사용할 수 있습니다.

업데이트 가능한 도움말은 Windows® 8 및 Windows Server® 2012에서 모든 Windows PowerShell 모듈에서 완전히 지원 하 고 해당 기능은 모든 Windows PowerShell 모듈 작성자가 사용할 수 있습니다. 업데이트 가능한 도움말에는 XML 기반 도움말 파일만 지원합니다. 주석 기반 도움말을 지원 하지는 않습니다.

업데이트 가능한 도움말에는 다음과 같은 기능이 있습니다.

- [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 사용자 최신 도움말 지 여부를 확인 하는 cmdlet 모듈에 대 한 파일 하 고, 그렇지 않은 경우 인터넷에서 최신 도움말 파일을 다운로드, 압축을 푼에 올바른 모듈 하위 디렉터리에 설치 된 사용자의 컴퓨터입니다. 사용자가 사용할 수는 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet을 새로 설치 된 도움말 항목을 즉시 확인 합니다. Windows PowerShell을 다시 시작할 필요가 없습니다.

- 합니다 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet은 최신 도움말을 다운로드 하는 인터넷에서 파일 및 파일 시스템 디렉터리에 저장 합니다. 사용자가 사용할 수는 `Update-Help` cmdlet을 통해 파일 시스템 디렉터리에서 도움말 파일을 가져올 및 압축 풀기를 사용자의 컴퓨터에서 모듈 하위 디렉터리에 설치 합니다. `Save-Help` cmdlet은 제한 된 사용자 또는 인터넷 액세스가 불가능 한 인터넷 액세스를 제한 하는 것을 선호 하는 엔터프라이즈를 위한 설계 되었습니다.

- **모듈에 대 한 도움말**합니다. 모듈에 대 한 도움말 파일 관리 되며 사용자가 사용 하 여 모듈에 대 한 도움말 파일을 모두 가져올 수 있도록 하나의 단위로 제공 됩니다. 업데이트할 수 있는 도움말은 Windows PowerShell 스냅인에 대 한 없습니다 모듈에 대해서만 지원 됩니다.

- **버전 지원**합니다. 표준 위치 4 (N1을 사용 하 여 업데이트할 수 있는 도움말. N2입니다. N3 합니다. N4) 버전 번호입니다. 사용자의 컴퓨터에 파일을 도움말의 버전 번호를 업데이트할 수 있는 도움말 도움말 파일을 다운로드 (또는 `Save-Help` 디렉터리) 인터넷 위치에 있는 도움말 파일의 버전 번호 보다 낮습니다.

- **다중 언어 지원**합니다. 업데이트 가능한 도움말 여러 UI 문화권의 모듈 도움말 파일을 지원합니다. 업데이트 가능한 도움말 파일 이름에 "EN-US" 및 "JA-JP"와 같은 표준 언어 코드를 포함 하며 `Update-Help` 및 `Save-Help` cmdlet 도움말 파일을 모듈 디렉터리의 언어별 하위 디렉터리에 배치 합니다.

- **자동 생성 된 도움말**합니다. 합니다 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet은 도움말 파일이 없는 명령에 대 한 기본적인 도움말을 표시 합니다. 자동 생성 된 도움말 명령 구문 및 별칭 및 온라인 도움말 및 업데이트할 수 있는 도움말 사용을 위한 지침을 포함 합니다.

- **온라인 도움말 향상**합니다. 온라인 도움말에 쉽게 액세스할 수는 도움말 파일이 더 이상 필요합니다. **Online** 의 매개 변수를 `Get-Help` cmdlet은 이제 값에서 온라인 도움말 항목의 URL을 가져옵니다 합니다 **HelpUri** 도움말 파일의 온라인 도움말 URL을 찾을 수 없으면 모든 명령의 속성. 채울 수 있습니다는 **HelpUri** 추가 하 여 속성을 **HelpUri** cmdlet, 함수 및 CIM 명령, 또는 사용 하 여 코드에 특성을 **입니다. 링크** 워크플로 및 스크립트에 대 한 설명 기반 도움말 지시문입니다.

  이 도움말 파일을 업데이트할 수 있는 하려면 Windows 8 및 Windows Server vNext에서 Windows PowerShell 모듈 도움말 파일이 함께 제공 되지 않습니다. 사용자는 도움말 파일을 설치 및 업데이트를 업데이트할 수 있는 도움말을 사용할 수 있습니다. 다른 모듈 작성자는 모듈의 도움말 파일을 포함 하거나 생략할 수 있습니다. 업데이트할 수 있는 도움말에 대 한 지원은 선택 사항 이지만 권장 합니다.

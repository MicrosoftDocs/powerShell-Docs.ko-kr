---
ms.date: 03/22/2012
ms.topic: reference
title: 업데이트 가능한 도움말 개요
description: 업데이트 가능한 도움말 개요
ms.openlocfilehash: b8008b7c28d94ebaac135934606042e6a6053591
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649566"
---
# <a name="updatable-help-overview"></a>업데이트 가능한 도움말 개요

이 문서에서는 PowerShell 업데이트할 수 있는 도움말 기능의 디자인 및 작업에 대 한 기본적인 소개를 제공 합니다. 이 도구는 모듈 작성자와 Windows PowerShell 도움말 항목을 사용자에 게 제공 하는 다른 사용자를 위해 설계 되었습니다.

## <a name="introduction"></a>소개

Powershell 도움말 항목은 PowerShell 환경에서 필수적인 부분입니다. PowerShell 모듈과 마찬가지로 도움말 항목은 작성자와 PowerShell 사용자 커뮤니티의 기여에 의해 지속적으로 업데이트 되 고 향상 됩니다.

Windows PowerShell 3.0에 도입 된 업데이트할 수 있는 *도움말* 기능을 사용 하면 새 모듈을 다운로드 하거나 Windows 업데이트를 실행 하지 않고도 기본 제공 PowerShell 명령에 대해서도 명령 프롬프트에서 최신 버전의 도움말 항목을 사용할 수 있습니다. 업데이트할 수 있는 도움말은 인터넷에서 최신 버전의 도움말 항목을 다운로드 하 여 사용자의 로컬 컴퓨터의 올바른 하위 디렉터리에 설치 하는 cmdlet을 제공 하 여 업데이트를 간단 하 게 만듭니다. 방화벽 뒤에 있는 사용자 라도 새 cmdlet을 사용 하 여 내부 파일 공유에서 업데이트 된 도움말을 가져올 수 있습니다.

업데이트할 수 있는 도움말은 Windows 8 및 Windows Server 2012의 모든 Windows PowerShell 모듈에서 완전히 지원 되며, 모든 Windows PowerShell 모듈 작성자는 해당 기능을 사용할 수 있습니다. 업데이트할 수 있는 도움말은 XML 기반 도움말 파일만 지원 합니다. 주석 기반 도움말은 지원 하지 않습니다.

업데이트할 수 있는 도움말에는 다음 기능이 포함 됩니다.

- [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet-사용자에 게 모듈에 대 한 최신 도움말 파일이 있는지 여부를 확인 하 고, 그렇지 않으면 인터넷에서 최신 도움말 파일을 다운로드 하 고 압축을 풀고 사용자 컴퓨터의 올바른 모듈 하위 디렉터리에 설치 합니다. 사용자는 [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet을 사용 하 여 새로 설치 된 도움말 항목을 즉시 볼 수 있습니다. PowerShell을 다시 시작할 필요는 없습니다.

- [Save help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet은 인터넷에서 최신 도움말 파일을 다운로드 하 여 파일 시스템 디렉터리에 저장 합니다. 사용자는 cmdlet을 사용 `Update-Help` 하 여 파일 시스템 디렉터리에서 도움말 파일을 가져오고 해당 파일의 압축을 풀고 사용자 컴퓨터의 모듈 하위 디렉터리에 설치할 수 있습니다. 이 cmdlet은 인터넷 액세스를 제한 하거나 인터넷 액세스 `Save-Help` 를 선호 하는 기업에 적합 한 사용자를 위해 설계 되었습니다.

- **모듈에 대 한 도움말** 입니다. 모듈에 대 한 도움말 파일은 하나의 단위로 관리 및 제공 되므로 사용자가 사용 하는 모듈에 대 한 도움말 파일을 모두 가져올 수 있습니다. 업데이트할 수 있는 도움말은 Windows PowerShell 스냅인이 아닌 모듈에만 지원 됩니다.

- **버전 지원**. 업데이트할 수 있는 도움말은 표준 4 자리 (N1. N2. N3. N4) 버전 번호입니다.
  업데이트할 수 있는 도움말은 사용자 컴퓨터 (또는 디렉터리)에 있는 도움말 파일의 버전 번호가 `Save-Help` 인터넷 위치에 있는 도움말 파일의 버전 번호 보다 낮을 때 도움말 파일을 다운로드 합니다.

- **다국어 지원**. 업데이트할 수 있는 도움말은 여러 UI 문화권의 모듈 도움말 파일을 지원 합니다.
  업데이트할 수 있는 도움말 파일 이름에는 "en-us" 및 "ja-jp"와 같은 표준 언어 코드가 포함 되며, `Update-Help` 및 `Save-Help` cmdlet은 도움말 파일을 모듈 디렉터리의 언어별 하위 디렉터리에 저장 합니다.

- **자동 생성 된 도움말** 입니다. [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet은 도움말 파일이 없는 명령에 대 한 기본 도움말을 표시 합니다. 자동 생성 된 도움말에는 명령 구문 및 별칭과 온라인 도움말 및 업데이트할 수 있는 도움말을 사용 하는 방법에 대 한 지침이 포함 되어 있습니다.

- **향상 된 온라인 도움말**. 온라인 도움말에 쉽게 액세스 하려면 도움말 파일이 더 이상 필요 하지 않습니다. 이제 cmdlet의 **online** 매개 변수는 `Get-Help` 도움말 파일에서 온라인 도움말 url을 찾을 수 없는 경우 모든 명령의 **HelpUri** 속성 값에서 온라인 도움말 항목의 url을 가져옵니다. Cmdlet, 함수 및 CIM 명령 코드에 **HelpUri** 특성을 추가 하거나를 사용 하 여 **HelpUri** 속성을 채울 수 있습니다 **.** 워크플로 및 스크립트에서 주석 기반 도움말 지시문을 연결 합니다.

  도움말 파일을 업데이트할 수 있도록 하기 위해 Windows 8 및 Windows Server vNext의 Windows PowerShell 모듈에는 도움말 파일이 함께 제공 되지 않습니다. 사용자는 업데이트할 수 있는 도움말을 사용 하 여 도움말 파일을 설치 하 고 업데이트할 수 있습니다. 다른 모듈의 작성자는 모듈에 도움말 파일을 포함 하거나 생략할 수 있습니다. 업데이트할 수 있는 도움말에 대 한 지원은 선택 사항 이지만 권장 됩니다.

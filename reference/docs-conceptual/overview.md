---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: PowerShell 스크립팅
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058491"
---
# <a name="powershell"></a>PowerShell

PowerShell은 .NET에서 구축된 작업 기반 명령줄 셸 및 스크립팅 언어입니다.
PowerShell을 통해 시스템 관리자 및 고급 사용자는 운영 체제(Linux, macOS 및 Windows) 및 프로세스를 관리하는 작업을 신속하게 자동화할 수 있습니다.

PowerShell 명령을 사용하면 명령줄에서 컴퓨터를 관리할 수 있습니다. PowerShell 공급자는 파일 시스템에 액세스하는 것처럼 쉽게, 레지스트리 및 인증서 저장소와 같은 데이터 저장소에 액세스하도록 지원합니다. PowerShell은 충분한 식을 포함하는 파서와 완전히 개발된 스크립트 언어를 포함합니다.

## <a name="powershell-is-open-source"></a>PowerShell이 오픈 소스로 제공됨

이제 GitHub에서 PowerShell 기본 소스 코드를 사용할 수 있으며 커뮤니티 참여가 개방됩니다.
[GitHub의 PowerShell 소스](https://github.com/powershell/powershell)를 참조하세요.

[Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell)(PowerShell 다운로드)에서 필요한 비트로 시작할 수 있습니다.
또는 [시작](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)에서 둘러보기로 시작합니다.

## <a name="powershell-design-goals"></a>PowerShell 디자인 목표

PowerShell은 장기적인 문제를 제거하고 새로운 기능을 추가하여 명령줄 및 스크립팅 환경을 개선하도록 설계되었습니다.

### <a name="discoverability"></a>검색 기능

PowerShell을 사용하면 해당 기능을 쉽게 검색할 수 있습니다. 예를 들어 Windows 서비스를 보고 변경하는 cmdlet 목록을 찾으려면 다음과 같이 입력합니다.

```powershell
Get-Command *-Service
```

작업을 수행하는 cmdlet을 검색한 후 `Get-Help` cmdlet을 사용하여 cmdlet에 대해 자세히 알아볼 수 있습니다. 예를 들어 `Get-Service` cmdlet에 대한 도움말을 표시하려면 다음과 같이 입력합니다.

```powershell
Get-Help Get-Service
```

대부분의 cmdlet은 조작한 다음 텍스트로 렌더링하여 표시할 수 있는 개체를 반환합니다. 해당 cmdlet의 출력을 완벽하게 이해하려면 출력을 `Get-Member` cmdlet에 파이프합니다. 예를 들어 다음 명령은 `Get-Service` cmdlet에 의한 개체 출력의 멤버에 대한 정보를 표시합니다.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>일관성

시스템 관리는 복잡한 작업일 수 있습니다. 도구에는 내재된 복잡성을 제어하는 데 도움이 되는 일관된 인터페이스가 있습니다. 그렇지만 일관성이 입증된 명령줄 도구 및 스크립트 가능한 COM(구성 요소 개체 모델) 개체는 없습니다.

PowerShell의 일관성은 기본 자산 중 하나입니다. 예를 들어 `Sort-Object` cmdlet을 사용하는 방법을 배운 경우 해당 지식을 사용하여 모든 cmdlet의 출력을 정렬할 수 있습니다. 각 cmdlet의 다른 정렬 루틴을 배울 필요가 없습니다.

또한 cmdlet 개발자는 해당 cmdlet의 정렬 기능을 디자인할 필요가 없습니다. PowerShell은 일관성을 강제하는 기본 기능이 있는 프레임워크를 제공합니다. 이 프레임워크를 사용하면 개발자가 선택해야 할 사항이 없습니다. 하지만 cmdlet의 개발은 훨씬 더 간단합니다.

### <a name="interactive-and-scripting-environments"></a>대화형 및 스크립팅 환경

Windows 명령 프롬프트는 명령줄 도구 및 기본 스크립팅에 액세스할 수 있는 대화형 셸을 제공합니다. WSH(Windows Script Host)에는 스크립트 가능한 명령줄 도구와 COM 자동화 개체가 있지만 대화형 셸은 없습니다.

PowerShell은 대화형 셸과 스크립팅 환경을 결합합니다. PowerShell은 명령줄 도구, COM 개체 및 .NET 클래스 라이브러리에 액세스할 수 있습니다. 이러한 기능 조합으로 대화형 사용자, 스크립트 작성자 및 시스템 관리자의 역량이 확장될 수 있습니다.

### <a name="object-orientation"></a>개체 방향

PowerShell은 텍스트가 아닌 개체를 기준으로 합니다. 명령의 출력은 개체입니다. 파이프라인을 통해 출력 개체를 다른 명령에 입력으로 보낼 수 있습니다.

이 파이프라인은 다른 셸에 익숙한 사용자에게 친숙한 인터페이스를 제공합니다. PowerShell은 텍스트가 아니라 개체를 전송하여 이 개념을 확장합니다.

### <a name="easy-transition-to-scripting"></a>스크립팅으로 쉽게 전환

PowerShell의 명령 검색 기능을 사용하면 대화형 명령 입력에서 스크립트 생성 및 실행으로 쉽게 전환할 수 있습니다. PowerShell 기록 및 내역을 통해 명령을 스크립트로 사용할 수 있게 쉽게 파일로 복사할 수 있습니다.

---
title: 문제 관리 방법
description: 이 문서에서는 PowerShell-Docs 팀이 끌어오기 요청을 관리하는 방법을 설명합니다.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: cd7aba83d42a6a2eba1ce73910fdd34096342c21
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060278"
---
# <a name="how-we-manage-issues"></a>문제 관리 방법

이 문서에서는 Microsoft가 PowerShell-Docs 리포지토리에서 문제를 관리하는 방법을 설명합니다. 이 문서는 PowerShell-Docs 팀 구성원을 위한 작업 보조 도구이며, 일반 기여자에게 프로세스의 투명도를 공개하기 위해 게시되었습니다.

## <a name="sources-of-issues"></a>문제 출처

- 커뮤니티 기여자
- 내부 기여자
- 소셜 미디어 채널에 게시된 댓글 전사
- Docs 피드백 양식을 통한 피드백

## <a name="response-time-targets"></a>목표 응답 시간

- 심사 - 영업일 기준 5일
- 수정 또는 변경 - 특정 목표 없음 - 최선의 노력 기울임

### <a name="labeling--milestones"></a>레이블 및 중요 시점

#### <a name="label-types"></a>레이블 형식

|접두사  | Description                                                         |
|------- | --------------------------------------------------------------------|
|영역    | PowerShell 또는 문서에서 문제가 설명하는 부분을 나타내는 데 사용됩니다.<br>기능 소유자가 해당 기능에 대한 문제를 찾는 데 유용합니다.|
|Pri     | 문제의 우선 순위를 나타내는 데 사용됩니다. 값 범위는 0~4입니다.        |
|문제   | 문제에 대한 피드백의 유형을 분류하는 데 사용됩니다.                     |
|검토  | 팀에서 추가로 검토해야 하는 문제에 사용됩니다.              |
|상태  | 작업 항목의 상태를 나타내는 데 사용됩니다.                        |
|대기 | 무언가를 기다리는 중임을 나타내는 데 사용됩니다.                   |

#### <a name="milestones"></a>중요 시점

문제 및 PR은 적절한 마일스톤으로 태그를 지정해야 합니다. 문제가 특정 버전을 대상으로 하지 않는 경우 마일스톤이 사용되지 않습니다. PowerShell 코드베이스에 아직 병합되지 않은 변경 내용에 대한 Docs PR 문제는 **향후** 마일스톤에 할당되어야 합니다. 코드 변경 내용이 병합된 이후에는 마일스톤을 적절한 버전으로 변경합니다.

|    Milestone     |                    Description                     |
| ---------------- | -------------------------------------------------- |
| 6.x              | PowerShell 6.0~6.2.x 관련 작업 항목 |
| 7.0.0            | PowerShell 7.0 관련 작업 항목               |
| 7.1.0            | PowerShell 7.1 관련 작업 항목               |
| 미래           | PowerShell 향후 버전 작업 항목          |
| PSReadline-vNext | PSReadline 향후 버전 작업 항목          |

## <a name="triage-process"></a>프로세스 심사

PowerShell Docs 팀은 매주 한 번 회의를 열고 마지막 회의 이후 추가된 문제에 대해 논의합니다. 문제는 레이블이나 소유자가 할당되면 심사된 것으로 간주됩니다. PowerShell Docs 팀 구성원들은 매일 문제를 검토하고 새로운 문제가 도착하는 대로 심사하고 있습니다. 그런 다음 주간 심사 회의에서 필요에 따라 새로운 문제를 더 자세히 논의합니다.

### <a name="misplaced-product-feedback"></a>잘못 배치된 제품 피드백

- 고객에게 해당 내용이 제품 피드백이라는 설명을 입력하고 적절한 피드백 채널에 대한 링크를 제공합니다.
- 선택 사항: 문제를 적절한 제품 피드백 위치로 복사하고 복사된 항목에 대한 링크를 추가한 다음 문제를 종결합니다. 문제를 UserVoice로 복사하지 마세요.

  | DocSet    | 제품 피드백 URL                                         |
  | --------- | ------------------------------------------------------------ |
  | developer | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | dsc       | https://windowsserver.uservoice.com/forums/301869-powershell |
  | gallery   | https://github.com/powershell/powershellgallery/issues/new   |
  | jea       | https://github.com/powershell/jea/issues/new                 |
  | reference | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | wmf       | https://windowsserver.uservoice.com/forums/301869-powershell |

### <a name="support-requests"></a>지원 요청

- 지원 질문이 단순한 경우 정중히 답변하고 문제를 종결합니다.
- 질문이 더 복잡하거나 제출자가 추가 질문으로 회신하는 경우 포럼 및 지원 채널로 리디렉션합니다. 포럼으로 리디렉션하기 위한 텍스트 제안:

    > 이 포럼은 이러한 종류의 질문에 적합하지 않습니다. 커뮤니티 지원 포럼에 질문을 게시해 보세요. 커뮤니티 포럼 목록은 다음을 참조하세요. https://docs.microsoft.com/powershell/scripting/community/community-support

### <a name="code-of-conduct-violations"></a>사용 규정 위반

- 필요한 경우 문제를 편집하여 악의적인 콘텐츠를 제거합니다.
- 해당 문제가 스팸이라는 설명을 입력하고, 문제를 종결한 다음 잠가 의견 추가를 방지합니다.
- 이러한 사례가 발생할 때마다 주간 심사에서 논의하여 추가 조치(GitHub 또는 Microsoft 법률 부서에 보고)가 필요한지 결정해야 합니다.

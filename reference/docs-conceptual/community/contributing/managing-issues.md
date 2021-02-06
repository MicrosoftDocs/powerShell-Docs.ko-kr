---
title: 문제 관리 방법
description: 이 문서에서는 PowerShell-Docs 팀이 문제를 관리하는 방법을 설명합니다.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 72267137a2657f51e5f616113adf92d80647acad
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "99599323"
---
# <a name="how-we-manage-issues"></a>문제 관리 방법

이 문서에서는 Microsoft가 PowerShell-Docs 리포지토리에서 문제를 관리하는 방법을 설명합니다. 이 문서는 PowerShell-Docs 팀 구성원을 위한 작업 보조 도구이며, 공용 참가자에 대 한 프로세스 투명도를 제공 하기 위해 여기에 게시 됩니다.

## <a name="sources-of-issues"></a>문제 출처

- 커뮤니티 기여자
- 내부 기여자
- 소셜 미디어 채널에 게시된 댓글 전사
- Docs 피드백 양식을 통한 피드백

## <a name="response-time-targets"></a>목표 응답 시간

80%의 새 문제는 영업일 3 일 이내에 종결 됩니다.

- 심사-영업일 1 일
- 해결 또는 변경-영업일 10 일

### <a name="labeling--milestones"></a>레이블 및 중요 시점

#### <a name="label-types"></a>레이블 형식

|   Type   | Description                                                         |
| -------- | ------------------------------------------------------------------- |
| 영역     | PowerShell 또는 문서에서 문제가 설명하는 부분을 나타내는 데 사용됩니다.<br>기능 소유자가 해당 기능에 대한 문제를 찾는 데 유용합니다. |
| 문제    | 문제의 유형을 나타냅니다.                                         |
| 우선 순위 | 문제의 우선 순위를 나타냅니다. 값 범위 0 (높음)-4 (낮음)  |
| 상태   | 작업 항목의 상태 또는 종결 된 이유를 나타냅니다.          |
| 태그      | 추가 분류에 사용 되는 레이블                        |
| 대기 중  | 다른 이벤트에서 대기 중임을 나타냅니다.         |

#### <a name="milestones"></a>중요 시점

문제 및 PR은 적절한 마일스톤으로 태그를 지정해야 합니다. 문제가 특정 버전에 적용 되지 않는 경우에는 마일스 톤이 사용 되지 않습니다. PowerShell 코드 베이스에 아직 병합 되지 않은 변경 내용에 대 한 Pr 및 관련 문제는 **이후** 마일스 톤에 할당 되어야 합니다. 코드 변경 내용이 병합된 이후에는 마일스톤을 적절한 버전으로 변경합니다.

|    Milestone     |                    Description                     |
| ---------------- | -------------------------------------------------- |
| 7.0.0            | PowerShell 7.0 관련 작업 항목               |
| 7.1.0            | PowerShell 7.1 관련 작업 항목               |
| 7.2.0            | PowerShell 7.2 관련 작업 항목               |
| 미래           | PowerShell 향후 버전 작업 항목          |

## <a name="triage-process"></a>프로세스 심사

PowerShell docs 팀 구성원은 문제를 매일 검토 하 고 새로운 문제가 도착 하면이를 심사 합니다. 팀에서 심사가 필요한 문제를 논의 하거나 해결 되지 않은 상태를 유지 합니다.

### <a name="misplaced-product-feedback"></a>잘못 배치된 제품 피드백

- 고객을 올바른 피드백 채널로 리디렉션하는 메모를 입력 합니다.
- 선택 사항: 문제를 적절한 제품 피드백 위치로 복사하고 복사된 항목에 대한 링크를 추가한 다음 문제를 종결합니다. 문제를 UserVoice로 복사하지 마세요.

  PowerShell 문제에 대 한 기본 위치는 [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose) 입니다.

  다음 주제 영역에는 문제에 대 한 여러 위치가 있습니다.

  | 제목 |                                                     제품 피드백 URL                                                     |
  | -------- | ---------------------------------------------------------------------------------------------------------------------------- |
  | dsc      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |
  | gallery  | [https://github.com/powershell/powershellgallery/issues/new](https://github.com/powershell/powershellgallery/issues/new)     |
  | jea      | [https://github.com/powershell/jea/issues/new](https://github.com/powershell/jea/issues/new)                                 |
  | wmf      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |

### <a name="support-requests"></a>지원 요청

- 지원 질문이 단순한 경우 정중히 답변하고 문제를 종결합니다.
- 질문이 더 복잡하거나 제출자가 추가 질문으로 회신하는 경우 포럼 및 지원 채널로 리디렉션합니다. 포럼으로 리디렉션하기 위한 텍스트 제안:

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a>사용 규정 위반

- 필요한 경우 문제를 편집하여 악의적인 콘텐츠를 제거합니다.
- 해당 문제가 스팸이라는 설명을 입력하고, 문제를 종결한 다음 잠가 의견 추가를 방지합니다.
- 각 위반을 주간 심사에서 논의 하 여 추가 작업 (GitHub 또는 Microsoft 법률 보고서)에 대 한 필요성을 확인 해야 합니다.

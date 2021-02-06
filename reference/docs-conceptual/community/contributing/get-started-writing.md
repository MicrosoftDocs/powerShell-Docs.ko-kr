---
title: PowerShell 설명서에 기여 시작
description: 이 문서는 PowerShell 설명서에 대한 기여자로 시작하는 방법을 간단히 설명합니다.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: ddcbf79de1ab05b901ce1abd67f65b2524ed164d
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "99601037"
---
# <a name="get-started-contributing-to-powershell-documentation"></a>PowerShell 설명서에 기여 시작

이 문서는 PowerShell 설명서에 대한 기여자로 시작하는 방법을 간단히 설명합니다.

## <a name="powershell-docs-structure"></a>PowerShell-Docs 구조

[PowerShell 문서 리포지토리][psdocs] 는 두 개의 콘텐츠 그룹인 참조 및 개념으로 나뉩니다.

### <a name="reference-content"></a>참조 콘텐츠

참조 콘텐츠는 PowerShell에서 제공 하는 cmdlet에 대 한 PowerShell cmdlet 참조입니다.
[참조][ref] 는 버전 폴더 (5.1, 7.0, 7.1 및 7.2)에서 수집 됩니다. 이 콘텐츠에는 PowerShell과 함께 제공 되는 모듈에 대 한 cmdlet 참조만 포함 되어 있습니다. 이 콘텐츠는 cmdlet에서 표시 하는 도움말 정보를 만드는 데도 사용 됩니다 `Get-Help` .

### <a name="conceptual-content"></a>개념적 콘텐츠

개념 설명서에는 다음과 같은 내용이 포함 되어 있습니다.

- 릴리스 정보
- 설치 지침
- 샘플 스크립트 및 방법 문서
- DSC 설명서
- SDK 설명서

[개념 설명서][conceptual] 는 버전 별로 구성 되지 않습니다. 모든 아티클이 모든 버전의 PowerShell에 대해 표시 됩니다. 버전별 문서를 만들기 위해 노력 하 고 있습니다. 설명서에서이 기능을 사용할 수 있는 경우이 가이드가 적절 한 정보로 업데이트 됩니다.

> [!NOTE]
> 개념 문서를 추가, 제거 또는 이름을 변경할 때마다 TOC를 업데이트 하 고 끌어오기 요청에 포함 해야 합니다.

## <a name="creating-new-articles"></a>새 문서 만들기

참가 하려는 새 문서에 대 한 GitHub 문제를 만들어야 합니다. 기존 문제를 확인 하 여 노력이 중복 되지 않는지 확인 합니다. 할당 된 문제는로 간주 됩니다 `in progress` . 문제에 대 한 공동 작업을 하려는 경우 해당 문제에 할당 된 담당자에 게 문의 하세요.

PowerShell [RFC 프로세스][rfc]와 마찬가지로 콘텐츠를 작성 하기 전에 문제를 만듭니다. 이 문제는 PowerShell-Docs 팀에서 거부 하는 작업에 대 한 시간과 노력을 낭비 하지 않도록 합니다. 이 문제를 통해 콘텐츠의 범위를 확인 하 고 PowerShell 설명서에 맞는 위치를 확인할 수 있습니다. 모든 아티클은 TOC (목차)에 포함 되어야 합니다. 제안 된 TOC 위치는 문제 토론에 포함 되어야 합니다.

> [!NOTE]
> 참조 콘텐츠의 TOC는 게시 시스템에서 자동으로 생성 됩니다. TOC를 업데이트할 필요가 없습니다.

## <a name="updating-existing-articles"></a>기존 아티클 업데이트

해당 하는 경우이 리포지토리에서 관리 되는 모든 버전의 PowerShell에서 cmdlet 참조 문서가 중복 됩니다. Cmdlet 참조 또는 아티클에 대 한 문제를 보고할 때 `About_` 문제의 영향을 받는 버전을 지정 해야 합니다. GitHub의 문제 템플릿에는 버전의 검사 목록이 포함 되어 있습니다. 확인란을 사용 하 여 영향을 받는 콘텐츠의 버전을 지정 합니다.

모든 버전의 문서를 확인 하 여 다른 버전에서 동일한 변경이 필요한 지 확인 합니다. 파일의 각 버전에 적절 한 변경 내용을 적용 합니다.

## <a name="localized-content"></a>지역화 된 콘텐츠

PowerShell 설명서는 영어로 작성 되었으며 17 개의 다른 언어로 번역 되어 있습니다. 영어 콘텐츠는 이라는 GitHub 리포지토리에 저장 됩니다 `MicrosoftDocs/PowerShell-Docs` . 지역화 된 콘텐츠는 각 언어에 대해 별도의 리포지토리에 저장 됩니다. 리포지토리는 동일한 basename를 사용 하지만 끝에 로캘 이름을 추가 합니다. 예를 들어에는 `MicrosoftDocs/PowerShell-Docs.de-de` 독일어로 번역 된 콘텐츠가 포함 되어 있습니다.

일반적으로 문제 및 변경 내용은 영어 리포지토리로 제출 해야 합니다. 모든 번역은 먼저 영어 콘텐츠에서 시작 됩니다. 사용자와 기계 번역을 모두 사용 합니다.

| Translation 메서드  |                              언어                               |
| ------------------- | -------------------------------------------------------------------- |
| 사용자 변환   | de-de, es, fr-fr, it, ja-jp, ko-kr, ko-kr-KR, pt-BR, zh-cn,, zh-cn |
| 기계 번역 | cs-CZ, hu-hu-HU-HU, nl-NL, pl, pt-PT, sv-SE, tr-TR                      |

기계 번역으로 변환 된 콘텐츠가 항상 올바른 단어 선택 및 문법을 초래 하지 않을 수 있습니다. 문서에 대 한 기술 세부 정보가 아니라 모든 언어에 대 한 번역에서 오류를 발견 한 경우 지역화 된 리포지토리에서 문제를 엽니다. 번역이 잘못 된 것으로 생각 하는 이유를 설명 합니다. Microsoft의 지역화 팀은 이러한 문제를 검토 하 고 대응 합니다.

## <a name="next-steps"></a>다음 단계

GitHub에서 변경 내용을 전송 하는 일반적인 방법에는 두 가지가 있습니다. 두 방법 모두 중앙 참가자 가이드에 설명 되어 있습니다.

1. GitHub 웹 인터페이스에서 [기존 문서를 신속 하 게 편집할](/contribute/#quick-edits-to-existing-documents) 수 있습니다.
1. [전체 GitHub 워크플로][making-changes] 를 사용 하 여 새 문서를 추가 하거나 여러 파일을 업데이트 하거나 기타 많은 변경 내용을 업데이트 합니다.

변경을 시작 하기 전에 PowerShell-Docs 리포지토리의 포크를 만들어야 합니다. PowerShell 문서 복사본의 작업 분기에서 변경 해야 합니다. GitHub에서 **빠른 편집** 방법을 사용 하는 경우 이러한 단계가 처리 됩니다. **전체 GitHub 워크플로** 를 사용 하는 경우 [로컬에서 작동][fork]하도록 설정 해야 합니다.

두 메서드는 모두 끌어오기 요청 (PR) 만들기로 끝납니다. 자세한 내용은 [끌어오기 요청 제출](pull-requests.md) 및 모범 사례를 참조 하세요.

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md

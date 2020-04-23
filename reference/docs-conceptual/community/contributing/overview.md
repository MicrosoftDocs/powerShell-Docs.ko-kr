---
title: PowerShell 설명서에 기여하기
description: 이 문서는 PowerShell 설명서의 기여자로 시작하는 방법을 간단히 설명합니다.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 5db78ae2805cb26aa79aa698cfb8b5d8ba8911dc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "79402630"
---
# <a name="contributing-to-powershell-documentation"></a>PowerShell 설명서에 기여하기

PowerShell을 지원해 주셔서 감사합니다!

기여자 가이드는 Microsoft에서 설명서를 만드는 데 사용하는 도구와 프로세스를 설명하는 문서 모음입니다. 이러한 가이드 중 일부는 [docs.microsoft.com][docs]에 게시된 모든 문서 집합의 일반적인 정보를 다루며, 일부 가이드는 PowerShell 설명서 작성 방법과 관련되어 있습니다.

일반 문서는 Microsoft의 통합 [기여자 가이드][contribute]에서 확인할 수 있습니다. PowerShell 관련 가이드는 여기에서 확인하세요.

## <a name="ways-to-contribute"></a>참가 방법

두 가지 방법으로 기여할 수 있습니다. 두 방법 모두 큰 도움이 됩니다.

- [문제 제출][file-an-issue]은 Microsoft가 설명서의 문제와 공백을 식별하는 데 도움이 됩니다. 때로는 문제 해결이 어렵고 더 많은 조사와 연구가 필요할 수 있습니다. 이 경우 문제 프로세스를 통해 문제에 관해 대화하고 만족스러운 해결책을 찾을 수 있습니다.

- 새로운 콘텐츠를 제출하거나 기존 문서를 변경하는 프로세스에는 더욱 긴밀한 참여가 필요합니다. 다음 정보에는 설명서에 콘텐츠를 제출하기 위한 도구, 프로세스, 표준이 간략하게 설명되어 있습니다.

## <a name="prepare-to-make-a-contribution"></a>기여 준비

설명서에 기여하려면 GitHub 계정이 필요합니다. 기여를 위한 도구를 획득하고 기여 프로세스를 이해하려면 다음 검사 목록을 활용하세요.

1. [GitHub에 등록](/contribute/get-started-setup-github)
1. [Git 및 Markdown 도구 설치](/contribute/get-started-setup-tools)
1. [Docs Authoring Pack 설치](/contribute/how-to-write-docs-auth-pack)
1. [Posh-Git 설치][posh-git] - 필수는 아니지만 권장 사항
1. [로컬 Git 리포지토리 설정](/contribute/get-started-setup-local)
1. [Git 및 GitHub 기본 사항 검토](/contribute/git-github-fundamentals)

## <a name="get-started-writing-docs"></a>문서 작성 시작

다음 두 가지 방법으로 설명서에 변경 내용을 적용할 수 있습니다.

1. [기존 문서의 빠른 편집](/contribute/#quick-edits-to-existing-documents)
   - 사소한 교정, 오타 수정 또는 약간의 내용 추가
1. [문서의 전체 GitHub 워크플로](/contribute/how-to-write-workflows-major)
   - 대규모 변경, 여러 버전 작성, 이미지 추가나 변경 또는 새 문서 작성

통합 기여자 가이드의 [문서 작성 필수 정보](/contribute/style-quick-start) 섹션도 참조해 보세요. 또 다른 훌륭한 리소스는 [Microsoft 문서 작성 스타일 가이드][style-guide]입니다. Microsoft 문서 작성 스타일 가이드의 목표는 편집자, 기술 작성자, 개발자, 마케터 및 IT 분야에 있는 그 밖의 모든 사람이 더 나은 콘텐츠를 작성하도록 돕는 것입니다.

공개 리포지토리의 설명서 및 코드 예시의 사소한 수정이나 설명은 docs.microsoft.com의 [사용 약관][terms-of-use]에서 다룹니다.

중요한 변경을 적용하는 경우에는 전체 GitHub 워크플로를 사용하세요. Microsoft 직원이 아니라면 중요한 변경 내용을 적용할 경우 [기여 라이센스 규약(CLA)][cla] 제출을 요청하는 주석이 끌어오기 요청에 생성됩니다. Microsoft가 끌어오기 요청을 검토하거나 수락하려면 기여자가 먼저 온라인 양식을 작성해야 합니다.

## <a name="code-of-conduct"></a>사용 규정

docs.microsoft.com에 게시되는 모든 리포지토리는 [Microsoft 오픈 소스 사용 규정](https://opensource.microsoft.com/codeofconduct/) 또는 [.NET Foundation 사용 규정](https://dotnetfoundation.org/code-of-conduct)을 채택하고 있습니다. 자세한 내용은 [사용 규정 FAQ](https://opensource.microsoft.com/codeofconduct/faq/)를 참조하세요.

## <a name="next-steps"></a>다음 단계

다음 문서에서는 PowerShell 설명서 관련 정보를 다룹니다. 통합 기여자 가이드의 지침과 중복되는 부분이 발견되면, Microsoft는 이러한 규칙이 PowerShell 콘텐츠의 경우 어떻게 적용되는지를 확인합니다.

다음 문서를 검토합니다.

- [문제 제출 방법](file-an-issue.md)
- [문서 작성 시작하기](get-started-writing.md)
- [끌어오기 요청 제출하기](pull-requests.md)
- [PowerShell-Docs 스타일 가이드](powershell-style-guide.md)
- [cmdlet 참조 편집하기](editing-cmdlet-ref.md)

추가 리소스

- [편집 검사 목록](editorial-checklist.md)
- [문제 관리 방법](managing-issues.md)
- [끌어오기 요청 관리 방법](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: https://docs.microsoft.com/powershell
[style-guide]: https://docs.microsoft.com/style-guide/welcome/
[terms-of-use]: https://docs.microsoft.com/legal/termsofuse
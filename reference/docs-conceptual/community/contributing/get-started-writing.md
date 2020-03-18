---
title: PowerShell 설명서에 기여 시작
description: 이 문서는 PowerShell 설명서에 대한 기여자로 시작하는 방법을 간단히 설명합니다.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 95eb2c3157a99fcb6560914da8464022e1b64fad
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060308"
---
# <a name="get-started-contributing-to-powershell-documentation"></a>PowerShell 설명서에 기여 시작

이 문서는 PowerShell 설명서에 대한 기여자로 시작하는 방법을 간단히 설명합니다.

## <a name="powershell-docs-structure"></a>PowerShell-Docs 구조

[PowerShell-Docs 리포지토리][psdocs]는 두 개의 콘텐츠 그룹으로 구분됩니다. Git 분기는 설명서가 게시되는 방법 및 시기를 관리하는 데 사용됩니다.

### <a name="reference-content"></a>참조 콘텐츠

참조 콘텐츠는 PowerShell에서 제공하는 cmdlet에 대한 PowerShell cmdlet 참조입니다.
[참조][ref]는 버전 폴더(5.1, 6, 7.0 및 7.1)에 수집됩니다. 이 콘텐츠에는 PowerShell과 함께 제공되는 모듈에 대한 cmdlet 참조만 포함되어 있습니다. 이 콘텐츠는 `Get-Help` cmdlet에 표시되는 도움말 정보를 만드는 데에도 사용됩니다.

> [!NOTE]
> 참조 콘텐츠의 TOC(목차)는 게시 시스템에서 자동으로 생성됩니다. TOC를 업데이트할 필요가 없습니다.

### <a name="conceptual-content"></a>개념 콘텐츠

개념 설명서에는 다음 콘텐츠가 포함됩니다.

- 릴리스 정보
- 설치 지침
- 샘플 스크립트 및 방법 문서
- DSC 설명서
- SDK 설명서

[개념 설명서][conceptual]는 버전별로 구성되어 있지 않습니다. 모든 문서는 PowerShell의 모든 버전에 대해 표시됩니다. Microsoft는 버전별 문서를 만들기 위해 노력하고 있습니다. 설명서에서 이 기능을 사용할 수 있는 경우 가이드에 적절한 정보가 업데이트됩니다.

> [!NOTE]
> 개념 문서를 추가, 제거 또는 이름 변경할 때마다 TOC를 업데이트하고 끌어오기 요청에 포함해야 합니다.

## <a name="using-git-branches"></a>Git 분기 사용

PowerShell-Docs 기본 분기는 `staging` 분기입니다. 작업 분기에서 수행한 변경은 게시 전에 `staging` 분기로 병합됩니다. 일주일에 한 번 `staging` 분기가 `live` 분기로 병합됩니다. `live` 분기에는 docs.microsoft.com에 게시된 콘텐츠가 포함되어 있습니다. `live` 분기에서는 직접 변경을 수행하면 안 됩니다.

릴리스되지 않은 버전의 PowerShell에만 적용되는 문서에 대한 변경 내용을 제출하는 경우 해당 버전에 대한 릴리스 분기가 있는지 확인하세요. 특정 향후 버전에 적용되는 모든 변경 내용은 릴리스 분기를 대상으로 해야 합니다. 릴리스 분기의 이름 패턴은 `release-<version>`입니다.

변경을 시작하기 전에 PowerShell-Docs 리포지토리의 로컬 복사본에 작업 분기를 만듭니다. 이는 [포크의 복제본][fork]이어야 합니다. 작업 분기를 만들기 전에 로컬 리포지토리를 동기화해야 합니다. `staging` 또는 `release` 분기의 최신 복사본에서 작업 분기를 만들어야 합니다.

통합 기여자 가이드 [변경][making-changes] 섹션의 프로세스에 따라 제출하려는 변경을 수행합니다.

### <a name="creating-new-articles"></a>새 문서 만들기

참가하려는 새 문서에 대해 GitHub 문제를 만들어야 합니다. 기존 문제를 확인하여 중복되는 문제가 없는지 확인합니다. 다른 사용자에게 할당된 문제는 "진행 중"으로 간주됩니다. 문제에 대한 공동 작업을 원하는 경우 해당 문제에 할당된 담당자에게 문의하세요.

PowerShell [RFC 프로세스][rfc]와 마찬가지로, 콘텐츠를 작성하기 전에 문제를 만들면 PowerShell-Docs 팀에서 거부한 콘텐츠에 많은 시간과 노력을 소비하지 않을 수 있습니다. Microsoft도 콘텐츠의 범위 및 PowerShell 설명서 해당 부분을 기여자와 상의할 수 있습니다.

### <a name="updating-existing-articles"></a>기존 문서 업데이트

해당하는 경우 cmdlet 참조 문서는 PowerShell의 모든 버전으로 복제됩니다. Cmdlet 참조 또는 `About_` 문서에 대한 문제를 보고할 경우 문제의 영향을 받는 버전을 지정해야 합니다. GitHub의 문제 템플릿에는 버전 검사 목록이 포함되어 있습니다. 확인란을 사용하여 영향을 받는 콘텐츠의 버전을 지정합니다. 콘텐츠의 여러 버전에 영향을 주는 문제에 대한 문서의 변경 내용을 제출할 경우 파일의 각 버전에 적절한 변경 내용을 적용해야 합니다.

## <a name="next-steps"></a>다음 단계

[끌어오기 요청 제출](pull-requests.md)을 참조하세요.

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md
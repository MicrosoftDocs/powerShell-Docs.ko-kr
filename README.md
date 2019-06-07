---
ms.openlocfilehash: 84b29953f09eb62eb30f52d84b087eb4f1f90eed
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470651"
---
# <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 오픈 소스 규정

이 프로젝트에서는 [Microsoft 오픈 소스 규정](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다.
자세한 내용은 [규정 FAQ](https://opensource.microsoft.com/codeofconduct/faq/)를 참조하고, 질문이나 의견이 더 있는 경우는 [opencode@microsoft.com](mailto:opencode@microsoft.com)으로 문의하세요.

[라이브 배지]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[스테이징 배지]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a>빌드 상태

| 라이브 분기 | 스테이징 분기 |
|:------------|:---------------|
| [![라이브 배지][]][라이브 배지] | [![스테이징 배지][]][스테이징 배지]

## <a name="powershell-documentation"></a>PowerShell 설명서

공식 PowerShell 설명서가 있는 PowerShell-Docs 리포지토리를 시작합니다.

## <a name="repository-structure"></a>리포지토리 구조

이 리포지토리에서 다음의 각 최상위 폴더에는 [Microsoft Docs](https://docs.microsoft.com/powershell)에 게시되는 DocSet이 있습니다.

- [/developer/](https://docs.microsoft.com/powershell/developer/)는 향후에 PowerShell SDK 설명서의 홈이 됩니다.
  - Microsoft는 이 콘텐츠를 MSDN에서 마이그레이션하는 중입니다.
- [/dsc/](https://docs.microsoft.com/powershell/dsc/)는 필요한 상태 구성 기능에 사용
- [/gallery/](https://docs.microsoft.com/powershell/gallery)는 [PowerShell 갤러리](https://www.powershellgallery.com/)에 사용
- [/jea/](https://docs.microsoft.com/powershell/jea/)는 Just Enough Administration 기능에 사용
- [/reference/](https://docs.microsoft.com/powershell/scripting/)는 버전 3.0, 4.0, 5.0, 5.1, 6.0에서 PowerShell 개념 항목 및 모듈 참조에 사용
  - 이 콘텐츠는 `Get-Help` cmdlet으로 검색되는 도움말 콘텐츠의 원본이기도 함
- [/wmf](https://docs.microsoft.com/powershell/wmf/readme)에는 새 버전의 PowerShell을 이전 버전의 Windows에 배포하는 데 사용되는 패키지인 Windows Management Framework의 릴리스 정보를 포함.

## <a name="contributing"></a>참가

Microsoft는 *준비* 분기로 [끌어오기 요청](https://help.github.com/articles/using-pull-requests/)을 통해 적극적으로 이 리포지토리로 참가하도록 모읍니다.
끌어오기 요청을 제출하기 전에 [참가 사용권 계약에 서명](https://cla.microsoft.com/)하여 커뮤니티에서 제출한 사항을 자유롭게 사용할 수 있도록 해야 합니다.

참가에 대한 자세한 내용은 [Contributor 가이드](CONTRIBUTING.md)를 참조하세요.
Contributor 가이드에는 설명서에 참가하는 방법, 제안되는 도구, 스타일 및 서식 요구 사항에 대한 자세한 정보가 들어 있습니다.
설명서 버전 간에 일관성을 유지할 수 있도록 문제 및 끌어오기 요청 템플릿을 사용하세요.

## <a name="licenses"></a>라이선스

이 프로젝트에 대한 라이선스 파일은 두 개가 있습니다.
MIT 라이선스는 이 리포지토리에 포함된 코드에 적용됩니다.
Creative Commons 라이선스는 설명서에 적용됩니다.
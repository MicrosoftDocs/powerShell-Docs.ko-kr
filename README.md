---
ms.openlocfilehash: f46b14e44c32ce31b4da1a14580fe03564bf9946
ms.sourcegitcommit: 0e18be0a2869beaa711ba3eca7a8a15514e5e962
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91899268"
---
# <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 오픈 소스 준수 사항

이 프로젝트는 [Microsoft 오픈 소스 준수 사항](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다. 자세한 내용은 [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/)(준수 사항 FAQ)를 참조하거나 [opencode@microsoft.com](mailto:opencode@microsoft.com)에 추가 질문 또는 의견을 알려주세요.

[라이브 배지]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[스테이징 배지]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a>빌드 상태

|          라이브 분기          |           스테이징 분기            |
| :---------------------------- | :---------------------------------- |
| [![라이브 배지][]][라이브 배지] | [![스테이징 배지][]][스테이징 배지] |

## <a name="powershell-documentation"></a>PowerShell 설명서

공식 PowerShell 설명서의 홈인 PowerShell-Docs 리포지토리를 시작합니다.

## <a name="repository-structure"></a>리포지토리 구조

다음 목록은 이 리포지토리의 기본 폴더를 설명합니다.

- `.github` - 이 리포지토리에 대해 GitHub에서 사용되는 구성 설정이 포함되어 있습니다.
- `.vscode` - VS Code(Visual Studio Code)에 대한 구성 설정 및 권장 확장이 포함되어 있습니다.
- `assets` - 설명서에 연결된 다운로드 가능한 파일이 포함되어 있습니다.
- `reference` - [docs.microsoft.com]([https://docs.microsoft.com/powershell/scripting/)에 게시된 설명서가 포함되어 있습니다. 여기에는 참조 콘텐츠와 개념 콘텐츠가 모두 포함됩니다.
  - `5.1` - PowerShell 5.1에 대한 cmdlet 참조 및 정보 항목이 포함되어 있습니다.
  - `6` - PowerShell 6에 대한 cmdlet 참조 및 정보 항목이 포함되어 있습니다.
  - `7.0` - PowerShell 7.0에 대한 cmdlet 참조 및 정보 항목이 포함되어 있습니다.
  - `7.1` - PowerShell 7.1에 대한 cmdlet 참조 및 정보 항목이 포함되어 있습니다.
  - `bread` - 이동 경로 탐색에 사용되는 TOC가 포함되어 있습니다.
  - `docs-conceptual` - Docs 사이트에 게시된 개념 문서가 포함되어 있습니다. 일반적으로 폴더 구조는 TOC(목차)를 미러링합니다.
  - `mapping` - 빌드 시스템에서 사용되는 버전 매핑 구성이 포함되어 있습니다.
  - `media` - 설명서에 사용되는 이미지 파일이 포함되어 있습니다. `docs-conceptual` 콘텐츠 전체에 미디어 폴더가 있습니다. 설명서에서 이미지를 사용하는 방법에 대한 자세한 내용은 기여자 가이드를 참조하세요.
  - `module` - 모듈 브라우저 페이지의 markdown 소스가 포함되어 있습니다.
- `tests` - 빌드 시스템에서 사용되는 Pester 테스트가 포함되어 있습니다.
- `tools` - 빌드 시스템에서 사용되는 기타 도구가 포함되어 있습니다.

> 참고: 참조 콘텐츠(번호가 매겨진 폴더 구조)는 Docs 사이트의 웹 페이지와 PowerShell에서 사용되는 업데이트할 수 있는 도움말을 만드는 데 사용됩니다.
> `docs-conceptual` 폴더의 문서는 Docs 웹 사이트에만 게시됩니다.

## <a name="contributing"></a>참여

Microsoft는 _스테이징_ 분기로의 [끌어오기 요청](https://help.github.com/articles/using-pull-requests/)을 통한 이 리포지토리에 대한 퍼블릭 기여를 환영합니다.
Microsoft에서 기여자의 끌어오기 요청을 수락하려면 먼저 기여자가 [기여 사용권 계약](https://cla.microsoft.com/)에 서명해야 합니다. 이 설정은 한 번만 수행하면 됩니다.

참가에 대한 자세한 내용은 [Contributor 가이드](https://aka.ms/PSDocsContributor)를 참조하세요. Contributor 가이드에는 설명서에 참가하는 방법, 제안되는 도구, 스타일 및 서식 요구 사항에 대한 자세한 정보가 들어 있습니다. 설명서 버전 간에 일관성을 유지할 수 있도록 문제 및 끌어오기 요청 템플릿을 사용하세요.

## <a name="licenses"></a>라이선스

이 프로젝트에 대한 라이선스 파일은 두 개가 있습니다. MIT 라이선스는 이 리포지토리에 포함된 코드에 적용됩니다. Creative Commons 라이선스는 설명서에 적용됩니다.

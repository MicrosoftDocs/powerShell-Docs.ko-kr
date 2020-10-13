---
ms.openlocfilehash: f46b14e44c32ce31b4da1a14580fe03564bf9946
ms.sourcegitcommit: 0e18be0a2869beaa711ba3eca7a8a15514e5e962
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91899268"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="5ef11-101">Microsoft 오픈 소스 준수 사항</span><span class="sxs-lookup"><span data-stu-id="5ef11-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="5ef11-102">이 프로젝트는 [Microsoft 오픈 소스 준수 사항](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span> <span data-ttu-id="5ef11-103">자세한 내용은 [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/)(준수 사항 FAQ)를 참조하거나 [opencode@microsoft.com](mailto:opencode@microsoft.com)에 추가 질문 또는 의견을 알려주세요.</span><span class="sxs-lookup"><span data-stu-id="5ef11-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

[라이브 배지]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[live-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[스테이징 배지]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging
[staging-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a><span data-ttu-id="5ef11-106">빌드 상태</span><span class="sxs-lookup"><span data-stu-id="5ef11-106">Build Status</span></span>

|          <span data-ttu-id="5ef11-107">라이브 분기</span><span class="sxs-lookup"><span data-stu-id="5ef11-107">Live Branch</span></span>          |           <span data-ttu-id="5ef11-108">스테이징 분기</span><span class="sxs-lookup"><span data-stu-id="5ef11-108">Staging Branch</span></span>            |
| :---------------------------- | :---------------------------------- |
| <span data-ttu-id="5ef11-109">[![라이브 배지][]][라이브 배지]</span><span class="sxs-lookup"><span data-stu-id="5ef11-109">[![live-badge][]][live-badge]</span></span> | <span data-ttu-id="5ef11-110">[![스테이징 배지][]][스테이징 배지]</span><span class="sxs-lookup"><span data-stu-id="5ef11-110">[![staging-badge][]][staging-badge]</span></span> |

## <a name="powershell-documentation"></a><span data-ttu-id="5ef11-111">PowerShell 설명서</span><span class="sxs-lookup"><span data-stu-id="5ef11-111">PowerShell Documentation</span></span>

<span data-ttu-id="5ef11-112">공식 PowerShell 설명서의 홈인 PowerShell-Docs 리포지토리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-112">Welcome to the PowerShell-Docs repository, the home of the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="5ef11-113">리포지토리 구조</span><span class="sxs-lookup"><span data-stu-id="5ef11-113">Repository Structure</span></span>

<span data-ttu-id="5ef11-114">다음 목록은 이 리포지토리의 기본 폴더를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-114">The following list describes the main folders in this repository.</span></span>

- <span data-ttu-id="5ef11-115">`.github` - 이 리포지토리에 대해 GitHub에서 사용되는 구성 설정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-115">`.github` - contains configuration settings used by GitHub for this repository</span></span>
- <span data-ttu-id="5ef11-116">`.vscode` - VS Code(Visual Studio Code)에 대한 구성 설정 및 권장 확장이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-116">`.vscode` - contains configuration settings and recommended extensions for Visual Studio Code (VS Code)</span></span>
- <span data-ttu-id="5ef11-117">`assets` - 설명서에 연결된 다운로드 가능한 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-117">`assets` - contains downloadable files linked in the documentation</span></span>
- <span data-ttu-id="5ef11-118">`reference` - [docs.microsoft.com]([https://docs.microsoft.com/powershell/scripting/)에 게시된 설명서가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-118">`reference` - contains the documentation published to [docs.microsoft.com]([https://docs.microsoft.com/powershell/scripting/).</span></span> <span data-ttu-id="5ef11-119">여기에는 참조 콘텐츠와 개념 콘텐츠가 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-119">This includes both reference and conceptual content.</span></span>
  - <span data-ttu-id="5ef11-120">`5.1` - PowerShell 5.1에 대한 cmdlet 참조 및 정보 항목이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-120">`5.1` - contains the cmdlet reference and about topics for PowerShell 5.1</span></span>
  - <span data-ttu-id="5ef11-121">`6` - PowerShell 6에 대한 cmdlet 참조 및 정보 항목이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-121">`6` - contains the cmdlet reference and about topics for PowerShell 6</span></span>
  - <span data-ttu-id="5ef11-122">`7.0` - PowerShell 7.0에 대한 cmdlet 참조 및 정보 항목이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-122">`7.0` - contains the cmdlet reference and about topics for PowerShell 7.0</span></span>
  - <span data-ttu-id="5ef11-123">`7.1` - PowerShell 7.1에 대한 cmdlet 참조 및 정보 항목이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-123">`7.1` - contains the cmdlet reference and about topics for PowerShell 7.1</span></span>
  - <span data-ttu-id="5ef11-124">`bread` - 이동 경로 탐색에 사용되는 TOC가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-124">`bread` - contains the TOC used for breadcrumb navigation</span></span>
  - <span data-ttu-id="5ef11-125">`docs-conceptual` - Docs 사이트에 게시된 개념 문서가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-125">`docs-conceptual` - contains the conceptual articles that are published to the Docs site.</span></span> <span data-ttu-id="5ef11-126">일반적으로 폴더 구조는 TOC(목차)를 미러링합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-126">In general, the folder structure mirrors the Table of Contents (TOC).</span></span>
  - <span data-ttu-id="5ef11-127">`mapping` - 빌드 시스템에서 사용되는 버전 매핑 구성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-127">`mapping` - contains the version mapping configuration used by the build system</span></span>
  - <span data-ttu-id="5ef11-128">`media` - 설명서에 사용되는 이미지 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-128">`media` - contains image files used in documentation.</span></span> <span data-ttu-id="5ef11-129">`docs-conceptual` 콘텐츠 전체에 미디어 폴더가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-129">There are media folders throughout the `docs-conceptual` content.</span></span> <span data-ttu-id="5ef11-130">설명서에서 이미지를 사용하는 방법에 대한 자세한 내용은 기여자 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5ef11-130">See the Contributor Guide for information on using images in documentation.</span></span>
  - <span data-ttu-id="5ef11-131">`module` - 모듈 브라우저 페이지의 markdown 소스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-131">`module` - contains the markdown source for the Module Browser page</span></span>
- <span data-ttu-id="5ef11-132">`tests` - 빌드 시스템에서 사용되는 Pester 테스트가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-132">`tests` - contains the Pester tests used by the build system</span></span>
- <span data-ttu-id="5ef11-133">`tools` - 빌드 시스템에서 사용되는 기타 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-133">`tools` - contains other tools used by the build system</span></span>

> <span data-ttu-id="5ef11-134">참고: 참조 콘텐츠(번호가 매겨진 폴더 구조)는 Docs 사이트의 웹 페이지와 PowerShell에서 사용되는 업데이트할 수 있는 도움말을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-134">NOTE: The reference content (in the numbered folders) is used to create the webpages on the Docs site as well as the updateable help used by PowerShell.</span></span>
> <span data-ttu-id="5ef11-135">`docs-conceptual` 폴더의 문서는 Docs 웹 사이트에만 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-135">The articles in the `docs-conceptual` folder are only published to the Docs website.</span></span>

## <a name="contributing"></a><span data-ttu-id="5ef11-136">참여</span><span class="sxs-lookup"><span data-stu-id="5ef11-136">Contributing</span></span>

<span data-ttu-id="5ef11-137">Microsoft는 _스테이징_ 분기로의 [끌어오기 요청](https://help.github.com/articles/using-pull-requests/)을 통한 이 리포지토리에 대한 퍼블릭 기여를 환영합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-137">We welcome public contributions into this repository via [pull requests](https://help.github.com/articles/using-pull-requests/) into the _staging_ branch.</span></span>
<span data-ttu-id="5ef11-138">Microsoft에서 기여자의 끌어오기 요청을 수락하려면 먼저 기여자가 [기여 사용권 계약](https://cla.microsoft.com/)에 서명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-138">Please note that before we can accept your pull request you must sign our [Contribution License Agreement](https://cla.microsoft.com/).</span></span> <span data-ttu-id="5ef11-139">이 설정은 한 번만 수행하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-139">This is a one-time requirement.</span></span>

<span data-ttu-id="5ef11-140">참가에 대한 자세한 내용은 [Contributor 가이드](https://aka.ms/PSDocsContributor)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5ef11-140">For more information on contributing, read our [contributor's guide](https://aka.ms/PSDocsContributor).</span></span> <span data-ttu-id="5ef11-141">Contributor 가이드에는 설명서에 참가하는 방법, 제안되는 도구, 스타일 및 서식 요구 사항에 대한 자세한 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-141">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span> <span data-ttu-id="5ef11-142">설명서 버전 간에 일관성을 유지할 수 있도록 문제 및 끌어오기 요청 템플릿을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="5ef11-142">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="5ef11-143">라이선스</span><span class="sxs-lookup"><span data-stu-id="5ef11-143">Licenses</span></span>

<span data-ttu-id="5ef11-144">이 프로젝트에 대한 라이선스 파일은 두 개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-144">There are two license files for this project.</span></span> <span data-ttu-id="5ef11-145">MIT 라이선스는 이 리포지토리에 포함된 코드에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-145">The MIT License applies to the code contained in this repo.</span></span> <span data-ttu-id="5ef11-146">Creative Commons 라이선스는 설명서에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef11-146">The Creative Commons license applies to the documentation.</span></span>

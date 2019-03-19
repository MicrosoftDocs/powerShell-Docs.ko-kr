---
ms.openlocfilehash: 6e36e6599e36218ce2a925dceda7aa0ee6811057
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "58142231"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="a3717-101">Microsoft 오픈 소스 규정</span><span class="sxs-lookup"><span data-stu-id="a3717-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="a3717-102">이 프로젝트에서는 [Microsoft 오픈 소스 규정](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다.</span><span class="sxs-lookup"><span data-stu-id="a3717-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="a3717-103">자세한 내용은 [규정 FAQ](https://opensource.microsoft.com/codeofconduct/faq/)를 참조하고, 질문이나 의견이 더 있는 경우는 [opencode@microsoft.com](mailto:opencode@microsoft.com)으로 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="a3717-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

<span data-ttu-id="a3717-104">[![빌드 상태](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)</span><span class="sxs-lookup"><span data-stu-id="a3717-104">[![Build status](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)</span></span>

## <a name="powershell-documentation"></a><span data-ttu-id="a3717-105">PowerShell 설명서</span><span class="sxs-lookup"><span data-stu-id="a3717-105">PowerShell Documentation</span></span>

<span data-ttu-id="a3717-106">공식 PowerShell 설명서가 있는 PowerShell-Docs 리포지토리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a3717-106">Welcome to the PowerShell-Docs repository, housing the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="a3717-107">리포지토리 구조</span><span class="sxs-lookup"><span data-stu-id="a3717-107">Repository Structure</span></span>

<span data-ttu-id="a3717-108">이 리포지토리에서 다음의 각 최상위 폴더에는 [Microsoft Docs](https://docs.microsoft.com/powershell)에 게시되는 DocSet이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3717-108">Each of the following top-level folders in this repo contain a DocSet that is published to [Microsoft Docs](https://docs.microsoft.com/powershell).</span></span>

- <span data-ttu-id="a3717-109">[/developer/](https://docs.microsoft.com/powershell/developer/)는 향후에 PowerShell SDK 설명서의 홈이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3717-109">[/developer/](https://docs.microsoft.com/powershell/developer/) is the future home of the PowerShell SDK documentation</span></span>
  - <span data-ttu-id="a3717-110">Microsoft는 이 콘텐츠를 MSDN에서 마이그레이션하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="a3717-110">We are in the process of migrating this content from MSDN</span></span>
- <span data-ttu-id="a3717-111">[/dsc/](https://docs.microsoft.com/powershell/dsc/)는 필요한 상태 구성 기능에 사용</span><span class="sxs-lookup"><span data-stu-id="a3717-111">[/dsc/](https://docs.microsoft.com/powershell/dsc/) is for the Desired State Configuration feature</span></span>
- <span data-ttu-id="a3717-112">[/gallery/](https://docs.microsoft.com/powershell/gallery)는 [PowerShell 갤러리](https://www.powershellgallery.com/)에 사용</span><span class="sxs-lookup"><span data-stu-id="a3717-112">[/gallery/](https://docs.microsoft.com/powershell/gallery) is for the [PowerShell Gallery](https://www.powershellgallery.com/)</span></span>
- <span data-ttu-id="a3717-113">[/jea/](https://docs.microsoft.com/powershell/jea/)는 Just Enough Administration 기능에 사용</span><span class="sxs-lookup"><span data-stu-id="a3717-113">[/jea/](https://docs.microsoft.com/powershell/jea/) is for the Just Enough Administration feature</span></span>
- <span data-ttu-id="a3717-114">[/reference/](https://docs.microsoft.com/powershell/scripting/)는 버전 3.0, 4.0, 5.0, 5.1, 6.0에서 PowerShell 개념 항목 및 모듈 참조에 사용</span><span class="sxs-lookup"><span data-stu-id="a3717-114">[/reference/](https://docs.microsoft.com/powershell/scripting/) is for PowerShell conceptual topics and module reference across versions 3.0, 4.0, 5.0, 5.1, and 6.0</span></span>
  - <span data-ttu-id="a3717-115">이 콘텐츠는 `Get-Help` cmdlet으로 검색되는 도움말 콘텐츠의 원본이기도 함</span><span class="sxs-lookup"><span data-stu-id="a3717-115">This content is also the source of help content retrieved by the `Get-Help` cmdlet</span></span>
- <span data-ttu-id="a3717-116">[/wmf](https://docs.microsoft.com/powershell/wmf/readme)에는 새 버전의 PowerShell을 이전 버전의 Windows에 배포하는 데 사용되는 패키지인 Windows Management Framework의 릴리스 정보를 포함.</span><span class="sxs-lookup"><span data-stu-id="a3717-116">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contains release notes for the Windows Management Framework, the package used to distribute new versions of PowerShell to previous versions of Windows.</span></span>

## <a name="contributing"></a><span data-ttu-id="a3717-117">참가</span><span class="sxs-lookup"><span data-stu-id="a3717-117">Contributing</span></span>

<span data-ttu-id="a3717-118">Microsoft는 *준비* 분기로 [끌어오기 요청](https://help.github.com/articles/using-pull-requests/)을 통해 적극적으로 이 리포지토리로 참가하도록 모읍니다.</span><span class="sxs-lookup"><span data-stu-id="a3717-118">We actively merge contributions into this repository via [pull request](https://help.github.com/articles/using-pull-requests/) into the *staging* branch.</span></span>
<span data-ttu-id="a3717-119">끌어오기 요청을 제출하기 전에 [참가 사용권 계약에 서명](https://cla.microsoft.com/)하여 커뮤니티에서 제출한 사항을 자유롭게 사용할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3717-119">Please note that before you submit a pull request you must [sign a Contribution License Agreement](https://cla.microsoft.com/) to ensure that the community is free to use your submissions.</span></span>

<span data-ttu-id="a3717-120">참가에 대한 자세한 내용은 [Contributor 가이드](CONTRIBUTING.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a3717-120">For more information on contributing, read our [contributor's guide](CONTRIBUTING.md).</span></span>
<span data-ttu-id="a3717-121">Contributor 가이드에는 설명서에 참가하는 방법, 제안되는 도구, 스타일 및 서식 요구 사항에 대한 자세한 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3717-121">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span>
<span data-ttu-id="a3717-122">설명서 버전 간에 일관성을 유지할 수 있도록 문제 및 끌어오기 요청 템플릿을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="a3717-122">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="a3717-123">라이선스</span><span class="sxs-lookup"><span data-stu-id="a3717-123">Licenses</span></span>

<span data-ttu-id="a3717-124">이 프로젝트에 대한 라이선스 파일은 두 개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3717-124">There are two license files for this project.</span></span>
<span data-ttu-id="a3717-125">MIT 라이선스는 이 리포지토리에 포함된 코드에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3717-125">The MIT License applies to the code contained in this repo.</span></span>
<span data-ttu-id="a3717-126">Creative Commons 라이선스는 설명서에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3717-126">The Creative Commons license applies to the documentation.</span></span>
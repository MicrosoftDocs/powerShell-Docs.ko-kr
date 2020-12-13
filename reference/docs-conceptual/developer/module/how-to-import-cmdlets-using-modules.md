---
ms.date: 08/28/2019
ms.topic: reference
title: 모듈을 사용하여 Cmdlet을 가져오는 방법
description: 모듈을 사용하여 Cmdlet을 가져오는 방법
ms.openlocfilehash: 485a4be4d2accaf050a6536e7f92a0673f62a30b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657287"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="412d3-103">모듈을 사용하여 Cmdlet을 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="412d3-103">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="412d3-104">이 문서에서는 이진 모듈을 사용 하 여 cmdlet을 PowerShell 세션으로 가져오는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="412d3-104">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="412d3-105">모듈의 멤버에는 cmdlet, 공급자, 함수, 변수, 별칭 등이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="412d3-105">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="412d3-106">스냅인은 cmdlet 및 공급자만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="412d3-106">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="412d3-107">모듈을 사용 하 여 cmdlet을 로드 하는 방법</span><span class="sxs-lookup"><span data-stu-id="412d3-107">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="412d3-108">Cmdlet이 구현 되는 어셈블리 파일과 이름이 같은 모듈 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="412d3-108">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="412d3-109">이 절차에서는 Windows 폴더에 module 폴더가 만들어집니다 `system32` .</span><span class="sxs-lookup"><span data-stu-id="412d3-109">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="412d3-110">`PSModulePath`환경 변수에 새 모듈 폴더에 대 한 경로가 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="412d3-110">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="412d3-111">기본적으로 시스템 폴더는 환경 변수에 이미 추가 되어 `PSModulePath` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="412d3-111">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="412d3-112">를 보려면 `PSModulePath` 을 입력 `$env:PSModulePath` 합니다.</span><span class="sxs-lookup"><span data-stu-id="412d3-112">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="412d3-113">Cmdlet 어셈블리를 모듈 폴더에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="412d3-113">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="412d3-114">`.psd1`모듈의 루트 폴더에 모듈 매니페스트 파일 ()을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="412d3-114">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="412d3-115">PowerShell은 모듈 매니페스트를 사용 하 여 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="412d3-115">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="412d3-116">자세한 내용은 [PowerShell 모듈 매니페스트를 작성 하는 방법](../module/how-to-write-a-powershell-module-manifest.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="412d3-116">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="412d3-117">다음 명령을 실행 하 여 cmdlet을 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="412d3-117">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="412d3-118">이 절차를 사용 하 여 cmdlet을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="412d3-118">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="412d3-119">어셈블리의 모든 cmdlet을 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="412d3-119">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="412d3-120">모듈에 대 한 자세한 내용은 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="412d3-120">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="412d3-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="412d3-121">See also</span></span>

[<span data-ttu-id="412d3-122">PowerShell 모듈 매니페스트를 작성하는 방법</span><span class="sxs-lookup"><span data-stu-id="412d3-122">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="412d3-123">PowerShell 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="412d3-123">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="412d3-124">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="412d3-124">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="412d3-125">모듈 설치</span><span class="sxs-lookup"><span data-stu-id="412d3-125">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="412d3-126">PSModulePath 설치 경로 수정</span><span class="sxs-lookup"><span data-stu-id="412d3-126">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

<span data-ttu-id="412d3-127">[Writing a Windows PowerShell Cmdlet](../cmdlet/cmdlet-overview.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="412d3-127">[Writing a Windows PowerShell Cmdlet](../cmdlet/cmdlet-overview.md)</span></span>

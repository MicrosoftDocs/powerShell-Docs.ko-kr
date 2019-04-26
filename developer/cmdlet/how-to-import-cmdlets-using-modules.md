---
title: 모듈을 사용 하 여 Cmdlet을 가져오는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067980"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="111e7-102">모듈을 사용하여 Cmdlet을 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="111e7-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="111e7-103">이 항목에서는 이진 모듈을 사용 하 여 Windows PowerShell 세션에 cmdlet을 가져오는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="111e7-103">This topic describes how to import cmdlets to a Windows PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="111e7-104">모듈의 멤버 cmdlet, 공급자, 함수, 변수, 별칭 및 등을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="111e7-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="111e7-105">스냅인에는 cmdlet과 공급자만 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="111e7-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="111e7-106">모듈을 사용 하 여 cmdlet을 로드 하는 방법</span><span class="sxs-lookup"><span data-stu-id="111e7-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="111e7-107">Cmdlet 구현 되는 어셈블리 파일 이름이 같은 모듈 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="111e7-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="111e7-108">이 절차에서는 모듈 폴더에 만들어집니다는 `system32` 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="111e7-108">In this procedure, the module folder is created in the `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. <span data-ttu-id="111e7-109">했는지를 `PSModulePath` 환경 변수는 새 모듈 폴더에 경로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="111e7-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="111e7-110">기본적으로 시스템 폴더는 이미 추가 하 여 `PSModulePath` 환경 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="111e7-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span>

3. <span data-ttu-id="111e7-111">Cmdlet은 어셈블리 모듈 폴더에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="111e7-111">Copy the cmdlet assembly into the module folder.</span></span>

4. <span data-ttu-id="111e7-112">Cmdlet은 세션에 추가 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="111e7-112">Run the following command to add the cmdlets to the session:</span></span>

   `import-module [Module_Name]`

   <span data-ttu-id="111e7-113">Cmdlet을 테스트 하려면이 절차를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="111e7-113">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="111e7-114">세션에 어셈블리의 모든 cmdlet을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="111e7-114">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="111e7-115">모듈에 대 한 자세한 내용은 다양 한 유형의 모듈을 로드할 모듈 및 내보낸 된 모듈의 요소를 제한 하는 방법에 대 한 다양 한 방법 참조 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="111e7-115">For more information about modules, the different types of modules, the different ways to load modules, and how to restrict the elements of a module that are exported, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="111e7-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="111e7-116">See Also</span></span>

<span data-ttu-id="111e7-117">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="111e7-117">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="111e7-118">모듈 설치</span><span class="sxs-lookup"><span data-stu-id="111e7-118">Installing Modules</span></span>](../module/installing-a-powershell-module.md)
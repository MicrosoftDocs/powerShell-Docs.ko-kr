---
title: 업데이트 가능한 도움말 CAB 파일 이름을 지정하는 방법
ms.date: 09/12/2016
ms.openlocfilehash: 42486461d92f1f6fcff452a4539edf5be7a66f22
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893002"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="f566d-102">업데이트 가능한 도움말 CAB 파일 이름을 지정하는 방법</span><span class="sxs-lookup"><span data-stu-id="f566d-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="f566d-103">이 항목에서는 업데이트할 수 있는 도움말 캐비닛 () 파일의 필수 이름 형식에 대해 설명 합니다 `.CAB` .</span><span class="sxs-lookup"><span data-stu-id="f566d-103">This topic explains the required name format for the Updatable Help cabinet (`.CAB`) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="f566d-104">업데이트 가능한 도움말 CAB 파일 이름을 지정하는 방법</span><span class="sxs-lookup"><span data-stu-id="f566d-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="f566d-105">업데이트할 수 있는 캐비닛 ( `.CAB` ) 파일의 이름은 다음과 같은 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f566d-105">A Updatable cabinet (`.CAB`) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="f566d-106">이름의 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f566d-106">The elements of the name are as follows.</span></span>

- <span data-ttu-id="f566d-107">`<ModuleName>`- [Import-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet이 반환 하는 **Moduleinfo** 개체의 **Name** 속성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f566d-107">`<ModuleName>` -The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
- <span data-ttu-id="f566d-108">`<ModuleGUID>`-모듈 매니페스트의 **GUID** 키 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f566d-108">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>
- <span data-ttu-id="f566d-109">`<UICulture>`-CAB 파일에 있는 도움말 파일의 UI 문화권입니다.</span><span class="sxs-lookup"><span data-stu-id="f566d-109">`<UICulture>` - The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="f566d-110">이 값은 모듈에 대 한 HelpInfo XML 파일의 **UICulture** 요소 중 하나의 값과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f566d-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="f566d-111">예를 들어 모듈 이름이 "TestModule"이 고 모듈 GUID가 9cabb9ad-4914-a46b-bfc1bebf07f9이 고 UI 문화권이 "en-us" 이면 CAB 파일의 이름은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f566d-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`

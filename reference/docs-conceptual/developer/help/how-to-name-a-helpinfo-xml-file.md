---
title: HelpInfo XML 파일 이름을 지정하는 방법
ms.date: 09/12/2016
ms.openlocfilehash: 9505a7f66852a569d25ac0c1be86e68f870a7930
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892934"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="8919e-102">HelpInfo XML 파일 이름을 지정하는 방법</span><span class="sxs-lookup"><span data-stu-id="8919e-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="8919e-103">이 항목에서는 일반적으로 HelpInfo XML 파일 이라고 하는 업데이트할 수 있는 도움말 정보 파일의 필수 이름 형식에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8919e-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="8919e-104">HelpInfo XML 파일 이름을 지정하는 방법</span><span class="sxs-lookup"><span data-stu-id="8919e-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="8919e-105">HelpInfo XML 파일의 이름은 다음과 같은 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8919e-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="8919e-106">이름의 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8919e-106">The elements of the name are as follows.</span></span>

- <span data-ttu-id="8919e-107">`<ModuleName>`- [Import-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet이 반환 하는 **Moduleinfo** 개체의 **Name** 속성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="8919e-107">`<ModuleName>` - The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

- <span data-ttu-id="8919e-108">`<ModuleGUID>`-모듈 매니페스트의 **GUID** 키 값입니다.</span><span class="sxs-lookup"><span data-stu-id="8919e-108">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="8919e-109">예를 들어 모듈 이름이 "TestModule"이 고 모듈 GUID가 9cabb9ad-4914-a46b-bfc1bebf07f9 인 경우 모듈의 HelpInfo XML 파일 이름은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8919e-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`

---
title: 업데이트할 수 있는 도움말 CAB 파일 이름을 지정 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 23303489372cfe7e036fdea842ae75f7e47503c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861289"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="49ef8-102">업데이트 가능한 도움말 CAB 파일 이름을 지정하는 방법</span><span class="sxs-lookup"><span data-stu-id="49ef8-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="49ef8-103">이 항목에서는 필수 이름 형식을 업데이트할 수 있는 도움말 캐비닛에 대 한 설명 (합니다. CAB) 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="49ef8-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="49ef8-104">업데이트 가능한 도움말 CAB 파일 이름을 지정하는 방법</span><span class="sxs-lookup"><span data-stu-id="49ef8-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="49ef8-105">업데이트할 수 있는 캐비닛 (합니다. CAB) 파일에는 다음 형식으로 이름이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49ef8-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="49ef8-106">이름의 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="49ef8-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="49ef8-107">ModuleName 값의를 **이름** 의 속성을 **ModuleInfo** 개체를 [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet이 반환.</span><span class="sxs-lookup"><span data-stu-id="49ef8-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
<span data-ttu-id="49ef8-108">값을 **이름** 의 속성을 **ModuleInfo** 개체를 [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="49ef8-108">The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="49ef8-109">ModuleGUID 값의 합니다 **GUID** 모듈 매니페스트 키입니다.</span><span class="sxs-lookup"><span data-stu-id="49ef8-109">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="49ef8-110">CAB 파일에 있는 도움말 파일의 UICulture UI culture입니다.</span><span class="sxs-lookup"><span data-stu-id="49ef8-110">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="49ef8-111">이 값 중 하나의 값과 일치 해야 합니다 **UICulture** 모듈에 대 한 HelpInfo XML 파일의 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="49ef8-111">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="49ef8-112">예를 들어 모듈 이름을 "TestModule" 인 경우 모듈 GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, 하며 UI 문화권이 "EN-US", CAB 파일의 이름이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="49ef8-112">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
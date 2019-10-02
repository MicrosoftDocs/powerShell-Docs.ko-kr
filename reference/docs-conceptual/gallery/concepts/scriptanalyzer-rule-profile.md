---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 갤러리에 대한 ScriptAnazlyer 규칙 프로필
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328474"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="92a5b-103">갤러리에 대한 ScriptAnazlyer 규칙 프로필</span><span class="sxs-lookup"><span data-stu-id="92a5b-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="92a5b-104">PowerShell 갤러리에 게시된 패키지의 품질을 보장하기 위해 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) 규칙을 실행하여 제출된 스크립트에 위반 사항이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92a5b-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="92a5b-105">ScriptAnalyzer [GitHub 페이지](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1)에서 실행하는 규칙의 목록을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92a5b-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="92a5b-106">실행하는 규칙과 관련해서 질문이 있는 경우 PowerShell 갤러리 관리자에게 문의하거나 ScriptAnalyzer에 대한 문제를 개설하세요.</span><span class="sxs-lookup"><span data-stu-id="92a5b-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="92a5b-107">ScriptAnalyzer 결과는 향후 릴리스의 갤러리에 포함된 각 개별 패키지 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92a5b-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="92a5b-108">패키지 소유자는 해당 패키지를 확인하여 게시된 패키지에 심각한 오류가 없는지 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="92a5b-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>

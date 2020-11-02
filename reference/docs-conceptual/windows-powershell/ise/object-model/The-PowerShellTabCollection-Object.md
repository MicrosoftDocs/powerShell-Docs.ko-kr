---
ms.date: 06/05/2017
title: PowerShellTabCollection 개체
description: PowerShellTab 컬렉션 개체는 PowerShellTab 개체의 컬렉션입니다. 각 PowerShellTab 개체는 별도의 런타임 환경으로 작동합니다.
ms.openlocfilehash: 60f8001f096b50bd8433a5685f1f70a350f07f61
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658270"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="42166-104">PowerShellTabCollection 개체</span><span class="sxs-lookup"><span data-stu-id="42166-104">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="42166-105">**PowerShellTab** 컬렉션 개체는 **PowerShellTab** 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="42166-105">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="42166-106">각 **PowerShellTab** 개체는 별도의 런타임 환경으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="42166-106">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="42166-107">Microsoft.PowerShell.Host.ISE.PowerShellTabs 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="42166-107">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="42166-108">`$psISE.PowerShellTabs` 개체를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42166-108">An example is the `$psISE.PowerShellTabs` object.</span></span>

## <a name="methods"></a><span data-ttu-id="42166-109">메서드</span><span class="sxs-lookup"><span data-stu-id="42166-109">Methods</span></span>

### <a name="add"></a><span data-ttu-id="42166-110">추가\(\)</span><span class="sxs-lookup"><span data-stu-id="42166-110">Add\(\)</span></span>

<span data-ttu-id="42166-111">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="42166-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="42166-112">새 PowerShell 탭을 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="42166-112">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="42166-113">새로 추가된 탭을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="42166-113">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="42166-114">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="42166-114">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="42166-115">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="42166-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="42166-116">**psTab** 매개 변수로 지정되는 탭을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="42166-116">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="42166-117">**psTab** 제거할 PowerShell 탭입니다.</span><span class="sxs-lookup"><span data-stu-id="42166-117">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="42166-118">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="42166-118">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="42166-119">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="42166-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="42166-120">**psTab** 매개 변수에서 지정하는 PowerShell 탭을 선택하여 현재 사용 중인 PowerShell 탭으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="42166-120">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="42166-121">**psTab** 선택할 PowerShell 탭입니다.</span><span class="sxs-lookup"><span data-stu-id="42166-121">**psTab** The PowerShell tab to select.</span></span>

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a><span data-ttu-id="42166-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42166-122">See Also</span></span>

- [<span data-ttu-id="42166-123">PowerShellTab 개체</span><span class="sxs-lookup"><span data-stu-id="42166-123">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="42166-124">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="42166-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="42166-125">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="42166-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

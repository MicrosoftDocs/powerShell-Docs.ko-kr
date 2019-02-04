---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShellTabCollection 개체
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682918"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="4fc35-103">PowerShellTabCollection 개체</span><span class="sxs-lookup"><span data-stu-id="4fc35-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="4fc35-104">**PowerShellTab** 컬렉션 개체는 **PowerShellTab** 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="4fc35-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="4fc35-105">각 **PowerShellTab** 개체는 별도의 런타임 환경으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc35-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="4fc35-106">Microsoft.PowerShell.Host.ISE.PowerShellTabs 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="4fc35-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="4fc35-107">예제는 **$psISE.PowerShellTabs** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="4fc35-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="4fc35-108">메서드</span><span class="sxs-lookup"><span data-stu-id="4fc35-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="4fc35-109">추가\(\)</span><span class="sxs-lookup"><span data-stu-id="4fc35-109">Add\(\)</span></span>

<span data-ttu-id="4fc35-110">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fc35-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4fc35-111">새 PowerShell 탭을 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc35-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="4fc35-112">새로 추가된 탭을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc35-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="4fc35-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="4fc35-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="4fc35-114">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fc35-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4fc35-115">**psTab** 매개 변수로 지정되는 탭을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc35-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="4fc35-116">**psTab** 제거할 PowerShell 탭입니다.</span><span class="sxs-lookup"><span data-stu-id="4fc35-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="4fc35-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="4fc35-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="4fc35-118">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fc35-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4fc35-119">**psTab** 매개 변수에서 지정하는 PowerShell 탭을 선택하여 현재 사용 중인 PowerShell 탭으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4fc35-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="4fc35-120">**psTab** 선택할 PowerShell 탭입니다.</span><span class="sxs-lookup"><span data-stu-id="4fc35-120">**psTab** The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4fc35-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4fc35-121">See Also</span></span>

- [<span data-ttu-id="4fc35-122">PowerShellTab 개체</span><span class="sxs-lookup"><span data-stu-id="4fc35-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="4fc35-123">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="4fc35-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="4fc35-124">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="4fc35-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
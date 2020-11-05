---
ms.date: 12/31/2019
title: ISEMenuItemCollection 개체
description: ISEMenuItemCollection 개체는 ISEMenuItem 개체의 컬렉션이며,
ms.openlocfilehash: cd86768d13b1326a8f35c44f0391ab60669cee4f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655999"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="fae26-103">ISEMenuItemCollection 개체</span><span class="sxs-lookup"><span data-stu-id="fae26-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="fae26-104">**ISEMenuItemCollection** 개체는 **ISEMenuItem** 개체의 컬렉션이며,</span><span class="sxs-lookup"><span data-stu-id="fae26-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="fae26-105">**Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="fae26-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection** class.</span></span> <span data-ttu-id="fae26-106">한 가지 예는 Windows PowerShell&reg; 통합 스크립팅 환경(ISE)에서 **추가 항목** 메뉴를 사용자 지정하는 데 사용되는 `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus` 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="fae26-106">An example is the `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus` object that is used to customize the **Add-On** menu in Windows PowerShell&reg; Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="fae26-107">방법</span><span class="sxs-lookup"><span data-stu-id="fae26-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="fae26-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span><span class="sxs-lookup"><span data-stu-id="fae26-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="fae26-109">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="fae26-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="fae26-110">메뉴 항목을 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fae26-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="fae26-111">**DisplayName** 추가할 메뉴의 표시 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fae26-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="fae26-112">**Action** 이 메뉴 항목과 연결되는 동작을 지정하는 **System.Management.Automation.ScriptBlock** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="fae26-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="fae26-113">**Shortcut** 작업에 대한 바로 가기 키입니다.</span><span class="sxs-lookup"><span data-stu-id="fae26-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="fae26-114">**Returns** 방금 추가된 **ISEMenuItem** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="fae26-114">**Returns** The **ISEMenuItem** object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="fae26-115">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="fae26-115">Clear\(\)</span></span>

<span data-ttu-id="fae26-116">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="fae26-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="fae26-117">메뉴 항목에서 모든 하위 메뉴를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="fae26-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="fae26-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fae26-118">See Also</span></span>

- [<span data-ttu-id="fae26-119">ISEMenuItem 개체</span><span class="sxs-lookup"><span data-stu-id="fae26-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="fae26-120">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="fae26-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="fae26-121">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="fae26-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

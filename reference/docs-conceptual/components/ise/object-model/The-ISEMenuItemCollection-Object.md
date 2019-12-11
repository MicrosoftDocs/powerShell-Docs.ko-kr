---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISEMenuItemCollection 개체
ms.openlocfilehash: b3795af1a6ed61ed6e371e5fc20cc4e95f643fd4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030531"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="5cd53-103">ISEMenuItemCollection 개체</span><span class="sxs-lookup"><span data-stu-id="5cd53-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="5cd53-104">**ISEMenuItemCollection** 개체는 **ISEMenuItem** 개체의 컬렉션이며,</span><span class="sxs-lookup"><span data-stu-id="5cd53-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="5cd53-105">Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd53-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="5cd53-106">예제는 Windows PowerShell® ISE(통합 스크립팅 환경)에서 **추가 기능** 메뉴를 사용자 지정하는 데 사용되는 **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd53-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="5cd53-107">방법</span><span class="sxs-lookup"><span data-stu-id="5cd53-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="5cd53-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span><span class="sxs-lookup"><span data-stu-id="5cd53-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="5cd53-109">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd53-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="5cd53-110">메뉴 항목을 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd53-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="5cd53-111">**DisplayName** 추가할 메뉴의 표시 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd53-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="5cd53-112">**Action** 이 메뉴 항목과 연결되는 동작을 지정하는 **System.Management.Automation.ScriptBlock** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd53-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="5cd53-113">**Shortcut** 작업에 대한 바로 가기 키입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd53-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="5cd53-114">**Returns** 방금 추가된 ISEMenuItem 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd53-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="5cd53-115">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="5cd53-115">Clear\(\)</span></span>

<span data-ttu-id="5cd53-116">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd53-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="5cd53-117">메뉴 항목에서 모든 하위 메뉴를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd53-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="5cd53-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5cd53-118">See Also</span></span>

- [<span data-ttu-id="5cd53-119">ISEMenuItem 개체</span><span class="sxs-lookup"><span data-stu-id="5cd53-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="5cd53-120">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="5cd53-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="5cd53-121">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="5cd53-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

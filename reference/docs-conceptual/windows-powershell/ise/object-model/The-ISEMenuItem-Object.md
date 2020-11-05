---
ms.date: 12/31/2019
title: ISEMenuItem 개체
description: ISEMenuItem 개체는 Microsoft.PowerShell.Host.ISE.ISEMenuItem 클래스의 인스턴스입니다. **추가 항목** 메뉴의 모든 메뉴 개체는 ISEMenuItem 클래스의 인스턴스입니다.
ms.openlocfilehash: 15036e3551687a21dfbe50834a89247c80949656
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663435"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="79ea4-104">ISEMenuItem 개체</span><span class="sxs-lookup"><span data-stu-id="79ea4-104">The ISEMenuItem Object</span></span>

<span data-ttu-id="79ea4-105">**ISEMenuItem** 개체는 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="79ea4-105">An **ISEMenuItem** object is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>
<span data-ttu-id="79ea4-106">**추가 기능** 메뉴의 모든 메뉴 개체는 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="79ea4-106">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="79ea4-107">속성</span><span class="sxs-lookup"><span data-stu-id="79ea4-107">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="79ea4-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="79ea4-108">DisplayName</span></span>

<span data-ttu-id="79ea4-109">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="79ea4-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79ea4-110">메뉴 항목의 표시 이름을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="79ea4-110">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="79ea4-111">작업</span><span class="sxs-lookup"><span data-stu-id="79ea4-111">Action</span></span>

<span data-ttu-id="79ea4-112">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="79ea4-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79ea4-113">스크립트 블록을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="79ea4-113">The read-only property that gets the block of script.</span></span> <span data-ttu-id="79ea4-114">메뉴 항목을 클릭하면 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="79ea4-114">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="79ea4-115">바로 가기</span><span class="sxs-lookup"><span data-stu-id="79ea4-115">Shortcut</span></span>

<span data-ttu-id="79ea4-116">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="79ea4-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79ea4-117">메뉴 항목에 대한 Windows 입력 바로 가기 키를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="79ea4-117">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="79ea4-118">하위 메뉴</span><span class="sxs-lookup"><span data-stu-id="79ea4-118">Submenus</span></span>

<span data-ttu-id="79ea4-119">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="79ea4-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79ea4-120">메뉴 항목의 [하위 메뉴 목록](The-ISEMenuItemCollection-Object.md)을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="79ea4-120">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="79ea4-121">스크립팅 예제</span><span class="sxs-lookup"><span data-stu-id="79ea4-121">Scripting example</span></span>

<span data-ttu-id="79ea4-122">추가 기능 메뉴와 스크립트 가능한 해당 속성의 사용에 대해 보다 잘 이해하려면 다음 스크립팅 예제를 자세히 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="79ea4-122">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a><span data-ttu-id="79ea4-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79ea4-123">See Also</span></span>

- [<span data-ttu-id="79ea4-124">ISEMenuItemCollection 개체</span><span class="sxs-lookup"><span data-stu-id="79ea4-124">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="79ea4-125">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="79ea4-125">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="79ea4-126">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="79ea4-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

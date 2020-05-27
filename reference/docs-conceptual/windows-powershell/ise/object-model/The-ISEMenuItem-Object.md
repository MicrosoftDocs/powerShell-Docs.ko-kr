---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEMenuItem 개체
ms.openlocfilehash: c3ffe6e8f0b28987543fe0a873c552292dc5158a
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809319"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="22648-103">ISEMenuItem 개체</span><span class="sxs-lookup"><span data-stu-id="22648-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="22648-104">**ISEMenuItem** 개체는 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="22648-104">An **ISEMenuItem** object is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>
<span data-ttu-id="22648-105">**추가 기능** 메뉴의 모든 메뉴 개체는 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="22648-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="22648-106">속성</span><span class="sxs-lookup"><span data-stu-id="22648-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="22648-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="22648-107">DisplayName</span></span>

<span data-ttu-id="22648-108">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="22648-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="22648-109">메뉴 항목의 표시 이름을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="22648-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="22648-110">작업</span><span class="sxs-lookup"><span data-stu-id="22648-110">Action</span></span>

<span data-ttu-id="22648-111">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="22648-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="22648-112">스크립트 블록을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="22648-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="22648-113">메뉴 항목을 클릭하면 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="22648-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="22648-114">바로 가기</span><span class="sxs-lookup"><span data-stu-id="22648-114">Shortcut</span></span>

<span data-ttu-id="22648-115">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="22648-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="22648-116">메뉴 항목에 대한 Windows 입력 바로 가기 키를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="22648-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="22648-117">하위 메뉴</span><span class="sxs-lookup"><span data-stu-id="22648-117">Submenus</span></span>

<span data-ttu-id="22648-118">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="22648-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="22648-119">메뉴 항목의 [하위 메뉴 목록](The-ISEMenuItemCollection-Object.md)을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="22648-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="22648-120">스크립팅 예제</span><span class="sxs-lookup"><span data-stu-id="22648-120">Scripting example</span></span>

<span data-ttu-id="22648-121">추가 기능 메뉴와 스크립트 가능한 해당 속성의 사용에 대해 보다 잘 이해하려면 다음 스크립팅 예제를 자세히 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="22648-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a><span data-ttu-id="22648-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="22648-122">See Also</span></span>

- [<span data-ttu-id="22648-123">ISEMenuItemCollection 개체</span><span class="sxs-lookup"><span data-stu-id="22648-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="22648-124">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="22648-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="22648-125">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="22648-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

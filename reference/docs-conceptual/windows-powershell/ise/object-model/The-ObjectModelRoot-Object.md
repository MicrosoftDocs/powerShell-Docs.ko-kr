---
ms.date: 08/25/2017
keywords: powershell,cmdlet
title: ObjectModelRoot 개체
ms.openlocfilehash: cd94e69de2e62f7ce9fac413e15458ae9986540e
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809569"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="07381-103">ObjectModelRoot 개체</span><span class="sxs-lookup"><span data-stu-id="07381-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="07381-104">Windows PowerShell® ISE(통합 스크립팅 환경)의 주 루트 개체인 `$psISE` 개체는 Microsoft.PowerShell.Host.ISE.ObjectModelRoot 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="07381-104">The `$psISE` object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span> <span data-ttu-id="07381-105">이 항목에서는 **ObjectModelRoot** 개체의 속성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="07381-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="07381-106">속성</span><span class="sxs-lookup"><span data-stu-id="07381-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="07381-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="07381-107">CurrentFile</span></span>

> <span data-ttu-id="07381-108">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="07381-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="07381-109">현재 포커스가 있는 이 호스트 개체와 연결된 파일을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="07381-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="07381-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="07381-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="07381-111">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="07381-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="07381-112">포커스가 있는 PowerShell 탭을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="07381-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="07381-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="07381-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="07381-114">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="07381-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="07381-115">편집기의 맨 아래에 있는 수평 도구 창에 위치한 현재 표시되는 Windows PowerShell ISE 추가 기능 도구를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="07381-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="07381-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="07381-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="07381-117">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="07381-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="07381-118">편집기의 오른쪽에 있는 수직 도구 창에 위치한 현재 표시되는 Windows PowerShell ISE 추가 기능 도구를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="07381-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="07381-119">옵션</span><span class="sxs-lookup"><span data-stu-id="07381-119">Options</span></span>

> <span data-ttu-id="07381-120">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="07381-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="07381-121">Windows PowerShell ISE에서 설정을 변경할 수 있는 다양한 옵션을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="07381-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="07381-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="07381-122">PowerShellTabs</span></span>

> <span data-ttu-id="07381-123">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="07381-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="07381-124">Windows PowerShell ISE에서 열려 있는 PowerShell 탭의 컬렉션을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="07381-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="07381-125">기본적으로 이 개체는 하나의 PowerShell 탭을 포함합니다. 그러나 스크립트를 사용하거나 Windows PowerShell ISE의 메뉴를 사용하여 이 개체에 더 많은 PowerShell 탭을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07381-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="07381-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07381-126">See Also</span></span>

- [<span data-ttu-id="07381-127">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="07381-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="07381-128">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="07381-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

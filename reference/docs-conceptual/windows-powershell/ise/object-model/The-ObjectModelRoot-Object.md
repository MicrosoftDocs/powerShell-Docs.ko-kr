---
ms.date: 08/25/2017
title: ObjectModelRoot 개체
description: PowerShell ISE의 주 루트 개체인 $psISE 개체는 Microsoft.PowerShell.Host.ISE.ObjectModelRoot 클래스의 인스턴스입니다. 이 항목에서는 ObjectModelRoot 개체의 속성을 설명합니다.
ms.openlocfilehash: c8ae703c2663256ca037090fd3b1eb239cfc431a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660948"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="199a2-104">ObjectModelRoot 개체</span><span class="sxs-lookup"><span data-stu-id="199a2-104">The ObjectModelRoot Object</span></span>

<span data-ttu-id="199a2-105">Windows PowerShell&reg; 통합 스크립팅 환경(ISE)의 주 루트 개체인 `$psISE` 개체는 Microsoft.PowerShell.Host.ISE.ObjectModelRoot 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-105">The `$psISE` object, which is the principal root object in Windows PowerShell&reg; Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span> <span data-ttu-id="199a2-106">이 항목에서는 **ObjectModelRoot** 개체의 속성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-106">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="199a2-107">속성</span><span class="sxs-lookup"><span data-stu-id="199a2-107">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="199a2-108">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="199a2-108">CurrentFile</span></span>

> <span data-ttu-id="199a2-109">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="199a2-110">현재 포커스가 있는 이 호스트 개체와 연결된 파일을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-110">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="199a2-111">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="199a2-111">CurrentPowerShellTab</span></span>

> <span data-ttu-id="199a2-112">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="199a2-113">포커스가 있는 PowerShell 탭을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-113">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="199a2-114">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="199a2-114">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="199a2-115">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="199a2-116">편집기의 맨 아래에 있는 수평 도구 창에 위치한 현재 표시되는 Windows PowerShell ISE 추가 기능 도구를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-116">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="199a2-117">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="199a2-117">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="199a2-118">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="199a2-119">편집기의 오른쪽에 있는 수직 도구 창에 위치한 현재 표시되는 Windows PowerShell ISE 추가 기능 도구를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-119">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="199a2-120">옵션</span><span class="sxs-lookup"><span data-stu-id="199a2-120">Options</span></span>

> <span data-ttu-id="199a2-121">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="199a2-122">Windows PowerShell ISE에서 설정을 변경할 수 있는 다양한 옵션을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-122">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="199a2-123">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="199a2-123">PowerShellTabs</span></span>

> <span data-ttu-id="199a2-124">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-124">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="199a2-125">Windows PowerShell ISE에서 열려 있는 PowerShell 탭의 컬렉션을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-125">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="199a2-126">기본적으로 이 개체는 하나의 PowerShell 탭을 포함합니다. 그러나 스크립트를 사용하거나 Windows PowerShell ISE의 메뉴를 사용하여 이 개체에 더 많은 PowerShell 탭을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="199a2-126">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="199a2-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="199a2-127">See Also</span></span>

- [<span data-ttu-id="199a2-128">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="199a2-128">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="199a2-129">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="199a2-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

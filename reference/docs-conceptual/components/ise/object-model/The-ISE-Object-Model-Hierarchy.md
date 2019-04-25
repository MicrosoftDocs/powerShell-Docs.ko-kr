---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISE 개체 모델 계층 구조
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057726"
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="7fdf9-103">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="7fdf9-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="7fdf9-104">이 항목에서는 Windows PowerShell ISE(통합 스크립팅 환경)에 속하는 개체의 계층 구조를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
<span data-ttu-id="7fdf9-105">Windows PowerShell ISE는 Windows PowerShell 3.0 및 Windows PowerShell 4.0에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span>
<span data-ttu-id="7fdf9-106">개체를 클릭하여 개체를 정의하는 클래스에 대한 참조 설명서로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="7fdf9-107">$psISE 개체</span><span class="sxs-lookup"><span data-stu-id="7fdf9-107">$psISE Object</span></span>

<span data-ttu-id="7fdf9-108">**$psISE** 개체는 Windows PowerShell ISE 개체 계층 구조의 [루트 개체](The-ObjectModelRoot-Object.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="7fdf9-109">최상위 수준에 있는 이 개체를 사용하면 스크립팅에 다음 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="7fdf9-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="7fdf9-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="7fdf9-111">**$psISE.CurrentFile** 개체는 [ISEFile](The-ISEFile-Object.md) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="7fdf9-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="7fdf9-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="7fdf9-113">**$psISE.CurrentPowerShellTab** 개체는 [PowerShellTab](The-PowerShellTab-Object.md) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="7fdf9-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="7fdf9-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="7fdf9-115">**$psISE.CurrentVisibleHorizontalTool** 개체는 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="7fdf9-116">현재 Windows PowerShell ISE 창의 위쪽 가장자리에 도킹되어 있는 설치된 추가 기능 도구를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="7fdf9-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="7fdf9-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="7fdf9-118">**$psISE.CurrentVisibleHorizontalTool** 개체는 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="7fdf9-119">현재 Windows PowerShell ISE 창의 오른쪽 가장자리에 도킹되어 있는 설치된 추가 기능 도구를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="7fdf9-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="7fdf9-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="7fdf9-121">**$psISE.Options** 개체는 [ISEOptions](The-ISEOptions-Object.md) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="7fdf9-122">ISEOptions 개체는 Windows PowerShell ISE에 대한 다양한 설정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="7fdf9-123">Microsoft.PowerShell.Host.ISE.ISEOptions 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="7fdf9-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="7fdf9-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="7fdf9-125">**$psISE.PowerShellTabs** 개체는 [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="7fdf9-126">로컬 컴퓨터 또는 연결된 원격 컴퓨터에서 사용 가능한 Windows PowerShell 실행 환경을 나타내는 현재 열려 있는 모든 PowerShell 탭의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span>
<span data-ttu-id="7fdf9-127">컬렉션의 각 멤버는 [PowerShellTab](The-PowerShellTab-Object.md) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="7fdf9-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7fdf9-128">See Also</span></span>

- [<span data-ttu-id="7fdf9-129">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="7fdf9-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="7fdf9-130">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="7fdf9-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
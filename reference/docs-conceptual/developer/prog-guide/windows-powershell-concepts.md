---
title: Windows PowerShell 개념 | Microsoft Docs
ms.custom: ''
ms.date: 6/12/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: 4410b1f9c80afefd5479fa68154f9947b805edcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366682"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="59741-102">Windows PowerShell 개념</span><span class="sxs-lookup"><span data-stu-id="59741-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="59741-103">이 섹션에는 개발자의 관점에서 PowerShell을 이해 하는 데 도움이 되는 개념 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59741-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="59741-104">토픽 이름</span><span class="sxs-lookup"><span data-stu-id="59741-104">Topic Name</span></span>|<span data-ttu-id="59741-105">설명</span><span class="sxs-lookup"><span data-stu-id="59741-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="59741-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="59741-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="59741-107">PowerShell 개체에 대 한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="59741-107">Description of PowerShell objects.</span></span> <span data-ttu-id="59741-108">자세한 내용은 [개체 만들기 정보](/powershell/module/microsoft.powershell.core/about/about_object_creation) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="59741-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="59741-109">Runspace 만들기</span><span class="sxs-lookup"><span data-stu-id="59741-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="59741-110">명령이 처리 되는 운영 환경</span><span class="sxs-lookup"><span data-stu-id="59741-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="59741-111">자세한 내용은 [Runspace 클래스](/dotnet/api/system.management.automation.runspaces.runspace)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="59741-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="59741-112">출력 개체 확장</span><span class="sxs-lookup"><span data-stu-id="59741-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="59741-113">PowerShell 개체를 확장 하는 방법</span><span class="sxs-lookup"><span data-stu-id="59741-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="59741-114">자세한 내용은 [형식 정보. types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="59741-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="59741-115">Cmdlet 등록</span><span class="sxs-lookup"><span data-stu-id="59741-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="59741-116">PowerShell에서 모듈 및 스냅인을 사용 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="59741-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="59741-117">자세한 내용은 [모듈 및 스냅인](../cmdlet/modules-and-snap-ins.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="59741-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="59741-118">Cmdlet에서 확인 요청</span><span class="sxs-lookup"><span data-stu-id="59741-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="59741-119">작업을 수행 하기 전에 cmdlet 및 공급자가 사용자의 피드백을 요청 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="59741-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="59741-120">RuntimeDefinedParameter 클래스</span><span class="sxs-lookup"><span data-stu-id="59741-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="59741-121">런타임 매개 변수 선언입니다.</span><span class="sxs-lookup"><span data-stu-id="59741-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="59741-122">System.web. Automation 네임 스페이스</span><span class="sxs-lookup"><span data-stu-id="59741-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="59741-123">PowerShell API 네임 스페이스 개요.</span><span class="sxs-lookup"><span data-stu-id="59741-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="59741-124">Windows PowerShell 공급자 개요</span><span class="sxs-lookup"><span data-stu-id="59741-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="59741-125">데이터 저장소에 액세스 하는 데 사용 되는 PowerShell 공급자에 대 한 개요입니다.</span><span class="sxs-lookup"><span data-stu-id="59741-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="59741-126">PowerShell Cmdlet에 대 한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="59741-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="59741-127">PowerShell cmdlet 도움말을 작성 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="59741-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="59741-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59741-128">See also</span></span>

[<span data-ttu-id="59741-129">PowerShell 클래스</span><span class="sxs-lookup"><span data-stu-id="59741-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="59741-130">PowerShell Core API 참조</span><span class="sxs-lookup"><span data-stu-id="59741-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="59741-131">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="59741-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="59741-132">Windows PowerShell 모듈에 대 한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="59741-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="59741-133">Windows Powershell 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="59741-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="59741-134">Windows PowerShell API 참조</span><span class="sxs-lookup"><span data-stu-id="59741-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

[<span data-ttu-id="59741-135">Windows PowerShell 참조</span><span class="sxs-lookup"><span data-stu-id="59741-135">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)
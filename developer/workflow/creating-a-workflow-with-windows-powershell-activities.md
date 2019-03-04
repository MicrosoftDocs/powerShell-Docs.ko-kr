---
title: Windows PowerShell 작업을 사용 하 여 워크플로 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 65d04c526ef7aa112da82adb924c0789731f3850
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853469"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="6d90c-102">Windows PowerShell 활동을 사용하여 워크플로 만들기</span><span class="sxs-lookup"><span data-stu-id="6d90c-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="6d90c-103">Visual Studio 도구 상자에서 활동을 선택 하 고 워크플로 디자이너 창으로 끌어와 Windows PowerShell 워크플로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="6d90c-104">Visual Studio 도구 상자에 Windows PowerShell 활동 추가 대 한 자세한 내용은 [Visual Studio 도구 상자에 Windows PowerShell 활동 추가](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="6d90c-105">다음 절차에는 사용자 지정 컴퓨터 그룹의 도메인 상태를 확인, 이미 가입 되지 않으며 다음 상태를 다시 확인 하는 경우 도메인에 조인 하는 워크플로 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="6d90c-106">프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="6d90c-106">Setting up the Project</span></span>

1. <span data-ttu-id="6d90c-107">절차에 따라 [Visual Studio 도구 상자에 Windows PowerShell 작업 추가](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) 워크플로 프로젝트 만들기의 활동을 추가 하는 [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) 하고[ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) 도구 상자에는 어셈블리입니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="6d90c-108">참조 어셈블리와 프로젝트에 대 한 System.Management.Automation "," Microsoft.PowerShell.Activities "," System.Management "," Microsoft.PowerShell.Management.Activities, "및" Microsoft.PowerShell.Commands.Management를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="6d90c-109">워크플로에 활동을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="6d90c-110">추가 된 **시퀀스** 활동을 워크플로.</span><span class="sxs-lookup"><span data-stu-id="6d90c-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="6d90c-111">명명 된 인수를 만듭니다 `ComputerName` 인수 유형으로 `String[]`입니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="6d90c-112">이 인수를 확인 하 고 조인 컴퓨터의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="6d90c-113">명명 된 인수를 만듭니다 `DomainCred` 형식의 [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)합니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-113">Create an argument named `DomainCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="6d90c-114">이 인수는 도메인에 컴퓨터를 가입 시킬 권한이 있는 도메인 계정의 도메인 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="6d90c-115">명명 된 인수를 만듭니다 `MachineCred` 형식의 [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)합니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-115">Create an argument named `MachineCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="6d90c-116">이 인수를 확인 하 고 조인 컴퓨터의 관리자의 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="6d90c-117">추가 **ParallelForEach** 내 활동의 **시퀀스** 활동입니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="6d90c-118">입력 `comp` 하 고 `ComputerName` 에서 루프의 요소를 반복 하는 입력란을 `ComputerName` 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="6d90c-119">추가 **시퀀스** 활동의 본문에는 **ParallelForEach** 활동입니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="6d90c-120">설정 된 **DisplayName** 시퀀스의 속성 `JoinDomain`합니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="6d90c-121">추가 **GetWmiObject** 작업을 합니다 **JoinDomain** 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="6d90c-122">속성을 편집 합니다 **GetWmiObject** 같이 작업 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="6d90c-123">속성</span><span class="sxs-lookup"><span data-stu-id="6d90c-123">Property</span></span>|<span data-ttu-id="6d90c-124">Value</span><span class="sxs-lookup"><span data-stu-id="6d90c-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="6d90c-125">**클래스**</span><span class="sxs-lookup"><span data-stu-id="6d90c-125">**Class**</span></span>|<span data-ttu-id="6d90c-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="6d90c-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="6d90c-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="6d90c-127">**PSComputerName**</span></span>|<span data-ttu-id="6d90c-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="6d90c-128">{comp}</span></span>|
   |<span data-ttu-id="6d90c-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="6d90c-129">**PSCredential**</span></span>|<span data-ttu-id="6d90c-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="6d90c-130">MachineCred</span></span>|

9. <span data-ttu-id="6d90c-131">추가 **AddComputer** 작업을 합니다 **JoinDomain** 후 시퀀스를 **GetWmiObject** 활동입니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="6d90c-132">속성을 편집 합니다 **AddComputer** 같이 작업 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="6d90c-133">속성</span><span class="sxs-lookup"><span data-stu-id="6d90c-133">Property</span></span>|<span data-ttu-id="6d90c-134">Value</span><span class="sxs-lookup"><span data-stu-id="6d90c-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="6d90c-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="6d90c-135">**ComputerName**</span></span>|<span data-ttu-id="6d90c-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="6d90c-136">{comp}</span></span>|
    |<span data-ttu-id="6d90c-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="6d90c-137">**DomainCredential**</span></span>|<span data-ttu-id="6d90c-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="6d90c-138">DomainCred</span></span>|

11. <span data-ttu-id="6d90c-139">추가 **RestartComputer** 작업을 합니다 **JoinDomain** 후 시퀀스를 **AddComputer** 활동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="6d90c-140">속성을 편집 합니다 **RestartComputer** 같이 작업 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="6d90c-141">속성</span><span class="sxs-lookup"><span data-stu-id="6d90c-141">Property</span></span>|<span data-ttu-id="6d90c-142">Value</span><span class="sxs-lookup"><span data-stu-id="6d90c-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="6d90c-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="6d90c-143">**ComputerName**</span></span>|<span data-ttu-id="6d90c-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="6d90c-144">{comp}</span></span>|
    |<span data-ttu-id="6d90c-145">**자격 증명**</span><span class="sxs-lookup"><span data-stu-id="6d90c-145">**Credential**</span></span>|<span data-ttu-id="6d90c-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="6d90c-146">MachineCred</span></span>|
    |<span data-ttu-id="6d90c-147">**에 대 한**</span><span class="sxs-lookup"><span data-stu-id="6d90c-147">**For**</span></span>|<span data-ttu-id="6d90c-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="6d90c-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="6d90c-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="6d90c-149">**Force**</span></span>|<span data-ttu-id="6d90c-150">True</span><span class="sxs-lookup"><span data-stu-id="6d90c-150">True</span></span>|
    |<span data-ttu-id="6d90c-151">연결 시도 간격</span><span class="sxs-lookup"><span data-stu-id="6d90c-151">Wait</span></span>|<span data-ttu-id="6d90c-152">True</span><span class="sxs-lookup"><span data-stu-id="6d90c-152">True</span></span>|
    |<span data-ttu-id="6d90c-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="6d90c-153">PSComputerName</span></span>|<span data-ttu-id="6d90c-154">{""}</span><span class="sxs-lookup"><span data-stu-id="6d90c-154">{""}</span></span>|

13. <span data-ttu-id="6d90c-155">추가 **GetWmiObject** 작업을 합니다 **JoinDomain** 후 시퀀스를 **RestartComputer** 활동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="6d90c-156">이전으로 동일 하도록 해당 속성을 편집할 **GetWmiObject** 활동입니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="6d90c-157">절차를 완료 한 후 워크플로 디자인 창 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d90c-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="6d90c-158">![Workflow designer의 JoinDomain XAML](../media/joindomainworkflow.png)
    ![Workflow designer의 JoinDomain XAML](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="6d90c-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>
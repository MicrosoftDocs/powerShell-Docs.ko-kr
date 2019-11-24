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
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359632"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="89fad-102">Windows PowerShell 활동을 사용하여 워크플로 만들기</span><span class="sxs-lookup"><span data-stu-id="89fad-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="89fad-103">Visual Studio 도구 상자에서 작업을 선택 하 고 워크플로 디자이너 창으로 끌어 Windows PowerShell 워크플로를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="89fad-104">Visual Studio 도구 상자에 Windows PowerShell 활동을 추가 하는 방법에 대 한 자세한 내용은 [Visual Studio 도구 상자에 Windows Powershell 활동 추가](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="89fad-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="89fad-105">다음 절차에서는 사용자 지정 컴퓨터 그룹의 도메인 상태를 확인 하 고 도메인에 가입 되어 있지 않은 경우이를 도메인에 조인 하는 워크플로를 만들고 상태를 다시 확인 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="89fad-106">프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="89fad-106">Setting up the Project</span></span>

1. <span data-ttu-id="89fad-107">[Visual Studio 도구 상자에 Windows PowerShell 활동 추가](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) 의 절차에 따라 워크플로 프로젝트를 만들고 [microsoft. powershell](/dotnet/api/Microsoft.PowerShell.Activities) 및 [microsoft.](/dotnet/api/Microsoft.PowerShell.Management.Activities) . s s e.</span><span class="sxs-lookup"><span data-stu-id="89fad-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="89fad-108">프로젝트에 참조 어셈블리로 서 management. Automation, Microsoft. management, microsoft. management, 및 Microsoft. c r e a t. n e t. n e t. Management를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="89fad-109">워크플로에 활동 추가</span><span class="sxs-lookup"><span data-stu-id="89fad-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="89fad-110">워크플로에 **시퀀스** 활동을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="89fad-111">인수 형식이 `String[]`인 `ComputerName` 이라는 인수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="89fad-112">이 인수는 확인 및 가입할 컴퓨터의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="89fad-113">[System.object](/dotnet/api/System.Management.Automation.PSCredential)형식의 `DomainCred` 이라는 인수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="89fad-114">이 인수는 도메인에 컴퓨터를 가입 시킬 수 있는 도메인 계정의 도메인 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="89fad-115">[System.object](/dotnet/api/System.Management.Automation.PSCredential)형식의 `MachineCred` 이라는 인수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="89fad-116">이 인수는 확인 및 가입할 컴퓨터의 관리자 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="89fad-117">**Sequence** 활동 내에 **ParallelForEach** 활동을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="89fad-118">루프에서 `ComputerName` 배열의 요소를 반복 하도록 텍스트 상자에 `comp` 및 `ComputerName`을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="89fad-119">**ParallelForEach** 활동의 본문에 **시퀀스** 활동을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="89fad-120">시퀀스의 **DisplayName** 속성을 `JoinDomain`로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="89fad-121">**JoinDomain** 시퀀스에 **GetWmiObject** 활동을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="89fad-122">다음과 같이 **GetWmiObject** 활동의 속성을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="89fad-123">속성</span><span class="sxs-lookup"><span data-stu-id="89fad-123">Property</span></span>|<span data-ttu-id="89fad-124">값</span><span class="sxs-lookup"><span data-stu-id="89fad-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="89fad-125">**클래스**</span><span class="sxs-lookup"><span data-stu-id="89fad-125">**Class**</span></span>|<span data-ttu-id="89fad-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="89fad-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="89fad-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="89fad-127">**PSComputerName**</span></span>|<span data-ttu-id="89fad-128">생략</span><span class="sxs-lookup"><span data-stu-id="89fad-128">{comp}</span></span>|
   |<span data-ttu-id="89fad-129">**유형이**</span><span class="sxs-lookup"><span data-stu-id="89fad-129">**PSCredential**</span></span>|<span data-ttu-id="89fad-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="89fad-130">MachineCred</span></span>|

9. <span data-ttu-id="89fad-131">**GetWmiObject** 활동 뒤에 **Addcomputer** 활동을 **JoinDomain** 시퀀스에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="89fad-132">다음과 같이 **Addcomputer** 활동의 속성을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="89fad-133">속성</span><span class="sxs-lookup"><span data-stu-id="89fad-133">Property</span></span>|<span data-ttu-id="89fad-134">값</span><span class="sxs-lookup"><span data-stu-id="89fad-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="89fad-135">**컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="89fad-135">**ComputerName**</span></span>|<span data-ttu-id="89fad-136">생략</span><span class="sxs-lookup"><span data-stu-id="89fad-136">{comp}</span></span>|
    |<span data-ttu-id="89fad-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="89fad-137">**DomainCredential**</span></span>|<span data-ttu-id="89fad-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="89fad-138">DomainCred</span></span>|

11. <span data-ttu-id="89fad-139">**Addcomputer** 활동 이후 **JoinDomain** 시퀀스에 **RestartComputer** 활동을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="89fad-140">다음과 같이 **RestartComputer** 활동의 속성을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="89fad-141">속성</span><span class="sxs-lookup"><span data-stu-id="89fad-141">Property</span></span>|<span data-ttu-id="89fad-142">값</span><span class="sxs-lookup"><span data-stu-id="89fad-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="89fad-143">**컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="89fad-143">**ComputerName**</span></span>|<span data-ttu-id="89fad-144">생략</span><span class="sxs-lookup"><span data-stu-id="89fad-144">{comp}</span></span>|
    |<span data-ttu-id="89fad-145">**증명서**</span><span class="sxs-lookup"><span data-stu-id="89fad-145">**Credential**</span></span>|<span data-ttu-id="89fad-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="89fad-146">MachineCred</span></span>|
    |<span data-ttu-id="89fad-147">**에 대 한**</span><span class="sxs-lookup"><span data-stu-id="89fad-147">**For**</span></span>|<span data-ttu-id="89fad-148">Microsoft. PowerShell. WaitForServiceTypes. PowerShell</span><span class="sxs-lookup"><span data-stu-id="89fad-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="89fad-149">**설정**</span><span class="sxs-lookup"><span data-stu-id="89fad-149">**Force**</span></span>|<span data-ttu-id="89fad-150">True</span><span class="sxs-lookup"><span data-stu-id="89fad-150">True</span></span>|
    |<span data-ttu-id="89fad-151">연결 시도 간격</span><span class="sxs-lookup"><span data-stu-id="89fad-151">Wait</span></span>|<span data-ttu-id="89fad-152">True</span><span class="sxs-lookup"><span data-stu-id="89fad-152">True</span></span>|
    |<span data-ttu-id="89fad-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="89fad-153">PSComputerName</span></span>|<span data-ttu-id="89fad-154">{""}</span><span class="sxs-lookup"><span data-stu-id="89fad-154">{""}</span></span>|

13. <span data-ttu-id="89fad-155">**RestartComputer** 활동 뒤에 **JoinDomain** 시퀀스에 **GetWmiObject** 활동을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="89fad-156">해당 속성을 이전 **GetWmiObject** 활동과 동일 하 게 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="89fad-157">절차를 완료 하면 워크플로 디자인 창이 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="89fad-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="89fad-158">workflow designer의 ![JoinDomain XAML](../media/joindomainworkflow.png)
    ![workflow designer의 JOINDOMAIN xaml](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="89fad-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>
---
title: 자문 개발 지침 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854873"
---
# <a name="advisory-development-guidelines"></a><span data-ttu-id="a17a3-102">권장되는 개발 지침</span><span class="sxs-lookup"><span data-stu-id="a17a3-102">Advisory Development Guidelines</span></span>

<span data-ttu-id="a17a3-103">이 섹션에서는 적절 한 개발 및 사용자 환경을 위해 고려해 야 하는 지침을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-103">This section describes guidelines that you should consider to ensure good development and user experiences.</span></span> <span data-ttu-id="a17a3-104">적용 될 수 있습니다 경우에 따라 및 경우도 있기 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-104">Sometimes they might apply, and sometimes they might not.</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="a17a3-105">디자인 지침</span><span class="sxs-lookup"><span data-stu-id="a17a3-105">Design Guidelines</span></span>

<span data-ttu-id="a17a3-106">Cmdlet을 디자인할 때 다음 지침을 고려 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-106">The following guidelines should be considered when designing cmdlets.</span></span> <span data-ttu-id="a17a3-107">상황에 적용 되는 디자인 지침을 찾으면 유사한 지침에 대 한 코드 지침 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-107">When you find a Design guideline that applies to your situation, be sure to look at the Code guidelines for similar guidelines.</span></span>

### <a name="support-an-inputobject-parameter-ad01"></a><span data-ttu-id="a17a3-108">InputObject 매개 변수 (AD01)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-108">Support an InputObject Parameter (AD01)</span></span>

<span data-ttu-id="a17a3-109">Microsoft.NET Framework 개체를 사용 하 여 직접 Windows PowerShell 작동 하기 때문에.NET Framework 개체는 정확히 일치 하는 항목의 유형은 사용자 특정 작업을 수행 하 고 사용할 수 있는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-109">Because Windows PowerShell works directly with Microsoft .NET Framework objects, a .NET Framework object is often available that exactly matches the type the user needs to perform a particular operation.</span></span> <span data-ttu-id="a17a3-110">`InputObject` 매개 변수 입력으로 이러한 개체에 대 한 표준 이름이입니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-110">`InputObject` is the standard name for a parameter that takes such an object as input.</span></span> <span data-ttu-id="a17a3-111">예를 들어 샘플 **중지 Proc** cmdlet에는 [StopProc 자습서](./stopproc-tutorial.md) 정의 `InputObject` 프로세스 파이프라인의 입력을 지 원하는 형식의 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-111">For example, the sample **Stop-Proc** cmdlet in the [StopProc Tutorial](./stopproc-tutorial.md) defines an `InputObject` parameter of type Process that supports the input from the pipeline.</span></span> <span data-ttu-id="a17a3-112">사용자 수 프로세스 개체의 집합을 가져옵니다, 개체를 중지 하려면를 선택 하 고 조작 및를 전달 합니다는 **중지 Proc** 직접 cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a17a3-112">The user can get a set of process objects, manipulate them to select the exact objects to stop, and then pass them to the **Stop-Proc** cmdlet directly.</span></span>

### <a name="support-the-force-parameter-ad02"></a><span data-ttu-id="a17a3-113">Force 매개 변수 (AD02)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-113">Support the Force Parameter (AD02)</span></span>

<span data-ttu-id="a17a3-114">경우에 따라 cmdlet에서 요청 된 작업을 수행할 수 없도록 사용자를 보호 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-114">Occasionally, a cmdlet needs to protect the user from performing a requested operation.</span></span> <span data-ttu-id="a17a3-115">이러한 cmdlet을 지원 해야는 `Force` 사용자가 사용자 작업을 수행할 권한이 있는 경우 해당 보호를 재정의할 수 있도록 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-115">Such a cmdlet should support a `Force` parameter to allow the user to override that protection if the user has permissions to perform the operation.</span></span>

<span data-ttu-id="a17a3-116">예를 들어 합니다 [Remove-item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet는 읽기 전용 파일을 정상적으로 제거 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-116">For example, the [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet does not normally remove a read-only file.</span></span> <span data-ttu-id="a17a3-117">하지만이 cmdlet은 지원 한 `Force` 매개 변수를 적용할 수 있는 읽기 전용 파일을 제거 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-117">However, this cmdlet supports a `Force` parameter so a user can force removal of a read-only file.</span></span> <span data-ttu-id="a17a3-118">사용자가 이미 읽기 전용 특성을 수정할 수 있는 권한이 사용자 파일을 제거 하 고 아니면 사용 하 여는 `Force` 매개 변수는 작업을 간소화 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-118">If the user already has permission to modify the read-only attribute, and the user removes the file, use of the `Force` parameter simplifies the operation.</span></span> <span data-ttu-id="a17a3-119">그러나 사용자 파일을 제거할 수 있는 권한이 없는 경우는 `Force` 매개 변수는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-119">However, if the user does not have permission to remove the file, the `Force` parameter has no effect.</span></span>

### <a name="handle-credentials-through-windows-powershell-ad03"></a><span data-ttu-id="a17a3-120">Windows PowerShell (AD03)을 통해 자격 증명 처리</span><span class="sxs-lookup"><span data-stu-id="a17a3-120">Handle Credentials Through Windows PowerShell (AD03)</span></span>

<span data-ttu-id="a17a3-121">Cmdlet을 정의 해야는 `Credential` 자격 증명을 나타내는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-121">A cmdlet should define a `Credential` parameter to represent credentials.</span></span> <span data-ttu-id="a17a3-122">이 매개 변수 형식 이어야 합니다 [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) 자격 증명 특성 선언을 사용 하 여 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-122">This parameter must be of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) and must be defined using a Credential attribute declaration.</span></span> <span data-ttu-id="a17a3-123">이 지원을 자동으로 전체 자격 증명을 직접 제공 되지 않은 경우 사용자 이름, 암호, 또는 둘 다에 사용자 라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-123">This support automatically prompts the user for the user name, for the password, or for both when a full credential is not supplied directly.</span></span> <span data-ttu-id="a17a3-124">자격 증명 특성에 대 한 자세한 내용은 참조 하세요. [자격 증명 특성 선언을](./credential-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-124">For more information about the Credential attribute, see [Credential Attribute Declaration](./credential-attribute-declaration.md).</span></span>

### <a name="support-encoding-parameters-ad04"></a><span data-ttu-id="a17a3-125">인코딩 매개 변수 (AD04)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-125">Support Encoding Parameters (AD04)</span></span>

<span data-ttu-id="a17a3-126">Cmdlet을 읽거나와 같은 쓰거나 파일 시스템을 파일에서 읽는 이진 형식으로 텍스트를 쓰는 경우 cmdlet에 이진 형식에서 텍스트 인코딩 되는 방식을 지정 하는 Encoding 매개 변수를 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-126">If your cmdlet reads or writes text to or from a binary form, such as writing to or reading from a file in a filesystem, then your cmdlet has to have Encoding parameter that specifies how the text is encoded in the binary form.</span></span>

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a><span data-ttu-id="a17a3-127">테스트 Cmdlet (AD05) 부울 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-127">Test Cmdlets Should Return a Boolean (AD05)</span></span>

<span data-ttu-id="a17a3-128">해당 리소스에 대 한 테스트를 수행 하는 Cmdlet를 반환할지를 [System.Boolean](/dotnet/api/System.Boolean) 조건식에 사용할 수 있도록 파이프라인으로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-128">Cmdlets that perform tests against their resources should return a [System.Boolean](/dotnet/api/System.Boolean) type to the pipeline so that they can be used in conditional expressions.</span></span>

## <a name="code-guidelines"></a><span data-ttu-id="a17a3-129">코드 지침</span><span class="sxs-lookup"><span data-stu-id="a17a3-129">Code Guidelines</span></span>

<span data-ttu-id="a17a3-130">Cmdlet 코드를 작성할 때 다음 지침을 고려 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-130">The following guidelines should be considered when writing cmdlet code.</span></span> <span data-ttu-id="a17a3-131">상황에 적용 되는 지침을 찾으면 유사한 지침에 대 한 디자인 지침 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-131">When you find a guideline that applies to your situation, be sure to look at the Design guidelines for similar guidelines.</span></span>

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a><span data-ttu-id="a17a3-132">Cmdlet 클래스 명명 규칙 (AC01)를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-132">Follow Cmdlet Class Naming Conventions (AC01)</span></span>

<span data-ttu-id="a17a3-133">다음 표준 명명 규칙에 의해 cmdlet 더 쉽게 검색할 수를 정확 하 게 cmdlet 수행할 작업을 이해 하면 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-133">By following standard naming conventions, you make your cmdlets more discoverable, and you help the user understand exactly what the cmdlets do.</span></span> <span data-ttu-id="a17a3-134">이 방법은 cmdlet는 공용 형식 이므로 Windows PowerShell을 사용 하 여 다른 개발자가 특히 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-134">This practice is particularly important for other developers using Windows PowerShell because cmdlets are public types.</span></span>

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a><span data-ttu-id="a17a3-135">올바른 Namespace에서 Cmdlet을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-135">Define a Cmdlet in the Correct Namespace</span></span>

<span data-ttu-id="a17a3-136">일반적으로 추가 되는.NET Framework 네임 스페이스에는 cmdlet에 대 한 클래스를 정의 "입니다. 명령 "cmdlet을 실행 하는 제품을 나타내는 네임 스페이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-136">You normally define the class for a cmdlet in a .NET Framework namespace that appends ".Commands" to the namespace that represents the product in which the cmdlet runs.</span></span> <span data-ttu-id="a17a3-137">Windows PowerShell을 사용 하 여 포함 된 cmdlet에 정의 된 예를 들어를 `Microsoft.PowerShell.Commands` 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-137">For example, cmdlets that are included with Windows PowerShell are defined in the `Microsoft.PowerShell.Commands` namespace.</span></span>

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a><span data-ttu-id="a17a3-138">Cmdlet 이름을 일치 하는 Cmdlet 클래스 이름</span><span class="sxs-lookup"><span data-stu-id="a17a3-138">Name the Cmdlet Class to Match the Cmdlet Name</span></span>

<span data-ttu-id="a17a3-139">Cmdlet을 구현 하는.NET Framework 클래스에 이름을 지정할 때 클래스 이름을 "*\<동사 >**\<명사 >**\<명령 >*" 합니다 바꾸어야, *\<동사 >* 하 고  *\<명사 >* 동사와 명사는 cmdlet 이름에 사용 되는 자리 표시자입니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-139">When you name the .NET Framework class that implements a cmdlet, name the class "*\<Verb>**\<Noun>**\<Command>*", where you replace the *\<Verb>* and *\<Noun>* placeholders with the verb and noun used for the cmdlet name.</span></span> <span data-ttu-id="a17a3-140">예를 들어 합니다 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 라는 클래스를 통해 구현 됩니다 `GetProcessCommand`합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-140">For example, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet is implemented by a class called `GetProcessCommand`.</span></span>

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a><span data-ttu-id="a17a3-141">파이프라인 입력 되지 않았습니다 (AC02) BeginProcessing 메서드를 재정의 하는 경우</span><span class="sxs-lookup"><span data-stu-id="a17a3-141">If No Pipeline Input Override the BeginProcessing Method (AC02)</span></span>

<span data-ttu-id="a17a3-142">Cmdlet에 파이프라인의 입력을 허용 하지 않는 경우 처리에 구현 해야 합니다 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드.</span><span class="sxs-lookup"><span data-stu-id="a17a3-142">If your cmdlet does not accept input from the pipeline, processing should be implemented in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span> <span data-ttu-id="a17a3-143">이 메서드를 사용 하면 cmdlet 간에 순서를 유지 하려면 Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a17a3-143">Use of this method allows Windows PowerShell to maintain ordering between cmdlets.</span></span> <span data-ttu-id="a17a3-144">파이프라인의 첫 번째 cmdlet을 파이프라인의 나머지 cmdlet을 사용 하면 처리를 시작 하려면 기회가 전에 항상 해당 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-144">The first cmdlet in the pipeline always returns its objects before the remaining cmdlets in the pipeline get a chance to start their processing.</span></span>

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a><span data-ttu-id="a17a3-145">처리 중지 요청 재정의 StopProcessing 메서드가 (AC03)</span><span class="sxs-lookup"><span data-stu-id="a17a3-145">To Handle Stop Requests Override the StopProcessing Method (AC03)</span></span>

<span data-ttu-id="a17a3-146">재정의 된 [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) 메서드 cmdlet에 중지 신호를 처리할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-146">Override the [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) method so that your cmdlet can handle stop signal.</span></span> <span data-ttu-id="a17a3-147">일부 cmdlet에는 해당 작업을 완료 하려면 시간이 오래 걸릴 및 오랫동안 cmdlet은 장기 실행 RPC 호출에 스레드를 차단 하는 경우와 같은 Windows PowerShell 런타임에 호출 간에 전달할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-147">Some cmdlets take a long time to complete their operation, and they let a long time pass between calls to the Windows PowerShell runtime, such as when the cmdlet blocks the thread in long-running RPC calls.</span></span> <span data-ttu-id="a17a3-148">이 호출 하는 cmdlet이 포함 됩니다는 [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드를 합니다 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드 및 기타 피드백 완료 하는 데 시간이 오래 걸릴 수 있습니다 하는 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-148">This includes cmdlets that make calls to the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method, to the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, and to other feedback mechanisms that may take a long time to complete.</span></span> <span data-ttu-id="a17a3-149">이러한 경우 사용자 이러한 cmdlet에 중지 신호를 보내야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-149">For these cases the user might need to send a stop signal to these cmdlets.</span></span>

### <a name="implement-the-idisposable-interface-ac04"></a><span data-ttu-id="a17a3-150">IDisposable 인터페이스 (AC04)</span><span class="sxs-lookup"><span data-stu-id="a17a3-150">Implement the IDisposable Interface (AC04)</span></span>

<span data-ttu-id="a17a3-151">Cmdlet에서 (파이프라인에 기록)의 정리 되지 않은 개체에는 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 cmdlet에 추가 개체 폐기 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-151">If your cmdlet has objects that are not disposed of (written to the pipeline) by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, your cmdlet might require additional object disposal.</span></span> <span data-ttu-id="a17a3-152">예를 들어, cmdlet에 대 한 파일 핸들을 열면 해당 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드 및 사용에 대 한 열 핸들을 유지 합니다 [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를이 핸들에 처리의 끝을 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-152">For example, if your cmdlet opens a file handle in its [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, this handle has to be closed at the end of processing.</span></span>

<span data-ttu-id="a17a3-153">Windows PowerShell 런타임에 항상 호출 하지 않습니다 합니다 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드.</span><span class="sxs-lookup"><span data-stu-id="a17a3-153">The Windows PowerShell runtime does not always call the  [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="a17a3-154">예를 들어 합니다 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) cmdlet은 해당 작업을 통해 중간 취소 되거나 종료 하는 경우 cmdlet의 모든 부분에서 오류가 발생 하는 경우 메서드를 호출 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-154">For example, the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method might not be called if the cmdlet is canceled midway through its operation or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="a17a3-155">개체를 정리 해야 하는 cmdlet에 대 한.NET Framework 클래스 전체를 구현 해야 하므로 [System.IDisposable](/dotnet/api/System.IDisposable) 인터페이스 패턴을 모두 Windows PowerShell 런타임에 호출할 수 있도록 종료자를 포함 하는 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 하 고 [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) 메서드 끝에 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-155">Therefore, the .NET Framework class for a cmdlet that requires object cleanup should implement the complete  [System.IDisposable](/dotnet/api/System.IDisposable) interface pattern, including the finalizer, so that the Windows PowerShell runtime can call both the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>

### <a name="use-serialization-friendly-parameter-types-ac05"></a><span data-ttu-id="a17a3-156">직렬화에 적합 한 매개 변수 형식 (AC05)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-156">Use Serialization-friendly Parameter Types (AC05)</span></span>

<span data-ttu-id="a17a3-157">원격 컴퓨터에서 cmdlet을 실행을 지원 하려면 클라이언트 컴퓨터에서 쉽게 직렬화 및 서버 컴퓨터의 다음 리하이드레이션 될 수 있는 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-157">To support running your cmdlet on remote computers, use types that can be easily serialized on the client computer and then rehydrated on the server computer.</span></span> <span data-ttu-id="a17a3-158">다음 형식은 serialization 친화적입니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-158">The follow types are serialization-friendly.</span></span>

<span data-ttu-id="a17a3-159">기본 형식:</span><span class="sxs-lookup"><span data-stu-id="a17a3-159">Primitive types:</span></span>

- <span data-ttu-id="a17a3-160">바이트, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32, 및 UInt64입니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-160">Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32, and UInt64.</span></span>

- <span data-ttu-id="a17a3-161">부울, Guid, Byte, TimeSpan, DateTime, Uri 및 버전.</span><span class="sxs-lookup"><span data-stu-id="a17a3-161">Boolean, Guid, Byte[], TimeSpan, DateTime, Uri, and Version.</span></span>

- <span data-ttu-id="a17a3-162">Char, String, XmlDocument입니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-162">Char, String, XmlDocument.</span></span>

<span data-ttu-id="a17a3-163">기본 제공 rehydratable 형식:</span><span class="sxs-lookup"><span data-stu-id="a17a3-163">Built-in rehydratable types:</span></span>

- <span data-ttu-id="a17a3-164">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="a17a3-164">PSPrimitiveDictionary</span></span>

- <span data-ttu-id="a17a3-165">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="a17a3-165">SwitchParameter</span></span>

- <span data-ttu-id="a17a3-166">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="a17a3-166">PSListModifier</span></span>

- <span data-ttu-id="a17a3-167">PSCredential</span><span class="sxs-lookup"><span data-stu-id="a17a3-167">PSCredential</span></span>

- <span data-ttu-id="a17a3-168">IPAddress, MailAddress</span><span class="sxs-lookup"><span data-stu-id="a17a3-168">IPAddress, MailAddress</span></span>

- <span data-ttu-id="a17a3-169">CultureInfo</span><span class="sxs-lookup"><span data-stu-id="a17a3-169">CultureInfo</span></span>

- <span data-ttu-id="a17a3-170">X509Certificate2, X500DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="a17a3-170">X509Certificate2, X500DistinguishedName</span></span>

- <span data-ttu-id="a17a3-171">DirectorySecurity, FileSecurity, RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="a17a3-171">DirectorySecurity, FileSecurity, RegistrySecurity</span></span>

<span data-ttu-id="a17a3-172">다른 유형:</span><span class="sxs-lookup"><span data-stu-id="a17a3-172">Other types:</span></span>

- <span data-ttu-id="a17a3-173">SecureString</span><span class="sxs-lookup"><span data-stu-id="a17a3-173">SecureString</span></span>

- <span data-ttu-id="a17a3-174">컨테이너 (목록과 사전 위 유형의)</span><span class="sxs-lookup"><span data-stu-id="a17a3-174">Containers (lists and dictionaries of the above type)</span></span>

### <a name="use-securestring-for-sensitive-data-ac06"></a><span data-ttu-id="a17a3-175">SecureString을 사용 하 여 중요 한 데이터 (AC06)</span><span class="sxs-lookup"><span data-stu-id="a17a3-175">Use SecureString for Sensitive Data (AC06)</span></span>

<span data-ttu-id="a17a3-176">중요 한 데이터를 항상 처리 하는 경우 사용 합니다 [System.Security.Securestring](/dotnet/api/System.Security.SecureString) 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-176">When handling sensitive data always use the [System.Security.Securestring](/dotnet/api/System.Security.SecureString) data type.</span></span> <span data-ttu-id="a17a3-177">이 파이프라인 입력 파이프라인으로 중요 한 데이터를 반환 합니다. 뿐만 아니라 매개 변수를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a17a3-177">This could include pipeline input to parameters, as well as returning sensitive data to the pipeline.</span></span>

## <a name="see-also"></a><span data-ttu-id="a17a3-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a17a3-178">See Also</span></span>

[<span data-ttu-id="a17a3-179">필요한 개발 지침</span><span class="sxs-lookup"><span data-stu-id="a17a3-179">Required Development Guidelines</span></span>](./required-development-guidelines.md)

[<span data-ttu-id="a17a3-180">좋습니다 개발 지침</span><span class="sxs-lookup"><span data-stu-id="a17a3-180">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

<span data-ttu-id="a17a3-181">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="a17a3-181">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

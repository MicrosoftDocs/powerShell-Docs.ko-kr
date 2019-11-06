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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370042"
---
# <a name="advisory-development-guidelines"></a><span data-ttu-id="591fc-102">권장되는 개발 지침</span><span class="sxs-lookup"><span data-stu-id="591fc-102">Advisory Development Guidelines</span></span>

<span data-ttu-id="591fc-103">이 섹션에서는 적절 한 개발과 사용자 환경을 보장 하기 위해 고려해 야 할 지침을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-103">This section describes guidelines that you should consider to ensure good development and user experiences.</span></span> <span data-ttu-id="591fc-104">경우에 따라 적용 될 수도 있고 그렇지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-104">Sometimes they might apply, and sometimes they might not.</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="591fc-105">디자인 지침</span><span class="sxs-lookup"><span data-stu-id="591fc-105">Design Guidelines</span></span>

<span data-ttu-id="591fc-106">Cmdlet을 디자인할 때 다음 지침을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-106">The following guidelines should be considered when designing cmdlets.</span></span> <span data-ttu-id="591fc-107">상황에 적용 되는 디자인 지침을 찾았으면 유사한 지침에 대 한 코드 지침을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-107">When you find a Design guideline that applies to your situation, be sure to look at the Code guidelines for similar guidelines.</span></span>

### <a name="support-an-inputobject-parameter-ad01"></a><span data-ttu-id="591fc-108">InputObject 매개 변수 지원 (AD01)</span><span class="sxs-lookup"><span data-stu-id="591fc-108">Support an InputObject Parameter (AD01)</span></span>

<span data-ttu-id="591fc-109">Windows PowerShell은 Microsoft .NET Framework 개체와 직접 연동 되므로 사용자가 특정 작업을 수행 하는 데 필요한 형식과 정확히 일치 하는 .NET Framework 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-109">Because Windows PowerShell works directly with Microsoft .NET Framework objects, a .NET Framework object is often available that exactly matches the type the user needs to perform a particular operation.</span></span> <span data-ttu-id="591fc-110">`InputObject`는 이러한 개체를 입력으로 사용 하는 매개 변수의 표준 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-110">`InputObject` is the standard name for a parameter that takes such an object as input.</span></span> <span data-ttu-id="591fc-111">예를 들어 [Stopproc 자습서](./stopproc-tutorial.md) 의 샘플 **Stop proc** cmdlet은 파이프라인에서 입력을 지 원하는 Process 형식의 `InputObject` 매개 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-111">For example, the sample **Stop-Proc** cmdlet in the [StopProc Tutorial](./stopproc-tutorial.md) defines an `InputObject` parameter of type Process that supports the input from the pipeline.</span></span> <span data-ttu-id="591fc-112">사용자는 프로세스 개체 집합을 가져온 다음이를 조작 하 여 중지할 정확한 개체를 선택 하 고이를 **중지 프로시저** cmdlet에 직접 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-112">The user can get a set of process objects, manipulate them to select the exact objects to stop, and then pass them to the **Stop-Proc** cmdlet directly.</span></span>

### <a name="support-the-force-parameter-ad02"></a><span data-ttu-id="591fc-113">Force 매개 변수 지원 (AD02)</span><span class="sxs-lookup"><span data-stu-id="591fc-113">Support the Force Parameter (AD02)</span></span>

<span data-ttu-id="591fc-114">경우에 따라 cmdlet은 요청 된 작업을 수행 하지 못하도록 사용자를 보호 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-114">Occasionally, a cmdlet needs to protect the user from performing a requested operation.</span></span> <span data-ttu-id="591fc-115">이러한 cmdlet은 사용자가 작업을 수행할 수 있는 권한이 있는 경우 사용자가 해당 보호를 재정의할 수 있도록 `Force` 매개 변수를 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-115">Such a cmdlet should support a `Force` parameter to allow the user to override that protection if the user has permissions to perform the operation.</span></span>

<span data-ttu-id="591fc-116">예를 들어, [항목 제거](/powershell/module/microsoft.powershell.management/remove-item) cmdlet은 일반적으로 읽기 전용 파일을 제거 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-116">For example, the [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet does not normally remove a read-only file.</span></span> <span data-ttu-id="591fc-117">그러나이 cmdlet은 `Force` 매개 변수를 지원 하므로 사용자가 읽기 전용 파일을 강제로 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-117">However, this cmdlet supports a `Force` parameter so a user can force removal of a read-only file.</span></span> <span data-ttu-id="591fc-118">사용자에 게 읽기 전용 특성을 수정할 수 있는 권한이 이미 있는 경우 사용자가 파일을 제거 하면 `Force` 매개 변수를 사용 하면 작업이 간단해 집니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-118">If the user already has permission to modify the read-only attribute, and the user removes the file, use of the `Force` parameter simplifies the operation.</span></span> <span data-ttu-id="591fc-119">그러나 사용자에 게 파일을 제거할 수 있는 권한이 없는 경우 `Force` 매개 변수는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-119">However, if the user does not have permission to remove the file, the `Force` parameter has no effect.</span></span>

### <a name="handle-credentials-through-windows-powershell-ad03"></a><span data-ttu-id="591fc-120">Windows PowerShell을 통해 자격 증명 처리 (AD03)</span><span class="sxs-lookup"><span data-stu-id="591fc-120">Handle Credentials Through Windows PowerShell (AD03)</span></span>

<span data-ttu-id="591fc-121">Cmdlet은 자격 증명을 나타내는 `Credential` 매개 변수를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-121">A cmdlet should define a `Credential` parameter to represent credentials.</span></span> <span data-ttu-id="591fc-122">이 매개 변수는 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 형식 이어야 하며 자격 증명 특성 선언을 사용 하 여 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-122">This parameter must be of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) and must be defined using a Credential attribute declaration.</span></span> <span data-ttu-id="591fc-123">이 지원은 자동으로 전체 자격 증명을 제공 하지 않을 때 사용자 이름, 암호 또는 둘 다를 사용자에 게 묻는 메시지를 자동으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-123">This support automatically prompts the user for the user name, for the password, or for both when a full credential is not supplied directly.</span></span> <span data-ttu-id="591fc-124">자격 증명 특성에 대 한 자세한 내용은 [자격 증명 특성 선언](./credential-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="591fc-124">For more information about the Credential attribute, see [Credential Attribute Declaration](./credential-attribute-declaration.md).</span></span>

### <a name="support-encoding-parameters-ad04"></a><span data-ttu-id="591fc-125">인코딩 매개 변수 지원 (AD04)</span><span class="sxs-lookup"><span data-stu-id="591fc-125">Support Encoding Parameters (AD04)</span></span>

<span data-ttu-id="591fc-126">Cmdlet이 파일 시스템의 파일에 쓰거나 파일을 읽는 등 이진 형식에서 텍스트를 읽거나 쓰는 경우에는 cmdlet에 이진 형식으로 텍스트를 인코딩하는 방법을 지정 하는 Encoding 매개 변수가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-126">If your cmdlet reads or writes text to or from a binary form, such as writing to or reading from a file in a filesystem, then your cmdlet has to have Encoding parameter that specifies how the text is encoded in the binary form.</span></span>

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a><span data-ttu-id="591fc-127">테스트 Cmdlet은 부울 (AD05)을 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-127">Test Cmdlets Should Return a Boolean (AD05)</span></span>

<span data-ttu-id="591fc-128">리소스에 대해 테스트를 수행 하는 cmdlet은 [부울](/dotnet/api/System.Boolean) 형식을 조건식에 반환 하 여 조건식에 사용할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-128">Cmdlets that perform tests against their resources should return a [System.Boolean](/dotnet/api/System.Boolean) type to the pipeline so that they can be used in conditional expressions.</span></span>

## <a name="code-guidelines"></a><span data-ttu-id="591fc-129">코드 지침</span><span class="sxs-lookup"><span data-stu-id="591fc-129">Code Guidelines</span></span>

<span data-ttu-id="591fc-130">Cmdlet 코드를 작성할 때는 다음 지침을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-130">The following guidelines should be considered when writing cmdlet code.</span></span> <span data-ttu-id="591fc-131">상황에 적용 되는 지침을 찾았으면 유사한 지침에 대 한 디자인 지침을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-131">When you find a guideline that applies to your situation, be sure to look at the Design guidelines for similar guidelines.</span></span>

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a><span data-ttu-id="591fc-132">Cmdlet 클래스 명명 규칙 (AC01)을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-132">Follow Cmdlet Class Naming Conventions (AC01)</span></span>

<span data-ttu-id="591fc-133">표준 명명 규칙을 사용 하 여 cmdlet을 더 검색 가능 하 게 만들고, 사용자가 cmdlet이 수행 하는 작업을 정확 하 게 이해할 수 있도록 도와줍니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-133">By following standard naming conventions, you make your cmdlets more discoverable, and you help the user understand exactly what the cmdlets do.</span></span> <span data-ttu-id="591fc-134">이 방법은 cmdlet이 공용 형식 이므로 Windows PowerShell을 사용 하는 다른 개발자에 게 특히 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-134">This practice is particularly important for other developers using Windows PowerShell because cmdlets are public types.</span></span>

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a><span data-ttu-id="591fc-135">올바른 네임 스페이스에 Cmdlet을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-135">Define a Cmdlet in the Correct Namespace</span></span>

<span data-ttu-id="591fc-136">일반적으로 "를 추가 하는 .NET Framework 네임 스페이스에서 cmdlet에 대 한 클래스를 정의 합니다. Cmdlet을 실행 하는 제품을 나타내는 네임 스페이스에 대 한 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-136">You normally define the class for a cmdlet in a .NET Framework namespace that appends ".Commands" to the namespace that represents the product in which the cmdlet runs.</span></span> <span data-ttu-id="591fc-137">예를 들어 Windows PowerShell에 포함 된 cmdlet은 `Microsoft.PowerShell.Commands` 네임 스페이스에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-137">For example, cmdlets that are included with Windows PowerShell are defined in the `Microsoft.PowerShell.Commands` namespace.</span></span>

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a><span data-ttu-id="591fc-138">Cmdlet 이름과 일치 하도록 Cmdlet 클래스 이름을</span><span class="sxs-lookup"><span data-stu-id="591fc-138">Name the Cmdlet Class to Match the Cmdlet Name</span></span>

<span data-ttu-id="591fc-139">Cmdlet을 구현 하는 .NET Framework 클래스의 이름을 " *\<Verb > **\<Noun >** \<Command >* "로 이름을 바꿉니다. 여기서 *\<Verb* *> 및 \<Noun* 자리 표시자를로 바꿉니다. cmdlet 이름에 사용 되는 동사와 명사입니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-139">When you name the .NET Framework class that implements a cmdlet, name the class "*\<Verb>**\<Noun>**\<Command>*", where you replace the *\<Verb>* and *\<Noun>* placeholders with the verb and noun used for the cmdlet name.</span></span> <span data-ttu-id="591fc-140">예를 들어, [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet은 `GetProcessCommand` 라는 클래스에 의해 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-140">For example, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet is implemented by a class called `GetProcessCommand`.</span></span>

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a><span data-ttu-id="591fc-141">파이프라인 입력이 BeginProcessing 메서드 (AC02)를 재정의 하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="591fc-141">If No Pipeline Input Override the BeginProcessing Method (AC02)</span></span>

<span data-ttu-id="591fc-142">Cmdlet이 파이프라인의 입력을 허용 하지 않는 경우에는 처리를 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 에서 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-142">If your cmdlet does not accept input from the pipeline, processing should be implemented in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span> <span data-ttu-id="591fc-143">이 방법을 사용 하면 Windows PowerShell에서 cmdlet 간의 순서를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-143">Use of this method allows Windows PowerShell to maintain ordering between cmdlets.</span></span> <span data-ttu-id="591fc-144">파이프라인의 첫 번째 cmdlet은 항상 파이프라인의 나머지 cmdlet이 해당 개체를 반환 하 여 처리를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-144">The first cmdlet in the pipeline always returns its objects before the remaining cmdlets in the pipeline get a chance to start their processing.</span></span>

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a><span data-ttu-id="591fc-145">중지 요청을 처리 하려면 StopProcessing 메서드 (AC03)를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-145">To Handle Stop Requests Override the StopProcessing Method (AC03)</span></span>

<span data-ttu-id="591fc-146">Cmdlet이 stop 신호를 처리할 수 있도록 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) 를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-146">Override the [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) method so that your cmdlet can handle stop signal.</span></span> <span data-ttu-id="591fc-147">일부 cmdlet은 작업을 완료 하는 데 시간이 오래 걸리고, cmdlet이 장기 실행 RPC 호출에서 스레드를 차단 하는 경우와 같이 Windows PowerShell 런타임 호출 사이에 긴 시간을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-147">Some cmdlets take a long time to complete their operation, and they let a long time pass between calls to the Windows PowerShell runtime, such as when the cmdlet blocks the thread in long-running RPC calls.</span></span> <span data-ttu-id="591fc-148">여기에는 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드를 호출 하 고, [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하 고, 완료 하는 데 시간이 오래 걸릴 수 있는 기타 피드백 메커니즘을 수행 하는 cmdlet이 포함 됩니다. .</span><span class="sxs-lookup"><span data-stu-id="591fc-148">This includes cmdlets that make calls to the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method, to the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, and to other feedback mechanisms that may take a long time to complete.</span></span> <span data-ttu-id="591fc-149">이러한 경우 사용자는 이러한 cmdlet에 중지 신호를 보내야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-149">For these cases the user might need to send a stop signal to these cmdlets.</span></span>

### <a name="implement-the-idisposable-interface-ac04"></a><span data-ttu-id="591fc-150">IDisposable 인터페이스 구현 (AC04)</span><span class="sxs-lookup"><span data-stu-id="591fc-150">Implement the IDisposable Interface (AC04)</span></span>

<span data-ttu-id="591fc-151">Cmdlet에 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 통해 삭제 되지 않는 개체 (파이프라인에 기록)가 있는 경우 cmdlet에서 추가 개체를 삭제 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-151">If your cmdlet has objects that are not disposed of (written to the pipeline) by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, your cmdlet might require additional object disposal.</span></span> <span data-ttu-id="591fc-152">예를 들어 cmdlet이 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드에서 파일 핸들을 [열고 해당 핸들](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 을 계속 열어 둘 경우이 핸들을 사용 하 여 해당 핸들을 열어 둘 수 있습니다. 처리가 끝날 때 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-152">For example, if your cmdlet opens a file handle in its [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, this handle has to be closed at the end of processing.</span></span>

<span data-ttu-id="591fc-153">Windows PowerShell 런타임에서는 항상 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드를 호출 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-153">The Windows PowerShell runtime does not always call the  [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="591fc-154">예를 들어 cmdlet이 작업을 통해 중간에 취소 되거나 cmdlet의 일부에서 종료 오류가 발생 하는 경우에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-154">For example, the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method might not be called if the cmdlet is canceled midway through its operation or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="591fc-155">따라서 개체 정리를 필요로 하는 cmdlet의 .NET Framework 클래스는 Windows PowerShell 런타임 처리가 완료된 후에 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)와 [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) 방법을 모두 호출할 수 있도록 종료자를 포함한 완전한 [System.IDisposable](/dotnet/api/System.IDisposable) 인터페이스 패턴을 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-155">Therefore, the .NET Framework class for a cmdlet that requires object cleanup should implement the complete  [System.IDisposable](/dotnet/api/System.IDisposable) interface pattern, including the finalizer, so that the Windows PowerShell runtime can call both the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>

### <a name="use-serialization-friendly-parameter-types-ac05"></a><span data-ttu-id="591fc-156">Serialization 친화적인 매개 변수 형식 사용 (AC05)</span><span class="sxs-lookup"><span data-stu-id="591fc-156">Use Serialization-friendly Parameter Types (AC05)</span></span>

<span data-ttu-id="591fc-157">원격 컴퓨터에서 cmdlet 실행을 지원 하려면 클라이언트 컴퓨터에서 쉽게 직렬화 할 수 있는 형식을 사용 하 고 서버 컴퓨터에서 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-157">To support running your cmdlet on remote computers, use types that can be easily serialized on the client computer and then rehydrated on the server computer.</span></span> <span data-ttu-id="591fc-158">다음 형식은 serialization에 편리 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-158">The follow types are serialization-friendly.</span></span>

<span data-ttu-id="591fc-159">기본 형식:</span><span class="sxs-lookup"><span data-stu-id="591fc-159">Primitive types:</span></span>

- <span data-ttu-id="591fc-160">Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32 및 UInt64.</span><span class="sxs-lookup"><span data-stu-id="591fc-160">Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32, and UInt64.</span></span>

- <span data-ttu-id="591fc-161">부울, Guid, Byte [], TimeSpan, DateTime, Uri 및 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-161">Boolean, Guid, Byte[], TimeSpan, DateTime, Uri, and Version.</span></span>

- <span data-ttu-id="591fc-162">Char, String, XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="591fc-162">Char, String, XmlDocument.</span></span>

<span data-ttu-id="591fc-163">기본 제공 rehydratable 형식:</span><span class="sxs-lookup"><span data-stu-id="591fc-163">Built-in rehydratable types:</span></span>

- <span data-ttu-id="591fc-164">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="591fc-164">PSPrimitiveDictionary</span></span>

- <span data-ttu-id="591fc-165">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="591fc-165">SwitchParameter</span></span>

- <span data-ttu-id="591fc-166">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="591fc-166">PSListModifier</span></span>

- <span data-ttu-id="591fc-167">유형이</span><span class="sxs-lookup"><span data-stu-id="591fc-167">PSCredential</span></span>

- <span data-ttu-id="591fc-168">IPAddress, MailAddress</span><span class="sxs-lookup"><span data-stu-id="591fc-168">IPAddress, MailAddress</span></span>

- <span data-ttu-id="591fc-169">CultureInfo</span><span class="sxs-lookup"><span data-stu-id="591fc-169">CultureInfo</span></span>

- <span data-ttu-id="591fc-170">X509Certificate2, System.security.cryptography.x509certificates.x500distinguishedname</span><span class="sxs-lookup"><span data-stu-id="591fc-170">X509Certificate2, X500DistinguishedName</span></span>

- <span data-ttu-id="591fc-171">DirectorySecurity, System.security.accesscontrol.filesecurity, RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="591fc-171">DirectorySecurity, FileSecurity, RegistrySecurity</span></span>

<span data-ttu-id="591fc-172">기타 형식:</span><span class="sxs-lookup"><span data-stu-id="591fc-172">Other types:</span></span>

- <span data-ttu-id="591fc-173">SecureString</span><span class="sxs-lookup"><span data-stu-id="591fc-173">SecureString</span></span>

- <span data-ttu-id="591fc-174">컨테이너 (위 형식의 목록 및 사전)</span><span class="sxs-lookup"><span data-stu-id="591fc-174">Containers (lists and dictionaries of the above type)</span></span>

### <a name="use-securestring-for-sensitive-data-ac06"></a><span data-ttu-id="591fc-175">중요 한 데이터에 SecureString 사용 (AC06)</span><span class="sxs-lookup"><span data-stu-id="591fc-175">Use SecureString for Sensitive Data (AC06)</span></span>

<span data-ttu-id="591fc-176">중요 한 데이터를 처리 하는 경우 항상 [system.web](/dotnet/api/System.Security.SecureString) 데이터 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-176">When handling sensitive data always use the [System.Security.Securestring](/dotnet/api/System.Security.SecureString) data type.</span></span> <span data-ttu-id="591fc-177">여기에는 매개 변수에 대 한 파이프라인 입력 뿐만 아니라 중요 한 데이터를 파이프라인으로 반환 하는 작업이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="591fc-177">This could include pipeline input to parameters, as well as returning sensitive data to the pipeline.</span></span>

## <a name="see-also"></a><span data-ttu-id="591fc-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="591fc-178">See Also</span></span>

[<span data-ttu-id="591fc-179">필수 개발 지침</span><span class="sxs-lookup"><span data-stu-id="591fc-179">Required Development Guidelines</span></span>](./required-development-guidelines.md)

[<span data-ttu-id="591fc-180">권장 되는 개발 지침</span><span class="sxs-lookup"><span data-stu-id="591fc-180">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

<span data-ttu-id="591fc-181">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="591fc-181">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

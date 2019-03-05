---
title: Cmdlet 입력 처리 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: dfaaa19fd3d4eb65a3fd335fb984a69874688f27
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861489"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="54d84-102">Cmdlet 입력 처리 메서드</span><span class="sxs-lookup"><span data-stu-id="54d84-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="54d84-103">Cmdlet은 입력 처리 작업을 수행 하려면이 항목에 설명 된 메서드 중 하나 이상을 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span> <span data-ttu-id="54d84-104">이러한 메서드는 전처리 작업, 입력 처리 작업 및 후 처리 작업을 수행 하는 cmdlet를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-104">These methods allow the cmdlet to perform pre-processing operations, input processing operations, and post-processing operations.</span></span> <span data-ttu-id="54d84-105">또한 이러한 메서드를 사용 하면 cmdlet 처리를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-105">These methods also allow you to stop cmdlet processing.</span></span>

## <a name="pre-processing-tasks"></a><span data-ttu-id="54d84-106">전처리 작업</span><span class="sxs-lookup"><span data-stu-id="54d84-106">Pre-Processing Tasks</span></span>

<span data-ttu-id="54d84-107">Cmdlet를 재정의 해야 합니다 [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) cmdlet에서 나중에 처리할 수 있는 모든 레코드에 대 한 잘못 된 모든 전처리 작업을 추가 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-107">Cmdlets should override the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span> <span data-ttu-id="54d84-108">Windows PowerShell 명령 파이프라인을 처리할 때 Windows PowerShell이이 메서드를 호출 되 면 cmdlet에 파이프라인의 각 인스턴스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-108">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="54d84-109">Windows PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-109">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="54d84-110">다음 코드의 구현을 보여 줍니다는 [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) 메서드.</span><span class="sxs-lookup"><span data-stu-id="54d84-110">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

<span data-ttu-id="54d84-111">사용 하는 방법의 자세한 예제는 [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) 메서드를 참조 하세요 [SelectStr 자습서](./selectstr-tutorial.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-111">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span> <span data-ttu-id="54d84-112">이 자습서에서는 합니다 **선택 Str** cmdlet을 사용 합니다 [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) 검색 입력 레코드를 처리 하는 데 사용 되는 정규식을 생성 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-112">In this tutorial, the **Select-Str** cmdlet uses the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to generate the regular expression that is used to search the input processing records.</span></span>

## <a name="input-processing-tasks"></a><span data-ttu-id="54d84-113">처리 태스크를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-113">Input Processing Tasks</span></span>

<span data-ttu-id="54d84-114">Cmdlet을 재정의할 수는 [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) cmdlet로 전송 되는 입력을 처리 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-114">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="54d84-115">Windows PowerShell 명령 파이프라인을 처리할 때 Windows PowerShell cmdlet에서 처리 되는 각 입력된 레코드에 대해이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-115">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="54d84-116">Windows PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-116">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>
<span data-ttu-id="54d84-117">Cmdlet을 재정의할 수는 [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) cmdlet로 전송 되는 입력을 처리 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-117">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="54d84-118">Windows PowerShell 명령 파이프라인을 처리할 때 Windows PowerShell cmdlet에서 처리 되는 각 입력된 레코드에 대해이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-118">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="54d84-119">Windows PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-119">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="54d84-120">다음 코드의 구현을 보여 줍니다는 [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) 메서드.</span><span class="sxs-lookup"><span data-stu-id="54d84-120">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

<span data-ttu-id="54d84-121">사용 하는 방법의 자세한 예제는 [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) 메서드를 참조 하세요 [SelectStr 자습서](./selectstr-tutorial.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-121">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="post-processing-tasks"></a><span data-ttu-id="54d84-122">사후 처리 작업</span><span class="sxs-lookup"><span data-stu-id="54d84-122">Post-Processing Tasks</span></span>

<span data-ttu-id="54d84-123">Cmdlet를 재정의 해야 합니다 [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) cmdlet에서 처리 된 모든 레코드에 유효한 모든 사후 처리 작업을 추가 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-123">Cmdlets should override the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span> <span data-ttu-id="54d84-124">예를 들어 cmdlet 할 개체 변수를 완료 한 후 정리를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-124">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="54d84-125">Windows PowerShell 명령 파이프라인을 처리할 때 Windows PowerShell이이 메서드를 호출 되 면 cmdlet에 파이프라인의 각 인스턴스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-125">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="54d84-126">그러나는 것이 Windows PowerShell 런타임을 호출 하지 것입니다 고려해 야 합니다 [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) 메서드 cmdlet은 해당 입력된 처리를 통해 중간 취소 되거나 종료 하는 경우 cmdlet의 모든 부분에서 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-126">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="54d84-127">이러한 이유로 cmdlet 개체를 정리 해야 하는 전체 구현 해야 [System.Idisposable](/dotnet/api/System.IDisposable) 둘 다 런타임에 호출할 수 있도록 종료자를 포함 하 여 패턴을 [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) 하 고 [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) 메서드 끝에 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-127">For this reason, a cmdlet that requires object cleanup should implement the complete [System.Idisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="54d84-128">Windows PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-128">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>
<span data-ttu-id="54d84-129">Windows PowerShell 명령 파이프라인을 처리할 때 Windows PowerShell이이 메서드를 호출 되 면 cmdlet에 파이프라인의 각 인스턴스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-129">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="54d84-130">그러나는 것이 Windows PowerShell 런타임을 호출 하지 것입니다 고려해 야 합니다 [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) 메서드 cmdlet은 해당 입력된 처리를 통해 중간 취소 되거나 종료 하는 경우 cmdlet의 모든 부분에서 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-130">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="54d84-131">이러한 이유로 cmdlet 개체를 정리 해야 하는 전체 구현 해야 [System.Idisposable](/dotnet/api/System.IDisposable) 둘 다 런타임에 호출할 수 있도록 종료자를 포함 하 여 패턴을 [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) 하 고 [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) 메서드 끝에 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-131">For this reason, a cmdlet that requires object cleanup should implement the complete [System.Idisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="54d84-132">Windows PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-132">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="54d84-133">다음 코드의 구현을 보여 줍니다는 [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) 메서드.</span><span class="sxs-lookup"><span data-stu-id="54d84-133">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

<span data-ttu-id="54d84-134">사용 하는 방법의 자세한 예제는 [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) 메서드를 참조 하세요 [SelectStr 자습서](./selectstr-tutorial.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="54d84-134">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54d84-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54d84-135">See Also</span></span>

[<span data-ttu-id="54d84-136">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="54d84-136">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="54d84-137">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="54d84-137">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[<span data-ttu-id="54d84-138">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="54d84-138">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="54d84-139">System.Idisposable</span><span class="sxs-lookup"><span data-stu-id="54d84-139">System.Idisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="54d84-140">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="54d84-140">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
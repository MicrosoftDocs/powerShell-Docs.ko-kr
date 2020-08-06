---
title: Cmdlet 입력 처리 방법 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.openlocfilehash: e69c5a366b2d74ddd92c844bda0b1e3a65539c10
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784455"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="623a6-102">Cmdlet 입력 처리 메서드</span><span class="sxs-lookup"><span data-stu-id="623a6-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="623a6-103">Cmdlet은 작업을 수행 하기 위해이 항목에서 설명 하는 하나 이상의 입력 처리 방법을 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="623a6-104">이러한 메서드를 통해 cmdlet은 전처리, 입력 처리 및 사후 처리 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="623a6-105">이러한 메서드를 사용 하 여 cmdlet 처리를 중지할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="623a6-106">이러한 메서드를 사용 하는 방법에 대 한 자세한 예제는 [Selectstr 자습서](selectstr-tutorial.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="623a6-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="623a6-107">전처리 작업</span><span class="sxs-lookup"><span data-stu-id="623a6-107">Pre-Processing Operations</span></span>

<span data-ttu-id="623a6-108">Cmdlet은 나중에 cmdlet에 의해 처리 되는 모든 레코드에 유효한 전처리 작업을 추가 하기 위해 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 를 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="623a6-109">PowerShell에서 명령 파이프라인을 처리할 때 PowerShell은 파이프라인에서 cmdlet의 각 인스턴스에 대해이 메서드를 한 번씩 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="623a6-110">PowerShell에서 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 [Cmdlet 처리 수명 주기](/previous-versions/ms714429(v=vs.85))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="623a6-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="623a6-111">다음 코드에서는 BeginProcessing 메서드의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="623a6-112">입력 처리 작업</span><span class="sxs-lookup"><span data-stu-id="623a6-112">Input Processing Operations</span></span>

<span data-ttu-id="623a6-113">Cmdlet은 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 하 여 cmdlet으로 전송 되는 입력을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="623a6-114">PowerShell에서 명령 파이프라인을 처리할 때 cmdlet에 의해 처리 되는 각 입력 레코드에 대해이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="623a6-115">PowerShell에서 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 [Cmdlet 처리 수명 주기](/previous-versions/ms714429(v=vs.85))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="623a6-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="623a6-116">다음 코드에서는 ProcessRecord 메서드의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="623a6-117">후 처리 작업</span><span class="sxs-lookup"><span data-stu-id="623a6-117">Post-Processing Operations</span></span>

<span data-ttu-id="623a6-118">Cmdlet은 cmdlet에 의해 처리 된 모든 레코드에 유효한 후 처리 작업을 추가 하기 위해 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 를 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="623a6-119">예를 들어 cmdlet은 처리를 완료 한 후 개체 변수를 정리 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="623a6-120">PowerShell에서 명령 파이프라인을 처리할 때 PowerShell은 파이프라인에서 cmdlet의 각 인스턴스에 대해이 메서드를 한 번씩 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="623a6-121">그러나 cmdlet이 입력 처리를 통해 중간에 취소 되거나 cmdlet의 일부에서 종료 오류가 발생 하는 경우에는 PowerShell 런타임이 EndProcessing 메서드를 호출 하지 않는다는 점을 기억해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="623a6-122">이러한 이유로 개체 정리를 필요로 하는 cmdlet은 종료자를 포함 하 [여 전체 system.string](/dotnet/api/System.IDisposable) 패턴을 구현 해야 합니다. 이렇게 하면 런타임에서 처리가 끝날 때 EndProcessing 및 [system.string 메서드를](/dotnet/api/System.IDisposable.Dispose) 모두 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="623a6-123">PowerShell에서 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 [Cmdlet 처리 수명 주기](/previous-versions/ms714429(v=vs.85))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="623a6-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="623a6-124">다음 코드에서는 EndProcessing 메서드의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="623a6-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="623a6-125">See Also</span></span>

[<span data-ttu-id="623a6-126">System.object를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="623a6-127">ProcessRecord입니다.</span><span class="sxs-lookup"><span data-stu-id="623a6-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="623a6-128">System.object..</span><span class="sxs-lookup"><span data-stu-id="623a6-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="623a6-129">SelectStr 자습서</span><span class="sxs-lookup"><span data-stu-id="623a6-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="623a6-130">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="623a6-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="623a6-131">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="623a6-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)

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
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068490"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="100ad-102">Cmdlet 입력 처리 메서드</span><span class="sxs-lookup"><span data-stu-id="100ad-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="100ad-103">Cmdlet은 입력 처리 작업을 수행 하려면이 항목에 설명 된 메서드 중 하나 이상을 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="100ad-104">이러한 메서드는 사전 처리, 입력된 처리 및 사후 처리 작업을 수행 하는 cmdlet를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="100ad-105">또한 이러한 메서드를 사용 하면 cmdlet 처리를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="100ad-106">이러한 메서드를 사용 하는 방법의 자세한 예제를 보려면 [SelectStr 자습서](selectstr-tutorial.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="100ad-107">전처리 작업</span><span class="sxs-lookup"><span data-stu-id="100ad-107">Pre-Processing Operations</span></span>

<span data-ttu-id="100ad-108">Cmdlet를 재정의 해야 합니다 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) cmdlet에서 나중에 처리할 수 있는 모든 레코드에 대 한 잘못 된 모든 전처리 작업을 추가 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="100ad-109">PowerShell 명령 파이프라인을 처리할 때 PowerShell이이 메서드를 호출 되 면 cmdlet에 파이프라인의 각 인스턴스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="100ad-110">PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](/previous-versions/ms714429(v=vs.85))합니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="100ad-111">다음 코드를 BeginProcessing 메서드 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="100ad-112">작업을 처리 하는 입력</span><span class="sxs-lookup"><span data-stu-id="100ad-112">Input Processing Operations</span></span>

<span data-ttu-id="100ad-113">Cmdlet을 재정의할 수는 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cmdlet로 전송 되는 입력을 처리 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="100ad-114">PowerShell 명령 파이프라인을 처리할 때 PowerShell cmdlet에서 처리 되는 각 입력된 레코드에 대해이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="100ad-115">PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](/previous-versions/ms714429(v=vs.85))합니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="100ad-116">다음 코드는 ProcessRecord 메서드의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="100ad-117">후 처리 작업</span><span class="sxs-lookup"><span data-stu-id="100ad-117">Post-Processing Operations</span></span>

<span data-ttu-id="100ad-118">Cmdlet를 재정의 해야 합니다 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) cmdlet에서 처리 된 모든 레코드에 유효한 모든 사후 처리 작업을 추가 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="100ad-119">예를 들어 cmdlet 할 개체 변수를 완료 한 후 정리를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="100ad-120">PowerShell 명령 파이프라인을 처리할 때 PowerShell이이 메서드를 호출 되 면 cmdlet에 파이프라인의 각 인스턴스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="100ad-121">그러나 것을 기억해 PowerShell 런타임이 cmdlet은 해당 입력된 처리를 통해 중간 취소 되 면 나 cmdlet의 모든 부분에서 종료 오류가 발생 한 경우 EndProcessing 메서드 호출 하지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="100ad-122">이러한 이유로 cmdlet 개체를 정리 해야 하는 전체 구현 해야 [System.IDisposable](/dotnet/api/System.IDisposable) 런타임에서 모두 EndProcessing을 호출할 수 있도록 종료자를 포함 하 여 패턴 및 [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) 메서드 끝에 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="100ad-123">PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](/previous-versions/ms714429(v=vs.85))합니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="100ad-124">다음 코드의 EndProcessing 메서드 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="100ad-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="100ad-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="100ad-125">See Also</span></span>

[<span data-ttu-id="100ad-126">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="100ad-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="100ad-127">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="100ad-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="100ad-128">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="100ad-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="100ad-129">SelectStr 자습서</span><span class="sxs-lookup"><span data-stu-id="100ad-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="100ad-130">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="100ad-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="100ad-131">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="100ad-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)

---
title: Cmdlet에서 확인 요청 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: 0c0517ef7fbd5ae6434773a2dfe276f3a8c35f39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369532"
---
# <a name="requesting-confirmation-from-cmdlets"></a><span data-ttu-id="8da28-102">Cmdlet에서 확인 요청</span><span class="sxs-lookup"><span data-stu-id="8da28-102">Requesting Confirmation from Cmdlets</span></span>

<span data-ttu-id="8da28-103">Cmdlet은 Windows PowerShell 환경 외부에 있는 시스템을 변경 하려고 할 때 확인을 요청 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-103">Cmdlets should request confirmation when they are about to make a change to the system that is outside of the Windows PowerShell environment.</span></span> <span data-ttu-id="8da28-104">예를 들어 cmdlet에서 사용자 계정을 추가 하거나 프로세스를 중지 하려는 경우에는 cmdlet을 실행 하기 전에 사용자의 확인이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-104">For example, if a cmdlet is about to add a user account or stop a process, the cmdlet should require confirmation from the user before it proceeds.</span></span> <span data-ttu-id="8da28-105">반면에 cmdlet이 Windows PowerShell 변수를 변경 하려는 경우에는 cmdlet에 확인이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-105">In contrast, if a cmdlet is about to change a Windows PowerShell variable, the cmdlet does not need to require confirmation.</span></span>

<span data-ttu-id="8da28-106">확인 요청을 수행하기위해 cmdlet은 확인 요청을 지원하도록 지정해야 하며, 이 경우에는(선택 사항) 확인 요청 메시지를 표시하는 메서드인 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 및 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)를 호출해야합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-106">In order to make a confirmation request, the cmdlet must indicate that it supports confirmation requests, and it must call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (optional) methods to display a confirmation request message.</span></span>

## <a name="supporting-confirmation-requests"></a><span data-ttu-id="8da28-107">확인 요청 지원</span><span class="sxs-lookup"><span data-stu-id="8da28-107">Supporting Confirmation Requests</span></span>

<span data-ttu-id="8da28-108">확인 요청을 지원 하려면 cmdlet이 Cmdlet 특성의 `SupportsShouldProcess` 매개 변수를 `true`으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-108">To support confirmation requests, the cmdlet must set the `SupportsShouldProcess` parameter of the Cmdlet attribute to `true`.</span></span> <span data-ttu-id="8da28-109">이를 통해 Windows PowerShell에서 제공 하는 `Confirm` 및 `WhatIf` cmdlet 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-109">This enables the `Confirm` and `WhatIf` cmdlet parameters that are provided by Windows PowerShell.</span></span> <span data-ttu-id="8da28-110">사용자는 `Confirm` 매개 변수를 사용 하 여 확인 요청이 표시 되는지 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-110">The `Confirm` parameter allows the user to control whether the confirmation request is displayed.</span></span> <span data-ttu-id="8da28-111">사용자는 `WhatIf` 매개 변수를 사용 하 여 cmdlet이 메시지를 표시 하거나 작업을 수행할지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-111">The `WhatIf` parameter allows the user to determine whether the cmdlet should display a message or perform its action.</span></span> <span data-ttu-id="8da28-112">Cmdlet에 `Confirm` 및 `WhatIf` 매개 변수를 수동으로 추가 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="8da28-112">Do not manually add the `Confirm` and `WhatIf` parameters to a cmdlet.</span></span>

<span data-ttu-id="8da28-113">다음 예에서는 확인 요청을 지 원하는 Cmdlet 특성 선언을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-113">The following example shows a Cmdlet attribute declaration that supports confirmation requests.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a><span data-ttu-id="8da28-114">확인 요청 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="8da28-114">Calling the Confirmation request methods</span></span>

<span data-ttu-id="8da28-115">Cmdlet 코드에서 시스템을 변경 하는 작업을 수행 하기 전에 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-115">In the cmdlet code, call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method before the operation that changes the system is performed.</span></span> <span data-ttu-id="8da28-116">호출에서 `false`값을 반환 하는 경우 작업이 수행 되지 않고 cmdlet이 다음 작업을 처리 하도록 cmdlet을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-116">Design the cmdlet so that if the call returns a value of `false`, the operation is not performed, and the cmdlet processes the next operation.</span></span>

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="8da28-117">ShouldContinue 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="8da28-117">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="8da28-118">대부분의 cmdlet은 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 사용 하 여 확인을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-118">Most cmdlets request confirmation using only the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="8da28-119">그러나 일부 경우에는 추가 확인이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-119">However, some cases might require additional confirmation.</span></span> <span data-ttu-id="8da28-120">이러한 경우 [에는 system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하 여. s a s. n a m a [.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)</span><span class="sxs-lookup"><span data-stu-id="8da28-120">For these cases, supplement the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call with a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method.</span></span> <span data-ttu-id="8da28-121">이렇게 하면 cmdlet 또는 공급자가 확인 프롬프트에 대 한 **모든 응답에** 대 한 예의 범위를 보다 세밀 하 게 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-121">This allows the cmdlet or provider to more finely control the scope of the **Yes to all** response to the confirmation prompt.</span></span>

<span data-ttu-id="8da28-122">Cmdlet이 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하는 경우 cmdlet은 `Force` 스위치 매개 변수도 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-122">If a cmdlet calls the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method, the cmdlet must also provide a `Force` switch parameter.</span></span> <span data-ttu-id="8da28-123">사용자가 cmdlet을 호출할 때 사용자가 `Force`를 지정 하는 경우 cmdlet은 여전히 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)를 호출 해야 하지만,이 프로세스는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)호출을 무시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-123">If the user specifies `Force` when the user invokes the cmdlet, the cmdlet should still call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), but it should bypass the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>

<span data-ttu-id="8da28-124">사용자에 게 메시지가 표시 되지 않는 비 대화형 환경에서 호출 되는 경우 [에는 예외가 throw 됩니다.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)</span><span class="sxs-lookup"><span data-stu-id="8da28-124">[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) will throw an exception when it is called from a non-interactive environment where the user cannot be prompted.</span></span> <span data-ttu-id="8da28-125">`Force` 매개 변수를 추가 하면 비 대화형 환경에서 호출 하는 경우에도 명령을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-125">Adding a `Force` parameter ensures that the command can still be performed when it is invoked in a non-interactive environment.</span></span>

<span data-ttu-id="8da28-126">다음 예제에서는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하는 [방법과. n](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)a m a. n a m a. a m a를 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-126">The following example shows how to call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

<span data-ttu-id="8da28-127">[System.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하는 동작은 cmdlet이 호출 되는 환경에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-127">The behavior of a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call can vary depending on the environment in which the cmdlet is invoked.</span></span> <span data-ttu-id="8da28-128">위의 지침을 사용 하면 호스트 환경에 관계 없이 cmdlet이 다른 cmdlet과 일관 되 게 동작 하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-128">Using the previous guidelines will help ensure that the cmdlet behaves consistently with other cmdlets, regardless of the host environment.</span></span>

<span data-ttu-id="8da28-129">[System.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하는 방법에 대 한 예제는 확인 [을 요청 하는 방법](./how-to-request-confirmations.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8da28-129">For an example of calling the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specify-the-impact-level"></a><span data-ttu-id="8da28-130">영향 수준 지정</span><span class="sxs-lookup"><span data-stu-id="8da28-130">Specify the Impact Level</span></span>

<span data-ttu-id="8da28-131">Cmdlet을 만들 때 변경의 영향 수준 (심각도)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-131">When you create the cmdlet, specify the impact level (the severity) of the change.</span></span> <span data-ttu-id="8da28-132">이렇게 하려면 Cmdlet 특성의 `ConfirmImpact` 매개 변수 값을 높음, 중간 또는 낮음으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-132">To do this, set the value of the `ConfirmImpact` parameter of the Cmdlet attribute to High, Medium, or Low.</span></span> <span data-ttu-id="8da28-133">Cmdlet에 대 한 `SupportsShouldProcess` 매개 변수도 지정 하는 경우에만 `ConfirmImpact` 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-133">You can specify a value for `ConfirmImpact` only when you also specify the `SupportsShouldProcess` parameter for the cmdlet.</span></span>

<span data-ttu-id="8da28-134">대부분의 cmdlet에 대해 `ConfirmImpact`를 명시적으로 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-134">For most cmdlets, you do not have to explicitly specify `ConfirmImpact`.</span></span>  <span data-ttu-id="8da28-135">대신 매개 변수의 기본 설정인 Medium을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-135">Instead, use the default setting of the parameter, which is Medium.</span></span> <span data-ttu-id="8da28-136">`ConfirmImpact`를 High로 설정 하면 작업이 기본적으로 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-136">If you set `ConfirmImpact` to High, the operation will be confirmed by default.</span></span> <span data-ttu-id="8da28-137">하드 디스크 볼륨을 다시 포맷 하는 등의 매우 방해가 되는 작업에 대해이 설정을 예약 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-137">Reserve this setting for highly disruptive actions, such as reformatting a hard-disk volume.</span></span>

## <a name="calling-non-confirmation-methods"></a><span data-ttu-id="8da28-138">확인 되지 않은 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="8da28-138">Calling Non-Confirmation Methods</span></span>

<span data-ttu-id="8da28-139">Cmdlet 또는 공급자가 메시지를 전송 해야 하지만 확인을 요청 하지 않는 경우 다음 세 가지 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-139">If the cmdlet or provider must send a message but not request confirmation, it can call the following three methods.</span></span> <span data-ttu-id="8da28-140">[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드를 사용 하 여 이러한 형식의 메시지를 보내는 것이 좋습니다. [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 출력은 Cmdlet 또는 공급자의 일반적인 출력과 함께 혼합 스크립트를 작성 하기 어려울 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-140">Avoid using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method to send messages of these types because [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) output is intermingled with the normal output of your cmdlet or provider, which makes script writing difficult.</span></span>

- <span data-ttu-id="8da28-141">사용자가 작업을 수행 하 고 작업을 계속 하기 위해 cmdlet 또는 공급자는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-141">To caution the user and continue with the operation, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method.</span></span>

- <span data-ttu-id="8da28-142">사용자가 `Verbose` 매개 변수를 사용 하 여 검색할 수 있는 추가 정보를 제공 하기 위해 cmdlet 또는 공급자는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-142">To provide additional information that the user can retrieve using the `Verbose` parameter, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method.</span></span>

- <span data-ttu-id="8da28-143">다른 개발자 또는 제품 지원에 대 한 디버깅 수준 세부 정보를 제공 하기 위해 cmdlet 또는 공급자는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-143">To provide debugging-level detail for other developers or for product support, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method.</span></span> <span data-ttu-id="8da28-144">사용자는 `Debug` 매개 변수를 사용 하 여이 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-144">The user can retrieve this information using the `Debug` parameter.</span></span>

<span data-ttu-id="8da28-145">Cmdlet 및 공급자는 먼저 다음 메서드를 호출 하 여 Windows PowerShell 외부에서 시스템을 변경 하는 작업을 수행 하기 전에 확인을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-145">Cmdlets and providers first call the following methods to request confirmation before they attempt to perform an operation that changes a system outside of Windows PowerShell:</span></span>

- [<span data-ttu-id="8da28-146">System.object를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-146">System.Management.Automation.Cmdlet.Shouldprocess</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [<span data-ttu-id="8da28-147">System.web. a n a.</span><span class="sxs-lookup"><span data-stu-id="8da28-147">System.Management.Automation.Provider.Cmdletprovider.Shouldprocess</span></span>](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

<span data-ttu-id="8da28-148">사용자가 명령을 호출 하는 방법에 따라 작업을 확인 하 라는 메시지를 표시 하는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8da28-148">They do so by calling the [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, which prompts the user to confirm the operation based on how the user invoked the command.</span></span>

## <a name="see-also"></a><span data-ttu-id="8da28-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8da28-149">See Also</span></span>

<span data-ttu-id="8da28-150">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="8da28-150">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

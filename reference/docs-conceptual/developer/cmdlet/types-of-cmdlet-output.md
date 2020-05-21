---
title: Cmdlet 출력의 유형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: de21d9ebfec4f23d3819695df225f7a230864a7b
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561418"
---
# <a name="types-of-cmdlet-output"></a><span data-ttu-id="ebaf6-102">Cmdlet 출력의 유형</span><span class="sxs-lookup"><span data-stu-id="ebaf6-102">Types of cmdlet output</span></span>

<span data-ttu-id="ebaf6-103">PowerShell은 출력을 생성 하기 위해 cmdlet에서 호출할 수 있는 몇 가지 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-103">PowerShell provides several methods that can be called by cmdlets to generate output.</span></span> <span data-ttu-id="ebaf6-104">이러한 메서드는 특정 작업을 사용 하 여 결과를 성공 데이터 스트림 또는 오류 데이터 스트림과 같은 특정 데이터 스트림에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-104">These methods use a specific operation to write their output to a specific data stream, such as the success data stream or the error data stream.</span></span> <span data-ttu-id="ebaf6-105">이 문서에서는 출력 형식 및이를 생성 하는 데 사용 되는 메서드를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-105">This article describes the types of output and the methods used to generate them.</span></span>

## <a name="types-of-output"></a><span data-ttu-id="ebaf6-106">출력 유형</span><span class="sxs-lookup"><span data-stu-id="ebaf6-106">Types of output</span></span>

### <a name="success-output"></a><span data-ttu-id="ebaf6-107">성공 출력</span><span class="sxs-lookup"><span data-stu-id="ebaf6-107">Success output</span></span>

<span data-ttu-id="ebaf6-108">Cmdlet은 파이프라인의 다음 명령으로 처리할 수 있는 개체를 반환 하 여 성공 여부를 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-108">Cmdlets can report success by returning an object that can be processed by the next command in the pipeline.</span></span> <span data-ttu-id="ebaf6-109">Cmdlet은 작업을 성공적으로 수행한 후 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-109">After the cmdlet has successfully performed its action, the cmdlet calls the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span> <span data-ttu-id="ebaf6-110">이 메서드를 호출 [하는 것](/dotnet/api/System.Console.WriteLine) 이 [PSHostUserInterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) 또는 시스템 대신이 메서드를 호출 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-110">We recommend that you call this method instead of the [System.Console.WriteLine](/dotnet/api/System.Console.WriteLine) or [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) methods.</span></span>

<span data-ttu-id="ebaf6-111">일반적으로 개체를 반환 하지 않는 cmdlet에 대 한 **PassThru** 스위치 매개 변수를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-111">You can provide a **PassThru** switch parameter for cmdlets that do not typically return objects.</span></span>
<span data-ttu-id="ebaf6-112">명령줄에서 **PassThru** 스위치 매개 변수를 지정 하면 cmdlet에서 개체를 반환 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-112">When the **PassThru** switch parameter is specified at the command line, the cmdlet is asked to return an object.</span></span> <span data-ttu-id="ebaf6-113">**PassThru** 매개 변수를 포함 하는 cmdlet의 예는 [추가-기록](/powershell/module/Microsoft.PowerShell.Core/Add-History)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-113">For an example of a cmdlet that has a **PassThru** parameter, see [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).</span></span>

### <a name="error-output"></a><span data-ttu-id="ebaf6-114">오류 출력.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-114">Error output</span></span>

<span data-ttu-id="ebaf6-115">Cmdlet은 오류를 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-115">Cmdlets can report errors.</span></span> <span data-ttu-id="ebaf6-116">종료 오류가 발생 하면 cmdlet이 예외를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-116">When a terminating error occurs, the cmdlet throws an exception.</span></span> <span data-ttu-id="ebaf6-117">종료 되지 않는 오류가 발생 하는 경우 cmdlet은 [WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 메서드를 호출 하 여 오류 레코드를 오류 데이터 스트림으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-117">When a non-terminating error occurs, the cmdlet calls the [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method to send an error record to the error data stream.</span></span> <span data-ttu-id="ebaf6-118">오류 보고에 대 한 자세한 내용은 [오류 보고 개념](./error-reporting-concepts.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-118">For more information about error reporting, see [Error Reporting Concepts](./error-reporting-concepts.md).</span></span>

### <a name="verbose-output"></a><span data-ttu-id="ebaf6-119">자세한 정보 출력</span><span class="sxs-lookup"><span data-stu-id="ebaf6-119">Verbose output</span></span>

<span data-ttu-id="ebaf6-120">Cmdlet은 사용자에 게 유용한 정보를 제공할 수 있습니다 .이 cmdlet은 cmdlet이 레코드를 올바르게 처리 하는 동안에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-120">Cmdlets can provide useful information to you while the cmdlet is correctly processing records by calling the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method.</span></span> <span data-ttu-id="ebaf6-121">메서드는 작업을 진행 하는 방법을 나타내는 자세한 정보 메시지를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-121">The method generates verbose messages that indicate how the action is proceeding.</span></span>

<span data-ttu-id="ebaf6-122">기본적으로 자세한 정보 표시 메시지는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-122">By default, verbose messages are not displayed.</span></span> <span data-ttu-id="ebaf6-123">이러한 메시지를 표시 하기 위해 cmdlet을 실행할 때 **Verbose** 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-123">You can specify the **Verbose** parameter when the cmdlet is run to display these messages.</span></span> <span data-ttu-id="ebaf6-124">**Verbose** 는 모든 cmdlet에서 사용할 수 있는 일반 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-124">**Verbose** is a common parameter that is available to all cmdlets.</span></span>

### <a name="progress-output"></a><span data-ttu-id="ebaf6-125">진행률 출력</span><span class="sxs-lookup"><span data-stu-id="ebaf6-125">Progress output</span></span>

<span data-ttu-id="ebaf6-126">Cmdlet은 디렉터리를 재귀적으로 복사 하는 것과 같이 완료 하는 데 시간이 오래 걸리는 작업을 수행할 때 진행률 정보를 사용자에 게 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-126">Cmdlets can provide progress information to you when the cmdlet is performing tasks that take a long time to complete, such as copying a directory recursively.</span></span> <span data-ttu-id="ebaf6-127">진행률 정보를 표시 하기 위해 cmdlet은 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-127">To display progress information the cmdlet calls the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

### <a name="debug-output"></a><span data-ttu-id="ebaf6-128">디버그 출력</span><span class="sxs-lookup"><span data-stu-id="ebaf6-128">Debug output</span></span>

<span data-ttu-id="ebaf6-129">Cmdlet은 cmdlet 코드 문제를 해결할 때 유용한 디버그 메시지를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-129">Cmdlets can provide debug messages that are helpful when troubleshooting the cmdlet code.</span></span> <span data-ttu-id="ebaf6-130">디버그 정보를 표시 하기 위해 cmdlet은 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-130">To display debug information the cmdlet calls the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method.</span></span>

<span data-ttu-id="ebaf6-131">기본적으로 디버그 메시지는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-131">By default, debug messages are not displayed.</span></span> <span data-ttu-id="ebaf6-132">이러한 메시지를 표시 하기 위해 cmdlet을 실행할 때 **Debug** 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-132">You can specify the **Debug** parameter when the cmdlet is run to display these messages.</span></span> <span data-ttu-id="ebaf6-133">**Debug** 는 모든 cmdlet에서 사용할 수 있는 일반 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-133">**Debug** is a common parameter that is available to all cmdlets.</span></span>

### <a name="warning-output"></a><span data-ttu-id="ebaf6-134">경고 출력</span><span class="sxs-lookup"><span data-stu-id="ebaf6-134">Warning output</span></span>

<span data-ttu-id="ebaf6-135">Cmdlet은 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 를 호출 하 여 경고 메시지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-135">Cmdlets can display warning messages by calling the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method.</span></span>

<span data-ttu-id="ebaf6-136">기본적으로 경고 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-136">By default, warning messages are displayed.</span></span> <span data-ttu-id="ebaf6-137">그러나 `$WarningPreference` cmdlet을 호출할 때 변수를 사용 하거나 **Verbose** 및 **Debug** 매개 변수를 사용 하 여 경고 메시지를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-137">However, you can configure warning messages by using the `$WarningPreference` variable or by using the **Verbose** and **Debug** parameters when the cmdlet is called.</span></span>

## <a name="displaying-output"></a><span data-ttu-id="ebaf6-138">출력 표시</span><span class="sxs-lookup"><span data-stu-id="ebaf6-138">Displaying output</span></span>

<span data-ttu-id="ebaf6-139">모든 쓰기 메서드 호출에서 콘텐츠 표시는 특정 런타임 변수에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-139">For all write-method calls, the content display is determined by specific runtime variables.</span></span> <span data-ttu-id="ebaf6-140">단, [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-140">The exception is the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span> <span data-ttu-id="ebaf6-141">이러한 변수를 사용 하 여 코드에서 올바른 위치에 적절 한 쓰기 호출을 수행할 수 있으며, 출력을 표시 해야 하는 경우 나 경우를 걱정 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-141">By using these variables, you can make the appropriate write call at the correct place in your code and not worry about when or if the output should be displayed.</span></span>

## <a name="accessing-the-output-functionality-of-a-host-application"></a><span data-ttu-id="ebaf6-142">호스트 응용 프로그램의 출력 기능에 액세스</span><span class="sxs-lookup"><span data-stu-id="ebaf6-142">Accessing the output functionality of a host application</span></span>

<span data-ttu-id="ebaf6-143">PowerShell 런타임을 통해 호스트 응용 프로그램의 출력 기능에 직접 액세스 하는 cmdlet을 디자인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-143">You can also design a cmdlet to directly access the output functionality of a host application through the PowerShell runtime.</span></span> <span data-ttu-id="ebaf6-144">[Console](/dotnet/api/System.Console) 또는 [system.web](/dotnet/api/System.Windows.Forms) 대신 PowerShell에서 제공 하는 호스트 api를 사용 하면 cmdlet이 다양 한 호스트에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-144">Using the host APIs provided by PowerShell instead of [System.Console](/dotnet/api/System.Console) or [System.Windows.Forms](/dotnet/api/System.Windows.Forms) ensures that your cmdlet will work with a variety of hosts.</span></span> <span data-ttu-id="ebaf6-145">예를 들어, **powershell .exe** 콘솔 호스트, **powershell_ise** 그래픽 호스트, powershell 원격 호스트 및 타사 호스트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaf6-145">For example: the **powershell.exe** console host, the **powershell_ise.exe** graphical host, the PowerShell remoting host, and third-party hosts.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebaf6-146">참조</span><span class="sxs-lookup"><span data-stu-id="ebaf6-146">See also</span></span>

[<span data-ttu-id="ebaf6-147">오류 보고 개념</span><span class="sxs-lookup"><span data-stu-id="ebaf6-147">Error Reporting Concepts</span></span>](./error-reporting-concepts.md)

[<span data-ttu-id="ebaf6-148">Cmdlet 개요</span><span class="sxs-lookup"><span data-stu-id="ebaf6-148">Cmdlet Overview</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="ebaf6-149">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="ebaf6-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

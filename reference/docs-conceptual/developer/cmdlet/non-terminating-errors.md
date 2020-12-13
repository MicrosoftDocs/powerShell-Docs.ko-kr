---
ms.date: 09/13/2016
ms.topic: reference
title: 종료되지 않는 오류
description: 종료되지 않는 오류
ms.openlocfilehash: d23642103e005c6d3a6168b317b11f40001b6bbe
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655745"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="f3906-103">종료되지 않는 오류</span><span class="sxs-lookup"><span data-stu-id="f3906-103">Non-Terminating Errors</span></span>

<span data-ttu-id="f3906-104">이 항목에서는 종료 되지 않는 오류를 보고 하는 데 사용 되는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3906-104">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="f3906-105">또한 cmdlet 내에서 메서드를 호출 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3906-105">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="f3906-106">종료 되지 않는 오류가 발생 하면 cmdlet은 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하 여이 오류를 보고 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3906-106">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="f3906-107">Cmdlet에서 종료 되지 않는 오류를 보고 하는 경우 cmdlet은이 입력 개체와 추가로 들어오는 파이프라인 개체에서 계속 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3906-107">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="f3906-108">Cmdlet이 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하는 경우 cmdlet은 종료 되지 않는 오류를 발생 시킨 조건을 설명 하는 오류 레코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3906-108">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="f3906-109">오류 레코드에 대 한 자세한 내용은 [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f3906-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="f3906-110">Cmdlet은 입력 처리 메서드 내에서 필요에 따라 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3906-110">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="f3906-111">그러나 cmdlet은 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) , [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)또는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 입력 처리 메서드를 호출 하는 [스레드에서만이를](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)호출할 수 있습니다 (예를 들어, cmdlet을 호출 하는 경우에만 해당 됩니다).</span><span class="sxs-lookup"><span data-stu-id="f3906-111">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="f3906-112">다른 스레드에서 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 를 호출 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="f3906-112">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="f3906-113">대신는 주 스레드로 다시 오류를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3906-113">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3906-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3906-114">See Also</span></span>

[<span data-ttu-id="f3906-115">WriteError입니다.</span><span class="sxs-lookup"><span data-stu-id="f3906-115">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="f3906-116">System.object를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3906-116">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="f3906-117">ProcessRecord입니다.</span><span class="sxs-lookup"><span data-stu-id="f3906-117">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="f3906-118">System.object..</span><span class="sxs-lookup"><span data-stu-id="f3906-118">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="f3906-119">Windows PowerShell 오류 레코드</span><span class="sxs-lookup"><span data-stu-id="f3906-119">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

<span data-ttu-id="f3906-120">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="f3906-120">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

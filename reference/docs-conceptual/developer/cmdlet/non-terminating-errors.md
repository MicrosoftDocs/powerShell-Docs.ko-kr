---
title: 종료 되지 않는 오류 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d74c248e6ef54151400b8060d76524e89d87352c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786563"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="fa082-102">종료되지 않는 오류</span><span class="sxs-lookup"><span data-stu-id="fa082-102">Non-Terminating Errors</span></span>

<span data-ttu-id="fa082-103">이 항목에서는 종료 되지 않는 오류를 보고 하는 데 사용 되는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa082-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="fa082-104">또한 cmdlet 내에서 메서드를 호출 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa082-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="fa082-105">종료 되지 않는 오류가 발생 하면 cmdlet은 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하 여이 오류를 보고 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa082-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="fa082-106">Cmdlet에서 종료 되지 않는 오류를 보고 하는 경우 cmdlet은이 입력 개체와 추가로 들어오는 파이프라인 개체에서 계속 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa082-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="fa082-107">Cmdlet이 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하는 경우 cmdlet은 종료 되지 않는 오류를 발생 시킨 조건을 설명 하는 오류 레코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa082-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="fa082-108">오류 레코드에 대 한 자세한 내용은 [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fa082-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="fa082-109">Cmdlet은 입력 처리 메서드 내에서 필요에 따라 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa082-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="fa082-110">그러나 cmdlet은 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) , [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)또는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 입력 처리 메서드를 호출 하는 [스레드에서만이를](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)호출할 수 있습니다 (예를 들어, cmdlet을 호출 하는 경우에만 해당 됩니다).</span><span class="sxs-lookup"><span data-stu-id="fa082-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="fa082-111">다른 스레드에서 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 를 호출 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="fa082-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="fa082-112">대신는 주 스레드로 다시 오류를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa082-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa082-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fa082-113">See Also</span></span>

[<span data-ttu-id="fa082-114">WriteError입니다.</span><span class="sxs-lookup"><span data-stu-id="fa082-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="fa082-115">System.object를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa082-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="fa082-116">ProcessRecord입니다.</span><span class="sxs-lookup"><span data-stu-id="fa082-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="fa082-117">System.object..</span><span class="sxs-lookup"><span data-stu-id="fa082-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="fa082-118">Windows PowerShell 오류 레코드</span><span class="sxs-lookup"><span data-stu-id="fa082-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="fa082-119">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="fa082-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

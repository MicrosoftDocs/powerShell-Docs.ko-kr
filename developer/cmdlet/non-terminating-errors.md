---
title: 비종료 오류 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 9d5c9b16fc5daf3d2f753eeeeedb0db925551a67
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853779"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="831ec-102">종료되지 않는 오류</span><span class="sxs-lookup"><span data-stu-id="831ec-102">Non-Terminating Errors</span></span>

<span data-ttu-id="831ec-103">이 항목에는 종료 되지 않는 오류를 보고 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="831ec-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="831ec-104">또한 cmdlet 내에서 메서드를 호출 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="831ec-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="831ec-105">비종료 오류가 발생 하는 경우 cmdlet을 호출 하 여이 오류를 보고 해야 합니다 [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드.</span><span class="sxs-lookup"><span data-stu-id="831ec-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="831ec-106">Cmdlet은 종료 되지 않는 오류를 보고할 때 cmdlet은 계속 작동할 수 있습니다이 입력된 개체에 추가 들어오는 개체를 파이프라인.</span><span class="sxs-lookup"><span data-stu-id="831ec-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="831ec-107">Cmdlet을 호출 하는 경우는 [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 cmdlet 비종료 오류를 발생 시키는 조건을 설명 하는 오류 레코드를 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="831ec-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="831ec-108">오류 레코드에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="831ec-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="831ec-109">Cmdlet를 호출할 수 있습니다 [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 해당 입력 처리 메서드 내에서 필요한 경우.</span><span class="sxs-lookup"><span data-stu-id="831ec-109">Cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="831ec-110">그러나 cmdlet를 호출할 수 있습니다 [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 호출한 스레드에서만 합니다 [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), 또는 [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 처리 방법을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="831ec-110">However, cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="831ec-111">호출 하지 마세요 [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 다른 스레드에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="831ec-111">Do not call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="831ec-112">대신, 오류를 주 스레드로 다시 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="831ec-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="831ec-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="831ec-113">See Also</span></span>

[<span data-ttu-id="831ec-114">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="831ec-114">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="831ec-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="831ec-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="831ec-116">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="831ec-116">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="831ec-117">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="831ec-117">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="831ec-118">Windows PowerShell 오류 레코드</span><span class="sxs-lookup"><span data-stu-id="831ec-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

<span data-ttu-id="831ec-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="831ec-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

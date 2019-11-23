---
title: GetProc01 (C#) Sample Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 499a688ce5e8daa78baff58c454ad237836bbe48
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416162"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="e605d-102">GetProc01(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="e605d-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="e605d-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e605d-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="e605d-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span><span class="sxs-lookup"><span data-stu-id="e605d-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="e605d-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="e605d-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e605d-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e605d-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="e605d-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span><span class="sxs-lookup"><span data-stu-id="e605d-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e605d-108">Code Sample</span><span class="sxs-lookup"><span data-stu-id="e605d-108">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="e605d-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e605d-109">See Also</span></span>

[<span data-ttu-id="e605d-110">Windows PowerShell Programmer's Guide</span><span class="sxs-lookup"><span data-stu-id="e605d-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e605d-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e605d-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

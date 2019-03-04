---
title: GetProc01 샘플 코드 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 1f11c89f60aef44905cbce3fe669def26119d12e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856069"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="286ea-102">GetProc01(VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="286ea-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="286ea-103">다음 코드는 GetProc01 샘플 cmdlet의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="286ea-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="286ea-104">Cmdlet에 검색 프로세스의 실제 작업을 두어 간단를 확인 합니다 [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) 메서드.</span><span class="sxs-lookup"><span data-stu-id="286ea-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="286ea-105">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 Get-proc cmdlet에 대 한 소스 파일 (getproc01.cs).</span><span class="sxs-lookup"><span data-stu-id="286ea-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="286ea-106">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="286ea-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="286ea-107">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 Get-proc cmdlet에 대 한 소스 파일 (getproc01.cs).</span><span class="sxs-lookup"><span data-stu-id="286ea-107">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="286ea-108">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="286ea-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="286ea-109">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="286ea-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="286ea-110">코드 예제</span><span class="sxs-lookup"><span data-stu-id="286ea-110">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="286ea-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="286ea-111">See Also</span></span>

[<span data-ttu-id="286ea-112">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="286ea-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="286ea-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="286ea-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
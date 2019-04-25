---
title: GetProc04 샘플 코드 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: 0d0d1a3f82bc2cee025139d69fee02eb601fa563
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081529"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="69094-102">GetProc04(VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="69094-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="69094-103">다음 코드의 구현을 보여 줍니다는 `Get-Process` 종료 되지 않는 오류를 보고 하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="69094-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="69094-104">이 구현에서는 호출 된 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 종료 되지 않는 오류를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="69094-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="69094-105">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 Get-proc cmdlet에 대 한 소스 파일 (getprov04.cs).</span><span class="sxs-lookup"><span data-stu-id="69094-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="69094-106">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="69094-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="69094-107">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="69094-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="69094-108">코드 예제</span><span class="sxs-lookup"><span data-stu-id="69094-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="69094-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69094-109">See Also</span></span>

[<span data-ttu-id="69094-110">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="69094-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="69094-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="69094-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
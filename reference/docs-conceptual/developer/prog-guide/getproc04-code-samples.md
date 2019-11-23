---
title: GetProc04 Code Samples | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 8326d1f47ce07698f09ade9ba97154ecc358465a
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417463"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="c8582-102">GetProc04 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="c8582-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="c8582-103">Here are the code samples for the GetProc04 sample cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c8582-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="c8582-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="c8582-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="c8582-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span><span class="sxs-lookup"><span data-stu-id="c8582-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="c8582-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="c8582-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c8582-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c8582-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c8582-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span><span class="sxs-lookup"><span data-stu-id="c8582-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="c8582-109">For complete sample code, see the following topics.</span><span class="sxs-lookup"><span data-stu-id="c8582-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="c8582-110">Language</span><span class="sxs-lookup"><span data-stu-id="c8582-110">Language</span></span>|<span data-ttu-id="c8582-111">항목</span><span class="sxs-lookup"><span data-stu-id="c8582-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="c8582-112">C#</span><span class="sxs-lookup"><span data-stu-id="c8582-112">C#</span></span>|[<span data-ttu-id="c8582-113">GetProc04 (C#) Sample Code</span><span class="sxs-lookup"><span data-stu-id="c8582-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="c8582-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="c8582-114">VB.NET</span></span>|[<span data-ttu-id="c8582-115">GetProc04 (VB.NET) Sample Code</span><span class="sxs-lookup"><span data-stu-id="c8582-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="c8582-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8582-116">See Also</span></span>

[<span data-ttu-id="c8582-117">Windows PowerShell Programmer's Guide</span><span class="sxs-lookup"><span data-stu-id="c8582-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c8582-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c8582-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

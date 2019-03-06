---
title: StopProcessSample04 (C#) 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 778ce1a2-e16d-4af5-b15b-77ca4326bdc4
caps.latest.revision: 5
ms.openlocfilehash: a09efae487dd34238289a6c13dd7786020f15c7d
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429502"
---
# <a name="stopprocesssample04-c-sample-code"></a><span data-ttu-id="37c91-102">StopProcessSample04(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="37c91-102">StopProcessSample04 (C#) Sample Code</span></span>

<span data-ttu-id="37c91-103">전체 다음과 같습니다 C# StopProc04 샘플 cmdlet에 대 한 코드 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="37c91-103">Here is the complete C# sample code for the StopProc04 sample cmdlet.</span></span> <span data-ttu-id="37c91-104">에 대 한 코드는이 `Stop-Process` 에 설명 된 cmdlet [Cmdlet에 매개 변수 집합 추가](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="37c91-104">This is the code for the `Stop-Process` cmdlet described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="37c91-105">합니다 `Stop-Process` cmdlet는 Get-proc cmdlet을 사용 하 여 검색 되는 프로세스를 중지 하도록 설계 되었습니다 (에서 설명한 [첫 번째 Cmdlet 만들기](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="37c91-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="37c91-106">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 중지 Proc cmdlet에 대 한 소스 파일 (stopprocesssample04.cs).</span><span class="sxs-lookup"><span data-stu-id="37c91-106">You can download the C# (stopprocesssample04.cs) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="37c91-107">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="37c91-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="37c91-108">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="37c91-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L11-L435 "StopProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="37c91-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37c91-109">See Also</span></span>

[<span data-ttu-id="37c91-110">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="37c91-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="37c91-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="37c91-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
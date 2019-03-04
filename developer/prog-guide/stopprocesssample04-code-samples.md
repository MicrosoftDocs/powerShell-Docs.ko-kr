---
title: StopProcessSample04 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc68af2b-f622-47c4-964f-b07f3d5bdf14
caps.latest.revision: 5
ms.openlocfilehash: fdb78ac93befba66041c4e45834f8a857e3670b6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862119"
---
# <a name="stopprocesssample04-code-samples"></a><span data-ttu-id="f837b-102">StopProcessSample04 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="f837b-102">StopProcessSample04 Code Samples</span></span>

<span data-ttu-id="f837b-103">StopProc00 샘플 cmdlet에 대 한 코드 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f837b-103">Here are the code samples for the StopProc00 sample cmdlet.</span></span> <span data-ttu-id="f837b-104">이 `Stop-Process` 에 설명 된 cmdlet 샘플 [cmdlet 매개 변수 집합 추가](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="f837b-104">This is the `Stop-Process` cmdlet sample described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="f837b-105">합니다 `Stop-Process` cmdlet는 Get-proc cmdlet을 사용 하 여 검색 되는 프로세스를 중지 하도록 설계 되었습니다 (에서 설명한 [첫 번째 Cmdlet 만들기](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="f837b-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="f837b-106">다운로드할 수 있습니다는 C# (stopprocesssample04.cs) 및 Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 중지 Proc cmdlet에 대 한 VB.NET (stopprocesssample04.vb).</span><span class="sxs-lookup"><span data-stu-id="f837b-106">You can download the C# (stopprocesssample04.cs) and VB.NET (stopprocesssample04.vb) for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f837b-107">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="f837b-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="f837b-108">다운로드할 수 있습니다는 C# (stopprocesssample04.cs) 및 Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 중지 Proc cmdlet에 대 한 VB.NET (stopprocesssample04.vb).</span><span class="sxs-lookup"><span data-stu-id="f837b-108">You can download the C# (stopprocesssample04.cs) and VB.NET (stopprocesssample04.vb) for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f837b-109">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="f837b-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="f837b-110">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="f837b-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="f837b-111">전체 샘플 코드를 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f837b-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="f837b-112">Language</span><span class="sxs-lookup"><span data-stu-id="f837b-112">Language</span></span>|<span data-ttu-id="f837b-113">항목</span><span class="sxs-lookup"><span data-stu-id="f837b-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="f837b-114">C#</span><span class="sxs-lookup"><span data-stu-id="f837b-114">C#</span></span>|[<span data-ttu-id="f837b-115">StopProc04 (C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="f837b-115">StopProc04 (C#) Sample Code</span></span>](./stopprocesssample04-csharp-sample-code.md)|
|<span data-ttu-id="f837b-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="f837b-116">VB.NET</span></span>|[<span data-ttu-id="f837b-117">StopProc04 (VB.NET) 샘플 코드</span><span class="sxs-lookup"><span data-stu-id="f837b-117">StopProc04 (VB.NET) Sample Code</span></span>](./stopprocesssample04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="f837b-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f837b-118">See Also</span></span>

[<span data-ttu-id="f837b-119">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="f837b-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f837b-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f837b-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
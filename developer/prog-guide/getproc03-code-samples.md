---
title: GetProc03 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad39c7d-2f64-49d1-9be0-d2295e4302b3
caps.latest.revision: 5
ms.openlocfilehash: 8cb02b9f2510b90f405651deaf551e9622f5a298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857309"
---
# <a name="getproc03-code-samples"></a><span data-ttu-id="312f3-102">GetProc03 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="312f3-102">GetProc03 Code Samples</span></span>

<span data-ttu-id="312f3-103">GetProc03 샘플 cmdlet에 대 한 코드 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="312f3-103">Here are the code samples for the GetProc03 sample cmdlet.</span></span> <span data-ttu-id="312f3-104">이 `Get-Process` 에서 설명 된 cmdlet 샘플 [해당 프로세스 파이프라인 입력 매개 변수를 추가](../cmdlet/adding-parameters-that-process-pipeline-input.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="312f3-104">This is the `Get-Process` cmdlet sample described in [Adding Parameters that Process Pipeline Input](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="312f3-105">이 `Get-Process` cmdlet을 사용 하는 `Name` 파이프라인 개체의 입력을 허용 하는 매개 변수는 제공 된 이름을 기반으로 하는 로컬 컴퓨터에서 프로세스 정보를 검색 하 고 다음 명령줄은 프로세스에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="312f3-105">This `Get-Process` cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="312f3-106">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 Get-proc cmdlet에 대 한 소스 파일 (getprov03.cs).</span><span class="sxs-lookup"><span data-stu-id="312f3-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="312f3-107">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="312f3-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="312f3-108">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 Get-proc cmdlet에 대 한 소스 파일 (getprov03.cs).</span><span class="sxs-lookup"><span data-stu-id="312f3-108">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="312f3-109">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="312f3-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="312f3-110">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="312f3-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="312f3-111">전체 샘플 코드를 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="312f3-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="312f3-112">Language</span><span class="sxs-lookup"><span data-stu-id="312f3-112">Language</span></span>|<span data-ttu-id="312f3-113">항목</span><span class="sxs-lookup"><span data-stu-id="312f3-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="312f3-114">C#</span><span class="sxs-lookup"><span data-stu-id="312f3-114">C#</span></span>|[<span data-ttu-id="312f3-115">GetProc03 (C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="312f3-115">GetProc03 (C#) Sample Code</span></span>](./getproc03-csharp-sample-code.md)|
|<span data-ttu-id="312f3-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="312f3-116">VB.NET</span></span>|[<span data-ttu-id="312f3-117">GetProc03 (VB.NET) 샘플 코드</span><span class="sxs-lookup"><span data-stu-id="312f3-117">GetProc03 (VB.NET) Sample Code</span></span>](./getproc03-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="312f3-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="312f3-118">See Also</span></span>

[<span data-ttu-id="312f3-119">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="312f3-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="312f3-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="312f3-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
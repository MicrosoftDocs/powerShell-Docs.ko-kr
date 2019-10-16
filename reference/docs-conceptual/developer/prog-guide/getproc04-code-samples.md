---
title: GetProc04 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360322"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="518a7-102">GetProc04 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="518a7-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="518a7-103">GetProc04 sample cmdlet에 대 한 코드 샘플은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="518a7-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="518a7-104">이는 Cmdlet에 종료 되지 않은 [오류 보고 추가](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)에 설명 된 `Get-Process` cmdlet 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="518a7-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="518a7-105">이 `Get-Process` cmdlet은 프로세스 정보를 검색 하는 동안 잘못 된 작업 예외가 throw 될 때마다 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="518a7-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="518a7-106">Windows Vista 용 Microsoft C# Windows 소프트웨어 개발 키트 및 .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 getprov04.cs cmdlet에 대 한 원본 파일 ()을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="518a7-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="518a7-107">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="518a7-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="518a7-108">다운로드 된 원본 파일은 **\<PowerShell 샘플 >** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="518a7-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="518a7-109">전체 샘플 코드는 다음 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="518a7-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="518a7-110">Language</span><span class="sxs-lookup"><span data-stu-id="518a7-110">Language</span></span>|<span data-ttu-id="518a7-111">항목</span><span class="sxs-lookup"><span data-stu-id="518a7-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="518a7-112">C#</span><span class="sxs-lookup"><span data-stu-id="518a7-112">C#</span></span>|[<span data-ttu-id="518a7-113">GetProc04 (C#) 샘플 코드</span><span class="sxs-lookup"><span data-stu-id="518a7-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="518a7-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="518a7-114">VB.NET</span></span>|[<span data-ttu-id="518a7-115">GetProc04 (VB.NET) 샘플 코드</span><span class="sxs-lookup"><span data-stu-id="518a7-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="518a7-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="518a7-116">See Also</span></span>

[<span data-ttu-id="518a7-117">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="518a7-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="518a7-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="518a7-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
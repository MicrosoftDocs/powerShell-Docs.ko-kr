---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc04 코드 샘플
description: GetProc04 코드 샘플
ms.openlocfilehash: db94eda2b3aa5fc88a3054df66f54628e1482f56
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659247"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="5efad-103">GetProc04 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="5efad-103">GetProc04 Code Samples</span></span>

<span data-ttu-id="5efad-104">GetProc04 sample cmdlet에 대 한 코드 샘플은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5efad-104">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="5efad-105">Cmdlet에 종료 되지 않는 `Get-Process` [오류 보고 추가](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)에 설명 된 cmdlet 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="5efad-105">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="5efad-106">이 `Get-Process` cmdlet은 프로세스 정보를 검색 하는 동안 잘못 된 작업 예외가 throw 될 때마다 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="5efad-106">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="5efad-107">Windows Vista 용 Microsoft Windows 소프트웨어 개발 키트 및 .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 Get-Proc cmdlet에 대 한 c # 소스 파일 (getprov04.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5efad-107">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5efad-108">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5efad-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="5efad-109">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="5efad-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="5efad-110">전체 샘플 코드는 다음 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5efad-110">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="5efad-111">언어</span><span class="sxs-lookup"><span data-stu-id="5efad-111">Language</span></span>|<span data-ttu-id="5efad-112">항목</span><span class="sxs-lookup"><span data-stu-id="5efad-112">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="5efad-113">C#</span><span class="sxs-lookup"><span data-stu-id="5efad-113">C#</span></span>|[<span data-ttu-id="5efad-114">GetProc04(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="5efad-114">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="5efad-115">VB.NET</span><span class="sxs-lookup"><span data-stu-id="5efad-115">VB.NET</span></span>|[<span data-ttu-id="5efad-116">GetProc04(VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="5efad-116">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="5efad-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5efad-117">See Also</span></span>

[<span data-ttu-id="5efad-118">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="5efad-118">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5efad-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5efad-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

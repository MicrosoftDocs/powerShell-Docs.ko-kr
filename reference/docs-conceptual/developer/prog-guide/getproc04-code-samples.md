---
title: GetProc04 코드 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b90b7e96c1454e57df93863b526758f25d9be690
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771960"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="370d0-102">GetProc04 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="370d0-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="370d0-103">GetProc04 sample cmdlet에 대 한 코드 샘플은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="370d0-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="370d0-104">Cmdlet에 종료 되지 않는 `Get-Process` [오류 보고 추가](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)에 설명 된 cmdlet 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="370d0-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="370d0-105">이 `Get-Process` cmdlet은 프로세스 정보를 검색 하는 동안 잘못 된 작업 예외가 throw 될 때마다 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="370d0-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="370d0-106">Windows Vista 및 .NET Framework 3.0 런타임 구성 요소에 대 한 Microsoft Windows 소프트웨어 개발 키트를 사용 하 여이 getprov04.cs cmdlet에 대 한 c # 소스 파일 ()을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="370d0-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="370d0-107">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="370d0-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="370d0-108">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="370d0-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="370d0-109">전체 샘플 코드는 다음 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="370d0-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="370d0-110">언어</span><span class="sxs-lookup"><span data-stu-id="370d0-110">Language</span></span>|<span data-ttu-id="370d0-111">항목</span><span class="sxs-lookup"><span data-stu-id="370d0-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="370d0-112">C#</span><span class="sxs-lookup"><span data-stu-id="370d0-112">C#</span></span>|[<span data-ttu-id="370d0-113">GetProc04(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="370d0-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="370d0-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="370d0-114">VB.NET</span></span>|[<span data-ttu-id="370d0-115">GetProc04(VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="370d0-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="370d0-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="370d0-116">See Also</span></span>

[<span data-ttu-id="370d0-117">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="370d0-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="370d0-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="370d0-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

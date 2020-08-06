---
title: GetProc04 (VB.NET) 샘플 코드 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 63fbbb2d6bef4634bf72d4b0f9e429de9ed9deca
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771875"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="ca4f5-102">GetProc04(VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="ca4f5-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="ca4f5-103">다음 코드에서는 `Get-Process` 종료 되지 않는 오류를 보고 하는 cmdlet의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ca4f5-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="ca4f5-104">이 구현은 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하 여 종료 되지 않는 오류를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca4f5-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="ca4f5-105">Windows Vista 및 .NET Framework 3.0 런타임 구성 요소에 대 한 Microsoft Windows 소프트웨어 개발 키트를 사용 하 여이 getprov04.cs cmdlet에 대 한 c # 소스 파일 ()을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca4f5-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ca4f5-106">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ca4f5-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="ca4f5-107">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="ca4f5-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ca4f5-108">코드 예제</span><span class="sxs-lookup"><span data-stu-id="ca4f5-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="ca4f5-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca4f5-109">See Also</span></span>

[<span data-ttu-id="ca4f5-110">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="ca4f5-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ca4f5-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ca4f5-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

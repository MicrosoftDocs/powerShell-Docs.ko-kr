---
title: RunSpace04 코드 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9a9b7e02358cdf9018199046c938c699aff8681c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787071"
---
# <a name="runspace04-code-samples"></a><span data-ttu-id="d9222-102">RunSpace04 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="d9222-102">RunSpace04 Code Samples</span></span>

<span data-ttu-id="d9222-103">다음은 종료 오류를 생성 하는 스크립트를 실행 하기 위해 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 클래스를 사용 하는 runspace에 대 한 코드 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="d9222-103">Here is a code sample for a runspace that uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="d9222-104">호스트 응용 프로그램은 오류를 catch 하 고 오류 레코드를 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9222-104">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="d9222-105">Windows Vista 용 Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 runspace에 대 한 VB.NET 원본 파일 (Runspace04)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9222-105">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d9222-106">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9222-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="d9222-107">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="d9222-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="d9222-108">전체 샘플 코드는 다음 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9222-108">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="d9222-109">언어</span><span class="sxs-lookup"><span data-stu-id="d9222-109">Language</span></span>|<span data-ttu-id="d9222-110">항목</span><span class="sxs-lookup"><span data-stu-id="d9222-110">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="d9222-111">VB.NET</span><span class="sxs-lookup"><span data-stu-id="d9222-111">VB.NET</span></span>|[<span data-ttu-id="d9222-112">Runspace01(VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="d9222-112">Runspace01 (VB.NET) Code Sample</span></span>](./runspace01-vb-net-code-sample.md)|

## <a name="see-also"></a><span data-ttu-id="d9222-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9222-113">See Also</span></span>

[<span data-ttu-id="d9222-114">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="d9222-114">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d9222-115">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d9222-115">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

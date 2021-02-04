---
ms.date: 01/04/2021
ms.topic: reference
title: RunSpace04 코드 샘플
description: RunSpace04 코드 샘플
ms.openlocfilehash: 6d2ff551b985046df493cf00fac0d25e94df423e
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879323"
---
# <a name="runspace04-code-samples"></a><span data-ttu-id="a3434-103">RunSpace04 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="a3434-103">RunSpace04 Code Samples</span></span>

<span data-ttu-id="a3434-104">다음은 종료 오류를 생성 하는 스크립트를 실행 하기 위해 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 클래스를 사용 하는 runspace에 대 한 코드 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="a3434-104">Here is a code sample for a runspace that uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="a3434-105">호스트 응용 프로그램은 오류를 catch 하 고 오류 레코드를 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3434-105">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="a3434-106">Windows Vista 용 Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 runspace에 대 한 VB.NET 원본 파일 (Runspace04)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3434-106">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span>
> <span data-ttu-id="a3434-107">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3434-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="a3434-108">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="a3434-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="a3434-109">전체 샘플 코드는 다음 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3434-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="a3434-110">언어</span><span class="sxs-lookup"><span data-stu-id="a3434-110">Language</span></span>|<span data-ttu-id="a3434-111">항목</span><span class="sxs-lookup"><span data-stu-id="a3434-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="a3434-112">VB.NET</span><span class="sxs-lookup"><span data-stu-id="a3434-112">VB.NET</span></span>|[<span data-ttu-id="a3434-113">Runspace04 (VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="a3434-113">Runspace04 (VB.NET) Code Sample</span></span>](./runspace04-vb-net-code-sample.md)|

## <a name="see-also"></a><span data-ttu-id="a3434-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a3434-114">See Also</span></span>

[<span data-ttu-id="a3434-115">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="a3434-115">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="a3434-116">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a3434-116">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

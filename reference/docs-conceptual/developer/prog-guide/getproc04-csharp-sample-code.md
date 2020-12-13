---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc04(C#) 코드 샘플
description: GetProc04(C#) 코드 샘플
ms.openlocfilehash: 80020b60a7ab34caec0c856b9b7d12021f4276b9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654379"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="639cc-103">GetProc04(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="639cc-103">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="639cc-104">다음 코드에서는 `Get-Process` 종료 되지 않는 오류를 보고 하는 cmdlet의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="639cc-104">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="639cc-105">이 구현은 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하 여 종료 되지 않는 오류를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="639cc-105">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="639cc-106">Windows Vista 용 Microsoft Windows 소프트웨어 개발 키트 및 .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 Get-Proc cmdlet에 대 한 c # 소스 파일 (getprov04.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="639cc-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="639cc-107">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="639cc-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="639cc-108">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="639cc-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="639cc-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="639cc-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs" range="11-98":::

## <a name="see-also"></a><span data-ttu-id="639cc-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="639cc-110">See Also</span></span>

[<span data-ttu-id="639cc-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="639cc-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="639cc-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="639cc-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

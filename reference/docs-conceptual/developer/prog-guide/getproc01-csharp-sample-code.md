---
title: 'GetProc01 (c #) 샘플 코드 | Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: 883beb9dd1328a1897b9b61656a98cf515a21be7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778887"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="9b4e5-102">GetProc01(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="9b4e5-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="9b4e5-103">다음 코드는 GetProc01 sample cmdlet의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9b4e5-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="9b4e5-104">프로세스 검색의 실제 작업을 사용 하 여 cmdlet을 간소화 하는 것을 알 수 [있습니다.](/dotnet/api/System.Diagnostics.Process.GetProcesses)</span><span class="sxs-lookup"><span data-stu-id="9b4e5-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="9b4e5-105">Windows Vista 및 .NET Framework 3.0 런타임 구성 요소에 대 한 Microsoft Windows 소프트웨어 개발 키트를 사용 하 여이 getproc01.cs cmdlet에 대 한 c # 소스 파일 ()을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b4e5-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9b4e5-106">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9b4e5-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="9b4e5-107">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="9b4e5-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9b4e5-108">코드 예제</span><span class="sxs-lookup"><span data-stu-id="9b4e5-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a><span data-ttu-id="9b4e5-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b4e5-109">See Also</span></span>

[<span data-ttu-id="9b4e5-110">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="9b4e5-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9b4e5-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9b4e5-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

---
title: GetProc01 (C#) 샘플 코드 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 71ba68521ed8d26d0c85169d2b0d547cc6d2d5e3
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978426"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="5acd0-102">GetProc01(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="5acd0-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="5acd0-103">다음 코드는 GetProc01 sample cmdlet의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5acd0-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="5acd0-104">프로세스 검색의 실제 작업을 사용 하 여 cmdlet을 간소화 하는 것을 알 수 [있습니다.](/dotnet/api/System.Diagnostics.Process.GetProcesses)</span><span class="sxs-lookup"><span data-stu-id="5acd0-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="5acd0-105">Windows Vista 용 Microsoft C# Windows 소프트웨어 개발 키트 및 .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 getproc01.cs cmdlet에 대 한 원본 파일 ()을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5acd0-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5acd0-106">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5acd0-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="5acd0-107">다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5acd0-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5acd0-108">코드 예제</span><span class="sxs-lookup"><span data-stu-id="5acd0-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a><span data-ttu-id="5acd0-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5acd0-109">See Also</span></span>

[<span data-ttu-id="5acd0-110">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="5acd0-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5acd0-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5acd0-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

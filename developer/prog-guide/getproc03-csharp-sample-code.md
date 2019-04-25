---
title: GetProc03 (C#) 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 4d921dd62999bc68b80838bafa2a3da8d4df3ebb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081521"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="a9e43-102">GetProc03(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="a9e43-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="a9e43-103">다음 코드의 구현을 보여 줍니다는 `Get-Process` 받아들일 수 있는 cmdlet은 파이프라인 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e43-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="a9e43-104">이 구현에서 정의 된 `Name` 파이프라인 입력을 허용 하는 매개 변수는 제공 된 이름을 기반으로 로컬 컴퓨터에서 프로세스 정보를 검색 하 고 사용 하 여는 [System.Management.Automation.Cmdlet.WriteObject% 28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) 메서드 개체를 파이프라인으로 보내기 위한 출력 메커니즘으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e43-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="a9e43-105">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 Get-proc cmdlet에 대 한 소스 파일 (getprov03.cs).</span><span class="sxs-lookup"><span data-stu-id="a9e43-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="a9e43-106">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e43-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="a9e43-107">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="a9e43-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a9e43-108">코드 예제</span><span class="sxs-lookup"><span data-stu-id="a9e43-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="a9e43-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a9e43-109">See Also</span></span>

[<span data-ttu-id="a9e43-110">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="a9e43-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="a9e43-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a9e43-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
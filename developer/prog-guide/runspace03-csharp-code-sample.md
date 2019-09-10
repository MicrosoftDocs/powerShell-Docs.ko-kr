---
title: RunSpace03 (C#) 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848033"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="2e2ad-102">RunSpace03(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="2e2ad-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="2e2ad-103">다음은 " C# 지정 된 스크립트를 실행 하는 콘솔 응용 프로그램 만들기"에 설명 된 콘솔 응용 프로그램의 소스 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="2e2ad-103">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="2e2ad-104">이 샘플에서는 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 클래스를 사용 하 여 스크립트에 전달 된 프로세스 이름 목록을 사용 하 여 프로세스 정보를 검색 하는 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2ad-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="2e2ad-105">입력 개체를 스크립트에 전달 하는 방법 및 출력 개체 뿐만 아니라 오류 개체를 검색 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2e2ad-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="2e2ad-106">Windows Vista 용 Microsoft C# Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 샘플에 대 한 소스 파일 (runspace03.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e2ad-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2e2ad-107">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2e2ad-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="2e2ad-108">다운로드 된 원본 파일은  **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e2ad-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="2e2ad-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="2e2ad-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="2e2ad-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e2ad-110">See Also</span></span>

[<span data-ttu-id="2e2ad-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="2e2ad-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2e2ad-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2e2ad-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
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
ms.openlocfilehash: 0e80f4d850a7c6dc044526a56b92f16eea4040b5
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429910"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="1a5ae-102">RunSpace03(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="1a5ae-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="1a5ae-103">다음은 C# 에 설명 된 콘솔 응용 프로그램의 소스 코드 [콘솔 응용 프로그램을 실행은 지정 된 스크립트를 만드는](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span><span class="sxs-lookup"><span data-stu-id="1a5ae-103">Here is the C# source code for the console application described in [Creating a Console Application That Runs a Specified Script](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span></span> <span data-ttu-id="1a5ae-104">이 샘플에서는 합니다 [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 검색 스크립트에 전달 하는 프로세스 이름 목록을 사용 하 여 정보를 처리 하는 스크립트를 실행 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="1a5ae-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="1a5ae-105">스크립트에 입력된 개체를 전달 하는 방법 및 출력 개체 뿐만 아니라 오류 개체를 검색 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1a5ae-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="1a5ae-106">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및 Microsoft.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 샘플에 대 한 원본 파일 (runspace03.cs).</span><span class="sxs-lookup"><span data-stu-id="1a5ae-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1a5ae-107">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="1a5ae-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="1a5ae-108">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="1a5ae-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1a5ae-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="1a5ae-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="1a5ae-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a5ae-110">See Also</span></span>

[<span data-ttu-id="1a5ae-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="1a5ae-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1a5ae-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1a5ae-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
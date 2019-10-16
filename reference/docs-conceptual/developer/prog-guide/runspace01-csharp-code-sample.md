---
title: Runspace01 (C#) 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 39e7d49b51942da51a581ab33dbe46ab848ca1c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366642"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="9187c-102">Runspace01(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="9187c-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="9187c-103">다음은 [지정 된 명령을 실행 하는 콘솔 응용 프로그램 만들기](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)에서 설명 하는 runspace에 대 한 코드 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="9187c-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="9187c-104">이렇게 하기 위해 응용 프로그램은 runspace를 호출한 다음 명령을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9187c-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="9187c-105">이 응용 프로그램은 runspace 구성 정보를 지정 하지 않으며 파이프라인을 명시적으로 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9187c-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="9187c-106">호출 되는 명령은 `Get-Process` cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="9187c-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="9187c-107">Windows Vista 용 Microsoft C# Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 runspace에 대 한 소스 파일 (runspace01.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9187c-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9187c-108">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9187c-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="9187c-109">다운로드 된 원본 파일은 **\<PowerShell 샘플 >** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9187c-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9187c-110">코드 샘플</span><span class="sxs-lookup"><span data-stu-id="9187c-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="9187c-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9187c-111">See Also</span></span>

[<span data-ttu-id="9187c-112">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="9187c-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9187c-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9187c-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

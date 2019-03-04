---
title: RunSpace07 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 3e016b0e98234797afc8f303a55919228eaf8829
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857929"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="eb08d-102">RunSpace07 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="eb08d-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="eb08d-103">설명 된 Runspace07 샘플에 대 한 소스 코드를 다음과 같습니다 [는 콘솔 응용 프로그램을 추가 명령 파이프라인에 만드는](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e)합니다.</span><span class="sxs-lookup"><span data-stu-id="eb08d-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="eb08d-104">이 샘플 응용 프로그램 runspace를 만들고, 파이프라인을 만듭니다, 그리고 파이프라인에 두 개의 명령을 추가 및 다음 파이프라인을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb08d-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="eb08d-105">명령 파이프라인에 추가 되는 `Get-Process` 고 `Measure-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb08d-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="eb08d-106">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및 Microsoft.NET Framework 3.0 런타임 구성 요소를 사용 하 여 원본 파일 (runspace07.cs).</span><span class="sxs-lookup"><span data-stu-id="eb08d-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="eb08d-107">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="eb08d-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="eb08d-108">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및 Microsoft.NET Framework 3.0 런타임 구성 요소를 사용 하 여 원본 파일 (runspace07.cs).</span><span class="sxs-lookup"><span data-stu-id="eb08d-108">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="eb08d-109">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="eb08d-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="eb08d-110">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="eb08d-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="eb08d-111">코드 예제</span><span class="sxs-lookup"><span data-stu-id="eb08d-111">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="eb08d-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eb08d-112">See Also</span></span>

[<span data-ttu-id="eb08d-113">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="eb08d-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="eb08d-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="eb08d-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
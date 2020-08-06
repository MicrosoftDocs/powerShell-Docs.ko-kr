---
title: RunSpace07 코드 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 615bb237d26bf3a314ea7fb21e983ba2b000d105
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784710"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="60c0f-102">RunSpace07 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="60c0f-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="60c0f-103">[파이프라인에 명령을 추가 하는 콘솔 응용 프로그램 만들기](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e)에서 설명한 Runspace07 샘플의 소스 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="60c0f-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span>
<span data-ttu-id="60c0f-104">이 샘플 응용 프로그램은 runspace를 만들고, 파이프라인을 만들고, 파이프라인에 두 개의 명령을 추가한 후 파이프라인을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="60c0f-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="60c0f-105">파이프라인에 추가 되는 명령은 `Get-Process` 및 `Measure-Object` cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="60c0f-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="60c0f-106">Windows Vista 용 Microsoft Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여 c # 소스 파일 (runspace07.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60c0f-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="60c0f-107">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60c0f-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="60c0f-108">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="60c0f-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="60c0f-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="60c0f-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs" range="11-108":::

## <a name="see-also"></a><span data-ttu-id="60c0f-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="60c0f-110">See Also</span></span>

[<span data-ttu-id="60c0f-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="60c0f-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="60c0f-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="60c0f-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

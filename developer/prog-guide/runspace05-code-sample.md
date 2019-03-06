---
title: RunSpace05 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: b16ee45383059c52ce3433699c6b8d2120992431
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429570"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="1c8d5-102">RunSpace05 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="1c8d5-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="1c8d5-103">여기에 설명 된 Runspace05 샘플에 대 한 소스 코드를입니다 [Runspace를 사용 하 여 RunspaceConfiguration 구성](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2)합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8d5-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="1c8d5-104">이 샘플 runspace 구성 정보를 runspace, 단일 명령으로 파이프라인을 만들 만들고 파이프라인을 실행 한 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1c8d5-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="1c8d5-105">실행 되는 명령입니다는 `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c8d5-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="1c8d5-106">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및 Microsoft.NET Framework 3.0 런타임 구성 요소를 사용 하 여 원본 파일 (runspace05.cs).</span><span class="sxs-lookup"><span data-stu-id="1c8d5-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1c8d5-107">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8d5-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="1c8d5-108">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="1c8d5-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1c8d5-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="1c8d5-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="1c8d5-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1c8d5-110">See Also</span></span>

[<span data-ttu-id="1c8d5-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="1c8d5-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1c8d5-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1c8d5-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
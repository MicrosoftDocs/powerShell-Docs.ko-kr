---
title: RunSpace06 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: c3ae45ae9587bd130bbe9bb65ef47dc246f6e465
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417908"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="36b60-102">RunSpace06 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="36b60-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="36b60-103">[Windows PowerShell 스냅인을 사용 하 여 Runspace 구성](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83)에 설명 된 Runspace06 샘플의 소스 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="36b60-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="36b60-104">이 샘플 응용 프로그램은 단일 명령을 사용 하 여 파이프라인을 실행 하는 데 사용 되는 Windows PowerShell 스냅인을 기반으로 runspace를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="36b60-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="36b60-105">이렇게 하기 위해 응용 프로그램은 runspace 구성 정보를 만들고, runspace를 만들고, 단일 명령을 사용 하 여 파이프라인을 만든 다음, 파이프라인을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="36b60-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="36b60-106">Windows Vista 용 Windows C# 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여 원본 파일 (runspace06.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36b60-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="36b60-107">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36b60-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="36b60-108">다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36b60-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="36b60-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="36b60-109">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="36b60-110">관련 항목</span><span class="sxs-lookup"><span data-stu-id="36b60-110">See Also</span></span>

[<span data-ttu-id="36b60-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="36b60-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="36b60-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="36b60-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace06 코드 샘플
description: RunSpace06 코드 샘플
ms.openlocfilehash: 627fa2be51721dd8bfdd63fabdd2e6f286d593be
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667483"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="1244c-103">RunSpace06 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="1244c-103">RunSpace06 Code Sample</span></span>

<span data-ttu-id="1244c-104">[Windows PowerShell 스냅인을 사용 하 여 Runspace 구성](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83)에 설명 된 Runspace06 샘플의 소스 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1244c-104">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span>
<span data-ttu-id="1244c-105">이 샘플 응용 프로그램은 단일 명령을 사용 하 여 파이프라인을 실행 하는 데 사용 되는 Windows PowerShell 스냅인을 기반으로 runspace를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1244c-105">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="1244c-106">이렇게 하기 위해 응용 프로그램은 runspace 구성 정보를 만들고, runspace를 만들고, 단일 명령을 사용 하 여 파이프라인을 만든 다음, 파이프라인을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1244c-106">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="1244c-107">Windows Vista 용 Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여 c # 소스 파일 (runspace06.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1244c-107">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1244c-108">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1244c-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="1244c-109">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="1244c-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1244c-110">코드 예제</span><span class="sxs-lookup"><span data-stu-id="1244c-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs" range="11-85":::

## <a name="see-also"></a><span data-ttu-id="1244c-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1244c-111">See Also</span></span>

[<span data-ttu-id="1244c-112">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="1244c-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1244c-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1244c-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

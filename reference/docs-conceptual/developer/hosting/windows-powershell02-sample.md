---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell02 샘플
description: Windows PowerShell02 샘플
ms.openlocfilehash: 61dedd72d93d4000edf9a12f12bbb49fbaeb9f3c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657364"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="1ae14-103">Windows PowerShell02 샘플</span><span class="sxs-lookup"><span data-stu-id="1ae14-103">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="1ae14-104">이 샘플에서는 runspace 풀의 runspace을 사용 하 여 비동기적으로 명령을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1ae14-104">This sample shows how to run commands asynchronously using the runspaces of a runspace pool.</span></span> <span data-ttu-id="1ae14-105">이 샘플에서는 명령 목록을 생성 한 다음, Windows PowerShell 엔진이 필요할 때 풀에서 runspace를 열 때 해당 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae14-105">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="1ae14-106">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1ae14-106">Requirements</span></span>

- <span data-ttu-id="1ae14-107">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae14-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="1ae14-108">데모</span><span class="sxs-lookup"><span data-stu-id="1ae14-108">Demonstrates</span></span>

<span data-ttu-id="1ae14-109">이 샘플은 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1ae14-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="1ae14-110">최소 및 최대 runspace 수를 사용 하 여 RunspacePool 개체를 만들고 동시에 열 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae14-110">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>
- <span data-ttu-id="1ae14-111">명령 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1ae14-111">Creating a list of commands.</span></span>
- <span data-ttu-id="1ae14-112">비동기적으로 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae14-112">Running the commands asynchronously.</span></span>
- <span data-ttu-id="1ae14-113">[Runspace Runspacepool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) 메서드를 호출 하 여 사용 가능한 runspace의 수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae14-113">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>
- <span data-ttu-id="1ae14-114">[System.object](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) 를 사용 하 여 명령 출력을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae14-114">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="1ae14-115">예제</span><span class="sxs-lookup"><span data-stu-id="1ae14-115">Example</span></span>

<span data-ttu-id="1ae14-116">이 샘플에서는 runspace 풀의 runspace를 여는 방법과 이러한 runspace에서 비동기적으로 명령을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1ae14-116">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a><span data-ttu-id="1ae14-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ae14-117">See Also</span></span>

[<span data-ttu-id="1ae14-118">Windows PowerShell 호스트 애플리케이션 작성</span><span class="sxs-lookup"><span data-stu-id="1ae14-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)

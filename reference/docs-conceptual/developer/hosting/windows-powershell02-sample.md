---
title: Windows PowerShell02 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 4d697e73ff4ab4cc4b88593f814d589f89005663
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978647"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="b3bf9-102">Windows PowerShell02 샘플</span><span class="sxs-lookup"><span data-stu-id="b3bf9-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="b3bf9-103">이 샘플에서는 runspace 풀의 runspace을 사용 하 여 비동기적으로 명령을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3bf9-103">This sample shows how to run commands asynchronously using the runspaces of a runspace pool.</span></span> <span data-ttu-id="b3bf9-104">이 샘플에서는 명령 목록을 생성 한 다음, Windows PowerShell 엔진이 필요할 때 풀에서 runspace를 열 때 해당 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3bf9-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="b3bf9-105">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b3bf9-105">Requirements</span></span>

- <span data-ttu-id="b3bf9-106">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3bf9-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b3bf9-107">데모</span><span class="sxs-lookup"><span data-stu-id="b3bf9-107">Demonstrates</span></span>

<span data-ttu-id="b3bf9-108">이 샘플은 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3bf9-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="b3bf9-109">최소 및 최대 runspace 수를 사용 하 여 RunspacePool 개체를 만들고 동시에 열 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3bf9-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>
- <span data-ttu-id="b3bf9-110">명령 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3bf9-110">Creating a list of commands.</span></span>
- <span data-ttu-id="b3bf9-111">비동기적으로 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3bf9-111">Running the commands asynchronously.</span></span>
- <span data-ttu-id="b3bf9-112">[Runspace Runspacepool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) 메서드를 호출 하 여 사용 가능한 runspace의 수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3bf9-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>
- <span data-ttu-id="b3bf9-113">[System.object](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) 를 사용 하 여 명령 출력을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="b3bf9-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="b3bf9-114">예제</span><span class="sxs-lookup"><span data-stu-id="b3bf9-114">Example</span></span>

<span data-ttu-id="b3bf9-115">이 샘플에서는 runspace 풀의 runspace를 여는 방법과 이러한 runspace에서 비동기적으로 명령을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3bf9-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a><span data-ttu-id="b3bf9-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3bf9-116">See Also</span></span>

[<span data-ttu-id="b3bf9-117">Windows PowerShell 호스트 응용 프로그램 작성</span><span class="sxs-lookup"><span data-stu-id="b3bf9-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)

---
title: Windows PowerShell02 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a82366a88addb08e186eede79e621d90d915c50f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779389"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="f31ae-102">Windows PowerShell02 샘플</span><span class="sxs-lookup"><span data-stu-id="f31ae-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="f31ae-103">이 샘플에서는 runspace 풀의 runspace을 사용 하 여 비동기적으로 명령을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f31ae-103">This sample shows how to run commands asynchronously using the runspaces of a runspace pool.</span></span> <span data-ttu-id="f31ae-104">이 샘플에서는 명령 목록을 생성 한 다음, Windows PowerShell 엔진이 필요할 때 풀에서 runspace를 열 때 해당 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31ae-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="f31ae-105">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f31ae-105">Requirements</span></span>

- <span data-ttu-id="f31ae-106">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31ae-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f31ae-107">데모</span><span class="sxs-lookup"><span data-stu-id="f31ae-107">Demonstrates</span></span>

<span data-ttu-id="f31ae-108">이 샘플은 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f31ae-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="f31ae-109">최소 및 최대 runspace 수를 사용 하 여 RunspacePool 개체를 만들고 동시에 열 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31ae-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>
- <span data-ttu-id="f31ae-110">명령 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f31ae-110">Creating a list of commands.</span></span>
- <span data-ttu-id="f31ae-111">비동기적으로 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31ae-111">Running the commands asynchronously.</span></span>
- <span data-ttu-id="f31ae-112">[Runspace Runspacepool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) 메서드를 호출 하 여 사용 가능한 runspace의 수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31ae-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>
- <span data-ttu-id="f31ae-113">[System.object](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) 를 사용 하 여 명령 출력을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="f31ae-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="f31ae-114">예제</span><span class="sxs-lookup"><span data-stu-id="f31ae-114">Example</span></span>

<span data-ttu-id="f31ae-115">이 샘플에서는 runspace 풀의 runspace를 여는 방법과 이러한 runspace에서 비동기적으로 명령을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f31ae-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a><span data-ttu-id="f31ae-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f31ae-116">See Also</span></span>

[<span data-ttu-id="f31ae-117">Windows PowerShell 호스트 애플리케이션 작성</span><span class="sxs-lookup"><span data-stu-id="f31ae-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)

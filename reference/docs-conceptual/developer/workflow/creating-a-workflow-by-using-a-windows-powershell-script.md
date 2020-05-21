---
title: Windows PowerShell 스크립트를 사용 하 여 워크플로 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: cc613240e056e8443b075019cbff6dd15da3716f
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557451"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="dc5f6-102">Windows PowerShell 스크립트를 사용하여 워크플로 만들기</span><span class="sxs-lookup"><span data-stu-id="dc5f6-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="dc5f6-103">Windows PowerShell 스크립트를 작성 하 여 워크플로를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc5f6-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="dc5f6-104">워크플로를 만들려면 스크립트 본문 앞에 워크플로 키워드와 워크플로 이름을 차례로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc5f6-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="dc5f6-105">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="dc5f6-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="dc5f6-106">다른 Windows PowerShell 명령과 동일한 방법으로 워크플로를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc5f6-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="dc5f6-107">병렬 및 시퀀스 구현</span><span class="sxs-lookup"><span data-stu-id="dc5f6-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="dc5f6-108">[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) 는 작업을 병렬로 실행할 수 있도록 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc5f6-108">[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) supports execution of activities in parallel.</span></span> <span data-ttu-id="dc5f6-109">Windows PowerShell 스크립트에서이 기능을 구현 하려면 `parallel` 스크립트 블록 앞에 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc5f6-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="dc5f6-110">또한 생성을 사용 `foreach -parallel` 하 여 개체 컬렉션을 병렬로 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc5f6-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="dc5f6-111">병렬 블록 내에서 작업 그룹을 순서 대로 실행 하려면 해당 작업 그룹을 스크립트 블록으로 묶고 시퀀스 키워드를 사용 하 여 블록 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="dc5f6-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="dc5f6-112">도메인에 컴퓨터 가입</span><span class="sxs-lookup"><span data-stu-id="dc5f6-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="dc5f6-113">다음 스크립트는 사용자 지정 컴퓨터 그룹의 도메인 상태를 확인 하 고 도메인에 가입 되어 있지 않은 경우이를 도메인에 가입 시키는 워크플로를 만든 다음 상태를 다시 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc5f6-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>
<span data-ttu-id="dc5f6-114">[Windows PowerShell 작업을 사용 하 여 워크플로 만들기](./creating-a-workflow-with-windows-powershell-activities.md)에서 설명 하는 XAML 워크플로의 스크립트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="dc5f6-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
}
```

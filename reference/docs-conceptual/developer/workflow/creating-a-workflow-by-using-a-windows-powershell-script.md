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
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366032"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="71b78-102">Windows PowerShell 스크립트를 사용하여 워크플로 만들기</span><span class="sxs-lookup"><span data-stu-id="71b78-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="71b78-103">Windows PowerShell 스크립트를 작성 하 여 워크플로를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71b78-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="71b78-104">워크플로를 만들려면 스크립트 본문 앞에 워크플로 키워드와 워크플로 이름을 차례로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="71b78-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="71b78-105">예:</span><span class="sxs-lookup"><span data-stu-id="71b78-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="71b78-106">다른 Windows PowerShell 명령과 동일한 방법으로 워크플로를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71b78-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="71b78-107">병렬 및 시퀀스 구현</span><span class="sxs-lookup"><span data-stu-id="71b78-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="71b78-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) 는 작업을 병렬로 실행할 수 있도록 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="71b78-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="71b78-109">Windows PowerShell 스크립트에서이 기능을 구현 하려면 스크립트 블록 앞에 `parallel` 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="71b78-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="71b78-110">@No__t-0 생성을 사용 하 여 개체 컬렉션을 병렬로 반복할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71b78-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="71b78-111">병렬 블록 내에서 작업 그룹을 순서 대로 실행 하려면 해당 작업 그룹을 스크립트 블록으로 묶고 시퀀스 키워드를 사용 하 여 블록 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="71b78-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="71b78-112">도메인에 컴퓨터 가입</span><span class="sxs-lookup"><span data-stu-id="71b78-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="71b78-113">다음 스크립트는 사용자 지정 컴퓨터 그룹의 도메인 상태를 확인 하 고 도메인에 가입 되어 있지 않은 경우이를 도메인에 가입 시키는 워크플로를 만든 다음 상태를 다시 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="71b78-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="71b78-114">[Windows PowerShell 작업을 사용 하 여 워크플로 만들기](./creating-a-workflow-with-windows-powershell-activities.md)에서 설명 하는 XAML 워크플로의 스크립트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="71b78-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

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
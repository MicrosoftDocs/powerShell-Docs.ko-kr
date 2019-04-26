---
title: StopProc 자습서 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067316"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="3aa55-102">StopProc 자습서</span><span class="sxs-lookup"><span data-stu-id="3aa55-102">StopProc Tutorial</span></span>

<span data-ttu-id="3aa55-103">이 섹션에서는 매우 비슷한 중지 Proc cmdlet 만들기에 대 한 자습서를 제공 합니다 [Stop-process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet은 Windows PowerShell에서 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aa55-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="3aa55-104">이 자습서에는 cmdlet 구현 하는 방법을 보여 주는 코드 조각 및 코드의 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aa55-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="3aa55-105">이 자습서의 항목</span><span class="sxs-lookup"><span data-stu-id="3aa55-105">Topics in this Tutorial</span></span>

<span data-ttu-id="3aa55-106">이 자습서의 항목에서는 이전 항목에서 설명한 것 토대로 각 항목을 순차적으로 읽을 수 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3aa55-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="3aa55-107">[시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md) 이 섹션에는 컴퓨터에서 실행 되는 프로세스를 중지 하는 등의 시스템 수정 작업을 지 원하는 cmdlet을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aa55-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="3aa55-108">[사용자 메시지 Your Cmdlet에 추가](./adding-user-messages-to-your-cmdlet.md) cmdlet에 사용자 메시지, 디버그 메시지, 경고 메시지 및 진행률 정보를 쓸 수 있는 기능을 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aa55-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="3aa55-109">[와일드 카드 식 별칭을 추가 하 고 Cmdlet 매개 변수를](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) 이 섹션에서는 매개 변수 별칭, 도움말 및 와일드 카드 확장을 지 원하는 cmdlet을 만드는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aa55-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="3aa55-110">[Cmdlet에 매개 변수 집합을 추가](./adding-parameter-sets-to-a-cmdlet.md) cmdlet에 매개 변수 집합 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aa55-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="3aa55-111">매개 변수 집합에 어떤 매개 변수를 사용자 지정에 따라 다르게 cmdlet이 작동을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aa55-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="3aa55-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3aa55-112">See Also</span></span>

[<span data-ttu-id="3aa55-113">시스템을 수정 하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="3aa55-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="3aa55-114">사용자 메시지 Cmdlet 추가</span><span class="sxs-lookup"><span data-stu-id="3aa55-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="3aa55-115">Cmdlet 매개 변수 및 별칭을 와일드 카드 확장 추가</span><span class="sxs-lookup"><span data-stu-id="3aa55-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="3aa55-116">Cmdlet 집합 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aa55-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="3aa55-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3aa55-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

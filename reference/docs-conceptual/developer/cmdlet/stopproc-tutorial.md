---
title: StopProc 자습서 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e298c729b7ac59141638052d19b95ab77aa25cd6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786478"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="e0e2f-102">StopProc 자습서</span><span class="sxs-lookup"><span data-stu-id="e0e2f-102">StopProc Tutorial</span></span>

<span data-ttu-id="e0e2f-103">이 섹션에서는 Windows PowerShell에서 제공 하는 [중지-프로세스](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet과 매우 유사한 중지-프로시저 cmdlet을 만드는 방법에 대 한 자습서를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e2f-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="e0e2f-104">이 자습서에서는 cmdlet을 구현 하는 방법과 코드에 대 한 설명을 보여 주는 코드 조각을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e2f-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="e0e2f-105">이 자습서의 항목</span><span class="sxs-lookup"><span data-stu-id="e0e2f-105">Topics in this Tutorial</span></span>

<span data-ttu-id="e0e2f-106">이 자습서의 항목은 순차적으로 읽을 수 있도록 설계 되었습니다. 각 항목은 이전 항목에서 설명한 내용에 대 한 정보를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e2f-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="e0e2f-107">[시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md) 이 섹션에서는 컴퓨터에서 실행 중인 프로세스를 중지 하는 것과 같이 시스템 수정을 지 원하는 cmdlet을 만드는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e2f-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="e0e2f-108">[Cmdlet에 사용자 메시지 추가](./adding-user-messages-to-your-cmdlet.md) 이 섹션에서는 cmdlet에 사용자 메시지, 디버그 메시지, 경고 메시지 및 진행률 정보를 작성 하는 기능을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e2f-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="e0e2f-109">[별칭, 와일드 카드 확장 및 Cmdlet 매개 변수에 대 한 도움말 추가](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) 이 섹션에서는 매개 변수 별칭, 도움말 및 와일드 카드 확장을 지 원하는 cmdlet을 만드는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e2f-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="e0e2f-110">[Cmdlet에 매개 변수 집합 추가](./adding-parameter-sets-to-a-cmdlet.md) 이 섹션에서는 cmdlet에 매개 변수 집합을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0e2f-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="e0e2f-111">매개 변수 집합을 사용 하면 cmdlet이 사용자에 의해 지정 된 매개 변수에 따라 다르게 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0e2f-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0e2f-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0e2f-112">See Also</span></span>

[<span data-ttu-id="e0e2f-113">시스템을 수정하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="e0e2f-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="e0e2f-114">Cmdlet에 사용자 메시지 추가</span><span class="sxs-lookup"><span data-stu-id="e0e2f-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="e0e2f-115">Cmdlet 매개 변수에 별칭, 와일드카드 확장 및 도움말 추가</span><span class="sxs-lookup"><span data-stu-id="e0e2f-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="e0e2f-116">Cmdlet에 매개 변수 집합 추가</span><span class="sxs-lookup"><span data-stu-id="e0e2f-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="e0e2f-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e0e2f-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

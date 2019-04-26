---
title: Cmdlet을 작성 하는 것에 대 한 자습서 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0b548aa-febf-45dd-bf71-2077730b9b73
caps.latest.revision: 6
ms.openlocfilehash: 767b392bd1603e83d80bad5b3fd9cb42ff142ce6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067249"
---
# <a name="tutorials-for-writing-cmdlets"></a><span data-ttu-id="c0368-102">Cmdlet 작성 자습서</span><span class="sxs-lookup"><span data-stu-id="c0368-102">Tutorials for Writing Cmdlets</span></span>

<span data-ttu-id="c0368-103">이 섹션에서는 cmdlet을 작성 하는 것에 대 한 자습서를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0368-103">This section contains tutorials for writing cmdlets.</span></span> <span data-ttu-id="c0368-104">이 자습서는 cmdlet 및 코드가 필요한 이유는 설명은 작성 하는 데 필요한 코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0368-104">These tutorials include the code needed to write the cmdlets, plus an explanation of why the code is needed.</span></span> <span data-ttu-id="c0368-105">이러한 항목은 cmdlet을 작성 하기 시작 하는 사람에 게 매우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0368-105">These topics will be very helpful for those who are just starting to write cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0368-106">사용자에 게 덜 설명 사용 하 여 코드 예제를 보려면을 참조 하세요 [Cmdlet 샘플](./cmdlet-samples.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="c0368-106">For those who want code examples with less description, see [Cmdlet Samples](./cmdlet-samples.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c0368-107">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="c0368-107">In This Section</span></span>

<span data-ttu-id="c0368-108">[GetProc 자습서](./getproc-tutorial.md) -이 자습서에는 cmdlet 클래스를 정의 하 고 매개 변수를 추가 하 고 오류 보고와 같은 기본 기능을 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0368-108">[GetProc Tutorial](./getproc-tutorial.md) - This tutorial describes how to define a cmdlet class and add basic functionality such as adding parameters and reporting errors.</span></span> <span data-ttu-id="c0368-109">이 자습서에 설명 된 cmdlet은 매우 유사 합니다 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet은 Windows PowerShell에서 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0368-109">The cmdlet described in this tutorial is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span>

<span data-ttu-id="c0368-110">[StopProc 자습서](./stopproc-tutorial.md) -이 자습서에서는 cmdlet을 정의 하 여 사용자 프롬프트를 와일드 카드 지원 등의 기능을 추가 하는 방법을 설명 하 고 설정 하는 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0368-110">[StopProc Tutorial](./stopproc-tutorial.md) - This tutorial describes how to define a cmdlet and add functionality such as user prompts, wildcard support, and the use of parameter sets.</span></span> <span data-ttu-id="c0368-111">여기에 설명 된 cmdlet와 동일한 작업을 수행 합니다 [Stop-process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet은 Windows PowerShell에서 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0368-111">The cmdlet described here performs the same task as the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span>

<span data-ttu-id="c0368-112">[SelectStr 자습서](./selectstr-tutorial.md) -이 자습서에서는 데이터 저장소에 액세스 하는 cmdlet을 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0368-112">[SelectStr Tutorial](./selectstr-tutorial.md) - This tutorial describes how to define a cmdlet that accesses a data store.</span></span> <span data-ttu-id="c0368-113">여기에 설명 된 cmdlet와 동일한 작업을 수행 합니다 [Select-string](/powershell/module/microsoft.powershell.utility/select-string) cmdlet은 Windows PowerShell에서 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0368-113">The cmdlet described here performs the same task as the [Select-String](/powershell/module/microsoft.powershell.utility/select-string) cmdlet provided by Windows PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0368-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c0368-114">See Also</span></span>

[<span data-ttu-id="c0368-115">GetProc 자습서</span><span class="sxs-lookup"><span data-stu-id="c0368-115">GetProc Tutorial</span></span>](./getproc-tutorial.md)

[<span data-ttu-id="c0368-116">StopProc 자습서</span><span class="sxs-lookup"><span data-stu-id="c0368-116">StopProc Tutorial</span></span>](./stopproc-tutorial.md)

[<span data-ttu-id="c0368-117">SelectStr 자습서</span><span class="sxs-lookup"><span data-stu-id="c0368-117">SelectStr Tutorial</span></span>](./selectstr-tutorial.md)

[<span data-ttu-id="c0368-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c0368-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

---
title: Cmdlet 작성 자습서 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0b548aa-febf-45dd-bf71-2077730b9b73
caps.latest.revision: 6
ms.openlocfilehash: 767b392bd1603e83d80bad5b3fd9cb42ff142ce6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369322"
---
# <a name="tutorials-for-writing-cmdlets"></a><span data-ttu-id="8898f-102">Cmdlet 작성 자습서</span><span class="sxs-lookup"><span data-stu-id="8898f-102">Tutorials for Writing Cmdlets</span></span>

<span data-ttu-id="8898f-103">이 섹션에는 cmdlet 작성에 대 한 자습서가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8898f-103">This section contains tutorials for writing cmdlets.</span></span> <span data-ttu-id="8898f-104">이러한 자습서에는 cmdlet을 작성 하는 데 필요한 코드와 코드가 필요한 이유에 대 한 설명이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8898f-104">These tutorials include the code needed to write the cmdlets, plus an explanation of why the code is needed.</span></span> <span data-ttu-id="8898f-105">이러한 항목은 cmdlet 작성을 시작 하는 사용자에 게 매우 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8898f-105">These topics will be very helpful for those who are just starting to write cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8898f-106">더 작은 설명으로 코드 예제를 사용 하려는 경우에는 [Cmdlet 샘플](./cmdlet-samples.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8898f-106">For those who want code examples with less description, see [Cmdlet Samples](./cmdlet-samples.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8898f-107">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="8898f-107">In This Section</span></span>

<span data-ttu-id="8898f-108">[Getproc 자습서](./getproc-tutorial.md) -이 자습서에서는 cmdlet 클래스를 정의 하 고 매개 변수 추가 및 오류 보고와 같은 기본 기능을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8898f-108">[GetProc Tutorial](./getproc-tutorial.md) - This tutorial describes how to define a cmdlet class and add basic functionality such as adding parameters and reporting errors.</span></span> <span data-ttu-id="8898f-109">이 자습서에서 설명 하는 cmdlet은 Windows PowerShell에서 제공 하는 [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet과 매우 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="8898f-109">The cmdlet described in this tutorial is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span>

<span data-ttu-id="8898f-110">[Stopproc 자습서](./stopproc-tutorial.md) -이 자습서에서는 cmdlet을 정의 하 고 사용자 프롬프트, 와일드 카드 지원 및 매개 변수 집합 사용과 같은 기능을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8898f-110">[StopProc Tutorial](./stopproc-tutorial.md) - This tutorial describes how to define a cmdlet and add functionality such as user prompts, wildcard support, and the use of parameter sets.</span></span> <span data-ttu-id="8898f-111">여기에 설명 된 cmdlet은 Windows PowerShell에서 제공 하는 [중지 프로세스](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet과 동일한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8898f-111">The cmdlet described here performs the same task as the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span>

<span data-ttu-id="8898f-112">[Selectstr 자습서](./selectstr-tutorial.md) -이 자습서에서는 데이터 저장소에 액세스 하는 cmdlet을 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8898f-112">[SelectStr Tutorial](./selectstr-tutorial.md) - This tutorial describes how to define a cmdlet that accesses a data store.</span></span> <span data-ttu-id="8898f-113">여기에 설명 된 cmdlet은 Windows PowerShell에서 제공 하는 [선택 문자열](/powershell/module/microsoft.powershell.utility/select-string) cmdlet과 동일한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8898f-113">The cmdlet described here performs the same task as the [Select-String](/powershell/module/microsoft.powershell.utility/select-string) cmdlet provided by Windows PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="8898f-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8898f-114">See Also</span></span>

[<span data-ttu-id="8898f-115">GetProc 자습서</span><span class="sxs-lookup"><span data-stu-id="8898f-115">GetProc Tutorial</span></span>](./getproc-tutorial.md)

[<span data-ttu-id="8898f-116">StopProc 자습서</span><span class="sxs-lookup"><span data-stu-id="8898f-116">StopProc Tutorial</span></span>](./stopproc-tutorial.md)

[<span data-ttu-id="8898f-117">SelectStr 자습서</span><span class="sxs-lookup"><span data-stu-id="8898f-117">SelectStr Tutorial</span></span>](./selectstr-tutorial.md)

[<span data-ttu-id="8898f-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8898f-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

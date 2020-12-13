---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 오류 보고
description: Windows PowerShell 오류 보고
ms.openlocfilehash: 438e3d96bf52d8ac1f770c0550ae49b356d616eb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650119"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="cd18b-103">Windows PowerShell 오류 보고</span><span class="sxs-lookup"><span data-stu-id="cd18b-103">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="cd18b-104">이 섹션의 항목에서는 cmdlet에서 오류를 보고 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd18b-104">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="cd18b-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="cd18b-105">In This Section</span></span>

<span data-ttu-id="cd18b-106">[오류 보고 개념](./error-reporting-concepts.md) Cmdlet에서 오류를 보고 하는 데 사용할 수 있는 두 가지 메커니즘을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd18b-106">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="cd18b-107">[종료 오류](./terminating-errors.md) 종료 오류를 보고 하는 데 사용 되는 메서드를 설명 합니다 .이는 cmdlet 내에서 해당 메서드를 호출할 수 있으며, 메서드를 호출할 때 Windows PowerShell 런타임에 의해 반환 될 수 있는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="cd18b-107">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="cd18b-108">[종료 되지 않는 오류](./non-terminating-errors.md) 종료 되지 않는 오류를 보고 하는 데 사용 되는 메서드와 cmdlet 내에서 해당 메서드를 호출할 수 있는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd18b-108">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="cd18b-109">[범주별 오류 정보 표시](./displaying-error-information.md) 사용자가 오류를 표시할 수 있는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd18b-109">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="cd18b-110">[Windows PowerShell 오류 레코드](./windows-powershell-error-records.md) 오류 레코드의 구성 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd18b-110">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="cd18b-111">[ErrorRecord 개체 해석](./interpreting-errorrecord-objects.md) ErrorRecord 개체가 해석 되는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd18b-111">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd18b-112">관련 항목</span><span class="sxs-lookup"><span data-stu-id="cd18b-112">See Also</span></span>

[<span data-ttu-id="cd18b-113">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="cd18b-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

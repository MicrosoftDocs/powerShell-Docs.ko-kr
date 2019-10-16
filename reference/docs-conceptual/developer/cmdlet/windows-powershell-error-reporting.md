---
title: Windows PowerShell 오류 보고 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364272"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="9152a-102">Windows PowerShell 오류 보고</span><span class="sxs-lookup"><span data-stu-id="9152a-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="9152a-103">이 섹션의 항목에서는 cmdlet에서 오류를 보고 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9152a-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9152a-104">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="9152a-104">In This Section</span></span>

<span data-ttu-id="9152a-105">[오류 보고 개념](./error-reporting-concepts.md) Cmdlet에서 오류를 보고 하는 데 사용할 수 있는 두 가지 메커니즘을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9152a-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="9152a-106">[종료 오류](./terminating-errors.md) 종료 오류를 보고 하는 데 사용 되는 메서드를 설명 합니다 .이는 cmdlet 내에서 해당 메서드를 호출할 수 있으며, 메서드를 호출할 때 Windows PowerShell 런타임에 의해 반환 될 수 있는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="9152a-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="9152a-107">[종료 되지 않는 오류](./non-terminating-errors.md) 종료 되지 않는 오류를 보고 하는 데 사용 되는 메서드와 cmdlet 내에서 해당 메서드를 호출할 수 있는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9152a-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="9152a-108">[범주별 오류 정보 표시](./displaying-error-information.md) 사용자가 오류를 표시할 수 있는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9152a-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="9152a-109">[Windows PowerShell 오류 레코드](./windows-powershell-error-records.md) 오류 레코드의 구성 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9152a-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="9152a-110">[ErrorRecord 개체 해석](./interpreting-errorrecord-objects.md) ErrorRecord 개체가 해석 되는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9152a-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="9152a-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9152a-111">See Also</span></span>

<span data-ttu-id="9152a-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="9152a-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

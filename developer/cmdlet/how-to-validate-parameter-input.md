---
title: 매개 변수 입력의 유효성을 검사 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f6c700c8-0889-49a1-a990-8c6e9aaf4735
caps.latest.revision: 6
ms.openlocfilehash: 5166213f8247fa23d5e0b3fdfd2367062d595169
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862469"
---
# <a name="how-to-validate-parameter-input"></a><span data-ttu-id="62c9f-102">매개 변수 입력 유효성을 검사하는 방법</span><span class="sxs-lookup"><span data-stu-id="62c9f-102">How to Validate Parameter Input</span></span>

<span data-ttu-id="62c9f-103">이 섹션에는 매개 변수 입력 유효성 검사 규칙을 구현 하려면 다양 한 특성을 사용 하 여 유효성을 검사 하는 방법을 보여 주는 예제가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c9f-103">This section contains examples that show how to validate parameter input by using various attributes to implement validation rules.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="62c9f-104">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="62c9f-104">In This Section</span></span>

<span data-ttu-id="62c9f-105">[인수 집합을 확인 하는 방법을](./how-to-validate-an-argument-set.md) 인수 ArgumentSet 특성을 사용 하 여 설정의 유효성을 검사 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c9f-105">[How to Validate an Argument Set](./how-to-validate-an-argument-set.md) Describes how to validate an argument set by using the ArgumentSet attribute.</span></span>

<span data-ttu-id="62c9f-106">[인수가 범위를 확인 하는 방법을](./how-to-validate-an-argument-range.md) ArgumentRange 특성을 사용 하 여 인수가 범위를 확인 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c9f-106">[How to Validate an Argument Range](./how-to-validate-an-argument-range.md) Describes how to validate an argument range by using the ArgumentRange attribute.</span></span>

<span data-ttu-id="62c9f-107">[인수 패턴의 유효성을 검사 하는 방법을](./how-to-validate-an-argument-pattern.md) 는 인수 패턴 ArgumentPattern 특성을 사용 하 여 유효성을 검사 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c9f-107">[How to Validate an Argument Pattern](./how-to-validate-an-argument-pattern.md) Describes how to validate an argument pattern by using the ArgumentPattern attribute.</span></span>

<span data-ttu-id="62c9f-108">[인수 길이 확인 하는 방법을](./how-to-validate-the-argument-length.md) ArgumentLength 특성을 사용 하 여 인수의 길이 유효성을 검사 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c9f-108">[How to Validate the Argument Length](./how-to-validate-the-argument-length.md) Describes how to validate the length of an argument by using the ArgumentLength attribute.</span></span>

<span data-ttu-id="62c9f-109">[인수 개수를 확인 하는 방법을](./how-to-validate-an-argument-count.md) ArgumentCount 특성을 사용 하 여 인수 개수를 확인 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c9f-109">[How to Validate an Argument Count](./how-to-validate-an-argument-count.md) Describes how to validate an argument count by using the ArgumentCount attribute.</span></span>

<span data-ttu-id="62c9f-110">매개 변수가 선언 된 방식으로 유효성 검사에 영향을 줄 수입니다.</span><span class="sxs-lookup"><span data-stu-id="62c9f-110">The way a parameter is declared can affect validation.</span></span> <span data-ttu-id="62c9f-111">자세한 내용은 [Cmdlet 매개 변수를 선언 하는 방법을](./how-to-declare-cmdlet-parameters.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="62c9f-111">For more information, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

## <a name="reference"></a><span data-ttu-id="62c9f-112">참조</span><span class="sxs-lookup"><span data-stu-id="62c9f-112">Reference</span></span>

## <a name="see-also"></a><span data-ttu-id="62c9f-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62c9f-113">See Also</span></span>

<span data-ttu-id="62c9f-114">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="62c9f-114">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

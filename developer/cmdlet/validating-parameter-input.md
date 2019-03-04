---
title: 매개 변수 입력 유효성 검사 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858849"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="73467-102">매개 변수 입력 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="73467-102">Validating Parameter Input</span></span>

<span data-ttu-id="73467-103">Windows PowerShell에는 여러 가지 방법으로 cmdlet 매개 변수에 전달 된 인수 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73467-103">Windows PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span> <span data-ttu-id="73467-104">Windows PowerShell은 길이, 범위 및 인수의 문자 패턴과 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73467-104">Windows PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span> <span data-ttu-id="73467-105">사용할 수 있는 인수 (개수) 수가 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73467-105">It can validate the number of arguments available (the count).</span></span> <span data-ttu-id="73467-106">이러한 유효성 검사 규칙 cmdlet 클래스의 공용 속성에 대 한 매개 변수 특성을 사용 하 여 선언 된 유효성 검사 특성에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73467-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="73467-107">매개 변수 인수에 유효성을 검사 하는 Windows PowerShell 런타임에 cmdlet을 실행 하기 전에 매개 변수의 값을 확인 하려면 유효성 검사 특성을 제공 하는 정보를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="73467-107">To validate a parameter argument, the Windows PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span> <span data-ttu-id="73467-108">매개 변수 입력 유효 하지 않으면 사용자는 오류 메시지를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="73467-108">If the parameter input is not valid, the user receives an error message.</span></span> <span data-ttu-id="73467-109">각 유효성 검사 매개 변수는 Windows PowerShell에서 적용 되는 유효성 검사 규칙을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="73467-109">Each validation parameter defines a validation rule that is enforced by Windows PowerShell.</span></span>

<span data-ttu-id="73467-110">Windows PowerShell에서 다음 특성을 기반으로 유효성 검사 규칙을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="73467-110">Windows PowerShell enforces the validation rules based on the following attributes.</span></span>

<span data-ttu-id="73467-111">ValidateCount 인수 매개 변수를 받아들일 수 있는 최소 및 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73467-111">ValidateCount Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span> <span data-ttu-id="73467-112">이 특성을 선언 하는 데 사용 되는 구문에 대 한 자세한 내용은 참조 하세요. [ValidateCount 특성 선언을](./validatecount-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="73467-112">For more information about the syntax used to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

<span data-ttu-id="73467-113">ValidateLength 매개 변수 인수에 최소 및 최대 문자 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73467-113">ValidateLength Specifies the minimum and maximum number of characters in the parameter argument.</span></span> <span data-ttu-id="73467-114">이 특성을 선언 하는 데 사용 되는 구문에 대 한 자세한 내용은 참조 하세요. [ValidateLength 특성 선언을](./validatelength-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="73467-114">For more information about the syntax used to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

<span data-ttu-id="73467-115">ValidatePattern 매개 변수 인수를 확인 하는 정규식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73467-115">ValidatePattern Specifies a regular expression that validates the parameter argument.</span></span> <span data-ttu-id="73467-116">이 특성을 선언 하는 데 사용 되는 구문에 대 한 자세한 내용은 참조 하세요. [ValidatePattern 특성 선언을](./validatepattern-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="73467-116">For more information about the syntax used to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

<span data-ttu-id="73467-117">ValidateRange 매개 변수 인수의 최소 및 최대 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73467-117">ValidateRange Specifies the minimum and maximum values of the parameter argument.</span></span> <span data-ttu-id="73467-118">이 특성을 선언 하는 데 사용 되는 구문에 대 한 자세한 내용은 참조 하세요. [ValidateRange 특성 선언을](./validaterange-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="73467-118">For more information about the syntax used to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

<span data-ttu-id="73467-119">ValidateSet 매개 변수 인수에 대 한 유효한 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73467-119">ValidateSet Specifies the valid values for the parameter argument.</span></span> <span data-ttu-id="73467-120">이 특성을 선언 하는 데 사용 되는 구문에 대 한 자세한 내용은 참조 하세요. [ValidateSet 특성 선언을](./validateset-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="73467-120">For more information about the syntax used to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73467-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73467-121">See Also</span></span>

[<span data-ttu-id="73467-122">매개 변수 입력의 유효성을 검사 하는 방법</span><span class="sxs-lookup"><span data-stu-id="73467-122">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

<span data-ttu-id="73467-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="73467-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

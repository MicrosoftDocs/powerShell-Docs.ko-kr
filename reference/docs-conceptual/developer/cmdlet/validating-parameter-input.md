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
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363512"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="801d8-102">매개 변수 입력 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="801d8-102">Validating Parameter Input</span></span>

<span data-ttu-id="801d8-103">PowerShell은 여러 가지 방법으로 cmdlet 매개 변수에 전달 되는 인수의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="801d8-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="801d8-104">PowerShell은 인수의 길이, 범위 및 패턴의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="801d8-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="801d8-105">사용할 수 있는 인수 수 (개수)의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="801d8-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="801d8-106">이러한 유효성 검사 규칙은 cmdlet 클래스의 공용 속성에 대 한 매개 변수 특성을 사용 하 여 선언 된 유효성 검사 특성에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="801d8-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="801d8-107">매개 변수 인수의 유효성을 검사 하기 위해 PowerShell 런타임은 유효성 검사 특성에서 제공 하는 정보를 사용 하 여 cmdlet이 실행 되기 전에 매개 변수의 값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="801d8-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="801d8-108">매개 변수 입력이 잘못 된 경우 사용자에 게 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="801d8-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="801d8-109">각 유효성 검사 매개 변수는 PowerShell에서 적용 되는 유효성 검사 규칙을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="801d8-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="801d8-110">PowerShell은 다음 특성을 기반으로 유효성 검사 규칙을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="801d8-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="801d8-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="801d8-111">ValidateCount</span></span>

<span data-ttu-id="801d8-112">매개 변수가 허용할 수 있는 인수의 최소 및 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="801d8-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="801d8-113">자세한 내용은 [Validatecount 특성 선언](./validatecount-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="801d8-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="801d8-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="801d8-114">ValidateLength</span></span>

<span data-ttu-id="801d8-115">매개 변수 인수에서 최소 및 최대 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="801d8-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="801d8-116">자세한 내용은 [ValidateLength Attribute 선언](./validatelength-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="801d8-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="801d8-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="801d8-117">ValidatePattern</span></span>

<span data-ttu-id="801d8-118">매개 변수 인수의 유효성을 검사 하는 정규식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="801d8-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="801d8-119">자세한 내용은 [ValidatePattern Attribute 선언](./validatepattern-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="801d8-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="801d8-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="801d8-120">ValidateRange</span></span>

<span data-ttu-id="801d8-121">매개 변수 인수의 최소값과 최대값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="801d8-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="801d8-122">자세한 내용은 [ValidateRange Attribute 선언](./validaterange-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="801d8-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="801d8-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="801d8-123">ValidateSet</span></span>

<span data-ttu-id="801d8-124">매개 변수 인수에 대 한 유효한 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="801d8-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="801d8-125">자세한 내용은 [ValidateSet Attribute 선언](./validateset-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="801d8-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="801d8-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="801d8-126">See Also</span></span>

[<span data-ttu-id="801d8-127">매개 변수 입력의 유효성을 검사 하는 방법</span><span class="sxs-lookup"><span data-stu-id="801d8-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

<span data-ttu-id="801d8-128">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="801d8-128">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

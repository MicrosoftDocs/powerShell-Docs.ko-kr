---
title: ValidatePattern 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369162"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="07cce-102">ValidatePattern 특성 선언</span><span class="sxs-lookup"><span data-stu-id="07cce-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="07cce-103">ValidatePattern 특성은 cmdlet 매개 변수의 인수에 대 한 유효성을 검사 하는 정규식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="07cce-104">이 특성은 Windows PowerShell 함수 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="07cce-105">Cmdlet 내에서 ValidatePattern가 호출 되 면 Windows PowerShell 런타임은 cmdlet 매개 변수의 인수를 문자열로 변환한 다음 해당 문자열을 ValidatePattern 특성에서 제공 된 패턴과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="07cce-106">이 cmdlet은 인수의 변환 된 문자열 표현과 제공 된 패턴이 일치 하는 경우에만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="07cce-107">일치 하지 않는 경우 Windows PowerShell 런타임에서 오류가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="07cce-108">구문</span><span class="sxs-lookup"><span data-stu-id="07cce-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="07cce-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="07cce-109">Parameters</span></span>

<span data-ttu-id="07cce-110">`RegexString` ([system.string](/dotnet/api/System.String))이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="07cce-111">매개 변수 인수의 유효성을 검사 하는 정규식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="07cce-112">옵션 ([system.text.regularexpressions.regex>. system.text.regularexpressions.regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions))은 선택적으로 명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="07cce-113">정규식 옵션을 지정 하는 [system.text.regularexpressions.regex>. system.text.regularexpressions.regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) 플래그의 비트 조합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="07cce-114">설명</span><span class="sxs-lookup"><span data-stu-id="07cce-114">Remarks</span></span>

- <span data-ttu-id="07cce-115">이 특성은 매개 변수 당 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="07cce-116">특성의 `Option` 매개 변수를 사용 하 여 패턴을 추가로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="07cce-117">예를 들어 대/소문자를 구분 하는 패턴을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="07cce-118">이 특성이 컬렉션에 적용 되는 경우 컬렉션의 각 요소가 패턴과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="07cce-119">ValidatePattern 특성은 [Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07cce-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="07cce-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07cce-120">See Also</span></span>

[<span data-ttu-id="07cce-121">Validatepatternattribute.</span><span class="sxs-lookup"><span data-stu-id="07cce-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

<span data-ttu-id="07cce-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="07cce-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

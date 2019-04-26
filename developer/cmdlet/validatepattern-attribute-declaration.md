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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067130"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="1a952-102">ValidatePattern 특성 선언</span><span class="sxs-lookup"><span data-stu-id="1a952-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="1a952-103">ValidatePattern 특성 cmdlet 매개 변수 인수의 유효성을 검사 하는 정규식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="1a952-104">Windows PowerShell 함수에서이 특성을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="1a952-105">ValidatePattern cmdlet 내에서 호출 되 면 Windows PowerShell cmdlet 매개 변수의 인수를 문자열로 변환 런타임과 ValidatePattern 특성에 의해 제공 된 패턴에 해당 문자열을 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="1a952-106">Cmdlet은 변환 된 문자열 표현을 인수 및 지정 된 패턴과 일치 하는 경우에 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="1a952-107">일치 하지 않으면 Windows PowerShell 런타임에 의해 오류가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="1a952-108">구문</span><span class="sxs-lookup"><span data-stu-id="1a952-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="1a952-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1a952-109">Parameters</span></span>

<span data-ttu-id="1a952-110">`RegexString` ([System.String](/dotnet/api/System.String)) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="1a952-111">매개 변수 인수를 확인 하는 정규식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="1a952-112">옵션 ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) 명명 된 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="1a952-113">비트 조합을 지정 [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) 정규식 옵션을 지정 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a952-114">설명</span><span class="sxs-lookup"><span data-stu-id="1a952-114">Remarks</span></span>

- <span data-ttu-id="1a952-115">이 특성 매개 변수당 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="1a952-116">사용할 수는 `Option` 추가로 패턴을 정의할 특성의 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="1a952-117">예를 들어 가능 패턴 대/소문자 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="1a952-118">이 특성 컬렉션에 적용할 경우 컬렉션의 각 요소에 패턴을 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="1a952-119">ValidatePattern 특성은 정의한 합니다 [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="1a952-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a952-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a952-120">See Also</span></span>

[<span data-ttu-id="1a952-121">System.Management.Automation.Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="1a952-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

<span data-ttu-id="1a952-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="1a952-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

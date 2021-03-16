---
description: 종료 오류를 생성하는 Throw 키워드에 대해 설명합니다.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: bef005f47583523f69a8b25651eb0ee5bfc5b224
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195841"
---
# <a name="about-throw"></a><span data-ttu-id="adf53-103">Throw 정보</span><span class="sxs-lookup"><span data-stu-id="adf53-103">About Throw</span></span>

## <a name="short-description"></a><span data-ttu-id="adf53-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="adf53-104">Short description</span></span>
<span data-ttu-id="adf53-105">종료 오류를 생성하는 Throw 키워드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-105">Describes the Throw keyword, which generates a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="adf53-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-106">Long description</span></span>

<span data-ttu-id="adf53-107">Throw 키워드는 종료 오류를 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-107">The Throw keyword causes a terminating error.</span></span> <span data-ttu-id="adf53-108">Throw 키워드를 사용 하 여 명령, 함수 또는 스크립트의 처리를 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-108">You can use the Throw keyword to stop the processing of a command, function, or script.</span></span>

<span data-ttu-id="adf53-109">예를 들어 If 문의 스크립트 블록에서 Throw 키워드를 사용 하 여 조건문의 조건 또는 Catch 블록에 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-109">For example, you can use the Throw keyword in the script block of an If statement to respond to a condition or in the Catch block of a Try-Catch-Finally statement.</span></span> <span data-ttu-id="adf53-110">매개 변수 선언에서 Throw 키워드를 사용 하 여 함수 매개 변수를 필수로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-110">You can also use the Throw keyword in a parameter declaration to make a function parameter mandatory.</span></span>

<span data-ttu-id="adf53-111">Throw 키워드는 사용자 메시지 문자열 또는 오류를 발생 시킨 개체와 같은 모든 개체를 throw 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-111">The Throw keyword can throw any object, such as a user message string or the object that caused the error.</span></span>

## <a name="syntax"></a><span data-ttu-id="adf53-112">구문</span><span class="sxs-lookup"><span data-stu-id="adf53-112">Syntax</span></span>

<span data-ttu-id="adf53-113">Throw 키워드의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-113">The syntax of the Throw keyword is as follows:</span></span>

```powershell
throw [<expression>]
```

<span data-ttu-id="adf53-114">Throw 구문의 식은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-114">The expression in the Throw syntax is optional.</span></span> <span data-ttu-id="adf53-115">Catch 블록에 Throw 문이 표시 되지 않고 식이 포함 되지 않은 경우에는 스크립트가 잘못 된 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-115">When the Throw statement does not appear in a Catch block, and it does not include an expression, it generates a ScriptHalted error.</span></span>

```powershell
C:\PS> throw

Exception: ScriptHalted
```

<span data-ttu-id="adf53-116">Throw 키워드가 식 없이 Catch 블록에서 사용 되는 경우 현재 RuntimeException을 다시 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-116">If the Throw keyword is used in a Catch block without an expression, it throws the current RuntimeException again.</span></span> <span data-ttu-id="adf53-117">자세한 내용은 about_Try_Catch_Finally를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="adf53-117">For more information, see about_Try_Catch_Finally.</span></span>

## <a name="throwing-a-string"></a><span data-ttu-id="adf53-118">문자열 throw</span><span class="sxs-lookup"><span data-stu-id="adf53-118">Throwing a string</span></span>

<span data-ttu-id="adf53-119">Throw 문의 선택적 식은 다음 예제에 표시 된 것 처럼 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-119">The optional expression in a Throw statement can be a string, as shown in the following example:</span></span>

```powershell
C:\PS> throw "This is an error."

Exception: This is an error.
```

## <a name="throwing-other-objects"></a><span data-ttu-id="adf53-120">다른 개체 throw</span><span class="sxs-lookup"><span data-stu-id="adf53-120">Throwing other objects</span></span>

<span data-ttu-id="adf53-121">식은 다음 예제와 같이 PowerShell 프로세스를 나타내는 개체를 throw 하는 개체 일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-121">The expression can also be an object that throws the object that represents the PowerShell process, as shown in the following example:</span></span>

```powershell
C:\PS> throw (get-process Pwsh)

Exception: System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh)
```

<span data-ttu-id="adf53-122">$Error 자동 변수에 ErrorRecord 개체의 TargetObject 속성을 사용 하 여 오류를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-122">You can use the TargetObject property of the ErrorRecord object in the $error automatic variable to examine the error.</span></span>

```powershell
C:\PS> $error[0].targetobject

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    125   174.44     229.57      23.61    1548   2 pwsh
     63    44.07      81.95       1.75    1732   2 pwsh
     63    43.32      77.65       1.48    9092   2 pwsh
```

<span data-ttu-id="adf53-123">ErrorRecord 개체 또는 .NET 예외를 throw 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-123">You can also throw an ErrorRecord object or a .NET exception.</span></span> <span data-ttu-id="adf53-124">다음 예제에서는 Throw 키워드를 사용 하 여 FormatException 개체를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-124">The following example uses the Throw keyword to throw a System.FormatException object.</span></span>

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

OperationStopped: One of the identified items was in an invalid format.
```

## <a name="the-resulting-error"></a><span data-ttu-id="adf53-125">결과 오류</span><span class="sxs-lookup"><span data-stu-id="adf53-125">The resulting error</span></span>

<span data-ttu-id="adf53-126">Throw 키워드는 ErrorRecord 개체를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-126">The Throw keyword can generate an ErrorRecord object.</span></span> <span data-ttu-id="adf53-127">ErrorRecord 개체의 Exception 속성에는 RuntimeException 개체가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-127">The Exception property of the ErrorRecord object contains a RuntimeException object.</span></span> <span data-ttu-id="adf53-128">ErrorRecord 개체와 RuntimeException 개체의 나머지 부분은 Throw 키워드가 throw 하는 개체에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-128">The remainder of the ErrorRecord object and the RuntimeException object vary with the object that the Throw keyword throws.</span></span>

<span data-ttu-id="adf53-129">RunTimeException 개체가 ErrorRecord 개체에 래핑되어 ErrorRecord 개체가 자동으로 $Error 자동으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="adf53-129">The RunTimeException object is wrapped in an ErrorRecord object, and the ErrorRecord object is automatically saved in the $Error automatic variable.</span></span>

## <a name="using-throw-to-create-a-mandatory-parameter"></a><span data-ttu-id="adf53-130">Throw를 사용 하 여 필수 매개 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="adf53-130">Using Throw to create a mandatory parameter</span></span>

<span data-ttu-id="adf53-131">PowerShell의 이전 버전과 달리 매개 변수 유효성 검사에는 Throw 키워드를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="adf53-131">Unlike past versions of PowerShell, do not use the Throw keyword for parameter validation.</span></span> <span data-ttu-id="adf53-132">올바른 방법에 대 한 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="adf53-132">See [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) for the correct way.</span></span>

## <a name="see-also"></a><span data-ttu-id="adf53-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="adf53-133">See also</span></span>

- [<span data-ttu-id="adf53-134">about_Break</span><span class="sxs-lookup"><span data-stu-id="adf53-134">about_Break</span></span>](about_Break.md)
- [<span data-ttu-id="adf53-135">about_Continue</span><span class="sxs-lookup"><span data-stu-id="adf53-135">about_Continue</span></span>](about_Continue.md)
- [<span data-ttu-id="adf53-136">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="adf53-136">about_Scopes</span></span>](about_Scopes.md)
- [<span data-ttu-id="adf53-137">about_Trap</span><span class="sxs-lookup"><span data-stu-id="adf53-137">about_Trap</span></span>](about_Trap.md)
- [<span data-ttu-id="adf53-138">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="adf53-138">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
---
description: 종료 오류를 생성하는 Throw 키워드에 대해 설명합니다.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: e573722154fff99363b26806064ec17c8903bfd8
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194167"
---
# <a name="about-throw"></a><span data-ttu-id="0a7f2-103">Throw 정보</span><span class="sxs-lookup"><span data-stu-id="0a7f2-103">About Throw</span></span>

## <a name="short-description"></a><span data-ttu-id="0a7f2-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="0a7f2-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="0a7f2-105">종료 오류를 생성하는 Throw 키워드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-105">Describes the Throw keyword, which generates a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="0a7f2-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="0a7f2-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="0a7f2-107">Throw 키워드는 종료 오류를 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-107">The Throw keyword causes a terminating error.</span></span> <span data-ttu-id="0a7f2-108">Throw 키워드를 사용 하 여 명령, 함수 또는 스크립트의 처리를 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-108">You can use the Throw keyword to stop the processing of a command, function, or script.</span></span>

<span data-ttu-id="0a7f2-109">예를 들어 If 문의 스크립트 블록에서 Throw 키워드를 사용 하 여 조건문의 조건 또는 Catch 블록에 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-109">For example, you can use the Throw keyword in the script block of an If statement to respond to a condition or in the Catch block of a Try-Catch-Finally statement.</span></span> <span data-ttu-id="0a7f2-110">매개 변수 선언에서 Throw 키워드를 사용 하 여 함수 매개 변수를 필수로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-110">You can also use the Throw keyword in a parameter declaration to make a function parameter mandatory.</span></span>

<span data-ttu-id="0a7f2-111">Throw 키워드는 사용자 메시지 문자열 또는 오류를 발생 시킨 개체와 같은 모든 개체를 throw 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-111">The Throw keyword can throw any object, such as a user message string or the object that caused the error.</span></span>

## <a name="syntax"></a><span data-ttu-id="0a7f2-112">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0a7f2-112">SYNTAX</span></span>

<span data-ttu-id="0a7f2-113">Throw 키워드의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-113">The syntax of the Throw keyword is as follows:</span></span>

```powershell
throw [<expression>]
```

<span data-ttu-id="0a7f2-114">Throw 구문의 식은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-114">The expression in the Throw syntax is optional.</span></span> <span data-ttu-id="0a7f2-115">Catch 블록에 Throw 문이 표시 되지 않고 식이 포함 되지 않은 경우에는 스크립트가 잘못 된 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-115">When the Throw statement does not appear in a Catch block, and it does not include an expression, it generates a ScriptHalted error.</span></span>

```powershell
C:\PS> throw

ScriptHalted
At line:1 char:6
+ throw <<<<
+ CategoryInfo          : OperationStopped: (:) [], RuntimeException
+ FullyQualifiedErrorId : ScriptHalted
```

<span data-ttu-id="0a7f2-116">Throw 키워드가 식 없이 Catch 블록에서 사용 되는 경우 현재 RuntimeException을 다시 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-116">If the Throw keyword is used in a Catch block without an expression, it throws the current RuntimeException again.</span></span> <span data-ttu-id="0a7f2-117">자세한 내용은 about_Try_Catch_Finally를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-117">For more information, see about_Try_Catch_Finally.</span></span>

## <a name="throwing-a-string"></a><span data-ttu-id="0a7f2-118">문자열 THROW</span><span class="sxs-lookup"><span data-stu-id="0a7f2-118">THROWING A STRING</span></span>

<span data-ttu-id="0a7f2-119">Throw 문의 선택적 식은 다음 예제에 표시 된 것 처럼 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-119">The optional expression in a Throw statement can be a string, as shown in the following example:</span></span>

```powershell
C:\PS> throw "This is an error."

This is an error.
At line:1 char:6
+ throw <<<<  "This is an error."
+ CategoryInfo          : OperationStopped: (This is an error.:String) [], R
untimeException
+ FullyQualifiedErrorId : This is an error.
```

## <a name="throwing-other-objects"></a><span data-ttu-id="0a7f2-120">다른 개체 THROW</span><span class="sxs-lookup"><span data-stu-id="0a7f2-120">THROWING OTHER OBJECTS</span></span>

<span data-ttu-id="0a7f2-121">식은 다음 예제와 같이 PowerShell 프로세스를 나타내는 개체를 throw 하는 개체 일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-121">The expression can also be an object that throws the object that represents the PowerShell process, as shown in the following example:</span></span>

```powershell
C:\PS> throw (get-process PowerShell)

System.Diagnostics.Process (PowerShell)
At line:1 char:6
+ throw <<<<  (get-process PowerShell)
+ CategoryInfo          : OperationStopped: (System.Diagnostics.Process (Pow
erShell):Process) [],
RuntimeException
+ FullyQualifiedErrorId : System.Diagnostics.Process (PowerShell)
```

<span data-ttu-id="0a7f2-122">$Error 자동 변수에 ErrorRecord 개체의 TargetObject 속성을 사용 하 여 오류를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-122">You can use the TargetObject property of the ErrorRecord object in the $error automatic variable to examine the error.</span></span>

```powershell
C:\PS> $error[0].targetobject

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
319      26    61016      70864   568     3.28   5548 PowerShell
```

<span data-ttu-id="0a7f2-123">ErrorRecord 개체 또는 Microsoft .NET 프레임 워크 예외를 throw 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-123">You can also throw an ErrorRecord object or a Microsoft .NET Framework exception.</span></span> <span data-ttu-id="0a7f2-124">다음 예제에서는 Throw 키워드를 사용 하 여 FormatException 개체를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-124">The following example uses the Throw keyword to throw a System.FormatException object.</span></span>

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

One of the identified items was in an invalid format.
At line:1 char:6
+ throw <<<<  $formatError
+ CategoryInfo          : OperationStopped: (:) [], FormatException
+ FullyQualifiedErrorId : One of the identified items was in an invalid
format.
```

## <a name="resulting-error"></a><span data-ttu-id="0a7f2-125">결과 오류</span><span class="sxs-lookup"><span data-stu-id="0a7f2-125">RESULTING ERROR</span></span>

<span data-ttu-id="0a7f2-126">Throw 키워드는 ErrorRecord 개체를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-126">The Throw keyword can generate an ErrorRecord object.</span></span> <span data-ttu-id="0a7f2-127">ErrorRecord 개체의 Exception 속성에는 RuntimeException 개체가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-127">The Exception property of the ErrorRecord object contains a RuntimeException object.</span></span> <span data-ttu-id="0a7f2-128">ErrorRecord 개체와 RuntimeException 개체의 나머지 부분은 Throw 키워드가 throw 하는 개체에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-128">The remainder of the ErrorRecord object and the RuntimeException object vary with the object that the Throw keyword throws.</span></span>

<span data-ttu-id="0a7f2-129">RunTimeException 개체가 ErrorRecord 개체에 래핑되어 ErrorRecord 개체가 자동으로 $Error 자동으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-129">The RunTimeException object is wrapped in an ErrorRecord object, and the ErrorRecord object is automatically saved in the $Error automatic variable.</span></span>

## <a name="using-throw-to-create-a-mandatory-parameter"></a><span data-ttu-id="0a7f2-130">THROW를 사용 하 여 필수 매개 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="0a7f2-130">USING THROW TO CREATE A MANDATORY PARAMETER</span></span>

<span data-ttu-id="0a7f2-131">Throw 키워드를 사용 하 여 함수 매개 변수를 필수로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-131">You can use the Throw keyword to make a function parameter mandatory.</span></span>

<span data-ttu-id="0a7f2-132">매개 변수 키워드의 필수 매개 변수를 사용 하는 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-132">This is an alternative to using the Mandatory parameter of the Parameter keyword.</span></span> <span data-ttu-id="0a7f2-133">필수 매개 변수를 사용 하는 경우 시스템은 사용자에 게 필요한 매개 변수 값을 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-133">When you use the Mandatory parameter, the system prompts the user for the required parameter value.</span></span> <span data-ttu-id="0a7f2-134">Throw 키워드를 사용 하는 경우 명령에서 오류 레코드를 중지 하 고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-134">When you use the Throw keyword, the command stops and displays the error record.</span></span>

<span data-ttu-id="0a7f2-135">예를 들어 매개 변수 하위 식의 Throw 키워드는 함수에서 Path 매개 변수를 필수 매개 변수로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-135">For example, the Throw keyword in the parameter subexpression makes the Path parameter a required parameter in the function.</span></span>

<span data-ttu-id="0a7f2-136">이 경우 Throw 키워드는 메시지 문자열을 throw 하지만 Path 매개 변수가 지정 되지 않은 경우에는 종료 오류를 생성 하는 Throw 키워드가 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-136">In this case, the Throw keyword throws a message string, but it is the presence of the Throw keyword that generates the terminating error if the Path parameter is not specified.</span></span> <span data-ttu-id="0a7f2-137">Throw 뒤에 오는 식은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="0a7f2-137">The expression that follows Throw is optional.</span></span>

```powershell
function Get-XMLFiles
{
  param ($path = $(throw "The Path parameter is required."))
  dir -path $path\*.xml -recurse |
    sort lastwritetime |
      ft lastwritetime, attributes, name  -auto
}
```

## <a name="see-also"></a><span data-ttu-id="0a7f2-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a7f2-138">SEE ALSO</span></span>

[<span data-ttu-id="0a7f2-139">about_Break</span><span class="sxs-lookup"><span data-stu-id="0a7f2-139">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="0a7f2-140">about_Continue</span><span class="sxs-lookup"><span data-stu-id="0a7f2-140">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="0a7f2-141">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="0a7f2-141">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="0a7f2-142">about_Trap</span><span class="sxs-lookup"><span data-stu-id="0a7f2-142">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="0a7f2-143">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="0a7f2-143">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)

---
description: 변수가 PowerShell에서 사용할 수 있는 값을 저장 하는 방법에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: 59a611cf49635f0391d3f3cc18bcf6d06a688638
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223217"
---
# <a name="about-variables"></a><span data-ttu-id="5c904-104">변수 정보</span><span class="sxs-lookup"><span data-stu-id="5c904-104">About Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="5c904-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="5c904-105">Short description</span></span>

<span data-ttu-id="5c904-106">변수가 PowerShell에서 사용할 수 있는 값을 저장 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-106">Describes how variables store values that can be used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="5c904-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-107">Long description</span></span>

<span data-ttu-id="5c904-108">모든 유형의 값을 PowerShell 변수에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-108">You can store all types of values in PowerShell variables.</span></span> <span data-ttu-id="5c904-109">예를 들어 명령 결과를 저장 하 고 명령 및 식에 사용 되는 요소 (예: 이름, 경로, 설정 및 값)를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-109">For example, store the results of commands, and store elements that are used in commands and expressions, such as names, paths, settings, and values.</span></span>

<span data-ttu-id="5c904-110">변수는 값이 저장 되는 메모리의 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-110">A variable is a unit of memory in which values are stored.</span></span> <span data-ttu-id="5c904-111">PowerShell에서 변수는 `$` , 또는와 같이 달러 기호 ()로 시작 하는 텍스트 문자열로 표시 됩니다 `$a` `$process` `$my_var` .</span><span class="sxs-lookup"><span data-stu-id="5c904-111">In PowerShell, variables are represented by text strings that begin with a dollar sign (`$`), such as `$a`, `$process`, or `$my_var`.</span></span>

<span data-ttu-id="5c904-112">변수 이름은 대/소문자를 구분 하지 않으며 공백과 특수 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-112">Variable names aren't case-sensitive, and can include spaces and special characters.</span></span> <span data-ttu-id="5c904-113">그러나 특수 문자 및 공백을 포함 하는 변수 이름은 사용 하기 어렵고 사용 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-113">But, variable names that include special characters and spaces are difficult to use and should be avoided.</span></span> <span data-ttu-id="5c904-114">자세한 내용은 [특수 문자를 포함 하는 변수 이름](#variable-names-that-include-special-characters)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c904-114">For more information, see [Variable names that include special characters](#variable-names-that-include-special-characters).</span></span>

<span data-ttu-id="5c904-115">PowerShell에는 여러 가지 유형의 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-115">There are several different types of variables in PowerShell.</span></span>

- <span data-ttu-id="5c904-116">사용자가 만든 변수: 사용자가 만든 변수를 사용자가 만들고 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-116">User-created variables: User-created variables are created and maintained by the user.</span></span> <span data-ttu-id="5c904-117">기본적으로 powershell 명령줄에서 만든 변수는 PowerShell 창이 열려 있는 동안에만 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-117">By default, the variables that you create at the PowerShell command line exist only while the PowerShell window is open.</span></span> <span data-ttu-id="5c904-118">PowerShell 창이 닫히면 변수가 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-118">When the PowerShell windows is closed, the variables are deleted.</span></span> <span data-ttu-id="5c904-119">변수를 저장 하려면 PowerShell 프로필에 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-119">To save a variable, add it to your PowerShell profile.</span></span> <span data-ttu-id="5c904-120">전역, 스크립트 또는 로컬 범위를 사용 하 여 스크립트에서 변수를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-120">You can also create variables in scripts with global, script, or local scope.</span></span>

- <span data-ttu-id="5c904-121">자동 변수: 자동 변수는 PowerShell의 상태를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-121">Automatic variables: Automatic variables store the state of PowerShell.</span></span> <span data-ttu-id="5c904-122">이러한 변수는 PowerShell에서 만들어지며 PowerShell은 정확성을 유지 하기 위해 필요에 따라 해당 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-122">These variables are created by PowerShell, and PowerShell changes their values as required to maintain their accuracy.</span></span> <span data-ttu-id="5c904-123">사용자는 이러한 변수의 값을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-123">Users can't change the value of these variables.</span></span> <span data-ttu-id="5c904-124">예를 들어 `$PSHOME` 변수는 PowerShell 설치 디렉터리에 대 한 경로를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-124">For example, the `$PSHOME` variable stores the path to the PowerShell installation directory.</span></span>

  <span data-ttu-id="5c904-125">자동 변수에 대 한 자세한 내용, 목록 및 설명은 [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c904-125">For more information, a list, and a description of the automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="5c904-126">기본 설정 변수: 기본 설정 변수는 PowerShell에 대 한 사용자 기본 설정을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-126">Preference variables: Preference variables store user preferences for PowerShell.</span></span> <span data-ttu-id="5c904-127">이러한 변수는 PowerShell에서 만들어지며 기본값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-127">These variables are created by PowerShell and are populated with default values.</span></span> <span data-ttu-id="5c904-128">사용자는 이러한 변수의 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-128">Users can change the values of these variables.</span></span> <span data-ttu-id="5c904-129">예를 들어 `$MaximumHistoryCount` 변수는 세션 기록의 최대 항목 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-129">For example, the `$MaximumHistoryCount` variable determines the maximum number of entries in the session history.</span></span>

  <span data-ttu-id="5c904-130">기본 설정 변수에 대 한 자세한 내용, 목록 및 설명은 [about_Preference_Variables](about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c904-130">For more information, a list, and a description of the preference variables, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="working-with-variables"></a><span data-ttu-id="5c904-131">변수 작업</span><span class="sxs-lookup"><span data-stu-id="5c904-131">Working with variables</span></span>

<span data-ttu-id="5c904-132">새 변수를 만들려면 대입문을 사용 하 여 변수에 값을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-132">To create a new variable, use an assignment statement to assign a value to the variable.</span></span> <span data-ttu-id="5c904-133">변수를 사용 하기 전에 선언 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-133">You don't have to declare the variable before using it.</span></span> <span data-ttu-id="5c904-134">모든 변수의 기본값은 `$null` 입니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-134">The default value of all variables is `$null`.</span></span>

<span data-ttu-id="5c904-135">PowerShell 세션의 모든 변수 목록을 가져오려면를 입력 `Get-Variable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-135">To get a list of all the variables in your PowerShell session, type `Get-Variable`.</span></span> <span data-ttu-id="5c904-136">변수 이름은 `$` 변수를 참조 하는 데 사용 되는 앞에 달러 () 기호 없이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-136">The variable names are displayed without the preceding dollar (`$`) sign that is used to reference variables.</span></span>

<span data-ttu-id="5c904-137">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="5c904-137">For example:</span></span>

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

<span data-ttu-id="5c904-138">변수는 명령 결과를 저장 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-138">Variables are useful for storing the results of commands.</span></span>

<span data-ttu-id="5c904-139">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="5c904-139">For example:</span></span>

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

<span data-ttu-id="5c904-140">변수의 값을 표시 하려면 변수 이름 앞에 달러 기호 ()를 입력 `$` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-140">To display the value of a variable, type the variable name, preceded by a dollar sign (`$`).</span></span>

<span data-ttu-id="5c904-141">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="5c904-141">For example:</span></span>

```powershell
$MyVariable
```

```Output
1
2
3
```

```powershell
$Today
```

```Output
Tuesday, September 3, 2019 09:46:46
```

<span data-ttu-id="5c904-142">변수의 값을 변경 하려면 변수에 새 값을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-142">To change the value of a variable, assign a new value to the variable.</span></span>

<span data-ttu-id="5c904-143">다음 예에서는 변수의 값을 표시 `$MyVariable` 하 고 변수 값을 변경한 다음 새 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-143">The following examples display the value of the `$MyVariable` variable, changes the value of the variable, and then displays the new value.</span></span>

```powershell
$MyVariable = 1, 2, 3
$MyVariable
```

```Output
1
2
3
```

```powershell
$MyVariable = "The green cat."
$MyVariable
```

```Output
The green cat.
```

<span data-ttu-id="5c904-144">변수 값을 삭제 하려면 cmdlet을 사용 `Clear-Variable` 하거나 값을로 변경 `$null` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-144">To delete the value of a variable, use the `Clear-Variable` cmdlet or change the value to `$null`.</span></span>

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

<span data-ttu-id="5c904-145">변수를 삭제 하려면 [변수 제거](xref:Microsoft.PowerShell.Utility.Remove-Variable) 또는 [항목 제거](xref:Microsoft.PowerShell.Management.Remove-Item)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-145">To delete the variable, use [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) or [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item).</span></span>

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

## <a name="types-of-variables"></a><span data-ttu-id="5c904-146">변수 유형</span><span class="sxs-lookup"><span data-stu-id="5c904-146">Types of variables</span></span>

<span data-ttu-id="5c904-147">정수, 문자열, 배열 및 해시 테이블을 포함 하 여 모든 형식의 개체를 변수에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-147">You can store any type of object in a variable, including integers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="5c904-148">프로세스, 서비스, 이벤트 로그 및 컴퓨터를 나타내는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-148">And, objects that represent processes, services, event logs, and computers.</span></span>

<span data-ttu-id="5c904-149">PowerShell 변수는 느슨하게 형식화 됩니다. 즉, 특정 유형의 개체로 제한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-149">PowerShell variables are loosely typed, which means that they aren't limited to a particular type of object.</span></span> <span data-ttu-id="5c904-150">단일 변수에는 서로 다른 형식의 개체에 대 한 컬렉션 또는 배열을 동시에 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-150">A single variable can even contain a collection, or array, of different types of objects at the same time.</span></span>

<span data-ttu-id="5c904-151">변수의 데이터 형식은 변수의 값에 대 한 .NET 형식에 의해 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-151">The data type of a variable is determined by the .NET types of the values of the variable.</span></span> <span data-ttu-id="5c904-152">변수의 개체 유형을 보려면 [Get 멤버](xref:Microsoft.PowerShell.Utility.Get-Member)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-152">To view a variable's object type, use [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member).</span></span>

<span data-ttu-id="5c904-153">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="5c904-153">For example:</span></span>

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

<span data-ttu-id="5c904-154">형식 특성 및 캐스트 표기법을 사용 하 여 해당 형식으로 변환할 수 있는 특정 개체 형식이 나 개체만이 변수에 포함 될 수 있도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-154">You can use a type attribute and cast notation to ensure that a variable can contain only specific object types or objects that can be converted to that type.</span></span> <span data-ttu-id="5c904-155">다른 형식의 값을 할당 하려고 하면 PowerShell에서 값을 해당 형식으로 변환 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-155">If you try to assign a value of another type, PowerShell tries to convert the value to its type.</span></span> <span data-ttu-id="5c904-156">형식을 변환할 수 없는 경우 대입문은 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-156">If the type can't be converted, the assignment statement fails.</span></span>

<span data-ttu-id="5c904-157">Cast 표기법을 사용 하려면 변수 이름 앞에 대괄호로 묶인 유형 이름 (대입문의 왼쪽에 있는)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-157">To use cast notation, enter a type name, enclosed in brackets, before the variable name (on the left side of the assignment statement).</span></span> <span data-ttu-id="5c904-158">다음 예에서는 `$number` 정수만 포함할 수 있는 변수, 문자열만 포함할 수 있는 `$words` 변수 및 `$dates` **DateTime** 개체만 포함할 수 있는 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-158">The following example creates a `$number` variable that can contain only integers, a `$words` variable that can contain only strings, and a `$dates` variable that can contain only **DateTime** objects.</span></span>

```powershell
[int]$number = 8
$number = "12345"  # The string is converted to an integer.
$number = "Hello"
```

```Output
Cannot convert value "Hello" to type "System.Int32". Error: "Input string was
 not in a correct format."
At line:1 char:1
+ $number = "Hello"
+ ~~~~~~~~~~~~~~~~~
+ CategoryInfo          : MetadataError: (:) [],
    ArgumentTransformationMetadataException
+ FullyQualifiedErrorId : RuntimeException
```

```powershell
[string]$words = "Hello"
$words = 2       # The integer is converted to a string.
$words += 10     # The plus (+) sign concatenates the strings.
$words
```

```Output
210
```

```powershell
[datetime] $dates = "09/12/91"  # The string is converted to a DateTime object.
$dates
```

```Output
Thursday, September 12, 1991 00:00:00
```

```powershell
$dates = 10    # The integer is converted to a DateTime object.
$dates
```

```Output
Monday, January 1, 0001 00:00:00
```

## <a name="using-variables-in-commands-and-expressions"></a><span data-ttu-id="5c904-159">명령 및 식에서 변수 사용</span><span class="sxs-lookup"><span data-stu-id="5c904-159">Using variables in commands and expressions</span></span>

<span data-ttu-id="5c904-160">명령 또는 식에서 변수를 사용 하려면 변수 이름 앞에 달러 () 기호를 입력 합니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="5c904-160">To use a variable in a command or expression, type the variable name, preceded by the dollar (`$`) sign.</span></span>

<span data-ttu-id="5c904-161">변수 이름 및 달러 기호가 따옴표로 묶여 있지 않거나 큰따옴표 ()로 묶은 경우에는 `"` 변수 값이 명령 또는 식에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-161">If the variable name and dollar sign aren't enclosed in quotation marks, or if they're enclosed in double quotation (`"`) marks, the value of the variable is used in the command or expression.</span></span>

<span data-ttu-id="5c904-162">변수 이름과 달러 기호가 작은따옴표 ()로 묶여 있으면 `'` 식에 변수 이름이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-162">If the variable name and dollar sign are enclosed in single quotation (`'`) marks, the variable name is used in the expression.</span></span>

<span data-ttu-id="5c904-163">PowerShell에서 따옴표를 사용 하는 방법에 대 한 자세한 내용은 [about_Quoting_Rules](about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c904-163">For more information about using quotation marks in PowerShell, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="5c904-164">이 예에서는 `$PROFILE` powershell 콘솔의 powershell 사용자 프로필 파일 경로에 해당 하는 변수의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-164">This example gets the value of the `$PROFILE` variable, which is the path to the PowerShell user profile file in the PowerShell console.</span></span>

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
```

<span data-ttu-id="5c904-165">이 예제에서는 **notepad.exe** 에서 PowerShell 프로필을 열 수 있는 두 명령이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-165">In this example, two commands are shown that can open the PowerShell profile in **notepad.exe**.</span></span> <span data-ttu-id="5c904-166">큰따옴표 () 표시가 있는 예제는 `"` 변수의 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-166">The example with double-quote (`"`) marks uses the variable's value.</span></span>

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

<span data-ttu-id="5c904-167">다음 예에서는 `'` 변수를 리터럴 텍스트로 처리 하는 작은따옴표 ()를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-167">The following examples use single-quote (`'`) marks that treat the variable as literal text.</span></span>

```powershell
'$PROFILE'
```

```Output
$PROFILE
```

```powershell
'Use the $PROFILE variable.'
```

```Output
Use the $PROFILE variable.
```

## <a name="variable-names-that-include-special-characters"></a><span data-ttu-id="5c904-168">특수 문자를 포함 하는 변수 이름</span><span class="sxs-lookup"><span data-stu-id="5c904-168">Variable names that include special characters</span></span>

<span data-ttu-id="5c904-169">변수 이름은 달러 ( `$` ) 기호로 시작 하 고 영숫자 문자 및 특수 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-169">Variable names begin with a dollar (`$`) sign and can include alphanumeric characters and special characters.</span></span> <span data-ttu-id="5c904-170">변수 이름 길이는 사용 가능한 메모리에 의해서만 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-170">The variable name length is limited only by available memory.</span></span>

<span data-ttu-id="5c904-171">가장 좋은 방법은 변수 이름에 영숫자 문자와 밑줄 () 문자만 포함 하는 것입니다 `_` .</span><span class="sxs-lookup"><span data-stu-id="5c904-171">The best practice is that variable names include only alphanumeric characters and the underscore (`_`) character.</span></span> <span data-ttu-id="5c904-172">공백과 기타 특수 문자를 포함 하는 변수 이름은 사용 하기 어렵고 사용 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-172">Variable names that include spaces and other special characters, are difficult to use and should be avoided.</span></span>

<span data-ttu-id="5c904-173">영숫자 변수 이름에는 다음 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-173">Alphanumeric variable names can contain these characters:</span></span>

- <span data-ttu-id="5c904-174">이러한 범주의 유니코드 문자는 **Lu** , **Ll** , **Lt** , **Lm** ,가 **Lo** 중 또는 **Nd** 입니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-174">Unicode characters from these categories: **Lu** , **Ll** , **Lt** , **Lm** , **Lo** , or **Nd**.</span></span>
- <span data-ttu-id="5c904-175">밑줄 ( `_` ) 문자.</span><span class="sxs-lookup"><span data-stu-id="5c904-175">Underscore (`_`) character.</span></span>
- <span data-ttu-id="5c904-176">물음표 ( `?` ) 문자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-176">Question mark (`?`) character.</span></span>

<span data-ttu-id="5c904-177">다음 목록에는 유니코드 범주 설명이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-177">The following list contains the Unicode category descriptions.</span></span> <span data-ttu-id="5c904-178">자세한 내용은 [자세한 내용은 system.globalization.unicodecategory](/dotnet/api/system.globalization.unicodecategory)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c904-178">For more information, see [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory).</span></span>

- <span data-ttu-id="5c904-179">**Lu** -UppercaseLetter</span><span class="sxs-lookup"><span data-stu-id="5c904-179">**Lu** - UppercaseLetter</span></span>
- <span data-ttu-id="5c904-180">**Ll** -LowercaseLetter</span><span class="sxs-lookup"><span data-stu-id="5c904-180">**Ll** - LowercaseLetter</span></span>
- <span data-ttu-id="5c904-181">**Lt** -TitlecaseLetter</span><span class="sxs-lookup"><span data-stu-id="5c904-181">**Lt** - TitlecaseLetter</span></span>
- <span data-ttu-id="5c904-182">**Lm** -ModifierLetter</span><span class="sxs-lookup"><span data-stu-id="5c904-182">**Lm** - ModifierLetter</span></span>
- <span data-ttu-id="5c904-183">**가-** otherletter</span><span class="sxs-lookup"><span data-stu-id="5c904-183">**Lo** - OtherLetter</span></span>
- <span data-ttu-id="5c904-184">**Nd** -DecimalDigitNumber</span><span class="sxs-lookup"><span data-stu-id="5c904-184">**Nd** - DecimalDigitNumber</span></span>

<span data-ttu-id="5c904-185">공백 또는 특수 문자를 포함 하는 변수 이름을 만들거나 표시 하려면 변수 이름을 중괄호 ( `{}` ) 문자로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-185">To create or display a variable name that includes spaces or special characters, enclose the variable name with the curly braces (`{}`) characters.</span></span>
<span data-ttu-id="5c904-186">변수 이름 문자를 리터럴로 해석 하는 중괄호 직접 PowerShell입니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-186">The curly braces direct PowerShell to interpret the variable name's characters as literals.</span></span>

<span data-ttu-id="5c904-187">특수 문자 변수 이름에는 다음 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-187">Special character variable names can contain these characters:</span></span>

- <span data-ttu-id="5c904-188">다음 예외를 제외 하 고 모든 유니코드 문자.</span><span class="sxs-lookup"><span data-stu-id="5c904-188">Any Unicode character, with the following exceptions:</span></span>
  - <span data-ttu-id="5c904-189">닫는 중괄호 ( `}` ) 문자 (U + 007D)입니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-189">The closing curly brace (`}`) character (U+007D).</span></span>
  - <span data-ttu-id="5c904-190">억음 ( `` ` `` ) 문자 (U + 0060)입니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-190">The backtick (`` ` ``) character (U+0060).</span></span> <span data-ttu-id="5c904-191">억음은 리터럴로 처리 되도록 유니코드 문자를 이스케이프 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-191">The backtick is used to escape Unicode characters so they're treated as literals.</span></span>

<span data-ttu-id="5c904-192">PowerShell에는 `$$` `$?` `$^` `$_` 영숫자 및 특수 문자를 포함 하는,,, 등의 예약 된 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-192">PowerShell has reserved variables such as `$$`, `$?`, `$^`, and `$_` that contain alphanumeric and special characters.</span></span> <span data-ttu-id="5c904-193">자세한 내용은 [about_Automatic_Variables](about_automatic_variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c904-193">For more information, see [about_Automatic_Variables](about_automatic_variables.md).</span></span>

<span data-ttu-id="5c904-194">예를 들어 다음 명령은 라는 변수를 만듭니다 `save-items` .</span><span class="sxs-lookup"><span data-stu-id="5c904-194">For example, the following command creates the variable named `save-items`.</span></span> <span data-ttu-id="5c904-195">변수 이름에는 `{}` 하이픈 () 특수 문자를 포함 하므로 중괄호 ()가 필요 합니다 `-` .</span><span class="sxs-lookup"><span data-stu-id="5c904-195">The curly braces (`{}`) are needed because variable name includes a hyphen (`-`) special character.</span></span>

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

<span data-ttu-id="5c904-196">다음 명령은 환경 변수로 표시 되는 디렉터리의 자식 항목을 가져옵니다 `ProgramFiles(x86)` .</span><span class="sxs-lookup"><span data-stu-id="5c904-196">The following command gets the child items in the directory that is represented by the `ProgramFiles(x86)` environment variable.</span></span>

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

<span data-ttu-id="5c904-197">중괄호를 포함 하는 변수 이름을 참조 하려면 변수 이름을 중괄호로 묶고 중괄호를 이스케이프 하려면 억음 문자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-197">To reference a variable name that includes braces, enclose the variable name in braces, and use the backtick character to escape the braces.</span></span> <span data-ttu-id="5c904-198">예를 들어 형식 이라는 변수를 만들려면 `this{value}is` 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-198">For example, to create a variable named `this{value}is` type:</span></span>

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a><span data-ttu-id="5c904-199">변수 및 범위</span><span class="sxs-lookup"><span data-stu-id="5c904-199">Variables and scope</span></span>

<span data-ttu-id="5c904-200">기본적으로 변수는 생성 된 범위 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-200">By default, variables are only available in the scope in which they're created.</span></span>

<span data-ttu-id="5c904-201">예를 들어 함수에서 만든 변수는 함수 내 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-201">For example, a variable that you create in a function is available only within the function.</span></span> <span data-ttu-id="5c904-202">스크립트에서 만든 변수는 스크립트 내 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-202">A variable that you create in a script is available only within the script.</span></span> <span data-ttu-id="5c904-203">스크립트를 점으로 원본으로 만들면 변수가 현재 범위에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-203">If you dot-source the script, the variable is added to the current scope.</span></span> <span data-ttu-id="5c904-204">자세한 내용은 [about_Scopes](about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c904-204">For more information, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="5c904-205">범위 한정자를 사용 하 여 변수의 기본 범위를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-205">You can use a scope modifier to change the default scope of the variable.</span></span> <span data-ttu-id="5c904-206">다음 식에서는 라는 변수를 만듭니다 `Computers` .</span><span class="sxs-lookup"><span data-stu-id="5c904-206">The following expression creates a variable named `Computers`.</span></span> <span data-ttu-id="5c904-207">변수는 스크립트나 함수에서 생성 된 경우에도 전역 범위를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-207">The variable has a global scope, even when it's created in a script or function.</span></span>

```powershell
$Global:Computers = "Server01"
```

<span data-ttu-id="5c904-208">세션에서 실행 되지 않는 스크립트나 명령의 경우 범위 한정자를 사용 하 여 `Using` 호출 세션 범위의 변수 값을 포함 해야 합니다. 이렇게 하면 세션 외부 코드에서 해당 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-208">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span>

<span data-ttu-id="5c904-209">자세한 내용은 [about_Remote_Variables](about_Remote_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c904-209">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="saving-variables"></a><span data-ttu-id="5c904-210">변수 저장</span><span class="sxs-lookup"><span data-stu-id="5c904-210">Saving variables</span></span>

<span data-ttu-id="5c904-211">만든 변수는 해당 변수를 만든 세션 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-211">Variables that you create are available only in the session in which you create them.</span></span> <span data-ttu-id="5c904-212">세션을 닫으면 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-212">They're lost when you close your session.</span></span>

<span data-ttu-id="5c904-213">시작 하는 모든 PowerShell 세션에서 변수를 만들려면 PowerShell 프로필에 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-213">To create the variable in every PowerShell session that you start, add the variable to your PowerShell profile.</span></span>

<span data-ttu-id="5c904-214">예를 들어 `$VerbosePreference` 모든 powershell 세션에서 변수의 값을 변경 하려면 다음 명령을 powershell 프로필에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-214">For example, to change the value of the `$VerbosePreference` variable in every PowerShell session, add the following command to your PowerShell profile.</span></span>

```powershell
$VerbosePreference = "Continue"
```

<span data-ttu-id="5c904-215">`$PROFILE` **notepad.exe** 와 같은 텍스트 편집기에서 파일을 열어 PowerShell 프로필에이 명령을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-215">You can add this command to your PowerShell profile by opening the `$PROFILE` file in a text editor, such as **notepad.exe**.</span></span> <span data-ttu-id="5c904-216">PowerShell 프로필에 대 한 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c904-216">For more information about PowerShell profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="the-variable-drive"></a><span data-ttu-id="5c904-217">변수: 드라이브</span><span class="sxs-lookup"><span data-stu-id="5c904-217">The Variable: drive</span></span>

<span data-ttu-id="5c904-218">PowerShell 변수 공급자는 `Variable:` 파일 시스템 드라이브를 검색 하 고 작동 하는 드라이브를 만들지만 세션의 변수와 해당 값을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-218">The PowerShell Variable provider creates a `Variable:` drive that looks and acts like a file system drive, but it contains the variables in your session and their values.</span></span>

<span data-ttu-id="5c904-219">드라이브로 변경 하려면 `Variable:` 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-219">To change to the `Variable:` drive, use the following command:</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="5c904-220">드라이브의 항목 및 변수를 나열 하려면 `Variable:` 또는 cmdlet을 사용 `Get-Item` `Get-ChildItem` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-220">To list the items and variables in the `Variable:` drive, use the `Get-Item` or `Get-ChildItem` cmdlets.</span></span>

```powershell
Get-ChildItem Variable:
```

<span data-ttu-id="5c904-221">특정 변수 값을 가져오려면 파일 시스템 표기법을 사용 하 여 드라이브의 이름과 변수의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-221">To get the value of a particular variable, use file system notation to specify the name of the drive and the name of the variable.</span></span> <span data-ttu-id="5c904-222">예를 들어 `$PSCulture` 자동 변수를 가져오려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-222">For example, to get the `$PSCulture` automatic variable, use the following command.</span></span>

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

<span data-ttu-id="5c904-223">드라이브 및 PowerShell 변수 공급자에 대 한 자세한 정보를 표시 하려면 `Variable:` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-223">To display more information about the `Variable:` drive and the PowerShell Variable provider, type:</span></span>

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a><span data-ttu-id="5c904-224">공급자 경로를 사용 하는 변수 구문</span><span class="sxs-lookup"><span data-stu-id="5c904-224">Variable syntax with provider paths</span></span>

<span data-ttu-id="5c904-225">공급자 경로에 달러 ( `$` ) 기호를 접두사로 사용 하 고 [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) 인터페이스를 구현 하는 모든 공급자의 콘텐츠에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-225">You can prefix a provider path with the dollar (`$`) sign, and access the content of any provider that implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>

<span data-ttu-id="5c904-226">다음 기본 제공 PowerShell 공급자는이 표기법을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-226">The following built-in PowerShell providers support this notation:</span></span>

- [<span data-ttu-id="5c904-227">about_Environment_Provider</span><span class="sxs-lookup"><span data-stu-id="5c904-227">about_Environment_Provider</span></span>](about_Environment_Provider.md)
- [<span data-ttu-id="5c904-228">about_Variable_Provider</span><span class="sxs-lookup"><span data-stu-id="5c904-228">about_Variable_Provider</span></span>](about_Variable_Provider.md)
- [<span data-ttu-id="5c904-229">about_Function_Provider</span><span class="sxs-lookup"><span data-stu-id="5c904-229">about_Function_Provider</span></span>](about_Function_Provider.md)
- [<span data-ttu-id="5c904-230">about_Alias_Provider</span><span class="sxs-lookup"><span data-stu-id="5c904-230">about_Alias_Provider</span></span>](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a><span data-ttu-id="5c904-231">변수 cmdlet</span><span class="sxs-lookup"><span data-stu-id="5c904-231">The variable cmdlets</span></span>

<span data-ttu-id="5c904-232">PowerShell에는 변수를 관리 하도록 설계 된 cmdlet 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-232">PowerShell includes a set of cmdlets that are designed to manage variables.</span></span>

<span data-ttu-id="5c904-233">Cmdlet을 나열 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-233">To list the cmdlets, type:</span></span>

```powershell
Get-Command -Noun Variable
```

<span data-ttu-id="5c904-234">특정 cmdlet에 대 한 도움말을 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-234">To get help for a specific cmdlet, type:</span></span>

```powershell
Get-Help <cmdlet-name>
```

| <span data-ttu-id="5c904-235">Cmdlet 이름</span><span class="sxs-lookup"><span data-stu-id="5c904-235">Cmdlet Name</span></span>       | <span data-ttu-id="5c904-236">Description</span><span class="sxs-lookup"><span data-stu-id="5c904-236">Description</span></span>                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | <span data-ttu-id="5c904-237">변수 값을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-237">Deletes the value of a variable.</span></span>           |
| `Get-Variable`    | <span data-ttu-id="5c904-238">현재 콘솔에 있는 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-238">Gets the variables in the current console.</span></span> |
| `New-Variable`    | <span data-ttu-id="5c904-239">새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-239">Creates a new variable.</span></span>                    |
| `Remove-Variable` | <span data-ttu-id="5c904-240">변수와 그 값을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-240">Deletes a variable and its value.</span></span>          |
| `Set-Variable`    | <span data-ttu-id="5c904-241">변수의 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c904-241">Changes the value of a variable.</span></span>           |

## <a name="see-also"></a><span data-ttu-id="5c904-242">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5c904-242">See also</span></span>

[<span data-ttu-id="5c904-243">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="5c904-243">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="5c904-244">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="5c904-244">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="5c904-245">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="5c904-245">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="5c904-246">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="5c904-246">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="5c904-247">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="5c904-247">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="5c904-248">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="5c904-248">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="5c904-249">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="5c904-249">about_Remote_Variables</span></span>](about_Remote_Variables.md)

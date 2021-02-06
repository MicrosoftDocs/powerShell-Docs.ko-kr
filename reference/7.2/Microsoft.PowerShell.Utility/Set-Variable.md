---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 573bb0054b60e8c17b79da72ebc712c6ef5575a5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602265"
---
# <span data-ttu-id="bb8a7-102">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="bb8a7-102">Set-Variable</span></span>

## <span data-ttu-id="bb8a7-103">개요</span><span class="sxs-lookup"><span data-stu-id="bb8a7-103">SYNOPSIS</span></span>
<span data-ttu-id="bb8a7-104">변수 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-104">Sets the value of a variable.</span></span> <span data-ttu-id="bb8a7-105">요청한 이름이 있는 변수가 없으면 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-105">Creates the variable if one with the requested name does not exist.</span></span>

## <span data-ttu-id="bb8a7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bb8a7-106">SYNTAX</span></span>

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bb8a7-107">설명</span><span class="sxs-lookup"><span data-stu-id="bb8a7-107">DESCRIPTION</span></span>

<span data-ttu-id="bb8a7-108">`Set-Variable`Cmdlet은 지정 된 변수에 값을 할당 하거나 현재 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-108">The `Set-Variable` cmdlet assigns a value to a specified variable or changes the current value.</span></span> <span data-ttu-id="bb8a7-109">변수가 없는 경우 cmdlet이 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-109">If the variable does not exist, the cmdlet creates it.</span></span>

## <span data-ttu-id="bb8a7-110">예제</span><span class="sxs-lookup"><span data-stu-id="bb8a7-110">EXAMPLES</span></span>

### <span data-ttu-id="bb8a7-111">예 1: 변수를 설정 하 고 해당 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="bb8a7-111">Example 1: Set a variable and get its value</span></span>

<span data-ttu-id="bb8a7-112">이러한 명령은 변수의 값을로 설정 하 `$desc` `A description` 고 변수 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-112">These commands set the value of the `$desc` variable to `A description`, and then gets the value of the variable.</span></span>

```powershell
Set-Variable -Name "desc" -Value "A description"
Get-Variable -Name "desc"
```

```Output
Name                           Value
----                           -----
desc                           A description
```

### <span data-ttu-id="bb8a7-113">예 2: 읽기 전용 전역 변수 설정</span><span class="sxs-lookup"><span data-stu-id="bb8a7-113">Example 2: Set a global, read-only variable</span></span>

<span data-ttu-id="bb8a7-114">이 예에서는 시스템의 모든 프로세스가 포함 된 읽기 전용의 전역 변수를 만든 다음 변수의 모든 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-114">This example creates a global, read-only variable that contains all processes on the system, and then it displays all properties of the variable.</span></span>

```powershell
Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru |
    Format-List -Property *
```

<span data-ttu-id="bb8a7-115">이 명령은 cmdlet을 사용 하 여 `Set-Variable` 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-115">The command uses the `Set-Variable` cmdlet to create the variable.</span></span> <span data-ttu-id="bb8a7-116">**PassThru** 매개 변수를 사용 하 여 새 변수를 나타내는 개체를 만든 다음 파이프라인 연산자 ()를 사용 하 여 `|` 개체를 cmdlet으로 전달 `Format-List` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-116">It uses the **PassThru** parameter to create an object representing the new variable, and it uses the pipeline operator (`|`) to pass the object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="bb8a7-117">의 **Property** 매개 변수를 `Format-List` all () 값과 함께 사용 `*` 하 여 새로 만든 변수의 모든 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-117">It uses the **Property** parameter of `Format-List` with a value of all (`*`) to display all properties of the newly created variable.</span></span>

<span data-ttu-id="bb8a7-118">값은 `(Get-Process)` 변수에 저장 하기 전에 실행 되도록 괄호로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-118">The value, `(Get-Process)`, is enclosed in parentheses to ensure that it is executed before being stored in the variable.</span></span> <span data-ttu-id="bb8a7-119">그렇지 않으면 변수는 "**Get Process**" 라는 단어를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-119">Otherwise, the variable contains the words "**Get-Process**".</span></span>

### <span data-ttu-id="bb8a7-120">예제 3: public 및 private 변수 이해</span><span class="sxs-lookup"><span data-stu-id="bb8a7-120">Example 3: Understand public vs. private variables</span></span>

<span data-ttu-id="bb8a7-121">이 예에서는 변수의 표시 유형을로 변경 하는 방법을 보여 줍니다 `Private` .</span><span class="sxs-lookup"><span data-stu-id="bb8a7-121">This example shows how to change the visibility of a variable to `Private`.</span></span> <span data-ttu-id="bb8a7-122">이 변수는 필요한 권한을 가진 스크립트를 통해 읽거나 변경할 수 있지만 사용자에게 표시되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-122">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

```
PS C:\> New-Variable -Name "counter" -Visibility Public -Value 26
PS C:\> $Counter
26

PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}
Counter               26

PS C:\> Set-Variable -Name "counter" -Visibility Private
PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"

PS C:\> .\use-counter.ps1
#Commands completed successfully.
```

<span data-ttu-id="bb8a7-123">이 명령은 변수의 표시 유형을 Private으로 변경 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-123">This command shows how to change the visibility of a variable to Private.</span></span> <span data-ttu-id="bb8a7-124">이 변수는 필요한 권한을 가진 스크립트를 통해 읽거나 변경할 수 있지만 사용자에게 표시되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-124">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

## <span data-ttu-id="bb8a7-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bb8a7-125">PARAMETERS</span></span>

### <span data-ttu-id="bb8a7-126">-Description</span><span class="sxs-lookup"><span data-stu-id="bb8a7-126">-Description</span></span>

<span data-ttu-id="bb8a7-127">변수에 대한 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-127">Specifies the description of the variable.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb8a7-128">-제외</span><span class="sxs-lookup"><span data-stu-id="bb8a7-128">-Exclude</span></span>

<span data-ttu-id="bb8a7-129">이 cmdlet이 작업에서 제외 하는 항목의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-129">Specifies an array of items that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="bb8a7-130">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-130">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="bb8a7-131">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-131">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="bb8a7-132">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-132">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bb8a7-133">-Force</span><span class="sxs-lookup"><span data-stu-id="bb8a7-133">-Force</span></span>

<span data-ttu-id="bb8a7-134">기존 읽기 전용 변수와 이름이 같은 변수를 만들거나 읽기 전용 변수의 값을 변경할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-134">Allows you to create a variable with the same name as an existing read-only variable, or to change the value of a read-only variable.</span></span>

<span data-ttu-id="bb8a7-135">기본적으로 변수에 또는의 옵션 값이 없는 경우 변수를 덮어쓸 수 있습니다 `ReadOnly` `Constant` .</span><span class="sxs-lookup"><span data-stu-id="bb8a7-135">By default, you can overwrite a variable, unless the variable has an option value of `ReadOnly` or `Constant`.</span></span> <span data-ttu-id="bb8a7-136">자세한 내용은 **Option** 매개 변수를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-136">For more information, see the **Option** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb8a7-137">-포함</span><span class="sxs-lookup"><span data-stu-id="bb8a7-137">-Include</span></span>

<span data-ttu-id="bb8a7-138">이 cmdlet이 작업에 포함 하는 항목의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-138">Specifies an array of items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="bb8a7-139">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-139">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="bb8a7-140">이름 또는 이름 패턴 (예:)을 입력 `c*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-140">Enter a name or name pattern, such as `c*`.</span></span> <span data-ttu-id="bb8a7-141">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-141">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bb8a7-142">-Name</span><span class="sxs-lookup"><span data-stu-id="bb8a7-142">-Name</span></span>

<span data-ttu-id="bb8a7-143">변수 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-143">Specifies the variable name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bb8a7-144">-옵션</span><span class="sxs-lookup"><span data-stu-id="bb8a7-144">-Option</span></span>

<span data-ttu-id="bb8a7-145">변수의 **Options** 속성 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-145">Specifies the value of the **Options** property of the variable.</span></span>

<span data-ttu-id="bb8a7-146">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-146">Valid values are:</span></span>

- <span data-ttu-id="bb8a7-147">`None`: 옵션을 설정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-147">`None`: Sets no options.</span></span> <span data-ttu-id="bb8a7-148">"None"이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-148">("None" is the default.)</span></span>
- <span data-ttu-id="bb8a7-149">`ReadOnly`: 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-149">`ReadOnly`: Can be deleted.</span></span> <span data-ttu-id="bb8a7-150">Force 매개 변수를 사용 하는 경우를 제외 하 고는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-150">Cannot be changed, except by using the Force parameter.</span></span>
- <span data-ttu-id="bb8a7-151">`Constant`: 삭제 하거나 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-151">`Constant`: Cannot be deleted or changed.</span></span> <span data-ttu-id="bb8a7-152">`Constant` 는 변수를 만드는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-152">`Constant` is valid only when you are creating a variable.</span></span> <span data-ttu-id="bb8a7-153">기존 변수의 옵션을로 변경할 수 없습니다 `Constant` .</span><span class="sxs-lookup"><span data-stu-id="bb8a7-153">You cannot change the options of an existing variable to `Constant`.</span></span>
- <span data-ttu-id="bb8a7-154">`Private`: 변수는 현재 범위 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-154">`Private`: The variable is available only in the current scope.</span></span>
- <span data-ttu-id="bb8a7-155">`AllScope`: 변수가 만들어진 모든 새 범위로 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-155">`AllScope`: The variable is copied to any new scopes that are created.</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb8a7-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="bb8a7-156">-PassThru</span></span>

<span data-ttu-id="bb8a7-157">새 변수를 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-157">Returns an object representing the new variable.</span></span> <span data-ttu-id="bb8a7-158">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-158">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb8a7-159">-범위</span><span class="sxs-lookup"><span data-stu-id="bb8a7-159">-Scope</span></span>

<span data-ttu-id="bb8a7-160">변수의 범위를 지정 합니다. 이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-160">Specifies the scope of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bb8a7-161">전역</span><span class="sxs-lookup"><span data-stu-id="bb8a7-161">Global</span></span>
- <span data-ttu-id="bb8a7-162">로컬</span><span class="sxs-lookup"><span data-stu-id="bb8a7-162">Local</span></span>
- <span data-ttu-id="bb8a7-163">스크립트</span><span class="sxs-lookup"><span data-stu-id="bb8a7-163">Script</span></span>
- <span data-ttu-id="bb8a7-164">비공개</span><span class="sxs-lookup"><span data-stu-id="bb8a7-164">Private</span></span>
- <span data-ttu-id="bb8a7-165">현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)입니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-165">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="bb8a7-166">Local이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-166">Local is the default.</span></span>

<span data-ttu-id="bb8a7-167">자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-167">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb8a7-168">-Value</span><span class="sxs-lookup"><span data-stu-id="bb8a7-168">-Value</span></span>

<span data-ttu-id="bb8a7-169">변수의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-169">Specifies the value of the variable.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bb8a7-170">-표시 유형</span><span class="sxs-lookup"><span data-stu-id="bb8a7-170">-Visibility</span></span>

<span data-ttu-id="bb8a7-171">변수를 만든 세션 외부에서도 변수가 표시되는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-171">Determines whether the variable is visible outside of the session in which it was created.</span></span> <span data-ttu-id="bb8a7-172">이 매개 변수는 다른 사용자에 게 전달 되는 스크립트 및 명령에 사용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-172">This parameter is designed for use in scripts and commands that will be delivered to other users.</span></span>

<span data-ttu-id="bb8a7-173">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-173">Valid values are:</span></span>

- <span data-ttu-id="bb8a7-174">Public: 변수가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-174">Public:  The variable is visible.</span></span> <span data-ttu-id="bb8a7-175">"Public"이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-175">("Public" is the default.)</span></span>
- <span data-ttu-id="bb8a7-176">Private: 변수가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-176">Private: The variable is not visible.</span></span>

<span data-ttu-id="bb8a7-177">변수가 private 이면 변수가에서 반환 하는 변수 `Get-Variable` 또는 **변수:** 드라이브의 표시와 같은 변수 목록에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-177">When a variable is private, it does not appear in lists of variables, such as those returned by `Get-Variable`, or in displays of the **Variable:** drive.</span></span> <span data-ttu-id="bb8a7-178">개인 변수의 값을 읽거나 변경하는 명령을 실행하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-178">Commands to read or change the value of a private variable return an error.</span></span> <span data-ttu-id="bb8a7-179">그러나 변수를 정의한 세션에서 명령을 작성한 경우에는 개인 변수를 사용하는 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-179">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: Public
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb8a7-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bb8a7-180">-Confirm</span></span>

<span data-ttu-id="bb8a7-181">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-181">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb8a7-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bb8a7-182">-WhatIf</span></span>

<span data-ttu-id="bb8a7-183">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-183">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="bb8a7-184">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-184">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb8a7-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb8a7-185">CommonParameters</span></span>

<span data-ttu-id="bb8a7-186">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bb8a7-187">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bb8a7-188">입력</span><span class="sxs-lookup"><span data-stu-id="bb8a7-188">INPUTS</span></span>

### <span data-ttu-id="bb8a7-189">System.Object</span><span class="sxs-lookup"><span data-stu-id="bb8a7-189">System.Object</span></span>

<span data-ttu-id="bb8a7-190">변수의 값을 나타내는 개체를로 파이프 할 수 있습니다 `Set-Variable` .</span><span class="sxs-lookup"><span data-stu-id="bb8a7-190">You can pipe an object that represents the value of the variable to `Set-Variable`.</span></span>

## <span data-ttu-id="bb8a7-191">출력</span><span class="sxs-lookup"><span data-stu-id="bb8a7-191">OUTPUTS</span></span>

### <span data-ttu-id="bb8a7-192">None 또는 System.object입니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-192">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="bb8a7-193">**PassThru** 매개 변수를 사용 하는 경우는 `Set-Variable` 새 변수 또는 변경 된 변수를 나타내는 **system.object** 를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-193">When you use the **PassThru** parameter, `Set-Variable` generates a **System.Management.Automation.PSVariable** object representing the new or changed variable.</span></span>
<span data-ttu-id="bb8a7-194">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8a7-194">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="bb8a7-195">참고</span><span class="sxs-lookup"><span data-stu-id="bb8a7-195">NOTES</span></span>

## <span data-ttu-id="bb8a7-196">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bb8a7-196">RELATED LINKS</span></span>

[<span data-ttu-id="bb8a7-197">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="bb8a7-197">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="bb8a7-198">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="bb8a7-198">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="bb8a7-199">New-Variable</span><span class="sxs-lookup"><span data-stu-id="bb8a7-199">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="bb8a7-200">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="bb8a7-200">Remove-Variable</span></span>](Remove-Variable.md)

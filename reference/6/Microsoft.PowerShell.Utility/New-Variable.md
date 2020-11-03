---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: faf8bc399185da402bebb678b02927e0e5628662
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216066"
---
# <span data-ttu-id="ada2e-103">New-Variable</span><span class="sxs-lookup"><span data-stu-id="ada2e-103">New-Variable</span></span>

## <span data-ttu-id="ada2e-104">개요</span><span class="sxs-lookup"><span data-stu-id="ada2e-104">SYNOPSIS</span></span>
<span data-ttu-id="ada2e-105">새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-105">Creates a new variable.</span></span>

## <span data-ttu-id="ada2e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ada2e-106">SYNTAX</span></span>

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="ada2e-107">설명</span><span class="sxs-lookup"><span data-stu-id="ada2e-107">DESCRIPTION</span></span>
<span data-ttu-id="ada2e-108">**새 변수** Cmdlet은 PowerShell에 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-108">The **New-Variable** cmdlet creates a new variable in PowerShell.</span></span>
<span data-ttu-id="ada2e-109">변수를 만드는 동안 값을 할당할 수도 있고 만든 후에 값을 할당하거나 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-109">You can assign a value to the variable while creating it or assign or change the value after it is created.</span></span>

<span data-ttu-id="ada2e-110">**새 변수** 매개 변수를 사용 하 여 변수의 속성을 설정 하 고, 변수의 범위를 설정 하 고, 변수가 공용 변수 인지 아니면 개인 변수 인지를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-110">You can use the parameters of **New-Variable** to set the properties of the variable, set the scope of a variable, and determine whether variables are public or private.</span></span>

<span data-ttu-id="ada2e-111">일반적으로 변수 이름과 해당 값 (예:)을 입력 하 여 새 변수를 `$Var = 3` 만들지만, **새** 변수 cmdlet을 사용 하 여 해당 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-111">Typically, you create a new variable by typing the variable name and its value, such as `$Var = 3`, but you can use the **New-Variable** cmdlet to use its parameters.</span></span>

## <span data-ttu-id="ada2e-112">예제</span><span class="sxs-lookup"><span data-stu-id="ada2e-112">EXAMPLES</span></span>

### <span data-ttu-id="ada2e-113">예제 1: 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="ada2e-113">Example 1: Create a variable</span></span>

```
PS C:\> New-Variable days
```

<span data-ttu-id="ada2e-114">이 명령은 days 라는 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-114">This command creates a new variable named days.</span></span>
<span data-ttu-id="ada2e-115">*Name* 매개 변수를 입력할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-115">You are not required to type the *Name* parameter.</span></span>

### <span data-ttu-id="ada2e-116">예 2: 변수를 만들고 값을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-116">Example 2: Create a variable and assign it a value</span></span>

```
PS C:\> New-Variable -Name "zipcode" -Value 98033
```

<span data-ttu-id="ada2e-117">이 명령은 zipcode 라는 변수를 만들고 값 98033을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-117">This command creates a variable named zipcode and assigns it the value 98033.</span></span>

### <span data-ttu-id="ada2e-118">예제 3: ReadOnly 옵션을 사용 하 여 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="ada2e-118">Example 3: Create a variable with the ReadOnly option</span></span>

```
PS C:\> New-Variable -Name Max -Value 256 -Option ReadOnly
PS C:\> New-Variable -Name max -Value 1024

New-Variable : A variable with name 'max' already exists.
At line:1 char:1
+ New-Variable -Name max -Value 1024
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ResourceExists: (max:String) [New-Variable], SessionStateException
    + FullyQualifiedErrorId : VariableAlreadyExists,Microsoft.PowerShell.Commands.NewVariableCommand

PS C:\> New-Variable -Name max -Value 1024 -Force
```

<span data-ttu-id="ada2e-119">이 예에서는 **New 변수의** ReadOnly 옵션을 사용 하 여 변수를 덮어쓰지 않도록 보호 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-119">This example shows how to use the ReadOnly option of **New-Variable** to protect a variable from being overwritten.</span></span>

<span data-ttu-id="ada2e-120">첫 번째 명령은 Max 라는 새 변수를 만들고 해당 값을 256로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-120">The first command creates a new variable named Max and sets its value to 256.</span></span>
<span data-ttu-id="ada2e-121">*Option* 매개 변수를 ReadOnly 값과 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-121">It uses the *Option* parameter with a value of ReadOnly.</span></span>

<span data-ttu-id="ada2e-122">두 번째 명령은 이름이 같은 두 번째 변수를 만들려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-122">The second command tries to create a second variable with the same name.</span></span>
<span data-ttu-id="ada2e-123">그러나 변수에 대해 읽기 전용 옵션이 설정되어 있으므로 이 명령을 실행하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-123">This command returns an error, because the read-only option is set on the variable.</span></span>

<span data-ttu-id="ada2e-124">세 번째 명령은 *Force* 매개 변수를 사용 하 여 변수에 대 한 읽기 전용 보호를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-124">The third command uses the *Force* parameter to override the read-only protection on the variable.</span></span>
<span data-ttu-id="ada2e-125">이 경우에는 이름이 같은 새 변수를 만드는 명령이 제대로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-125">In this case, the command to create a new variable with the same name succeeds.</span></span>

### <span data-ttu-id="ada2e-126">예제 4: 전용 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="ada2e-126">Example 4: Create a private variable</span></span>

```
PS C:\> New-Variable -Name counter -Visibility Private

#Effect of private variable in a module.

PS C:\> Get-Variable c*

Name                           Value
----                           -----
Culture                        en-US
ConsoleFileName
ConfirmPreference              High
CommandLineParameters          {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"
At line:1 char:1
+ $counter
+ ~~~~~~~~
    + CategoryInfo          : PermissionDenied: (counter:String) [], SessionStateException
    + FullyQualifiedErrorId : VariableIsPrivate

PS C:\> Get-Counter
Name         Value
----         -----
Counter1     3.1415
...
```

<span data-ttu-id="ada2e-127">이 명령은 모듈의 개인 변수 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-127">This command demonstrates the behavior of a private variable in a module.</span></span>
<span data-ttu-id="ada2e-128">이 모듈에는 Counter 라는 전용 변수가 있는 Get-Counter cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-128">The module contains the Get-Counter cmdlet, which has a private variable named Counter.</span></span>
<span data-ttu-id="ada2e-129">이 명령은 값이 Private 인 *Visibility* 매개 변수를 사용 하 여 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-129">The command uses the *Visibility* parameter with a value of Private to create the variable.</span></span>

<span data-ttu-id="ada2e-130">샘플 출력은 개인 변수의 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-130">The sample output shows the behavior of a private variable.</span></span>
<span data-ttu-id="ada2e-131">모듈을 로드한 사용자는 Counter 변수 값을 보거나 변경할 수 없지만, 모듈의 명령을 통해 Counter 변수를 읽고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-131">The user who has loaded the module cannot view or change the value of the Counter variable, but the Counter variable can be read and changed by the commands in the module.</span></span>

### <span data-ttu-id="ada2e-132">예 5: 공백으로 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="ada2e-132">Example 5: Create a variable with a space</span></span>

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

<span data-ttu-id="ada2e-133">이 명령은 공백이 있는 변수를 만들 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-133">This command demonstrates that variables with spaces can be created.</span></span>
<span data-ttu-id="ada2e-134">변수는 **Get 변수** cmdlet을 사용 하 여 액세스 하거나 중괄호를 사용 하 여 변수를 구분 하 여 직접 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-134">The variables can be accessed using the **Get-Variable** cmdlet or directly by delimiting a variable with braces.</span></span>

## <span data-ttu-id="ada2e-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ada2e-135">PARAMETERS</span></span>

### <span data-ttu-id="ada2e-136">-Description</span><span class="sxs-lookup"><span data-stu-id="ada2e-136">-Description</span></span>
<span data-ttu-id="ada2e-137">변수의 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-137">Specifies a description of the variable.</span></span>

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

### <span data-ttu-id="ada2e-138">-Force</span><span class="sxs-lookup"><span data-stu-id="ada2e-138">-Force</span></span>
<span data-ttu-id="ada2e-139">Cmdlet이 기존 읽기 전용 변수와 이름이 같은 변수를 생성 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-139">Indicates that the cmdlet creates a variable with the same name as an existing read-only variable.</span></span>

<span data-ttu-id="ada2e-140">기본적으로 ReadOnly 또는 Constant 옵션 값이 없는 변수는 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-140">By default, you can overwrite a variable unless the variable has an option value of ReadOnly or Constant.</span></span>
<span data-ttu-id="ada2e-141">자세한 내용은 *Option* 매개 변수를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ada2e-141">For more information, see the *Option* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ada2e-142">-Name</span><span class="sxs-lookup"><span data-stu-id="ada2e-142">-Name</span></span>
<span data-ttu-id="ada2e-143">새 변수의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-143">Specifies a name for the new variable.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ada2e-144">-옵션</span><span class="sxs-lookup"><span data-stu-id="ada2e-144">-Option</span></span>
<span data-ttu-id="ada2e-145">변수의 **Options** 속성 값을 지정 합니다. 이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-145">Specifies the value of the **Options** property of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ada2e-146">없음</span><span class="sxs-lookup"><span data-stu-id="ada2e-146">None.</span></span>
<span data-ttu-id="ada2e-147">옵션을 설정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-147">Sets no options.</span></span>
<span data-ttu-id="ada2e-148">기본값은 없음입니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-148">(None is the default.)</span></span>
- <span data-ttu-id="ada2e-149">ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="ada2e-149">ReadOnly.</span></span>
<span data-ttu-id="ada2e-150">삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-150">Can be deleted.</span></span>
<span data-ttu-id="ada2e-151">*Force* 매개 변수를 사용 하는 경우를 제외 하 고는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-151">Cannot be changed, except by using the *Force* parameter.</span></span>
- <span data-ttu-id="ada2e-152">비공개.</span><span class="sxs-lookup"><span data-stu-id="ada2e-152">Private.</span></span>
<span data-ttu-id="ada2e-153">변수는 현재 범위에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-153">The variable is available only in the current scope.</span></span>
- <span data-ttu-id="ada2e-154">AllScope.</span><span class="sxs-lookup"><span data-stu-id="ada2e-154">AllScope.</span></span>
<span data-ttu-id="ada2e-155">변수는 새로 만든 범위로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-155">The variable is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="ada2e-156">상수입니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-156">Constant.</span></span>
<span data-ttu-id="ada2e-157">삭제하거나 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-157">Cannot be deleted or changed.</span></span>
<span data-ttu-id="ada2e-158">상수는 변수를 만드는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-158">Constant is valid only when you are creating a variable.</span></span>
<span data-ttu-id="ada2e-159">기존 변수의 옵션을 Constant로 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-159">You cannot change the options of an existing variable to Constant.</span></span>

<span data-ttu-id="ada2e-160">세션에 있는 모든 변수의 **Options** 속성을 보려면를 입력 `Get-Variable | Format-Table -Property name, options -autosize` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-160">To see the **Options** property of all variables in the session, type `Get-Variable | Format-Table -Property name, options -autosize`.</span></span>

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

### <span data-ttu-id="ada2e-161">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ada2e-161">-PassThru</span></span>
<span data-ttu-id="ada2e-162">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-162">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="ada2e-163">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-163">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ada2e-164">-범위</span><span class="sxs-lookup"><span data-stu-id="ada2e-164">-Scope</span></span>
<span data-ttu-id="ada2e-165">새 변수의 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-165">Specifies the scope of the new variable.</span></span>
<span data-ttu-id="ada2e-166">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-166">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ada2e-167">전역적.</span><span class="sxs-lookup"><span data-stu-id="ada2e-167">Global.</span></span>
<span data-ttu-id="ada2e-168">전역 범위에서 만든 변수는 PowerShell 프로세스의 모든 위치에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-168">Variables created in the global scope are accessible everywhere in a PowerShell process.</span></span>
- <span data-ttu-id="ada2e-169">로컬.</span><span class="sxs-lookup"><span data-stu-id="ada2e-169">Local.</span></span>
<span data-ttu-id="ada2e-170">로컬 범위는 현재 범위를 참조 하며, 컨텍스트에 따라 모든 범위가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-170">The local scope refers to the current scope, this can be any scope depending on the context.</span></span>
- <span data-ttu-id="ada2e-171">스크립트.</span><span class="sxs-lookup"><span data-stu-id="ada2e-171">Script.</span></span>
<span data-ttu-id="ada2e-172">스크립트 범위에서 만든 변수는 스크립트 파일이 나 생성 된 모듈 내 에서만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-172">Variables created in the script scope are accessible only within the script file or module they are created in.</span></span>
- <span data-ttu-id="ada2e-173">비공개.</span><span class="sxs-lookup"><span data-stu-id="ada2e-173">Private.</span></span>
<span data-ttu-id="ada2e-174">전용 범위에서 만든 변수는에 존재 하는 범위 밖에 서 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-174">Variables created in the private scope cannot be accessed outside the scope they exist in.</span></span>
<span data-ttu-id="ada2e-175">전용 범위를 사용 하 여 다른 범위에 있는 동일한 이름의 개인 버전을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-175">You can use private scope to create a private version of an item with the same name in another scope.</span></span>
- <span data-ttu-id="ada2e-176">현재 범위 (0부터 범위 수까지, 여기서 0은 현재 범위, 1은 부모, 2는 부모 범위의 부모)에 상대적인 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-176">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope, 1 is its parent, 2 the parent of the parent scope, and so on).</span></span>
<span data-ttu-id="ada2e-177">음수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-177">Negative numbers cannot be used.</span></span>

<span data-ttu-id="ada2e-178">범위 매개 변수가 지정 되지 않은 경우 Local은 기본 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-178">Local is the default scope when the scope parameter is not specified.</span></span>

<span data-ttu-id="ada2e-179">자세한 내용은 about_Scopes를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ada2e-179">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="ada2e-180">-Value</span><span class="sxs-lookup"><span data-stu-id="ada2e-180">-Value</span></span>
<span data-ttu-id="ada2e-181">변수의 초기 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-181">Specifies the initial value of the variable.</span></span>

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

### <span data-ttu-id="ada2e-182">-표시 유형</span><span class="sxs-lookup"><span data-stu-id="ada2e-182">-Visibility</span></span>
<span data-ttu-id="ada2e-183">변수를 만든 세션 외부에서도 변수가 표시되는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-183">Determines whether the variable is visible outside of the session in which it was created.</span></span>
<span data-ttu-id="ada2e-184">이 매개 변수는 다른 사용자에게 전달할 스크립트 및 명령에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-184">This parameter is designed for  use in scripts and commands that will be delivered to other users.</span></span>
<span data-ttu-id="ada2e-185">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-185">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ada2e-186">공개.</span><span class="sxs-lookup"><span data-stu-id="ada2e-186">Public.</span></span>
<span data-ttu-id="ada2e-187">변수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-187">The variable is visible.</span></span>
<span data-ttu-id="ada2e-188">기본값은 Public입니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-188">(Public is the default.)</span></span>
- <span data-ttu-id="ada2e-189">비공개.</span><span class="sxs-lookup"><span data-stu-id="ada2e-189">Private.</span></span>
<span data-ttu-id="ada2e-190">변수가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-190">The variable is not visible.</span></span>

<span data-ttu-id="ada2e-191">개인 변수는 Get-Variable에서 반환하는 목록과 같은 변수 목록이나 Variable: 드라이브의 표시에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-191">When a variable is private, it does not appear in lists of variables, such as those returned by Get-Variable, or in displays of the Variable: drive.</span></span>
<span data-ttu-id="ada2e-192">개인 변수의 값을 읽거나 변경하는 명령을 실행하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-192">Commands to read or change the value of a private variable return an error.</span></span>
<span data-ttu-id="ada2e-193">그러나 변수를 정의한 세션에서 명령을 작성한 경우에는 개인 변수를 사용하는 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-193">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ada2e-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ada2e-194">-Confirm</span></span>
<span data-ttu-id="ada2e-195">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-195">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ada2e-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ada2e-196">-WhatIf</span></span>
<span data-ttu-id="ada2e-197">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-197">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ada2e-198">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-198">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ada2e-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ada2e-199">CommonParameters</span></span>
<span data-ttu-id="ada2e-200">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ada2e-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ada2e-201">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ada2e-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ada2e-202">입력</span><span class="sxs-lookup"><span data-stu-id="ada2e-202">INPUTS</span></span>

### <span data-ttu-id="ada2e-203">System.Object</span><span class="sxs-lookup"><span data-stu-id="ada2e-203">System.Object</span></span>
<span data-ttu-id="ada2e-204">**새 변수에** 값을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-204">You can pipe a value to **New-Variable**.</span></span>

## <span data-ttu-id="ada2e-205">출력</span><span class="sxs-lookup"><span data-stu-id="ada2e-205">OUTPUTS</span></span>

### <span data-ttu-id="ada2e-206">None 또는 System.object입니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-206">None or System.Management.Automation.PSVariable</span></span>
<span data-ttu-id="ada2e-207">*PassThru* 매개 변수를 사용 하는 경우 **새** 변수는 새 변수를 나타내는 **system.object** 를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-207">When you use the *PassThru* parameter, **New-Variable** generates a **System.Management.Automation.PSVariable** object representing the new variable.</span></span>
<span data-ttu-id="ada2e-208">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ada2e-208">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ada2e-209">참고</span><span class="sxs-lookup"><span data-stu-id="ada2e-209">NOTES</span></span>

## <span data-ttu-id="ada2e-210">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ada2e-210">RELATED LINKS</span></span>

[<span data-ttu-id="ada2e-211">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="ada2e-211">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="ada2e-212">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="ada2e-212">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="ada2e-213">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="ada2e-213">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="ada2e-214">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="ada2e-214">Set-Variable</span></span>](Set-Variable.md)

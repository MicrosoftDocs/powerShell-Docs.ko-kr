---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 2/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Alias
ms.openlocfilehash: 2a84c08022689d53c3273f1b6f802cfeae67953d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211825"
---
# <span data-ttu-id="b9809-103">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="b9809-103">Set-Alias</span></span>

## <span data-ttu-id="b9809-104">개요</span><span class="sxs-lookup"><span data-stu-id="b9809-104">SYNOPSIS</span></span>
<span data-ttu-id="b9809-105">현재 PowerShell 세션의 cmdlet 또는 다른 명령에 대 한 별칭을 만들거나 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-105">Creates or changes an alias for a cmdlet or other command in the current PowerShell session.</span></span>

## <span data-ttu-id="b9809-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b9809-106">SYNTAX</span></span>

### <span data-ttu-id="b9809-107">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="b9809-107">Default (Default)</span></span>

```
Set-Alias [-Name] <string> [-Value] <string> [-Description <string>] [-Option <ScopedItemOptions>]
 [-PassThru] [-Scope <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b9809-108">설명</span><span class="sxs-lookup"><span data-stu-id="b9809-108">DESCRIPTION</span></span>

<span data-ttu-id="b9809-109">`Set-Alias`Cmdlet은 cmdlet 또는 명령 (예: 함수, 스크립트, 파일 또는 기타 실행 파일)에 대 한 별칭을 만들거나 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-109">The `Set-Alias` cmdlet creates or changes an alias for a cmdlet or a command, such as a function, script, file, or other executable.</span></span> <span data-ttu-id="b9809-110">별칭은 cmdlet 또는 명령을 참조 하는 대체 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-110">An alias is an alternate name that refers to a cmdlet or command.</span></span>
<span data-ttu-id="b9809-111">예를 들어 `sal` 는 cmdlet에 대 한 별칭입니다 `Set-Alias` .</span><span class="sxs-lookup"><span data-stu-id="b9809-111">For example, `sal` is the alias for the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="b9809-112">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b9809-112">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="b9809-113">Cmdlet은 여러 별칭을 포함할 수 있지만 별칭은 하나의 cmdlet에만 연결 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-113">A cmdlet can have multiple aliases, but an alias can only be associated with one cmdlet.</span></span> <span data-ttu-id="b9809-114">`Set-Alias`를 사용 하 여 기존 별칭을 다른 cmdlet에 재할당 하거나 설명 등의 별칭 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-114">You can use `Set-Alias` to reassign an existing alias to another cmdlet, or change an alias's properties, such as the description.</span></span>

<span data-ttu-id="b9809-115">에 의해 만들어지거나 변경 된 별칭 `Set-Alias` 은 영구적이 지 않으며 현재 PowerShell 세션 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-115">An alias that is created or changed by `Set-Alias` is not permanent and is only available during the current PowerShell session.</span></span> <span data-ttu-id="b9809-116">PowerShell 세션이 닫히면 별칭이 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-116">When the PowerShell session is closed, the alias is removed.</span></span>

## <span data-ttu-id="b9809-117">예제</span><span class="sxs-lookup"><span data-stu-id="b9809-117">EXAMPLES</span></span>

### <span data-ttu-id="b9809-118">예제 1: cmdlet에 대 한 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="b9809-118">Example 1: Create an alias for a cmdlet</span></span>

<span data-ttu-id="b9809-119">이 명령은 현재 PowerShell 세션에서 cmdlet에 대 한 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-119">This command creates an alias to a cmdlet in the current PowerShell session.</span></span>

```
PS> Set-Alias -Name list -Value Get-ChildItem

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem
```

<span data-ttu-id="b9809-120">`Set-Alias`Cmdlet은 현재 PowerShell 세션에서 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-120">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="b9809-121">**Name** 매개 변수는 별칭의 이름을 지정 합니다 `list` .</span><span class="sxs-lookup"><span data-stu-id="b9809-121">The **Name** parameter specifies the alias's name, `list`.</span></span> <span data-ttu-id="b9809-122">**Value** 매개 변수는 별칭이 실행 되는 cmdlet을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-122">The **Value** parameter specifies the cmdlet that the alias runs.</span></span>

<span data-ttu-id="b9809-123">별칭을 실행 하려면 `list` PowerShell 명령줄에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-123">To run the alias, type `list` on the PowerShell command line.</span></span>

### <span data-ttu-id="b9809-124">예 2: 다른 cmdlet에 기존 별칭 재할당</span><span class="sxs-lookup"><span data-stu-id="b9809-124">Example 2: Reassign an existing alias to a different cmdlet</span></span>

<span data-ttu-id="b9809-125">이 명령은 기존 별칭을 다시 할당 하 여 다른 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-125">This command reassigns an existing alias to run a different cmdlet.</span></span>

```
PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem

PS> Set-Alias -Name list -Value Get-Location

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-Location
```

<span data-ttu-id="b9809-126">`Get-Alias`Cmdlet은 **Name** 매개 변수를 사용 하 여 별칭을 표시 합니다 `list` .</span><span class="sxs-lookup"><span data-stu-id="b9809-126">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="b9809-127">`list`별칭은 cmdlet과 연결 됩니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="b9809-127">The `list` alias is associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="b9809-128">`list`별칭을 실행 하면 현재 디렉터리의 항목이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-128">When the `list` alias is run, the items in the current directory are displayed.</span></span>

<span data-ttu-id="b9809-129">`Set-Alias`Cmdlet은 **Name** 매개 변수를 사용 하 여 별칭을 지정 합니다 `list` .</span><span class="sxs-lookup"><span data-stu-id="b9809-129">The `Set-Alias` cmdlet uses the **Name** parameter to specify the `list` alias.</span></span> <span data-ttu-id="b9809-130">**값** 매개 변수는 별칭을 cmdlet에 연결 합니다 `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="b9809-130">The **Value** parameter associates the alias to the `Get-Location` cmdlet.</span></span>

<span data-ttu-id="b9809-131">`Get-Alias`Cmdlet은 **Name** 매개 변수를 사용 하 여 별칭을 표시 합니다 `list` .</span><span class="sxs-lookup"><span data-stu-id="b9809-131">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="b9809-132">`list`별칭은 cmdlet과 연결 됩니다 `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="b9809-132">The `list` alias is associated with the `Get-Location` cmdlet.</span></span> <span data-ttu-id="b9809-133">`list`별칭을 실행 하면 현재 디렉터리의 위치가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-133">When the `list` alias is run, the current directory's location is displayed.</span></span>

### <span data-ttu-id="b9809-134">예제 3: 읽기 전용 별칭 만들기 및 변경</span><span class="sxs-lookup"><span data-stu-id="b9809-134">Example 3: Create and change a read-only alias</span></span>

<span data-ttu-id="b9809-135">이 명령은 읽기 전용 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-135">This command creates a read-only alias.</span></span> <span data-ttu-id="b9809-136">읽기 전용 옵션을 선택 하면 별칭에 대 한 의도 하지 않은 변경을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-136">The read-only option prevents unintended changes to an alias.</span></span> <span data-ttu-id="b9809-137">읽기 전용 별칭을 변경 하거나 삭제 하려면 **Force** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-137">To change or delete a read-only alias, use the **Force** parameter.</span></span>

```
PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         :
Name                : loc
CommandType         : Alias

PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -Description 'Displays the current directory' -Force -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         : Displays the current directory
Name                : loc
CommandType         : Alias
```

<span data-ttu-id="b9809-138">`Set-Alias`Cmdlet은 현재 PowerShell 세션에서 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-138">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="b9809-139">**Name** 매개 변수는 별칭의 이름을 지정 합니다 `loc` .</span><span class="sxs-lookup"><span data-stu-id="b9809-139">The **Name** parameter specifies the alias's name, `loc`.</span></span> <span data-ttu-id="b9809-140">**Value** 매개 변수는 `Get-Location` 별칭이 실행 되는 cmdlet을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-140">The **Value** parameter specifies the `Get-Location` cmdlet that the alias runs.</span></span> <span data-ttu-id="b9809-141">**Option** 매개 변수는 **ReadOnly** 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-141">The **Option** parameter specifies the **ReadOnly** value.</span></span> <span data-ttu-id="b9809-142">**PassThru** 매개 변수는 별칭 개체를 나타내며 파이프라인에서 개체를 cmdlet으로 보냅니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="b9809-142">The **PassThru** parameter represents the alias object and sends the object down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="b9809-143">`Format-List`**속성** 매개 변수를 별표 ()와 함께 사용 하 여 `*` 모든 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-143">`Format-List` uses the **Property** parameter with an asterisk (`*`) so that all of the properties are displayed.</span></span> <span data-ttu-id="b9809-144">예제 출력에서는 이러한 속성의 일부 목록을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-144">The example output shows a partial list of those properties.</span></span>

<span data-ttu-id="b9809-145">`loc`두 매개 변수를 추가 하 여 별칭을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-145">The `loc` alias is changed with the addition of two parameters.</span></span> <span data-ttu-id="b9809-146">**설명** 별칭의 용도를 설명 하는 텍스트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-146">**Description** adds text to explain the alias's purpose.</span></span> <span data-ttu-id="b9809-147">별칭은 읽기 전용 이므로 **Force** 매개 변수가 필요 합니다 `loc` .</span><span class="sxs-lookup"><span data-stu-id="b9809-147">The **Force** parameter is needed because the `loc` alias is read-only.</span></span> <span data-ttu-id="b9809-148">**Force** 매개 변수를 사용 하지 않으면 변경이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-148">If the **Force** parameter is not used, the change fails.</span></span>

### <span data-ttu-id="b9809-149">예제 4: 실행 파일에 대 한 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="b9809-149">Example 4: Create an alias to an executable file</span></span>

<span data-ttu-id="b9809-150">이 예제에서는 로컬 컴퓨터의 실행 파일에 대 한 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-150">This example creates an alias to an executable file on the local computer.</span></span>

```
PS> Set-Alias -Name np -Value C:\Windows\notepad.exe

PS> Get-Alias -Name np

CommandType     Name
-----------     ----
Alias           np -> notepad.exe
```

<span data-ttu-id="b9809-151">`Set-Alias`Cmdlet은 현재 PowerShell 세션에서 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-151">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="b9809-152">**Name** 매개 변수는 별칭의 이름을 지정 합니다 `np` .</span><span class="sxs-lookup"><span data-stu-id="b9809-152">The **Name** parameter specifies the alias's name, `np`.</span></span> <span data-ttu-id="b9809-153">**값** 매개 변수는 **C:\Windows\notepad.exe** 경로 및 응용 프로그램 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-153">The **Value** parameter specifies the path and application name **C:\Windows\notepad.exe** .</span></span> <span data-ttu-id="b9809-154">`Get-Alias`이 cmdlet은 **Name** 매개 변수를 사용 하 여 `np` 별칭이 **notepad.exe** 와 연결 되어 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-154">The `Get-Alias` cmdlet uses the **Name** parameter to show that the `np` alias is associated with **notepad.exe** .</span></span>

<span data-ttu-id="b9809-155">별칭을 실행 하려면 `np` PowerShell 명령줄에를 입력 하 여 **notepad.exe** 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-155">To run the alias, type `np` on the PowerShell command line to open **notepad.exe** .</span></span>

### <span data-ttu-id="b9809-156">예 5: 매개 변수를 사용 하 여 명령에 대 한 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="b9809-156">Example 5: Create an alias for a command with parameters</span></span>

<span data-ttu-id="b9809-157">이 예제에서는 매개 변수를 사용 하 여 명령에 별칭을 할당 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-157">This example shows how to assign an alias to a command with parameters.</span></span>

<span data-ttu-id="b9809-158">Cmdlet에 대 한 별칭을 만들 수 있습니다 (예:) `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="b9809-158">You can create an alias for a cmdlet, such as `Set-Location`.</span></span> <span data-ttu-id="b9809-159">매개 변수 및 값 (예:)을 사용 하 여 명령에 대 한 별칭을 만들 수 없습니다 `Set-Location -Path C:\Windows\System32` .</span><span class="sxs-lookup"><span data-stu-id="b9809-159">You cannot create an alias for a command with parameters and values, such as `Set-Location -Path C:\Windows\System32`.</span></span> <span data-ttu-id="b9809-160">명령의 별칭을 만들려면 명령이 포함된 함수를 만든 다음 함수의 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-160">To create an alias for a command, create a function that includes the command, and then create an alias to the function.</span></span> <span data-ttu-id="b9809-161">자세한 내용은 [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b9809-161">For more information, see [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md).</span></span>

```
PS> Function CD32 {Set-Location -Path C:\Windows\System32}

PS> Set-Alias -Name Go -Value CD32
```

<span data-ttu-id="b9809-162">이라는 함수를 `CD32` 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-162">A function named `CD32` is created.</span></span> <span data-ttu-id="b9809-163">함수는 `Set-Location` **Path** 매개 변수와 함께 cmdlet을 사용 하 여 디렉터리를 지정 합니다 ( **c:\system32** ).</span><span class="sxs-lookup"><span data-stu-id="b9809-163">The function uses the `Set-Location` cmdlet with the **Path** parameter to specify the directory, **C:\Windows\System32** .</span></span>

<span data-ttu-id="b9809-164">`Set-Alias`Cmdlet은 현재 PowerShell 세션에서 함수에 대 한 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-164">The `Set-Alias` cmdlet creates an alias to the function in the current PowerShell session.</span></span> <span data-ttu-id="b9809-165">**Name** 매개 변수는 별칭의 이름을 지정 합니다 `Go` .</span><span class="sxs-lookup"><span data-stu-id="b9809-165">The **Name** parameter specifies the alias's name, `Go`.</span></span> <span data-ttu-id="b9809-166">**값** 매개 변수는 함수의 이름를 지정 합니다 `CD32` .</span><span class="sxs-lookup"><span data-stu-id="b9809-166">The **Value** parameter specifies the function's name, `CD32`.</span></span>

<span data-ttu-id="b9809-167">별칭을 실행 하려면 `Go` PowerShell 명령줄에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-167">To run the alias, type `Go` on the PowerShell command line.</span></span> <span data-ttu-id="b9809-168">함수는를 `CD32` 실행 하 고 디렉터리를 **C:\Windows\System32** 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-168">The `CD32` function runs and changes to the directory **C:\Windows\System32** .</span></span>

## <span data-ttu-id="b9809-169">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b9809-169">PARAMETERS</span></span>

### <span data-ttu-id="b9809-170">-Description</span><span class="sxs-lookup"><span data-stu-id="b9809-170">-Description</span></span>

<span data-ttu-id="b9809-171">별칭에 대한 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-171">Specifies a description of the alias.</span></span> <span data-ttu-id="b9809-172">아무 문자열이나 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-172">You can type any string.</span></span> <span data-ttu-id="b9809-173">설명에 공백이 포함 되어 있으면 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-173">If the description includes spaces, enclose it single quotation marks.</span></span>

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

### <span data-ttu-id="b9809-174">-Force</span><span class="sxs-lookup"><span data-stu-id="b9809-174">-Force</span></span>

<span data-ttu-id="b9809-175">**Force** 매개 변수를 사용 하 여 **Option** 매개 변수가 **ReadOnly** 로 설정 된 별칭을 변경 하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-175">Use the **Force** parameter to change or delete an alias that has the **Option** parameter set to **ReadOnly** .</span></span>

<span data-ttu-id="b9809-176">**Force** 매개 변수는 **상수** 로 설정 된 **Option** 매개 변수를 사용 하 여 별칭을 변경 하거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-176">The **Force** parameter cannot change or delete an alias with the **Option** parameter set to **Constant** .</span></span>

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

### <span data-ttu-id="b9809-177">-Name</span><span class="sxs-lookup"><span data-stu-id="b9809-177">-Name</span></span>

<span data-ttu-id="b9809-178">새 별칭의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-178">Specifies the name of a new alias.</span></span> <span data-ttu-id="b9809-179">별칭 이름에는 영숫자 문자와 하이픈이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-179">An alias name can contain alphanumeric characters and hyphens.</span></span> <span data-ttu-id="b9809-180">별칭 이름은 숫자 (예: 123) 일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-180">Alias names cannot be numeric, such as 123.</span></span>

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

### <span data-ttu-id="b9809-181">-옵션</span><span class="sxs-lookup"><span data-stu-id="b9809-181">-Option</span></span>

<span data-ttu-id="b9809-182">별칭의 **Option** 속성 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-182">Sets the **Option** property value of the alias.</span></span> <span data-ttu-id="b9809-183">**ReadOnly** 및 **Constant** 와 같은 값은 의도 하지 않은 변경 으로부터 별칭을 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-183">Values such as **ReadOnly** and **Constant** protect an alias from unintended changes.</span></span> <span data-ttu-id="b9809-184">세션에 있는 모든 별칭의 **Option** 속성을 보려면를 입력 `Get-Alias | Format-Table -Property Name, Options -Autosize` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-184">To see the **Option** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -Autosize`.</span></span>

<span data-ttu-id="b9809-185">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-185">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b9809-186">**AllScope** 별칭은 새로 생성 된 범위에 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-186">**AllScope** The alias is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="b9809-187">**상수** 을 변경 하거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-187">**Constant** Cannot be changed or deleted.</span></span>
- <span data-ttu-id="b9809-188">**없음** 는 옵션을 설정 하지 않으며 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-188">**None** Sets no options and is the default.</span></span>
- <span data-ttu-id="b9809-189">**개인** 별칭은 현재 범위 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-189">**Private** The alias is available only in the current scope.</span></span>
- <span data-ttu-id="b9809-190">**읽기 전용** **Force** 매개 변수를 사용 하지 않으면를 변경 하거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-190">**ReadOnly** Cannot be changed or deleted unless the **Force** parameter is used.</span></span>
- <span data-ttu-id="b9809-191">**Unspecified**</span><span class="sxs-lookup"><span data-stu-id="b9809-191">**Unspecified**</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: AllScope, Constant, None, Private, ReadOnly, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9809-192">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b9809-192">-PassThru</span></span>

<span data-ttu-id="b9809-193">별칭을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-193">Returns an object that represents the alias.</span></span> <span data-ttu-id="b9809-194">와 같은 형식 cmdlet을 사용 `Format-List` 하 여 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-194">Use a format cmdlet such as `Format-List` to display the object.</span></span> <span data-ttu-id="b9809-195">기본적으로는 `Set-Alias` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-195">By default, `Set-Alias` does not generate any output.</span></span>

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

### <span data-ttu-id="b9809-196">-범위</span><span class="sxs-lookup"><span data-stu-id="b9809-196">-Scope</span></span>

<span data-ttu-id="b9809-197">이 별칭이 유효한 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-197">Specifies the scope in which this alias is valid.</span></span> <span data-ttu-id="b9809-198">기본값은 **Local** 입니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-198">The default value is **Local** .</span></span> <span data-ttu-id="b9809-199">자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b9809-199">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

<span data-ttu-id="b9809-200">허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-200">The acceptable values are as follows:</span></span>

- <span data-ttu-id="b9809-201">전역</span><span class="sxs-lookup"><span data-stu-id="b9809-201">Global</span></span>
- <span data-ttu-id="b9809-202">로컬</span><span class="sxs-lookup"><span data-stu-id="b9809-202">Local</span></span>
- <span data-ttu-id="b9809-203">Private</span><span class="sxs-lookup"><span data-stu-id="b9809-203">Private</span></span>
- <span data-ttu-id="b9809-204">번호가 매겨진 범위</span><span class="sxs-lookup"><span data-stu-id="b9809-204">Numbered scopes</span></span>
- <span data-ttu-id="b9809-205">스크립트</span><span class="sxs-lookup"><span data-stu-id="b9809-205">Script</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Global, Local, Private, Numbered scopes, Script

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9809-206">-Value</span><span class="sxs-lookup"><span data-stu-id="b9809-206">-Value</span></span>

<span data-ttu-id="b9809-207">별칭이 실행 되는 cmdlet 또는 명령의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-207">Specifies the name of the cmdlet or command that the alias runs.</span></span> <span data-ttu-id="b9809-208">**값** 매개 변수는 별칭의 **정의** 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-208">The **Value** parameter is the alias's **Definition** property.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b9809-209">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b9809-209">-Confirm</span></span>

<span data-ttu-id="b9809-210">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-210">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b9809-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b9809-211">-WhatIf</span></span>

<span data-ttu-id="b9809-212">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-212">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b9809-213">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-213">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b9809-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b9809-214">CommonParameters</span></span>

<span data-ttu-id="b9809-215">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b9809-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b9809-216">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9809-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b9809-217">입력</span><span class="sxs-lookup"><span data-stu-id="b9809-217">INPUTS</span></span>

### <span data-ttu-id="b9809-218">없음</span><span class="sxs-lookup"><span data-stu-id="b9809-218">None</span></span>

<span data-ttu-id="b9809-219">`Set-Alias` 파이프라인의 입력을 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-219">`Set-Alias` does not accept input from the pipeline.</span></span>

## <span data-ttu-id="b9809-220">출력</span><span class="sxs-lookup"><span data-stu-id="b9809-220">OUTPUTS</span></span>

### <span data-ttu-id="b9809-221">없음 또는 System.management.automation.aliasinfo</span><span class="sxs-lookup"><span data-stu-id="b9809-221">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="b9809-222">**PassThru** 매개 변수를 사용 하는 경우는 `Set-Alias` 별칭을 나타내는 **system.management.automation.aliasinfo** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-222">When you use the **PassThru** parameter, `Set-Alias` generates a **System.Management.Automation.AliasInfo** object representing the alias.</span></span> <span data-ttu-id="b9809-223">그렇지 않으면에서 `Set-Alias` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-223">Otherwise, `Set-Alias` does not generate any output.</span></span>

## <span data-ttu-id="b9809-224">참고</span><span class="sxs-lookup"><span data-stu-id="b9809-224">NOTES</span></span>

<span data-ttu-id="b9809-225">PowerShell은 각 PowerShell 세션에서 사용할 수 있는 기본 제공 별칭을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-225">PowerShell includes built-in aliases that are available in each PowerShell session.</span></span> <span data-ttu-id="b9809-226">`Get-Alias`Cmdlet은 PowerShell 세션에서 사용할 수 있는 별칭을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-226">The `Get-Alias` cmdlet displays the aliases available in a PowerShell session.</span></span>

<span data-ttu-id="b9809-227">별칭을 만들려면 cmdlet 또는를 사용 `Set-Alias` `New-Alias` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-227">To create an alias, use the cmdlets `Set-Alias` or `New-Alias`.</span></span> <span data-ttu-id="b9809-228">PowerShell 6에서 별칭을 삭제 하려면 cmdlet을 사용 `Remove-Alias` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-228">In PowerShell 6, to delete an alias, use the `Remove-Alias` cmdlet.</span></span> <span data-ttu-id="b9809-229">`Remove-Item` 이전 버전의 PowerShell을 사용 하 여 만든 스크립트와 같은 이전 버전과의 호환성을 위해이 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-229">`Remove-Item` is accepted for backwards compatibility such as for scripts created with prior versions of PowerShell.</span></span> <span data-ttu-id="b9809-230">와 같은 명령을 사용 `Remove-Item -Path Alias:aliasname` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-230">Use a command such as `Remove-Item -Path Alias:aliasname`.</span></span>

<span data-ttu-id="b9809-231">각 PowerShell 세션에서 사용할 수 있는 별칭을 만들려면 PowerShell 프로필에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-231">To create an alias that is available in each PowerShell session, add it to your PowerShell profile.</span></span>
<span data-ttu-id="b9809-232">자세한 내용은 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b9809-232">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="b9809-233">내보내기 및 가져오기를 수행 하 여 다른 PowerShell 세션에서 별칭을 저장 하 고 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-233">An alias can be saved and reused in another PowerShell session by doing an export and import.</span></span> <span data-ttu-id="b9809-234">별칭을 파일에 저장 하려면를 사용 `Export-Alias` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-234">To save an alias to a file, use `Export-Alias`.</span></span> <span data-ttu-id="b9809-235">새 PowerShell 세션에 저장 된 별칭을 추가 하려면를 사용 `Import-Alias` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9809-235">To add a saved alias to a new PowerShell session, use `Import-Alias`.</span></span>

## <span data-ttu-id="b9809-236">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b9809-236">RELATED LINKS</span></span>

[<span data-ttu-id="b9809-237">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="b9809-237">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="b9809-238">about_Functions</span><span class="sxs-lookup"><span data-stu-id="b9809-238">about_Functions</span></span>](../Microsoft.PowerShell.Core/about/about_Functions.md)

[<span data-ttu-id="b9809-239">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="b9809-239">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_Profiles.md)

[<span data-ttu-id="b9809-240">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="b9809-240">about_Scopes</span></span>](../Microsoft.PowerShell.Core/About/about_Scopes.md)

[<span data-ttu-id="b9809-241">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="b9809-241">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="b9809-242">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="b9809-242">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="b9809-243">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="b9809-243">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="b9809-244">New-Alias</span><span class="sxs-lookup"><span data-stu-id="b9809-244">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="b9809-245">Remove-Alias</span><span class="sxs-lookup"><span data-stu-id="b9809-245">Remove-Alias</span></span>](Remove-Alias.md)

[<span data-ttu-id="b9809-246">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="b9809-246">Remove-Item</span></span>](../Microsoft.PowerShell.Management/Remove-Item.md)


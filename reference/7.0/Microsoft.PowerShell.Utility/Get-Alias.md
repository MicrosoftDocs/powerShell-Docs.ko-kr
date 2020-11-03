---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: 98f68cff8501fec375e3a2b8ac446e41d5721fc7
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210713"
---
# <span data-ttu-id="e2ba0-103">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="e2ba0-103">Get-Alias</span></span>

## <span data-ttu-id="e2ba0-104">개요</span><span class="sxs-lookup"><span data-stu-id="e2ba0-104">SYNOPSIS</span></span>
<span data-ttu-id="e2ba0-105">현재 세션의 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-105">Gets the aliases for the current session.</span></span>

## <span data-ttu-id="e2ba0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e2ba0-106">SYNTAX</span></span>

### <span data-ttu-id="e2ba0-107">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="e2ba0-107">Default (Default)</span></span>

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>] [<CommonParameters>]
```

### <span data-ttu-id="e2ba0-108">정의</span><span class="sxs-lookup"><span data-stu-id="e2ba0-108">Definition</span></span>

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="e2ba0-109">설명</span><span class="sxs-lookup"><span data-stu-id="e2ba0-109">DESCRIPTION</span></span>

<span data-ttu-id="e2ba0-110">이 **cmdlet은** 현재 세션의 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-110">The **Get-Alias** cmdlet gets the aliases in the current session.</span></span>
<span data-ttu-id="e2ba0-111">여기에는 기본 제공 별칭, 사용자가 설정 하거나 가져온 별칭 및 PowerShell 프로필에 추가한 별칭이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-111">This includes built-in aliases, aliases that you have set or imported, and aliases that you have added to your PowerShell profile.</span></span>

<span data-ttu-id="e2ba0-112">기본적 **으로, alias는 별칭을 사용** 하 여 명령 이름을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-112">By default, **Get-Alias** takes an alias and returns the command name.</span></span>
<span data-ttu-id="e2ba0-113">*Definition* 매개 변수를 사용 하는 경우에는 **Get 별칭** 에서 명령 이름을 사용 하 여 해당 별칭을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-113">When you use the *Definition* parameter, **Get-Alias** takes a command name and returns its aliases.</span></span>

<span data-ttu-id="e2ba0-114">Windows PowerShell 3.0부터 **가져오기 별칭** 에는 하이픈을 사용 하지 않는 별칭 이름이 형식으로 표시 `<alias> -> <definition>` 되므로 필요한 정보를 더 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-114">Beginning in Windows PowerShell 3.0, **Get-Alias** displays non-hyphenated alias names in an `<alias> -> <definition>` format to make it even easier to find the information that you need.</span></span>

## <span data-ttu-id="e2ba0-115">예제</span><span class="sxs-lookup"><span data-stu-id="e2ba0-115">EXAMPLES</span></span>

### <span data-ttu-id="e2ba0-116">예 1: 현재 세션의 모든 별칭 가져오기</span><span class="sxs-lookup"><span data-stu-id="e2ba0-116">Example 1: Get all aliases in the current session</span></span>

```
PS C:\> Get-Alias

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           asnp -> Add-PSSnapin
Alias           cat -> Get-Content
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           clc -> Clear-Content
Alias           clear -> Clear-Host
Alias           clhy -> Clear-History
...
```

<span data-ttu-id="e2ba0-117">이 명령은 현재 세션의 모든 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-117">This command gets all aliases in the current session.</span></span>

<span data-ttu-id="e2ba0-118">출력은 `<alias> -> <definition>` Windows PowerShell 3.0에 도입 된 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-118">The output shows the `<alias> -> <definition>` format that was introduced in Windows PowerShell 3.0.</span></span>
<span data-ttu-id="e2ba0-119">일반적으로 cmdlet 및 함수 이름에는 애칭 대신 하이픈 있는 별칭을 사용하는 것이 좋으므로 이 형식은 하이픈을 포함하지 않는 별칭에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-119">This format is used only for aliases that do not include hyphens, because aliases with hyphens are typically preferred names for cmdlets and functions, rather than nicknames.</span></span>

### <span data-ttu-id="e2ba0-120">예제 2: 이름으로 별칭 가져오기</span><span class="sxs-lookup"><span data-stu-id="e2ba0-120">Example 2: Get aliases by name</span></span>

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

<span data-ttu-id="e2ba0-121">이 명령은 ps로 끝나는 별칭을 제외 하 고 gp 또는 sp로 시작 하는 모든 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-121">This command gets all aliases that begin with gp or sp, except for aliases that end with ps.</span></span>

### <span data-ttu-id="e2ba0-122">예 3: cmdlet에 대 한 별칭 가져오기</span><span class="sxs-lookup"><span data-stu-id="e2ba0-122">Example 3: Get aliases for a cmdlet</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

<span data-ttu-id="e2ba0-123">이 명령은 Get-ChildItem cmdlet의 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-123">This command gets the aliases for the Get-ChildItem cmdlet.</span></span>

<span data-ttu-id="e2ba0-124">기본적으로, 별칭을 알고 있는 경우 **에는 별칭 cmdlet이** 항목 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-124">By default, the **Get-Alias** cmdlet gets the item name when you know the alias.</span></span>
<span data-ttu-id="e2ba0-125">*정의* 매개 변수는 항목 이름을 알고 있을 때 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-125">The *Definition* parameter gets the alias when you know the item name.</span></span>

### <span data-ttu-id="e2ba0-126">예제 4: 속성으로 별칭 가져오기</span><span class="sxs-lookup"><span data-stu-id="e2ba0-126">Example 4: Get aliases by property</span></span>

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

<span data-ttu-id="e2ba0-127">이 명령은 Options 속성 값이 ReadOnly 인 모든 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-127">This command gets all aliases in which the value of the Options property is ReadOnly.</span></span>
<span data-ttu-id="e2ba0-128">이 명령은 읽기 전용 옵션이 있으므로 PowerShell에 기본 제공 되는 별칭을 신속 하 게 찾는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-128">This command provides a quick way to find the aliases that are built into PowerShell, because they have the ReadOnly option.</span></span>

<span data-ttu-id="e2ba0-129">옵션은 System.management.automation.aliasinfo가 **가져오는** 개체의 속성 중 하나일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-129">Options is just one property of the AliasInfo objects that **Get-Alias** gets.</span></span>
<span data-ttu-id="e2ba0-130">System.management.automation.aliasinfo 개체의 속성 및 메서드를 모두 찾으려면를 입력 `Get-Alias | get-member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-130">To find all properties and methods of AliasInfo objects, type `Get-Alias | get-member`.</span></span>

### <span data-ttu-id="e2ba0-131">예 5: 이름을 기준으로 별칭 가져오기 및 시작 문자를 기준으로 필터링</span><span class="sxs-lookup"><span data-stu-id="e2ba0-131">Example 5: Get aliases by name and filter by beginning letter</span></span>

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

<span data-ttu-id="e2ba0-132">이 예제에서는 이름이 "e"로 시작하지 않고 "-PSSession"으로 끝나는 명령의 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-132">This example gets aliases for commands that have names that end in "-PSSession", except for those that begin with "e".</span></span>

<span data-ttu-id="e2ba0-133">이 명령은 *scope* 매개 변수를 사용 하 여 전역 범위에 명령을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-133">The command uses the *Scope* parameter to apply the command in the global scope.</span></span>
<span data-ttu-id="e2ba0-134">이 명령은 스크립트에서 세션의 별칭을 가져오려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-134">This is useful in scripts when you want to get the aliases in the session.</span></span>

## <span data-ttu-id="e2ba0-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e2ba0-135">PARAMETERS</span></span>

### <span data-ttu-id="e2ba0-136">-Definition</span><span class="sxs-lookup"><span data-stu-id="e2ba0-136">-Definition</span></span>

<span data-ttu-id="e2ba0-137">지정한 항목의 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-137">Gets the aliases for the specified item.</span></span>
<span data-ttu-id="e2ba0-138">cmdlet, 함수, 스크립트, 파일 또는 실행 파일의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-138">Enter the name of a cmdlet, function, script, file, or executable file.</span></span>

<span data-ttu-id="e2ba0-139">이 매개 변수는 별칭 개체의 Definition 속성에서 항목 이름을 검색 하므로 *정의* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-139">This parameter is called *Definition* , because it searches for the item name in the Definition property of the alias object.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Definition
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e2ba0-140">-제외</span><span class="sxs-lookup"><span data-stu-id="e2ba0-140">-Exclude</span></span>

<span data-ttu-id="e2ba0-141">지정된 항목을 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-141">Omits the specified items.</span></span>
<span data-ttu-id="e2ba0-142">이 매개 변수 값은 Name 및 Definition 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-142">The value of this parameter qualifies the Name and Definition parameters.</span></span>
<span data-ttu-id="e2ba0-143">이름, 정의 또는 패턴(예: "s\*")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-143">Enter a name, a definition, or a pattern, such as "s\*".</span></span>
<span data-ttu-id="e2ba0-144">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-144">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="e2ba0-145">-Name</span><span class="sxs-lookup"><span data-stu-id="e2ba0-145">-Name</span></span>

<span data-ttu-id="e2ba0-146">이 cmdlet이 가져오는 별칭을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-146">Specifies the aliases that this cmdlet gets.</span></span>
<span data-ttu-id="e2ba0-147">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-147">Wildcards are permitted.</span></span>
<span data-ttu-id="e2ba0-148">기본적으로는 `Get-Alias` 현재 세션에 대해 정의 된 모든 별칭을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-148">By default, `Get-Alias` retrieves all aliases defined for the current session.</span></span>
<span data-ttu-id="e2ba0-149">매개 변수 이름 **이름은** 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-149">The parameter name **Name** is optional.</span></span>
<span data-ttu-id="e2ba0-150">별칭 이름을로 파이프 할 수도 있습니다 `Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="e2ba0-150">You can also pipe alias names to `Get-Alias`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: All aliases
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="e2ba0-151">-범위</span><span class="sxs-lookup"><span data-stu-id="e2ba0-151">-Scope</span></span>

<span data-ttu-id="e2ba0-152">이 cmdlet이 별칭을 가져오는 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-152">Specifies the scope for which this cmdlet gets aliases.</span></span>
<span data-ttu-id="e2ba0-153">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e2ba0-154">전역</span><span class="sxs-lookup"><span data-stu-id="e2ba0-154">Global</span></span>
- <span data-ttu-id="e2ba0-155">로컬</span><span class="sxs-lookup"><span data-stu-id="e2ba0-155">Local</span></span>
- <span data-ttu-id="e2ba0-156">스크립트</span><span class="sxs-lookup"><span data-stu-id="e2ba0-156">Script</span></span>
- <span data-ttu-id="e2ba0-157">현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)</span><span class="sxs-lookup"><span data-stu-id="e2ba0-157">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="e2ba0-158">Local이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-158">Local is the default.</span></span>
<span data-ttu-id="e2ba0-159">자세한 내용은 about_Scopes를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-159">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="e2ba0-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e2ba0-160">CommonParameters</span></span>

<span data-ttu-id="e2ba0-161">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e2ba0-162">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e2ba0-163">입력</span><span class="sxs-lookup"><span data-stu-id="e2ba0-163">INPUTS</span></span>

### <span data-ttu-id="e2ba0-164">System.String</span><span class="sxs-lookup"><span data-stu-id="e2ba0-164">System.String</span></span>

<span data-ttu-id="e2ba0-165">**별칭에 별칭** 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-165">You can pipe alias names to **Get-Alias** .</span></span>

## <span data-ttu-id="e2ba0-166">출력</span><span class="sxs-lookup"><span data-stu-id="e2ba0-166">OUTPUTS</span></span>

### <span data-ttu-id="e2ba0-167">System.management.automation.aliasinfo.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-167">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="e2ba0-168">**Get-help** 는 각 별칭을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-168">**Get-Alias** returns an object that represents each alias.</span></span>
<span data-ttu-id="e2ba0-169">**Alias는** 모든 별칭에 대해 동일한 개체를 반환 하지만 PowerShell은 화살표 기반 형식을 사용 하 여 하이픈을 사용 하지 않는 별칭의 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-169">**Get-Alias** returns the same object for every alias, but PowerShell uses an arrow-based format to display the names of non-hyphenated aliases.</span></span>

## <span data-ttu-id="e2ba0-170">참고</span><span class="sxs-lookup"><span data-stu-id="e2ba0-170">NOTES</span></span>

- <span data-ttu-id="e2ba0-171">새 별칭을 만들려면 Set-Alias 또는 New-Alias를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-171">To create a new alias, use Set-Alias or New-Alias.</span></span> <span data-ttu-id="e2ba0-172">별칭을 삭제하려면 Remove-Item을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-172">To delete an alias, use Remove-Item.</span></span>
- <span data-ttu-id="e2ba0-173">하이픈을 포함하는 별칭에는 화살표 기반 별칭 이름 형식이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-173">The arrow-based alias name format is not used for aliases that include a hyphen.</span></span> <span data-ttu-id="e2ba0-174">대체로 cmdlet 및 함수의 대체 이름으로 일반적인 약어나 애칭 대신 별칭을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e2ba0-174">These are likely to be preferred substitute names for cmdlets and functions, instead of typical abbreviations or nicknames.</span></span>

## <span data-ttu-id="e2ba0-175">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e2ba0-175">RELATED LINKS</span></span>

[<span data-ttu-id="e2ba0-176">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="e2ba0-176">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="e2ba0-177">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="e2ba0-177">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="e2ba0-178">New-Alias</span><span class="sxs-lookup"><span data-stu-id="e2ba0-178">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="e2ba0-179">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="e2ba0-179">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="e2ba0-180">별칭 공급자</span><span class="sxs-lookup"><span data-stu-id="e2ba0-180">Alias Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[<span data-ttu-id="e2ba0-181">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="e2ba0-181">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

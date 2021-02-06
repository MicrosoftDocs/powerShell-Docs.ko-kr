---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: 7f226af3cb221543cdae88930f661e2343d954b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602680"
---
# <span data-ttu-id="d5a43-102">New-Alias</span><span class="sxs-lookup"><span data-stu-id="d5a43-102">New-Alias</span></span>

## <span data-ttu-id="d5a43-103">개요</span><span class="sxs-lookup"><span data-stu-id="d5a43-103">SYNOPSIS</span></span>
<span data-ttu-id="d5a43-104">새 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-104">Creates a new alias.</span></span>

## <span data-ttu-id="d5a43-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d5a43-105">SYNTAX</span></span>

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d5a43-106">설명</span><span class="sxs-lookup"><span data-stu-id="d5a43-106">DESCRIPTION</span></span>

<span data-ttu-id="d5a43-107">**새 별칭** cmdlet은 현재 PowerShell 세션에서 새 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-107">The **New-Alias** cmdlet creates a new alias in the current PowerShell session.</span></span>
<span data-ttu-id="d5a43-108">세션을 종료 하거나 PowerShell을 닫은 후에는 **새 별칭** 을 사용 하 여 만든 별칭이 저장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-108">Aliases created by using **New-Alias** are not saved after you exit the session or close PowerShell.</span></span>
<span data-ttu-id="d5a43-109">Export-Alias cmdlet을 사용하여 파일에 별칭 정보를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-109">You can use the Export-Alias cmdlet to save your alias information to a file.</span></span>
<span data-ttu-id="d5a43-110">나중에 **Import-alias** 를 사용 하 여 저장 된 별칭 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-110">You can later use **Import-Alias** to retrieve that saved alias information.</span></span>

## <span data-ttu-id="d5a43-111">예제</span><span class="sxs-lookup"><span data-stu-id="d5a43-111">EXAMPLES</span></span>

### <span data-ttu-id="d5a43-112">예제 1: cmdlet에 대 한 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="d5a43-112">Example 1: Create an alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "List" Get-ChildItem
```

<span data-ttu-id="d5a43-113">이 명령은 Get-ChildItem cmdlet을 나타내는 별칭 이라는 이름의 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-113">This command creates an alias named List to represent the Get-ChildItem cmdlet.</span></span>

### <span data-ttu-id="d5a43-114">예제 2: cmdlet에 대 한 읽기 전용 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="d5a43-114">Example 2: Create a read-only alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "W" -Value Get-WmiObject -Description "quick wmi alias" -Option ReadOnly
PS C:\> Get-Alias -Name "W" | Format-List *
```

<span data-ttu-id="d5a43-115">이 명령은 Get-WmiObject cmdlet을 나타내는 W 라는 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-115">This command creates an alias named W to represent the Get-WmiObject cmdlet.</span></span>
<span data-ttu-id="d5a43-116">별칭에 대 한 설명, 빠른 wmi 별칭을 만들고 읽기 전용으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-116">It creates a description, quick wmi alias, for the alias and makes it read-only.</span></span>
<span data-ttu-id="d5a43-117">명령의 마지막 줄은 Get-Alias를 사용하여 새 별칭을 가져오고 이를 Format-List로 파이프하여 그에 대한 모든 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-117">The last line of the command uses Get-Alias to get the new alias and pipes it to Format-List to display all of the information about it.</span></span>

## <span data-ttu-id="d5a43-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d5a43-118">PARAMETERS</span></span>

### <span data-ttu-id="d5a43-119">-Description</span><span class="sxs-lookup"><span data-stu-id="d5a43-119">-Description</span></span>

<span data-ttu-id="d5a43-120">별칭에 대한 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-120">Specifies a description of the alias.</span></span>
<span data-ttu-id="d5a43-121">아무 문자열이나 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-121">You can type any string.</span></span>
<span data-ttu-id="d5a43-122">설명에 공백이 포함되어 있으면 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-122">If the description includes spaces, enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="d5a43-123">-Force</span><span class="sxs-lookup"><span data-stu-id="d5a43-123">-Force</span></span>

<span data-ttu-id="d5a43-124">이라는 별칭이 이미 있는 경우 cmdlet이 Set-Alias 처럼 동작 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-124">Indicates that the cmdlet acts like Set-Alias if the alias named already exists.</span></span>

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

### <span data-ttu-id="d5a43-125">-Name</span><span class="sxs-lookup"><span data-stu-id="d5a43-125">-Name</span></span>

<span data-ttu-id="d5a43-126">새 별칭을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-126">Specifies the new alias.</span></span>
<span data-ttu-id="d5a43-127">별칭에는 모든 영숫자 문자를 사용할 수 있지만 첫 문자는 숫자가 아니어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-127">You can use any alphanumeric characters in an alias, but the first character cannot be a number.</span></span>

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

### <span data-ttu-id="d5a43-128">-옵션</span><span class="sxs-lookup"><span data-stu-id="d5a43-128">-Option</span></span>

<span data-ttu-id="d5a43-129">별칭의 **Options** 속성 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-129">Specifies the value of the **Options** property of the alias.</span></span>
<span data-ttu-id="d5a43-130">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-130">Valid values are:</span></span>

- <span data-ttu-id="d5a43-131">없음: 별칭에 제약 조건 (기본값)이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-131">None: The alias has no constraints (default value)</span></span>
- <span data-ttu-id="d5a43-132">ReadOnly: 별칭을 삭제할 수는 있지만 **Force** 매개 변수를 사용 하는 경우를 제외 하 고는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-132">ReadOnly: The alias can be deleted but cannot be changed except by using the **Force** parameter</span></span>
- <span data-ttu-id="d5a43-133">상수: 별칭을 삭제 하거나 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-133">Constant: The alias cannot be deleted or changed</span></span>
- <span data-ttu-id="d5a43-134">비공개: 별칭은 현재 범위 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-134">Private: The alias is available only in the current scope</span></span>
- <span data-ttu-id="d5a43-135">AllScope: 별칭이 만들어진 모든 새 범위에 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-135">AllScope: The alias is copied to any new scopes that are created</span></span>
- <span data-ttu-id="d5a43-136">지정 되지 않음: 옵션이 지정 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-136">Unspecified: The option is not specified</span></span>

<span data-ttu-id="d5a43-137">세션에 있는 모든 별칭의 **Options** 속성을 보려면를 입력 `Get-Alias | Format-Table -Property Name, Options -AutoSize` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-137">To see the **Options** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -AutoSize`.</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: [System.Management.Automation.ScopedItemOptions]::None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d5a43-138">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d5a43-138">-PassThru</span></span>

<span data-ttu-id="d5a43-139">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-139">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="d5a43-140">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-140">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="d5a43-141">-범위</span><span class="sxs-lookup"><span data-stu-id="d5a43-141">-Scope</span></span>

<span data-ttu-id="d5a43-142">새 별칭의 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-142">Specifies the scope of the new alias.</span></span>
<span data-ttu-id="d5a43-143">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-143">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d5a43-144">전역</span><span class="sxs-lookup"><span data-stu-id="d5a43-144">Global</span></span>
- <span data-ttu-id="d5a43-145">로컬</span><span class="sxs-lookup"><span data-stu-id="d5a43-145">Local</span></span>
- <span data-ttu-id="d5a43-146">스크립트</span><span class="sxs-lookup"><span data-stu-id="d5a43-146">Script</span></span>
- <span data-ttu-id="d5a43-147">현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)입니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-147">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="d5a43-148">Local이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-148">Local is the default.</span></span>
<span data-ttu-id="d5a43-149">자세한 내용은 about_Scopes를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5a43-149">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="d5a43-150">-Value</span><span class="sxs-lookup"><span data-stu-id="d5a43-150">-Value</span></span>

<span data-ttu-id="d5a43-151">별칭을 지정할 cmdlet 또는 명령 요소의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-151">Specifies the name of the cmdlet or command element that is being aliased.</span></span>

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

### <span data-ttu-id="d5a43-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d5a43-152">-Confirm</span></span>

<span data-ttu-id="d5a43-153">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d5a43-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d5a43-154">-WhatIf</span></span>

<span data-ttu-id="d5a43-155">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d5a43-156">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d5a43-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d5a43-157">CommonParameters</span></span>

<span data-ttu-id="d5a43-158">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d5a43-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d5a43-159">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5a43-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d5a43-160">입력</span><span class="sxs-lookup"><span data-stu-id="d5a43-160">INPUTS</span></span>

### <span data-ttu-id="d5a43-161">없음</span><span class="sxs-lookup"><span data-stu-id="d5a43-161">None</span></span>

<span data-ttu-id="d5a43-162">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-162">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d5a43-163">출력</span><span class="sxs-lookup"><span data-stu-id="d5a43-163">OUTPUTS</span></span>

### <span data-ttu-id="d5a43-164">없음 또는 System.management.automation.aliasinfo</span><span class="sxs-lookup"><span data-stu-id="d5a43-164">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="d5a43-165">*Passthru* 매개 변수를 사용 하는 경우 **새** 별칭을 나타내는 **system.management.automation.aliasinfo** 개체가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-165">When you use the *Passthru* parameter, **New-Alias** generates a **System.Management.Automation.AliasInfo** object representing the new alias.</span></span>
<span data-ttu-id="d5a43-166">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-166">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d5a43-167">참고</span><span class="sxs-lookup"><span data-stu-id="d5a43-167">NOTES</span></span>

* <span data-ttu-id="d5a43-168">새 별칭을 만들려면 또는를 사용 `Set-Alias` `New-Alias` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-168">To create a new alias, use `Set-Alias` or `New-Alias`.</span></span> <span data-ttu-id="d5a43-169">별칭을 변경 하려면를 사용 `Set-Alias` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-169">To change an alias, use `Set-Alias`.</span></span> <span data-ttu-id="d5a43-170">별칭을 삭제 하려면를 사용 `Remove-Item` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a43-170">To delete an alias, use `Remove-Item`.</span></span>

## <span data-ttu-id="d5a43-171">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d5a43-171">RELATED LINKS</span></span>

[<span data-ttu-id="d5a43-172">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="d5a43-172">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="d5a43-173">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="d5a43-173">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="d5a43-174">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="d5a43-174">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="d5a43-175">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="d5a43-175">Set-Alias</span></span>](Set-Alias.md)


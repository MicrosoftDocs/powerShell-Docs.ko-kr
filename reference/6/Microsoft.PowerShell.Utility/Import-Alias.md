---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: 438f089c1cd6e647ae5ee858234a3919bdc0328d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216073"
---
# <span data-ttu-id="d2263-103">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="d2263-103">Import-Alias</span></span>

## <span data-ttu-id="d2263-104">개요</span><span class="sxs-lookup"><span data-stu-id="d2263-104">SYNOPSIS</span></span>
<span data-ttu-id="d2263-105">파일에서 별칭 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-105">Imports an alias list from a file.</span></span>

## <span data-ttu-id="d2263-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d2263-106">SYNTAX</span></span>

### <span data-ttu-id="d2263-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="d2263-107">ByPath (Default)</span></span>

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d2263-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="d2263-108">ByLiteralPath</span></span>

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="d2263-109">설명</span><span class="sxs-lookup"><span data-stu-id="d2263-109">DESCRIPTION</span></span>

<span data-ttu-id="d2263-110">`Import-Alias`Cmdlet은 파일에서 별칭 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-110">The `Import-Alias` cmdlet imports an alias list from a file.</span></span>

<span data-ttu-id="d2263-111">Windows PowerShell 3.0부터 보안 기능부터 `Import-Alias` 은 기본적으로 기존 별칭을 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-111">Beginning in Windows PowerShell 3.0, as a security feature, `Import-Alias` does not overwrite existing aliases by default.</span></span>
<span data-ttu-id="d2263-112">기존 별칭을 덮어쓰려면 별칭 파일의 내용이 안전한지 확인한 후 **Force** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-112">To overwrite an existing alias, after assuring that the contents of the alias file is safe, use the **Force** parameter.</span></span>

## <span data-ttu-id="d2263-113">예제</span><span class="sxs-lookup"><span data-stu-id="d2263-113">EXAMPLES</span></span>

### <span data-ttu-id="d2263-114">예제 1: 파일에서 별칭 가져오기</span><span class="sxs-lookup"><span data-stu-id="d2263-114">Example 1: Import aliases from a file</span></span>

```powershell
Import-Alias test.txt
```

<span data-ttu-id="d2263-115">이 명령은 test.txt라는 파일에서 별칭 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-115">This command imports alias information from a file named test.txt.</span></span>

## <span data-ttu-id="d2263-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d2263-116">PARAMETERS</span></span>

### <span data-ttu-id="d2263-117">-Force</span><span class="sxs-lookup"><span data-stu-id="d2263-117">-Force</span></span>

<span data-ttu-id="d2263-118">cmdlet이 이미 정의되어 있거나 읽기 전용인 별칭을 가져올 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-118">Allows the cmdlet to import an alias that is already defined or is read only.</span></span>
<span data-ttu-id="d2263-119">다음 명령을 사용하여 현재 정의된 별칭에 대한 정보를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-119">You can use the following command to display information about the currently-defined aliases:</span></span>

`Get-Alias | Select-Object Name, Options`

<span data-ttu-id="d2263-120">해당 별칭이 읽기 전용인 경우 **Options** 속성 값에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-120">If the corresponding alias is read-only, it will be displayed in the value of the **Options** property.</span></span>

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

### <span data-ttu-id="d2263-121">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d2263-121">-LiteralPath</span></span>

<span data-ttu-id="d2263-122">내보낸 별칭 정보가 포함된 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-122">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="d2263-123">**Path** 매개 변수와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-123">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="d2263-124">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-124">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="d2263-125">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="d2263-125">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="d2263-126">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-126">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d2263-127">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d2263-127">-PassThru</span></span>

<span data-ttu-id="d2263-128">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-128">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="d2263-129">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-129">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="d2263-130">-Path</span><span class="sxs-lookup"><span data-stu-id="d2263-130">-Path</span></span>

<span data-ttu-id="d2263-131">내보낸 별칭 정보가 포함된 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-131">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="d2263-132">와일드카드를 사용할 수 있지만 하나의 이름으로 확인되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-132">Wildcards are allowed but they must resolve to a single name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="d2263-133">-범위</span><span class="sxs-lookup"><span data-stu-id="d2263-133">-Scope</span></span>

<span data-ttu-id="d2263-134">별칭을 가져올 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-134">Specifies the scope into which the aliases are imported.</span></span>
<span data-ttu-id="d2263-135">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d2263-136">전역</span><span class="sxs-lookup"><span data-stu-id="d2263-136">Global</span></span>
- <span data-ttu-id="d2263-137">로컬</span><span class="sxs-lookup"><span data-stu-id="d2263-137">Local</span></span>
- <span data-ttu-id="d2263-138">스크립트</span><span class="sxs-lookup"><span data-stu-id="d2263-138">Script</span></span>
- <span data-ttu-id="d2263-139">현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)</span><span class="sxs-lookup"><span data-stu-id="d2263-139">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="d2263-140">기본값은 Local입니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-140">The default is Local.</span></span>
<span data-ttu-id="d2263-141">자세한 내용은 about_Scopes를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2263-141">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="d2263-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d2263-142">-Confirm</span></span>

<span data-ttu-id="d2263-143">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d2263-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d2263-144">-WhatIf</span></span>

<span data-ttu-id="d2263-145">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d2263-146">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d2263-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d2263-147">CommonParameters</span></span>

<span data-ttu-id="d2263-148">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d2263-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d2263-149">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2263-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d2263-150">입력</span><span class="sxs-lookup"><span data-stu-id="d2263-150">INPUTS</span></span>

### <span data-ttu-id="d2263-151">System.String</span><span class="sxs-lookup"><span data-stu-id="d2263-151">System.String</span></span>

<span data-ttu-id="d2263-152">경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Import-Alias` .</span><span class="sxs-lookup"><span data-stu-id="d2263-152">You can pipe a string that contains a path to `Import-Alias`.</span></span>

## <span data-ttu-id="d2263-153">출력</span><span class="sxs-lookup"><span data-stu-id="d2263-153">OUTPUTS</span></span>

### <span data-ttu-id="d2263-154">없음 또는 System.management.automation.aliasinfo</span><span class="sxs-lookup"><span data-stu-id="d2263-154">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="d2263-155">**Passthru** 매개 변수를 사용 하는 경우는 `Import-Alias` 별칭을 나타내는 **system.management.automation.aliasinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-155">When you use the **Passthru** parameter, `Import-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="d2263-156">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2263-156">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d2263-157">참고</span><span class="sxs-lookup"><span data-stu-id="d2263-157">NOTES</span></span>

## <span data-ttu-id="d2263-158">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d2263-158">RELATED LINKS</span></span>

[<span data-ttu-id="d2263-159">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="d2263-159">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="d2263-160">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="d2263-160">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="d2263-161">New-Alias</span><span class="sxs-lookup"><span data-stu-id="d2263-161">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="d2263-162">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="d2263-162">Set-Alias</span></span>](Set-Alias.md)

---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 6f98a910e43b87793ac4f2af8ffb069d3e5d47ba
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210289"
---
# <span data-ttu-id="56689-103">Remove-Alias</span><span class="sxs-lookup"><span data-stu-id="56689-103">Remove-Alias</span></span>

## <span data-ttu-id="56689-104">개요</span><span class="sxs-lookup"><span data-stu-id="56689-104">SYNOPSIS</span></span>
<span data-ttu-id="56689-105">현재 세션에서 별칭을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="56689-105">Remove an alias from the current session.</span></span>

## <span data-ttu-id="56689-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="56689-106">SYNTAX</span></span>

### <span data-ttu-id="56689-107">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="56689-107">Default (Default)</span></span>

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="56689-108">설명</span><span class="sxs-lookup"><span data-stu-id="56689-108">DESCRIPTION</span></span>

<span data-ttu-id="56689-109">`Remove-Alias`Cmdlet은 현재 PowerShell 세션에서 별칭을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="56689-109">The `Remove-Alias` cmdlet removes an alias from the current PowerShell session.</span></span> <span data-ttu-id="56689-110">**Option** 속성이 **ReadOnly** 로 설정 된 별칭을 제거 하려면 **Force** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="56689-110">To remove an alias with the **Option** property set to **ReadOnly** , use the **Force** parameter.</span></span>

<span data-ttu-id="56689-111">`Remove-Alias`Cmdlet은 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="56689-111">The `Remove-Alias` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="56689-112">예제</span><span class="sxs-lookup"><span data-stu-id="56689-112">EXAMPLES</span></span>

### <span data-ttu-id="56689-113">예제 1-별칭 제거</span><span class="sxs-lookup"><span data-stu-id="56689-113">Example 1 - Remove an alias</span></span>

<span data-ttu-id="56689-114">이 예에서는 cmdlet을 나타내는 라는 별칭을 제거 합니다 `del` `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="56689-114">This example removes an alias named `del` that represents the `Remove-Item` cmdlet.</span></span>

```powershell
Remove-Alias -Name del
```

### <span data-ttu-id="56689-115">예제 2-비상수 별칭 모두 제거</span><span class="sxs-lookup"><span data-stu-id="56689-115">Example 2 - Remove all non-Constant aliases</span></span>

<span data-ttu-id="56689-116">이 예에서는 **Options** 속성이 **상수로** 설정 된 별칭을 제외 하 고 현재 PowerShell 세션에서 모든 별칭을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="56689-116">This example removes all aliases from the current PowerShell session, except for aliases with the **Options** property set to **Constant** .</span></span> <span data-ttu-id="56689-117">명령을 실행 한 후에는 다른 PowerShell 세션 또는 새로운 PowerShell 세션에서 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56689-117">After the command is run, the aliases are available in other PowerShell sessions or new PowerShell sessions.</span></span>

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

<span data-ttu-id="56689-118">`Get-Alias` PowerShell 세션의 모든 별칭을 가져오고 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="56689-118">`Get-Alias` gets all the aliases in the PowerShell session and sends the objects down the pipeline.</span></span>
<span data-ttu-id="56689-119">`Where-Object` 는 스크립트 블록을 사용 하 고 자동 변수 ( `$_` ) 및 **옵션** 속성은 현재 파이프라인 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="56689-119">`Where-Object` uses a script block, and the automatic variable (`$_`) and **Options** property represent the current pipeline object.</span></span> <span data-ttu-id="56689-120">**NE** (같지 않음) 매개 변수는 **옵션** 값이 **상수로** 설정 되지 않은 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="56689-120">The parameter **NE** (not equal), selects objects that don't have an **Options** value set to **Constant** .</span></span> <span data-ttu-id="56689-121">`Remove-Alias`**Force** 매개 변수를 사용 하 여 PowerShell 세션에서 읽기 전용 별칭을 포함 하 여 별칭을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="56689-121">`Remove-Alias` uses the **Force** parameter to remove aliases, including read-only aliases, from the PowerShell session.</span></span>

## <span data-ttu-id="56689-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="56689-122">PARAMETERS</span></span>

### <span data-ttu-id="56689-123">-Force</span><span class="sxs-lookup"><span data-stu-id="56689-123">-Force</span></span>

<span data-ttu-id="56689-124">**옵션** 속성이 **ReadOnly** 로 설정 된 별칭을 포함 하 여 cmdlet이 별칭을 제거 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="56689-124">Indicates that the cmdlet removes an alias, including aliases with the **Option** property set to **ReadOnly** .</span></span> <span data-ttu-id="56689-125">**Force** 매개 변수는 **옵션** 속성이 **상수로** 설정 된 별칭을 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56689-125">The **Force** parameter can't remove an alias with an **Option** property set to **Constant** .</span></span>

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

### <span data-ttu-id="56689-126">-Name</span><span class="sxs-lookup"><span data-stu-id="56689-126">-Name</span></span>

<span data-ttu-id="56689-127">제거할 별칭의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="56689-127">Specifies the name of the alias to remove.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="56689-128">-범위</span><span class="sxs-lookup"><span data-stu-id="56689-128">-Scope</span></span>

<span data-ttu-id="56689-129">지정 된 범위에 있는 별칭에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="56689-129">Affects only the aliases in the specified scope.</span></span> <span data-ttu-id="56689-130">기본 범위는 **Local** 입니다.</span><span class="sxs-lookup"><span data-stu-id="56689-130">The default scope is **Local** .</span></span> <span data-ttu-id="56689-131">자세한 내용은 [about_Scopes](../microsoft.powershell.core/about/about_scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56689-131">For more information, see [about_Scopes](../microsoft.powershell.core/about/about_scopes.md).</span></span>

<span data-ttu-id="56689-132">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="56689-132">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="56689-133">전역</span><span class="sxs-lookup"><span data-stu-id="56689-133">Global</span></span>
- <span data-ttu-id="56689-134">로컬</span><span class="sxs-lookup"><span data-stu-id="56689-134">Local</span></span>
- <span data-ttu-id="56689-135">스크립트</span><span class="sxs-lookup"><span data-stu-id="56689-135">Script</span></span>
- <span data-ttu-id="56689-136">현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)</span><span class="sxs-lookup"><span data-stu-id="56689-136">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

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

### <span data-ttu-id="56689-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="56689-137">CommonParameters</span></span>

<span data-ttu-id="56689-138">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="56689-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="56689-139">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56689-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="56689-140">입력</span><span class="sxs-lookup"><span data-stu-id="56689-140">INPUTS</span></span>

### <span data-ttu-id="56689-141">System.String[]</span><span class="sxs-lookup"><span data-stu-id="56689-141">System.String[]</span></span>

<span data-ttu-id="56689-142">별칭 개체를 파이프로 파이프 하 여 **제거할** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56689-142">You can pipe an alias object to **Remove-Alias** .</span></span>

## <span data-ttu-id="56689-143">출력</span><span class="sxs-lookup"><span data-stu-id="56689-143">OUTPUTS</span></span>

### <span data-ttu-id="56689-144">없음</span><span class="sxs-lookup"><span data-stu-id="56689-144">None</span></span>

<span data-ttu-id="56689-145">이 cmdlet은 출력을 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56689-145">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="56689-146">참고</span><span class="sxs-lookup"><span data-stu-id="56689-146">NOTES</span></span>

<span data-ttu-id="56689-147">변경 내용은 현재 범위에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="56689-147">Changes only affect the current scope.</span></span> <span data-ttu-id="56689-148">모든 세션에서 별칭을 제거 하려면 PowerShell 프로필에 **제거 별칭** 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="56689-148">To remove an alias from all sessions, add a **Remove-Alias** command to your PowerShell profile.</span></span>

<span data-ttu-id="56689-149">자세한 내용은 [about_Aliases](../microsoft.powershell.core/about/about_aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56689-149">For more information, see [about_Aliases](../microsoft.powershell.core/about/about_aliases.md).</span></span>

## <span data-ttu-id="56689-150">관련 링크</span><span class="sxs-lookup"><span data-stu-id="56689-150">RELATED LINKS</span></span>

[<span data-ttu-id="56689-151">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="56689-151">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="56689-152">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="56689-152">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="56689-153">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="56689-153">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="56689-154">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="56689-154">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="56689-155">New-Alias</span><span class="sxs-lookup"><span data-stu-id="56689-155">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="56689-156">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="56689-156">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="56689-157">Where-Object</span><span class="sxs-lookup"><span data-stu-id="56689-157">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

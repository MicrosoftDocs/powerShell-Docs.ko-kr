---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 0ce13bef77e9ef9647809336aed650833dab51f3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601043"
---
# <span data-ttu-id="a957b-102">Remove-Alias</span><span class="sxs-lookup"><span data-stu-id="a957b-102">Remove-Alias</span></span>

## <span data-ttu-id="a957b-103">개요</span><span class="sxs-lookup"><span data-stu-id="a957b-103">SYNOPSIS</span></span>
<span data-ttu-id="a957b-104">현재 세션에서 별칭을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-104">Remove an alias from the current session.</span></span>

## <span data-ttu-id="a957b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a957b-105">SYNTAX</span></span>

### <span data-ttu-id="a957b-106">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="a957b-106">Default (Default)</span></span>

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="a957b-107">설명</span><span class="sxs-lookup"><span data-stu-id="a957b-107">DESCRIPTION</span></span>

<span data-ttu-id="a957b-108">`Remove-Alias`Cmdlet은 현재 PowerShell 세션에서 별칭을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-108">The `Remove-Alias` cmdlet removes an alias from the current PowerShell session.</span></span> <span data-ttu-id="a957b-109">**Option** 속성이 **ReadOnly** 로 설정 된 별칭을 제거 하려면 **Force** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-109">To remove an alias with the **Option** property set to **ReadOnly**, use the **Force** parameter.</span></span>

<span data-ttu-id="a957b-110">`Remove-Alias`Cmdlet은 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-110">The `Remove-Alias` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="a957b-111">예제</span><span class="sxs-lookup"><span data-stu-id="a957b-111">EXAMPLES</span></span>

### <span data-ttu-id="a957b-112">예제 1-별칭 제거</span><span class="sxs-lookup"><span data-stu-id="a957b-112">Example 1 - Remove an alias</span></span>

<span data-ttu-id="a957b-113">이 예에서는 cmdlet을 나타내는 라는 별칭을 제거 합니다 `del` `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="a957b-113">This example removes an alias named `del` that represents the `Remove-Item` cmdlet.</span></span>

```powershell
Remove-Alias -Name del
```

### <span data-ttu-id="a957b-114">예제 2-비상수 별칭 모두 제거</span><span class="sxs-lookup"><span data-stu-id="a957b-114">Example 2 - Remove all non-Constant aliases</span></span>

<span data-ttu-id="a957b-115">이 예에서는 **Options** 속성이 **상수로** 설정 된 별칭을 제외 하 고 현재 PowerShell 세션에서 모든 별칭을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-115">This example removes all aliases from the current PowerShell session, except for aliases with the **Options** property set to **Constant**.</span></span> <span data-ttu-id="a957b-116">명령을 실행 한 후에는 다른 PowerShell 세션 또는 새로운 PowerShell 세션에서 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-116">After the command is run, the aliases are available in other PowerShell sessions or new PowerShell sessions.</span></span>

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

<span data-ttu-id="a957b-117">`Get-Alias` PowerShell 세션의 모든 별칭을 가져오고 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-117">`Get-Alias` gets all the aliases in the PowerShell session and sends the objects down the pipeline.</span></span>
<span data-ttu-id="a957b-118">`Where-Object` 는 스크립트 블록을 사용 하 고 자동 변수 ( `$_` ) 및 **옵션** 속성은 현재 파이프라인 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-118">`Where-Object` uses a script block, and the automatic variable (`$_`) and **Options** property represent the current pipeline object.</span></span> <span data-ttu-id="a957b-119">**NE** (같지 않음) 매개 변수는 **옵션** 값이 **상수로** 설정 되지 않은 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-119">The parameter **NE** (not equal), selects objects that don't have an **Options** value set to **Constant**.</span></span> <span data-ttu-id="a957b-120">`Remove-Alias`**Force** 매개 변수를 사용 하 여 PowerShell 세션에서 읽기 전용 별칭을 포함 하 여 별칭을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-120">`Remove-Alias` uses the **Force** parameter to remove aliases, including read-only aliases, from the PowerShell session.</span></span>

## <span data-ttu-id="a957b-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a957b-121">PARAMETERS</span></span>

### <span data-ttu-id="a957b-122">-Force</span><span class="sxs-lookup"><span data-stu-id="a957b-122">-Force</span></span>

<span data-ttu-id="a957b-123">**옵션** 속성이 **ReadOnly** 로 설정 된 별칭을 포함 하 여 cmdlet이 별칭을 제거 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-123">Indicates that the cmdlet removes an alias, including aliases with the **Option** property set to **ReadOnly**.</span></span> <span data-ttu-id="a957b-124">**Force** 매개 변수는 **옵션** 속성이 **상수로** 설정 된 별칭을 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-124">The **Force** parameter can't remove an alias with an **Option** property set to **Constant**.</span></span>

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

### <span data-ttu-id="a957b-125">-Name</span><span class="sxs-lookup"><span data-stu-id="a957b-125">-Name</span></span>

<span data-ttu-id="a957b-126">제거할 별칭의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-126">Specifies the name of the alias to remove.</span></span>

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

### <span data-ttu-id="a957b-127">-범위</span><span class="sxs-lookup"><span data-stu-id="a957b-127">-Scope</span></span>

<span data-ttu-id="a957b-128">지정 된 범위에 있는 별칭에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-128">Affects only the aliases in the specified scope.</span></span> <span data-ttu-id="a957b-129">기본 범위는 **Local** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-129">The default scope is **Local**.</span></span> <span data-ttu-id="a957b-130">자세한 내용은 [about_Scopes](../microsoft.powershell.core/about/about_scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a957b-130">For more information, see [about_Scopes](../microsoft.powershell.core/about/about_scopes.md).</span></span>

<span data-ttu-id="a957b-131">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-131">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a957b-132">전역</span><span class="sxs-lookup"><span data-stu-id="a957b-132">Global</span></span>
- <span data-ttu-id="a957b-133">로컬</span><span class="sxs-lookup"><span data-stu-id="a957b-133">Local</span></span>
- <span data-ttu-id="a957b-134">스크립트</span><span class="sxs-lookup"><span data-stu-id="a957b-134">Script</span></span>
- <span data-ttu-id="a957b-135">현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)</span><span class="sxs-lookup"><span data-stu-id="a957b-135">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

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

### <span data-ttu-id="a957b-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a957b-136">CommonParameters</span></span>

<span data-ttu-id="a957b-137">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a957b-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a957b-138">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a957b-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a957b-139">입력</span><span class="sxs-lookup"><span data-stu-id="a957b-139">INPUTS</span></span>

### <span data-ttu-id="a957b-140">System.String[]</span><span class="sxs-lookup"><span data-stu-id="a957b-140">System.String[]</span></span>

<span data-ttu-id="a957b-141">별칭 개체를 파이프로 파이프 하 여 **제거할** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-141">You can pipe an alias object to **Remove-Alias**.</span></span>

## <span data-ttu-id="a957b-142">출력</span><span class="sxs-lookup"><span data-stu-id="a957b-142">OUTPUTS</span></span>

### <span data-ttu-id="a957b-143">없음</span><span class="sxs-lookup"><span data-stu-id="a957b-143">None</span></span>

<span data-ttu-id="a957b-144">이 cmdlet은 출력을 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-144">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="a957b-145">참고</span><span class="sxs-lookup"><span data-stu-id="a957b-145">NOTES</span></span>

<span data-ttu-id="a957b-146">변경 내용은 현재 범위에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-146">Changes only affect the current scope.</span></span> <span data-ttu-id="a957b-147">모든 세션에서 별칭을 제거 하려면 PowerShell 프로필에 **제거 별칭** 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a957b-147">To remove an alias from all sessions, add a **Remove-Alias** command to your PowerShell profile.</span></span>

<span data-ttu-id="a957b-148">자세한 내용은 [about_Aliases](../microsoft.powershell.core/about/about_aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a957b-148">For more information, see [about_Aliases](../microsoft.powershell.core/about/about_aliases.md).</span></span>

## <span data-ttu-id="a957b-149">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a957b-149">RELATED LINKS</span></span>

[<span data-ttu-id="a957b-150">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="a957b-150">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="a957b-151">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="a957b-151">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="a957b-152">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="a957b-152">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="a957b-153">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="a957b-153">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="a957b-154">New-Alias</span><span class="sxs-lookup"><span data-stu-id="a957b-154">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="a957b-155">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="a957b-155">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="a957b-156">Where-Object</span><span class="sxs-lookup"><span data-stu-id="a957b-156">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)


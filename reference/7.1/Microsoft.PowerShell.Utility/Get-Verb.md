---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/07/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-verb?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 27434dfbc76d26724b34fe19fd143a7c52a14e90
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/11/2020
ms.locfileid: "93219521"
---
# <span data-ttu-id="f4408-103">Get-Verb</span><span class="sxs-lookup"><span data-stu-id="f4408-103">Get-Verb</span></span>

## <span data-ttu-id="f4408-104">개요</span><span class="sxs-lookup"><span data-stu-id="f4408-104">SYNOPSIS</span></span>
<span data-ttu-id="f4408-105">승인 된 PowerShell 동사를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-105">Gets approved PowerShell verbs.</span></span>

## <span data-ttu-id="f4408-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f4408-106">SYNTAX</span></span>

```
Get-Verb [[-Verb] <String[]>] [[-Group] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="f4408-107">설명</span><span class="sxs-lookup"><span data-stu-id="f4408-107">DESCRIPTION</span></span>

<span data-ttu-id="f4408-108">`Get-Verb`함수는 PowerShell 명령에서 사용 하도록 승인 된 동사를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-108">The `Get-Verb` function gets verbs that are approved for use in PowerShell commands.</span></span>

<span data-ttu-id="f4408-109">PowerShell cmdlet 및 함수 이름은 형식이 며 승인 된 동사를 포함 하는 것이 좋습니다 `Verb-Noun` .</span><span class="sxs-lookup"><span data-stu-id="f4408-109">It is recommended that PowerShell cmdlet and function names have the `Verb-Noun` format and include an approved verb.</span></span> <span data-ttu-id="f4408-110">이 방법을 사용 하면 명령 이름을 보다 일관 되 고 예측 가능 하며 더 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-110">This practice makes command names more consistent, predictable, and easier to use.</span></span>

<span data-ttu-id="f4408-111">승인 되지 않은 동사를 사용 하는 명령이 PowerShell에서 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-111">Commands that use unapproved verbs, still run in PowerShell.</span></span> <span data-ttu-id="f4408-112">그러나 이름에 승인 되지 않은 동사가 포함 된 명령이 있는 모듈을 가져올 경우이 `Import-Module` 명령은 경고 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-112">However, when you import a module that includes a command with an unapproved verb in its name, the `Import-Module` command displays a warning message.</span></span>

> [!NOTE]
> <span data-ttu-id="f4408-113">에서 반환 하는 동사 목록이 `Get-Verb` 불완전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-113">The verb list that `Get-Verb` returns might not be complete.</span></span> <span data-ttu-id="f4408-114">설명으로 승인 된 PowerShell 동사의 업데이트 된 목록은 Microsoft Docs에서 [승인 된 동사](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f4408-114">For an updated list of approved PowerShell verbs with descriptions, see [Approved Verbs](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in the Microsoft Docs.</span></span>

## <span data-ttu-id="f4408-115">예</span><span class="sxs-lookup"><span data-stu-id="f4408-115">Examples</span></span>

### <span data-ttu-id="f4408-116">예 1-모든 동사의 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="f4408-116">Example 1 - Get a list of all verbs</span></span>

```powershell
Get-Verb
```

### <span data-ttu-id="f4408-117">예 2-"un"으로 시작 하는 승인 된 동사 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="f4408-117">Example 2 - Get a list of approved verbs that begin with "un"</span></span>

```powershell
Get-Verb un*
```

```Output
Verb       AliasPrefix Group     Description
----       ----------- -----     -----------
Undo       un          Common    Sets a resource to its previous state
Unlock     uk          Common    Releases a resource that was locked
Unpublish  ub          Data      Makes a resource unavailable to others
Uninstall  us          Lifecycle Removes a resource from an indicated location
Unregister ur          Lifecycle Removes the entry for a resource from a repository
Unblock    ul          Security  Removes restrictions to a resource
Unprotect  up          Security  Removes safeguards from a resource that were added to prevent it from attack or loss
```

### <span data-ttu-id="f4408-118">예 3-보안 그룹에서 승인 된 모든 동사 가져오기</span><span class="sxs-lookup"><span data-stu-id="f4408-118">Example 3 - Get all approved verbs in the Security group</span></span>

```powershell
Get-Verb -Group Security
```

```Output
Verb      AliasPrefix Group    Description
----      ----------- -----    -----------
Block     bl          Security Restricts access to a resource
Grant     gr          Security Allows access to a resource
Protect   pt          Security Safeguards a resource from attack or loss
Revoke    rk          Security Specifies an action that does not allow access to a resource
Unblock   ul          Security Removes restrictions to a resource
Unprotect up          Security Removes safeguards from a resource that were added to prevent it from attack or loss
```

### <span data-ttu-id="f4408-119">예제 4-승인 되지 않은 동사가 있는 모듈의 모든 명령을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-119">Example 4 - Finds all commands in a module that have unapproved verbs</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## <span data-ttu-id="f4408-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f4408-120">PARAMETERS</span></span>

### <span data-ttu-id="f4408-121">-동사</span><span class="sxs-lookup"><span data-stu-id="f4408-121">-Verb</span></span>

<span data-ttu-id="f4408-122">지정된 동사만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-122">Gets only the specified verbs.</span></span> <span data-ttu-id="f4408-123">동사의 이름 또는 이름 패턴을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="f4408-123">Enter the name of a verb or a name pattern.</span></span> <span data-ttu-id="f4408-124">와일드카드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-124">Wildcards are allowed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Common, Communications, Data, Diagnostic, Lifecycle, Other, Security

Required: False
Position: 1
Default value: All groups
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="f4408-125">-그룹</span><span class="sxs-lookup"><span data-stu-id="f4408-125">-Group</span></span>

<span data-ttu-id="f4408-126">지정 된 그룹만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-126">Gets only the specified groups.</span></span> <span data-ttu-id="f4408-127">그룹의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-127">Enter the name of a group.</span></span> <span data-ttu-id="f4408-128">와일드 카드는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-128">Wildcards are not allowed.</span></span>

<span data-ttu-id="f4408-129">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-129">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All verbs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f4408-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f4408-130">CommonParameters</span></span>

<span data-ttu-id="f4408-131">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f4408-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f4408-132">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4408-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f4408-133">입력</span><span class="sxs-lookup"><span data-stu-id="f4408-133">INPUTS</span></span>

### <span data-ttu-id="f4408-134">없음</span><span class="sxs-lookup"><span data-stu-id="f4408-134">None</span></span>

## <span data-ttu-id="f4408-135">출력</span><span class="sxs-lookup"><span data-stu-id="f4408-135">OUTPUTS</span></span>

### <span data-ttu-id="f4408-136">VerbInfo.</span><span class="sxs-lookup"><span data-stu-id="f4408-136">System.Management.Automation.VerbInfo</span></span>

## <span data-ttu-id="f4408-137">참고</span><span class="sxs-lookup"><span data-stu-id="f4408-137">NOTES</span></span>

<span data-ttu-id="f4408-138">PowerShell 동사는 가장 일반적인 용도에 따라 그룹에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-138">PowerShell verbs are assigned to a group based on their most common use.</span></span> <span data-ttu-id="f4408-139">그룹은 동사의 용도를 제한하지 않으면서 쉽게 찾고 비교할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-139">The groups are designed to make the verbs easy to find and compare, not to restrict their use.</span></span> <span data-ttu-id="f4408-140">모든 유형의 명령에 대해 승인된 모든 동사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-140">You can use any approved verb for any type of command.</span></span>

<span data-ttu-id="f4408-141">각 PowerShell 동사는 다음 그룹 중 하나에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-141">Each PowerShell verb is assigned to one of the following groups.</span></span>

- <span data-ttu-id="f4408-142">Common: 추가와 같은 거의 모든 cmdlet에 적용할 수 있는 일반 동작을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-142">Common: Define generic actions that can apply to almost any cmdlet, such as Add.</span></span>
- <span data-ttu-id="f4408-143">통신: Connect와 같은 통신에 적용 되는 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-143">Communications: Define actions that apply to communications, such as Connect.</span></span>
- <span data-ttu-id="f4408-144">데이터: 백업 등의 데이터 처리에 적용 되는 동작을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-144">Data: Define actions that apply to data handling, such as Backup.</span></span>
- <span data-ttu-id="f4408-145">진단: 디버그와 같은 진단에 적용 되는 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-145">Diagnostic: Define actions that apply to diagnostics, such as Debug.</span></span>
- <span data-ttu-id="f4408-146">수명 주기: cmdlet의 수명 주기 (예: Complete)에 적용 되는 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-146">Lifecycle: Define actions that apply to the lifecycle of a cmdlet, such as Complete.</span></span>
- <span data-ttu-id="f4408-147">보안: Revoke와 같은 보안에 적용 되는 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-147">Security: Define actions that apply to security, such as Revoke.</span></span>
- <span data-ttu-id="f4408-148">기타: 다른 유형의 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-148">Other: Define other types of actions.</span></span>

<span data-ttu-id="f4408-149">PowerShell과 함께 설치 되는 일부 cmdlet (예: 및)은 승인 되지 않은 `Tee-Object` `Where-Object` 동사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-149">Some of the cmdlets that are installed with PowerShell, such as `Tee-Object` and `Where-Object`, use unapproved verbs.</span></span> <span data-ttu-id="f4408-150">이러한 cmdlet은 기록 예외 이며 해당 동사는 **예약** 된 것으로 분류 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4408-150">These cmdlets are historic exceptions and their verbs are classified as **reserved**.</span></span>

## <span data-ttu-id="f4408-151">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f4408-151">RELATED LINKS</span></span>

[<span data-ttu-id="f4408-152">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="f4408-152">Import-Module</span></span>](../microsoft.powershell.core/import-module.md)


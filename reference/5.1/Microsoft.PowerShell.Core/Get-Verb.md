---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/07/2018
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/functions/get-verb?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 4474bb50c2bf3be10e72d2554190208e956f9040
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/11/2020
ms.locfileid: "93219497"
---
# <span data-ttu-id="39597-103">Get-Verb</span><span class="sxs-lookup"><span data-stu-id="39597-103">Get-Verb</span></span>

## <span data-ttu-id="39597-104">개요</span><span class="sxs-lookup"><span data-stu-id="39597-104">SYNOPSIS</span></span>
<span data-ttu-id="39597-105">승인 된 PowerShell 동사를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="39597-105">Gets approved PowerShell verbs.</span></span>

## <span data-ttu-id="39597-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="39597-106">SYNTAX</span></span>

```
Get-Verb [[-verb] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="39597-107">설명</span><span class="sxs-lookup"><span data-stu-id="39597-107">DESCRIPTION</span></span>

<span data-ttu-id="39597-108">`Get-Verb`함수는 PowerShell 명령에서 사용 하도록 승인 된 동사를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="39597-108">The `Get-Verb` function gets verbs that are approved for use in PowerShell commands.</span></span>

<span data-ttu-id="39597-109">PowerShell에서는 cmdlet 및 함수 이름에 Verb-Noun 형식을 지정 하 고 승인 된 동사를 포함 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="39597-109">PowerShell recommends cmdlet and function names have the Verb-Noun format and include an approved verb.</span></span> <span data-ttu-id="39597-110">이 방법을 사용 하면 명령 이름을 보다 일관 되 고 예측 가능 하며 더 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39597-110">This practice makes command names more consistent, predictable, and easier to use.</span></span>

<span data-ttu-id="39597-111">승인 되지 않은 동사를 사용 하는 명령은 PowerShell에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39597-111">Commands that use unapproved verbs run in PowerShell.</span></span> <span data-ttu-id="39597-112">그러나 이름에 승인 되지 않은 동사가 포함 된 명령이 있는 모듈을 가져올 경우이 `Import-Module` 명령은 경고 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="39597-112">However, when you import a module that includes a command with an unapproved verb in its name, the `Import-Module` command displays a warning message.</span></span>

> [!NOTE]
> <span data-ttu-id="39597-113">에서 반환 하는 동사 목록이 `Get-Verb` 불완전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39597-113">The verb list that `Get-Verb` returns might not be complete.</span></span> <span data-ttu-id="39597-114">설명으로 승인 된 PowerShell 동사의 업데이트 된 목록은 Microsoft Docs에서 [승인 된 동사](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="39597-114">For an updated list of approved PowerShell verbs with descriptions, see [Approved Verbs](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in the Microsoft Docs.</span></span>

## <span data-ttu-id="39597-115">예제</span><span class="sxs-lookup"><span data-stu-id="39597-115">EXAMPLES</span></span>

### <span data-ttu-id="39597-116">예 1-모든 동사의 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="39597-116">Example 1 - Get a list of all verbs</span></span>

```powershell
Get-Verb
```

### <span data-ttu-id="39597-117">예 2-"un"으로 시작 하는 승인 된 동사 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="39597-117">Example 2 - Get a list of approved verbs that begin with "un"</span></span>

```powershell
Get-Verb un*
```

```Output
Verb                 Group
----                 -----
Undo                 Common
Unlock               Common
Unpublish            Data
Uninstall            Lifecycle
Unregister           Lifecycle
Unblock              Security
Unprotect            Security
```

### <span data-ttu-id="39597-118">예 3-보안 그룹에서 승인 된 모든 동사 가져오기</span><span class="sxs-lookup"><span data-stu-id="39597-118">Example 3 - Get all approved verbs in the Security group</span></span>

```powershell
Get-Verb | Where-Object Group -EQ Security
```

```Output
Verb      Group
----      -----
Block     Security
Grant     Security
Protect   Security
Revoke    Security
Unblock   Security
Unprotect Security
```

### <span data-ttu-id="39597-119">예제 4-승인 되지 않은 동사가 있는 모듈의 모든 명령을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="39597-119">Example 4 - Finds all commands in a module that have unapproved verbs</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## <span data-ttu-id="39597-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="39597-120">PARAMETERS</span></span>

### <span data-ttu-id="39597-121">-동사</span><span class="sxs-lookup"><span data-stu-id="39597-121">-verb</span></span>

<span data-ttu-id="39597-122">지정된 동사만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="39597-122">Gets only the specified verbs.</span></span>
<span data-ttu-id="39597-123">동사의 이름 또는 이름 패턴을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="39597-123">Enter the name of a verb or a name pattern.</span></span>
<span data-ttu-id="39597-124">와일드카드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39597-124">Wildcards are allowed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: All verbs
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

## <span data-ttu-id="39597-125">입력</span><span class="sxs-lookup"><span data-stu-id="39597-125">INPUTS</span></span>

### <span data-ttu-id="39597-126">없음</span><span class="sxs-lookup"><span data-stu-id="39597-126">None</span></span>

## <span data-ttu-id="39597-127">출력</span><span class="sxs-lookup"><span data-stu-id="39597-127">OUTPUTS</span></span>

### <span data-ttu-id="39597-128">Selected.Microsoft.PowerShell.Commands.MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="39597-128">Selected.Microsoft.PowerShell.Commands.MemberDefinition</span></span>

## <span data-ttu-id="39597-129">참고</span><span class="sxs-lookup"><span data-stu-id="39597-129">NOTES</span></span>

<span data-ttu-id="39597-130">`Get-Verb` Microsoft. PowerShell. MemberDefinition 개체의 수정 된 버전을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="39597-130">`Get-Verb` returns a modified version of a Microsoft.PowerShell.Commands.MemberDefinition object.</span></span>
<span data-ttu-id="39597-131">이 개체에 MemberDefinition 개체의 표준 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="39597-131">The object does not have the standard properties of a MemberDefinition object.</span></span> <span data-ttu-id="39597-132">대신 이 개체는 Verb 및 Group 속성을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="39597-132">Instead it has Verb and Group properties.</span></span> <span data-ttu-id="39597-133">Verb 속성에는 동사 이름의 문자열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="39597-133">The Verb property contains a string with the verb name.</span></span> <span data-ttu-id="39597-134">Group 속성에는 동사 그룹의 문자열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="39597-134">The Group property contains a string with the verb group.</span></span>

<span data-ttu-id="39597-135">PowerShell 동사는 가장 일반적인 용도에 따라 그룹에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39597-135">PowerShell verbs are assigned to a group based on their most common use.</span></span> <span data-ttu-id="39597-136">그룹은 동사의 용도를 제한하지 않으면서 쉽게 찾고 비교할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="39597-136">The groups are designed to make the verbs easy to find and compare, not to restrict their use.</span></span> <span data-ttu-id="39597-137">모든 유형의 명령에 대해 승인된 모든 동사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39597-137">You can use any approved verb for any type of command.</span></span>

<span data-ttu-id="39597-138">각 PowerShell 동사는 다음 그룹 중 하나에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39597-138">Each PowerShell verb is assigned to one of the following groups.</span></span>

- <span data-ttu-id="39597-139">Common: 추가와 같은 거의 모든 cmdlet에 적용할 수 있는 일반 동작을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="39597-139">Common: Define generic actions that can apply to almost any cmdlet, such as Add.</span></span>
- <span data-ttu-id="39597-140">통신: Connect와 같은 통신에 적용 되는 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="39597-140">Communications:  Define actions that apply to communications, such as Connect.</span></span>
- <span data-ttu-id="39597-141">데이터: 백업 등의 데이터 처리에 적용 되는 동작을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="39597-141">Data:  Define actions that apply to data handling, such as Backup.</span></span>
- <span data-ttu-id="39597-142">진단: 디버그와 같은 진단에 적용 되는 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="39597-142">Diagnostic: Define actions that apply to diagnostics, such as Debug.</span></span>
- <span data-ttu-id="39597-143">수명 주기: cmdlet의 수명 주기 (예: Complete)에 적용 되는 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="39597-143">Lifecycle: Define actions that apply to the lifecycle of a cmdlet, such as Complete.</span></span>
- <span data-ttu-id="39597-144">보안: Revoke와 같은 보안에 적용 되는 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="39597-144">Security: Define actions that apply to security, such as Revoke.</span></span>
- <span data-ttu-id="39597-145">기타: 다른 유형의 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="39597-145">Other: Define other types of actions.</span></span>

<span data-ttu-id="39597-146">PowerShell과 함께 설치 되는 일부 cmdlet (예: 및)은 승인 되지 않은 `Tee-Object` `Where-Object` 동사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="39597-146">Some of the cmdlets that are installed with PowerShell, such as `Tee-Object` and `Where-Object`, use unapproved verbs.</span></span> <span data-ttu-id="39597-147">이러한 cmdlet은 기록 예외 이며 해당 동사는 **예약** 된 것으로 분류 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39597-147">These cmdlets are historic exceptions and their verbs are classified as **reserved**.</span></span>

## <span data-ttu-id="39597-148">관련 링크</span><span class="sxs-lookup"><span data-stu-id="39597-148">RELATED LINKS</span></span>

[<span data-ttu-id="39597-149">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="39597-149">Import-Module</span></span>](import-module.md)

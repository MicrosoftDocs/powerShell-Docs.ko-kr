---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: 7fb4341a84706f7d31d463bb527a1a31f387c2ae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605006"
---
# <span data-ttu-id="6bcc9-102">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="6bcc9-102">Invoke-History</span></span>

## <span data-ttu-id="6bcc9-103">개요</span><span class="sxs-lookup"><span data-stu-id="6bcc9-103">SYNOPSIS</span></span>
<span data-ttu-id="6bcc9-104">세션 기록에서 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-104">Runs commands from the session history.</span></span>

## <span data-ttu-id="6bcc9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6bcc9-105">SYNTAX</span></span>

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6bcc9-106">설명</span><span class="sxs-lookup"><span data-stu-id="6bcc9-106">DESCRIPTION</span></span>

<span data-ttu-id="6bcc9-107">`Invoke-History`Cmdlet은 세션 기록에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-107">The `Invoke-History` cmdlet runs commands from the session history.</span></span> <span data-ttu-id="6bcc9-108">Get-History에서 명령을 나타내는 개체를 전달 `Invoke-History` 하거나 해당 **Id** 번호를 사용 하 여 현재 기록의 명령을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-108">You can pass objects representing the commands from Get-History to `Invoke-History`, or you can identify commands in the current history by using their **Id** number.</span></span> <span data-ttu-id="6bcc9-109">명령의 id 번호를 확인 하려면 cmdlet을 사용 합니다 `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="6bcc9-109">To find the identification number of a command, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="6bcc9-110">세션 기록은 **Psreadline** 모듈에 의해 유지 관리 되는 기록과 별도로 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-110">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="6bcc9-111">**Psreadline** 이 로드 된 세션에서 두 기록을 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-111">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="6bcc9-112">이 cmdlet은 세션 기록 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-112">This cmdlet only works with the session history.</span></span> <span data-ttu-id="6bcc9-113">자세한 내용은 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-113">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="6bcc9-114">예제</span><span class="sxs-lookup"><span data-stu-id="6bcc9-114">EXAMPLES</span></span>

### <span data-ttu-id="6bcc9-115">예제 1: 기록에서 최신 명령 실행</span><span class="sxs-lookup"><span data-stu-id="6bcc9-115">Example 1: Run the most recent command in the history</span></span>

<span data-ttu-id="6bcc9-116">이 예에서는 세션 기록에서 마지막 또는 가장 최근 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-116">This example runs the last, or most recent, command in the session history.</span></span> <span data-ttu-id="6bcc9-117">이 명령을 `r` 에 대 한 별칭으로 약어로 사용할 수 있습니다 `Invoke-History` .</span><span class="sxs-lookup"><span data-stu-id="6bcc9-117">You can abbreviate this command as `r`, the alias for `Invoke-History`.</span></span>

```powershell
Invoke-History
```

### <span data-ttu-id="6bcc9-118">예 2: 지정 된 ID를 가진 명령 실행</span><span class="sxs-lookup"><span data-stu-id="6bcc9-118">Example 2: Run the command that has a specified ID</span></span>

<span data-ttu-id="6bcc9-119">이 예제에서는 **Id가** 132 인 세션 기록에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-119">This example runs the command in the session history with **Id** 132.</span></span> <span data-ttu-id="6bcc9-120">**Id** 매개 변수의 이름은 선택 사항 이므로이 명령의 약어는, 또는로 지정할 수 있습니다 `Invoke-History 132` `ihy 132` `r 132` .</span><span class="sxs-lookup"><span data-stu-id="6bcc9-120">Because the name of the **Id** parameter is optional, you can abbreviate this command as the following: `Invoke-History 132`, `ihy 132`, or `r 132`.</span></span>

```powershell
Invoke-History -Id 132
```

### <span data-ttu-id="6bcc9-121">예제 3: 명령 텍스트를 사용 하 여 가장 최근 명령 실행</span><span class="sxs-lookup"><span data-stu-id="6bcc9-121">Example 3: Run the most recent command by using the command text</span></span>

<span data-ttu-id="6bcc9-122">이 예에서는 `Get-Process` 세션 기록에서 가장 최근의 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-122">This example runs the most recent `Get-Process` command in the session history.</span></span> <span data-ttu-id="6bcc9-123">**Id** 매개 변수에 대 한 문자를 입력 하는 경우 `Invoke-History` 가장 최근 명령부터 시작 하 여 패턴에 일치 하는 첫 번째 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-123">When you type characters for the **Id** parameter, `Invoke-History` runs the first command that it finds that matches the pattern, starting with the most recent commands.</span></span>

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> <span data-ttu-id="6bcc9-124">패턴 일치는 대/소문자를 구분 하지 않지만 패턴은 줄의 시작 부분을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-124">Pattern matching is case-insensitive, but the pattern matches the beginning of the line.</span></span>

### <span data-ttu-id="6bcc9-125">예제 4: 기록에서 일련의 명령 실행</span><span class="sxs-lookup"><span data-stu-id="6bcc9-125">Example 4: Run a sequence of commands from the history</span></span>

<span data-ttu-id="6bcc9-126">이 예제에서는 16-24 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-126">This example runs commands 16 through 24.</span></span> <span data-ttu-id="6bcc9-127">하나의 **id** 값만 나열할 수 있으므로 명령은 cmdlet을 사용 하 여 `ForEach-Object` `Invoke-History` 각 **id** 값에 대해 명령을 한 번 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-127">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command one time for each **Id** value.</span></span>

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### <span data-ttu-id="6bcc9-128">예제 5</span><span class="sxs-lookup"><span data-stu-id="6bcc9-128">Example 5</span></span>

<span data-ttu-id="6bcc9-129">이 예제에서는 기록에서 명령 255 (249 ~ 255)로 끝나는 명령 7 개를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-129">This example runs the seven commands in the history that end with command 255 (249 through 255).</span></span> <span data-ttu-id="6bcc9-130">Cmdlet을 사용 하 여 `Get-History` 명령을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-130">It uses the `Get-History` cmdlet to retrieve the commands.</span></span> <span data-ttu-id="6bcc9-131">하나의 **id** 값만 나열할 수 있으므로 명령은 cmdlet을 사용 하 여 `ForEach-Object` `Invoke-History` 각 **id** 값에 대해 명령을 한 번 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-131">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command once for each **Id** value.</span></span>

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## <span data-ttu-id="6bcc9-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6bcc9-132">PARAMETERS</span></span>

### <span data-ttu-id="6bcc9-133">-Id</span><span class="sxs-lookup"><span data-stu-id="6bcc9-133">-Id</span></span>

<span data-ttu-id="6bcc9-134">기록의 명령 **Id** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-134">Specifies the **Id** of a command in the history.</span></span> <span data-ttu-id="6bcc9-135">명령의 **Id** 번호 또는 명령의 처음 몇 문자를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-135">You can type the **Id** number of the command or the first few characters of the command.</span></span>

<span data-ttu-id="6bcc9-136">문자를 입력 하 `Invoke-History` 는 경우 가장 최근 명령과 가장 먼저 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-136">If you type characters, `Invoke-History` matches the most recent commands first.</span></span> <span data-ttu-id="6bcc9-137">이 매개 변수를 생략 하면는 `Invoke-History` 마지막 또는 가장 최근 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-137">If you omit this parameter, `Invoke-History` runs the last, or most recent, command.</span></span> <span data-ttu-id="6bcc9-138">명령의 **Id** 번호를 찾으려면 cmdlet을 사용 합니다 `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="6bcc9-138">To find the **Id** number of a command, use the `Get-History` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6bcc9-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6bcc9-139">-Confirm</span></span>

<span data-ttu-id="6bcc9-140">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6bcc9-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6bcc9-141">-WhatIf</span></span>

<span data-ttu-id="6bcc9-142">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6bcc9-143">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6bcc9-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6bcc9-144">CommonParameters</span></span>

<span data-ttu-id="6bcc9-145">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6bcc9-146">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6bcc9-147">입력</span><span class="sxs-lookup"><span data-stu-id="6bcc9-147">INPUTS</span></span>

### <span data-ttu-id="6bcc9-148">System.String</span><span class="sxs-lookup"><span data-stu-id="6bcc9-148">System.String</span></span>

<span data-ttu-id="6bcc9-149">기록 **Id** 를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-149">You can pipe a history **Id** to this cmdlet.</span></span>

## <span data-ttu-id="6bcc9-150">출력</span><span class="sxs-lookup"><span data-stu-id="6bcc9-150">OUTPUTS</span></span>

### <span data-ttu-id="6bcc9-151">없음</span><span class="sxs-lookup"><span data-stu-id="6bcc9-151">None</span></span>

<span data-ttu-id="6bcc9-152">이 cmdlet은 출력을 생성 하지 않지만를 실행 하는 명령에 의해 출력이 생성 될 수 있습니다 `Invoke-History` .</span><span class="sxs-lookup"><span data-stu-id="6bcc9-152">This cmdlet does not generate any output, but output might be generated by the commands that `Invoke-History` runs.</span></span>

## <span data-ttu-id="6bcc9-153">참고</span><span class="sxs-lookup"><span data-stu-id="6bcc9-153">NOTES</span></span>

<span data-ttu-id="6bcc9-154">세션 기록은 세션 중에 입력된 명령 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-154">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="6bcc9-155">세션 기록은 명령의 실행 순서, 상태, 시작 시간 및 종료 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-155">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="6bcc9-156">각 명령을 입력 하면 PowerShell에서 해당 명령을 다시 사용할 수 있도록 기록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-156">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="6bcc9-157">세션 기록에 대 한 자세한 내용은 [about_History](About/about_History.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-157">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="6bcc9-158">`Invoke-History`기본 제공 별칭인 및를 참조할 수도 있습니다 `r` `ihy` .</span><span class="sxs-lookup"><span data-stu-id="6bcc9-158">You can also refer to `Invoke-History` by its built-in aliases, `r` and `ihy`.</span></span> <span data-ttu-id="6bcc9-159">자세한 내용은 [about_Aliases](About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6bcc9-159">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="6bcc9-160">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6bcc9-160">RELATED LINKS</span></span>

[<span data-ttu-id="6bcc9-161">Add-History</span><span class="sxs-lookup"><span data-stu-id="6bcc9-161">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="6bcc9-162">Clear-History</span><span class="sxs-lookup"><span data-stu-id="6bcc9-162">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="6bcc9-163">Get-History</span><span class="sxs-lookup"><span data-stu-id="6bcc9-163">Get-History</span></span>](Get-History.md)

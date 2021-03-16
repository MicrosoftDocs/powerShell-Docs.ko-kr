---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-History
ms.openlocfilehash: be47925211c57760ddbd0bd4c8e985e161d24593
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601049"
---
# <span data-ttu-id="12e0d-102">Get-History</span><span class="sxs-lookup"><span data-stu-id="12e0d-102">Get-History</span></span>

## <span data-ttu-id="12e0d-103">개요</span><span class="sxs-lookup"><span data-stu-id="12e0d-103">SYNOPSIS</span></span>
<span data-ttu-id="12e0d-104">현재 세션 중에 입력된 명령 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-104">Gets a list of the commands entered during the current session.</span></span>

## <span data-ttu-id="12e0d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="12e0d-105">SYNTAX</span></span>

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="12e0d-106">설명</span><span class="sxs-lookup"><span data-stu-id="12e0d-106">DESCRIPTION</span></span>

<span data-ttu-id="12e0d-107">`Get-History`Cmdlet은 세션 기록, 즉 현재 세션 중에 입력 된 명령 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-107">The `Get-History` cmdlet gets the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="12e0d-108">PowerShell은 각 세션의 기록을 자동으로 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-108">PowerShell automatically maintains a history of each session.</span></span> <span data-ttu-id="12e0d-109">세션 기록의 항목 수는 기본 설정 변수의 값에 따라 결정 됩니다 `$MaximumHistoryCount` .</span><span class="sxs-lookup"><span data-stu-id="12e0d-109">The number of entries in the session history is determined by the value of the `$MaximumHistoryCount` preference variable.</span></span> <span data-ttu-id="12e0d-110">Windows PowerShell 3.0부터 기본값은 `4096` 입니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-110">Beginning in Windows PowerShell 3.0, the default value is `4096`.</span></span> <span data-ttu-id="12e0d-111">기본적으로 기록 파일은 홈 디렉터리에 저장되지만 원하는 위치에 파일을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-111">By default, history files are saved in the home directory, but you can save the file in any location.</span></span> <span data-ttu-id="12e0d-112">PowerShell의 기록 기능에 대 한 자세한 내용은 [about_History](About/about_History.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="12e0d-112">For more information about the history features in PowerShell, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="12e0d-113">세션 기록은 **Psreadline** 모듈에 의해 유지 관리 되는 기록과 별도로 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-113">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="12e0d-114">**Psreadline** 이 로드 된 세션에서 두 기록을 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-114">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="12e0d-115">이 cmdlet은 세션 기록 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-115">This cmdlet only works with the session history.</span></span> <span data-ttu-id="12e0d-116">자세한 내용은 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="12e0d-116">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="12e0d-117">예제</span><span class="sxs-lookup"><span data-stu-id="12e0d-117">EXAMPLES</span></span>

### <span data-ttu-id="12e0d-118">예제 1: 세션 기록 가져오기</span><span class="sxs-lookup"><span data-stu-id="12e0d-118">Example 1: Get the session history</span></span>

<span data-ttu-id="12e0d-119">이 예제에서는 세션 기록의 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-119">This example gets the entries in the session history.</span></span> <span data-ttu-id="12e0d-120">기본 표시에는 각 명령과 각 명령이 실행 된 순서를 나타내는 해당 ID가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-120">The default display shows each command and its ID, which indicates the order in which they ran.</span></span>

```powershell
Get-History
```

### <span data-ttu-id="12e0d-121">예제 2: 문자열을 포함 하는 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="12e0d-121">Example 2: Get entries that include a string</span></span>

<span data-ttu-id="12e0d-122">이 예제에서는 문자열 서비스를 포함 하는 명령 기록의 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-122">This example gets entries in the command history that include the string service.</span></span> <span data-ttu-id="12e0d-123">첫 번째 명령은 세션 기록의 모든 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-123">The first command gets all entries in the session history.</span></span> <span data-ttu-id="12e0d-124">파이프라인 연산자 ( `|` )는 결과를 cmdlet으로 전달 합니다 `Where-Object` .이 cmdlet은 서비스를 포함 하는 명령만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-124">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects only the commands that include service.</span></span>

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### <span data-ttu-id="12e0d-125">예 3: 특정 ID까지 기록 항목 내보내기</span><span class="sxs-lookup"><span data-stu-id="12e0d-125">Example 3: Export history entries up to a specific ID</span></span>

<span data-ttu-id="12e0d-126">이 예제에서는 항목 7로 끝나는 5 개의 최근 기록 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-126">This example gets the five most recent history entries ending with entry 7.</span></span> <span data-ttu-id="12e0d-127">파이프라인 연산자는 결과를 cmdlet으로 전달 합니다 `Export-Csv` .이 cmdlet은 기록을 쉼표로 구분 된 텍스트로 포맷 하 고 History.csv 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-127">The pipeline operator passes the result to the `Export-Csv` cmdlet, which formats the history as comma-separated text and saves it in the History.csv file.</span></span> <span data-ttu-id="12e0d-128">이 파일에는 기록의 형식을 목록으로 지정할 때 표시 되는 데이터가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-128">The file includes the data that is displayed when you format the history as a list.</span></span> <span data-ttu-id="12e0d-129">여기에는 명령의 상태와 시작 및 종료 시간이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-129">This includes the status and start and end times of the command.</span></span>

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### <span data-ttu-id="12e0d-130">예제 4: 최신 명령 표시</span><span class="sxs-lookup"><span data-stu-id="12e0d-130">Example 4: Display the most recent command</span></span>

<span data-ttu-id="12e0d-131">이 예제에서는 명령 기록의 마지막 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-131">This example gets the last command in the command history.</span></span> <span data-ttu-id="12e0d-132">마지막 명령은 가장 최근에 입력 한 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-132">The last command is the most recently entered command.</span></span> <span data-ttu-id="12e0d-133">이 명령은 **Count** 매개 변수를 사용 하 여 하나의 명령만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-133">This command uses the **Count** parameter to display just one command.</span></span> <span data-ttu-id="12e0d-134">기본적으로 `Get-History` 가장 최근 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-134">By default, `Get-History` gets the most recent commands.</span></span> <span data-ttu-id="12e0d-135">이 명령은 "h -c 1"로 간략하게 표시할 수 있으며 위쪽 화살표 키를 누르는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-135">This command can be abbreviated to "h -c 1" and is equivalent to pressing the up-arrow key.</span></span>

```powershell
Get-History -Count 1
```

### <span data-ttu-id="12e0d-136">예 5: 기록에 있는 항목의 모든 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-136">Example 5: Display all the properties of the entries in the history</span></span>

<span data-ttu-id="12e0d-137">이 예에서는 세션 기록에 있는 항목의 모든 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-137">This example displays all of the properties of entries in the session history.</span></span> <span data-ttu-id="12e0d-138">파이프라인 연산자는 명령 결과를 `Get-History` cmdlet에 전달 합니다 `Format-List` . 그러면이 cmdlet이 각 기록 항목의 모든 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-138">The pipeline operator passes the results of a `Get-History` command to the `Format-List` cmdlet, which displays all of the properties of each history entry.</span></span> <span data-ttu-id="12e0d-139">여기에는 명령의 ID, 상태 및 시작 시간과 종료 시간이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-139">This includes the ID, status, and start and end times of the command.</span></span>

```powershell
Get-History | Format-List -Property *
```

## <span data-ttu-id="12e0d-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12e0d-140">PARAMETERS</span></span>

### <span data-ttu-id="12e0d-141">-개수</span><span class="sxs-lookup"><span data-stu-id="12e0d-141">-Count</span></span>

<span data-ttu-id="12e0d-142">이 cmdlet이 가져오는 최근 기록 항목의 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-142">Specifies the number of the most recent history entries that this cmdlet gets.</span></span> <span data-ttu-id="12e0d-143">기본적으로 `Get-History` 세션 기록의 모든 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-143">By, default, `Get-History` gets all entries in the session history.</span></span> <span data-ttu-id="12e0d-144">명령에서 **Count** 및 **Id** 매개 변수를 모두 사용하는 경우 표시는 **Id** 매개 변수에 지정된 명령으로 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-144">If you use both the **Count** and **Id** parameters in a command, the display ends with the command that is specified by the **Id** parameter.</span></span>

<span data-ttu-id="12e0d-145">Windows PowerShell 2.0에서는 기본적으로 32의 `Get-History` 가장 최근 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-145">In Windows PowerShell 2.0, by default, `Get-History` gets the 32 most recent entries.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e0d-146">-Id</span><span class="sxs-lookup"><span data-stu-id="12e0d-146">-Id</span></span>

<span data-ttu-id="12e0d-147">세션 기록에 있는 항목의 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-147">Specifies an array of the IDs of entries in the session history.</span></span> <span data-ttu-id="12e0d-148">`Get-History` 지정 된 항목만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-148">`Get-History` gets only specified entries.</span></span> <span data-ttu-id="12e0d-149">명령에서 **id** 및 **Count** 매개 변수를 모두 사용 하는 경우 `Get-History` **id** 매개 변수로 지정 된 항목으로 끝나는 가장 최근 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-149">If you use both the **Id** and **Count** parameters in a command, `Get-History` gets the most recent entries ending with the entry specified by the **Id** parameter.</span></span>

```yaml
Type: System.Int64[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="12e0d-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12e0d-150">CommonParameters</span></span>

<span data-ttu-id="12e0d-151">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="12e0d-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12e0d-152">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12e0d-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12e0d-153">입력</span><span class="sxs-lookup"><span data-stu-id="12e0d-153">INPUTS</span></span>

### <span data-ttu-id="12e0d-154">System.Int64</span><span class="sxs-lookup"><span data-stu-id="12e0d-154">System.Int64</span></span>

<span data-ttu-id="12e0d-155">기록 ID를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-155">You can pipe a history ID to this cmdlet.</span></span>

## <span data-ttu-id="12e0d-156">출력</span><span class="sxs-lookup"><span data-stu-id="12e0d-156">OUTPUTS</span></span>

### <span data-ttu-id="12e0d-157">HistoryInfo.</span><span class="sxs-lookup"><span data-stu-id="12e0d-157">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="12e0d-158">이 cmdlet은 가져온 각 기록 항목에 대 한 기록 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-158">This cmdlet returns a history object for each history item that it gets.</span></span>

## <span data-ttu-id="12e0d-159">참고</span><span class="sxs-lookup"><span data-stu-id="12e0d-159">NOTES</span></span>

<span data-ttu-id="12e0d-160">세션 기록은 세션 중에 입력된 명령 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-160">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="12e0d-161">세션 기록은 명령의 실행 순서, 상태, 시작 시간 및 종료 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-161">The session history represents the run order, the status, and the start and end times of the command.</span></span> <span data-ttu-id="12e0d-162">각 명령을 입력 하면 PowerShell에서 해당 명령을 다시 사용할 수 있도록 기록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-162">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="12e0d-163">명령 기록에 대 한 자세한 내용은 [about_History](About/about_History.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="12e0d-163">For more information about the command history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="12e0d-164">Windows PowerShell 3.0부터 기본 `$MaximumHistoryCount` 설정 변수의 기본값은 `4096` 입니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-164">Starting in Windows PowerShell 3.0, the default value of the `$MaximumHistoryCount` preference variable is `4096`.</span></span> <span data-ttu-id="12e0d-165">Windows PowerShell 2.0에서 기본값은 `64` 입니다.</span><span class="sxs-lookup"><span data-stu-id="12e0d-165">In Windows PowerShell 2.0, the default value is `64`.</span></span> <span data-ttu-id="12e0d-166">변수에 대 한 자세한 내용은 `$MaximumHistoryCount` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="12e0d-166">For more information about the `$MaximumHistoryCount` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="12e0d-167">관련 링크</span><span class="sxs-lookup"><span data-stu-id="12e0d-167">RELATED LINKS</span></span>

[<span data-ttu-id="12e0d-168">Add-History</span><span class="sxs-lookup"><span data-stu-id="12e0d-168">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="12e0d-169">Clear-History</span><span class="sxs-lookup"><span data-stu-id="12e0d-169">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="12e0d-170">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="12e0d-170">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="12e0d-171">about_History</span><span class="sxs-lookup"><span data-stu-id="12e0d-171">about_History</span></span>](About/about_History.md)
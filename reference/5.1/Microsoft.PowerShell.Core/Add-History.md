---
external help file: System.Management.Automation.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-history?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-History
ms.openlocfilehash: 29f1bbab871a91a9bd77c42f99f9e7f11e18b588
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212129"
---
# <span data-ttu-id="c3aa7-103">Add-History</span><span class="sxs-lookup"><span data-stu-id="c3aa7-103">Add-History</span></span>

## <span data-ttu-id="c3aa7-104">개요</span><span class="sxs-lookup"><span data-stu-id="c3aa7-104">SYNOPSIS</span></span>
<span data-ttu-id="c3aa7-105">세션 기록에 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-105">Appends entries to the session history.</span></span>

## <span data-ttu-id="c3aa7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c3aa7-106">SYNTAX</span></span>

```
Add-History [[-InputObject] <PSObject[]>] [-Passthru] [<CommonParameters>]
```

## <span data-ttu-id="c3aa7-107">설명</span><span class="sxs-lookup"><span data-stu-id="c3aa7-107">DESCRIPTION</span></span>

<span data-ttu-id="c3aa7-108">`Add-History`Cmdlet은 세션 기록 끝, 즉 현재 세션 중에 입력 된 명령 목록에 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-108">The `Add-History` cmdlet adds entries to the end of the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="c3aa7-109">세션 기록은 세션 중에 입력된 명령 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-109">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="c3aa7-110">세션 기록은 명령의 실행 순서, 상태, 시작 시간 및 종료 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-110">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="c3aa7-111">각 명령을 입력 하면 PowerShell에서 해당 명령을 다시 사용할 수 있도록 기록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-111">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="c3aa7-112">세션 기록에 대 한 자세한 내용은 [about_History](About/about_History.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-112">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="c3aa7-113">세션 기록은 **Psreadline** 모듈에 의해 유지 관리 되는 기록과 별도로 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-113">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="c3aa7-114">**Psreadline** 이 로드 된 세션에서 두 기록을 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-114">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="c3aa7-115">이 cmdlet은 세션 기록 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-115">This cmdlet only works with the session history.</span></span> <span data-ttu-id="c3aa7-116">자세한 내용은 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-116">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

<span data-ttu-id="c3aa7-117">Cmdlet을 사용 `Get-History` 하 여 명령을 가져오고이를에 전달 하거나, `Add-History` 명령을 CSV 또는 XML 파일로 내보낸 다음, 명령을 가져와 가져온 파일을에 전달할 수 있습니다 `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="c3aa7-117">You can use the `Get-History` cmdlet to get the commands and pass them to `Add-History`, or you can export the commands to a CSV or XML file, then import the commands, and pass the imported file to `Add-History`.</span></span> <span data-ttu-id="c3aa7-118">이 cmdlet을 사용하여 기록에 특정 명령을 추가하거나 두 개 이상의 세션 명령을 포함하는 하나의 기록 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-118">You can use this cmdlet to add specific commands to the history or to create a single history file that includes commands from more than one session.</span></span>

## <span data-ttu-id="c3aa7-119">예제</span><span class="sxs-lookup"><span data-stu-id="c3aa7-119">EXAMPLES</span></span>

### <span data-ttu-id="c3aa7-120">예제 1: 다른 세션의 기록에 명령 추가</span><span class="sxs-lookup"><span data-stu-id="c3aa7-120">Example 1: Add commands to the history of a different session</span></span>

<span data-ttu-id="c3aa7-121">이 예에서는 하나의 PowerShell 세션에서 입력 된 명령을 다른 PowerShell 세션의 기록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-121">This example add the commands typed in one PowerShell session to the history of a different PowerShell session.</span></span>

```powershell
Get-History | Export-Csv c:\testing\history.csv -IncludeTypeInformation
Import-Csv c:\testing\history.csv | Add-History
```

<span data-ttu-id="c3aa7-122">첫 번째 명령은 기록의 명령을 나타내는 개체를 가져와 `History.csv` 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-122">The first command gets objects representing the commands in the history and exports them to the `History.csv` file.</span></span>

<span data-ttu-id="c3aa7-123">두 번째 명령은 다른 세션의 명령줄에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-123">The second command is typed at the command line of a different session.</span></span> <span data-ttu-id="c3aa7-124">Cmdlet을 사용 하 여 `Import-Csv` 파일의 개체를 가져옵니다 `History.csv` .</span><span class="sxs-lookup"><span data-stu-id="c3aa7-124">It uses the `Import-Csv` cmdlet to import the objects in the `History.csv` file.</span></span> <span data-ttu-id="c3aa7-125">파이프라인 연산자 ( `|` )는 개체를 cmdlet으로 전달 합니다 `Add-History` . 그러면이 cmdlet이 파일의 명령을 나타내는 개체를 `History.csv` 현재 세션 기록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-125">The pipeline operator (`|`) passes the objects to the `Add-History` cmdlet, which adds the objects representing the commands in the `History.csv` file to the current session history.</span></span>

### <span data-ttu-id="c3aa7-126">예제 2: 명령 가져오기 및 실행</span><span class="sxs-lookup"><span data-stu-id="c3aa7-126">Example 2: Import and run commands</span></span>

<span data-ttu-id="c3aa7-127">이 예제에서는 파일에서 명령을 가져와 `History.xml` 현재 세션 기록에 추가한 다음 결합 된 기록에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-127">This example imports commands from the `History.xml` file, adds them to the current session history, and then runs the commands in the combined history.</span></span>

```powershell
Import-Clixml c:\temp\history.xml | Add-History -PassThru | ForEach-Object -Process {Invoke-History}
```

<span data-ttu-id="c3aa7-128">첫 번째 명령은 cmdlet을 사용 하 여 `Import-Clixml` 파일로 내보낸 명령 기록을 가져옵니다 `History.xml` .</span><span class="sxs-lookup"><span data-stu-id="c3aa7-128">The first command uses the `Import-Clixml` cmdlet to import a command history that was exported to the `History.xml` file.</span></span> <span data-ttu-id="c3aa7-129">파이프라인 연산자는 명령을 `Add-History` 현재 세션 기록에 추가 하는 cmdlet에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-129">The pipeline operator passes the commands to the `Add-History` cmdlet, which adds the commands to the current session history.</span></span> <span data-ttu-id="c3aa7-130">**PassThru** 매개 변수는 추가 된 명령을 나타내는 개체를 파이프라인으로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-130">The **PassThru** parameter passes the objects representing the added commands down the pipeline.</span></span>

<span data-ttu-id="c3aa7-131">그런 다음이 명령은 cmdlet을 사용 하 여 `ForEach-Object` `Invoke-History` 결합 된 기록의 각 명령에 명령을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-131">The command then uses the `ForEach-Object` cmdlet to apply the `Invoke-History` command to each of the commands in the combined history.</span></span> <span data-ttu-id="c3aa7-132">`Invoke-History`명령은 `{}` Cmdlet의 **Process** 매개 변수에서 요구 하는 대로 중괄호 ()로 묶인 스크립트 블록으로 형식이 지정 됩니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="c3aa7-132">The `Invoke-History` command is formatted as a script block, enclosed in braces (`{}`), as required by the **Process** parameter of the `ForEach-Object` cmdlet.</span></span>

### <span data-ttu-id="c3aa7-133">예제 3: 기록의 끝 부분에 명령 추가</span><span class="sxs-lookup"><span data-stu-id="c3aa7-133">Example 3: Add commands in the history to the end of the history</span></span>

<span data-ttu-id="c3aa7-134">이 예에서는 기록의 처음 5 개 명령을 기록 목록의 끝에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-134">This example adds the first five commands in the history to the end of the history list.</span></span>

```powershell
Get-History -Id 5 -Count 5 | Add-History
```

<span data-ttu-id="c3aa7-135">`Get-History`Cmdlet은 명령 5에서 끝나는 5 개의 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-135">The `Get-History` cmdlet gets the five commands ending in command 5.</span></span> <span data-ttu-id="c3aa7-136">파이프라인 연산자가 cmdlet에 전달 하 여 `Add-History` 현재 기록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-136">The pipeline operator passes them to the `Add-History` cmdlet, which appends them to the current history.</span></span> <span data-ttu-id="c3aa7-137">명령에는 `Add-History` 매개 변수가 포함 되어 있지 않지만 PowerShell은 파이프라인을 통해 전달 된 개체를의 **InputObject** 매개 변수와 연결 합니다 `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="c3aa7-137">The `Add-History` command does not include any parameters, but PowerShell associates the objects passed through the pipeline with the **InputObject** parameter of `Add-History`.</span></span>

### <span data-ttu-id="c3aa7-138">예제 4: .csv 파일의 명령을 현재 기록에 추가</span><span class="sxs-lookup"><span data-stu-id="c3aa7-138">Example 4: Add commands in a .csv file to the current history</span></span>

<span data-ttu-id="c3aa7-139">이 예에서는 파일의 명령을 `History.csv` 현재 세션 기록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-139">This example add the commands in the `History.csv` file to the current session history.</span></span>

```powershell
$a = Import-Csv c:\testing\history.csv
Add-History -InputObject $a -PassThru
```

<span data-ttu-id="c3aa7-140">`Import-Csv`Cmdlet은 파일의 명령을 가져와 `History.csv` 변수에 해당 내용을 저장 `$a` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-140">The `Import-Csv` cmdlet imports the commands in the `History.csv` file and store its contents in the variable `$a`.</span></span>

<span data-ttu-id="c3aa7-141">두 번째 명령은 cmdlet을 사용 하 여 `Add-History` 의 명령을 `History.csv` 현재 세션 기록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-141">The second command uses the `Add-History` cmdlet to add the commands from `History.csv` to the current session history.</span></span> <span data-ttu-id="c3aa7-142">**InputObject** 매개 변수를 사용 하 여 변수를 지정 하 `$a` 고 **PassThru** 매개 변수를 사용 하 여 명령줄에 표시할 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-142">It uses the **InputObject** parameter to specify the `$a` variable and the **PassThru** parameter to generate an object to display at the command line.</span></span> <span data-ttu-id="c3aa7-143">**PassThru** 매개 변수를 사용 하지 않으면 `Add-History` cmdlet은 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-143">Without the **PassThru** parameter, the `Add-History` cmdlet does not generate any output.</span></span>

### <span data-ttu-id="c3aa7-144">예 5: .xml 파일의 명령을 현재 기록에 추가</span><span class="sxs-lookup"><span data-stu-id="c3aa7-144">Example 5: Add commands in an .xml file to the current history</span></span>

<span data-ttu-id="c3aa7-145">이 예에서는 파일의 명령을 `history.xml` 현재 세션 기록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-145">This example adds the commands in the `history.xml` file to the current session history.</span></span>

```powershell
Add-History -InputObject (Import-Clixml c:\temp\history.xml)
```

<span data-ttu-id="c3aa7-146">**InputObject** 매개 변수는 명령 결과를 괄호 안에 cmdlet에 전달 합니다 `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="c3aa7-146">The **InputObject** parameter passes the results of the command in parentheses to the `Add-History` cmdlet.</span></span> <span data-ttu-id="c3aa7-147">괄호 안의 명령은 먼저 실행 되 고 `history.xml` 파일을 PowerShell로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-147">The command in parentheses, which is executed first, imports the `history.xml` file into PowerShell.</span></span> <span data-ttu-id="c3aa7-148">`Add-History`그런 다음 cmdlet은 파일의 명령을 세션 기록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-148">The `Add-History` cmdlet then adds the commands in the file to the session history.</span></span>

## <span data-ttu-id="c3aa7-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c3aa7-149">PARAMETERS</span></span>

### <span data-ttu-id="c3aa7-150">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c3aa7-150">-InputObject</span></span>

<span data-ttu-id="c3aa7-151">**HistoryInfo** 개체로 기록에 추가할 항목의 배열을 세션 기록에 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-151">Specifies an array of entries to add to the history as **HistoryInfo** object to the session history.</span></span>
<span data-ttu-id="c3aa7-152">이 매개 변수를 사용 하 여 **HistoryInfo** `Get-History` , `Import-Clixml` 또는 cmdlet에서 반환 된 개체와 같은 HistoryInfo 개체를로 전송할 수 있습니다 `Import-Csv` `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="c3aa7-152">You can use this parameter to submit a **HistoryInfo** object, such as the ones that are returned by the `Get-History`, `Import-Clixml`, or `Import-Csv` cmdlets, to `Add-History`.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c3aa7-153">-Passthru</span><span class="sxs-lookup"><span data-stu-id="c3aa7-153">-Passthru</span></span>

<span data-ttu-id="c3aa7-154">이 cmdlet이 각 기록 항목에 대 한 **HistoryInfo** 개체를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-154">Indicates that this cmdlet returns a **HistoryInfo** object for each history entry.</span></span> <span data-ttu-id="c3aa7-155">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-155">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="c3aa7-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c3aa7-156">CommonParameters</span></span>

<span data-ttu-id="c3aa7-157">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c3aa7-158">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c3aa7-159">입력</span><span class="sxs-lookup"><span data-stu-id="c3aa7-159">INPUTS</span></span>

### <span data-ttu-id="c3aa7-160">HistoryInfo.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-160">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="c3aa7-161">**HistoryInfo** 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-161">You can pipe a **HistoryInfo** object to this cmdlet.</span></span>

## <span data-ttu-id="c3aa7-162">출력</span><span class="sxs-lookup"><span data-stu-id="c3aa7-162">OUTPUTS</span></span>

### <span data-ttu-id="c3aa7-163">None 또는 HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="c3aa7-163">None or Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="c3aa7-164">**PassThru** 매개 변수를 지정 하는 경우이 Cmdlet은 **HistoryInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-164">This cmdlet returns a **HistoryInfo** object if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="c3aa7-165">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-165">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c3aa7-166">참고</span><span class="sxs-lookup"><span data-stu-id="c3aa7-166">NOTES</span></span>

<span data-ttu-id="c3aa7-167">세션 기록은 ID와 함께 세션 중에 입력 된 명령 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-167">The session history is a list of the commands entered during the session together with the ID.</span></span> <span data-ttu-id="c3aa7-168">세션 기록은 명령의 실행 순서, 상태, 시작 시간 및 종료 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-168">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="c3aa7-169">각 명령을 입력 하면 PowerShell에서 해당 명령을 다시 사용할 수 있도록 기록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-169">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="c3aa7-170">세션 기록에 대 한 자세한 내용은 [about_History](About/about_History.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-170">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="c3aa7-171">기록에 추가할 명령을 지정하려면 **InputObject** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-171">To specify the commands to add to the history, use the **InputObject** parameter.</span></span> <span data-ttu-id="c3aa7-172">`Add-History`명령은 cmdlet에 의해 각 명령에 대해 반환 된 개체와 같은 **HistoryInfo** 개체만 허용 `Get-History` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-172">The `Add-History` command accepts only **HistoryInfo** objects, such as those returned for each command by the `Get-History` cmdlet.</span></span> <span data-ttu-id="c3aa7-173">경로 및 파일 이름이나 명령 목록은 전달할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-173">You cannot pass it a path and file name or a list of commands.</span></span>

<span data-ttu-id="c3aa7-174">**InputObject** 매개 변수를 사용 하 여 **HistoryInfo** 개체의 파일을에 전달할 수 있습니다 `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="c3aa7-174">You can use the **InputObject** parameter to pass a file of **HistoryInfo** objects to `Add-History`.</span></span> <span data-ttu-id="c3aa7-175">이렇게 하려면 `Get-History` 또는 cmdlet을 사용 하 여 명령 결과를 파일로 내보낸 `Export-Csv` `Export-Clixml` 다음 또는 cmdlet을 사용 하 여 파일을 가져옵니다 `Import-Csv` `Import-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="c3aa7-175">To do so, export the results of a `Get-History` command to a file by using the `Export-Csv` or `Export-Clixml` cmdlet and then import the file by using the `Import-Csv` or `Import-Clixml` cmdlets.</span></span> <span data-ttu-id="c3aa7-176">그런 다음 파이프라인 또는 변수를 통해 가져온 **HistoryInfo** 개체의 파일을에 전달할 수 있습니다 `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="c3aa7-176">You can then pass the file of imported **HistoryInfo** objects to `Add-History` through a pipeline or in a variable.</span></span> <span data-ttu-id="c3aa7-177">자세한 내용은 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-177">For more information, see the examples.</span></span>

<span data-ttu-id="c3aa7-178">Cmdlet에 전달 하는 **HistoryInfo** 개체의 파일은 `Add-History` 유형 정보, 열 머리글 및 **HistoryInfo** 개체의 모든 속성을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-178">The file of **HistoryInfo** objects that you pass to the `Add-History` cmdlet must include the type information, column headings, and all of the properties of the **HistoryInfo** objects.</span></span> <span data-ttu-id="c3aa7-179">개체를 다시에 전달 하려는 경우 `Add-History` cmdlet의 **notypeinformation** 매개 변수를 사용 하지 말고 `Export-Csv` 파일의 유형 정보, 열 머리글 또는 필드를 삭제 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-179">If you intend to pass the objects back to `Add-History`, do not use the **NoTypeInformation** parameter of the `Export-Csv` cmdlet and do not delete the type information, column headings, or any fields in the file.</span></span>

<span data-ttu-id="c3aa7-180">세션 기록을 수정 하려면 세션을 CSV 또는 XML 파일로 내보낸 다음 파일을 수정 하 고를 사용 하 여 `Add-History` 현재 세션 기록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3aa7-180">To modify the session history, export the session to a CSV or XML file, modify the file, import the file, and use `Add-History` to append it to the current session history.</span></span>

## <span data-ttu-id="c3aa7-181">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c3aa7-181">RELATED LINKS</span></span>

[<span data-ttu-id="c3aa7-182">Clear-History</span><span class="sxs-lookup"><span data-stu-id="c3aa7-182">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="c3aa7-183">Get-History</span><span class="sxs-lookup"><span data-stu-id="c3aa7-183">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="c3aa7-184">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="c3aa7-184">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="c3aa7-185">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="c3aa7-185">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="c3aa7-186">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="c3aa7-186">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="c3aa7-187">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="c3aa7-187">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)

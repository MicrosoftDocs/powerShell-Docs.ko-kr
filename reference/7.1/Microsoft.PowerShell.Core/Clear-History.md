---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: c159262b21e39965f32db4a0fa736aa70de8e916
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211657"
---
# <span data-ttu-id="d2304-103">Clear-History</span><span class="sxs-lookup"><span data-stu-id="d2304-103">Clear-History</span></span>

## <span data-ttu-id="d2304-104">개요</span><span class="sxs-lookup"><span data-stu-id="d2304-104">SYNOPSIS</span></span>
<span data-ttu-id="d2304-105">PowerShell 세션 명령 기록에서 항목을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-105">Deletes entries from the PowerShell session command history.</span></span>

## <span data-ttu-id="d2304-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d2304-106">SYNTAX</span></span>

### <span data-ttu-id="d2304-107">IDParameter (기본값)</span><span class="sxs-lookup"><span data-stu-id="d2304-107">IDParameter (Default)</span></span>

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d2304-108">CommandLineParameter</span><span class="sxs-lookup"><span data-stu-id="d2304-108">CommandLineParameter</span></span>

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## <span data-ttu-id="d2304-109">설명</span><span class="sxs-lookup"><span data-stu-id="d2304-109">DESCRIPTION</span></span>

<span data-ttu-id="d2304-110">`Clear-History` PowerShell 세션에서 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-110">`Clear-History` deletes the command history from a PowerShell session.</span></span> <span data-ttu-id="d2304-111">각 PowerShell 세션에는 자체 명령 기록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-111">Each PowerShell session has its own command history.</span></span> <span data-ttu-id="d2304-112">명령 기록을 표시 하려면 cmdlet을 사용 `Get-History` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-112">To display the command history, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="d2304-113">기본적으로는 `Clear-History` PowerShell 세션에서 전체 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-113">By default, `Clear-History` deletes the entire command history from a PowerShell session.</span></span> <span data-ttu-id="d2304-114">매개 변수를 사용 `Clear-History` 하 여 선택한 명령을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-114">You can use parameters with `Clear-History` to delete selected commands.</span></span>

<span data-ttu-id="d2304-115">`Clear-History``PSReadLine`명령 기록 파일을 지우지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-115">`Clear-History` does not clear the `PSReadLine` command history file.</span></span> <span data-ttu-id="d2304-116">`PSReadLine`모듈은 모든 powershell 세션의 모든 powershell 명령을 포함 하는 기록 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-116">The `PSReadLine` module stores a history file that contains every PowerShell command from every PowerShell session.</span></span> <span data-ttu-id="d2304-117">PowerShell 프롬프트에서 키보드의 위쪽 및 아래쪽 화살표를 사용 하 여 명령 기록을 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-117">From a PowerShell prompt, use the up and down arrows on your keyboard to scroll through the command history.</span></span> <span data-ttu-id="d2304-118">`PSReadLine`명령 기록에 대 한 구성을 표시 하려면를 사용 `Get-PSReadLineOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-118">To display the `PSReadLine` configuration for command history, use `Get-PSReadLineOption`.</span></span>
<span data-ttu-id="d2304-119">`PSReadLine` PowerShell 5.0 이상에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-119">`PSReadLine` shipped with PowerShell 5.0 and above.</span></span> <span data-ttu-id="d2304-120">자세한 내용은 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2304-120">For more information, see [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="d2304-121">예제</span><span class="sxs-lookup"><span data-stu-id="d2304-121">EXAMPLES</span></span>

### <span data-ttu-id="d2304-122">예제 1: PowerShell 세션에서 명령 기록 삭제</span><span class="sxs-lookup"><span data-stu-id="d2304-122">Example 1: Delete the command history from a PowerShell session</span></span>

<span data-ttu-id="d2304-123">이 명령은 PowerShell 세션의 기록에서 모든 명령을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-123">This command deletes all of the commands from a PowerShell session's history.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location .\Test
   2 Update-Help
   3 Set-Location C:\Test\Logs
   4 Get-Location
```

```powershell
Clear-History
Get-History
```

```Output
  Id CommandLine
  -- -----------
   5 Clear-History
```

<span data-ttu-id="d2304-124">`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-124">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="d2304-125">`Clear-History` 전체 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-125">`Clear-History` deletes the entire command history.</span></span> <span data-ttu-id="d2304-126">`Get-History` 업데이트 된 명령 기록을 표시 하 고 이전 기록을 삭제 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-126">`Get-History` displays the updated command history and confirms the prior history was deleted.</span></span>

### <span data-ttu-id="d2304-127">예 2: 최신 명령 삭제</span><span class="sxs-lookup"><span data-stu-id="d2304-127">Example 2: Delete the newest commands</span></span>

<span data-ttu-id="d2304-128">이 명령은 **Count** 및 **최신** 매개 변수를 사용 하 여 PowerShell 세션의 기록에서 최신 명령을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-128">This command uses the **Count** and **Newest** parameters to delete the newest commands from a PowerShell session's history.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Count 5 -Newest
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
  11 Clear-History -Count 5 -Newest
```

<span data-ttu-id="d2304-129">`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-129">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="d2304-130">`Clear-History` 는 명령 기록을 삭제 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-130">`Clear-History` is used to delete the command history.</span></span> <span data-ttu-id="d2304-131">**Count** 매개 변수는 지정 된 **Id** 를 포함 하 여 삭제할 명령의 수를 지정 합니다. **최신** 매개 변수는 최근 명령이 기록에서 삭제 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-131">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id** . The **Newest** parameter specifies that the newest commands are cleared from the history.</span></span> <span data-ttu-id="d2304-132">`Get-History`업데이트 된 명령 기록을 표시 하 고 5 개의 최신 명령이 삭제 되었는지 확인 합니다 ( **id 6**  -  **id 10** ).</span><span class="sxs-lookup"><span data-stu-id="d2304-132">`Get-History` displays the updated command history and confirms that the five newest commands were deleted, **Id 6** - **Id 10** .</span></span>

### <span data-ttu-id="d2304-133">예 3: 특정 조건과 일치 하는 명령 삭제</span><span class="sxs-lookup"><span data-stu-id="d2304-133">Example 3: Delete commands that match specific criteria</span></span>

<span data-ttu-id="d2304-134">이 명령은 **CommandLine** 매개 변수로 정의 된 특정 조건과 일치 하는 명령을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-134">This command deletes commands that match specific criteria defined by the **CommandLine** parameter.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
```

```powershell
Clear-History -CommandLine *Help*, *Syntax
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   4 Get-Command Clear-History -ShowCommandInfo
   8 Clear-History -CommandLine *Help*, *Syntax
```

<span data-ttu-id="d2304-135">`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-135">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="d2304-136">`Clear-History` 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-136">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="d2304-137">**CommandLine** 매개 변수는 **도움말과** end **구문을** 포함 하는 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-137">The **CommandLine** parameter specifies commands that contain **Help** or end with **Syntax** .</span></span> <span data-ttu-id="d2304-138">`Get-History` 업데이트 된 명령 기록을 표시 하 고, id **3** , **id 5** , id **6** 및 **id 7** 명령이 삭제 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-138">`Get-History` displays the updated command history and confirms that commands **Id 3** , **Id 5** , **Id 6** , and **Id 7** were deleted.</span></span>

### <span data-ttu-id="d2304-139">예 4: Id 번호로 명령 삭제</span><span class="sxs-lookup"><span data-stu-id="d2304-139">Example 4: Delete commands by Id number</span></span>

<span data-ttu-id="d2304-140">이 명령은 **Id** 를 사용 하 여 특정 기록 항목을 삭제 합니다. 여러 명령을 삭제 하려면 쉼표로 구분 된 **Id** 번호 목록을 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-140">This command deletes specific history items using the **Id** . To delete multiple commands, submit a comma-separated list of **Id** numbers.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   3 Get-Help Get-Alias
   4 Get-Command Clear-History
   5 Get-Command Clear-History -Syntax
   6 Get-Command Clear-History -ShowCommandInfo
```

```powershell
Clear-History -Id 3, 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   4 Get-Command Clear-History
   6 Get-Command Clear-History -ShowCommandInfo
   7 Get-History
   8 Clear-History -Id 3, 5
```

<span data-ttu-id="d2304-141">`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-141">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="d2304-142">`Clear-History` 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-142">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="d2304-143">**Id** 매개 변수는 삭제할 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-143">The **Id** parameter specifies which commands to delete.</span></span> <span data-ttu-id="d2304-144">`Get-History` 업데이트 된 명령 기록을 표시 하 고 **id 3** 및 **id 5** 가 삭제 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-144">`Get-History` displays the updated command history and confirms that **Id 3** and **Id 5** were deleted.</span></span>

### <span data-ttu-id="d2304-145">예 5: Id 번호 및 개수로 명령 삭제</span><span class="sxs-lookup"><span data-stu-id="d2304-145">Example 5: Delete commands by Id number and count</span></span>

<span data-ttu-id="d2304-146">이 명령은 **Id** 및 **Count** 매개 변수를 사용 하 여 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-146">This command uses the **Id** and **Count** parameters to delete command history.</span></span> <span data-ttu-id="d2304-147">명령이 지정 된 **Id** 에서 역순으로 (최신에서 가장 오래 된 순서로) 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-147">Commands are deleted from the specified **Id** in reverse order, newest to oldest.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Id 7 -Count 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
  11 Clear-History -Id 7 -Count 5
```

<span data-ttu-id="d2304-148">`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-148">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="d2304-149">`Clear-History` 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-149">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="d2304-150">**Id** 매개 변수는 **id 7** 로 시작 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-150">The **Id** parameter specifies to begin with **Id 7** .</span></span> <span data-ttu-id="d2304-151">**Count** 매개 변수는 지정 된 **Id** 를 포함 하 여 다섯 개의 명령을 삭제 하도록 지정 합니다. `Get-History`업데이트 된 명령 기록을 표시 하 고 5 개의 명령이 삭제 되었는지 확인 합니다 ( **id 3**  -  **id 7** ).</span><span class="sxs-lookup"><span data-stu-id="d2304-151">The **Count** parameter specifies to delete five commands, inclusive of the specified **Id** . `Get-History` displays the updated command history and confirms that five commands were deleted, **Id 3** - **Id 7** .</span></span>

## <span data-ttu-id="d2304-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d2304-152">PARAMETERS</span></span>

### <span data-ttu-id="d2304-153">-CommandLine</span><span class="sxs-lookup"><span data-stu-id="d2304-153">-CommandLine</span></span>

<span data-ttu-id="d2304-154">PowerShell 세션에서 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-154">Deletes command history from a PowerShell session.</span></span> <span data-ttu-id="d2304-155">문자열은 정확히 일치 해야 합니다. 또는 와일드 카드를 사용 하 여에 표시 된 PowerShell 세션 기록의 명령과 일치 해야 합니다 `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="d2304-155">The string must be an exact match or use wildcards to match commands in the PowerShell session history displayed by `Get-History`.</span></span> <span data-ttu-id="d2304-156">둘 이상의 문자열을 입력 하는 경우는 `Clear-History` 문자열과 일치 하는 명령을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-156">If you enter more than one string, `Clear-History` deletes commands that match any of the strings.</span></span> <span data-ttu-id="d2304-157">**CommandLine** 매개 변수는 **Count** 와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-157">The **CommandLine** parameter can be used with **Count** .</span></span>

<span data-ttu-id="d2304-158">공백이 있는 문자열의 경우 단일 따옴표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-158">For strings with a space, use single quotations.</span></span> <span data-ttu-id="d2304-159">자세한 내용은 [about_Quoting_Rules](About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2304-159">For more information, see [about_Quoting_Rules](About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandLineParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="d2304-160">-개수</span><span class="sxs-lookup"><span data-stu-id="d2304-160">-Count</span></span>

<span data-ttu-id="d2304-161">삭제할 기록 항목의 수를 지정 합니다 `Clear-History` .</span><span class="sxs-lookup"><span data-stu-id="d2304-161">Specifies the number of history entries that `Clear-History` deletes.</span></span> <span data-ttu-id="d2304-162">명령은 기록에서 가장 오래 된 항목부터 시작 하 여 순서 대로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-162">Commands are deleted in order, beginning with the oldest entry in the history.</span></span>

<span data-ttu-id="d2304-163">**Count** 및 **Id** 매개 변수를 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-163">The **Count** and **Id** parameters can be used together.</span></span> <span data-ttu-id="d2304-164">**Count** 매개 변수는 지정 된 **Id** 를 포함 하 여 삭제할 명령의 수를 지정 합니다. 지정 된 **Id** 부터 명령이 순차적으로 역순으로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-164">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id** . Beginning at the specified **Id** , commands are deleted in reverse sequential order.</span></span> <span data-ttu-id="d2304-165">예를 들어 **Id** 가 30이 고 **개수가** 10 이면에서 `Clear-History` 21 ~ 30 개 항목을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-165">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 21 through 30.</span></span>

<span data-ttu-id="d2304-166">**Count** 및 **CommandLine** 매개 변수를 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-166">The **Count** and **CommandLine** parameters can be used together.</span></span> <span data-ttu-id="d2304-167">**Count** 는 해당 일치 하는 **명령줄** 매개 변수 값을 삭제 하는 명령 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-167">**Count** specifies the number of commands to delete that match **CommandLine** parameter value.</span></span> <span data-ttu-id="d2304-168">명령이 순서 대로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-168">The commands are deleted in sequential order.</span></span>

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

### <span data-ttu-id="d2304-169">-Id</span><span class="sxs-lookup"><span data-stu-id="d2304-169">-Id</span></span>

<span data-ttu-id="d2304-170">에서 삭제 하는 명령 기록 **Id** 를 지정 합니다 `Clear-History` .</span><span class="sxs-lookup"><span data-stu-id="d2304-170">Specifies the command history **Id** that `Clear-History` deletes.</span></span> <span data-ttu-id="d2304-171">**Id** 번호를 표시 하려면 cmdlet을 사용 `Get-History` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-171">To display **Id** numbers, use the `Get-History` cmdlet.</span></span> <span data-ttu-id="d2304-172">**Id** 번호는 순차적 이며 명령은 PowerShell 세션 전체에서 **id** 번호를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-172">The **Id** numbers are sequential and commands keep their **Id** number throughout a PowerShell session.</span></span> <span data-ttu-id="d2304-173">**Id** 매개 변수는 **Count** 와 **최신** 에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-173">The **Id** parameter can be used with **Count** and **Newest** .</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IDParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2304-174">-최신</span><span class="sxs-lookup"><span data-stu-id="d2304-174">-Newest</span></span>

<span data-ttu-id="d2304-175">**최신** 매개 변수가 사용 되 면는 `Clear-History` 기록에서 최신 항목을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-175">When the **Newest** parameter is used, `Clear-History` deletes the newest entries in the history.</span></span> <span data-ttu-id="d2304-176">기본적으로는 `Clear-History` 기록에서 가장 오래 된 항목을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-176">By default, `Clear-History` deletes the oldest entries in the history.</span></span>

<span data-ttu-id="d2304-177">**최신** 매개 변수는 **Id** 및 **개수** 와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-177">The **Newest** parameter can be used with **Id** and **Count** .</span></span> <span data-ttu-id="d2304-178">**Count** 매개 변수는 지정 된 **Id** 를 포함 하 여 삭제할 명령의 수를 지정 합니다. 지정 된 **Id** 부터 명령이 순서 대로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-178">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id** . Beginning at the specified **Id** , commands are deleted in sequential order.</span></span> <span data-ttu-id="d2304-179">예를 들어 **Id** 가 30이 고 **개수가** 10 인 경우는 `Clear-History` 30 ~ 39 항목을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-179">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 30 through 39.</span></span>

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

### <span data-ttu-id="d2304-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d2304-180">-Confirm</span></span>

<span data-ttu-id="d2304-181">Cmdlet을 실행 하기 전에 확인 메시지를 표시 `Clear-History` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-181">Prompts you for confirmation before running the `Clear-History` cmdlet.</span></span>

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

### <span data-ttu-id="d2304-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d2304-182">-WhatIf</span></span>

<span data-ttu-id="d2304-183">Cmdlet이 실행 될 경우 발생 하는 상황을 보여 줍니다 `Clear-History` .</span><span class="sxs-lookup"><span data-stu-id="d2304-183">Shows what would happen if the `Clear-History` cmdlet runs.</span></span> <span data-ttu-id="d2304-184">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-184">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d2304-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d2304-185">CommonParameters</span></span>

<span data-ttu-id="d2304-186">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d2304-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d2304-187">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2304-187">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="d2304-188">입력</span><span class="sxs-lookup"><span data-stu-id="d2304-188">INPUTS</span></span>

### <span data-ttu-id="d2304-189">없음</span><span class="sxs-lookup"><span data-stu-id="d2304-189">None</span></span>

<span data-ttu-id="d2304-190">개체를에 연결할 수 없습니다 `Clear-History` .</span><span class="sxs-lookup"><span data-stu-id="d2304-190">You cannot pipe objects to `Clear-History`.</span></span>

## <span data-ttu-id="d2304-191">출력</span><span class="sxs-lookup"><span data-stu-id="d2304-191">OUTPUTS</span></span>

### <span data-ttu-id="d2304-192">없음</span><span class="sxs-lookup"><span data-stu-id="d2304-192">None</span></span>

<span data-ttu-id="d2304-193">`Clear-History` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-193">`Clear-History` does not generate any output.</span></span>

## <span data-ttu-id="d2304-194">참고</span><span class="sxs-lookup"><span data-stu-id="d2304-194">NOTES</span></span>

<span data-ttu-id="d2304-195">Powershell 세션 기록은 PowerShell 세션 중에 입력 된 명령 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-195">The PowerShell session history is a list of the commands entered during a PowerShell session.</span></span> <span data-ttu-id="d2304-196">기록을 보고, 명령을 추가 및 삭제하고, 기록에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-196">You can view the history, add and delete commands, and run commands from the history.</span></span> <span data-ttu-id="d2304-197">자세한 내용은 [about_History](About/about_History.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2304-197">For more information, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="d2304-198">세션 기록은 **Psreadline** 모듈에 의해 유지 관리 되는 기록과 별도로 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-198">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="d2304-199">**Psreadline** 이 로드 된 세션에서 두 기록을 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-199">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="d2304-200">이 cmdlet은 세션 기록 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2304-200">This cmdlet only works with the session history.</span></span> <span data-ttu-id="d2304-201">자세한 내용은 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2304-201">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="d2304-202">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d2304-202">RELATED LINKS</span></span>

[<span data-ttu-id="d2304-203">about_History</span><span class="sxs-lookup"><span data-stu-id="d2304-203">about_History</span></span>](About/about_History.md)

[<span data-ttu-id="d2304-204">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="d2304-204">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="d2304-205">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="d2304-205">about_Quoting_Rules</span></span>](About/about_Quoting_Rules.md)

[<span data-ttu-id="d2304-206">Add-History</span><span class="sxs-lookup"><span data-stu-id="d2304-206">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="d2304-207">Get-History</span><span class="sxs-lookup"><span data-stu-id="d2304-207">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="d2304-208">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="d2304-208">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="d2304-209">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="d2304-209">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="d2304-210">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="d2304-210">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)


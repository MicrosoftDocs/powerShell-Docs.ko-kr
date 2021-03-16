---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: 1b465779f56c6bd71d7adfa7ffb5b391f5402656
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601867"
---
# <span data-ttu-id="6469b-102">Clear-History</span><span class="sxs-lookup"><span data-stu-id="6469b-102">Clear-History</span></span>

## <span data-ttu-id="6469b-103">개요</span><span class="sxs-lookup"><span data-stu-id="6469b-103">SYNOPSIS</span></span>
<span data-ttu-id="6469b-104">PowerShell 세션 명령 기록에서 항목을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-104">Deletes entries from the PowerShell session command history.</span></span>

## <span data-ttu-id="6469b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6469b-105">SYNTAX</span></span>

### <span data-ttu-id="6469b-106">IDParameter (기본값)</span><span class="sxs-lookup"><span data-stu-id="6469b-106">IDParameter (Default)</span></span>

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6469b-107">CommandLineParameter</span><span class="sxs-lookup"><span data-stu-id="6469b-107">CommandLineParameter</span></span>

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## <span data-ttu-id="6469b-108">설명</span><span class="sxs-lookup"><span data-stu-id="6469b-108">DESCRIPTION</span></span>

<span data-ttu-id="6469b-109">`Clear-History` PowerShell 세션에서 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-109">`Clear-History` deletes the command history from a PowerShell session.</span></span> <span data-ttu-id="6469b-110">각 PowerShell 세션에는 자체 명령 기록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-110">Each PowerShell session has its own command history.</span></span> <span data-ttu-id="6469b-111">명령 기록을 표시 하려면 cmdlet을 사용 `Get-History` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-111">To display the command history, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="6469b-112">기본적으로는 `Clear-History` PowerShell 세션에서 전체 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-112">By default, `Clear-History` deletes the entire command history from a PowerShell session.</span></span> <span data-ttu-id="6469b-113">매개 변수를 사용 `Clear-History` 하 여 선택한 명령을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-113">You can use parameters with `Clear-History` to delete selected commands.</span></span>

<span data-ttu-id="6469b-114">`Clear-History``PSReadLine`명령 기록 파일을 지우지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-114">`Clear-History` does not clear the `PSReadLine` command history file.</span></span> <span data-ttu-id="6469b-115">`PSReadLine`모듈은 모든 powershell 세션의 모든 powershell 명령을 포함 하는 기록 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-115">The `PSReadLine` module stores a history file that contains every PowerShell command from every PowerShell session.</span></span> <span data-ttu-id="6469b-116">PowerShell 프롬프트에서 키보드의 위쪽 및 아래쪽 화살표를 사용 하 여 명령 기록을 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-116">From a PowerShell prompt, use the up and down arrows on your keyboard to scroll through the command history.</span></span> <span data-ttu-id="6469b-117">`PSReadLine`명령 기록에 대 한 구성을 표시 하려면를 사용 `Get-PSReadLineOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-117">To display the `PSReadLine` configuration for command history, use `Get-PSReadLineOption`.</span></span>
<span data-ttu-id="6469b-118">`PSReadLine` PowerShell 5.0 이상에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-118">`PSReadLine` shipped with PowerShell 5.0 and above.</span></span> <span data-ttu-id="6469b-119">자세한 내용은 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6469b-119">For more information, see [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="6469b-120">예제</span><span class="sxs-lookup"><span data-stu-id="6469b-120">EXAMPLES</span></span>

### <span data-ttu-id="6469b-121">예제 1: PowerShell 세션에서 명령 기록 삭제</span><span class="sxs-lookup"><span data-stu-id="6469b-121">Example 1: Delete the command history from a PowerShell session</span></span>

<span data-ttu-id="6469b-122">이 명령은 PowerShell 세션의 기록에서 모든 명령을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-122">This command deletes all of the commands from a PowerShell session's history.</span></span>

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

<span data-ttu-id="6469b-123">`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-123">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="6469b-124">`Clear-History` 전체 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-124">`Clear-History` deletes the entire command history.</span></span> <span data-ttu-id="6469b-125">`Get-History` 업데이트 된 명령 기록을 표시 하 고 이전 기록을 삭제 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-125">`Get-History` displays the updated command history and confirms the prior history was deleted.</span></span>

### <span data-ttu-id="6469b-126">예 2: 최신 명령 삭제</span><span class="sxs-lookup"><span data-stu-id="6469b-126">Example 2: Delete the newest commands</span></span>

<span data-ttu-id="6469b-127">이 명령은 **Count** 및 **최신** 매개 변수를 사용 하 여 PowerShell 세션의 기록에서 최신 명령을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-127">This command uses the **Count** and **Newest** parameters to delete the newest commands from a PowerShell session's history.</span></span>

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

<span data-ttu-id="6469b-128">`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-128">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="6469b-129">`Clear-History` 는 명령 기록을 삭제 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-129">`Clear-History` is used to delete the command history.</span></span> <span data-ttu-id="6469b-130">**Count** 매개 변수는 지정 된 **Id** 를 포함 하 여 삭제할 명령의 수를 지정 합니다. **최신** 매개 변수는 최근 명령이 기록에서 삭제 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-130">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. The **Newest** parameter specifies that the newest commands are cleared from the history.</span></span> <span data-ttu-id="6469b-131">`Get-History`업데이트 된 명령 기록을 표시 하 고 5 개의 최신 명령이 삭제 되었는지 확인 합니다 ( **id 6**  -  **id 10**).</span><span class="sxs-lookup"><span data-stu-id="6469b-131">`Get-History` displays the updated command history and confirms that the five newest commands were deleted, **Id 6** - **Id 10**.</span></span>

### <span data-ttu-id="6469b-132">예 3: 특정 조건과 일치 하는 명령 삭제</span><span class="sxs-lookup"><span data-stu-id="6469b-132">Example 3: Delete commands that match specific criteria</span></span>

<span data-ttu-id="6469b-133">이 명령은 **CommandLine** 매개 변수로 정의 된 특정 조건과 일치 하는 명령을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-133">This command deletes commands that match specific criteria defined by the **CommandLine** parameter.</span></span>

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

<span data-ttu-id="6469b-134">`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-134">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="6469b-135">`Clear-History` 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-135">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="6469b-136">**CommandLine** 매개 변수는 **도움말과** end **구문을** 포함 하는 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-136">The **CommandLine** parameter specifies commands that contain **Help** or end with **Syntax**.</span></span> <span data-ttu-id="6469b-137">`Get-History` 업데이트 된 명령 기록을 표시 하 고, id **3**, **id 5**, id **6** 및 **id 7** 명령이 삭제 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-137">`Get-History` displays the updated command history and confirms that commands **Id 3**, **Id 5**, **Id 6**, and **Id 7** were deleted.</span></span>

### <span data-ttu-id="6469b-138">예 4: Id 번호로 명령 삭제</span><span class="sxs-lookup"><span data-stu-id="6469b-138">Example 4: Delete commands by Id number</span></span>

<span data-ttu-id="6469b-139">이 명령은 **Id** 를 사용 하 여 특정 기록 항목을 삭제 합니다. 여러 명령을 삭제 하려면 쉼표로 구분 된 **Id** 번호 목록을 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-139">This command deletes specific history items using the **Id**. To delete multiple commands, submit a comma-separated list of **Id** numbers.</span></span>

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

<span data-ttu-id="6469b-140">`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-140">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="6469b-141">`Clear-History` 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-141">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="6469b-142">**Id** 매개 변수는 삭제할 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-142">The **Id** parameter specifies which commands to delete.</span></span> <span data-ttu-id="6469b-143">`Get-History` 업데이트 된 명령 기록을 표시 하 고 **id 3** 및 **id 5** 가 삭제 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-143">`Get-History` displays the updated command history and confirms that **Id 3** and **Id 5** were deleted.</span></span>

### <span data-ttu-id="6469b-144">예 5: Id 번호 및 개수로 명령 삭제</span><span class="sxs-lookup"><span data-stu-id="6469b-144">Example 5: Delete commands by Id number and count</span></span>

<span data-ttu-id="6469b-145">이 명령은 **Id** 및 **Count** 매개 변수를 사용 하 여 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-145">This command uses the **Id** and **Count** parameters to delete command history.</span></span> <span data-ttu-id="6469b-146">명령이 지정 된 **Id** 에서 역순으로 (최신에서 가장 오래 된 순서로) 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-146">Commands are deleted from the specified **Id** in reverse order, newest to oldest.</span></span>

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

<span data-ttu-id="6469b-147">`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-147">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="6469b-148">`Clear-History` 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-148">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="6469b-149">**Id** 매개 변수는 **id 7** 로 시작 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-149">The **Id** parameter specifies to begin with **Id 7**.</span></span> <span data-ttu-id="6469b-150">**Count** 매개 변수는 지정 된 **Id** 를 포함 하 여 다섯 개의 명령을 삭제 하도록 지정 합니다. `Get-History`업데이트 된 명령 기록을 표시 하 고 5 개의 명령이 삭제 되었는지 확인 합니다 ( **id 3**  -  **id 7**).</span><span class="sxs-lookup"><span data-stu-id="6469b-150">The **Count** parameter specifies to delete five commands, inclusive of the specified **Id**. `Get-History` displays the updated command history and confirms that five commands were deleted, **Id 3** - **Id 7**.</span></span>

## <span data-ttu-id="6469b-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6469b-151">PARAMETERS</span></span>

### <span data-ttu-id="6469b-152">-CommandLine</span><span class="sxs-lookup"><span data-stu-id="6469b-152">-CommandLine</span></span>

<span data-ttu-id="6469b-153">PowerShell 세션에서 명령 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-153">Deletes command history from a PowerShell session.</span></span> <span data-ttu-id="6469b-154">문자열은 정확히 일치 해야 합니다. 또는 와일드 카드를 사용 하 여에 표시 된 PowerShell 세션 기록의 명령과 일치 해야 합니다 `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="6469b-154">The string must be an exact match or use wildcards to match commands in the PowerShell session history displayed by `Get-History`.</span></span> <span data-ttu-id="6469b-155">둘 이상의 문자열을 입력 하는 경우는 `Clear-History` 문자열과 일치 하는 명령을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-155">If you enter more than one string, `Clear-History` deletes commands that match any of the strings.</span></span> <span data-ttu-id="6469b-156">**CommandLine** 매개 변수는 **Count** 와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-156">The **CommandLine** parameter can be used with **Count**.</span></span>

<span data-ttu-id="6469b-157">공백이 있는 문자열의 경우 단일 따옴표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-157">For strings with a space, use single quotations.</span></span> <span data-ttu-id="6469b-158">자세한 내용은 [about_Quoting_Rules](About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6469b-158">For more information, see [about_Quoting_Rules](About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="6469b-159">-개수</span><span class="sxs-lookup"><span data-stu-id="6469b-159">-Count</span></span>

<span data-ttu-id="6469b-160">삭제할 기록 항목의 수를 지정 합니다 `Clear-History` .</span><span class="sxs-lookup"><span data-stu-id="6469b-160">Specifies the number of history entries that `Clear-History` deletes.</span></span> <span data-ttu-id="6469b-161">명령은 기록에서 가장 오래 된 항목부터 시작 하 여 순서 대로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-161">Commands are deleted in order, beginning with the oldest entry in the history.</span></span>

<span data-ttu-id="6469b-162">**Count** 및 **Id** 매개 변수를 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-162">The **Count** and **Id** parameters can be used together.</span></span> <span data-ttu-id="6469b-163">**Count** 매개 변수는 지정 된 **Id** 를 포함 하 여 삭제할 명령의 수를 지정 합니다. 지정 된 **Id** 부터 명령이 순차적으로 역순으로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-163">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. Beginning at the specified **Id**, commands are deleted in reverse sequential order.</span></span> <span data-ttu-id="6469b-164">예를 들어 **Id** 가 30이 고 **개수가** 10 이면에서 `Clear-History` 21 ~ 30 개 항목을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-164">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 21 through 30.</span></span>

<span data-ttu-id="6469b-165">**Count** 및 **CommandLine** 매개 변수를 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-165">The **Count** and **CommandLine** parameters can be used together.</span></span> <span data-ttu-id="6469b-166">**Count** 는 해당 일치 하는 **명령줄** 매개 변수 값을 삭제 하는 명령 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-166">**Count** specifies the number of commands to delete that match **CommandLine** parameter value.</span></span> <span data-ttu-id="6469b-167">명령이 순서 대로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-167">The commands are deleted in sequential order.</span></span>

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

### <span data-ttu-id="6469b-168">-Id</span><span class="sxs-lookup"><span data-stu-id="6469b-168">-Id</span></span>

<span data-ttu-id="6469b-169">에서 삭제 하는 명령 기록 **Id** 를 지정 합니다 `Clear-History` .</span><span class="sxs-lookup"><span data-stu-id="6469b-169">Specifies the command history **Id** that `Clear-History` deletes.</span></span> <span data-ttu-id="6469b-170">**Id** 번호를 표시 하려면 cmdlet을 사용 `Get-History` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-170">To display **Id** numbers, use the `Get-History` cmdlet.</span></span> <span data-ttu-id="6469b-171">**Id** 번호는 순차적 이며 명령은 PowerShell 세션 전체에서 **id** 번호를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-171">The **Id** numbers are sequential and commands keep their **Id** number throughout a PowerShell session.</span></span> <span data-ttu-id="6469b-172">**Id** 매개 변수는 **Count** 와 **최신** 에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-172">The **Id** parameter can be used with **Count** and **Newest**.</span></span>

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

### <span data-ttu-id="6469b-173">-최신</span><span class="sxs-lookup"><span data-stu-id="6469b-173">-Newest</span></span>

<span data-ttu-id="6469b-174">**최신** 매개 변수가 사용 되 면는 `Clear-History` 기록에서 최신 항목을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-174">When the **Newest** parameter is used, `Clear-History` deletes the newest entries in the history.</span></span> <span data-ttu-id="6469b-175">기본적으로는 `Clear-History` 기록에서 가장 오래 된 항목을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-175">By default, `Clear-History` deletes the oldest entries in the history.</span></span>

<span data-ttu-id="6469b-176">**최신** 매개 변수는 **Id** 및 **개수** 와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-176">The **Newest** parameter can be used with **Id** and **Count**.</span></span> <span data-ttu-id="6469b-177">**Count** 매개 변수는 지정 된 **Id** 를 포함 하 여 삭제할 명령의 수를 지정 합니다. 지정 된 **Id** 부터 명령이 순서 대로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-177">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. Beginning at the specified **Id**, commands are deleted in sequential order.</span></span> <span data-ttu-id="6469b-178">예를 들어 **Id** 가 30이 고 **개수가** 10 인 경우는 `Clear-History` 30 ~ 39 항목을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-178">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 30 through 39.</span></span>

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

### <span data-ttu-id="6469b-179">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6469b-179">-Confirm</span></span>

<span data-ttu-id="6469b-180">Cmdlet을 실행 하기 전에 확인 메시지를 표시 `Clear-History` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-180">Prompts you for confirmation before running the `Clear-History` cmdlet.</span></span>

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

### <span data-ttu-id="6469b-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6469b-181">-WhatIf</span></span>

<span data-ttu-id="6469b-182">Cmdlet이 실행 될 경우 발생 하는 상황을 보여 줍니다 `Clear-History` .</span><span class="sxs-lookup"><span data-stu-id="6469b-182">Shows what would happen if the `Clear-History` cmdlet runs.</span></span> <span data-ttu-id="6469b-183">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-183">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6469b-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6469b-184">CommonParameters</span></span>

<span data-ttu-id="6469b-185">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6469b-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6469b-186">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6469b-186">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6469b-187">입력</span><span class="sxs-lookup"><span data-stu-id="6469b-187">INPUTS</span></span>

### <span data-ttu-id="6469b-188">없음</span><span class="sxs-lookup"><span data-stu-id="6469b-188">None</span></span>

<span data-ttu-id="6469b-189">개체를에 연결할 수 없습니다 `Clear-History` .</span><span class="sxs-lookup"><span data-stu-id="6469b-189">You cannot pipe objects to `Clear-History`.</span></span>

## <span data-ttu-id="6469b-190">출력</span><span class="sxs-lookup"><span data-stu-id="6469b-190">OUTPUTS</span></span>

### <span data-ttu-id="6469b-191">없음</span><span class="sxs-lookup"><span data-stu-id="6469b-191">None</span></span>

<span data-ttu-id="6469b-192">`Clear-History` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-192">`Clear-History` does not generate any output.</span></span>

## <span data-ttu-id="6469b-193">참고</span><span class="sxs-lookup"><span data-stu-id="6469b-193">NOTES</span></span>

<span data-ttu-id="6469b-194">Powershell 세션 기록은 PowerShell 세션 중에 입력 된 명령 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-194">The PowerShell session history is a list of the commands entered during a PowerShell session.</span></span> <span data-ttu-id="6469b-195">기록을 보고, 명령을 추가 및 삭제하고, 기록에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-195">You can view the history, add and delete commands, and run commands from the history.</span></span> <span data-ttu-id="6469b-196">자세한 내용은 [about_History](About/about_History.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6469b-196">For more information, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="6469b-197">세션 기록은 **Psreadline** 모듈에 의해 유지 관리 되는 기록과 별도로 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-197">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="6469b-198">**Psreadline** 이 로드 된 세션에서 두 기록을 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-198">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="6469b-199">이 cmdlet은 세션 기록 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6469b-199">This cmdlet only works with the session history.</span></span> <span data-ttu-id="6469b-200">자세한 내용은 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6469b-200">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="6469b-201">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6469b-201">RELATED LINKS</span></span>

[<span data-ttu-id="6469b-202">about_History</span><span class="sxs-lookup"><span data-stu-id="6469b-202">about_History</span></span>](About/about_History.md)

[<span data-ttu-id="6469b-203">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="6469b-203">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="6469b-204">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="6469b-204">about_Quoting_Rules</span></span>](About/about_Quoting_Rules.md)

[<span data-ttu-id="6469b-205">Add-History</span><span class="sxs-lookup"><span data-stu-id="6469b-205">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="6469b-206">Get-History</span><span class="sxs-lookup"><span data-stu-id="6469b-206">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="6469b-207">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="6469b-207">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="6469b-208">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="6469b-208">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="6469b-209">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="6469b-209">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)

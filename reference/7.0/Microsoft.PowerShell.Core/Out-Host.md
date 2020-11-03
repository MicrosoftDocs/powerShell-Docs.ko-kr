---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-host?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Host
ms.openlocfilehash: e3b009ae92abde371a4a6380d0ac6d491093333f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210650"
---
# <span data-ttu-id="dc085-103">Out-Host</span><span class="sxs-lookup"><span data-stu-id="dc085-103">Out-Host</span></span>

## <span data-ttu-id="dc085-104">개요</span><span class="sxs-lookup"><span data-stu-id="dc085-104">SYNOPSIS</span></span>
<span data-ttu-id="dc085-105">출력을 명령줄로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-105">Sends output to the command line.</span></span>

## <span data-ttu-id="dc085-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dc085-106">SYNTAX</span></span>

### <span data-ttu-id="dc085-107">모두</span><span class="sxs-lookup"><span data-stu-id="dc085-107">All</span></span>

```
Out-Host [-Paging] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="dc085-108">설명</span><span class="sxs-lookup"><span data-stu-id="dc085-108">DESCRIPTION</span></span>

<span data-ttu-id="dc085-109">`Out-Host`Cmdlet은 표시를 위해 출력을 PowerShell 호스트로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-109">The `Out-Host` cmdlet sends output to the PowerShell host for display.</span></span> <span data-ttu-id="dc085-110">이 호스트는 명령줄에 출력을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-110">The host displays the output at the command line.</span></span> <span data-ttu-id="dc085-111">는 기본값 이기 때문에 `Out-Host` 매개 변수를 사용 하지 않을 경우에는 지정 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-111">Because `Out-Host` is the default, you don't have to specify it unless you want to use its parameters.</span></span>

<span data-ttu-id="dc085-112">`Out-Host` 는 실행 되는 모든 명령에 자동으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-112">`Out-Host` is automatically appended to every command that is executed.</span></span> <span data-ttu-id="dc085-113">명령을 실행 하는 호스트에 파이프라인 출력을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-113">It passes the output of the pipeline to the host executing the command.</span></span> <span data-ttu-id="dc085-114">`Out-Host` ANSI 이스케이프 시퀀스를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-114">`Out-Host` ignores ANSI escape sequences.</span></span> <span data-ttu-id="dc085-115">이스케이프 시퀀스는 호스트에 의해 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-115">The escape sequences are handled by the host.</span></span> <span data-ttu-id="dc085-116">`Out-Host` 해석 하거나 변경 하지 않고 ANSI 이스케이프 시퀀스를 호스트에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-116">`Out-Host` passes ANSI escape sequences to the host without trying to interpret or change them.</span></span>

## <span data-ttu-id="dc085-117">예제</span><span class="sxs-lookup"><span data-stu-id="dc085-117">EXAMPLES</span></span>

### <span data-ttu-id="dc085-118">예제 1: 한 번에 한 페이지씩 출력 표시</span><span class="sxs-lookup"><span data-stu-id="dc085-118">Example 1: Display output one page at a time</span></span>

<span data-ttu-id="dc085-119">이 예에서는 시스템 프로세스를 한 번에 한 페이지씩 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-119">This example displays the system processes one page at a time.</span></span>

```powershell
Get-Process | Out-Host -Paging
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     30    24.12      36.95      15.86   21004  14 ApplicationFrameHost
     55    24.33      60.48      10.80   12904  14 BCompare
<SPACE> next page; <CR> next line; Q quit
      9     4.71       8.94       0.00   16864  14 explorer
<SPACE> next page; <CR> next line; Q quit
```

<span data-ttu-id="dc085-120">`Get-Process` 시스템 프로세스를 가져오고 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-120">`Get-Process` gets the system processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="dc085-121">`Out-Host`**페이징** 매개 변수를 사용 하 여 한 번에 하나의 데이터 페이지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-121">`Out-Host` uses the **Paging** parameter to display one page of data at a time.</span></span>

### <span data-ttu-id="dc085-122">예제 2: 변수를 입력으로 사용</span><span class="sxs-lookup"><span data-stu-id="dc085-122">Example 2: Use a variable as input</span></span>

<span data-ttu-id="dc085-123">이 예에서는 변수에 저장 된 개체를에 대 한 입력으로 사용 `Out-Host` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-123">This example uses objects stored in a variable as the input for `Out-Host`.</span></span>

```powershell
$io = Get-History
Out-Host -InputObject $io
```

<span data-ttu-id="dc085-124">`Get-History` PowerShell 세션의 기록을 가져오고 개체를 `$io` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-124">`Get-History` gets the PowerShell session's history, and stores the objects in the `$io` variable.</span></span>
<span data-ttu-id="dc085-125">`Out-Host`**InputObject** 매개 변수를 사용 하 여 변수를 지정 하 `$io` 고 기록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-125">`Out-Host` uses the **InputObject** parameter to specify the `$io` variable and displays the history.</span></span>

## <span data-ttu-id="dc085-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dc085-126">PARAMETERS</span></span>

### <span data-ttu-id="dc085-127">-InputObject</span><span class="sxs-lookup"><span data-stu-id="dc085-127">-InputObject</span></span>

<span data-ttu-id="dc085-128">콘솔에 기록할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-128">Specifies the objects that are written to the console.</span></span> <span data-ttu-id="dc085-129">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="dc085-129">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dc085-130">-페이징</span><span class="sxs-lookup"><span data-stu-id="dc085-130">-Paging</span></span>

<span data-ttu-id="dc085-131">에서 한 번 `Out-Host` 에 한 페이지씩 출력을 표시 하 고 나머지 페이지를 표시 하기 전에 사용자 입력을 대기 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-131">Indicates that `Out-Host` displays one page of output at a time, and waits for user input before the remaining pages are displayed.</span></span> <span data-ttu-id="dc085-132">기본적으로 모든 출력은 단일 페이지에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-132">By default, all the output is displayed on a single page.</span></span> <span data-ttu-id="dc085-133">호스트의 특성에 따라 페이지 크기가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-133">The page size is determined by the characteristics of the host.</span></span>

<span data-ttu-id="dc085-134">다음 출력 페이지를 표시 하려면 <kbd>스페이스바</kbd> 를 누르고 출력의 다음 줄을 보려면 <kbd>enter</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-134">Press the <kbd>Space</kbd> bar to display the next page of output or the <kbd>Enter</kbd> key to view the next line of output.</span></span> <span data-ttu-id="dc085-135"><kbd>Q</kbd> 키를 눌러 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-135">Press <kbd>Q</kbd> to quit.</span></span>

<span data-ttu-id="dc085-136">**페이징은** **추가** 명령과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-136">**Paging** is similar to the **more** command.</span></span>

> [!NOTE]
> <span data-ttu-id="dc085-137">**페이징** 매개 변수는 PowerShell ISE 호스트에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-137">The **Paging** parameter isn't supported by the PowerShell ISE host.</span></span>

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

### <span data-ttu-id="dc085-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dc085-138">CommonParameters</span></span>

<span data-ttu-id="dc085-139">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dc085-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dc085-140">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc085-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dc085-141">입력</span><span class="sxs-lookup"><span data-stu-id="dc085-141">INPUTS</span></span>

### <span data-ttu-id="dc085-142">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="dc085-142">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="dc085-143">파이프라인에서로 개체를 보낼 수 있습니다 `Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="dc085-143">You can send objects down the pipeline to `Out-Host`.</span></span>

## <span data-ttu-id="dc085-144">출력</span><span class="sxs-lookup"><span data-stu-id="dc085-144">OUTPUTS</span></span>

### <span data-ttu-id="dc085-145">없음</span><span class="sxs-lookup"><span data-stu-id="dc085-145">None</span></span>

<span data-ttu-id="dc085-146">`Out-Host` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-146">`Out-Host` doesn't generate any output.</span></span> <span data-ttu-id="dc085-147">표시 하기 위해 호스트에 개체를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-147">It sends objects to the host for display.</span></span>

## <span data-ttu-id="dc085-148">참고</span><span class="sxs-lookup"><span data-stu-id="dc085-148">NOTES</span></span>

<span data-ttu-id="dc085-149">모든 PowerShell 호스트에서 **페이징** 매개 변수를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-149">The **Paging** parameter isn't supported by all PowerShell hosts.</span></span> <span data-ttu-id="dc085-150">예를 들어 PowerShell ISE에서 **Paging** 매개 변수를 사용 하는 경우 다음과 같은 오류가 표시 됩니다. `out-lineoutput : The method or operation is not implemented.`</span><span class="sxs-lookup"><span data-stu-id="dc085-150">For example, if you use the **Paging** parameter in the PowerShell ISE, the following error is displayed: `out-lineoutput : The method or operation is not implemented.`</span></span>

<span data-ttu-id="dc085-151">**Out** 동사를 포함 하는 cmdlet은 `Out-` 개체의 형식을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-151">The cmdlets that contain the **Out** verb, `Out-`, don't format objects.</span></span> <span data-ttu-id="dc085-152">개체를 렌더링 하 고 지정 된 표시 대상으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-152">They render objects and send them to the specified display destination.</span></span> <span data-ttu-id="dc085-153">포맷 되지 않은 개체를 cmdlet에 보내면 `Out-` cmdlet이 해당 개체를 렌더링 하기 전에 형식 지정 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-153">If you send an unformatted object to an `Out-` cmdlet, the cmdlet sends it to a formatting cmdlet before rendering it.</span></span>

<span data-ttu-id="dc085-154">Cmdlet에는 `Out-` 이름 또는 파일 경로에 대 한 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-154">The `Out-` cmdlets don't have parameters for names or file paths.</span></span> <span data-ttu-id="dc085-155">Cmdlet을 사용 하 여 cmdlet에 데이터를 보내려면 파이프라인을 사용 하 여 `Out-` PowerShell 명령의 출력을 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-155">To send data to an `Out-` cmdlet, use the pipeline to send a PowerShell command's output to the cmdlet.</span></span> <span data-ttu-id="dc085-156">또는 변수에 데이터를 저장 하 고 **InputObject** 매개 변수를 사용 하 여 cmdlet에 데이터를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-156">Or, you can store data in a variable and use the **InputObject** parameter to pass the data to the cmdlet.</span></span>

<span data-ttu-id="dc085-157">`Out-Host` 는 데이터를 보내지만 출력 개체를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-157">`Out-Host` sends data, but it doesn't produce any output objects.</span></span> <span data-ttu-id="dc085-158">의 출력을 cmdlet으로 파이프라인 하는 경우는 `Out-Host` `Get-Member` 지정 된 `Get-Member` 개체가 없음을 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc085-158">If you pipeline the output of `Out-Host` to the `Get-Member` cmdlet, `Get-Member` reports that no objects have been specified.</span></span>

## <span data-ttu-id="dc085-159">관련 링크</span><span class="sxs-lookup"><span data-stu-id="dc085-159">RELATED LINKS</span></span>

[<span data-ttu-id="dc085-160">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="dc085-160">Clear-Host</span></span>](Clear-Host.md)

[<span data-ttu-id="dc085-161">Out-Default</span><span class="sxs-lookup"><span data-stu-id="dc085-161">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="dc085-162">Out-File</span><span class="sxs-lookup"><span data-stu-id="dc085-162">Out-File</span></span>](../Microsoft.PowerShell.Utility/Out-File.md)

[<span data-ttu-id="dc085-163">Out-Null</span><span class="sxs-lookup"><span data-stu-id="dc085-163">Out-Null</span></span>](Out-Null.md)

[<span data-ttu-id="dc085-164">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="dc085-164">Out-Printer</span></span>](../Microsoft.PowerShell.Utility/Out-Printer.md)

[<span data-ttu-id="dc085-165">Out-String</span><span class="sxs-lookup"><span data-stu-id="dc085-165">Out-String</span></span>](../Microsoft.PowerShell.Utility/Out-String.md)

[<span data-ttu-id="dc085-166">Write-Host</span><span class="sxs-lookup"><span data-stu-id="dc085-166">Write-Host</span></span>](../Microsoft.PowerShell.Utility/Write-Host.md)

---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: 7e622367f1753fc15bed26fe083e9f343fd82b85
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224346"
---
# <span data-ttu-id="27df4-103">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="27df4-103">Write-Debug</span></span>

## <span data-ttu-id="27df4-104">개요</span><span class="sxs-lookup"><span data-stu-id="27df4-104">SYNOPSIS</span></span>
<span data-ttu-id="27df4-105">콘솔에 디버그 메시지를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-105">Writes a debug message to the console.</span></span>

## <span data-ttu-id="27df4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="27df4-106">SYNTAX</span></span>

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="27df4-107">설명</span><span class="sxs-lookup"><span data-stu-id="27df4-107">DESCRIPTION</span></span>

<span data-ttu-id="27df4-108">`Write-Debug`Cmdlet은 스크립트 또는 명령에서 호스트에 디버그 메시지를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-108">The `Write-Debug` cmdlet writes debug messages to the host from a script or command.</span></span>

<span data-ttu-id="27df4-109">기본적으로 디버그 메시지는 콘솔에 표시 되지 않지만 **debug** 매개 변수 또는 변수를 사용 하 여 표시할 수 있습니다 `$DebugPreference` .</span><span class="sxs-lookup"><span data-stu-id="27df4-109">By default, debug messages are not displayed in the console, but you can display them by using the **Debug** parameter or the `$DebugPreference` variable.</span></span>

## <span data-ttu-id="27df4-110">예제</span><span class="sxs-lookup"><span data-stu-id="27df4-110">EXAMPLES</span></span>

### <span data-ttu-id="27df4-111">예 1: $DebugPreference 이해</span><span class="sxs-lookup"><span data-stu-id="27df4-111">Example 1: Understand $DebugPreference</span></span>

<span data-ttu-id="27df4-112">이 예제에서는 디버그 메시지를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-112">This example writes a debug message.</span></span>

```powershell
Write-Debug "Cannot open file."
```

<span data-ttu-id="27df4-113">의 기본값은 `$DebugPreference` **SilentlyContinue** 입니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-113">The default value of `$DebugPreference` is **SilentlyContinue** .</span></span> <span data-ttu-id="27df4-114">따라서 메시지는 콘솔에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-114">Therefore, the message is not displayed in the console.</span></span>

### <span data-ttu-id="27df4-115">예제 2: 값 변경 $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="27df4-115">Example 2: Change the value of $DebugPreference</span></span>

<span data-ttu-id="27df4-116">이 예에서는 변수 값을 변경 하는 경우의 결과를 보여 줍니다 `$DebugPreference` .</span><span class="sxs-lookup"><span data-stu-id="27df4-116">This example shows the effect of changing the value of the `$DebugPreference` variable.</span></span> <span data-ttu-id="27df4-117">먼저의 현재 값을 표시 하 `$DebugPreference` 고 디버그 메시지를 쓰려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-117">First, we display the current value of `$DebugPreference` and attempt to write a debug message.</span></span> <span data-ttu-id="27df4-118">그런 다음 값을 `$DebugPreference` **Continue** 로 변경 하 여 디버그 메시지를 표시할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-118">Then we change the value of `$DebugPreference` to **Continue** , which allows debug messages to be displayed.</span></span>

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

<span data-ttu-id="27df4-119">에 대 한 자세한 내용은 `$DebugPreference` [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="27df4-119">For more information about `$DebugPreference`, see [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).</span></span>

### <span data-ttu-id="27df4-120">예제 3: Debug 매개 변수를 사용 하 여 $DebugPreference 재정의</span><span class="sxs-lookup"><span data-stu-id="27df4-120">Example 3: Use the Debug parameter to override $DebugPreference</span></span>

<span data-ttu-id="27df4-121">`Test-Debug`함수는 변수 값을 `$DebugPreference` PowerShell 호스트 및 디버그 스트림에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-121">The `Test-Debug` function writes the value of the `$DebugPreference` variable to the PowerShell host and to the Debug stream.</span></span> <span data-ttu-id="27df4-122">이 예제에서는 **Debug** 매개 변수를 사용 하 여 값을 재정의 `$DebugPreference` 합니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-122">In this example, we use the **Debug** parameter to override the `$DebugPreference` value.</span></span>

```powershell
function Test-Debug {
    [CmdletBinding()]
    param()
    Write-Debug ('$DebugPreference is ' + $DebugPreference)
    Write-Host ('$DebugPreference is ' + $DebugPreference)
}
```

```
PS> Test-Debug
$DebugPreference is SilentlyContinue

PS> Test-Debug -Debug
DEBUG: $DebugPreference is Inquire

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
$DebugPreference is Inquire
PS> $DebugPreference
SilentlyContinue
```

<span data-ttu-id="27df4-123">Debug 매개 변수를 사용 하는 경우의 값이 변경 된 것을 확인할 `$DebugPreference` 수 있습니다. **Debug**</span><span class="sxs-lookup"><span data-stu-id="27df4-123">Notice that the value of `$DebugPreference` changes when you use the **Debug** parameter.</span></span> <span data-ttu-id="27df4-124">이 변경은 함수의 범위에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-124">This change only affects the scope of the function.</span></span> <span data-ttu-id="27df4-125">값은 함수 외부에 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-125">The value is not affected outside the function.</span></span>

> [!NOTE]
> <span data-ttu-id="27df4-126">의 값 `$DebugPreference` 이 **Inquire** 인 경우 PowerShell은 실행을 계속할지 여부를 묻는 실행을 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-126">When the value of `$DebugPreference` is **Inquire** , PowerShell halts execution to ask if execution should continue.</span></span>

<span data-ttu-id="27df4-127">**Debug** 일반 매개 변수에 대 한 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="27df4-127">For more information about the **Debug** common parameter, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="27df4-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="27df4-128">PARAMETERS</span></span>

### <span data-ttu-id="27df4-129">-메시지</span><span class="sxs-lookup"><span data-stu-id="27df4-129">-Message</span></span>

<span data-ttu-id="27df4-130">콘솔에 보낼 디버그 메시지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-130">Specifies the debug message to send to the console.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="27df4-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="27df4-131">CommonParameters</span></span>

<span data-ttu-id="27df4-132">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="27df4-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="27df4-133">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="27df4-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="27df4-134">입력</span><span class="sxs-lookup"><span data-stu-id="27df4-134">INPUTS</span></span>

### <span data-ttu-id="27df4-135">System.String</span><span class="sxs-lookup"><span data-stu-id="27df4-135">System.String</span></span>

<span data-ttu-id="27df4-136">디버그 메시지를 포함 하는 문자열을로 파이프 할 수 있습니다 `Write-Debug` .</span><span class="sxs-lookup"><span data-stu-id="27df4-136">You can pipe a string that contains a debug message to `Write-Debug`.</span></span>

## <span data-ttu-id="27df4-137">출력</span><span class="sxs-lookup"><span data-stu-id="27df4-137">OUTPUTS</span></span>

### <span data-ttu-id="27df4-138">없음</span><span class="sxs-lookup"><span data-stu-id="27df4-138">None</span></span>

<span data-ttu-id="27df4-139">`Write-Debug` 는 디버그 스트림에만 씁니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-139">`Write-Debug` only writes to the debug stream.</span></span> <span data-ttu-id="27df4-140">파이프라인에 개체를 쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27df4-140">It does not write any objects to the pipeline.</span></span>

## <span data-ttu-id="27df4-141">참고</span><span class="sxs-lookup"><span data-stu-id="27df4-141">NOTES</span></span>

## <span data-ttu-id="27df4-142">관련 링크</span><span class="sxs-lookup"><span data-stu-id="27df4-142">RELATED LINKS</span></span>

[<span data-ttu-id="27df4-143">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="27df4-143">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="27df4-144">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="27df4-144">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="27df4-145">쓰기 오류</span><span class="sxs-lookup"><span data-stu-id="27df4-145">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="27df4-146">Write-Host</span><span class="sxs-lookup"><span data-stu-id="27df4-146">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="27df4-147">Write-Output</span><span class="sxs-lookup"><span data-stu-id="27df4-147">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="27df4-148">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="27df4-148">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="27df4-149">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="27df4-149">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="27df4-150">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="27df4-150">Write-Warning</span></span>](Write-Warning.md)

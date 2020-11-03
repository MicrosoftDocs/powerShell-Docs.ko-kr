---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-warning?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Warning
ms.openlocfilehash: dde8e497159e3e9a7bf63010bc12566d68d8de0f
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224433"
---
# <span data-ttu-id="c1422-103">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="c1422-103">Write-Warning</span></span>

## <span data-ttu-id="c1422-104">개요</span><span class="sxs-lookup"><span data-stu-id="c1422-104">SYNOPSIS</span></span>
<span data-ttu-id="c1422-105">경고 메시지를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-105">Writes a warning message.</span></span>

## <span data-ttu-id="c1422-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c1422-106">SYNTAX</span></span>

```
Write-Warning [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="c1422-107">설명</span><span class="sxs-lookup"><span data-stu-id="c1422-107">DESCRIPTION</span></span>

<span data-ttu-id="c1422-108">`Write-Warning`Cmdlet은 PowerShell 호스트에 경고 메시지를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-108">The `Write-Warning` cmdlet writes a warning message to the PowerShell host.</span></span> <span data-ttu-id="c1422-109">경고에 대 한 응답은 사용자의 `$WarningPreference` 변수 값 및 **WarningAction** 일반 매개 변수 사용에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-109">The response to the warning depends on the value of the user's `$WarningPreference` variable and the use of the **WarningAction** common parameter.</span></span>

## <span data-ttu-id="c1422-110">예제</span><span class="sxs-lookup"><span data-stu-id="c1422-110">EXAMPLES</span></span>

### <span data-ttu-id="c1422-111">예제 1: 경고 메시지 작성</span><span class="sxs-lookup"><span data-stu-id="c1422-111">Example 1: Write a warning message</span></span>

<span data-ttu-id="c1422-112">이 명령은 "경고: 테스트 경고만입니다." 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-112">This command displays the message "WARNING: This is only a test warning."</span></span>

```powershell
Write-Warning "This is only a test warning."
```

### <span data-ttu-id="c1422-113">예제 2: Write-Warning에 문자열 전달</span><span class="sxs-lookup"><span data-stu-id="c1422-113">Example 2: Pass a string to Write-Warning</span></span>

<span data-ttu-id="c1422-114">이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 에 문자열을 보낼 수 있음을 보여 줍니다 `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="c1422-114">This command shows that you can use a pipeline operator (`|`) to send a string to `Write-Warning`.</span></span>
<span data-ttu-id="c1422-115">이 명령에 표시 된 대로 문자열을 변수에 저장 하거나로 직접 파이프 할 수 있습니다 `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="c1422-115">You can save the string in a variable, as shown in this command, or pipe the string directly to `Write-Warning`.</span></span>

```powershell
$w = "This is only a test warning."
$w | Write-Warning
```

### <span data-ttu-id="c1422-116">예 3: $WarningPreference 변수를 설정 하 고 경고를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-116">Example 3: Set the $WarningPreference variable and write a warning</span></span>

<span data-ttu-id="c1422-117">이 예에서는 명령에 대 한 변수 값의 영향을 보여 줍니다 `$WarningPreference` `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="c1422-117">This example shows the effect of the value of the `$WarningPreference` variable on a `Write-Warning` command.</span></span>

```powershell
PS> $WarningPreference
Continue
PS> Write-Warning "This is only a test warning."
This is only a test warning.
PS> $WarningPreference = "SilentlyContinue"
PS> Write-Warning "This is only a test warning."
PS> $WarningPreference = "Stop"
PS> Write-Warning "This is only a test warning."
WARNING: This is only a test message.
Write-Warning : Command execution stopped because the shell variable "WarningPreference" is set to Stop.
At line:1 char:14
     + Write-Warning <<<<  "This is only a test message."
```

<span data-ttu-id="c1422-118">첫 번째 명령은 변수의 기본값을 표시 합니다 `$WarningPreference` `Continue` .</span><span class="sxs-lookup"><span data-stu-id="c1422-118">The first command displays the default value of the `$WarningPreference` variable, which is `Continue`.</span></span> <span data-ttu-id="c1422-119">따라서 경고를 작성할 때 경고 메시지가 표시되고 실행이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-119">As a result, when you write a warning, the warning message is displayed and execution continues.</span></span>

<span data-ttu-id="c1422-120">변수의 값을 변경 하면 `$WarningPreference` `Write-Warning` 명령의 영향이 다시 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-120">When you change the value of the `$WarningPreference` variable, the effect of the `Write-Warning` command changes again.</span></span> <span data-ttu-id="c1422-121">값이 이면 `SilentlyContinue` 경고를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-121">A value of `SilentlyContinue` suppresses the warning.</span></span> <span data-ttu-id="c1422-122">값은 `Stop` 경고를 표시 한 다음 명령 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-122">A value of `Stop` displays the warning and then stops execution of the command.</span></span>

<span data-ttu-id="c1422-123">변수에 대 한 자세한 내용은 `$WarningPreference` [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c1422-123">For more information about the `$WarningPreference` variable, see [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="c1422-124">예 4: WarningAction 매개 변수를 설정 하 고 경고를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-124">Example 4: Set the WarningAction parameter and write a warning</span></span>

<span data-ttu-id="c1422-125">이 예에서는 명령에 **WarningAction** common 매개 변수의 효과를 보여 줍니다 `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="c1422-125">This example shows the effect of the **WarningAction** common parameter on a `Write-Warning` command.</span></span> <span data-ttu-id="c1422-126">**WarningAction** 일반 매개 변수를 cmdlet과 함께 사용 하 여 PowerShell이 해당 명령으로 인해 발생 하는 경고에 응답 하는 방법을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-126">You can use the **WarningAction** common parameter with any cmdlet to determine how PowerShell responds to warnings resulting from that command.</span></span> <span data-ttu-id="c1422-127">**WarningAction** 일반 매개 변수는 `$WarningPreference` 특정 명령에 대해서만 값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-127">The **WarningAction** common parameter overrides the value of the `$WarningPreference` only for that particular command.</span></span>

```powershell
PS> Write-Warning "This is only a test warning." -WarningAction Inquire
WARNING: This is only a test warning.
Confirm
Continue with this operation?
 [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="c1422-128">이 명령은 cmdlet을 사용 하 여 `Write-Warning` 경고를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-128">This command uses the `Write-Warning` cmdlet to display a warning.</span></span> <span data-ttu-id="c1422-129">**WarningAction** 일반 매개 변수는 명령에 경고가 표시 될 때 시스템에서 사용자에 게 메시지를 표시 하도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-129">The **WarningAction** common parameter with a value of Inquire directs the system to prompt the user when the command displays a warning.</span></span>

<span data-ttu-id="c1422-130">**WarningAction** 일반 매개 변수에 대 한 자세한 내용은 [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c1422-130">For more information about the **WarningAction** common parameter, see [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c1422-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c1422-131">PARAMETERS</span></span>

### <span data-ttu-id="c1422-132">-메시지</span><span class="sxs-lookup"><span data-stu-id="c1422-132">-Message</span></span>
<span data-ttu-id="c1422-133">경고 메시지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-133">Specifies the warning message.</span></span>

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

### <span data-ttu-id="c1422-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c1422-134">CommonParameters</span></span>

<span data-ttu-id="c1422-135">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c1422-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c1422-136">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1422-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c1422-137">입력</span><span class="sxs-lookup"><span data-stu-id="c1422-137">INPUTS</span></span>

### <span data-ttu-id="c1422-138">System.String</span><span class="sxs-lookup"><span data-stu-id="c1422-138">System.String</span></span>

<span data-ttu-id="c1422-139">경고가 포함 된 문자열을로 파이프 할 수 있습니다 `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="c1422-139">You can pipe a string that contains the warning to `Write-Warning`.</span></span>

## <span data-ttu-id="c1422-140">출력</span><span class="sxs-lookup"><span data-stu-id="c1422-140">OUTPUTS</span></span>

### <span data-ttu-id="c1422-141">없음</span><span class="sxs-lookup"><span data-stu-id="c1422-141">None</span></span>

<span data-ttu-id="c1422-142">`Write-Warning` 경고 스트림에만 씁니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-142">`Write-Warning` writes only to the warning stream.</span></span> <span data-ttu-id="c1422-143">다른 출력은 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-143">It does not generate any other output.</span></span>

## <span data-ttu-id="c1422-144">참고</span><span class="sxs-lookup"><span data-stu-id="c1422-144">NOTES</span></span>

<span data-ttu-id="c1422-145">변수의 기본값은 경고를 `$WarningPreference` 표시 하 `Continue` 고 명령을 계속 실행 하는입니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-145">The default value for the `$WarningPreference` variable is `Continue`, which displays the warning and then continues executing the command.</span></span> <span data-ttu-id="c1422-146">와 같은 기본 설정 변수에 대 한 유효한 값을 확인 하려면 `$WarningPreference` "abc"와 같은 임의의 문자 문자열로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-146">To determine valid values for a preference variable such as `$WarningPreference`, set it to a string of random characters, such as "abc".</span></span> <span data-ttu-id="c1422-147">결과 오류 메시지에는 유효한 값이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1422-147">The resulting error message lists the valid values.</span></span>

## <span data-ttu-id="c1422-148">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c1422-148">RELATED LINKS</span></span>

[<span data-ttu-id="c1422-149">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="c1422-149">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="c1422-150">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="c1422-150">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="c1422-151">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="c1422-151">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="c1422-152">쓰기 오류</span><span class="sxs-lookup"><span data-stu-id="c1422-152">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="c1422-153">Write-Host</span><span class="sxs-lookup"><span data-stu-id="c1422-153">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="c1422-154">Write-Information</span><span class="sxs-lookup"><span data-stu-id="c1422-154">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="c1422-155">Write-Output</span><span class="sxs-lookup"><span data-stu-id="c1422-155">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="c1422-156">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="c1422-156">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="c1422-157">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="c1422-157">Write-Verbose</span></span>](Write-Verbose.md)

---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-information?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Information
ms.openlocfilehash: f15902c1c6c298dd02db3edf061d56e1446ecb1f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602810"
---
# <span data-ttu-id="549ff-102">Write-Information</span><span class="sxs-lookup"><span data-stu-id="549ff-102">Write-Information</span></span>

## <span data-ttu-id="549ff-103">개요</span><span class="sxs-lookup"><span data-stu-id="549ff-103">SYNOPSIS</span></span>

<span data-ttu-id="549ff-104">PowerShell에서 명령에 대 한 정보 스트림 데이터를 처리 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-104">Specifies how PowerShell handles information stream data for a command.</span></span>

## <span data-ttu-id="549ff-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="549ff-105">SYNTAX</span></span>

```
Write-Information [-MessageData] <Object> [[-Tags] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="549ff-106">설명</span><span class="sxs-lookup"><span data-stu-id="549ff-106">DESCRIPTION</span></span>

<span data-ttu-id="549ff-107">`Write-Information`Cmdlet은 PowerShell에서 명령에 대 한 정보 스트림 데이터를 처리 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-107">The `Write-Information` cmdlet specifies how PowerShell handles information stream data for a command.</span></span>

<span data-ttu-id="549ff-108">Windows PowerShell 5.0에는 새로운 구조화 된 정보 스트림이 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-108">Windows PowerShell 5.0 introduces a new, structured information stream.</span></span> <span data-ttu-id="549ff-109">이 스트림을 사용 하 여 스크립트와 해당 호출자 또는 호스트 응용 프로그램 간에 구조화 된 데이터를 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-109">You can use this stream to transmit structured data between a script and its callers or the host application.</span></span>
<span data-ttu-id="549ff-110">`Write-Information` 스트림에 정보 메시지를 추가 하 고 PowerShell에서 명령에 대 한 정보 스트림 데이터를 처리 하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-110">`Write-Information` lets you add an informational message to the stream, and specify how PowerShell handles information stream data for a command.</span></span> <span data-ttu-id="549ff-111">정보 스트림은 `PowerShell.Streams` , 작업 및 예약 된 작업에 대해서도 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-111">Information streams also work for `PowerShell.Streams`, jobs, and scheduled tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="549ff-112">정보 스트림은 메시지에 "[Stream Name]:"을 접두사로 추가 하는 표준 규칙을 따르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-112">The information stream does not follow the standard convention of prefixing its messages with "[Stream Name]:".</span></span> <span data-ttu-id="549ff-113">이는 간단 하 고 시각적으로 청결도 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-113">This was intended for brevity and visual cleanliness.</span></span>

<span data-ttu-id="549ff-114">`$InformationPreference`기본 설정 변수 값은 사용자가 제공 하는 메시지를 `Write-Information` 스크립트 작업의 예상 지점에 표시할지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-114">The `$InformationPreference` preference variable value determines whether the message you provide to `Write-Information` is displayed at the expected point in a script's operation.</span></span> <span data-ttu-id="549ff-115">이 변수의 기본값은 이므로 `SilentlyContinue` 기본적으로 정보 메시지는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-115">Because the default value of this variable is `SilentlyContinue`, by default, informational messages are not shown.</span></span> <span data-ttu-id="549ff-116">의 값을 변경 하지 않으려면 `$InformationPreference` `InformationAction` 일반 매개 변수를 명령에 추가 하 여 해당 값을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-116">If you don't want to change the value of `$InformationPreference`, you can override its value by adding the `InformationAction` common parameter to your command.</span></span> <span data-ttu-id="549ff-117">자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) 및 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="549ff-117">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) and [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="549ff-118">Windows PowerShell 5.0부터 `Write-Host` 은이에 대 한 래퍼로,를 사용 하 여 `Write-Information` 출력을 `Write-Host` 정보 스트림으로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-118">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="549ff-119">이를 통해 이전 버전과의 호환성을 유지 하면서 **를 사용** 하 여 작성 된 데이터를 **캡처하거나** 제거할 수 있습니다 `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="549ff-119">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span> <span data-ttu-id="549ff-120">자세한 내용은 [쓰기 호스트](Write-Host.md) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="549ff-120">For more information see [Write-Host](Write-Host.md)</span></span>

<span data-ttu-id="549ff-121">`Write-Information` 는 또한 PowerShell 5.x에서 지원 되는 워크플로 활동입니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-121">`Write-Information` is also a supported workflow activity in PowerShell 5.x.</span></span>

## <span data-ttu-id="549ff-122">예제</span><span class="sxs-lookup"><span data-stu-id="549ff-122">EXAMPLES</span></span>

### <span data-ttu-id="549ff-123">예제 1: Get 결과에 대 한 정보 작성</span><span class="sxs-lookup"><span data-stu-id="549ff-123">Example 1: Write information for Get- results</span></span>

<span data-ttu-id="549ff-124">이 예제에서는 `Get-WindowsFeature` ' p '로 시작 하는 이름 값이 있는 모든 기능을 찾기 위해 명령을 실행 한 후 정보 메시지 "기능을 가져왔습니다!"를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-124">In this example, you show an informational message, "Got your features!", after running the `Get-WindowsFeature` command to find all features that have a Name value that starts with 'p'.</span></span>
<span data-ttu-id="549ff-125">`$InformationPreference`변수가 여전히 기본값인로 설정 되어 있기 때문에 `SilentlyContinue` `InformationAction` 매개 변수를 추가 하 여 값을 재정의 하 `$InformationPreference` 고 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-125">Because the `$InformationPreference` variable is still set to its default, `SilentlyContinue`, you add the `InformationAction` parameter to override the `$InformationPreference` value, and show the message.</span></span> <span data-ttu-id="549ff-126">`InformationAction`값은 Continue입니다. 즉, 메시지가 표시 되지만 스크립트나 명령이 아직 완료 되지 않았으면 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-126">The `InformationAction` value is Continue, which means that your message is shown, but the script or command continues, if it is not yet finished.</span></span>

```powershell
Get-WindowsFeature -Name p*
Write-Information -MessageData "Got your features!" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
Got your features!
```

### <span data-ttu-id="549ff-127">예제 2: 정보 작성 및 태그</span><span class="sxs-lookup"><span data-stu-id="549ff-127">Example 2: Write information and tag it</span></span>

<span data-ttu-id="549ff-128">이 예제에서는 `Write-Information` 를 사용 하 여 사용자가 현재 명령 실행이 완료 된 후 다른 명령을 실행 해야 한다는 사실을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-128">In this example, you use `Write-Information` to let users know they'll need to run another command after they're done running the current command.</span></span> <span data-ttu-id="549ff-129">이 예에서는 정보 메시지에 태그 지침을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-129">The example adds the tag Instructions to the informational message.</span></span> <span data-ttu-id="549ff-130">이 명령을 실행 한 후 정보 스트림을 검색 하 여 표시 되는 메시지에 대 한 지침을 검색 하면 여기에 지정 된 메시지가 결과 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-130">After running this command, if you search the information stream for messages tagged Instructions, the message specified here would be among the results.</span></span>

```powershell
$message = "To filter your results for PowerShell, pipe your results to the Where-Object cmdlet."
Get-WindowsFeature -Name p*
Write-Information -MessageData $message -Tags "Instructions" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
To filter your results for PowerShell, pipe your results to the Where-Object cmdlet.
```

### <span data-ttu-id="549ff-131">예제 3: 파일에 정보 쓰기</span><span class="sxs-lookup"><span data-stu-id="549ff-131">Example 3: Write information to a file</span></span>

<span data-ttu-id="549ff-132">이 예제에서는 `Info.txt` 코드를 사용 하 여 함수의 정보 스트림을로 리디렉션합니다 `6>` .</span><span class="sxs-lookup"><span data-stu-id="549ff-132">In this example, you redirect the information stream in the function to a `Info.txt` using the code `6>`.</span></span> <span data-ttu-id="549ff-133">파일을 열면 `Info.txt` "여기 서 이동 했습니다." 라는 텍스트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-133">When you open the `Info.txt` file, you see the text, "Here you go."</span></span>

```powershell
function Test-Info
{
    Get-Process P*
    Write-Information "Here you go"
}
Test-Info 6> Info.txt
```

### <span data-ttu-id="549ff-134">예제 4: 개체를 전달 하 여 정보 쓰기</span><span class="sxs-lookup"><span data-stu-id="549ff-134">Example 4: Pass object to write information</span></span>

<span data-ttu-id="549ff-135">이 예제에서는를 사용 하 여 `Write-Information` `Get-Process` 여러 파이프라인을 통과 하는 개체 출력에서 상위 10 개의 최고 CPU 사용률 프로세스를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-135">In this example, you can use `Write-Information` to write the top 10 highest CPU utilization processes from the `Get-Process` object output that has passes through multiple pipelines.</span></span>

```powershell
Get-Process | Sort-Object CPU -Descending |
    Select-Object Id, ProcessName, CPU -First 10 |
        Write-Information -InformationAction Continue
```

```Output
@{Id=12692; ProcessName=chrome; CPU=39431.296875}
@{Id=21292; ProcessName=OUTLOOK; CPU=23991.875}
@{Id=10548; ProcessName=CefSharp.BrowserSubprocess; CPU=20546.203125}
@{Id=312848; ProcessName=Taskmgr; CPU=13173.1875}
@{Id=10848; ProcessName=SnapClient; CPU=7014.265625}
@{Id=9760; ProcessName=Receiver; CPU=6792.359375}
@{Id=12040; ProcessName=Teams; CPU=5605.578125}
@{Id=498388; ProcessName=chrome; CPU=3062.453125}
@{Id=6900; ProcessName=chrome; CPU=2546.9375}
@{Id=9044; ProcessName=explorer; CPU=2358.765625}
```

## <span data-ttu-id="549ff-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="549ff-136">PARAMETERS</span></span>

### <span data-ttu-id="549ff-137">-MessageData</span><span class="sxs-lookup"><span data-stu-id="549ff-137">-MessageData</span></span>

<span data-ttu-id="549ff-138">스크립트나 명령을 실행할 때 사용자에 게 표시 하려는 정보 메시지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-138">Specifies an informational message that you want to display to users as they run a script or command.</span></span> <span data-ttu-id="549ff-139">최상의 결과를 위해 정보 메시지를 큰따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-139">For best results, enclose the informational message in quotation marks.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="549ff-140">-태그</span><span class="sxs-lookup"><span data-stu-id="549ff-140">-Tags</span></span>

<span data-ttu-id="549ff-141">를 사용 하 여 정보 스트림에 추가한 메시지를 정렬 하 고 필터링 하는 데 사용할 수 있는 간단한 문자열을 지정 `Write-Information` 합니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-141">Specifies a simple string that you can use to sort and filter messages that you have added to the information stream with `Write-Information`.</span></span> <span data-ttu-id="549ff-142">이 매개 변수는의 **Tags** 매개 변수와 유사 하 게 작동 `New-ModuleManifest` 합니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-142">This parameter works similarly to the **Tags** parameter in `New-ModuleManifest`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="549ff-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="549ff-143">CommonParameters</span></span>

<span data-ttu-id="549ff-144">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="549ff-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="549ff-145">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="549ff-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="549ff-146">입력</span><span class="sxs-lookup"><span data-stu-id="549ff-146">INPUTS</span></span>

### <span data-ttu-id="549ff-147">System.Object</span><span class="sxs-lookup"><span data-stu-id="549ff-147">System.Object</span></span>

<span data-ttu-id="549ff-148">`Write-Information` 파이프 된 개체가 정보 스트림으로 전달 되도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="549ff-148">`Write-Information` accepts piped objects to pass to the information stream.</span></span>

## <span data-ttu-id="549ff-149">출력</span><span class="sxs-lookup"><span data-stu-id="549ff-149">OUTPUTS</span></span>

### <span data-ttu-id="549ff-150">System.web. InformationRecord</span><span class="sxs-lookup"><span data-stu-id="549ff-150">System.Management.Automation.InformationRecord</span></span>

## <span data-ttu-id="549ff-151">참고</span><span class="sxs-lookup"><span data-stu-id="549ff-151">NOTES</span></span>

## <span data-ttu-id="549ff-152">관련 링크</span><span class="sxs-lookup"><span data-stu-id="549ff-152">RELATED LINKS</span></span>

[<span data-ttu-id="549ff-153">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="549ff-153">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="549ff-154">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="549ff-154">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="549ff-155">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="549ff-155">about_CommonParameters</span></span>](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)

[<span data-ttu-id="549ff-156">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="549ff-156">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="549ff-157">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="549ff-157">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="549ff-158">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="549ff-158">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="549ff-159">Write-Host</span><span class="sxs-lookup"><span data-stu-id="549ff-159">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="549ff-160">Write-Information</span><span class="sxs-lookup"><span data-stu-id="549ff-160">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="549ff-161">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="549ff-161">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="549ff-162">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="549ff-162">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="549ff-163">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="549ff-163">Write-Warning</span></span>](Write-Warning.md)

[<span data-ttu-id="549ff-164">Write-Output</span><span class="sxs-lookup"><span data-stu-id="549ff-164">Write-Output</span></span>](Write-Output.md)

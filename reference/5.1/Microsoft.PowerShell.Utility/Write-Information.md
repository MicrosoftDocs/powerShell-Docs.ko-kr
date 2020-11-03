---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-information?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Information
ms.openlocfilehash: e0f28393c95e2c0703c489d4691edcf883b4cb05
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224298"
---
# <span data-ttu-id="63ce5-103">Write-Information</span><span class="sxs-lookup"><span data-stu-id="63ce5-103">Write-Information</span></span>

## <span data-ttu-id="63ce5-104">개요</span><span class="sxs-lookup"><span data-stu-id="63ce5-104">SYNOPSIS</span></span>

<span data-ttu-id="63ce5-105">PowerShell에서 명령에 대 한 정보 스트림 데이터를 처리 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-105">Specifies how PowerShell handles information stream data for a command.</span></span>

## <span data-ttu-id="63ce5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="63ce5-106">SYNTAX</span></span>

```
Write-Information [-MessageData] <Object> [[-Tags] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="63ce5-107">설명</span><span class="sxs-lookup"><span data-stu-id="63ce5-107">DESCRIPTION</span></span>

<span data-ttu-id="63ce5-108">`Write-Information`Cmdlet은 PowerShell에서 명령에 대 한 정보 스트림 데이터를 처리 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-108">The `Write-Information` cmdlet specifies how PowerShell handles information stream data for a command.</span></span>

<span data-ttu-id="63ce5-109">Windows PowerShell 5.0에는 새로운 구조화 된 정보 스트림이 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-109">Windows PowerShell 5.0 introduces a new, structured information stream.</span></span> <span data-ttu-id="63ce5-110">이 스트림을 사용 하 여 스크립트와 해당 호출자 또는 호스트 응용 프로그램 간에 구조화 된 데이터를 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-110">You can use this stream to transmit structured data between a script and its callers or the host application.</span></span>
<span data-ttu-id="63ce5-111">`Write-Information` 스트림에 정보 메시지를 추가 하 고 PowerShell에서 명령에 대 한 정보 스트림 데이터를 처리 하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-111">`Write-Information` lets you add an informational message to the stream, and specify how PowerShell handles information stream data for a command.</span></span> <span data-ttu-id="63ce5-112">정보 스트림은 `PowerShell.Streams` , 작업 및 예약 된 작업에 대해서도 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-112">Information streams also work for `PowerShell.Streams`, jobs, and scheduled tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="63ce5-113">정보 스트림은 메시지에 "[Stream Name]:"을 접두사로 추가 하는 표준 규칙을 따르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-113">The information stream does not follow the standard convention of prefixing its messages with "[Stream Name]:".</span></span> <span data-ttu-id="63ce5-114">이는 간단 하 고 시각적으로 청결도 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-114">This was intended for brevity and visual cleanliness.</span></span>

<span data-ttu-id="63ce5-115">`$InformationPreference`기본 설정 변수 값은 사용자가 제공 하는 메시지를 `Write-Information` 스크립트 작업의 예상 지점에 표시할지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-115">The `$InformationPreference` preference variable value determines whether the message you provide to `Write-Information` is displayed at the expected point in a script's operation.</span></span> <span data-ttu-id="63ce5-116">이 변수의 기본값은 이므로 `SilentlyContinue` 기본적으로 정보 메시지는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-116">Because the default value of this variable is `SilentlyContinue`, by default, informational messages are not shown.</span></span> <span data-ttu-id="63ce5-117">의 값을 변경 하지 않으려면 `$InformationPreference` `InformationAction` 일반 매개 변수를 명령에 추가 하 여 해당 값을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-117">If you don't want to change the value of `$InformationPreference`, you can override its value by adding the `InformationAction` common parameter to your command.</span></span> <span data-ttu-id="63ce5-118">자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) 및 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="63ce5-118">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) and [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="63ce5-119">Windows PowerShell 5.0부터 `Write-Host` 은이에 대 한 래퍼로,를 사용 하 여 `Write-Information` 출력을 `Write-Host` 정보 스트림으로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-119">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="63ce5-120">이를 통해 이전 버전과의 호환성을 유지 하면서 **를 사용** 하 여 작성 된 데이터를 **캡처하거나** 제거할 수 있습니다 `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="63ce5-120">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span> <span data-ttu-id="63ce5-121">자세한 내용은 [쓰기 호스트](Write-Host.md) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="63ce5-121">For more information see [Write-Host](Write-Host.md)</span></span>

<span data-ttu-id="63ce5-122">`Write-Information` 는 또한 PowerShell 5.x에서 지원 되는 워크플로 활동입니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-122">`Write-Information` is also a supported workflow activity in PowerShell 5.x.</span></span>

## <span data-ttu-id="63ce5-123">예제</span><span class="sxs-lookup"><span data-stu-id="63ce5-123">EXAMPLES</span></span>

### <span data-ttu-id="63ce5-124">예제 1: Get 결과에 대 한 정보 작성</span><span class="sxs-lookup"><span data-stu-id="63ce5-124">Example 1: Write information for Get- results</span></span>

<span data-ttu-id="63ce5-125">이 예제에서는 `Get-WindowsFeature` ' p '로 시작 하는 이름 값이 있는 모든 기능을 찾기 위해 명령을 실행 한 후 정보 메시지 "기능을 가져왔습니다!"를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-125">In this example, you show an informational message, "Got your features!", after running the `Get-WindowsFeature` command to find all features that have a Name value that starts with 'p'.</span></span>
<span data-ttu-id="63ce5-126">`$InformationPreference`변수가 여전히 기본값인로 설정 되어 있기 때문에 `SilentlyContinue` `InformationAction` 매개 변수를 추가 하 여 값을 재정의 하 `$InformationPreference` 고 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-126">Because the `$InformationPreference` variable is still set to its default, `SilentlyContinue`, you add the `InformationAction` parameter to override the `$InformationPreference` value, and show the message.</span></span> <span data-ttu-id="63ce5-127">`InformationAction`값은 Continue입니다. 즉, 메시지가 표시 되지만 스크립트나 명령이 아직 완료 되지 않았으면 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-127">The `InformationAction` value is Continue, which means that your message is shown, but the script or command continues, if it is not yet finished.</span></span>

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

### <span data-ttu-id="63ce5-128">예제 2: 정보 작성 및 태그</span><span class="sxs-lookup"><span data-stu-id="63ce5-128">Example 2: Write information and tag it</span></span>

<span data-ttu-id="63ce5-129">이 예제에서는 `Write-Information` 를 사용 하 여 사용자가 현재 명령 실행이 완료 된 후 다른 명령을 실행 해야 한다는 사실을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-129">In this example, you use `Write-Information` to let users know they'll need to run another command after they're done running the current command.</span></span> <span data-ttu-id="63ce5-130">이 예에서는 정보 메시지에 태그 지침을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-130">The example adds the tag Instructions to the informational message.</span></span> <span data-ttu-id="63ce5-131">이 명령을 실행 한 후 정보 스트림을 검색 하 여 표시 되는 메시지에 대 한 지침을 검색 하면 여기에 지정 된 메시지가 결과 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-131">After running this command, if you search the information stream for messages tagged Instructions, the message specified here would be among the results.</span></span>

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

### <span data-ttu-id="63ce5-132">예제 3: 파일에 정보 쓰기</span><span class="sxs-lookup"><span data-stu-id="63ce5-132">Example 3: Write information to a file</span></span>

```powershell
function Test-Info
{
    Get-Process P*
    Write-Information "Here you go"
}
Test-Info 6> Info.txt
```

## <span data-ttu-id="63ce5-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="63ce5-133">PARAMETERS</span></span>

### <span data-ttu-id="63ce5-134">-MessageData</span><span class="sxs-lookup"><span data-stu-id="63ce5-134">-MessageData</span></span>

<span data-ttu-id="63ce5-135">스크립트나 명령을 실행할 때 사용자에 게 표시 하려는 정보 메시지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-135">Specifies an informational message that you want to display to users as they run a script or command.</span></span> <span data-ttu-id="63ce5-136">최상의 결과를 위해 정보 메시지를 큰따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-136">For best results, enclose the informational message in quotation marks.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63ce5-137">-태그</span><span class="sxs-lookup"><span data-stu-id="63ce5-137">-Tags</span></span>

<span data-ttu-id="63ce5-138">를 사용 하 여 정보 스트림에 추가한 메시지를 정렬 하 고 필터링 하는 데 사용할 수 있는 간단한 문자열을 지정 `Write-Information` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-138">Specifies a simple string that you can use to sort and filter messages that you have added to the information stream with `Write-Information`.</span></span> <span data-ttu-id="63ce5-139">이 매개 변수는의 **Tags** 매개 변수와 유사 하 게 작동 `New-ModuleManifest` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-139">This parameter works similarly to the **Tags** parameter in `New-ModuleManifest`.</span></span>

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

### <span data-ttu-id="63ce5-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="63ce5-140">CommonParameters</span></span>

<span data-ttu-id="63ce5-141">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="63ce5-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="63ce5-142">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63ce5-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="63ce5-143">입력</span><span class="sxs-lookup"><span data-stu-id="63ce5-143">INPUTS</span></span>

### <span data-ttu-id="63ce5-144">None</span><span class="sxs-lookup"><span data-stu-id="63ce5-144">None</span></span>

<span data-ttu-id="63ce5-145">`Write-Information` 파이프 입력을 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63ce5-145">`Write-Information` does not accept piped input.</span></span>

## <span data-ttu-id="63ce5-146">출력</span><span class="sxs-lookup"><span data-stu-id="63ce5-146">OUTPUTS</span></span>

### <span data-ttu-id="63ce5-147">System.web. InformationRecord</span><span class="sxs-lookup"><span data-stu-id="63ce5-147">System.Management.Automation.InformationRecord</span></span>

## <span data-ttu-id="63ce5-148">참고</span><span class="sxs-lookup"><span data-stu-id="63ce5-148">NOTES</span></span>

## <span data-ttu-id="63ce5-149">관련 링크</span><span class="sxs-lookup"><span data-stu-id="63ce5-149">RELATED LINKS</span></span>

[<span data-ttu-id="63ce5-150">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="63ce5-150">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="63ce5-151">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="63ce5-151">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="63ce5-152">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="63ce5-152">about_CommonParameters</span></span>](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)

[<span data-ttu-id="63ce5-153">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="63ce5-153">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="63ce5-154">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="63ce5-154">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="63ce5-155">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="63ce5-155">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="63ce5-156">Write-Host</span><span class="sxs-lookup"><span data-stu-id="63ce5-156">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="63ce5-157">Write-Information</span><span class="sxs-lookup"><span data-stu-id="63ce5-157">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="63ce5-158">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="63ce5-158">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="63ce5-159">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="63ce5-159">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="63ce5-160">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="63ce5-160">Write-Warning</span></span>](Write-Warning.md)

[<span data-ttu-id="63ce5-161">Write-Output</span><span class="sxs-lookup"><span data-stu-id="63ce5-161">Write-Output</span></span>](Write-Output.md)

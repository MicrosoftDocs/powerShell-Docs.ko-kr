---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: e16e002ab9e803900712542c329723f6a44a880f
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224290"
---
# <span data-ttu-id="b76d9-103">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="b76d9-103">Write-Verbose</span></span>

## <span data-ttu-id="b76d9-104">개요</span><span class="sxs-lookup"><span data-stu-id="b76d9-104">SYNOPSIS</span></span>
<span data-ttu-id="b76d9-105">자세한 정보 메시지 스트림에 텍스트를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-105">Writes text to the verbose message stream.</span></span>

## <span data-ttu-id="b76d9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b76d9-106">SYNTAX</span></span>

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="b76d9-107">설명</span><span class="sxs-lookup"><span data-stu-id="b76d9-107">DESCRIPTION</span></span>

<span data-ttu-id="b76d9-108">`Write-Verbose`Cmdlet은 PowerShell의 자세한 정보 메시지 스트림에 텍스트를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-108">The `Write-Verbose` cmdlet writes text to the verbose message stream in PowerShell.</span></span> <span data-ttu-id="b76d9-109">일반적으로 자세한 정보 메시지 스트림은 명령 처리에 대 한 자세한 정보를 제공 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-109">Typically, the verbose message stream is used to deliver more in depth information about command processing.</span></span>

<span data-ttu-id="b76d9-110">기본적으로 자세한 정보 메시지 스트림은 표시 되지 않지만, 변수 값을 변경 `$VerbosePreference` 하거나 임의의 명령에서 **verbose** 일반 매개 변수를 사용 하 여 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-110">By default, the verbose message stream is not displayed, but you can display it by changing the value of the `$VerbosePreference` variable or using the **Verbose** common parameter in any command.</span></span>

## <span data-ttu-id="b76d9-111">예제</span><span class="sxs-lookup"><span data-stu-id="b76d9-111">EXAMPLES</span></span>

### <span data-ttu-id="b76d9-112">예제 1: 상태 메시지 작성</span><span class="sxs-lookup"><span data-stu-id="b76d9-112">Example 1: Write a status message</span></span>

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

<span data-ttu-id="b76d9-113">이러한 명령은 cmdlet을 사용 `Write-Verbose` 하 여 상태 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-113">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="b76d9-114">이 메시지는 기본적으로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-114">By default, the message is not displayed.</span></span>

<span data-ttu-id="b76d9-115">두 번째 명령은 **verbose** 일반 매개 변수를 사용 합니다 .이 매개 변수는 변수의 값에 관계 없이 자세한 정보 메시지를 표시 합니다 `$VerbosePreference` .</span><span class="sxs-lookup"><span data-stu-id="b76d9-115">The second command uses the **Verbose** common parameter, which displays any verbose messages, regardless of the value of the `$VerbosePreference` variable.</span></span>

### <span data-ttu-id="b76d9-116">예제 2: $VerbosePreference 설정 및 상태 메시지 작성</span><span class="sxs-lookup"><span data-stu-id="b76d9-116">Example 2: Set $VerbosePreference and write a status message</span></span>

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

<span data-ttu-id="b76d9-117">이러한 명령은 cmdlet을 사용 `Write-Verbose` 하 여 상태 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-117">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="b76d9-118">이 메시지는 기본적으로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-118">By default, the message is not displayed.</span></span>

<span data-ttu-id="b76d9-119">첫 번째 명령은 기본 설정 변수에 Continue 값을 할당 합니다 `$VerbosePreference` .</span><span class="sxs-lookup"><span data-stu-id="b76d9-119">The first command assigns a value of Continue to the `$VerbosePreference` preference variable.</span></span> <span data-ttu-id="b76d9-120">기본값인는 `SilentlyContinue` 자세한 정보 표시 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-120">The default value, `SilentlyContinue`, suppresses verbose messages.</span></span> <span data-ttu-id="b76d9-121">두 번째 명령은 자세한 정보 메시지를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-121">The second command writes a verbose message.</span></span>

## <span data-ttu-id="b76d9-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b76d9-122">PARAMETERS</span></span>

### <span data-ttu-id="b76d9-123">-메시지</span><span class="sxs-lookup"><span data-stu-id="b76d9-123">-Message</span></span>

<span data-ttu-id="b76d9-124">표시할 메시지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-124">Specifies the message to display.</span></span> <span data-ttu-id="b76d9-125">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-125">This parameter is required.</span></span> <span data-ttu-id="b76d9-126">메시지 문자열을로 파이프 할 수도 있습니다 `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="b76d9-126">You can also pipe a message string to `Write-Verbose`.</span></span>

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

### <span data-ttu-id="b76d9-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b76d9-127">CommonParameters</span></span>

<span data-ttu-id="b76d9-128">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b76d9-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b76d9-129">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b76d9-129">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b76d9-130">입력</span><span class="sxs-lookup"><span data-stu-id="b76d9-130">INPUTS</span></span>

### <span data-ttu-id="b76d9-131">System.String</span><span class="sxs-lookup"><span data-stu-id="b76d9-131">System.String</span></span>

<span data-ttu-id="b76d9-132">메시지를 포함 하는 문자열을로 파이프 할 수 있습니다 `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="b76d9-132">You can pipe a string that contains the message to `Write-Verbose`.</span></span>

## <span data-ttu-id="b76d9-133">출력</span><span class="sxs-lookup"><span data-stu-id="b76d9-133">OUTPUTS</span></span>

### <span data-ttu-id="b76d9-134">None</span><span class="sxs-lookup"><span data-stu-id="b76d9-134">None</span></span>

<span data-ttu-id="b76d9-135">`Write-Verbose` 자세한 정보 메시지 스트림에만 씁니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-135">`Write-Verbose` writes only to the verbose message stream.</span></span>

## <span data-ttu-id="b76d9-136">참고</span><span class="sxs-lookup"><span data-stu-id="b76d9-136">NOTES</span></span>

- <span data-ttu-id="b76d9-137">자세한 정보 메시지는 명령에서 **Verbose** 일반 매개 변수를 사용하는 경우에만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-137">Verbose messages are returned only when the command uses the **Verbose** common parameter.</span></span> <span data-ttu-id="b76d9-138">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b76d9-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>
- <span data-ttu-id="b76d9-139">Windows PowerShell 백그라운드 작업 및 원격 명령에서 `$VerbosePreference` 작업 세션 및 원격 세션의 변수는 자세한 정보 표시 메시지를 기본적으로 표시할지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b76d9-139">In Windows PowerShell background jobs and remote commands, the `$VerbosePreference` variable in the job session and remote session determine whether the verbose message is displayed by default.</span></span>
  <span data-ttu-id="b76d9-140">변수에 대 한 자세한 내용은 `$VerbosePreference` [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b76d9-140">For more information about the `$VerbosePreference` variable, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="b76d9-141">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b76d9-141">RELATED LINKS</span></span>

[<span data-ttu-id="b76d9-142">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="b76d9-142">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="b76d9-143">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="b76d9-143">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="b76d9-144">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="b76d9-144">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="b76d9-145">쓰기 오류</span><span class="sxs-lookup"><span data-stu-id="b76d9-145">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="b76d9-146">Write-Host</span><span class="sxs-lookup"><span data-stu-id="b76d9-146">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="b76d9-147">Write-Information</span><span class="sxs-lookup"><span data-stu-id="b76d9-147">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="b76d9-148">Write-Output</span><span class="sxs-lookup"><span data-stu-id="b76d9-148">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="b76d9-149">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="b76d9-149">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="b76d9-150">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="b76d9-150">Write-Warning</span></span>](Write-Warning.md)

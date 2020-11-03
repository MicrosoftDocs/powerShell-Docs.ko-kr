---
external help file: Stop-DscConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/19/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/stop-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-DscConfiguration
ms.openlocfilehash: 93c8585ae948dfa360a2ae8e2563670de8fd6e93
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213601"
---
# <span data-ttu-id="79e86-103">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="79e86-103">Stop-DscConfiguration</span></span>

## <span data-ttu-id="79e86-104">개요</span><span class="sxs-lookup"><span data-stu-id="79e86-104">SYNOPSIS</span></span>
<span data-ttu-id="79e86-105">실행 중인 구성 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-105">Stops a configuration job that is running.</span></span>

## <span data-ttu-id="79e86-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="79e86-106">SYNTAX</span></span>

### <span data-ttu-id="79e86-107">모두</span><span class="sxs-lookup"><span data-stu-id="79e86-107">All</span></span>

```
Stop-DscConfiguration [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="79e86-108">설명</span><span class="sxs-lookup"><span data-stu-id="79e86-108">DESCRIPTION</span></span>

<span data-ttu-id="79e86-109">Cmdlet은를 `Stop-DscConfiguration` 실행 하는 구성 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-109">The `Stop-DscConfiguration` cmdlet stops a configuration job that is running.</span></span> <span data-ttu-id="79e86-110">CIM(Common Information Model) (CIM) 세션을 사용 하 여이 cmdlet이 적용 되는 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-110">Specify which computers this cmdlet applies to by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="79e86-111">실행 중인 구성 작업이 없는 경우이 cmdlet은 경고 메시지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-111">If there's no configuration job running, this cmdlet returns a warning message.</span></span>

<span data-ttu-id="79e86-112">`Stop-DscConfiguration` 는 Microsoft 지원 라이브러리에서 [WINDOWS RT 8.1, Windows 8.1 및 Windows Server 2012 r 2에 대 한 11 월 2014 업데이트 롤업의](https://support.microsoft.com/kb/3000850) 일부로만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-112">`Stop-DscConfiguration` is only available as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span> <span data-ttu-id="79e86-113">이 cmdlet을 사용 하기 전에 [Windows PowerShell 5.0의 새로운 기능](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50) 정보를 검토 하십시오.</span><span class="sxs-lookup"><span data-stu-id="79e86-113">Before you use this cmdlet, review the information in [What's New in Windows PowerShell 5.0](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50)</span></span>

## <span data-ttu-id="79e86-114">예제</span><span class="sxs-lookup"><span data-stu-id="79e86-114">EXAMPLES</span></span>

### <span data-ttu-id="79e86-115">예제 1: 구성 작업 중지</span><span class="sxs-lookup"><span data-stu-id="79e86-115">Example 1: Stop a configuration job</span></span>

<span data-ttu-id="79e86-116">이 예제에서는 cmdlet을 사용 하 여 CIM 세션을 만듭니다 `New-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="79e86-116">In this example, a CIM session is created using the `New-CimSession` cmdlet.</span></span> <span data-ttu-id="79e86-117">**CimSession** 개체는 실행 중인 구성 작업을 중지 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-117">The **CimSession** object is used to stop a running configuration job.</span></span>

```powershell
$Session = New-CimSession -ComputerName Server01 -Credential ACCOUNTS\User01
Stop-DscConfiguration -CimSession $Session
```

<span data-ttu-id="79e86-118">`New-CimSession`**ComputerName** 매개 변수를 사용 하 여 Server01 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-118">`New-CimSession` uses the **ComputerName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="79e86-119">**Credential** 매개 변수는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-119">The **Credential** parameter specifies the user account.</span></span> <span data-ttu-id="79e86-120">**CimSession** 개체는 변수에 저장 됩니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="79e86-120">The **CimSession** object is stored in the `$Session` variable.</span></span> <span data-ttu-id="79e86-121">명령이 실행 되 면 사용자 계정의 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-121">When the command is run, you're prompted for the user account's password.</span></span>

<span data-ttu-id="79e86-122">`Stop-DscConfiguration` 는 **CimSession** 매개 변수 및에 저장 된 개체를 사용 하 여 `$Session` 구성 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-122">`Stop-DscConfiguration` uses the **CimSession** parameter and the object stored in `$Session` to stop the configuration job.</span></span>

## <span data-ttu-id="79e86-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="79e86-123">PARAMETERS</span></span>

### <span data-ttu-id="79e86-124">-AsJob</span><span class="sxs-lookup"><span data-stu-id="79e86-124">-AsJob</span></span>

<span data-ttu-id="79e86-125">이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-125">Indicates that this cmdlet runs the command as a background job.</span></span> <span data-ttu-id="79e86-126">PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) 및 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79e86-126">For more information about PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="79e86-127">**AsJob** 매개 변수를 사용 하려면 원격 컴퓨터에 대 한 로컬 및 원격 컴퓨터를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-127">To use the **AsJob** parameter, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="79e86-128">Windows Vista 이상 버전의 Windows 운영 체제에서는 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-128">On Windows Vista and later versions of the Windows operating system, you must open PowerShell with the **Run as administrator** option.</span></span> <span data-ttu-id="79e86-129">자세한 내용은 [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79e86-129">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79e86-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="79e86-130">-CimSession</span></span>

<span data-ttu-id="79e86-131">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-131">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="79e86-132">컴퓨터 이름 또는 세션 개체 (예: 또는의 출력)를 입력 `New-CimSession` 합니다 `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="79e86-132">Enter a computer name or a session object, such as the output from `New-CimSession` or `Get-CimSession`.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79e86-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="79e86-133">-Confirm</span></span>

<span data-ttu-id="79e86-134">`Stop-DscConfiguration` 는 **Confirm** 매개 변수를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-134">`Stop-DscConfiguration` doesn't support the **Confirm** parameter.</span></span> <span data-ttu-id="79e86-135">**Confirm** 매개 변수를 사용 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-135">If the **Confirm** parameter is used, an error is displayed.</span></span>

<span data-ttu-id="79e86-136">**확인** 을 지 원하는 PowerShell cmdlet의 경우 매개 변수를 사용 하 여 명령을 실행 하기 전에 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-136">For PowerShell cmdlets that support **Confirm** , using the parameter prompts you for verification before a command is run.</span></span>

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

### <span data-ttu-id="79e86-137">-Force</span><span class="sxs-lookup"><span data-stu-id="79e86-137">-Force</span></span>

<span data-ttu-id="79e86-138">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-138">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79e86-139">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="79e86-139">-ThrottleLimit</span></span>

<span data-ttu-id="79e86-140">cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-140">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

<span data-ttu-id="79e86-141">이 매개 변수를 생략 하거나 값을 `0` 입력 하면 PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 최적 스로틀 제한을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-141">If this parameter is omitted or a value of `0` is entered, PowerShell calculates an optimum throttle limit based on the number of CIM cmdlets that are running on the computer.</span></span> <span data-ttu-id="79e86-142">스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-142">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79e86-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="79e86-143">-WhatIf</span></span>

<span data-ttu-id="79e86-144">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-144">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="79e86-145">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79e86-145">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="79e86-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="79e86-146">CommonParameters</span></span>

<span data-ttu-id="79e86-147">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="79e86-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="79e86-148">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79e86-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="79e86-149">입력</span><span class="sxs-lookup"><span data-stu-id="79e86-149">INPUTS</span></span>

### <span data-ttu-id="79e86-150">없음</span><span class="sxs-lookup"><span data-stu-id="79e86-150">None</span></span>

## <span data-ttu-id="79e86-151">출력</span><span class="sxs-lookup"><span data-stu-id="79e86-151">OUTPUTS</span></span>

### <span data-ttu-id="79e86-152">없음</span><span class="sxs-lookup"><span data-stu-id="79e86-152">None</span></span>

## <span data-ttu-id="79e86-153">참고</span><span class="sxs-lookup"><span data-stu-id="79e86-153">NOTES</span></span>

## <span data-ttu-id="79e86-154">관련 링크</span><span class="sxs-lookup"><span data-stu-id="79e86-154">RELATED LINKS</span></span>

[<span data-ttu-id="79e86-155">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="79e86-155">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="79e86-156">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="79e86-156">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="79e86-157">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="79e86-157">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="79e86-158">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="79e86-158">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="79e86-159">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="79e86-159">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="79e86-160">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="79e86-160">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="79e86-161">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="79e86-161">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

[<span data-ttu-id="79e86-162">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="79e86-162">Update-DscConfiguration</span></span>](Update-DscConfiguration.md)

[<span data-ttu-id="79e86-163">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="79e86-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

---
external help file: Enable-DscDebug.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/enable-dscdebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-DscDebug
ms.openlocfilehash: 136481c5a1945c3d5cbd1ca7fc8ce5f580c39b0f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215361"
---
# <span data-ttu-id="b817b-103">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="b817b-103">Enable-DscDebug</span></span>

## <span data-ttu-id="b817b-104">개요</span><span class="sxs-lookup"><span data-stu-id="b817b-104">SYNOPSIS</span></span>
<span data-ttu-id="b817b-105">모든 DSC 리소스의 디버깅을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-105">Starts debugging of all DSC resources.</span></span>

## <span data-ttu-id="b817b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b817b-106">SYNTAX</span></span>

```
Enable-DscDebug [-BreakAll] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="b817b-107">설명</span><span class="sxs-lookup"><span data-stu-id="b817b-107">DESCRIPTION</span></span>
<span data-ttu-id="b817b-108">**Enable-DscDebug** CMDLET은 dsc 엔진에서 WINDOWS PowerShell Dsc (필요한 상태 구성) 리소스를 디버깅할 수 있도록 합니다 .이를 로컬 CONFIGURATION MANAGER (LCM)이 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-108">The **Enable-DscDebug** cmdlet enables Windows PowerShell Desired State Configuration (DSC) resource debugging by the DSC engine, which is also known as the Local Configuration Manager (LCM).</span></span>
<span data-ttu-id="b817b-109">기본적으로 모든 리소스 인스턴스는 디버거로 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-109">By default, all resource instances break into the debugger.</span></span>

## <span data-ttu-id="b817b-110">예제</span><span class="sxs-lookup"><span data-stu-id="b817b-110">EXAMPLES</span></span>

### <span data-ttu-id="b817b-111">예제 1: 디버깅 시작</span><span class="sxs-lookup"><span data-stu-id="b817b-111">Example 1: Start debugging</span></span>

```
PS C:\> Enable-DscDebug -BreakAll
```

<span data-ttu-id="b817b-112">이 명령은 DSC 엔진 또는 LCM에서 리소스 디버깅을 시작 하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-112">This command indicates to the DSC engine or LCM to start resource debugging.</span></span>
<span data-ttu-id="b817b-113">다음에 구성을 실행할 때 프로세스가 디버거로 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-113">The next time the configuration is run, the process enters the debugger.</span></span>

### <span data-ttu-id="b817b-114">예제 2: 원격 디버깅 시작</span><span class="sxs-lookup"><span data-stu-id="b817b-114">Example 2: Start remote debugging</span></span>

```
PS C:\> Enable-DscDebug -BreakAll -CimSession DeploymentServer
```

<span data-ttu-id="b817b-115">이 명령은 원격 컴퓨터의 DSC 엔진에서 리소스 디버깅을 시작 하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-115">This command indicates to the DSC engine of the remote computer to start resource debugging.</span></span>

## <span data-ttu-id="b817b-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b817b-116">PARAMETERS</span></span>

### <span data-ttu-id="b817b-117">-AsJob</span><span class="sxs-lookup"><span data-stu-id="b817b-117">-AsJob</span></span>
<span data-ttu-id="b817b-118">이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-118">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="b817b-119">-간</span><span class="sxs-lookup"><span data-stu-id="b817b-119">-BreakAll</span></span>
<span data-ttu-id="b817b-120">구성 실행 시 모든 리소스가 디버거에 입력 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-120">Indicates that all resources enter the debugger when a configuration runs.</span></span>

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

### <span data-ttu-id="b817b-121">-CimSession</span><span class="sxs-lookup"><span data-stu-id="b817b-121">-CimSession</span></span>
<span data-ttu-id="b817b-122">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-122">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="b817b-123">[CimSession](/powershell/module/cimcmdlets/new-cimsession) 또는 [CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-123">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="b817b-124">기본값은 로컬 컴퓨터의 현재 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-124">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="b817b-125">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b817b-125">-ThrottleLimit</span></span>
<span data-ttu-id="b817b-126">cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-126">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="b817b-127">이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-127">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="b817b-128">스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-128">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="b817b-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b817b-129">-Confirm</span></span>
<span data-ttu-id="b817b-130">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b817b-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b817b-131">-WhatIf</span></span>
<span data-ttu-id="b817b-132">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b817b-133">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b817b-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b817b-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b817b-134">CommonParameters</span></span>
<span data-ttu-id="b817b-135">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b817b-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b817b-136">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b817b-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b817b-137">입력</span><span class="sxs-lookup"><span data-stu-id="b817b-137">INPUTS</span></span>

## <span data-ttu-id="b817b-138">출력</span><span class="sxs-lookup"><span data-stu-id="b817b-138">OUTPUTS</span></span>

## <span data-ttu-id="b817b-139">참고</span><span class="sxs-lookup"><span data-stu-id="b817b-139">NOTES</span></span>

## <span data-ttu-id="b817b-140">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b817b-140">RELATED LINKS</span></span>

[<span data-ttu-id="b817b-141">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="b817b-141">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="b817b-142">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="b817b-142">Disable-DscDebug</span></span>](Disable-DscDebug.md)

[<span data-ttu-id="b817b-143">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b817b-143">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="b817b-144">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="b817b-144">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="b817b-145">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b817b-145">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="b817b-146">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b817b-146">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="b817b-147">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b817b-147">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

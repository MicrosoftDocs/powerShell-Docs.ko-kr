---
external help file: Disable-DscDebug.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/disable-dscdebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-DscDebug
ms.openlocfilehash: fdaba8358772f559a33117c796a923d774b009cb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215353"
---
# <span data-ttu-id="5aaac-103">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="5aaac-103">Disable-DscDebug</span></span>

## <span data-ttu-id="5aaac-104">개요</span><span class="sxs-lookup"><span data-stu-id="5aaac-104">SYNOPSIS</span></span>
<span data-ttu-id="5aaac-105">DSC 리소스의 디버깅을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-105">Stops debugging of DSC resources.</span></span>

## <span data-ttu-id="5aaac-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5aaac-106">SYNTAX</span></span>

```
Disable-DscDebug [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="5aaac-107">설명</span><span class="sxs-lookup"><span data-stu-id="5aaac-107">DESCRIPTION</span></span>
<span data-ttu-id="5aaac-108">**Disable-DscDebug** Cmdlet은 WINDOWS PowerShell Dsc (필요한 상태 구성) 엔진에서 dsc 리소스의 디버깅을 중지 하도록 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-108">The **Disable-DscDebug** cmdlet requests that the Windows PowerShell Desired State Configuration (DSC) engine stop debugging of DSC resources.</span></span>
<span data-ttu-id="5aaac-109">이 cmdlet은 DSC 엔진이 현재 디버깅 모드가 아닌 경우에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-109">This cmdlet has no effect if the DSC engine is not currently in debugging mode.</span></span>

## <span data-ttu-id="5aaac-110">예제</span><span class="sxs-lookup"><span data-stu-id="5aaac-110">EXAMPLES</span></span>

### <span data-ttu-id="5aaac-111">예제 1: 리소스 디버깅 중지</span><span class="sxs-lookup"><span data-stu-id="5aaac-111">Example 1: Stop resource debugging</span></span>

```
PS C:\> Disable-DscDebug
```

<span data-ttu-id="5aaac-112">이 명령은 LCM (로컬 Configuration Manager)에서 DSC 엔진을 지정 하 여 리소스 디버깅을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-112">This command indicates to the DSC engine on the Local Configuration Manager (LCM) to stop resource debugging.</span></span>

### <span data-ttu-id="5aaac-113">예 2: 엔진 상태를 확인 하 고 디버깅을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-113">Example 2: Check the engine state and stop debugging</span></span>

```
PS C:\> if((Get-DscLocalConfigurationManager).DebugMode -like '*Break*'){Disable-DscDebug}
```

<span data-ttu-id="5aaac-114">이 명령은 DSC 엔진 상태를 확인 하 고 이미 디버깅 모드에 있는 경우에만 리소스 디버깅을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-114">This command checks the DSC engine state, and stops resource debugging only if it is already in debugging mode</span></span>

## <span data-ttu-id="5aaac-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5aaac-115">PARAMETERS</span></span>

### <span data-ttu-id="5aaac-116">-AsJob</span><span class="sxs-lookup"><span data-stu-id="5aaac-116">-AsJob</span></span>
<span data-ttu-id="5aaac-117">이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-117">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="5aaac-118">-CimSession</span><span class="sxs-lookup"><span data-stu-id="5aaac-118">-CimSession</span></span>
<span data-ttu-id="5aaac-119">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-119">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="5aaac-120">[CimSession](/powershell/module/cimcmdlets/new-cimsession) 또는 [CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-120">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="5aaac-121">기본값은 로컬 컴퓨터의 현재 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-121">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="5aaac-122">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="5aaac-122">-ThrottleLimit</span></span>
<span data-ttu-id="5aaac-123">cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-123">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="5aaac-124">이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-124">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="5aaac-125">스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-125">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="5aaac-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5aaac-126">-Confirm</span></span>
<span data-ttu-id="5aaac-127">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5aaac-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5aaac-128">-WhatIf</span></span>
<span data-ttu-id="5aaac-129">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5aaac-130">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5aaac-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5aaac-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5aaac-131">CommonParameters</span></span>
<span data-ttu-id="5aaac-132">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5aaac-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5aaac-133">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5aaac-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5aaac-134">입력</span><span class="sxs-lookup"><span data-stu-id="5aaac-134">INPUTS</span></span>

## <span data-ttu-id="5aaac-135">출력</span><span class="sxs-lookup"><span data-stu-id="5aaac-135">OUTPUTS</span></span>

## <span data-ttu-id="5aaac-136">참고</span><span class="sxs-lookup"><span data-stu-id="5aaac-136">NOTES</span></span>

## <span data-ttu-id="5aaac-137">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5aaac-137">RELATED LINKS</span></span>

[<span data-ttu-id="5aaac-138">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="5aaac-138">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="5aaac-139">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="5aaac-139">Enable-DscDebug</span></span>](Enable-DscDebug.md)

[<span data-ttu-id="5aaac-140">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="5aaac-140">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="5aaac-141">Get DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5aaac-141">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)

[<span data-ttu-id="5aaac-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="5aaac-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="5aaac-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="5aaac-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="5aaac-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="5aaac-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

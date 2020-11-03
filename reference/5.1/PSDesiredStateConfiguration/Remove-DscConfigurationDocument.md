---
external help file: Remove-DscConfigurationDocument.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-DscConfigurationDocument
ms.openlocfilehash: d3e9b15dfeea94921503247adc08b291eed9d7d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215298"
---
# <span data-ttu-id="20815-103">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="20815-103">Remove-DscConfigurationDocument</span></span>

## <span data-ttu-id="20815-104">개요</span><span class="sxs-lookup"><span data-stu-id="20815-104">SYNOPSIS</span></span>
<span data-ttu-id="20815-105">DSC 구성 저장소에서 구성 문서를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-105">Removes a configuration document from the DSC configuration store.</span></span>

## <span data-ttu-id="20815-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="20815-106">SYNTAX</span></span>

```
Remove-DscConfigurationDocument -Stage <Stage> [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>]
 [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="20815-107">설명</span><span class="sxs-lookup"><span data-stu-id="20815-107">DESCRIPTION</span></span>
<span data-ttu-id="20815-108">`Remove-DscConfigurationDocument`Cmdlet은 Windows POWERSHELL DSC (필요한 상태 구성) 구성 저장소에서 구성 문서 (.mof 파일)를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-108">The `Remove-DscConfigurationDocument` cmdlet removes a configuration document (.mof file) from the Windows PowerShell Desired State Configuration (DSC) configuration store.</span></span>
<span data-ttu-id="20815-109">구성 하는 동안 `Start-DscConfiguration` cmdlet은 .mof 파일을 대상 컴퓨터의 폴더에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-109">During configuration, the `Start-DscConfiguration` cmdlet copies a .mof file to a folder on the target computer.</span></span>
<span data-ttu-id="20815-110">이 cmdlet은 해당 구성 문서를 제거 하 고 추가 정리를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-110">This cmdlet removes that configuration document and does additional cleanup.</span></span>

<span data-ttu-id="20815-111">이 cmdlet은 Microsoft 지원 라이브러리에서 [WINDOWS RT 8.1, Windows 8.1 및 Windows Server 2012 r 2에 대 한 11 월 2014 업데이트 롤업의](https://support.microsoft.com/kb/3000850) 일부로만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20815-111">This cmdlet is available only as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span>

## <span data-ttu-id="20815-112">예제</span><span class="sxs-lookup"><span data-stu-id="20815-112">EXAMPLES</span></span>

### <span data-ttu-id="20815-113">예제 1: 현재 구성 문서 제거</span><span class="sxs-lookup"><span data-stu-id="20815-113">Example 1: Remove the current configuration document</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Remove-DscConfigurationDocument -Stage Current -CimSession $Session
```

<span data-ttu-id="20815-114">첫 번째 명령은 **New-CimSession** cmdlet을 사용하여 CIM 세션을 만든 다음 **CimSession** 개체를 $Session 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-114">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="20815-115">또한 암호를 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-115">The command prompts you for a password.</span></span>
<span data-ttu-id="20815-116">자세한 내용을 보려면 `Get-Help New-CimSession`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="20815-116">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="20815-117">두 번째 명령은 $Session에 저장 된 **CimSession** 에 지정 된 컴퓨터에 대 한 현재 구성 문서를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-117">The second command removes the current configuration document for the computer specified in the **CimSession** stored in $Session.</span></span>

## <span data-ttu-id="20815-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="20815-118">PARAMETERS</span></span>

### <span data-ttu-id="20815-119">-AsJob</span><span class="sxs-lookup"><span data-stu-id="20815-119">-AsJob</span></span>
<span data-ttu-id="20815-120">이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="20815-120">Indicates that this cmdlet runs the command as a background job.</span></span>

<span data-ttu-id="20815-121">*AsJob* 매개 변수를 지정 하는 경우이 명령은 작업을 나타내는 개체를 반환한 다음 명령 프롬프트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-121">If you specify the *AsJob* parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span>
<span data-ttu-id="20815-122">작업이 완료 될 때까지 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20815-122">You can continue to work in the session until the job finishes.</span></span>
<span data-ttu-id="20815-123">AsJob 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-123">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="20815-124">작업을 관리하려면 Job cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-124">To manage the job, use the Job cmdlets.</span></span>
<span data-ttu-id="20815-125">작업 결과를 가져오려면 Receive-Job cmdlet을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="20815-125">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="20815-126">이 매개 변수를 사용 하려면 로컬 및 원격 컴퓨터를 원격으로 구성 하 고 Windows Vista 이상 버전의 Windows 운영 체제에서는 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-126">To use this parameter, the local and remote computers must be configured for remoting, and on Windows Vista and later versions of the Windows operating system, you must open Windows PowerShell with the Run as administrator option.</span></span>
<span data-ttu-id="20815-127">자세한 내용은 [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20815-127">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="20815-128">Windows PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) 및 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="20815-128">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="20815-129">-CimSession</span><span class="sxs-lookup"><span data-stu-id="20815-129">-CimSession</span></span>
<span data-ttu-id="20815-130">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-130">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="20815-131">**CimSession** 또는 **CimSession** cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-131">Enter a computer name or a session object, such as the output of a **New-CimSession** or **Get-CimSession** cmdlet.</span></span>

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

### <span data-ttu-id="20815-132">-Force</span><span class="sxs-lookup"><span data-stu-id="20815-132">-Force</span></span>
<span data-ttu-id="20815-133">이 cmdlet이 구성 문서를 제거 하기 전에 실행 중인 구성 작업을 중지 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="20815-133">Indicates that this cmdlet stops the running configuration job before it removes the configuration document.</span></span>
<span data-ttu-id="20815-134">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-134">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="20815-135">-단계</span><span class="sxs-lookup"><span data-stu-id="20815-135">-Stage</span></span>
<span data-ttu-id="20815-136">제거할 구성 문서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-136">Specifies which configuration document to remove.</span></span>
<span data-ttu-id="20815-137">여러 문서를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20815-137">You can specify multiple documents.</span></span>
<span data-ttu-id="20815-138">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="20815-138">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="20815-139">현재 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="20815-139">Current.</span></span>
<span data-ttu-id="20815-140">시스템의 현재 상태를 설명 하는 구성 문서를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-140">Remove the configuration document that describes the current state of the system.</span></span>
- <span data-ttu-id="20815-141">보류 중.</span><span class="sxs-lookup"><span data-stu-id="20815-141">Pending.</span></span>
<span data-ttu-id="20815-142">시스템의 보류 상태를 설명 하는 구성 문서를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-142">Remove the configuration document that describes the pending state of the system.</span></span>
- <span data-ttu-id="20815-143">선행.</span><span class="sxs-lookup"><span data-stu-id="20815-143">Previous.</span></span>
<span data-ttu-id="20815-144">시스템의 이전 상태를 설명 하는 구성 문서를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-144">Remove the configuration document that describes the previous state of the system.</span></span>

```yaml
Type: Microsoft.PowerShell.Cmdletization.GeneratedTypes.RemoveDscConfigurationDocument.Stage
Parameter Sets: (All)
Aliases:
Accepted values: Current, Pending, Previous

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20815-145">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="20815-145">-ThrottleLimit</span></span>
<span data-ttu-id="20815-146">cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-146">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="20815-147">이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-147">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="20815-148">스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20815-148">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="20815-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="20815-149">-Confirm</span></span>
<span data-ttu-id="20815-150">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="20815-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="20815-151">-WhatIf</span></span>
<span data-ttu-id="20815-152">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20815-152">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="20815-153">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20815-153">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="20815-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20815-154">CommonParameters</span></span>
<span data-ttu-id="20815-155">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="20815-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="20815-156">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20815-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="20815-157">입력</span><span class="sxs-lookup"><span data-stu-id="20815-157">INPUTS</span></span>

### <span data-ttu-id="20815-158">없음</span><span class="sxs-lookup"><span data-stu-id="20815-158">None</span></span>

## <span data-ttu-id="20815-159">출력</span><span class="sxs-lookup"><span data-stu-id="20815-159">OUTPUTS</span></span>

### <span data-ttu-id="20815-160">없음</span><span class="sxs-lookup"><span data-stu-id="20815-160">None</span></span>

## <span data-ttu-id="20815-161">참고</span><span class="sxs-lookup"><span data-stu-id="20815-161">NOTES</span></span>

## <span data-ttu-id="20815-162">관련 링크</span><span class="sxs-lookup"><span data-stu-id="20815-162">RELATED LINKS</span></span>

[<span data-ttu-id="20815-163">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="20815-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="20815-164">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="20815-164">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="20815-165">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="20815-165">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

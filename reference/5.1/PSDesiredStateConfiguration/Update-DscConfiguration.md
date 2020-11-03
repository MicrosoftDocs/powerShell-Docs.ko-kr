---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/update-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-DscConfiguration
ms.openlocfilehash: 13365902ab317a3daa41b9a951d5e2fa6e4f1b37
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213570"
---
# <span data-ttu-id="b4da0-103">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b4da0-103">Update-DscConfiguration</span></span>

## <span data-ttu-id="b4da0-104">개요</span><span class="sxs-lookup"><span data-stu-id="b4da0-104">SYNOPSIS</span></span>
<span data-ttu-id="b4da0-105">끌어오기 서버에서 업데이트 된 구성을 확인 하 고 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-105">Checks the pull server for an updated configuration and applies it.</span></span>

## <span data-ttu-id="b4da0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b4da0-106">SYNTAX</span></span>

### <span data-ttu-id="b4da0-107">ComputerNameSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="b4da0-107">ComputerNameSet (Default)</span></span>

```
Update-DscConfiguration [-Wait] [-JobName <String>] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b4da0-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="b4da0-108">CimSessionSet</span></span>

```
Update-DscConfiguration [-Wait] [-JobName <String>] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b4da0-109">설명</span><span class="sxs-lookup"><span data-stu-id="b4da0-109">DESCRIPTION</span></span>
<span data-ttu-id="b4da0-110">`Update-DscConfiguration`Cmdlet은 끌어오기 서버에 연결 하 고, 노드가 노드의 최신 항목과 다른 경우 구성을 다운로드 한 후 컴퓨터에 구성을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-110">The `Update-DscConfiguration` cmdlet connects to a pull server, downloads the configuration if it differs from what is current on the node, and then applies the configuration to the computer.</span></span>

<span data-ttu-id="b4da0-111">이 cmdlet은 Microsoft 지원 라이브러리에서 [WINDOWS RT 8.1, Windows 8.1 및 Windows Server 2012 r 2에 대 한 11 월 2014 업데이트 롤업의](https://support.microsoft.com/kb/3000850) 일부로만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-111">This cmdlet is available only as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span>

## <span data-ttu-id="b4da0-112">예제</span><span class="sxs-lookup"><span data-stu-id="b4da0-112">EXAMPLES</span></span>

### <span data-ttu-id="b4da0-113">예제 1: 구성 업데이트</span><span class="sxs-lookup"><span data-stu-id="b4da0-113">Example 1: Update a configuration</span></span>

```
PS C:\> Update-DscConfiguration -Wait -Verbose
```

<span data-ttu-id="b4da0-114">이 명령을 실행 한 후 서버에서 등록 된 끌어오기 서비스에 연결 하 고, 할당 된 최신 구성을 다운로드 한 후 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-114">After running this command, the server will connect to the registered pull service, download the latest assigned configuration, and then apply it.</span></span>
<span data-ttu-id="b4da0-115">-Wait 및-Verbose 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-115">The -Wait and -Verbose parameters are optional.</span></span>
<span data-ttu-id="b4da0-116">대화형으로 작업 하는 경우 이러한 매개 변수를 결합 하면 구성 적용 시 진행률 및 성공 또는 실패에 대 한 실시간 피드백을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-116">When working interactively, these parameters combined enable real-time feedback about progress and success or failure when applying the configuration.</span></span>

### <span data-ttu-id="b4da0-117">예제 2: CIM 세션을 통해 연결 하 여 구성 업데이트</span><span class="sxs-lookup"><span data-stu-id="b4da0-117">Example 2: Update a configuration by connecting over a CIM session</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Update-DscConfiguration -CimSession $Session -Wait
```

<span data-ttu-id="b4da0-118">첫 번째 명령은 **New-CimSession** cmdlet을 사용하여 CIM 세션을 만든 다음 **CimSession** 개체를 $Session 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-118">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="b4da0-119">또한 암호를 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-119">The command prompts you for a password.</span></span>
<span data-ttu-id="b4da0-120">자세한 내용을 보려면 `Get-Help New-CimSession`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4da0-120">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="b4da0-121">두 번째 명령은 $Session에 저장 된 **CimSession** 에 지정 된 컴퓨터를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-121">The second command updates the computer specified in the **CimSession** stored in $Session.</span></span>
<span data-ttu-id="b4da0-122">이 명령은 *Wait* 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-122">The command specifies the *Wait* parameter.</span></span>
<span data-ttu-id="b4da0-123">현재 명령이 완료 될 때까지 콘솔에서 추가 명령을 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-123">The console does not accept additional commands until the current command finishes.</span></span>

## <span data-ttu-id="b4da0-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b4da0-124">PARAMETERS</span></span>

### <span data-ttu-id="b4da0-125">-CimSession</span><span class="sxs-lookup"><span data-stu-id="b4da0-125">-CimSession</span></span>
<span data-ttu-id="b4da0-126">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-126">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="b4da0-127">[CimSession](/powershell/module/cimcmdlets/new-cimsession) 또는 [CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-127">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="b4da0-128">기본값은 로컬 컴퓨터의 현재 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-128">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b4da0-129">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b4da0-129">-ComputerName</span></span>
<span data-ttu-id="b4da0-130">컴퓨터 이름 배열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-130">Specifies an array of computer names.</span></span>
<span data-ttu-id="b4da0-131">Cmdlet은이 매개 변수가 지정 하는 컴퓨터에 구성 설정을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-131">The cmdlet applies the configuration settings to the computers that this parameter specifies.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b4da0-132">-Credential</span><span class="sxs-lookup"><span data-stu-id="b4da0-132">-Credential</span></span>
<span data-ttu-id="b4da0-133">대상 컴퓨터에 대한 사용자 이름과 암호를 **PSCredential** 개체로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-133">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="b4da0-134">**PSCredential** 개체를 가져오려면 Get-Credential cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-134">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="b4da0-135">자세한 내용을 보려면 `Get-Help Get-Credential`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4da0-135">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b4da0-136">-JobName</span><span class="sxs-lookup"><span data-stu-id="b4da0-136">-JobName</span></span>
<span data-ttu-id="b4da0-137">작업의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-137">Specifies a friendly name for a job.</span></span>
<span data-ttu-id="b4da0-138">이 매개 변수를 지정하면 cmdlet이 작업으로 실행되고 **Job** 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-138">If you specify this parameter, the cmdlet runs as a job, and it returns a **Job** object.</span></span>

<span data-ttu-id="b4da0-139">기본적으로 Windows PowerShell은 이름 JobN을 할당 합니다. 여기서 N은 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-139">By default, Windows PowerShell assigns the name JobN where N is an integer.</span></span>

<span data-ttu-id="b4da0-140">*Wait* 매개 변수를 지정하는 경우 이 매개 변수를 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b4da0-140">If you specify the *Wait* parameter, do not specify this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b4da0-141">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b4da0-141">-ThrottleLimit</span></span>
<span data-ttu-id="b4da0-142">cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-142">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="b4da0-143">이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-143">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="b4da0-144">스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-144">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="b4da0-145">-Wait</span><span class="sxs-lookup"><span data-stu-id="b4da0-145">-Wait</span></span>
<span data-ttu-id="b4da0-146">Cmdlet이 모든 구성 작업을 완료할 때까지 콘솔을 차단 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-146">Indicates that the cmdlet blocks the console until it finishes all configuration tasks.</span></span>

<span data-ttu-id="b4da0-147">이 매개 변수를 지정하는 경우 *JobName* 매개 변수를 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b4da0-147">If you specify this parameter, do not specify the *JobName* parameter.</span></span>

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

### <span data-ttu-id="b4da0-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b4da0-148">-Confirm</span></span>
<span data-ttu-id="b4da0-149">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b4da0-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b4da0-150">-WhatIf</span></span>
<span data-ttu-id="b4da0-151">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b4da0-152">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4da0-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b4da0-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b4da0-153">CommonParameters</span></span>
<span data-ttu-id="b4da0-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b4da0-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b4da0-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4da0-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b4da0-156">입력</span><span class="sxs-lookup"><span data-stu-id="b4da0-156">INPUTS</span></span>

## <span data-ttu-id="b4da0-157">출력</span><span class="sxs-lookup"><span data-stu-id="b4da0-157">OUTPUTS</span></span>

## <span data-ttu-id="b4da0-158">참고</span><span class="sxs-lookup"><span data-stu-id="b4da0-158">NOTES</span></span>

## <span data-ttu-id="b4da0-159">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b4da0-159">RELATED LINKS</span></span>

[<span data-ttu-id="b4da0-160">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="b4da0-160">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="b4da0-161">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b4da0-161">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="b4da0-162">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="b4da0-162">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="b4da0-163">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b4da0-163">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="b4da0-164">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b4da0-164">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="b4da0-165">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b4da0-165">Stop-DscConfiguration</span></span>](Stop-DscConfiguration.md)

[<span data-ttu-id="b4da0-166">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b4da0-166">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

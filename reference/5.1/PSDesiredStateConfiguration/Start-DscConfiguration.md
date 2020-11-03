---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/start-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-DscConfiguration
ms.openlocfilehash: c34754aeb7fce99030cf4ddb235e3e7e8161f3eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215289"
---
# <span data-ttu-id="51bc7-103">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="51bc7-103">Start-DscConfiguration</span></span>

## <span data-ttu-id="51bc7-104">개요</span><span class="sxs-lookup"><span data-stu-id="51bc7-104">SYNOPSIS</span></span>
<span data-ttu-id="51bc7-105">구성을 노드에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-105">Applies configuration to nodes.</span></span>

## <span data-ttu-id="51bc7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="51bc7-106">SYNTAX</span></span>

### <span data-ttu-id="51bc7-107">ComputerNameAndPathSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="51bc7-107">ComputerNameAndPathSet (Default)</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="51bc7-108">CimSessionAndPathSet</span><span class="sxs-lookup"><span data-stu-id="51bc7-108">CimSessionAndPathSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] -CimSession <CimSession[]> [-ThrottleLimit <Int32>]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="51bc7-109">ComputerNameAndUseExistingSet</span><span class="sxs-lookup"><span data-stu-id="51bc7-109">ComputerNameAndUseExistingSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-UseExisting] [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="51bc7-110">CimSessionAndUseExistingSet</span><span class="sxs-lookup"><span data-stu-id="51bc7-110">CimSessionAndUseExistingSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] -CimSession <CimSession[]> [-ThrottleLimit <Int32>] [-UseExisting]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="51bc7-111">설명</span><span class="sxs-lookup"><span data-stu-id="51bc7-111">DESCRIPTION</span></span>
<span data-ttu-id="51bc7-112">**Start-DscConfiguration** cmdlet은 노드에 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-112">The **Start-DscConfiguration** cmdlet applies configuration to nodes.</span></span>
<span data-ttu-id="51bc7-113">*UseExisting* 매개 변수와 함께 사용 하는 경우 대상 컴퓨터의 기존 구성이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-113">When used with the *UseExisting* parameter, the existing configuration on the target computer is applied.</span></span>
<span data-ttu-id="51bc7-114">컴퓨터 이름을 지정 하거나 CIM(Common Information Model) (CIM) 세션을 사용 하 여 구성을 적용할 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-114">Specify which computers that you want to apply configuration to by specifying computer names or by using Common Information Model (CIM) sessions.</span></span>

<span data-ttu-id="51bc7-115">기본적으로 이 cmdlet은 작업을 만들고 **Job** 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-115">By default, this cmdlet creates a job and returns a **Job** object.</span></span>
<span data-ttu-id="51bc7-116">백그라운드 작업에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help about_Jobs` .</span><span class="sxs-lookup"><span data-stu-id="51bc7-116">For more information about background jobs, type `Get-Help about_Jobs`.</span></span>
<span data-ttu-id="51bc7-117">이 cmdlet을 대화형으로 사용하려면 *Wait* 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-117">To use this cmdlet interactively, specify the *Wait* parameter.</span></span>

<span data-ttu-id="51bc7-118">구성 설정을 적용할 때 cmdlet이 수행하는 작업의 세부 정보를 보려면 *Verbose* 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-118">Specify the *Verbose* parameter to see details of what the cmdlet does when it applies configuration settings.</span></span>

## <span data-ttu-id="51bc7-119">예제</span><span class="sxs-lookup"><span data-stu-id="51bc7-119">EXAMPLES</span></span>

### <span data-ttu-id="51bc7-120">예제 1: 구성 설정 적용</span><span class="sxs-lookup"><span data-stu-id="51bc7-120">Example 1: Apply configuration settings</span></span>

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="51bc7-121">이 명령은 C:\DSC\Configurations\에 설정이 있는 모든 컴퓨터에 해당 폴더의 구성 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-121">This command applies the configuration settings from C:\DSC\Configurations\ to the every computer that has settings in that folder.</span></span>
<span data-ttu-id="51bc7-122">또한 배포된 각 대상 노드에 대한 **Job** 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-122">The command returns **Job** objects for each target node deployed to.</span></span>

### <span data-ttu-id="51bc7-123">예제 2: 구성 설정 적용 및 구성이 완료 될 때까지 대기</span><span class="sxs-lookup"><span data-stu-id="51bc7-123">Example 2: Apply configuration settings and wait for configuration to complete</span></span>

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -Wait -Verbose
```

<span data-ttu-id="51bc7-124">이 명령은 C:\DSC\Configurations\의 구성을 로컬 컴퓨터에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-124">This command applies the configuration from C:\DSC\Configurations\ to the local computer.</span></span>
<span data-ttu-id="51bc7-125">또한 배포된 각 대상 노드(이 경우 로컬 컴퓨터만 해당)에 대한 **Job** 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-125">The command returns **Job** objects for each target node deployed to, in this case, just the local computer.</span></span>
<span data-ttu-id="51bc7-126">이 예에서는 *Verbose* 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-126">This example specifies the *Verbose* parameter.</span></span>
<span data-ttu-id="51bc7-127">따라서 명령이 진행 됨에 따라 콘솔에 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-127">Therefore, the command sends messages to the console as it proceeds.</span></span>
<span data-ttu-id="51bc7-128">이 명령에는 *Wait* 매개 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-128">The command includes the *Wait* parameter.</span></span>
<span data-ttu-id="51bc7-129">따라서 명령이 모든 구성 작업을 완료할 때까지 콘솔을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-129">Therefore, you cannot use the console until the command finishes all configuration tasks.</span></span>

### <span data-ttu-id="51bc7-130">예제 3: CIM 세션을 사용 하 여 구성 설정 적용</span><span class="sxs-lookup"><span data-stu-id="51bc7-130">Example 3: Apply configuration settings by using a CIM session</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -CimSession $Session
```

<span data-ttu-id="51bc7-131">이 예제에서는 지정한 컴퓨터에 구성 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-131">This example applies configuration settings to a specified computer.</span></span>
<span data-ttu-id="51bc7-132">또한 cmdlet에 사용하기 위해 이름이 Server01인 컴퓨터에 대한 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-132">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="51bc7-133">또는 지정한 여러 컴퓨터에 cmdlet을 적용하기 위해 CIM 세션 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-133">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="51bc7-134">첫 번째 명령은 **New-CimSession** cmdlet을 사용하여 CIM 세션을 만든 다음 **CimSession** 개체를 $Session 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-134">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="51bc7-135">또한 암호를 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-135">The command prompts you for a password.</span></span>
<span data-ttu-id="51bc7-136">자세한 내용을 보려면 `Get-Help NewCimSession`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="51bc7-136">For more information, type `Get-Help NewCimSession`.</span></span>

<span data-ttu-id="51bc7-137">두 번째 명령은 $Session 변수에 저장 된 **CimSession** 개체로 식별 된 컴퓨터에 C:\wom\configurations\의 구성 설정을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-137">The second command applies the configuration settings from C:\DSC\Configurations\ to the computers identified by the **CimSession** objects stored in the $Session variable.</span></span>
<span data-ttu-id="51bc7-138">이 예제에서는 $Session 변수에 이름이 $Server01인 컴퓨터에 대한 CIM 세션만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-138">In this example, the $Session variable contains a CIM session only for the computer named Server01.</span></span>
<span data-ttu-id="51bc7-139">명령이 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-139">The command applies the configuration.</span></span>
<span data-ttu-id="51bc7-140">또한 구성된 각 컴퓨터에 대한 **Job** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-140">The command creates **Job** objects for each configured computer.</span></span>

## <span data-ttu-id="51bc7-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="51bc7-141">PARAMETERS</span></span>

### <span data-ttu-id="51bc7-142">-CimSession</span><span class="sxs-lookup"><span data-stu-id="51bc7-142">-CimSession</span></span>
<span data-ttu-id="51bc7-143">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-143">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="51bc7-144">[CimSession](/powershell/module/cimcmdlets/new-cimsession) 또는 [CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-144">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="51bc7-145">기본값은 로컬 컴퓨터의 현재 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-145">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="51bc7-146">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="51bc7-146">-ComputerName</span></span>
<span data-ttu-id="51bc7-147">컴퓨터 이름 배열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-147">Specifies an array of computer names.</span></span>
<span data-ttu-id="51bc7-148">이 매개 변수는 *Path* 매개 변수의 구성 문서를 포함 하는 컴퓨터를 배열에 지정 된 것으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-148">This parameter restricts the computers that have configuration documents in the *Path* parameter to those specified in the array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="51bc7-149">-Credential</span><span class="sxs-lookup"><span data-stu-id="51bc7-149">-Credential</span></span>
<span data-ttu-id="51bc7-150">대상 컴퓨터에 대한 사용자 이름과 암호를 **PSCredential** 개체로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-150">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="51bc7-151">**PSCredential** 개체를 가져오려면 Get-Credential cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-151">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="51bc7-152">자세한 내용을 보려면 `Get-Help Get-Credential`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="51bc7-152">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51bc7-153">-Force</span><span class="sxs-lookup"><span data-stu-id="51bc7-153">-Force</span></span>
<span data-ttu-id="51bc7-154">대상 컴퓨터에서 현재 실행 되 고 있는 구성 작업을 중지 하 고 새 Start-Configuration 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-154">Stops the configuration operation currently running on the target computer and begins the new Start-Configuration operation.</span></span>
<span data-ttu-id="51bc7-155">로컬 Configuration Manager의 **Refreshmode** 속성이 **Pull** 로 설정 되어 있으면이 매개 변수를 지정 하면 **푸시** 로 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-155">If the **RefreshMode** property of the Local Configuration Manager is set to **Pull** , specifying this parameter changes it to **Push** .</span></span>

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

### <span data-ttu-id="51bc7-156">-JobName</span><span class="sxs-lookup"><span data-stu-id="51bc7-156">-JobName</span></span>
<span data-ttu-id="51bc7-157">작업의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-157">Specifies a friendly name for a job.</span></span>
<span data-ttu-id="51bc7-158">이 매개 변수를 지정하면 cmdlet이 작업으로 실행되고 **Job** 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-158">If you specify this parameter, the cmdlet runs as a job, and it returns a **Job** object.</span></span>

<span data-ttu-id="51bc7-159">기본적으로 Windows PowerShell은 이름 JobN을 할당 합니다. 여기서 N은 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-159">By default, Windows PowerShell assigns the name JobN where N is an integer.</span></span>

<span data-ttu-id="51bc7-160">*Wait* 매개 변수를 지정하는 경우 이 매개 변수를 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="51bc7-160">If you specify the *Wait* parameter, do not specify this parameter.</span></span>

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

### <span data-ttu-id="51bc7-161">-Path</span><span class="sxs-lookup"><span data-stu-id="51bc7-161">-Path</span></span>
<span data-ttu-id="51bc7-162">구성 설정 파일이 포함된 폴더의 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-162">Specifies a file path of a folder that contains configuration settings files.</span></span>
<span data-ttu-id="51bc7-163">이 cmdlet은 지정 된 경로에 설정 파일이 있는 컴퓨터에 이러한 구성 설정을 게시 하 고 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-163">This cmdlet publishes and applies these configuration settings to computers that have settings files in the specified path.</span></span>
<span data-ttu-id="51bc7-164">각 대상 노드에는 다음 형식의 설정 파일이 있어야 합니다. NetBIOS 이름. mof.</span><span class="sxs-lookup"><span data-stu-id="51bc7-164">Each target node must have a settings file of the following format: NetBIOS Name.mof.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51bc7-165">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="51bc7-165">-ThrottleLimit</span></span>
<span data-ttu-id="51bc7-166">cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-166">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="51bc7-167">이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-167">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="51bc7-168">스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-168">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="51bc7-169">-UseExisting</span><span class="sxs-lookup"><span data-stu-id="51bc7-169">-UseExisting</span></span>
<span data-ttu-id="51bc7-170">이 cmdlet이 기존 구성을 적용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-170">Indicates that this cmdlet applies the existing configuration.</span></span>
<span data-ttu-id="51bc7-171">Start-dscconfiguration cmdlet Publish-DscConfiguration을 사용 하 여 **Start-DscConfiguration** 또는 게시를 사용 하 여 대상 컴퓨터에 구성이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-171">The configuration can exist on the target computer by enactment using **Start-DscConfiguration** or by publication using the Publish-DscConfiguration cmdlet.</span></span>

<span data-ttu-id="51bc7-172">이 cmdlet에 대해이 매개 변수를 지정 하기 전에 [Windows PowerShell 5.0의 새로운 기능](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50) 정보를 검토 하십시오.</span><span class="sxs-lookup"><span data-stu-id="51bc7-172">Before you specify this parameter for this cmdlet, review the information in [What's New in Windows PowerShell 5.0](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50)</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameAndUseExistingSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51bc7-173">-Wait</span><span class="sxs-lookup"><span data-stu-id="51bc7-173">-Wait</span></span>
<span data-ttu-id="51bc7-174">Cmdlet이 모든 구성 작업을 완료할 때까지 콘솔을 차단 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-174">Indicates that the cmdlet blocks the console until it finishes all configuration tasks.</span></span>

<span data-ttu-id="51bc7-175">이 매개 변수를 지정하는 경우 *JobName* 매개 변수를 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="51bc7-175">If you specify this parameter, do not specify the *JobName* parameter.</span></span>

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

### <span data-ttu-id="51bc7-176">-Confirm</span><span class="sxs-lookup"><span data-stu-id="51bc7-176">-Confirm</span></span>
<span data-ttu-id="51bc7-177">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-177">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="51bc7-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="51bc7-178">-WhatIf</span></span>
<span data-ttu-id="51bc7-179">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-179">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="51bc7-180">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51bc7-180">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="51bc7-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="51bc7-181">CommonParameters</span></span>
<span data-ttu-id="51bc7-182">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="51bc7-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="51bc7-183">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51bc7-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="51bc7-184">입력</span><span class="sxs-lookup"><span data-stu-id="51bc7-184">INPUTS</span></span>

## <span data-ttu-id="51bc7-185">출력</span><span class="sxs-lookup"><span data-stu-id="51bc7-185">OUTPUTS</span></span>

## <span data-ttu-id="51bc7-186">참고</span><span class="sxs-lookup"><span data-stu-id="51bc7-186">NOTES</span></span>

## <span data-ttu-id="51bc7-187">관련 링크</span><span class="sxs-lookup"><span data-stu-id="51bc7-187">RELATED LINKS</span></span>

[<span data-ttu-id="51bc7-188">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="51bc7-188">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="51bc7-189">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="51bc7-189">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="51bc7-190">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="51bc7-190">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="51bc7-191">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="51bc7-191">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="51bc7-192">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="51bc7-192">Stop-DscConfiguration</span></span>](Stop-DscConfiguration.md)

[<span data-ttu-id="51bc7-193">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="51bc7-193">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

[<span data-ttu-id="51bc7-194">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="51bc7-194">Update-DscConfiguration</span></span>](Update-DscConfiguration.md)

---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/publish-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-DscConfiguration
ms.openlocfilehash: 139de2bfdb88c443e7bc48d36e37e95644556bf5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215305"
---
# <span data-ttu-id="7c03f-103">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="7c03f-103">Publish-DscConfiguration</span></span>

## <span data-ttu-id="7c03f-104">개요</span><span class="sxs-lookup"><span data-stu-id="7c03f-104">SYNOPSIS</span></span>
<span data-ttu-id="7c03f-105">컴퓨터 집합에 DSC 구성을 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-105">Publishes a DSC configuration to a set of computers.</span></span>

## <span data-ttu-id="7c03f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7c03f-106">SYNTAX</span></span>

### <span data-ttu-id="7c03f-107">ComputerNameSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="7c03f-107">ComputerNameSet (Default)</span></span>

```
Publish-DscConfiguration [-Path] <String> [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7c03f-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="7c03f-108">CimSessionSet</span></span>

```
Publish-DscConfiguration [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7c03f-109">설명</span><span class="sxs-lookup"><span data-stu-id="7c03f-109">DESCRIPTION</span></span>
<span data-ttu-id="7c03f-110">**Start-dscconfiguration** cmdlet은 컴퓨터 집합에 WINDOWS PowerShell DSC (필요한 상태 구성) 구성 문서를 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-110">The **Publish-DscConfiguration** cmdlet publishes a Windows PowerShell Desired State Configuration (DSC) configuration document on set of computers.</span></span>
<span data-ttu-id="7c03f-111">이 cmdlet은 구성을 적용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-111">This cmdlet does not apply the configuration.</span></span>
<span data-ttu-id="7c03f-112">*UseExisting* 매개 변수와 함께 사용 되거나 DSC 엔진에서 일관성 주기를 실행 하는 경우 Start-DscConfiguration cmdlet에 의해 구성이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-112">Configurations are applied by either the Start-DscConfiguration cmdlet when it is used with the *UseExisting* parameter or when the DSC engine runs its consistency cycle.</span></span>
<span data-ttu-id="7c03f-113">DSC 엔진은 로컬 Configuration Manager (LCM) 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-113">The DSC engine is also known as the Local Configuration Manager (LCM).</span></span>

<span data-ttu-id="7c03f-114">이 cmdlet은 여러 구성 문서의 조각이 제공 되는 경우 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-114">This cmdlet is especially useful when fragments of multiple configuration documents are delivered.</span></span>
<span data-ttu-id="7c03f-115">여러 구성 문서 조각이 제공 되 면 이전 구성 문서 조각을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-115">When multiple configuration documents fragments are delivered, they overwrite the older configuration document fragments.</span></span>

## <span data-ttu-id="7c03f-116">예제</span><span class="sxs-lookup"><span data-stu-id="7c03f-116">EXAMPLES</span></span>

### <span data-ttu-id="7c03f-117">예제 1: 원격 컴퓨터에 구성 게시</span><span class="sxs-lookup"><span data-stu-id="7c03f-117">Example 1: Publish a configuration to a remote computer</span></span>

```
PS C:\> Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

<span data-ttu-id="7c03f-118">이 명령은 원격 컴퓨터에 구성을 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-118">This command publishes a configuration to a remote computer.</span></span>
<span data-ttu-id="7c03f-119">이 cmdlet을 실행 하는 사용자는 원격 컴퓨터의 관리자 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-119">The user who runs the cmdlet should be administrator on the remote computer.</span></span>

## <span data-ttu-id="7c03f-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7c03f-120">PARAMETERS</span></span>

### <span data-ttu-id="7c03f-121">-CimSession</span><span class="sxs-lookup"><span data-stu-id="7c03f-121">-CimSession</span></span>
<span data-ttu-id="7c03f-122">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-122">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="7c03f-123">[CimSession](/powershell/module/cimcmdlets/new-cimsession) 또는 [CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-123">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="7c03f-124">기본값은 로컬 컴퓨터의 현재 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-124">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="7c03f-125">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="7c03f-125">-ComputerName</span></span>
<span data-ttu-id="7c03f-126">이 cmdlet이 구성을 게시 하는 컴퓨터를 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-126">Specifies one or more computers on which this cmdlet publishes the configuration.</span></span>

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

### <span data-ttu-id="7c03f-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="7c03f-127">-Credential</span></span>
<span data-ttu-id="7c03f-128">대상 장치에 액세스 하는 데 사용 되는 자격 증명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-128">Specifies credentials that are used to access the target device.</span></span>

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

### <span data-ttu-id="7c03f-129">-Force</span><span class="sxs-lookup"><span data-stu-id="7c03f-129">-Force</span></span>
<span data-ttu-id="7c03f-130">Cmdlet을 강제로 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-130">Forces the cmdlet to finish.</span></span>
<span data-ttu-id="7c03f-131">로컬 Configuration Manager 새로 고침 모드를 PULL로 설정 하면이 매개 변수를 사용 하면 밀어넣기로 바뀌고 DSC 구성의 게시를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-131">If the Local Configuration Manager refresh mode is set to PULL, usage of this parameter changes it to PUSH and enables publication of the DSC configuration.</span></span>
<span data-ttu-id="7c03f-132">또한 보류 중인 DSC 구성이 있으면이 매개 변수를 사용 하 여 보류 중인 구성을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-132">Also, if a pending DSC configuration exists, usage of this parameter overwrites that pending configuration.</span></span>

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

### <span data-ttu-id="7c03f-133">-Path</span><span class="sxs-lookup"><span data-stu-id="7c03f-133">-Path</span></span>
<span data-ttu-id="7c03f-134">대상 컴퓨터에 게시할 구성이 포함 된 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-134">Specifies a path that contains configurations to publish to target computers.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c03f-135">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="7c03f-135">-ThrottleLimit</span></span>
<span data-ttu-id="7c03f-136">cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-136">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="7c03f-137">이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-137">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="7c03f-138">스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-138">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="7c03f-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7c03f-139">-Confirm</span></span>
<span data-ttu-id="7c03f-140">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7c03f-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7c03f-141">-WhatIf</span></span>
<span data-ttu-id="7c03f-142">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-142">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7c03f-143">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c03f-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7c03f-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7c03f-144">CommonParameters</span></span>
<span data-ttu-id="7c03f-145">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7c03f-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7c03f-146">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c03f-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7c03f-147">입력</span><span class="sxs-lookup"><span data-stu-id="7c03f-147">INPUTS</span></span>

## <span data-ttu-id="7c03f-148">출력</span><span class="sxs-lookup"><span data-stu-id="7c03f-148">OUTPUTS</span></span>

## <span data-ttu-id="7c03f-149">참고</span><span class="sxs-lookup"><span data-stu-id="7c03f-149">NOTES</span></span>

## <span data-ttu-id="7c03f-150">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7c03f-150">RELATED LINKS</span></span>

[<span data-ttu-id="7c03f-151">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="7c03f-151">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="7c03f-152">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="7c03f-152">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="7c03f-153">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="7c03f-153">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="7c03f-154">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="7c03f-154">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="7c03f-155">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="7c03f-155">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="7c03f-156">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="7c03f-156">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

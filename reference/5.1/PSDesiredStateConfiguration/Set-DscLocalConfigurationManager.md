---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 04/29/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/set-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-DscLocalConfigurationManager
ms.openlocfilehash: 0d35aa56a52f0e6c17abd0e7b2707869e780324c
ms.sourcegitcommit: 0d4d3e47f6979876550591f62061096e7a568f7e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2020
ms.locfileid: "93218017"
---
# <span data-ttu-id="ef800-103">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ef800-103">Set-DscLocalConfigurationManager</span></span>

## <span data-ttu-id="ef800-104">개요</span><span class="sxs-lookup"><span data-stu-id="ef800-104">SYNOPSIS</span></span>

<span data-ttu-id="ef800-105">LCM (로컬 Configuration Manager) 설정을 노드에 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-105">Applies Local Configuration Manager (LCM) settings to nodes.</span></span>

## <span data-ttu-id="ef800-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ef800-106">SYNTAX</span></span>

### <span data-ttu-id="ef800-107">ComputerNameSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="ef800-107">ComputerNameSet (Default)</span></span>

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ef800-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="ef800-108">CimSessionSet</span></span>

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ef800-109">설명</span><span class="sxs-lookup"><span data-stu-id="ef800-109">DESCRIPTION</span></span>

<span data-ttu-id="ef800-110">`Set-DscLocalConfigurationManager`Cmdlet은 LCM 설정 또는 메타 구성을 노드에 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-110">The `Set-DscLocalConfigurationManager` cmdlet applies LCM settings, or meta-configuration, to nodes.</span></span> <span data-ttu-id="ef800-111">컴퓨터 이름을 지정하거나 CIM(Common Information Model) 세션을 사용하여 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-111">Specify computers by specifying computer names or by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="ef800-112">대상 컴퓨터를 지정하지 않으면 cmdlet이 로컬 컴퓨터에 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-112">If you do not specify a target computer, the cmdlet applies settings to the local computer.</span></span>

## <span data-ttu-id="ef800-113">예제</span><span class="sxs-lookup"><span data-stu-id="ef800-113">EXAMPLES</span></span>

### <span data-ttu-id="ef800-114">예제 1: LCM 설정 적용</span><span class="sxs-lookup"><span data-stu-id="ef800-114">Example 1: Apply LCM settings</span></span>

```
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="ef800-115">이 명령은에서 대상 노드에 LCM 설정을 적용 `C:\DSC\Configurations\` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-115">This command applies the LCM settings from `C:\DSC\Configurations\` to the targeted nodes.</span></span> <span data-ttu-id="ef800-116">설정을 받은 후 LCM에서 해당 설정을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-116">After receiving the settings, LCM processes them.</span></span>

> [!WARNING]
> <span data-ttu-id="ef800-117">지정 된 폴더에 저장 된 동일한 컴퓨터에 대 한 메타 mof 여러 개 있는 경우 첫 번째 메타 mof만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-117">If there are multiple meta mofs for the same computer stored in the specified folder, only the first meta mof will be applied.</span></span>

### <span data-ttu-id="ef800-118">예제 2: CIM 세션을 사용 하 여 LCM 설정 적용</span><span class="sxs-lookup"><span data-stu-id="ef800-118">Example 2: Apply LCM settings by using a CIM session</span></span>

```
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\" -CimSession $Session
```

<span data-ttu-id="ef800-119">이 예제에서는 컴퓨터에 LCM 설정을 적용 하 고 설정을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-119">This example applies LCM settings to a computer and applies the settings.</span></span> <span data-ttu-id="ef800-120">또한 cmdlet에 사용하기 위해 이름이 Server01인 컴퓨터에 대한 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-120">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span> <span data-ttu-id="ef800-121">또는 지정한 여러 컴퓨터에 cmdlet을 적용하기 위해 CIM 세션 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-121">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="ef800-122">첫 번째 명령은 cmdlet을 사용 하 여 CIM 세션을 만든 `New-CimSession` 다음 변수에 **CimSession** 개체를 저장 합니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="ef800-122">The first command creates a CIM session by using the `New-CimSession` cmdlet, and then stores the **CimSession** object in the `$Session` variable.</span></span> <span data-ttu-id="ef800-123">또한 암호를 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-123">The command prompts you for a password.</span></span> <span data-ttu-id="ef800-124">자세한 내용을 보려면 `Get-Help New-CimSession`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="ef800-124">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="ef800-125">두 번째 명령은에서 대상 노드에 대 한 LCM 설정을 `C:\DSC\Configurations\` 변수에 저장 된 **CimSession** 개체로 식별 된 컴퓨터에 적용 `$Session` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-125">The second command applies LCM settings for the targeted node from `C:\DSC\Configurations\` to the computer identified by the **CimSession** objects stored in the `$Session` variable.</span></span> <span data-ttu-id="ef800-126">이 예에서 `$Session` 변수는 이름이 Server01 인 컴퓨터에 대 한 CIM 세션을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-126">In this example, the `$Session` variable contains a CIM session only for the computer named Server01.</span></span> <span data-ttu-id="ef800-127">명령이 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-127">The command applies the settings.</span></span> <span data-ttu-id="ef800-128">설정을 받은 후 LCM에서 해당 설정을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-128">After receiving the settings, LCM processes them.</span></span>

## <span data-ttu-id="ef800-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ef800-129">PARAMETERS</span></span>

### <span data-ttu-id="ef800-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="ef800-130">-CimSession</span></span>

<span data-ttu-id="ef800-131">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-131">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="ef800-132">[CimSession](/powershell/module/CimCmdlets/New-CimSession) 또는 [CimSession](/powershell/module/CimCmdlets/Get-CimSession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-132">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) or [Get-CimSession](/powershell/module/CimCmdlets/Get-CimSession) cmdlet.</span></span>
<span data-ttu-id="ef800-133">기본값은 로컬 컴퓨터의 현재 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-133">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="ef800-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ef800-134">-ComputerName</span></span>

<span data-ttu-id="ef800-135">컴퓨터 이름 배열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-135">Specifies an array of computer names.</span></span> <span data-ttu-id="ef800-136">이 매개 변수는 **Path** 매개 변수에서 메타 구성 문서가 있는 컴퓨터를 배열에 지정 된 것으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-136">This parameter restricts the computers that have meta-configuration documents in the **Path** parameter to those specified in the array.</span></span>

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

### <span data-ttu-id="ef800-137">-Credential</span><span class="sxs-lookup"><span data-stu-id="ef800-137">-Credential</span></span>

<span data-ttu-id="ef800-138">대상 컴퓨터에 대한 사용자 이름과 암호를 **PSCredential** 개체로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-138">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span> <span data-ttu-id="ef800-139">**PSCredential** 개체를 가져오려면 Get-Credential cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-139">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span> <span data-ttu-id="ef800-140">자세한 내용을 보려면 `Get-Help Get-Credential`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="ef800-140">For more information, type `Get-Help Get-Credential`.</span></span>

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

### <span data-ttu-id="ef800-141">-Force</span><span class="sxs-lookup"><span data-stu-id="ef800-141">-Force</span></span>

<span data-ttu-id="ef800-142">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-142">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ef800-143">-Path</span><span class="sxs-lookup"><span data-stu-id="ef800-143">-Path</span></span>

<span data-ttu-id="ef800-144">구성 설정 파일이 포함된 폴더의 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-144">Specifies a file path of a folder that contains configuration settings files.</span></span> <span data-ttu-id="ef800-145">Cmdlet은 지정 된 경로에 설정 파일이 있는 컴퓨터에 이러한 LCM 설정을 게시 하 고 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-145">The cmdlet publishes and applies these LCM settings to computers that have settings files in the specified path.</span></span> <span data-ttu-id="ef800-146">각 대상 노드에는 다음 형식의 설정 파일이 있어야 합니다 `NetBIOS Name.meta.mof` ..</span><span class="sxs-lookup"><span data-stu-id="ef800-146">Each target node must have a settings file of the following format: `NetBIOS Name.meta.mof`.</span></span>

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

### <span data-ttu-id="ef800-147">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="ef800-147">-ThrottleLimit</span></span>

<span data-ttu-id="ef800-148">cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-148">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span> <span data-ttu-id="ef800-149">이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-149">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span> <span data-ttu-id="ef800-150">스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-150">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="ef800-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ef800-151">-Confirm</span></span>

<span data-ttu-id="ef800-152">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ef800-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ef800-153">-WhatIf</span></span>

<span data-ttu-id="ef800-154">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ef800-155">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef800-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ef800-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ef800-156">CommonParameters</span></span>

<span data-ttu-id="ef800-157">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ef800-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ef800-158">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef800-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ef800-159">입력</span><span class="sxs-lookup"><span data-stu-id="ef800-159">INPUTS</span></span>

## <span data-ttu-id="ef800-160">출력</span><span class="sxs-lookup"><span data-stu-id="ef800-160">OUTPUTS</span></span>

## <span data-ttu-id="ef800-161">참고</span><span class="sxs-lookup"><span data-stu-id="ef800-161">NOTES</span></span>

## <span data-ttu-id="ef800-162">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ef800-162">RELATED LINKS</span></span>

[<span data-ttu-id="ef800-163">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="ef800-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="ef800-164">Get DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ef800-164">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)

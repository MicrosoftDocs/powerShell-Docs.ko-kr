---
external help file: Get-DSCLocalConfigurationManager.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get DscLocalConfigurationManager
ms.openlocfilehash: 162770d8eb3a8953dcfaeb31f30742a46353b33b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215314"
---
# <span data-ttu-id="554f2-103">Get DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="554f2-103">Get-DscLocalConfigurationManager</span></span>

## <span data-ttu-id="554f2-104">개요</span><span class="sxs-lookup"><span data-stu-id="554f2-104">SYNOPSIS</span></span>

<span data-ttu-id="554f2-105">노드의 로컬 Configuration Manager (LCM) 설정 및 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-105">Gets Local Configuration Manager (LCM) settings and states for the node.</span></span>

## <span data-ttu-id="554f2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="554f2-106">SYNTAX</span></span>

```
Get-DscLocalConfigurationManager [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## <span data-ttu-id="554f2-107">설명</span><span class="sxs-lookup"><span data-stu-id="554f2-107">DESCRIPTION</span></span>

<span data-ttu-id="554f2-108">`Get-DscLocalConfigurationManager`Cmdlet은 lcm 설정, 메타 구성 및 해당 노드에 대 한 lcm의 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-108">The `Get-DscLocalConfigurationManager` cmdlet gets LCM settings, or meta-configuration, and the states of LCM for the node.</span></span> <span data-ttu-id="554f2-109">CIM(Common Information Model) 세션을 사용하여 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-109">Specify computers by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="554f2-110">대상 컴퓨터를 지정하지 않으면 cmdlet이 로컬 컴퓨터의 구성 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-110">If you do not specify a target computer, the cmdlet gets the configuration settings from the local computer.</span></span>

## <span data-ttu-id="554f2-111">예제</span><span class="sxs-lookup"><span data-stu-id="554f2-111">EXAMPLES</span></span>

### <span data-ttu-id="554f2-112">예 1: 로컬 컴퓨터에 대 한 LCM 설정 가져오기</span><span class="sxs-lookup"><span data-stu-id="554f2-112">Example 1: Get LCM settings for the local computer</span></span>

```powershell
Get-DscLocalConfigurationManager
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 47edd8c9-2798-4827-839a-b35cc87e69fb
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName
```

<span data-ttu-id="554f2-113">이 명령은 로컬 컴퓨터의 LCM 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-113">This command gets LCM settings for the local computer.</span></span>

<span data-ttu-id="554f2-114">출력의 개별 특성에 대 한 자세한 내용은 [로컬 Configuration Manager 구성](../../docs-conceptual/dsc/managing-nodes/metaconfig.md#basic-settings) 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="554f2-114">For more information on the individual attributes of the output, see the [Configuring the Local Configuration Manager](../../docs-conceptual/dsc/managing-nodes/metaconfig.md#basic-settings) documentation.</span></span>

### <span data-ttu-id="554f2-115">예 2: 지정 된 컴퓨터에 대 한 LCM 설정 가져오기</span><span class="sxs-lookup"><span data-stu-id="554f2-115">Example 2: Get LCM settings for a specified computer</span></span>

```powershell
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Get-DscLocalConfigurationManager -CimSession $Session
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 169dfa57-a7f9-43be-a7a5-9dd06587e052
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName                 : Server01
PSComputerName                 : Server01
```

<span data-ttu-id="554f2-116">이 예제에서는 CIM 세션에 지정 된 컴퓨터에 대 한 LCM 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-116">This example gets LCM settings for a computer specified by a CIM session.</span></span>
<span data-ttu-id="554f2-117">또한 cmdlet에 사용하기 위해 이름이 Server01인 컴퓨터에 대한 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-117">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="554f2-118">또는 지정한 여러 컴퓨터에 cmdlet을 적용하기 위해 CIM 세션 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-118">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="554f2-119">첫 번째 명령은 cmdlet을 사용 하 여 CIM 세션을 만든 `New-CimSession` 다음 $Session 변수에 **CimSession** 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-119">The first command creates a CIM session by using the `New-CimSession` cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span> <span data-ttu-id="554f2-120">또한 암호를 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-120">The command prompts you for a password.</span></span> <span data-ttu-id="554f2-121">자세한 내용을 보려면 `Get-Help New-CimSession`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="554f2-121">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="554f2-122">두 번째 명령은 $Session 변수에 저장 된 **CimSession** 개체로 식별 되는 컴퓨터에 대 한 로컬 Configuration Manager 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-122">The second command gets Local Configuration Manager settings for the computers identified by the **CimSession** objects stored in the $Session variable.</span></span> <span data-ttu-id="554f2-123">이 경우 이름이 Server01 인 컴퓨터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-123">In this case, the computer named Server01.</span></span>

## <span data-ttu-id="554f2-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="554f2-124">PARAMETERS</span></span>

### <span data-ttu-id="554f2-125">-AsJob</span><span class="sxs-lookup"><span data-stu-id="554f2-125">-AsJob</span></span>

<span data-ttu-id="554f2-126">이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-126">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="554f2-127">-CimSession</span><span class="sxs-lookup"><span data-stu-id="554f2-127">-CimSession</span></span>

<span data-ttu-id="554f2-128">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-128">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="554f2-129">컴퓨터 이름 또는 세션 개체 (예: 또는 cmdlet의 출력)를 입력 `New-CimSession` 합니다 `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="554f2-129">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span>

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

### <span data-ttu-id="554f2-130">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="554f2-130">-ThrottleLimit</span></span>

<span data-ttu-id="554f2-131">cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="554f2-131">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

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

### <span data-ttu-id="554f2-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="554f2-132">CommonParameters</span></span>

<span data-ttu-id="554f2-133">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="554f2-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="554f2-134">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="554f2-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="554f2-135">입력</span><span class="sxs-lookup"><span data-stu-id="554f2-135">INPUTS</span></span>

## <span data-ttu-id="554f2-136">출력</span><span class="sxs-lookup"><span data-stu-id="554f2-136">OUTPUTS</span></span>

## <span data-ttu-id="554f2-137">참고</span><span class="sxs-lookup"><span data-stu-id="554f2-137">NOTES</span></span>

## <span data-ttu-id="554f2-138">관련 링크</span><span class="sxs-lookup"><span data-stu-id="554f2-138">RELATED LINKS</span></span>

[<span data-ttu-id="554f2-139">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="554f2-139">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="554f2-140">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="554f2-140">Set-DscLocalConfigurationManager</span></span>](Set-DscLocalConfigurationManager.md)

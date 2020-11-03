---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowexecutionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowExecutionOption
ms.openlocfilehash: db5d19396f555a41ad14552823c57f3b11c79321
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218289"
---
# <span data-ttu-id="54411-103">New-PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="54411-103">New-PSWorkflowExecutionOption</span></span>

## <span data-ttu-id="54411-104">개요</span><span class="sxs-lookup"><span data-stu-id="54411-104">SYNOPSIS</span></span>

<span data-ttu-id="54411-105">워크플로 세션에 대한 세션 구성 옵션을 포함하는 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="54411-105">Creates an object that contains session configuration options for workflow sessions.</span></span>

## <span data-ttu-id="54411-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="54411-106">SYNTAX</span></span>

```
New-PSWorkflowExecutionOption [-PersistencePath <String>] [-MaxPersistenceStoreSizeGB <Int64>]
 [-PersistWithEncryption] [-MaxRunningWorkflows <Int32>] [-AllowedActivity <String[]>]
 [-OutOfProcessActivity <String[]>] [-EnableValidation] [-MaxDisconnectedSessions <Int32>]
 [-MaxConnectedSessions <Int32>] [-MaxSessionsPerWorkflow <Int32>] [-MaxSessionsPerRemoteNode <Int32>]
 [-MaxActivityProcesses <Int32>] [-ActivityProcessIdleTimeoutSec <Int32>]
 [-RemoteNodeSessionIdleTimeoutSec <Int32>] [-SessionThrottleLimit <Int32>]
 [-WorkflowShutdownTimeoutMSec <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="54411-107">설명</span><span class="sxs-lookup"><span data-stu-id="54411-107">DESCRIPTION</span></span>

<span data-ttu-id="54411-108">`New-PSWorkflowExecutionOption`Cmdlet은 Windows PowerShell 워크플로 워크플로를 실행 하도록 설계 된 세션 구성 인 워크플로 세션 구성에 대 한 고급 옵션을 포함 하는 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="54411-108">The `New-PSWorkflowExecutionOption` cmdlet creates an object that contains advanced options for workflow session configurations, that is session configurations designed to run Windows PowerShell Workflow workflows.</span></span>

<span data-ttu-id="54411-109">**PSWorkflowExecutionOption** `New-PSWorkflowExecutionOption` 및 cmdlet과 같은 세션 구성을 만들거나 변경 하는 Cmdlet의 **sessiontypeoption** 매개 변수 값으로 생성 되는 psworkflowexecutionoption 개체를 사용할 수 있습니다 `Register-PSSessionConfiguration` `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="54411-109">You can use the **PSWorkflowExecutionOption** object that `New-PSWorkflowExecutionOption` generates as the value of the **SessionTypeOption** parameter of cmdlets that create or change a session configuration, such as the `Register-PSSessionConfiguration` and `Set-PSSessionConfiguration` cmdlets.</span></span>

<span data-ttu-id="54411-110">Cmdlet의 각 매개 변수는 `New-PSWorkflowExecutionOption` cmdlet이 반환 하는 워크플로 세션 구성 옵션 개체의 속성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="54411-110">Each parameter of the `New-PSWorkflowExecutionOption` cmdlet represents a property of the workflow session configuration option object that the cmdlet returns.</span></span> <span data-ttu-id="54411-111">매개 변수를 생략하면 이 cmdlet은 속성의 기본값으로 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="54411-111">If you omit a parameter, the cmdlet creates the object with a default value for the property.</span></span>

<span data-ttu-id="54411-112">`New-PSWorkflowExecutionOption`이 cmdlet은 Windows PowerShell 워크플로 기능의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-112">The `New-PSWorkflowExecutionOption` cmdlet is part of the Windows PowerShell Workflow feature.</span></span>

<span data-ttu-id="54411-113">또한 이 명령에 워크플로 일반 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54411-113">You can also add workflow common parameters to this command.</span></span> <span data-ttu-id="54411-114">워크플로 일반 매개 변수에 대 한 자세한 내용은 [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54411-114">For more information about workflow common parameters, see [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md).</span></span>

<span data-ttu-id="54411-115">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="54411-115">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="54411-116">예제</span><span class="sxs-lookup"><span data-stu-id="54411-116">EXAMPLES</span></span>

### <span data-ttu-id="54411-117">예제 1: 워크플로 옵션 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="54411-117">Example 1: Create a Workflow Options Object</span></span>

```powershell
New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
```

```Output
SessionThrottleLimit                       : 100
PersistencePath                            : C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell\WF\PS
MaxPersistenceStoreSizeGB                  : 10
PersistWithEncryption                      : False
MaxRunningWorkflows                        : 30
AllowedActivity                            : {PSDefaultActivities}
OutOfProcessActivity                       : {InlineScript}
EnableValidation                           : True
MaxDisconnectedSessions                    : 200
MaxConnectedSessions                       : 100
MaxSessionsPerWorkflow                     : 10
MaxSessionsPerRemoteNode                   : 5
MaxActivityProcesses                       : 5
ActivityProcessIdleTimeoutSec              : 60
RemoteNodeSessionIdleTimeoutSec            : 60
WorkflowShutdownTimeoutMSec                : 500
```

<span data-ttu-id="54411-118">이 명령은 cmdlet을 사용 하 여 `New-PSWorkflowExecutionOption` **Maxsessionsperworkflow** 값을 10으로 늘리고 **MaxDisconnectedSessions** 값을 200로 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-118">This command uses the `New-PSWorkflowExecutionOption` cmdlet to increase the **MaxSessionsPerWorkflow** value to 10 and decrease the **MaxDisconnectedSessions** value to 200.</span></span>

<span data-ttu-id="54411-119">출력은 이 cmdlet에서 반환하는 개체를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="54411-119">The output shows the object that the cmdlet returns.</span></span>

### <span data-ttu-id="54411-120">예제 2: 워크플로 옵션 개체 사용</span><span class="sxs-lookup"><span data-stu-id="54411-120">Example 2: Using a Workflow Options Object</span></span>

```powershell
# Create a Workflow Options object and save it in a variable
$wo = New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
# Create the ITWorkflow session configuration
Register-PSSessionConfiguration -Name ITWorkflows -SessionTypeOption $wo -Force
```

```Output
    WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=ITWorkflows}                  ITWorkflows
```

```powershell
Get-PSSessionConfiguration ITWorkflows | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITWorkflows
MaxConcurrentCommandsPerShell : 1000
allowedactivity               : PSDefaultActivities
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
maxsessionsperworkflow        : 10
lang                          : en-US
sessionconfigurationdata      : <SessionConfigurationData>
                                    <Param Name='PrivateData'>
                                        <PrivateData>
                                            <ParamName='enablevalidation' Value='True'/>
                                            <Param Name='allowedactivity'Value='PSDefaultActivities' />
                                            <Param Name='outofprocessactivity' Value='InlineScript'/>
                                            <Param Name='maxdisconnectedsessions' Value='200' />
                                            <ParamName='maxsessionsperworkflow' Value='10'/>
                                        </PrivateData>
                                    </Param>
                                </SessionConfigurationData>
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 25
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
outofprocessactivity          : InlineScript
SDKVersion                    : 2
Name                          : ITWorkflows
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
enablevalidation              : True
Enabled                       : True
maxdisconnectedsessions       : 200
MaxShellsPerUser              : 25
Permission                    :
```

<span data-ttu-id="54411-121">처음 두 명령은 새 세션 구성 개체를 만들어 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-121">The first two commands create a new session configuration object and registers it.</span></span>

<span data-ttu-id="54411-122">세 번째 명령은이 cmdlet을 사용 하 여 `Get-PSSessionConfiguration` ITWorkflows 세션 구성 가져오기 및를 사용 하 여 `Format-List` 세션 구성의 모든 속성을 목록으로 표시 합니다. 출력은 세션 구성의 워크플로 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="54411-122">The third command uses the `Get-PSSessionConfiguration` cmdlet to the get the ITWorkflows session configuration and the `Format-List` to display all properties of the session configuration in a list.The output shows that the workflow options in the session configuration.</span></span> <span data-ttu-id="54411-123">특히, 세션 구성에는 **MaxSessionsPerWorkflow** 속성의 값이 10으로 설정되어 있고 **MaxDisconnectedSessions** 속성의 값이 200으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54411-123">Specifically, the session configuration has a **MaxSessionsPerWorkflow** property with a value of 10 and a **MaxDisconnectedSessions** property with a value of 200.</span></span>

## <span data-ttu-id="54411-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="54411-124">PARAMETERS</span></span>

### <span data-ttu-id="54411-125">-ActivityProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="54411-125">-ActivityProcessIdleTimeoutSec</span></span>

<span data-ttu-id="54411-126">각 활동 호스트 프로세스가 유휴 상태가 된 후 유지되는 기간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-126">Determines how long each activity host process is maintained after the process becomes idle.</span></span> <span data-ttu-id="54411-127">간격이 만료되면 프로세스가 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="54411-127">When the interval expires, the process closes.</span></span>

<span data-ttu-id="54411-128">값을 초 단위로 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="54411-128">Enter a value in seconds.</span></span> <span data-ttu-id="54411-129">기본값은 60입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-129">The default value is 60.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-130">-AllowedActivity</span><span class="sxs-lookup"><span data-stu-id="54411-130">-AllowedActivity</span></span>

<span data-ttu-id="54411-131">세션에서 실행이 허용된 활동을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-131">Specifies the activities that are permitted to run in the session.</span></span>

<span data-ttu-id="54411-132">네임 스페이스의 정규화 된 활동 이름 (예:)을 입력 `Microsoft.Powershell.HyperV.Activities.*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-132">Enter namespace-qualified activity names, such as `Microsoft.Powershell.HyperV.Activities.*`.</span></span>
<span data-ttu-id="54411-133">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="54411-133">Wildcard characters are supported.</span></span> <span data-ttu-id="54411-134">기본값 **PSDefaultActivities** 는 기본 제공 Windows Workflow Foundation 활동 및 Windows PowerShell 핵심 cmdlet을 나타내는 활동을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-134">The default value, **PSDefaultActivities** , includes the built-in Windows Workflow Foundation activities and the activities that represent the Windows PowerShell Core cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: PSDefaultActivities
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-135">-EnableValidation</span><span class="sxs-lookup"><span data-stu-id="54411-135">-EnableValidation</span></span>

<span data-ttu-id="54411-136">세션의 모든 워크플로 활동이 허용된 활동 목록에 포함되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-136">Verifies that all workflow activities in the session are included in the allowed activities list.</span></span>

<span data-ttu-id="54411-137">기본값은 True입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-137">The default value is True.</span></span> <span data-ttu-id="54411-138">유효성 검사를 사용 하지 않도록 설정 하려면 다음 명령 형식을 사용 `-EnableValidation:$false` 합니다..</span><span class="sxs-lookup"><span data-stu-id="54411-138">To disable validation, use the following command format: `-EnableValidation:$false`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-139">-MaxActivityProcesses</span><span class="sxs-lookup"><span data-stu-id="54411-139">-MaxActivityProcesses</span></span>

<span data-ttu-id="54411-140">워크플로 활동을 지원하기 위해 세션에서 만들 수 있는 최대 프로세스 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-140">Specifies the maximum number of processes that can be created in the session to support workflow activities.</span></span> <span data-ttu-id="54411-141">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-141">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-142">-MaxConnectedSessions</span><span class="sxs-lookup"><span data-stu-id="54411-142">-MaxConnectedSessions</span></span>

<span data-ttu-id="54411-143">작동 상태인 원격 세션의 최대 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-143">Specifies the maximum number of remote sessions that are in an operational state.</span></span> <span data-ttu-id="54411-144">이 할당량은 모든 원격 노드(대상 컴퓨터)에 연결된 세션에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="54411-144">This quota is applied to sessions connected to all remote nodes (target computers).</span></span> <span data-ttu-id="54411-145">기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-145">The default value is 100.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-146">-MaxDisconnectedSessions</span><span class="sxs-lookup"><span data-stu-id="54411-146">-MaxDisconnectedSessions</span></span>

<span data-ttu-id="54411-147">연결이 끊어진 상태인 원격 세션의 최대 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-147">Specifies the maximum number of remote sessions that are in a disconnected state.</span></span> <span data-ttu-id="54411-148">이 할당량은 모든 원격 노드(대상 컴퓨터)에 연결된 세션에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="54411-148">This quota is applied to sessions connected to all remote nodes (target computers).</span></span> <span data-ttu-id="54411-149">기본값은 1000입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-149">The default value is 1000.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1000
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-150">-MaxPersistenceStoreSizeGB</span><span class="sxs-lookup"><span data-stu-id="54411-150">-MaxPersistenceStoreSizeGB</span></span>

<span data-ttu-id="54411-151">세션에서 실행되는 워크플로에 할당된 지속성 저장소의 최대 크기(GB)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-151">Specifies the maximum size, in gigabytes, of the persistence store allocated to workflows that run in the session.</span></span> <span data-ttu-id="54411-152">크기를 초과하면 지속성 저장소가 확장되어 모든 영구 데이터를 저장하지만 경고가 표시되고 워크플로 이벤트 로그에 메시지가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="54411-152">When the size is exceeded, the persistence store is expanded to save all persisted data, but a warning is displayed and a message is written to the workflow event log.</span></span> <span data-ttu-id="54411-153">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-153">The default value is 10.</span></span>

<span data-ttu-id="54411-154">지속성 저장소는 모든 워크플로 작업의 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-154">The persistence store contains data for all workflow jobs.</span></span> <span data-ttu-id="54411-155">데이터를 저장할 수 있는 기능을 통해 작업이 상태 손실 없이 다시 시작될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54411-155">The ability to store data allows the jobs to resume without losing state.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-156">-MaxRunningWorkflows</span><span class="sxs-lookup"><span data-stu-id="54411-156">-MaxRunningWorkflows</span></span>

<span data-ttu-id="54411-157">세션에서 동시에 실행될 수 있는 최대 워크플로 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-157">Specifies that maximum number of workflows that can run in the session concurrently.</span></span>
<span data-ttu-id="54411-158">기본값은 30입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-158">The default value is 30.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 30
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-159">-MaxSessionsPerRemoteNode</span><span class="sxs-lookup"><span data-stu-id="54411-159">-MaxSessionsPerRemoteNode</span></span>

<span data-ttu-id="54411-160">각 원격 노드(대상 컴퓨터)에 연결할 수 있는 최대 세션 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-160">Specifies the maximum number of sessions that can be connected to each remote node (target computer).</span></span> <span data-ttu-id="54411-161">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-161">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-162">-MaxSessionsPerWorkflow</span><span class="sxs-lookup"><span data-stu-id="54411-162">-MaxSessionsPerWorkflow</span></span>

<span data-ttu-id="54411-163">각 워크플로를 지원하기 위해 만들 수 있는 최대 세션 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-163">Specifies the maximum number of session that can be created to support each workflow.</span></span> <span data-ttu-id="54411-164">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-164">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-165">-OutOfProcessActivity</span><span class="sxs-lookup"><span data-stu-id="54411-165">-OutOfProcessActivity</span></span>

<span data-ttu-id="54411-166">out-of-process를 실행한 허용된 활동( **AllowedActivities** 매개 변수로 지정됨)을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-166">Determines which allowed activities (specified by the **AllowedActivities** parameter) run out-of-process.</span></span> <span data-ttu-id="54411-167">기본값은 **InlineScript** 입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-167">The default value is **InlineScript**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineScript
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-168">-PersistencePath</span><span class="sxs-lookup"><span data-stu-id="54411-168">-PersistencePath</span></span>

<span data-ttu-id="54411-169">워크플로 상태 및 데이터를 저장할 디스크의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-169">Specifies the location on disk where workflow state and data are stored.</span></span> <span data-ttu-id="54411-170">워크플로 상태 및 데이터를 저장하면 워크플로를 일시 중단했다가 다시 시작하고, 중단 및 네트워크 오류에서 워크플로를 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54411-170">Storing the workflow state and data allows workflows to be suspended and resumed, and to recover from interruptions and network failures.</span></span>

<span data-ttu-id="54411-171">기본값은 `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-171">The default value is `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-172">-PersistWithEncryption</span><span class="sxs-lookup"><span data-stu-id="54411-172">-PersistWithEncryption</span></span>

<span data-ttu-id="54411-173">워크플로가 지 속성 저장소의 데이터를 암호화 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="54411-173">Indicates that the workflow encrypts the data in the persistence store.</span></span> <span data-ttu-id="54411-174">네트워크 공유에 지속성 데이터를 저장할 때 이 기능 사용을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="54411-174">Consider using this feature when storing persistence data in a network share.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-175">-RemoteNodeSessionIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="54411-175">-RemoteNodeSessionIdleTimeoutSec</span></span>

<span data-ttu-id="54411-176">원격 노드(대상 컴퓨터)에 연결된 세션이 유지되는 기간을 지정합니다(유휴 상태인 경우).</span><span class="sxs-lookup"><span data-stu-id="54411-176">Specifies how long a session that is connected to a remote node (target computer) is maintained if it is idle.</span></span>

<span data-ttu-id="54411-177">값을 초 단위로 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="54411-177">Enter a value in seconds.</span></span> <span data-ttu-id="54411-178">기본값은 60입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-178">The default value is 60.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-179">-SessionThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="54411-179">-SessionThrottleLimit</span></span>

<span data-ttu-id="54411-180">세션에서 시작된 모든 워크플로를 지원하기 위해 만드는 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-180">Specifies how many operations are created to support all workflows started in the session.</span></span> <span data-ttu-id="54411-181">기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-181">The default value is 100.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-182">-WorkflowShutdownTimeoutMSec</span><span class="sxs-lookup"><span data-stu-id="54411-182">-WorkflowShutdownTimeoutMSec</span></span>

<span data-ttu-id="54411-183">세션의 모든 워크플로가 강제로 일시 중단된 후 세션이 유지되는 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-183">Specifies how long the session is maintained after all workflows in the session are forcibly suspended.</span></span> <span data-ttu-id="54411-184">시간 제한이 만료되면 모든 워크플로가 아직 일시 중단되지 않은 경우에도 Windows PowerShell에서 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="54411-184">When the timeout expires, Windows PowerShell closes the session, even if all workflows are not yet suspended.</span></span>

<span data-ttu-id="54411-185">값을 밀리초 단위로 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="54411-185">Enter a value in milliseconds.</span></span>
<span data-ttu-id="54411-186">기본값은 500입니다.</span><span class="sxs-lookup"><span data-stu-id="54411-186">The default value is 500.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 500
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54411-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="54411-187">CommonParameters</span></span>

<span data-ttu-id="54411-188">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="54411-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="54411-189">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54411-189">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="54411-190">입력</span><span class="sxs-lookup"><span data-stu-id="54411-190">INPUTS</span></span>

### <span data-ttu-id="54411-191">없음</span><span class="sxs-lookup"><span data-stu-id="54411-191">None</span></span>

<span data-ttu-id="54411-192">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54411-192">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="54411-193">출력</span><span class="sxs-lookup"><span data-stu-id="54411-193">OUTPUTS</span></span>

### <span data-ttu-id="54411-194">Microsoft. PowerShell. PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="54411-194">Microsoft.PowerShell.Commands.PSWorkflowExecutionOption</span></span>

## <span data-ttu-id="54411-195">참고</span><span class="sxs-lookup"><span data-stu-id="54411-195">NOTES</span></span>

<span data-ttu-id="54411-196">옵션으로 설정된 최대값을 초과하면 매개 변수 설명에 다른 설명이 없는 한 세션에 다른 인스턴스를 만드는 명령은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-196">When the maximum value set by an option is exceeded, the command to create another instance in the session fails, unless noted in the parameter description.</span></span> <span data-ttu-id="54411-197">예를 들어 **MaxConnectedSessions** 값이 100이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-197">For example, if the value of **MaxConnectedSessions** is 100.</span></span> <span data-ttu-id="54411-198">그러면 원격 노드(대상 컴퓨터)에 대한 101번째 세션을 만드는 명령은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="54411-198">The command to create the 101st session to a remote node (target computer) fails.</span></span>

<span data-ttu-id="54411-199">세션 구성 개체의 속성은 세션 구성에 대해 설정된 옵션과 해당 옵션 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="54411-199">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="54411-200">또한 세션 구성 파일을 사용하는 세션 구성에는 추가 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54411-200">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="54411-201">특히, **PSWorkflowExecutionOptions** 개체가 포함된 세션 구성의 속성은 워크플로 옵션 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="54411-201">In particular, the properties of session configurations that include a **PSWorkflowExecutionOptions** object vary based on the workflow option values.</span></span> <span data-ttu-id="54411-202">예를 들어 세션 구성에 **SessionThrottleLimit** 속성에 대해 기본값이 아닌 값을 설정하는 **PSWorkflowExecutionOptions** 개체가 포함된 경우 세션 구성에 **SessionThrottleLimit** 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="54411-202">For example, if the session configuration includes a **PSWorkflowExecutionOptions** object that sets a non-default value for the **SessionThrottleLimit** property, the session configuration has a **SessionThrottleLimit** property.</span></span> <span data-ttu-id="54411-203">그러지 않으면 이러한 속성을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54411-203">Otherwise, it does not.</span></span>

## <span data-ttu-id="54411-204">관련 링크</span><span class="sxs-lookup"><span data-stu-id="54411-204">RELATED LINKS</span></span>

[<span data-ttu-id="54411-205">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="54411-205">New-PSWorkflowSession</span></span>](New-PSWorkflowSession.md)

[<span data-ttu-id="54411-206">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="54411-206">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="54411-207">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="54411-207">about_WorkflowCommonParameters</span></span>](About/about_WorkflowCommonParameters.md)

---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 보고서 서버 사용
ms.openlocfilehash: 1ccd4f96b782b41b7d7c953735cb41b3ba3d2bce
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953580"
---
# <a name="using-a-dsc-report-server"></a><span data-ttu-id="c5905-103">DSC 보고서 서버 사용</span><span class="sxs-lookup"><span data-stu-id="c5905-103">Using a DSC report server</span></span>

<span data-ttu-id="c5905-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="c5905-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c5905-105">끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="c5905-106">관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>
>
> [!NOTE]
> <span data-ttu-id="c5905-107">이 토픽에 설명된 보고서 서버는 PowerShell 4.0에서 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-107">The report server described in this topic is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="c5905-108">노드의 LCM(로컬 구성 관리자)은 해당 구성 상태에 대한 보고서를 끌어오기 서버에 보내도록 구성할 수 있습니다. 이렇게 하면 해당 데이터를 검색하도록 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-108">The Local Configuration Manager (LCM) of a node can be configured to send reports about its configuration status to a pull server, which can then be queried to retrieve that data.</span></span> <span data-ttu-id="c5905-109">노드는 구성을 확인하고 적용할 때마다 보고서를 보고서 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-109">Each time the node checks and applies a configuration, it sends a report to the report server.</span></span> <span data-ttu-id="c5905-110">이러한 보고서는 서버의 데이터베이스에 저장되며, 보고 웹 서비스를 호출하여 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-110">These reports are stored in a database on the server, and can be retrieved by calling the reporting web service.</span></span> <span data-ttu-id="c5905-111">각 보고서에는 적용된 구성, 성공 여부, 사용된 리소스, 발생한 모든 오류, 시작 및 완료 시간 등의 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-111">Each report contains information such as what configurations were applied and whether they succeeded, the resources used, any errors that were thrown, and start and finish times.</span></span>

## <a name="configuring-a-node-to-send-reports"></a><span data-ttu-id="c5905-112">보고서를 보내도록 노드 구성</span><span class="sxs-lookup"><span data-stu-id="c5905-112">Configuring a node to send reports</span></span>

<span data-ttu-id="c5905-113">노드의 LCM 구성에서 **ReportServerWeb** 블록을 사용하여 서버에 보고서를 보내도록 노드에게 지시하세요(LCM 구성에 대해서는 [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="c5905-113">You tell a node to send reports to a server by using a **ReportServerWeb** block in the node's LCM configuration (for information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)).</span></span> <span data-ttu-id="c5905-114">노드가 보내는 보고서를 받는 서버는 웹 끌어오기 서버로 설정되어 있어야 합니다(SMB 공유에는 보고서를 보낼 수 없음).</span><span class="sxs-lookup"><span data-stu-id="c5905-114">The server to which the node sends reports must be set up as a web pull server (you cannot send reports to an SMB share).</span></span> <span data-ttu-id="c5905-115">끌어오기 서버 설정에 대한 내용은 [DSC 웹 끌어오기 서버 설정](pullServer.md)을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-115">For information about setting up a pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span> <span data-ttu-id="c5905-116">보고서 서버는 노드가 구성을 끌어오고 리소스를 가져오는 서비스와 동일한 서비스일 수도 있고 다른 서비스일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-116">The report server can be the same service from which the node pulls configurations and gets resources, or it can be a different service.</span></span>

<span data-ttu-id="c5905-117">**ReportServerWeb** 블록에서는 끌어오기 서비스의 URL과 서버에 알려진 등록 키를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-117">In the **ReportServerWeb** block, you specify the URL of the pull service and a registration key that is known to the server.</span></span>

<span data-ttu-id="c5905-118">다음 구성은 한 서비스에서 구성을 끌어오고 다른 서버의 서비스에 보고서를 보내도록 노드를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-118">The following configuration configures a node to pull configurations from one service, and send reports to a service on a different server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCPullServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}

ReportClientConfig
```

<span data-ttu-id="c5905-119">다음 구성에서는 구성, 리소스 및 보고에 단일 서버를 사용하도록 노드를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-119">The following configuration configures a node to use a single server for configurations, resources, and reporting.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }



        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfig
```

> [!NOTE]
> <span data-ttu-id="c5905-120">끌어오기 서버를 설정할 때 웹 서비스 이름을 원하는 대로 지정할 수 있지만 **ServerURL** 속성은 서비스 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-120">You can name the web service whatever you want when you set up a pull server, but the **ServerURL** property must match the service name.</span></span>

## <a name="getting-report-data"></a><span data-ttu-id="c5905-121">보고서 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="c5905-121">Getting report data</span></span>

<span data-ttu-id="c5905-122">끌어오기 서버에 전송된 보고서는 서버의 데이터베이스에 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-122">Reports sent to the pull server are entered into a database on the server.</span></span> <span data-ttu-id="c5905-123">보고서는 웹 서비스 호출을 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-123">The reports are available through calls to the web service.</span></span> <span data-ttu-id="c5905-124">특정 노드에서 보고서를 검색하려면 보고서 웹 서비스에 다음 형식으로 HTTP 요청을 보냅니다. `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span><span class="sxs-lookup"><span data-stu-id="c5905-124">To retrieve reports for a specific node, send an HTTP request to the report web service in the following form: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span></span>
<span data-ttu-id="c5905-125">여기서 `MyNodeAgentId`는 보고서를 가져올 노드의 에이전트 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-125">where `MyNodeAgentId` is the AgentId of the node for which you want to get reports.</span></span> <span data-ttu-id="c5905-126">해당 노드에서 [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)를 호출하여 노드에 대한 에이전트 ID를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-126">You can get the AgentID for a node by calling [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) on that node.</span></span>

<span data-ttu-id="c5905-127">보고서는 JSON 개체의 배열로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-127">The reports are returned as an array of JSON objects.</span></span>

<span data-ttu-id="c5905-128">다음 스크립트는 스크립트가 실행되는 노드에 대한 보고서를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-128">The following script returns the reports for the node on which it is run:</span></span>

```powershell
function GetReport
{
    param
    (
        $AgentId = "$((glcm).AgentId)", 
        $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCPullServer.svc"
    )

    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```

## <a name="viewing-report-data"></a><span data-ttu-id="c5905-129">보고서 데이터 보기</span><span class="sxs-lookup"><span data-stu-id="c5905-129">Viewing report data</span></span>

<span data-ttu-id="c5905-130">변수를 **GetReport** 함수의 결과로 설정하는 경우, 반환되는 배열의 요소에서 개별 필드를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-130">If you set a variable to the result of the **GetReport** function, you can view the individual fields in an element of the array that is returned:</span></span>

```powershell
$reports = GetReport
$reports[1]
```

```output
JobId                : 019dfbe5-f99f-11e5-80c6-001dd8b8065c
OperationType        : Consistency
RefreshMode          : Pull
Status               : Success
ReportFormatVersion  : 2.0
ConfigurationVersion : 2.0.0
StartTime            : 04/03/2016 06:21:43
EndTime              : 04/03/2016 06:22:04
RebootRequested      : False
Errors               : {}
StatusData           : {{"StartDate":"2016-04-03T06:21:43.7220000-07:00","IPV6Addresses":["2001:4898:d8:f2f2:852b:b255:b071:283b","fe80::852b:b255:b071
                       :283b%12","::2000:0:0:0","::1","::2000:0:0:0"],"DurationInSeconds":"21","JobID":"{019DFBE5-F99F-11E5-80C6-001DD8B8065C}","Curren
                       tChecksum":"A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F","MetaData":"Author: configAuthor; Name:
                       Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost: CONTOSO-PullSrv;","RebootRequested":"False
                       ","Status":"Success","IPV4Addresses":["10.240.179.151","127.0.0.1"],"LCMVersion":"2.0","ResourcesNotInDesiredState":[{"SourceInf
                       o":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall","ModuleName":"xNetworking","DurationInSeconds":"8.785",
                       "InstanceName":"Firewall","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"xFirewall","ModuleVersion":"2.7.0.0","
                       RebootRequested":"False","ResourceId":"[xFirewall]Firewall","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"False
                       "}],"NumberOfResources":"2","Type":"Consistency","HostName":"CONTOSO-PULLCLI","ResourcesInDesiredState":[{"SourceInfo":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive","ModuleName":"PSDesiredStateConfiguration","DurationInSeconds":"1.848",
                       "InstanceName":"ArchiveExample","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"Archive","ModuleVersion":"1.1","
                       RebootRequested":"False","ResourceId":"[Archive]ArchiveExample","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"T
                       rue"}],"MACAddresses":["00-1D-D8-B8-06-5C","00-00-00-00-00-00-00-E0"],"MetaConfiguration":{"AgentId":"52DA826D-00DE-4166-8ACB-73F2B46A7E00",
                       "ConfigurationDownloadManagers":[{"SourceInfo":"C:\\ReportTest\\LCMConfig.ps1::14::9::ConfigurationRepositoryWeb","A
                       llowUnsecureConnection":"True","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","RegistrationKey":"","ResourceId":"[Config
                       urationRepositoryWeb]CONTOSO-PullSrv","ConfigurationNames":["ClientConfig"]}],"ActionAfterReboot":"ContinueConfiguration","LCMCo
                       mpatibleVersions":["1.0","2.0"],"LCMState":"Idle","ResourceModuleManagers":[],"ReportManagers":[{"AllowUnsecureConnection":"True
                       ","RegistrationKey":"","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","ResourceId":"[ReportServerWeb]CONTOSO-PullSrv","S
                       ourceInfo":"C:\\ReportTest\\LCMConfig.ps1::24::9::ReportServerWeb"}],"StatusRetentionTimeInDays":"10","LCMVersion":"2.0","Config
                       urationMode":"ApplyAndMonitor","RefreshFrequencyMins":"30","RebootNodeIfNeeded":"True","RefreshMode":"Pull","DebugMode":["NONE"]
                       ,"LCMStateDetail":"","AllowModuleOverwrite":"False","ConfigurationModeFrequencyMins":"15"},"Locale":"en-US","Mode":"Pull"}}
AdditionalData       : {}
```

<span data-ttu-id="c5905-131">기본적으로 보고서는 **JobID**를 기준으로 정렬되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-131">By default, the reports are sorted by **JobID**.</span></span> <span data-ttu-id="c5905-132">가장 최근 보고서를 보려면 **StartTime** 속성을 기준으로 보고서를 내림차순으로 정렬한 다음 배열의 첫 번째 요소를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-132">To get the most recent report, you can sort the reports by descending **StartTime** property, and then get the first element of the array:</span></span>

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

<span data-ttu-id="c5905-133">**StatusData** 속성은 다양한 속성이 있는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-133">Notice that the **StatusData** property is an object with a number of properties.</span></span> <span data-ttu-id="c5905-134">대부분의 보고 데이터가 이 속성에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-134">This is where much of the reporting data is.</span></span> <span data-ttu-id="c5905-135">최근 보고서에 대한 **StatusData** 속성의 개별 필드를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-135">Let's look at the individual fields of the **StatusData** property for the most recent report:</span></span>

```powershell
$statusData = $reportMostRecent.StatusData | ConvertFrom-Json
$statusData
```

```output
StartDate                  : 2016-04-04T11:21:41.2990000-07:00
IPV6Addresses              : {2001:4898:d8:f2f2:852b:b255:b071:283b, fe80::852b:b255:b071:283b%12, ::2000:0:0:0, ::1...}
DurationInSeconds          : 25
JobID                      : {135D230E-FA92-11E5-80C6-001DD8B8065C}
CurrentChecksum            : A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F
MetaData                   : Author: configAuthor; Name: Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost:
                             CONTOSO-PullSrv;
RebootRequested            : False
Status                     : Success
IPV4Addresses              : {10.240.179.151, 127.0.0.1}
LCMVersion                 : 2.0
ResourcesNotInDesiredState : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall; ModuleName=xNetworking;
                             DurationInSeconds=10.725; InstanceName=Firewall; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=xFirewall;
                             ModuleVersion=2.7.0.0; RebootRequested=False; ResourceId=[xFirewall]Firewall; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=False}}
NumberOfResources          : 2
Type                       : Consistency
HostName                   : CONTOSO-PULLCLI
ResourcesInDesiredState    : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive; ModuleName=PSDesiredStateConfiguration;
                             DurationInSeconds=2.672; InstanceName=ArchiveExample; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=Archive;
                             ModuleVersion=1.1; RebootRequested=False; ResourceId=[Archive]ArchiveExample; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=True}}
MACAddresses               : {00-1D-D8-B8-06-5C, 00-00-00-00-00-00-00-E0}
MetaConfiguration          : @{AgentId=52DA826D-00DE-4166-8ACB-73F2B46A7E00; ConfigurationDownloadManagers=System.Object[];
                             ActionAfterReboot=ContinueConfiguration; LCMCompatibleVersions=System.Object[]; LCMState=Idle;
                             ResourceModuleManagers=System.Object[]; ReportManagers=System.Object[]; StatusRetentionTimeInDays=10; LCMVersion=2.0;
                             ConfigurationMode=ApplyAndMonitor; RefreshFrequencyMins=30; RebootNodeIfNeeded=True; RefreshMode=Pull;
                             DebugMode=System.Object[]; LCMStateDetail=; AllowModuleOverwrite=False; ConfigurationModeFrequencyMins=15}
Locale                     : en-US
Mode                       : Pull
```

<span data-ttu-id="c5905-136">무엇보다도, 이 속성은 가장 최근 구성에서 두 개의 리소스를 호출했으며, 그중에서 하나는 원하는 상태였고 다른 하나는 원하는 상태가 아니었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-136">Among other things, this shows that the most recent configuration called two resources, and that one of them was in the desired state, and one of them was not.</span></span> <span data-ttu-id="c5905-137">**ResourcesNotInDesiredState** 속성만 포함된 보다 읽기 쉬운 출력을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-137">You can get a more readable output of just the **ResourcesNotInDesiredState** property:</span></span>

```powershell
$statusData.ResourcesInDesiredState
```

```output
SourceInfo        : C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive
ModuleName        : PSDesiredStateConfiguration
DurationInSeconds : 2.672
InstanceName      : ArchiveExample
StartDate         : 2016-04-04T11:21:55.7200000-07:00
ResourceName      : Archive
ModuleVersion     : 1.1
RebootRequested   : False
ResourceId        : [Archive]ArchiveExample
ConfigurationName : Sample_ArchiveFirewall
InDesiredState    : True
```

<span data-ttu-id="c5905-138">이러한 예제는 보고서 데이터로 수행할 수 있는 작업에 대해 알 수 있도록 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c5905-138">Note that these examples are meant to give you an idea of what you can do with report data.</span></span> <span data-ttu-id="c5905-139">PowerShell에서의 JSON 사용에 대한 소개 내용을 알려면 [Playing with JSON and PowerShell(JSON 및 PowerShell 사용)](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c5905-139">For an introduction on working with JSON in PowerShell, see [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span></span>

## <a name="see-also"></a><span data-ttu-id="c5905-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c5905-140">See Also</span></span>

[<span data-ttu-id="c5905-141">로컬 구성 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="c5905-141">Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="c5905-142">DSC 웹 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="c5905-142">Setting up a DSC web pull server</span></span>](pullServer.md)

[<span data-ttu-id="c5905-143">구성 이름을 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="c5905-143">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)

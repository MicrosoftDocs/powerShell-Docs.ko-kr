---
ms.date: 10/30/2018
keywords: dsc,powershell,configuration,setup
title: DSC 문제 해결
ms.openlocfilehash: 5cbe6496a6e0b9940f4b69e13d1e19e43b3915f0
ms.sourcegitcommit: 5f199cd2a1b31dbcebaab44f2fe496f289831a30
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77478788"
---
# <a name="troubleshooting-dsc"></a>DSC 문제 해결

_적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0_

이 항목에서는 문제가 발생할 때 DSC 문제를 해결하는 방법을 설명합니다.

## <a name="winrm-dependency"></a>WinRM 종속성

Windows PowerShell DSC(원하는 상태 구성)는 WinRM에 종속됩니다. WinRM은 Windows Server 2008 R2 및 Windows 7에서 기본적으로 사용하도록 설정되지 않습니다. Windows PowerShell 관리자 권한 세션에서 `Set-WSManQuickConfig`를 실행하여 WinRM을 사용하도록 설정합니다.

## <a name="using-get-dscconfigurationstatus"></a>Get-DscConfigurationStatus 사용

[Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet은 대상 노드에서 구성 상태에 대한 정보를 가져옵니다. 구성 실행의 성공 여부에 대한 상위 수준 정보를 포함하는 다양한 개체가 반환됩니다. 개체를 자세히 검토하면 다음과 같은 구성 실행에 대한 정보를 검색할 수 있습니다.

- 실패한 모든 리소스
- 다시 부팅을 요청한 모든 리소스
- 구성 실행 시 메타 구성 설정
- 기타

다음 매개 변수 집합은 마지막 구성 실행에 대한 상태 정보를 반환합니다.

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
다음 매개 변수 집합은 모든 이전 구성 실행에 대한 상태 정보를 반환합니다.

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a>예제

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ResourceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>스크립트가 실행되지 않음: DSC 로그를 사용하여 스크립트 오류 진단

모든 Windows 소프트웨어와 마찬가지로, DSC에서는 [이벤트 뷰어](https://support.microsoft.com/hub/4338813/windows-help)에서 볼 수 있는 [로그](/windows/desktop/EventLog/about-event-logging)에 오류와 이벤트를 기록합니다.
이러한 로그를 검사하면 특정 작업이 실패한 이유와 나중에 오류를 방지하는 방법을 이해하는 데 도움이 될 수 있습니다. 구성 스크립트 작성은 까다로울 수 있으므로, 작성자로서 오류 추적을 보다 쉽게 하려면, DSC 로그 리소스를 사용하여 분석 DSC 이벤트 로그에 있는 구성의 진행률을 추적합니다.

## <a name="where-are-dsc-event-logs"></a>DSC 이벤트 로그는 어디에 있나요?

이벤트 뷰어에서 DSC 이벤트는 다음에 위치합니다. **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**

해당 PowerShell cmdlet인 [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)를 실행해도 이벤트 로그를 볼 수도 있습니다.

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

위와 같이 DSC의 기본 로그 이름은 **Microsoft->Windows->DSC**(Windows 아래의 다른 로그 이름은 간결하게 하기 위해 표시하지 않음)입니다. 기본 이름을 채널 이름에 추가하여 전체 로그 이름이 만들어집니다. DSC 엔진은 주로 다음과 같은 세 가지 형식의 로그로 작성합니다. [운영, 분석 및 디버그 로그](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)) 분석 및 디버그 로그는 기본적으로 해제 되어 있으므로, 이벤트 뷰어에서 설정해야 합니다. 이렇게 하려면 Windows PowerShell에서 Show-EventLog를 입력하여 이벤트 뷰어를 엽니다. 또는 **시작** 단추, **제어판**, **관리 도구**, **이벤트 뷰어**를 차례로 클릭합니다.
이벤트 뷰어의 **보기** 메뉴에서 **분석 및 디버그 로그 표시**를 클릭합니다. 분석 채널에 대한 로그 이름은 **Microsoft-Windows-Dsc/Analytic**이고, 디버그 채널은 **Microsoft-Windows-Dsc/Debug**입니다. 다음 예에서 보듯이, [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) 유틸리티를 사용하여 로그를 사용할 수도 있습니다.

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>DSC 로그에 들어 있는 내용은 무엇인가요?

DSC 로그는 메시지의 중요도에 따라 3개의 로그 채널로 분할됩니다. DSC의 작업 로그는 모든 오류 메시지를 포함하며, 문제를 파악하는 데 사용될 수 있습니다. 분석 로그는 더 많은 양의 이벤트를 포함하며, 오류가 발생한 위치를 식별할 수 있습니다. 이 채널은 자세한 정보 메시지도 포함합니다(있는 경우). 디버그 로그는 오류가 발생하는 방식을 이해하는 데 도움이 될 수 있는 로그를 포함합니다. DSC 이벤트 메시지는 모든 이벤트 메시지가 고유하게 DSC 작업을 나타내는 작업 ID로 시작되도록 구조화되어 있습니다. 아래 예제는 작업 DSC 로그에 로그되는 첫 번째 이벤트에서 메시지 가져오기를 시도합니다.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

DSC 이벤트는 사용자가 하나의 DSC 작업에서 이벤트를 집계할 수 있도록 해주는 특정 구조로 로그됩니다. 구조는 다음과 같습니다.

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a>단일 DSC 작업에서 이벤트 수집

DSC 이벤트 로그에는 다양한 DSC 작업에서 생성된 이벤트가 포함됩니다. 그러나 우리는 일반적으로 하나의 특정 작업에 대한 세부 정보에 관심이 있습니다. 모든 DSC 로그는 각 DSC 작업에 대해 고유한 작업 ID 속성으로 그룹화할 수 있습니다. 작업 ID는 모든 DSC 이벤트에서 첫 번째 속성 값으로 표시됩니다. 다음 단계에서는 그룹화된 배열 구조에서 모든 이벤트를 누적하는 방법을 설명합니다.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

여기, 변수 `$SeparateDscOperations`는 작업 ID로 그룹화된 로그를 포함합니다. 이 변수의 각 배열 요소는 로그에 대한 추가 정보에 액세스할 수 있도록 다른 DSC 작업을 통해 로그되는 이벤트 그룹을 나타냅니다.

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....

PS C:\> $SeparateDscOperations[0].Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

[Where-Object](/powershell/module/microsoft.powershell.core/where-object)를 사용하여 `$SeparateDscOperations` 변수에서 데이터를 추출할 수 있습니다. 다음은 DSC 문제 해결을 위해 데이터를 추출해야 하는 다섯 개의 시나리오입니다.

### <a name="1-operations-failures"></a>1: 작업 오류

모든 이벤트에는 [심각도](/windows/desktop/WES/defining-severity-levels)가 있습니다. 오류 이벤트를 식별하는 데 이 정보를 사용할 수 있습니다.

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2: 마지막 30분 동안 실행된 작업의 세부 정보

모든 Windows 이벤트의 속성인 `TimeCreated`는 이벤트가 만들어진 시간을 기술합니다. 이 속성을 특정 날짜/시간 개체와 비교하여 모든 이벤트를 필터링할 수 있습니다.

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a>3: 최신 작업의 메시지

최신 작업은 배열 그룹 `$SeparateDscOperations`의 첫 번째 인덱스에 저장됩니다.
인덱스 0에 대한 그룹의 메시지를 쿼리하면 최신 작업에 대한 모든 메시지가 반환됩니다.

```powershell
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4: 최근 실패한 작업에 대해 로그된 오류 메시지

`$SeparateDscOperations[0].Group`에는 최신 작업에 대한 이벤트 집합이 포함되어 있습니다. 수준 표시 이름에 따라 이벤트를 필터링하려면 `Where-Object` cmdlet을 실행하세요. 결과는 이벤트 메시지를 가져오기 위해 추가적으로 분석할 수 있는 `$myFailedEvent` 변수에 저장됩니다.

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5: 특정 작업 ID에 대해 생성된 모든 이벤트

`$SeparateDscOperations`는 고유한 작업 ID로서 각각 이름이 있는 그룹의 배열입니다. `Where-Object` cmdlet을 실행하면 특정 작업 ID를 가지고 있는 이벤트들의 그룹을 추출할 수 있습니다.

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>xDscDiagnostics를 사용하여 DSC 로그 분석

**xDscDiagnostics**는 컴퓨터에서 DSC 실패를 분석하는 데 도움이 되는 여러 함수로 구성된 PowerShell 모듈입니다. 이 함수들은 지난 DSC 작업의 모든 로컬 이벤트나 원격 컴퓨터의 DSC 이벤트(유효한 자격 증명 사용)를 식별하는 데 유용할 수 있습니다. 여기에서 DSC 작업이라는 용어는 시작부터 끝까지 하나의 고유한 DSC 실행을 정의하는 데 사용됩니다. 예를 들어 `Test-DscConfiguration`은 별도의 DSC 작업입니다. 마찬가지로, DSC에 있는 모든 다른 cmdlet(예: `Get-DscConfiguration`, `Start-DscConfiguration` 등)은 각각 별도의 DSC 작업으로 식별될 수 있습니다. 함수에 대한 설명은 [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics)에 나와 있습니다. `Get-Help <cmdlet name>`을 실행하여 도움말을 사용할 수 있습니다.

### <a name="getting-details-of-dsc-operations"></a>DSC 작업의 세부 정보 가져오기

`Get-xDscOperation` 함수는 하나 또는 여러 컴퓨터에서 실행되는 DSC 작업의 결과를 찾을 수 있도록 해주며, 각 DSC 작업에서 생성된 이벤트의 컬렉션을 포함하는 개체를 반환합니다. 예를 들어 다음의 출력에서는 세 가지 명령이 실행되었습니다. 첫 번째 명령은 통과했고, 다른 두 개는 실패했습니다. 이 결과는 `Get-xDscOperation`의 출력에 요약되어 있습니다.

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

또한 `Newest` 매개 변수를 사용하여 최신 작업에 대한 결과만 필요하다고 지정할 수 있습니다.

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a>DSC 이벤트의 세부 정보 가져오기

`Trace-xDscOperation` cmdlet은 이벤트의 컬렉션, 해당 이벤트 형식 및 특정 DSC 작업으로 생성된 메시지 출력을 포함하는 개체를 반환합니다. 일반적으로 `Get-xDscOperation`을 사용하는 작업 중에 오류가 발생하면, 오류를 초래한 이벤트를 찾기 위해 해당 작업을 추적하게 됩니다.

`SequenceID` 매개 변수를 사용하여 특정 컴퓨터의 특정 작업에 대한 이벤트를 가져옵니다.
예를 들어 `SequenceID`를 9로 지정하는 경우 `Trace-xDscOperaion`은 마지막 작업에서 9번째인 DSC 작업에 대한 추적을 가져옵니다.

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

`Get-xDscOperation` cmldet에서 반환하는 특정 DSC 작업에 할당된 **GUID**를 전달하여 해당 DSC 작업에 대한 이벤트 세부 정보를 가져옵니다.

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

`Trace-xDscOperation`에서는 분석, 디버그 및 작업 로그에서 이벤트를 집계하므로, 위에서 설명한 대로 이러한 로그를 사용하도록 설정하라는 메시지가 표시됩니다.

또는, `Trace-xDscOperation`의 출력을 변수에 저장하여 이벤트에 대한 정보를 수집할 수 있습니다. 다음 명령을 사용하여 특정 DSC 작업에 대한 모든 이벤트를 표시할 수 있습니다.

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

이렇게 하면 아래 출력과 같이 `Get-WinEvent` cmdlet과 동일한 결과가 표시됩니다.

```output
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

먼저 `Get-xDscOperation`을 사용하여 컴퓨터에서의 마지막 몇 개 DSC 구성 실행을 나열하는 것이 좋습니다. 그런 다음에 `Trace-xDscOperation`으로 단일 작업(해당 SequenceID 또는 JobID 사용)을 검사하여 백그라운드에서 수행한 작업을 검색할 수 있습니다.

### <a name="getting-events-for-a-remote-computer"></a>원격 컴퓨터에 대한 이벤트 가져오기

`Trace-xDscOperation` cmdlet의 `ComputerName` 매개 변수를 사용하여 원격 컴퓨터의 이벤트 세부 정보를 가져옵니다. 이렇게 하려면 먼저 원격 컴퓨터에서 원격 관리를 허용하도록 방화벽 규칙을 만들어야 합니다.

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

이제 호출에서 해당 컴퓨터를 `Trace-xDscOperation`으로 지정할 수 있습니다.

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>리소스가 업데이트되지 않음: 캐시를 다시 설정하는 방법

DSC 엔진은 효율성 향상을 위해 PowerShell 모듈로서 구현하는 리소스를 캐시합니다.
그러나 이렇게 하면 프로세스가 다시 시작되기 전까지 DSC가 캐시된 버전을 로드하게 되므로 리소스를 작성하고 동시에 테스트하는 경우 문제가 발생할 수 있습니다. DSC가 최신 버전을 로드하도록 하는 유일한 방법은 DSC 엔진을 호스팅하는 프로세스를 명시적으로 종료하는 것입니다.

마찬가지로, `Start-DscConfiguration`을 실행하는 경우, 사용자 지정 리소스를 추가하고 수정하면 컴퓨터를 다시 부팅하지 않으면, 또는 다시 부팅하기 전까지는 수정이 실행되지 않을 수 있습니다. 이것은 DSC가 WMI 공급자 호스트 프로세스(WmiPrvSE)에서 실행되고, 일반적으로 한 번에 실행되는 WmiPrvSE 인스턴스가 많기 때문입니다. 컴퓨터를 다시 부팅하면 호스트 프로세스가 다시 시작되고 캐시가 지워집니다.

다시 부팅하지 않고도 구성을 성공적으로 재활용하고, 캐시를 지우려면, 호스트 프로세스를 중지했다가 다시 시작해야 합니다. 이 작업은 인스턴스별로 수행할 수 있으며, 그에 따라 프로세스를 식별, 중지 및 다시 시작할 수 있습니다. 또는 아래 설명된 대로 `DebugMode`를 사용하여 PowerShell DSC 리소스를 다시 로드할 수 있습니다.

인스턴스별로 DSC 엔진을 호스트하고 중지하는 프로세스를 식별하기 위해 DSC 엔진을 호스팅하는 WmiPrvSE의 프로세스 ID를 나열할 수 있습니다. 그런 다음 공급자를 업데이트하려면, 아래 명령을 사용하여 WmiPrvSE 프로세스를 중지한 다음, **Start-DscConfiguration**을 다시 실행합니다.

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a>DebugMode 사용

호스트 프로세스를 다시 시작할 때 항상 캐시가 지워지도록 하기 위해 `DebugMode`를 사용하도록 DSC LCM(로컬 구성 관리자)를 구성할 수 있습니다. **TRUE**로 설정하면, 엔진이 항상 PowerShell DSC 리소스를 다시 로드합니다. 리소스를 작성을 완료하면, 다시 **FALSE**로 설정할 수 있으며, 엔진은 모듈을 캐싱하는 동작으로 되돌아갑니다.

다음은 `DebugMode`가 캐시를 자동으로 새로 고칠 수 있는 방법을 보여 주는 데모입니다. 우선, 기본 구성을 살펴보겠습니다.

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

`DebugMode`가 **"없음"** 으로 설정된 것을 확인할 수 있습니다.

`DebugMode` 데모를 설정하려면 다음 PowerShell 리소스를 사용합니다.

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

이제, `TestProviderDebugMode`라는 위의 리소스를 사용하여 구성을 작성합니다.

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

파일 내용: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt`가 **1**임을 알 수 있습니다.

이제, 다음 스크립트를 사용하여 공급자 코드를 업데이트합니다.

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

이 스크립트는 난수를 생성하고 그에 따라 공급자 코드를 업데이트합니다. `DebugMode`가 false로 설정되면 파일 내용 “ **$env:SystemDrive\OutputFromTestProviderDebugMode.txt**”가 변경되지 않습니다.

이제, 구성 스크립트에서 `DebugMode`를 **"ForceModuleImport"** 로 설정합니다.

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

다시 위의 스크립트를 실행하면 파일의 내용이 매번 다른 것을 보게 됩니다. (`Get-DscConfiguration`를 실행하여 확인할 수 있습니다.) 다음은 두 번의 추가 실행에 대한 결과입니다(결과는 스크립트를 실행하는 경우 다를 수 있음).

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="dsc-returns-unexpected-response-code-internalservererror-when-registering-with-windows-pull-server"></a>Windows Pull Server에 등록할 때 DSC에서 "예기치 않은 응답 코드 InternalServerError" 반환

서버에 메타 구성을 적용하여 Windows Pull Server 인스턴스에 등록할 때 다음과 같은 오류가 발생할 수 있습니다.

```PowerShell
Registration of the Dsc Agent with the server https://<serverfqdn>:8080/PSDSCPullServer.svc failed. The underlying error is: The attempt to register Dsc Agent with AgentId <ID> with the server 
https://<serverfqdn>:8080/PSDSCPullServer.svc/Nodes(AgentId='<ID>') returned unexpected response code InternalServerError. .
    + CategoryInfo          : InvalidResult: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : RegisterDscAgentUnsuccessful,Microsoft.PowerShell.DesiredStateConfiguration.Commands.RegisterDscAgentCommand
    + PSComputerName        : <computername>
```

이는 서버에서 트래픽을 암호화하는 데 사용되는 인증서에 노드에서 URL을 확인하기 위해 사용하는 DNS 이름과 다른 CN(일반 이름)이 있을 때 발생할 수 있습니다.
수정된 이름의 인증서를 사용하도록 Windows Pull Server 인스턴스를 업데이트합니다.

## <a name="error-when-running-sysprep-after-applying-a-dsc-configuration"></a>DSC 구성을 적용한 후 Sysprep을 실행하는 동안 오류 발생

DSC 구성을 적용한 후 Sysprep을 실행하여 Windows Server를 범용화하려고 할 때 다음과 같은 오류가 발생할 수 있습니다.

```
SYSPRP LaunchDll:Failure occurred while executing 'DscCore.dll,SysPrep_Cleanup', returned error code 0x2
```

Windows PowerShell Desired State Configuration을 사용하여 서버를 구성한 후 범용화하는 것은 지원되지 않는 시나리오입니다.  대신 Windows 설치 프로그램의 특수화 단계를 완료한 후에 Windows에 구성을 적용합니다.

## <a name="see-also"></a>참고 항목

### <a name="concepts"></a>개념

- [사용자 지정 Windows PowerShell 필요한 상태 구성 리소스 빌드](../resources/authoringResource.md)

### <a name="other-resources"></a>관련 자료

- [Windows PowerShell Desired State Configuration Cmdlets(Windows PowerShell DSC(필요한 상태 구성) Cmdlet)](/powershell/module/psdesiredstateconfiguration/)

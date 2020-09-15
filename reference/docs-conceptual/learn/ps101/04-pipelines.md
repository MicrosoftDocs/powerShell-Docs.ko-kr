---
title: 원라이너 및 파이프라인
description: PowerShell 원라이너는 단일 작업을 수행하기 위해 여러 명령을 포함하는 하나의 연속 파이프라인입니다.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: b8fd45e5e5dc408754ebac015757ef4241428978
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633348"
---
# <a name="chapter-4---one-liners-and-the-pipeline"></a>4장 - 원라이너 및 파이프라인

PowerShell을 처음 배우기 시작했을 때 필자는 PowerShell 원라이너를 사용하여 작업을 수행할 수 없으면 GUI로 돌아갔습니다. 시간이 지나면서 스크립트, 함수, 모듈을 작성하는 기술이 늘었습니다. 인터넷에서 볼 수 있는 몇몇 고급 예제에 너무 압도당하지 마세요. 타고난 PowerShell 전문가는 아무도 없습니다. 우리 모두는 초보자였습니다.

관리를 위해 아직 GUI를 사용하는 사람들에게 한 마디 조언을 드리자면, 관리자 워크스테이션에 관리 도구를 설치하고 서버를 원격으로 관리하세요. 이러한 방식으로 서버에서 운영 체제의 GUI 또는 Server Core 설치를 실행하는 경우 문제가 되지 않습니다.
이는 PowerShell을 사용하여 서버를 원격으로 관리하는 것을 준비하는 데 도움이 될 것입니다.

이전 장과 마찬가지로 Windows 10 랩 환경 컴퓨터에서 내용을 따라해야 합니다.

## <a name="one-liners"></a>원라이너

PowerShell 원라이너는 하나의 연속 파이프라인이며 반드시 한 줄로 작성된 명령이 아닙니다. 한 줄로 작성된 명령이 모두 원라이너는 아닙니다.

다음 명령은 여러 줄로 작성되었지만 하나의 연속 파이프라인이므로 PowerShell 원라이너입니다. 한 줄로 작성할 수는 있었지만 파이프 기호에서 줄 바꿈을 선택한 것입니다. 파이프 기호는 PowerShell에서 자연 줄 바꿈이 허용되는 문자 중 하나입니다.

```powershell
Get-Service |
  Where-Object CanPauseAndContinue -eq $true |
    Select-Object -Property *
```

```Output
Name                : LanmanWorkstation
RequiredServices    : {NSI, MRxSmb20, Bowser}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Workstation
DependentServices   : {SessionEnv, Netlogon, Browser}
MachineName         : .
ServiceName         : LanmanWorkstation
ServicesDependedOn  : {NSI, MRxSmb20, Bowser}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : Netlogon
RequiredServices    : {LanmanWorkstation}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Netlogon
DependentServices   : {}
MachineName         : .
ServiceName         : Netlogon
ServicesDependedOn  : {LanmanWorkstation}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : vmicheartbeat
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Heartbeat Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicheartbeat
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmickvpexchange
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Data Exchange Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmickvpexchange
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicrdv
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Remote Desktop Virtualization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicrdv
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicshutdown
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Guest Shutdown Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicshutdown
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmictimesync
RequiredServices    : {VmGid}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Time Synchronization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmictimesync
ServicesDependedOn  : {VmGid}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicvss
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Volume Shadow Copy Requestor
DependentServices   : {}
MachineName         : .
ServiceName         : vmicvss
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : Winmgmt
RequiredServices    : {RPCSS}
CanPauseAndContinue : True
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Management Instrumentation
DependentServices   : {wscsvc, NcaSvc, iphlpsvc}
MachineName         : .
ServiceName         : Winmgmt
ServicesDependedOn  : {RPCSS}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :
```

줄 바꿈은 쉼표(`,`)와 여는 대괄호(`[`), 중괄호(`{`) 및 괄호(`(`)를 비롯하여 일반적으로 사용되는 문자에서 발생할 수 있습니다. 그다지 일반적이지 않은 다른 문자로는 세미콜론(`;`), 등호(`=`), 여는 작은따옴표 및 큰따옴표(`'`,`"`)가 포함됩니다.

줄 연속 문자로 역따옴표(`` ` ``) 또는 억음 악센트 문자를 사용하는 것은 논란이 있는 주제입니다. 가능한 한 이 문제를 회피할 것을 권장합니다. 자연 줄 바꿈 문자 바로 뒤에 역따옴표를 사용하여 작성된 PowerShell 명령이 종종 보입니다.
그럴 이유는 없습니다.

```powershell
Get-Service -Name w32time |
>> Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

이전의 두 예제에 표시된 명령은 PowerShell 콘솔에서 문제 없이 작동합니다. 그러나 PowerShell ISE의 콘솔 창에서 실행하려고 하면 오류가 발생합니다. Powershell ISE의 콘솔 창은 PowerShell 콘솔처럼 다음 줄에 명령의 나머지 부분을 입력할 때까지 기다리지 않습니다. PowerShell ISE의 콘솔 창에서 이 문제를 방지하려면 다른 줄에 명령을 계속 입력할 때 <kbd>Enter</kbd> 키만 누르는 대신 <kbd>Shift</kbd>+<kbd>Enter</kbd> 키를 사용하세요.

다음 예제는 하나의 연속 파이프라인이 아니기 때문에 원라이너가 아닙니다. 한 줄에서 세미콜론으로 구분된 별도의 두 명령입니다.

```powershell
$Service = 'w32time'; Get-Service -Name $Service
```

```powershell
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

많은 프로그래밍 및 스크립팅 언어에는 각 줄의 끝에 세미콜론이 필요합니다. PowerShell에서도 이러한 방식을 사용할 수 있지만 세미콜론은 필요하지 않으므로 사용하지 않는 것이 좋습니다.

## <a name="filtering-left"></a>왼쪽으로 필터링

이 장에 표시된 명령의 결과는 하위 집합으로 필터링되었습니다. 예를 들어 `Get-Service`는 Windows 시간 서비스로만 반환된 서비스 목록을 필터링하기 위해 **Name** 매개 변수와 함께 사용되었습니다.

파이프라인에서 여러분은 항상 가능한 한 빨리 원하는 결과를 필터링하기를 원할 것입니다. 이를 위해서는 첫 번째 명령, 즉 맨 왼쪽에 있는 명령에 매개 변수를 사용합니다.
이를 왼쪽으로 필터링이라고도 합니다.

다음 예제에서는 `Get-Service`의 **Name** 매개 변수를 사용하여 Windows 시간 서비스에 대한 결과만 즉시 필터링합니다.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

필터링을 수행하기 위해 명령을 `Where-Object`로 파이프하는 예는 드물지 않습니다.

```powershell
Get-Service | Where-Object Name -eq w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Windows Time
```

첫 번째 예제에서는 소스에서 필터링하여 Windows 시간 서비스에 대한 결과만 반환합니다.
두 번째 예제에서는 모든 서비스를 반환한 다음 필터링을 수행하는 다른 명령으로 파이프합니다. 이 예제에서는 큰 문제가 아닐 수 있지만, Active Directory 사용자 목록을 쿼리한다고 가정해보세요. 정말로 Active Directory에서 수천 개의 사용자 계정에 대한 정보를 작은 하위 집합으로 필터링하는 다른 명령으로만 파이프하고 싶으신가요? 중요하지 않은 경우에도 항상 왼쪽으로 필터링하는 것이 좋습니다. 정말 중요한 경우에는 자동으로 왼쪽으로 필터링하는 데 익숙해질 것입니다.

명령을 지정하는 순서가 중요하지 않다고 누군가가 말하는 것을 들은 적이 있습니다. 이는 전혀 사실이 아닙니다. 명령이 지정되는 순서는 필터링을 수행할 때 중요합니다. 예를 들어 `Select-Object`를 사용하여 몇 가지 속성만 선택하고 `Where-Object`를 사용하여 선택 항목에 없는 속성을 필터링하는 시나리오를 살펴보겠습니다. 이 시나리오에서는 필터링이 먼저 발생해야 합니다. 그렇지 않으면 필터링을 수행하려고 할 때 파이프라인에 속성이 존재하지 않습니다.

```powershell
Get-Service |
Select-Object -Property DisplayName, Running, Status |
Where-Object CanPauseAndContinue
```

`Select-Object`의 결과가 `Where-Object`로 파이프될 때 **CanStopAndContinue** 속성이 존재하지 않기 때문에 이전 예제의 명령은 결과를 반환하지 않습니다. 이 속성은 "선택"되지 않았습니다. 요컨대 필터링된 것입니다. `Select-Object`와 `Where-Object`의 순서를 반대로 바꾸면 원하는 결과가 생성됩니다.

```powershell
Get-Service |
Where-Object CanPauseAndContinue |
Select-Object -Property DisplayName, Status
```

```Output
DisplayName                                    Status
-----------                                    ------
Workstation                                    Running
Netlogon                                       Running
Hyper-V Heartbeat Service                      Running
Hyper-V Data Exchange Service                  Running
Hyper-V Remote Desktop Virtualization Service  Running
Hyper-V Guest Shutdown Service                 Running
Hyper-V Time Synchronization Service           Running
Hyper-V Volume Shadow Copy Requestor           Running
Windows Management Instrumentation             Running
```

## <a name="the-pipeline"></a>파이프라인

이 책에서 지금까지 보여 드린 많은 예제에서 확인할 수 있듯이, 한 명령의 출력을 다른 명령에 대한 입력으로 사용할 수 있는 경우가 많습니다. 3장에서 `Get-Member`는 명령이 생성하는 개체 형식을 결정하는 데 사용되었습니다. 또한 3장에는 `Get-Command`의 **ParameterType** 매개 변수를 사용하여 반드시 파이프라인 입력이 아니더라도 해당 입력 형식을 허용하는 명령을 결정하는 예제도 있었습니다.

명령 도움말이 얼마나 자세한지에 따라 **INPUTS** 및 **OUTPUTS** 섹션이 포함될 수 있습니다.

```powershell
help Stop-Service -Full
```

```Output
...
INPUTS
    System.ServiceProcess.ServiceController, System.String
        You can pipe a service object or a string that contains the name of a service
        to this cmdlet.

OUTPUTS
    None, System.ServiceProcess.ServiceController
        This cmdlet generates a System.ServiceProcess.ServiceController object that
        represents the service, if you use the PassThru parameter. Otherwise, this
        cmdlet does not generate any output.
...
```

위의 결과에는 도움말의 관련 섹션만 표시됩니다. 여기에서 볼 수 있듯이 **INPUTS** 섹션은 **ServiceController** 또는 **문자열** 개체가 `Stop-Service` cmdlet으로 파이프될 수 있음을 보여 줍니다. 해당 입력 형식을 허용하는 매개 변수는 보여 주지 않습니다. 이 정보를 확인하는 가장 쉬운 방법 중 하나는 `Stop-Service` cmdlet에 대한 도움말의 전체 버전에서 다양한 매개 변수를 살펴보는 것입니다.

```powershell
help Stop-Service -Full
```

```powershell
...
-DisplayName <String[]>
    Specifies the display names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false

-InputObject <ServiceController[]>
    Specifies ServiceController objects that represent the services to stop. Enter a
    variable that contains the objects, or type a command or expression that gets the
    objects.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByValue)
    Accept wildcard characters?  false

-Name <String[]>
    Specifies the service names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  false
...
```

다시 한 번, 이전 결과 집합에는 도움말의 관련 부분만 표시했습니다. **DisplayName** 매개 변수는 파이프라인 입력을 허용하지 않고, **InputObject** 매개 변수는 **ServiceController** 개체에 **값 기준**으로 파이프라인 입력을 허용하고, **Name** 매개 변수는 **문자열** 개체에 **값 기준**으로 파이프라인 입력을 허용합니다. 또한 **속성 이름 기준**으로도 파이프라인 입력을 허용합니다.

매개 변수가 속성 이름 기준 및 값 기준 모두에서 파이프라인 입력을 허용하는 경우 항상 **값 기준**을 먼저 시도합니다. **값 기준**이 실패하면 **속성 이름 기준**을 시도합니다. **값 기준**은 약간 오해의 소지가 있습니다. 필자는 **형식 기준**으로 부르는 것을 선호합니다. 즉 **ServiceController** 개체 형식을 생성하는 명령 결과를 `Stop-Service`로 파이프하면 이 명령은 해당 입력을 **InputObject** 매개 변수에 바인딩합니다. 그러나 **문자열** 출력을 생성하는 명령의 결과를 `Stop-Service`로 파이프하면 이 명령은 **Name** 매개 변수에 바인딩합니다. **ServiceController** 또는 **문자열** 개체를 생성하지 않지만 **Name**이라는 속성을 포함하는 출력을 생성하는 명령의 결과를 `Stop-Service`에 파이프하면 이 명령은 **Name** 속성을 `Stop-Service`의 **Name** 매개 변수에 바인딩합니다.

`Get-Service` 명령이 생성하는 출력 형식을 결정합니다.

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController
```

`Get-Service`는 ServiceController 개체 형식을 생성합니다.

도움말에서 앞서 살펴본 것처럼 `Stop-Service`의 **InputObject** 매개 변수는 파이프라인 **값 기준**(형식 기준)을 통해 **ServiceController** 개체를 허용합니다. 즉 `Get-Service` cmdlet의 결과가 `Stop-Service`로 파이프되면 `Stop-Service`의 **InputObject** 매개 변수에 바인딩됩니다.

```powershell
Get-Service -Name w32time | Stop-Service
```

이제 문자열 입력을 시도해보겠습니다. `w32time`을 `Get-Member`로 파이프하여 문자열인지만 확인합니다.

```powershell
'w32time' | Get-Member
```

```Output
   TypeName: System.String
```

앞서 설명한 것처럼 문자열을 `Stop-Service`로 파이프하면 **값 기준**으로 `Stop-Service`의 **Name** 매개 변수에 바인딩됩니다. `w32time`을 `Stop-Service`로 파이프하여 이를 테스트합니다.

```powershell
'w32time' | Stop-Service
```

이전 예제에서는 문자열 `w32time`을 작은따옴표로 묶었습니다. PowerShell에서는 따옴표로 묶인 문자열의 내용에 실제 값으로 확장해야 하는 변수가 포함되어 있지 않으면 항상 큰따옴표 대신 작은따옴표를 사용해야 합니다. 작은따옴표를 사용하면 PowerShell이 따옴표 안에 포함된 콘텐츠를 구문 분석할 필요가 없으므로 코드가 약간 더 빠르게 실행됩니다.

`Stop-Service`의 **Name** 매개 변수에 대한 속성 이름 기준 파이프라인 입력을 테스트하는 사용자 지정 개체를 만듭니다.

```powershell
$CustomObject = [pscustomobject]@{
 Name = 'w32time'
 }
```

**CustomObject** 변수의 내용은 **PSCustomObject** 개체 형식이며 **Name**이라는 속성을 포함합니다.

```powershell
$CustomObject | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty string Name=w32time
```

`$CustomObject` 변수를 따옴표로 묶는 경우 큰따옴표를 사용하는 것이 좋습니다.
그렇지 않고 작은따옴표를 사용하는 경우 변수에 포함된 값 대신 리터럴 문자열 `$CustomObject`가 `Get-Member`로 파이프됩니다.

`$CustomObject`의 내용을 `Stop-Service` cmdlet으로 파이프하면 **Name** 매개 변수에 바인딩되기는 하지만, 이번에는 **값 기준**이 아니라 **속성 이름 기준**으로 바인딩됩니다. `$CustomObject`의 내용이 **Name**이라는 속성을 가진 개체이기 때문입니다.

이 예제에서는 **Service**와 같은 다른 속성 이름을 사용하여 다른 사용자 지정 개체를 만듭니다.

```powershell
$CustomObject = [pscustomobject]@{
  Service = 'w32time'
}
```

`$CustomObject`를 `Stop-Service`로 파이프하려고 하면 오류가 생성됩니다. 이 명령은 **ServiceController** 또는 **문자열** 개체를 생성하지 않고 **Name**이라는 속성을 포함하지 않기 때문입니다.

```powershell
$CustomObject | Stop-Service
```

```Output
Stop-Service : Cannot find any service with service name '@{Service=w32time}'.
At line:1 char:17
+ $CustomObject | Stop-Service
+
    + CategoryInfo          : ObjectNotFound: (@{Service=w32time}:String) [Stop-Service]
   , ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.S
   topServiceCommand
```

한 명령의 출력이 다른 명령의 파이프라인 입력 옵션과 일치하지 않는 경우 속성이 올바로 일치하도록 `Select-Object`를 사용하여 속성의 이름을 변경할 수 있습니다.

```powershell
$CustomObject |
  Select-Object -Property @{name='Name';expression={$_.Service}} |
    Stop-Service
```

이 예제에서는 `Select-Object`를 사용하여 **Service** 속성의 이름을 **Name**이라는 속성으로 변경했습니다.

이 예제의 구문은 처음에 약간 복잡한 것처럼 보일 수 있습니다. 경험상 코드를 복사하여 붙여넣는 방법으로는 구문을 배울 수 없습니다. 시간을 들여 코드를 입력해야 합니다. 몇 번이면 자연스러워지게 됩니다. 한 화면에 예제 코드를 표시하고 다른 화면에서 코드를 입력할 수 있으므로 여러 모니터를 사용하면 매우 유용합니다.

파이프라인 입력을 허용하지 않는 매개 변수를 사용해야 하는 경우가 있습니다. 다음 예제에서는 한 명령의 출력을 다른 명령에 대한 입력으로 사용하는 방법을 보여 줍니다. 먼저 두 Windows 서비스의 표시 이름을 텍스트 파일에 저장합니다.

```powershell
'Background Intelligent Transfer Service', 'Windows Time' |
Out-File -FilePath $env:TEMP\services.txt
```

입력이 필요한 명령의 매개 변수에 대한 값으로 괄호 안에서 필요한 출력을 제공하는 명령을 실행할 수 있습니다.

```powershell
Stop-Service -DisplayName (Get-Content -Path $env:TEMP\services.txt)
```

이는 여러분이 기억하고 있는 대수학 연산 순서와 똑같습니다. 괄호 안의 명령은 항상 괄호 밖의 명령 부분보다 먼저 실행됩니다.

## <a name="powershellget"></a>PowerShellGet

PowerShellGet은 NuGet 리포지토리에서 PowerShell 모듈(및 기타 아티팩트)을 검색, 설치, 게시 및 업데이트하기 위한 명령을 포함하는 PowerShell 모듈입니다. PowerShellGet은 PowerShell 버전 5.0 이상에서 제공됩니다. PowerShell 버전 3.0 이상에서는 별도의 다운로드로 제공됩니다.

Microsoft에서는 [PowerShell 갤러리][]라는 온라인 NuGet 리포지토리를 호스트합니다. 이 리포지토리는 Microsoft에서 호스트하지만 리포지토리 내에 포함된 대부분의 모듈은 Microsoft에서 작성하지 않습니다. PowerShell 갤러리에서 가져오는 모든 코드는 프로덕션 환경에서 사용하기에 적합한 것으로 간주하기 전에 격리된 테스트 환경에서 철저히 검토해야 합니다.

대부분의 회사는 내부 전용 NuGet 리포지토리를 호스트하면서 내부 전용 모듈 그리고 다른 소스에서 다운로드한 후 악의적이지 않은 것으로 확인된 모듈만 게시해야 할 것입니다.

PowerShellGet 모듈의 일부인 `Find-Module` cmdlet을 사용하여 PowerShell 갤러리에서 필자가 작성한 MrToolkit라는 모듈을 찾습니다.

```powershell
Find-Module -Name MrToolkit
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with
NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or
'C:\Users\MrAdmin\AppData\Local\PackageManagement\ProviderAssemblies'. You can also
install the NuGet provider by running 'Install-PackageProvider -Name NuGet
-MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the
NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1        MrToolkit                           PSGallery            Misc PowerShell Tools
```

PowerShellGet 모듈의 명령 중 하나를 처음 사용할 때 NuGet 공급자를 설치할지 묻는 메시지가 표시됩니다.

MrToolkit 모듈을 설치하려면 이전 명령을 `Install-Module`로 파이프합니다.

```powershell
Find-Module -Name MrToolkit | Install-Module
```

```Output
Untrusted repository
You are installing the modules from an untrusted repository. If you trust this
repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet.
Are you sure you want to install the modules from
'https://www.powershellgallery.com/api/v2/'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): y
```

PowerShell 갤러리는 신뢰할 수 없는 리포지토리이므로 모듈 설치를 승인하라는 메시지가 표시됩니다.

## <a name="finding-pipeline-input-the-easy-way"></a>간편하게 파이프라인 찾기

MrToolkit 모듈은 `Get-MrPipelineInput`이라는 함수를 포함합니다. 이 cmdlet을 사용하여 파이프라인 입력을 허용하는 명령 매개 변수, 허용하는 개체 형식, 파이프라인 입력을 **값 기준** 또는 **속성 이름 기준**으로 허용할지 여부를 간편하게 결정할 수 있습니다.

```powershell
Get-MrPipelineInput -Name Stop-Service
```

```Output
ParameterName ParameterType                             ValueFromPipeline ValueFromPipelineByPropertyName
------------- -------------                             ----------------- ---------------
InputObject   System.ServiceProcess.ServiceController[]              True           False
Name          System.String[]                                        True            True
```

여기에서 볼 수 있듯이 앞서 도움말을 통해 확인했던 것과 동일한 정보를 이 함수를 사용하여 쉽게 얻을 수 있습니다.

## <a name="summary"></a>요약

이 장에서는 PowerShell 원라이너에 대해 알아보았습니다. PowerShell 명령이 원라이너인지 여부는 해당 명령이 작성된 실제 줄 수와 상관이 없다는 것을 배웠습니다. 또한 왼쪽으로 필터링, 파이프라인, PowerShellGet에 대해서도 알아보았습니다.

## <a name="review"></a>검토

1. PowerShell 원라이너란 무엇인가요?
1. PowerShell에서 자연 줄 바꿈이 발생할 수 있는 몇 가지 문자는 무엇인가요?
1. 왼쪽으로 필터링해야 하는 이유는 무엇인가요?
1. PowerShell 명령이 파이프라인 입력을 허용할 수 있는 두 가지 방법은 무엇인가요?
1. PowerShell 갤러리에 있는 명령을 신뢰하지 않는 이유는 무엇인가요?

## <a name="recommended-reading"></a>권장 참조 항목

- [about_Pipelines][]
- [about_Command_Syntax][]
- [about_Parameters][]
- [PowerShellGet: PowerShell 모듈을 검색, 설치, 업데이트하는 가장 쉬운 방법][psget]

<!-- link references-->
[about_Pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[about_Parameters]: /powershell/module/microsoft.powershell.core/about/about_parameters
[psget]: https://mikefrobbins.com/2015/04/23/powershellget-the-big-easy-way-to-discover-install-and-update-powershell-modules/
[PowerShell 갤러리]: https://www.powershellgallery.com/

---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: JEA에 대한 감사 및 보고
ms.openlocfilehash: 2388c735840d8d3683aa8bc9869b9fb0371e5902
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682823"
---
# <a name="auditing-and-reporting-on-jea"></a>JEA에 대한 감사 및 보고

> 적용 대상: Windows Powershell 5.0

JEA를 배포한 후에는 정기적으로 JEA 구성을 감사하려고 할 것입니다.
감사를 통해 올바른 사용자에게 JEA 엔드포인트에 대한 액세스 권한이 있는지와 할당된 해당 역할이 여전히 올바른지를 평가할 수 있습니다.

이 항목에서는 JEA 엔드포인트를 감사할 수 있는 다양한 방법을 설명합니다.

## <a name="find-registered-jea-sessions-on-a-machine"></a>컴퓨터에서 등록된 JEA 세션 찾기

컴퓨터에 등록된 JEA 세션을 확인하려면 [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet을 사용합니다.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

엔드포인트에 대한 유효 권한은 "Permission" 속성에 나열됩니다.
이러한 사용자는 JEA 엔드포인트에 연결할 수 있는 권한을 갖지만, 액세스할 수 있는 역할(및 확장에 의한 명령)은 엔드포인트를 등록하는 데 사용된 [세션 구성 파일](session-configurations.md)의 "RoleDefinitions" 필드에 의해 결정됩니다.

"RoleDefinitions" 속성의 데이터를 확장하여 등록된 JEA 엔드포인트의 역할 매핑을 평가할 수 있습니다.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>컴퓨터에서 사용 가능한 역할 기능 찾기

역할 기능 파일은 유효한 PowerShell 모듈 내의 "RoleCapabilities" 폴더에 저장된 경우에만 JEA에서 사용됩니다.
사용 가능한 모듈 목록을 검색하여 컴퓨터에서 사용할 수 있는 모든 역할 기능을 찾을 수 있습니다.

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> 여러 역할 기능에서 같은 이름을 공유하는 경우 이 함수의 결과 순서가 반드시 역할 기능이 선택된 순서인 것은 아닙니다.

## <a name="check-effective-rights-for-a-specific-user"></a>특정 사용자에 대한 유효 권한 확인

JEA 엔드포인트를 설정한 후에는 JEA 세션에서 특정 사용자가 사용할 수 있는 명령을 확인하고자 할 수 있습니다.
사용자가 현재 그룹 구성원으로 JEA 세션을 시작하도록 되어 있는 경우 [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability)를 사용하여 해당 사용자에게 적용되는 모든 명령을 열거할 수 있습니다.
`Get-PSSessionCapability`의 출력은 JEA 세션에서 `Get-Command -CommandType All`을 실행하는 지정된 사용자의 출력과 같습니다.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

사용자가 추가 JEA 권한을 부여하는 그룹의 영구 구성원이 아닌 경우 이 cmdlet은 이러한 추가 사용 권한을 반영하지 않을 수 있습니다.
이는 일반적으로 "Just-In-Time" 권한 있는 액세스 권한 관리 시스템을 사용하여 사용자가 일시적으로 보안 그룹에 속할 수 있도록 하는 경우입니다.
항상 역할에 대한 사용자 매핑과 각 역할의 내용을 신중하게 평가하여 사용자에게 작업을 수행하는 데 필요한 최소량의 명령에 대한 액세스 권한만 부여되도록 합니다.

## <a name="powershell-event-logs"></a>PowerShell 이벤트 로그

시스템에서 모듈 및/또는 스크립트 블록 로깅을 사용하도록 설정한 경우 Windows 이벤트 로그에서 사용자가 해당 JEA 세션에서 실행한 각 명령에 대한 이벤트를 찾을 수 있습니다.
이러한 이벤트를 찾으려면 Windows 이벤트 뷰어를 열고 **Microsoft-Windows-PowerShell/Operational** 이벤트 로그로 이동한 다음 이벤트 ID가 **4104**인 이벤트를 찾습니다.

각 이벤트 로그 항목에는 명령이 실행된 세션에 대한 정보가 포함됩니다.
JEA 세션의 경우 이러한 정보로는 JEA 세션을 만든 실제 사용자인 **ConnectedUser**와 명령을 실행하는 데 사용된 계정 JEA를 식별하는 **RunAsUser**에 대한 중요 정보가 있습니다.
애플리케이션 이벤트 로그에는 RunAsUser가 수행한 변경 내용이 표시되므로, 기록 또는 모듈/스크립트 로깅을 사용하도록 설정해야 사용자까지 거슬러 올라가 특정 명령 호출을 추적할 수 있습니다.

## <a name="application-event-logs"></a>애플리케이션 이벤트 로그

외부 애플리케이션 또는 서비스와 상호 작용하는 JEA 세션에서 명령을 실행하는 경우 해당 애플리케이션이 자체 이벤트 로그에 이벤트를 기록할 수 있습니다.
PowerShell 로그 및 기록과 달리, 다른 로깅 메커니즘은 JEA 세션의 연결된 사용자를 캡처하지 않으며 대신 가상 실행 사용자 또는 그룹 관리 서비스 계정만 기록합니다.
명령을 실행한 사용자를 확인하려면 [세션 기록](#session-transcripts)을 확인하거나 PowerShell 이벤트 로그를 애플리케이션 이벤트 로그에 표시된 시간 및 사용자와 상관 관계를 지정해야 합니다.

WinRM도 애플리케이션 이벤트 로그의 실행 사용자와 연결하는 사용자의 상관 관계를 지정하는 데 도움이 될 수 있습니다.
**Microsoft-Windows-Windows Remote Management/Operational** 로그의 이벤트 ID **193**은 JEA 세션이 만들어질 때마다 연결하는 사용자와 실행 사용자의 SID(보안 식별자) 및 계정 이름을 기록합니다.

## <a name="session-transcripts"></a>세션 기록

각 사용자 세션에 대한 기록을 만들도록 JEA를 구성한 경우 모든 사용자 작업의 텍스트 복사본이 지정된 폴더에 저장됩니다.

모든 기록 디렉터리를 찾으려면 JEA로 구성된 컴퓨터에서 관리자로 다음 명령을 실행합니다.

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

각 기록은 세션이 시작된 시간, 세션에 연결된 사용자 및 해당 사용자에게 할당된 JEA ID에 대한 정보로 시작합니다.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

기록의 본문에는 사용자가 호출한 각 명령에 대한 정보가 기록됩니다.
PowerShell 원격에 대해 명령이 변환된 방법으로 인해 사용자가 실행한 명령의 정확한 구문은 JEA 세션에서 사용할 수 없지만, 실행된 유효 명령을 여전히 확인할 수는 있습니다.
JEA 세션에서 `Get-Service Dns`를 실행한 사용자의 예제 기록 코드 조각은 다음과 같습니다.

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

사용자가 실행한 각 명령에 대해 사용자가 호출한 cmdlet 또는 함수를 설명하는 "CommandInvocation" 줄이 기록됩니다.
ParameterBinding은 각 CommandInvocation을 따라 명령과 함께 제공된 각 매개 변수 및 값에 대해 알려줍니다.
위의 예제에서 매개 변수 "Name"이 "Get-service" cmdlet에 대한 값 "Dns"를 제공했음을 알 수 있습니다.

또한 각 명령의 출력은 일반적으로 Out-Default로 CommandInvocation을 트리거합니다.
Out-Default의 InputObject는 명령에서 반환되는 PowerShell 개체입니다.
해당 개체의 세부 정보가 몇 줄 아래에 출력되어 사용자가 보게 되는 내용과 매우 비슷한 내용을 표시합니다.

## <a name="see-also"></a>참고 항목

- [보안에 관한 *PowerShell ♥ the Blue Team*(PowerShell ♥ Blue Team) 블로그 게시물](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

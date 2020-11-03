---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disconnect-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-PSSession
ms.openlocfilehash: 7694154c4724bef35aeb1ccdc46aee6a1875cf57
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218225"
---
# Disconnect-PSSession

## 개요
세션에서 연결을 끊습니다.

## SYNTAX

### 세션(기본값)

```
Disconnect-PSSession [-Session] <PSSession[]> [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### 속성

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Disconnect-PSSession`Cmdlet은 `New-PSSession` 현재 세션에서 cmdlet을 사용 하 여 시작한 것과 같은 PowerShell 세션 ("PSSession")의 연결을 끊습니다. 그 결과로 PSSession은 연결이 끊긴 상태입니다. 현재 세션 또는 로컬 컴퓨터의 다른 세션이나 다른 컴퓨터에서 연결이 끊긴 PSSession에 연결할 수 있습니다.

`Disconnect-PSSession`Cmdlet은 현재 세션에 연결 된 오픈 pssession만 연결을 끊습니다. `Disconnect-PSSession` cmdlet을 사용 하 여 시작 된 끊어진 PSSessions 또는 대화형 pssession의 연결을 끊을 수 없으며 `Enter-PSSession` , 다른 세션에 연결 된 pssession의 연결을 끊을 수 없습니다.

연결이 끊어진 PSSession에 다시 연결 하려면 `Connect-PSSession` 또는 cmdlet을 사용 `Receive-PSSession` 합니다.

PSSession이 시간 초과되었거나 출력 버퍼가 가득 차서 PSSession의 명령이 차단된 경우가 아니면 PSSession의 연결이 끊겨도 PSSession의 명령은 완료될 때까지 계속 실행됩니다. 유휴 시간 제한을 변경하려면 **IdleTimeoutSec** 매개 변수를 사용합니다. 출력 버퍼링 모드를 변경 하려면 **OutputBufferingMode** 매개 변수를 사용 합니다. 또한 Cmdlet의 **InDisconnectedSession** 매개 변수를 사용 하 여 연결 되지 않은 `Invoke-Command` 세션에서 명령을 실행할 수 있습니다.

연결이 끊긴 세션 기능에 대한 자세한 내용은 [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)를 참조하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예 1-이름별로 세션 연결 끊기

이 명령은 현재 세션에서 Server01 컴퓨터에 있는 UpdateSession PSSession의 연결을 끊습니다. 이 명령은 **Name** 매개 변수를 사용 하 여 PSSession을 식별 합니다.

```
PS> Disconnect-PSSession -Name UpdateSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  UpdateSession   Server01        Disconnected  Microsoft.PowerShell          None
```

출력은 연결 끊기 시도가 성공했음을 보여 줍니다. 세션 상태가 Disconnected이고 Availability가 None이므로 세션이 사용되고 있지 않으며 다시 연결할 수 있음을 나타냅니다.

### 예 2-특정 컴퓨터에서 세션 연결 끊기

이 명령은 현재 세션에서 Server12 컴퓨터에 있는 ITTask PSSession의 연결을 끊습니다.
ITTask 세션은 현재 세션에서 만들어졌으며 Server12 컴퓨터에 연결합니다. 이 명령은 cmdlet을 사용 하 여 세션을 가져오고 cmdlet을 사용 하 여 `Get-PSSession` `Disconnect-PSSession` 연결을 끊습니다.

```
PS> Get-PSSession -ComputerName Server12 -Name ITTask |
  Disconnect-PSSession -OutputBufferingMode Drop -IdleTimeoutSec 86400
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  ITTask          Server12        Disconnected  ITTasks               None
```

이 `Disconnect-PSSession` 명령은 **OutputBufferingMode** 매개 변수를 사용 하 여 출력 모드를 **Drop** 으로 설정 합니다. 이 설정은 세션 출력 버퍼가 가득 차도 세션에서 실행 중인 스크립트를 계속 실행할 수 있게 합니다. 스크립트가 파일 공유의 보고서에 출력을 쓰기 때문에 다른 출력이 영향 없이 손실될 수 있습니다.

또한 이 명령은 **IdleTimeoutSec** 매개 변수를 사용하여 세션의 시간 제한을 24시간으로 연장합니다. 이 설정은 이 관리자나 다른 관리자가 세션에 다시 연결하여 스크립트가 실행되었는지 확인하고 필요한 경우 문제를 해결할 수 있는 시간을 허용합니다.

### 예 3-여러 컴퓨터에서 여러 PSSessions 사용

이 일련의 명령은 `Disconnect-PSSession` 엔터프라이즈 시나리오에서 cmdlet을 사용 하는 방법을 보여 줍니다. 이 경우 새 기술자가 원격 컴퓨터의 세션에서 스크립트를 시작한 후 문제가 발생합니다. 보다 경험이 많은 관리자가 세션에 연결하여 문제를 해결할 수 있도록 기술자가 세션에서 연결을 끊습니다.

```
PS> $s = New-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
PS> Invoke-Command $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Get-PSSession -Name ITTask -ComputerName Srv1 | Disconnect-PSSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1 ITTask           Srv1            Disconnected  Microsoft.PowerShell          None

PS> Get-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None
 2 ITTask          Srv2            Opened        Microsoft.PowerShell     Available
 3 ITTask          Srv30           Opened        Microsoft.PowerShell     Available

PS> Get-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None

PS> $s = Connect-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
PS> Invoke-Command -Session $s {dir $home\Scripts\PatchStatusOutput.ps1}
PS> Invoke-Command -Session $s {mkdir $home\Scripts\PatchStatusOutput}
PS> Invoke-Command -Session $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Disconnect-PSSession -Session $s
```

기술자는 먼저 여러 원격 컴퓨터에서 세션을 만들고 각 세션에서 스크립트를 실행합니다. 첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` 세 개의 원격 컴퓨터에서 ITTask 세션을 만듭니다. 이 명령은 세션을 $s 변수에 저장합니다. 두 번째 명령은 cmdlet의 **FilePath** 매개 변수를 사용 하 여 `Invoke-Command` $s 변수의 세션에서 스크립트를 실행 합니다.

Srv1 컴퓨터에서 실행되는 스크립트가 예기치 않은 오류를 생성합니다. 기술자가 관리자에게 지원을 요청합니다. 관리자가 검토할 수 있도록 기술 자가 세션에서 연결을 끊도록 지시 합니다. 두 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` Srv1 컴퓨터의 ITTask 세션을 가져온 다음 cmdlet을 사용 하 여 `Disconnect-PSSession` 연결을 끊습니다. 이 명령은 다른 컴퓨터의 ITTask 세션에 영향을 주지 않습니다.

세 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` ITTask 세션을 가져옵니다. 출력은 Srv2 및 Srv30 컴퓨터의 ITTask 세션이 연결 끊기 명령의 영향을 받지 않았음을 보여 줍니다.

관리자는 자신의 가정용 컴퓨터에 로그온 하 고, 회사 네트워크에 연결 하 고, Windows PowerShell을 시작 하 고, cmdlet을 사용 하 여 `Get-PSSession` Srv1 컴퓨터의 ITTask 세션을 가져옵니다. 기술자 자격 증명을 사용하여 세션에 액세스한

그런 다음, 관리자는 cmdlet을 사용 하 여 `Connect-PSSession` Srv1 컴퓨터의 ITTask 세션에 연결 합니다. 이 명령은 세션을 $s 변수에 저장합니다.

관리자는 cmdlet을 사용 하 여 `Invoke-Command` 변수의 세션에서 일부 진단 명령을 실행 합니다 `$s` . 스크립트가 필요한 디렉터리를 찾지 못해 실패했음을 발견합니다.
관리자는 함수를 사용 하 여 `MkDir` 디렉터리를 만든 다음 스크립트를 다시 시작 하 `Get-PatchStatus.ps1` 고 세션에서 연결을 끊습니다. 관리자는 해당 결과를 기술 지원 담당자에 게 보고 하 고, 세션에 다시 연결 하 여 작업을 완료 하 고, `Get-PatchStatus.ps1` 필요한 디렉터리가 없는 경우 해당 디렉터리를 만드는 스크립트에 명령을 추가 하 라는 메시지를 표시 합니다.

### 예 4-PSSession에 대 한 제한 시간 값 변경

이 예제에서는 세션 연결을 끊을 수 있도록 세션의 **IdleTimeout** 속성 값을 수정하는 방법을 보여 줍니다.

세션의 유휴 시간 제한 속성은 연결이 끊긴 세션이 삭제되기 전에 유지되는 기간을 결정하므로 연결이 끊긴 세션에 중요합니다. 세션을 만들 때 및 세션 연결을 끊을 때 유휴 시간 제한 옵션을 설정할 수 있습니다. 세션의 유휴 시간 제한에 대 한 기본값은 `$PSSessionOption` 로컬 컴퓨터의 기본 설정 변수 및 원격 컴퓨터의 세션 구성에 설정 됩니다. 세션에 대해 설정된 값이 세션 구성에서 설정된 값보다 우선하지만 세션 값은 세션 구성에서 설정된 할당량(예: **MaxIdleTimeoutMs** 값)을 초과할 수 없습니다.

```
PS> $Timeout = New-PSSessionOption -IdleTimeout 172800000
PS> $s = New-PSSession -Computer Server01 -Name ITTask -SessionOption $Timeout
PS> Disconnect-PSSession -Session $s
Disconnect-PSSession : The session ITTask cannot be disconnected because the specified
idle timeout value 172800(seconds) is either greater than the server maximum allowed
43200 (seconds) or less that the minimum allowed60(seconds).  Choose an idle time out
value that is within the allowed range and try again.

PS> Invoke-Command -ComputerName Server01 {Get-PSSessionConfiguration Microsoft.PowerShell} |
 Format-List -Property *

Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/microsoft.powershell
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
SecurityDescriptorSddl        : O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GXGW;;;WD)
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 2147483647
Uri                           : http://schemas.microsoft.com/powershell/microsoft.powershell
SDKVersion                    : 2
Name                          : microsoft.powershell
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
ParentResourceUri             : http://schemas.microsoft.com/powershell/microsoft.powershell
Enabled                       : true
MaxShells                     : 25
MaxShellsPerUser              : 25
Permission                    : BUILTIN\Administrators AccessAllowed
PSComputerName                : localhost
RunspaceId                    : aea84310-6dbf-4c21-90ac-13980039925a
PSShowComputerName            : True


PS> $s.Runspace.ConnectionInfo
ConnectionUri                     : http://Server01/wsman
ComputerName                      : Server01
Scheme                            : http
Port                              : 80
AppName                           : /wsman
Credential                        :
ShellUri                          : http://schemas.microsoft.com/powershell/Microsoft.PowerShell
AuthenticationMechanism           : Default
CertificateThumbprint             :
MaximumConnectionRedirectionCount : 5
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
UseCompression                    : True
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
NoEncryption                      : False
UseUTF16                          : False
OutputBufferingMode               : Drop
IncludePortInSPN                  : False
Culture                           : en-US
UICulture                         : en-US
OpenTimeout                       : 180000
CancelTimeout                     : 60000
OperationTimeout                  : 180000
IdleTimeout                       : 172800000

PS> Disconnect-PSSession $s -IdleTimeoutSec 43200
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Disconnected  Microsoft.PowerShell          None

PS> $s.Runspace.ConnectionInfo.IdleTimeout
43200000
```

첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSessionOption` 세션 옵션 개체를 만듭니다. **IdleTimeout** 매개 변수를 사용하여 유휴 시간 제한을 48시간(172800000밀리초)으로 설정합니다. 또한 세션 옵션 개체를 $Timeout 변수에 저장합니다.

두 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` Server01 컴퓨터에서 ITTask 세션을 만듭니다. 이 명령은 세션을 $s 변수에 저장합니다. **SessionOption** 매개 변수 값은 $Timeout 변수에 있는 48시간 유휴 시간 제한입니다.

세 번째 명령은 $s 변수에 있는 ITTask 세션의 연결을 끊습니다. 세션의 유휴 시간 제한 값이 세션 구성의 **MaxIdleTimeoutMs** 할당량을 초과하기 때문에 명령이 실패합니다. 세션 연결이 끊길 때까지 유휴 시간 제한이 사용되지 않았으므로 세션이 사용 중인 동안에는 이 위반이 검색되지 않을 수 있습니다.

네 번째 명령은 cmdlet을 사용 `Invoke-Command` 하 여 `Get-PSSessionConfiguration` Server01 컴퓨터의 Microsoft PowerShell 세션 구성에 대 한 명령을 실행 합니다. 이 명령은 cmdlet을 사용 `Format-List` 하 여 세션 구성의 모든 속성을 목록으로 표시 합니다. 출력은 세션 구성을 사용 하는 세션에 대해 허용 되는 최대 **IdleTimeout** 값을 설정 하는 **MaxIdleTimeoutMS** 속성이 4320만 밀리초 (12 시간) 임을 보여 줍니다.

다섯 번째 명령은 $s 변수에 있는 세션의 세션 옵션 값을 가져옵니다. 여러 세션 옵션의 값은 세션의 **Runspace** 속성에 대 한 **ConnectionInfo** 속성의 속성입니다. 출력은 세션의 **IdleTimeout** 속성 값이 1억7280만 밀리초 (48 시간) 임을 보여 주며,이는 세션 구성에서 12 시간의 **MaxIdleTimeoutMs** 할당량을 위반 합니다. 이 충돌을 해결 하려면 **ConfigurationName** 매개 변수를 사용 하 여 다른 세션 구성을 선택 하거나 **IdleTimeout** 매개 변수를 사용 하 여 세션의 유휴 시간 제한을 줄일 수 있습니다.

여섯 번째 명령은 세션 연결을 끊습니다. **IdleTimeoutSec** 매개 변수를 사용하여 유휴 시간 제한을 최대값 12시간으로 설정합니다.

일곱 번째 명령은 연결이 끊긴 세션의 **IdleTimeout** 속성 값을 가져옵니다. 이 값은 밀리초 단위로 측정됩니다. 출력은 명령이 성공했음을 확인합니다.

## PARAMETERS

### -Id

지정한 세션 ID를 가진 세션에서 연결을 끊습니다. 하나 이상의 ID를 쉼표로 구분하여 입력하거나 범위 연산자(..)를 사용하여 ID 범위를 지정하세요.

세션의 ID를 가져오려면 cmdlet을 사용 합니다 `Get-PSSession` . 인스턴스 ID는 세션의 **ID** 속성에 저장됩니다.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IdleTimeoutSec

연결이 끊긴 PSSession의 유휴 시간 제한 값을 변경합니다. 값을 초 단위로 입력하세요. 최소값은 60 (1 분)입니다.

유휴 시간 제한은 원격 컴퓨터에서 연결이 끊긴 PSSession을 유지 관리하는 기간을 결정합니다. 시간 제한이 만료되면 PSSession이 삭제됩니다.

연결이 끊긴 PSSession은 연결이 끊긴 세션에서 명령을 실행 중인 경우에도 연결이 끊긴 순간부터 유휴 상태로 간주됩니다.

세션의 유휴 시간 제한에 대한 기본값은 세션 구성의 **IdleTimeoutMs** 속성 값에 의해 설정됩니다. 기본값은 7200000밀리초(2시간)입니다.

이 매개 변수 값은 $PSSessionOption 기본 설정 변수의 **IdleTimeout** 속성 값 및 세션 구성의 기본 유휴 시간 제한 값보다 우선합니다. 그러나 세션 구성의 **MaxIdleTimeoutMs** 속성 값을 초과할 수는 없습니다. **MaxIdleTimeoutMs** 의 기본값은 12시간(43200000밀리초)입니다.

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

### -InstanceId

지정한 인스턴스 ID를 가진 세션에서 연결을 끊습니다.

인스턴스 ID는 로컬 또는 원격 컴퓨터의 세션을 고유하게 식별하는 GUID입니다. 인스턴스 ID는 여러 컴퓨터의 세션 간에도 고유합니다.

세션의 인스턴스 ID를 가져오려면 cmdlet을 사용 합니다 `Get-PSSession` . 인스턴스 ID는 세션의 **InstanceID** 속성에 저장 됩니다.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

지정한 이름을 가진 세션에서 연결을 끊습니다. 와일드카드가 지원됩니다.

세션의 이름을 가져오려면 cmdlet을 사용 합니다 `Get-PSSession` . 이름은 세션의 **Name** 속성에 저장됩니다.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Session

지정한 PSSession에서 연결을 끊습니다. Cmdlet에서 반환 하는 것과 같은 PSSession 개체를 입력 `New-PSSession` 합니다. PSSession 개체를로 파이프 할 수도 있습니다 `Disconnect-PSSession` .

`Get-PSSession`Cmdlet은 연결이 끊어진 pssession 및 다른 컴퓨터의 다른 세션에 연결 된 pssession을 포함 하 여 원격 컴퓨터에서 종료 되는 모든 pssession을 가져올 수 있습니다. `Disconnect-PSSession` 현재 세션에 연결 된 PSSession만 연결을 끊습니다. 다른 pssession을에 파이프 하면 `Disconnect-PSSession` `Disconnect-PSSession` 명령이 실패 합니다.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ThrottleLimit

명령에 대 한 제한 제한을 설정 합니다 `Disconnect-PSSession` .

제한 한도는 이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수입니다. 이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다.

제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputBufferingMode

출력 버퍼가 가득 찰 경우 연결이 끊긴 세션에서 명령 출력을 관리하는 방법을 결정합니다. 기본값은 **Block** 입니다.

연결된 세션의 명령이 출력을 반환하여 출력 버퍼가 가득 찰 경우 이 매개 변수 값에 의해 세션 연결이 끊긴 동안 명령을 계속 실행할지 여부를 결정합니다. 값이 **Block** 이면 세션을 다시 연결할 때까지 명령이 일시 중단됩니다. 값이 **Drop** 이면 데이터가 손실될 수는 있지만 명령을 완료할 수 있습니다. **Drop** 값을 사용할 경우 명령 출력을 디스크의 파일로 리디렉션합니다.

유효한 값은 다음과 같습니다.

- **차단** : 출력 버퍼가 가득 차면 버퍼가 명확 해질 때까지 실행이 일시 중단 됩니다.
- **Drop** : 출력 버퍼가 가득 차면 실행이 계속 됩니다. 새 출력이 저장되면 가장 오래된 출력을 버립니다.
- **없음** : 출력 버퍼링 모드를 지정 하지 않았습니다. 세션 구성의 **OutputBufferingMode** 속성 값을 연결이 끊긴 세션에 사용합니다.

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Block
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

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

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](./About/about_CommonParameters.md)를 참조하세요.

## 입력

### Runspace입니다.

세션을로 파이프 할 수 있습니다 `Disconnect-PSSession` .

## 출력

### Runspace입니다.

`Disconnect-PSSession` 연결을 끊은 세션을 나타내는 개체를 반환 합니다.

## 참고

- `Disconnect-PSSession`이 cmdlet은 로컬 및 원격 컴퓨터에서 PowerShell 3.0 이상을 실행 하는 경우에만 작동 합니다.
- 연결 되지 않은 세션에서 cmdlet을 사용 하는 경우이 `Disconnect-PSSession` 명령은 세션에 영향을 주지 않으며 오류를 생성 하지 않습니다.
- 대화형 보안 토큰이 있는 연결이 끊긴 루프백 세션( **EnableNetworkAccess** 매개 변수로 만든 세션)은 세션을 만든 컴퓨터에서만 다시 연결할 수 있습니다. 이 제한은 악의적인 액세스로부터 컴퓨터를 보호합니다.
- PSSession의 연결을 끊을 경우 세션 상태는 **Disconnected** 이고 가용성은 **None** 입니다.

  **State** 속성 값은 현재 세션을 기준으로 합니다. 따라서 값 **Disconnected** 는 PSSession이 현재 세션에 연결되어 있지 않음을 의미합니다. 그렇다고 PSSession의 연결이 모든 세션에서 끊어졌다는 것을 의미하지는 않습니다. 다른 세션에 연결되어 있을 수도 있습니다. 세션에 연결하거나 다시 연결할 수 있는지 확인하려면 **Availability** 속성을 사용합니다.

  **Availability** 값이 **None** 이면 세션에 연결할 수 있습니다. 값이 **Busy** 이면 PSSession이 다른 세션에 연결되어 있어서 연결할 수 없습니다.

  세션의 **State** 속성 값에 대 한 자세한 내용은 [RunspaceState 열거형](/dotnet/api/system.management.automation.runspaces.runspacestate)을 참조 하세요.

  세션의 **Availability** 속성 값에 대 한 자세한 내용은 [RunspaceAvailability 열거형](/dotnet/api/system.management.automation.runspaces.runspaceavailability)을 참조 하세요.

## 관련 링크

[Connect-PSSession](Connect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Receive-PSSession](Receive-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Remove-PSSession](Remove-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)

[about_Remote_Disconnected_Sessions](About/about_Remote_Disconnected_Sessions.md)

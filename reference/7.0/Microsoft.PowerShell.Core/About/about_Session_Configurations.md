---
description: 컴퓨터에 원격으로 연결할 수 있는 사용자와 실행할 수 있는 명령을 결정하는 세션 구성에 대해 설명합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 5b59d8fb05ee118f5b2d7b5b859efad9be75814a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220594"
---
# <a name="about-session-configurations"></a>세션 구성 정보

## <a name="short-description"></a>간단한 설명
컴퓨터에 원격으로 연결할 수 있는 사용자와 실행할 수 있는 명령을 결정하는 세션 구성에 대해 설명합니다.

## <a name="long-description"></a>자세한 설명

"끝점"이 라고도 하는 세션 구성은 원격 사용자 또는 로컬 사용자가 로컬 컴퓨터의 PowerShell에 연결할 때 생성 되는 PowerShell 세션의 환경을 정의 하는 로컬 컴퓨터의 설정 그룹입니다.

컴퓨터 관리자는 세션 구성을 사용 하 여 컴퓨터를 보호 하 고 컴퓨터에 연결 하는 사용자에 대 한 사용자 지정 환경을 정의할 수 있습니다.

또한 관리자는 세션 구성을 사용 하 여 컴퓨터에 원격으로 연결 하는 데 필요한 권한을 결정할 수 있습니다. 기본적으로 Administrators 그룹의 구성원만 세션 구성을 사용 하 여 원격으로 연결 하는 권한을 가지 지만, 모든 사용자 또는 선택한 사용자가 컴퓨터에 원격으로 연결할 수 있도록 기본 설정을 변경할 수 있습니다.

PowerShell 3.0부터 세션 구성 파일을 사용 하 여 세션 구성의 요소를 정의할 수 있습니다. 이 기능을 사용 하면 코드를 작성 하지 않고 세션을 쉽게 사용자 지정 하 고 세션 구성의 속성을 검색할 수 있습니다. 세션 구성 파일을 만들려면 New-PSSessionConfiguration cmdlet을 사용 합니다. 세션 구성 파일에 대한 자세한 내용은 [about_Session_Configuration_Files](about_Session_Configuration_Files.md)를 참조하세요.

세션 구성은 WS-MANAGEMENT (Web Services for Management) 기반 PowerShell 원격 기능입니다. 이는 새 PSSession, 호출 명령 또는 Enter-PSSession cmdlet을 사용 하 여 원격 컴퓨터에 연결 하는 경우에만 사용 됩니다.

참고: 세션 구성을 관리 하려면 "관리자 권한으로 실행" 옵션을 사용 하 여 PowerShell을 시작 합니다.

세션 구성 정보

모든 PowerShell 세션은 세션 구성을 사용 합니다. 여기에는 New-PSSession 또는 Enter-PSSession cmdlet을 사용 하 여 만드는 영구 세션과 PowerShell에서 사용 하는 임시 세션 (예: Invoke 명령과 같은 WS-MANAGEMENT 기반 원격 기술을 사용 하는 cmdlet의 ComputerName 매개 변수를 사용 하는 경우)이 포함 됩니다.

관리자는 세션 구성을 사용 하 여 컴퓨터의 리소스를 보호 하 고 컴퓨터에 연결 하는 사용자에 대 한 사용자 지정 환경을 만들 수 있습니다. 예를 들어 세션 구성을 사용 하 여 컴퓨터에서 세션에 수신 하는 개체의 크기를 제한 하 고, 세션의 언어 모드를 정의 하 고, 세션에서 사용할 수 있는 cmdlet, 공급자 및 함수를 지정할 수 있습니다.

세션 구성의 보안 설명자를 구성 하 여 세션 구성을 사용 하 여 컴퓨터에 연결할 수 있는 사용자를 결정할 수 있습니다.
세션에서 사용 하려면 사용자에 게 세션 구성에 대 한 Execute 권한이 있어야 합니다. 사용자에 게 컴퓨터의 세션 구성을 사용 하는 데 필요한 권한이 없는 경우에는 사용자가 원격으로 컴퓨터에 연결할 수 없습니다.

기본적으로 컴퓨터의 관리자 에게만 기본 세션 구성을 사용할 수 있는 권한이 있습니다. 그러나 보안 설명자를 변경 하 여 모든 사용자가 없거나 선택한 사용자만 컴퓨터에서 세션 구성을 사용할 수 있도록 할 수 있습니다.

기본 제공 세션 구성

PowerShell 3.0에는 Microsoft. PowerShell 및 Microsoft. Workflow 라는 기본 제공 세션 구성이 포함 되어 있습니다. 64 비트 버전의 Windows를 실행 하는 컴퓨터에서 PowerShell은 Microsoft.powershell32 (32 비트 세션 구성)도 제공 합니다.

Microsoft. PowerShell 세션 구성은 기본적으로 세션에 사용 됩니다. 즉, 세션을 만드는 명령에 새 PSSession, Enter-PSSession 또는 Invoke-Command cmdlet의 ConfigurationName 매개 변수가 포함 되지 않습니다.

기본 세션 구성에 대 한 보안 설명자를 사용 하 여 로컬 컴퓨터의 Administrators 그룹 구성원만이를 사용할 수 있습니다. 따라서 기본 설정을 변경 하지 않는 한 관리자 그룹의 구성원만 원격으로 컴퓨터에 연결할 수 있습니다.

$PSSessionConfigurationName 기본 설정 변수를 사용 하 여 기본 세션 구성을 변경할 수 있습니다. 자세한 내용은 about_preference_variables를 참조하세요.

로컬 컴퓨터에서 세션 구성 보기

로컬 컴퓨터의 세션 구성을 가져오려면 Get-PSSessionConfiguration cmdlet을 사용 합니다.

예를 들어 다음과 같이 입력합니다.

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

세션 구성 파일을 사용 하 여 구성 된 세션 구성의 속성을 표시 하기 위해 PowerShell 3.0에서 세션 구성 개체가 확장 됩니다.

예를 들어 세션 구성 개체의 모든 속성을 보려면 다음을 입력 합니다.

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

PowerShell에서 WSMan 공급자를 사용 하 여 세션 구성을 볼 수도 있습니다. WSMan 공급자는 세션에 WSMAN: 드라이브를 만듭니다.

WSMAN: 드라이브에서 세션 구성은 플러그 인 노드에 있습니다. 모든 세션 구성은 플러그 인 노드에 있지만 세션 구성이 아닌 플러그 인 노드에 항목이 있습니다.

예를 들어 로컬 컴퓨터의 세션 구성을 보려면 다음과 같이 입력 합니다.

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

원격 컴퓨터에서 세션 구성 보기

원격 컴퓨터의 세션 구성을 보려면 Connect-WSMan cmdlet을 사용 하 여 원격 컴퓨터의 정보를 로컬 컴퓨터의 WSMAN: 드라이브에 추가한 다음 WSMAN: 드라이브를 사용 하 여 세션 구성을 확인 합니다.

예를 들어 다음 명령은 로컬 컴퓨터의 WSMAN: 드라이브에 Server01 원격 컴퓨터에 대 한 노드를 추가 합니다.

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

명령이 완료 되 면 Server01 컴퓨터의 노드로 이동 하 여 세션 구성을 볼 수 있습니다.

다음은 그 예입니다. 

```powershell
PS C:> cd wsman:

PS WSMan:> dir

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01.corp.fabrikam.com                    Container

PS WSMan:> dir server01\plugin\

WSManConfig: Microsoft.WSMan.Management\WSMan::server01.corp.fabrikam.com\Pl
ugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

세션 구성의 보안 설명자 변경

Windows server 2012 이상 버전의 Windows Server에서는 기본적으로 원격 사용자에 대해 기본 제공 세션 구성이 사용 됩니다. 지원 되는 다른 버전의 Windows에서는 원격 액세스를 허용 하도록 세션 구성의 보안 설명자를 변경 해야 합니다.

컴퓨터의 세션 구성에 대 한 원격 액세스를 사용 하도록 설정 하려면 Enable-PSRemoting cmdlet을 사용 합니다. 이 cmdlet은 두 개의 세션 구성을 만듭니다.

- 이름이 "PowerShell"로 정의 됩니다. + "현재 PowerShell 버전"
- 이름이 "PowerShell. 6" 인 경우 특정 PowerShell 버전에 연결 되지 않습니다.

또한 기본적으로 컴퓨터의 Administrators 그룹 구성원만 기본 세션 구성에 대 한 실행 권한을 가지 지만 기본 세션 구성 및 사용자가 만든 모든 세션 구성에 대 한 보안 설명자를 변경할 수 있습니다.

다른 사용자에 게 원격으로 컴퓨터에 연결할 수 있는 권한을 부여 하려면 Set-PSSessionConfiguration cmdlet을 사용 하 여 해당 사용자에 대 한 "실행" 권한을 Microsoft.powershell32 세션 구성의 보안 설명자에 추가 합니다.

예를 들어 다음 명령은 Microsoft PowerShell 기본 세션 구성에 대 한 보안 설명자를 변경할 수 있는 속성 페이지를 엽니다.

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

컴퓨터의 모든 세션 구성에 대 한 모든 권한을 거부 하려면 Disable-PSSessionConfiguration cmdlet을 사용 합니다. 예를 들어 다음 명령은 컴퓨터에서 기본 세션 구성을 사용 하지 않도록 설정 합니다.

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

원격 사용자가 컴퓨터에 연결 하는 것을 방지 하기 위해 로컬 사용자가 연결할 수 있도록 하려면 Disable-PSRemoting cmdlet을 사용 합니다. Disable-PSRemoting 컴퓨터의 모든 세션 구성에 "Network_Deny_All" 항목을 추가 합니다.

```powershell
PS C:> Disable-PSRemoting
```

원격 사용자가 컴퓨터에서 모든 세션 구성을 사용할 수 있도록 하려면 Enable-PSRemoting 또는 Enable-PSSessionConfiguration cmdlet을 사용 합니다. 예를 들어 다음 명령은 기본 제공 세션 구성에 대 한 원격 액세스를 사용 하도록 설정 합니다.

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

세션 구성의 보안 설명자에 대 한 다른 변경 작업을 수행 하려면 Set-PSSessionConfiguration cmdlet을 사용 합니다. SecurityDescriptorSDDL 매개 변수를 사용 하 여 SDDL 문자열 값을 제출 합니다. ShowSecurityDescriptorUI 매개 변수를 사용 하 여 새 SDDL을 만드는 데 도움이 되는 사용자 인터페이스 속성 시트를 표시 합니다.

다음은 그 예입니다. 

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

새 세션 구성 만들기

로컬 컴퓨터에서 새 세션 구성을 만들려면 Register-PSSessionConfiguration cmdlet을 사용 합니다. 새 세션 구성을 정의 하기 위해 c # 어셈블리, PowerShell 스크립트 및 Register-PSSessionConfiguration cmdlet의 매개 변수를 사용할 수 있습니다.

예를 들어 다음 명령은 원격 명령에서 받은 데이터를 20mb로 제한 한다는 점을 제외 하 고는 Microsoft. PowerShell 세션 구성과 동일한 세션 구성을 만듭니다. 기본값은 50입니다.

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

세션 구성을 만들 때 다른 세션 구성 cmdlet을 사용 하 여 관리할 수 있으며,이는 WSMAN: 드라이브에 표시 됩니다.

자세한 내용은 Register-pssessionconfiguration를 참조 하세요.

세션 구성 제거

로컬 컴퓨터에서 세션 구성을 제거 하려면 Unregister-PSSessionConfiguration cmdlet을 사용 합니다. 예를 들어 다음 명령은 컴퓨터에서 NewConfig 세션 구성을 제거 합니다.

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

자세한 내용은 Register-pssessionconfiguration을 참조 하세요.

세션 구성 복원

실수로 삭제 (등록 취소) 된 기본 세션 구성을 복원 하려면 Enable-PSRemoting cmdlet을 사용 합니다.

Enable-PSRemoting cmdlet은 컴퓨터에 존재 하지 않는 모든 기본 세션 구성을 다시 만듭니다. 기존 세션 구성의 속성 값을 덮어쓰거나 변경 하지 않습니다.

기본 세션 구성의 원래 속성 값을 복원 하려면 Unregister-PSSessionConfiguration을 사용 하 여 세션 구성을 삭제 한 다음 Enable-PSRemoting cmdlet을 사용 하 여 다시 만드십시오.

세션 구성 선택

세션에 대 한 특정 세션 구성을 선택 하려면 New-PSSession, Enter-PSSession 또는 Invoke 명령의 ConfigurationName 매개 변수를 사용 합니다.

예를 들어이 명령은 New-PSSession cmdlet을 사용 하 여 Server01 컴퓨터에서 PSSession을 시작 합니다. 이 명령은 ConfigurationName 매개 변수를 사용 하 여 Server01 컴퓨터에서 WithProfile 구성을 선택 합니다.

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

이 명령은 현재 사용자가 WithProfile 세션 구성을 사용할 수 있는 권한이 있거나 필요한 권한이 있는 사용자의 자격 증명을 제공할 수 있는 경우에만 성공 합니다.

$PSSessionConfigurationName 기본 설정 변수를 사용 하 여 컴퓨터의 기본 세션 구성을 변경할 수도 있습니다. $PSSessionConfigurationName 기본 설정 변수에 대 한 자세한 내용은 about_Preference_Variables을 참조 하세요.

## <a name="keywords"></a>어

about_Endpoints about_SessionConfigurations

## <a name="see-also"></a>참고 항목

[about_Preference_Variables](about_Preference_Variables.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Session_Configuration_Files](about_Session_Configuration_Files.md)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Disable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[Enable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[Get-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[New-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[Register-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[Set-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[Test-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[Unregister-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

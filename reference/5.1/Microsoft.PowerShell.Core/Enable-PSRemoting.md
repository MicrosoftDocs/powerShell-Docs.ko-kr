---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 0c8c386ab376afde3d15fcd29b3f653b3f738f63
ms.sourcegitcommit: 0e0f45d0d8deb8c9088a4f4a32218edde052b686
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/17/2020
ms.locfileid: "93218041"
---
# Enable-PSRemoting

## 개요
원격 명령을 받도록 컴퓨터를 구성합니다.

## SYNTAX

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Enable-PSRemoting`Cmdlet은 WS-Management 기술을 사용 하 여 전송 된 PowerShell 원격 명령을 받도록 컴퓨터를 구성 합니다.

Windows Server 2012에서는 PowerShell remoting이 기본적으로 사용 하도록 설정 되어 있습니다. `Enable-PSRemoting`를 사용 하 여 지원 되는 다른 windows 버전에서 PowerShell 원격을 사용 하도록 설정 하 고 Windows Server 2012에서 원격 기능을 사용 하지 않도록 설정할 수 있습니다.

명령을 수신 하는 각 컴퓨터에서이 명령을 한 번만 실행 해야 합니다. 명령을 전송 하는 컴퓨터에서는 실행할 필요가 없습니다. 구성에서 수신기를 시작 하기 때문에 필요한 경우에만 실행 하는 것이 좋습니다.

PowerShell 3.0부터 `Enable-PSRemoting` 이 cmdlet은 컴퓨터가 공용 네트워크에 있을 때 Windows 클라이언트 버전에서 powershell 원격 기능을 사용 하도록 설정할 수 있습니다. 자세한 내용은 **SkipNetworkProfileCheck** 매개 변수에 대한 설명을 참조하세요.

`Enable-PSRemoting`Cmdlet은 다음 작업을 수행 합니다.

- 다음 작업을 수행 하는 [set-wsmanquickconfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet을 실행 합니다.
  - WinRM 서비스를 시작 합니다.
  - WinRM 서비스의 시작 유형을 자동으로 설정 합니다.
  - 모든 IP 주소에서 요청을 수락 하는 수신기를 만듭니다.
  - WS-Management 통신에 대 한 방화벽 예외를 사용 하도록 설정 합니다.
  - 아직 등록 되지 않은 경우 **microsoft. powershell** 및 **microsoft 워크플로** 세션 구성을 등록 합니다.
  - **Microsoft.powershell32** 세션 구성이 아직 등록 되지 않은 경우 64 비트 컴퓨터에 등록 합니다.
  - 모든 세션 구성을 사용 하도록 설정 합니다.
  - 모든 세션 구성의 보안 설명자를 변경 하 여 원격 액세스를 허용 합니다.
- WinRM 서비스를 다시 시작 하 여 위의 변경 내용이 적용 되도록 합니다.

Windows 플랫폼에서이 cmdlet을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다. Linux 또는 MacOS 버전의 PowerShell에는 적용 되지 않습니다.

> [!CAUTION]
> PowerShell 3.0 및 PowerShell 2.0이 모두 있는 시스템에서는 PowerShell 2.0을 사용 하 여 및 cmdlet을 실행 하지 마세요 `Enable-PSRemoting` `Disable-PSRemoting` . 명령이 성공한 것처럼 보일 수 있지만 원격 기능이 올바르게 구성되지 않았습니다. 원격 명령 및 원격 기능을 사용 하거나 사용 하지 않도록 설정 하려고 하면 실패할 가능성이 높습니다.

## 예제

### 예 1: 원격 명령을 받도록 컴퓨터 구성

이 명령은 원격 명령을 수신하도록 컴퓨터를 구성합니다.

```powershell
Enable-PSRemoting
```

### 예 2: 확인 메시지 없이 원격 명령을 받도록 컴퓨터 구성

이 명령은 원격 명령을 수신하도록 컴퓨터를 구성합니다.
**Force** 매개 변수를 사용 하면 사용자 프롬프트가 표시 되지 않습니다.

```powershell
Enable-PSRemoting -Force
```

### 예제 3: 클라이언트에서 원격 액세스 허용

이 예제에서는 Windows 운영 체제 클라이언트 버전의 공용 네트워크에서 원격 액세스를 허용 하는 방법을 보여 줍니다. 방화벽 규칙의 이름은 서로 다른 버전의 Windows에 대해 다를 수 있습니다.
`Get-NetFirewallRule`규칙 목록을 보려면를 사용 합니다. 방화벽 규칙을 사용 하도록 설정 하기 전에 규칙의 보안 설정을 확인 하 여 구성이 환경에 적합 한지 확인 합니다.

```powershell
Get-NetFirewallRule -Name 'WINRM*' | Select-Object Name
```

```Output
Name
----
WINRM-HTTP-In-TCP-NoScope
WINRM-HTTP-In-TCP
WINRM-HTTP-Compat-In-TCP-NoScope
WINRM-HTTP-Compat-In-TCP
```

```powershell
Enable-PSRemoting -SkipNetworkProfileCheck -Force
Set-NetFirewallRule -Name 'WINRM-HTTP-In-TCP' -RemoteAddress Any
```

기본적으로에서는 `Enable-PSRemoting` 개인 및 도메인 네트워크에서 원격 액세스를 허용 하는 네트워크 규칙을 만듭니다. 이 명령은 **SkipNetworkProfileCheck** 매개 변수를 사용하여 동일한 로컬 서브넷에 있는 공용 네트워크에서의 원격 액세스를 허용합니다. 명령은 **Force** 매개 변수를 지정 하 여 확인 메시지를 표시 하지 않습니다.

**SkipNetworkProfileCheck** 매개 변수는 기본적으로 동일한 로컬 서브넷에 있는 공용 네트워크에서의 원격 액세스를 허용 하는 Windows 운영 체제의 서버 버전에 영향을 주지 않습니다.

`Set-NetFirewallRule` **Netsecurity** 모듈의 cmdlet은 원격 위치의 공용 네트워크에서 원격 액세스를 허용 하는 방화벽 규칙을 추가 합니다. 여기에는 다른 서브넷의 위치가 포함 됩니다.

> [!NOTE]
> 방화벽 규칙의 이름은 Windows 버전에 따라 다를 수 있습니다. Cmdlet을 사용 `Get-NetFirewallRule` 하 여 시스템에 있는 규칙의 이름을 나열 합니다.

## PARAMETERS

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

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

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

### -SkipNetworkProfileCheck

이 cmdlet은 컴퓨터가 공용 네트워크에 있을 때 Windows 운영 체제의 클라이언트 버전에서 원격 기능을 사용할 수 있음을 나타냅니다. 이 매개 변수는 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용하는 방화벽 규칙을 공용 네트워크에 사용하도록 설정합니다.

이 매개 변수는 기본적으로 공용 네트워크에 대 한 로컬 서브넷 방화벽 규칙이 있는 Windows 운영 체제의 서버 버전에 영향을 주지 않습니다. 서버 버전에서 로컬 서브넷 방화벽 규칙을 사용 하지 않도록 설정한 경우 `Enable-PSRemoting` 이 매개 변수 값에 관계 없이을 다시 사용 하도록 설정 합니다.

로컬 서브넷 제한을 제거 하 고 공용 네트워크의 모든 위치에서 원격 액세스를 사용 하도록 설정 하려면 `Set-NetFirewallRule` **netsecurity** 모듈에서 cmdlet을 사용 합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### System.String

이 cmdlet은 결과를 설명 하는 문자열을 반환 합니다.

## 참고

PowerShell 3.0에서는 `Enable-PSRemoting` WS-Management 통신에 대해 다음과 같은 방화벽 예외를 만듭니다.

서버 버전의 Windows 운영 체제에서는 `Enable-PSRemoting` 원격 액세스를 허용 하는 개인 및 도메인 네트워크에 대 한 방화벽 규칙을 만들고, 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용 하는 공용 네트워크에 대 한 방화벽 규칙을 만듭니다.

클라이언트 버전의 Windows 운영 체제에서 `Enable-PSRemoting` PowerShell 3.0은 무제한 원격 액세스를 허용 하는 개인 및 도메인 네트워크에 대 한 방화벽 규칙을 만듭니다. 공용 네트워크에 대해 동일한 로컬 서브넷에서의 원격 액세스를 허용하는 방화벽 규칙을 만들려면 **SkipNetworkProfileCheck** 매개 변수를 사용합니다.

클라이언트 또는 서버 버전의 Windows 운영 체제에서 로컬 서브넷 제한을 제거 하 고 원격 액세스를 허용 하는 공용 네트워크에 대 한 방화벽 규칙을 만들려면 `Set-NetFirewallRule` NetSecurity 모듈에서 cmdlet을 사용 하 여 다음 명령을 실행 합니다. `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`

PowerShell 2.0에서는 `Enable-PSRemoting` WS-Management 통신에 대해 다음과 같은 방화벽 예외를 만듭니다.

서버 버전의 Windows 운영 체제에서는 원격 액세스를 허용 하는 모든 네트워크에 대 한 방화벽 규칙을 만듭니다.

Windows 운영 체제의 클라이언트 버전에서 `Enable-PSRemoting` PowerShell 2.0은 도메인 및 개인 네트워크 위치에 대해서만 방화벽 예외를 만듭니다. 보안 위험을 최소화 하기 위해에서는 `Enable-PSRemoting` Windows 클라이언트 버전에서 공용 네트워크에 대 한 방화벽 규칙을 만들지 않습니다. 현재 네트워크 위치가 public 이면에서 `Enable-PSRemoting` 방화벽의 상태를 확인할 수 없습니다. 메시지를 반환 합니다.

PowerShell 3.0부터 `Enable-PSRemoting` 모든 세션 구성의 **Enabled** 속성 값을로 설정 하 여 모든 세션 구성을 사용 하도록 설정 `$True` 합니다.

PowerShell 2.0에서는 `Enable-PSRemoting` 세션 구성의 보안 설명자에서 **Deny_All** 설정을 제거 합니다. PowerShell 3.0에서는 `Enable-PSRemoting` **Deny_All** 및 **Network_Deny_All** 설정을 제거 합니다. 로컬에서 사용 하도록 예약 된 세션 구성에 대 한 원격 액세스를 제공 합니다.

## 관련 링크

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Disable-PSRemoting](Disable-PSRemoting.md)

[WSMan 공급자](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Remote](About/about_Remote.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

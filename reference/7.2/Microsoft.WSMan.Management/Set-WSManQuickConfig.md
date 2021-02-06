---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: e5d50af0551a183b8e9e1995fbd722c331a48486
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600416"
---
# Set-WSManQuickConfig

## 개요
원격 관리를 위해 로컬 컴퓨터를 구성합니다.

## SYNTAX

### 모두

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## 설명

`Set-WSManQuickConfig`Cmdlet은 ws-management (Web Services For management) 기술을 사용 하 여 전송 된 PowerShell 원격 명령을 받도록 컴퓨터를 구성 합니다.

`Set-WSManQuickConfig` 는 다음 작업을 수행합니다.

- WinRM 서비스가 실행 중인지 확인 합니다. WinRM 서비스가 실행 되 고 있지 않은 경우 서비스가 시작 됩니다.
- WinRM 서비스 시작 유형을 자동으로 설정 합니다.
- 모든 IP 주소에서 요청을 수락 하는 수신기를 만듭니다. 기본 전송은 **HTTP** 입니다.
- WinRM 트래픽에 대해 방화벽 예외를 사용 하도록 설정 합니다.

를 실행 하려면 `Set-WSManQuickConfig` **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.

## 예제

### 예제 1: HTTP를 통해 로컬 컴퓨터의 원격 관리 사용

이 예에서는 로컬 컴퓨터의 원격 관리를 사용 하도록 설정 하는 데 필요한 구성을 설정 합니다. 기본적으로이 명령은 **HTTP** 에 WS-Management 수신기를 만듭니다.

```powershell
Set-WSManQuickConfig
```

### 예 2: HTTPS를 통해 로컬 컴퓨터의 원격 관리 사용

이 예에서는 로컬 컴퓨터의 원격 관리를 사용 하도록 설정 하는 데 필요한 구성을 설정 합니다. **UseSSL** 매개 변수는 **HTTPS** 가 컴퓨터와 통신 하는 데 사용 되도록 지정 합니다.

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> **HTTPS** 를 사용 하려면 수동 구성이 필요 합니다. 자세한 내용은 **UseSSL** 매개 변수의 설명을 참조 하십시오.

## PARAMETERS

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipNetworkProfileCheck

컴퓨터가 공용 네트워크에 있을 때 원격 기능을 사용할 수 있도록 Windows 클라이언트 버전을 구성 합니다. 이 매개 변수는 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용하는 방화벽 규칙을 공용 네트워크에 사용하도록 설정합니다.

이 매개 변수는 기본적으로 공용 네트워크에 대 한 로컬 서브넷 방화벽 규칙이 있는 Windows 서버 버전에는 영향을 주지 않습니다. 서버 버전의 Windows에서 로컬 서브넷 방화벽 규칙을 사용 하지 않도록 설정한 경우 `Enable-PSRemoting` 이 매개 변수의 값에 관계 없이에서 다시 사용 하도록 설정 합니다.

로컬 서브넷 제한을 제거 하 고 공용 네트워크의 모든 위치에서 원격 액세스를 사용 하도록 설정 하려면 `Set-NetFirewallRule` **netsecurity** 모듈에서 cmdlet을 사용 합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

원격 컴퓨터에 대 한 연결을 설정 하는 데 SSL (SSL(Secure Sockets Layer)) 프로토콜을 사용 하도록 지정 합니다. 기본적으로 SSL은 사용 되지 않습니다.

WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다. **UseSSL** 매개 변수를 사용 하 여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다. 이 매개 변수를 사용 하 고 연결에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.

**HTTPS** 는 WinRM 및 방화벽 규칙을 수동으로 구성 해야 합니다. 자세한 내용은 [방법: HTTPS에 대해 WINRM 구성](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)을 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

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

이 cmdlet은 어떠한 입력도 허용 하지 않습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성 하지 않습니다.

## 참고

## 관련 링크

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-PSRemoting](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[방법: HTTPS에 대해 WINRM 구성](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Test-WSMan](Test-WSMan.md)


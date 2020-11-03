---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 08/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/enable-wsmancredssp?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManCredSSP
ms.openlocfilehash: 3f1b72c2cbdf5d7b9ef4b77bcca7277ccbe8b021
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218729"
---
# Enable-WSManCredSSP

## 개요
컴퓨터에서 CredSSP (Credential Security Support Provider) 인증을 사용 하도록 설정 합니다.

## SYNTAX

### 모두

```
Enable-WSManCredSSP [[-DelegateComputer] <String[]>] [-Force] [-Role] <String> [<CommonParameters>]
```

## 설명

`Enable-WSManCredSSP`Cmdlet은 클라이언트 또는 서버 컴퓨터에서 CredSSP 인증을 사용 하도록 설정 합니다.
CredSSP 인증을 사용 하는 경우 사용자 자격 증명이 인증을 위해 원격 컴퓨터에 전달 됩니다. 이 인증 유형은 다른 원격 세션에서 원격 세션을 만드는 명령을 위해 설계 되었습니다. 예를 들어 원격 컴퓨터에서 백그라운드 작업을 실행 하려는 경우 이러한 종류의 인증을 사용 합니다.

`Enable-WSManCredSSP`**클라이언트** 또는 **서버** 에서 CredSSP를 사용 하도록 설정할 수 있습니다. 클라이언트에서 CredSSP를 사용 하도록 설정 하려면 **Role** 매개 변수에 **client** 를 지정 합니다. 클라이언트는 서버 인증이 수행 될 때 서버에 명시적 자격 증명을 위임 합니다. 서버에서 CredSSP를 사용 하도록 설정 하려면 **Role** 매개 변수에 **server** 를 지정 합니다. 서버는 클라이언트의 대리자 역할을 합니다. 자세한 내용은 매개 변수 섹션의 **역할** 을 참조 하세요.

> [!CAUTION]
> CredSSP 인증은 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다. 이렇게 하면 원격 작업의 보안 위험이 증가합니다. 원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.

## 예제

### 예제 1: 클라이언트 자격 증명 위임

이 예에서는 정규화 된 도메인 이름을 사용 하 여 컴퓨터에 클라이언트 자격 증명을 위임할 수 있습니다.

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "Server02.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### 예 2: 도메인의 모든 컴퓨터에 클라이언트 자격 증명 위임

이 예에서는 **fabrikam.com** 도메인의 모든 컴퓨터에 클라이언트 자격 증명을 위임할 수 있습니다. 별표 ( `*` ) 와일드 카드는 모든 컴퓨터를 지정 합니다.

> [!NOTE]
> **DelegateComputer** 매개 변수와 함께 와일드 카드를 사용 하면 필요한 것 보다 많은 컴퓨터에서 CredSSP를 사용 하도록 설정할 수 있습니다.

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "*.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### 예 3: 여러 컴퓨터에 클라이언트 자격 증명 위임

이 예제에서는 클라이언트 자격 증명이 여러 컴퓨터에 위임 될 수 있도록 합니다.

```powershell
$servers = "server02.fabrikam.com", "server03.fabrikam.com", "server04.fabrikam.com"
Enable-WSManCredSSP -Role "Client" -DelegateComputer $servers
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

`$servers`변수는 서버 이름 목록을 포함 합니다. `Enable-WSManCredSSP`**role** 매개 변수를 사용 하 여 **클라이언트** 역할을 지정 합니다. **DelegateComputer** 는 변수에서 컴퓨터 이름을 가져옵니다 `$servers` .

### 예제 4: 컴퓨터에서 대리자 역할을 할 수 있도록 허용

이 예제에서는 컴퓨터가 다른 컴퓨터의 대리자 역할을 할 수 있도록 합니다. `Enable-WSManCredSSP`앞의 예제에 표시 된 cmdlet은 클라이언트 에서만 CredSSP 인증을 사용 하도록 설정 하 고, 대신 작업을 수행할 수 있는 원격 컴퓨터를 지정 합니다. 원격 컴퓨터가 클라이언트의 대리자 역할을 하도록 하려면 WSMan의 **서비스** 노드에 있는 CredSSP 항목을 true로 설정 해야 합니다. 이 예에서는 WSMan의 **서비스** 노드에 있는 CredSSP 항목을 true로 설정 합니다.

```powershell
Enable-WSManCredSSP -Role "Server"
```

### 예제 5: 컴퓨터에서 Set-Item를 사용 하 여 대리자 역할을 할 수 있도록 허용

이 예제에서는 컴퓨터가 다른 컴퓨터의 대리자 역할을 할 수 있도록 합니다. `Enable-WSManCredSSP`이전 예제에 표시 된 명령은 클라이언트 컴퓨터 에서만 CredSSP 인증을 사용 하도록 설정 하 고 클라이언트 컴퓨터를 대신 하 여 작동할 수 있는 원격 컴퓨터를 지정 합니다. 원격 컴퓨터가 클라이언트 컴퓨터의 대리자 역할을 하도록 하려면 WSMan 공급자의 서비스 디렉터리에 있는 CredSSP 항목을 true로 설정해야 합니다.

```powershell
Connect-WSMan -ComputerName "server02"
Set-Item -Path "WSMan:\server02\service\auth\credSSP" -Value $True
```

`Connect-WSMan` 원격 컴퓨터 server02에 대 한 연결을 만듭니다. `Set-Item` 는 **Path** 매개 변수를 사용 하 여 **WSMan** 공급자의 위치를 지정 합니다. **값** 매개 변수는 **서비스** 설정을 true로 설정 합니다.

## PARAMETERS

### -DelegateComputer

클라이언트 자격 증명을 위임할 서버를 지정 합니다. 가장 좋은 방법은 정규화 된 도메인 이름을 사용 하는 것입니다.

와일드 카드가 허용 되지만 필요한 것 보다 많은 컴퓨터에서 CredSSP를 사용 하도록 설정할 수 있습니다.

**Role** 매개 변수가 **Client** 인 경우이 매개 변수를 지정 해야 합니다. **Role** 이 **Server** 인 경우이 매개 변수를 지정 하지 마세요.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

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

### -Role

CredSSP를 클라이언트 또는 서버로 사용할지 여부를 지정 합니다. 이 매개 변수에 허용 되는 값은 **클라이언트** 및 **서버** 입니다.

**클라이언트** 를 지정 하는 경우 다음 작업이 수행 됩니다. 서버 인증이 수행될 때 이러한 설정을 통해 클라이언트는 명시적 자격 증명을 서버에 위임할 수 있습니다.

- 클라이언트에서 CredSSP를 사용 하도록 설정 합니다.
- WS-Management 설정을 `\<localhost|computername\>\Client\Auth\CredSSP` true로 설정 합니다.
- 클라이언트에서 Windows CredSSP 정책 **AllowFreshCredentials** 을 **WSMan/Delegate** 로 설정 합니다.

**서버** 를 지정 하는 경우 다음 작업이 수행 됩니다. 이 정책 설정을 통해 서버는 클라이언트의 대리자 역할을 할 수 있습니다.

- 서버에서 CredSSP를 사용 하도록 설정 합니다.
- WS-Management 설정을 `\<localhost|computername\>\Service\Auth\CredSSP` true로 설정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet은 어떠한 입력도 허용 하지 않습니다.

## 출력

### System.Xml.Xml요소

CredSSP 인증을 사용 하는 경우이 cmdlet은 **XMLElement** 개체를 생성 합니다.

## 참고

CredSSP 인증을 사용 하지 않도록 설정 하려면 cmdlet을 사용 `Disable-WSManCredSSP` 합니다.

## 관련 링크

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)


---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: 3202e21b5f002610557f827f3a5f65659dec6823
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210841"
---
# Disable-WSManCredSSP

## 개요
컴퓨터에서 CredSSP 인증을 사용 하지 않도록 설정 합니다.

## SYNTAX

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## 설명
**Enable-wsmancredssp** cmdlet은 클라이언트 또는 서버 컴퓨터에서 CredSSP (Credential Security Support Provider) 인증을 사용 하지 않도록 설정 합니다.
CredSSP 인증을 사용 하는 경우 사용자 자격 증명이 인증을 위해 원격 컴퓨터에 전달 됩니다.

이 cmdlet을 사용 하면 *Role* 매개 변수에 client를 지정 하 여 클라이언트에서 CredSSP를 사용 하지 않도록 설정할 수 있습니다.
이 cmdlet은 다음 작업을 수행 합니다.

- 클라이언트에서 CredSSP를 사용 하지 않도록 설정 합니다. 이 cmdlet은 WS-Management 설정 **\<localhost|computername\> \Client\auth\ststst\sts** 를 false로 설정 합니다.
- 클라이언트의 Windows CredSSP 정책 **AllowFreshCredentials** 에서 WSMan/* 설정을 제거 합니다.

이 cmdlet을 사용 하면 *역할* 에 서버를 지정 하 여 서버에서 CredSSP를 사용 하지 않도록 설정할 수 있습니다.
이 cmdlet은 다음 작업을 수행 합니다.

- 서버에서 CredSSP를 사용 하지 않도록 설정 합니다. 이 cmdlet은 WS-Management 설정 **\<localhost|computername\> \Service\auth\test\des** 를 false로 설정 합니다.

주의: CredSSP 인증은 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.
이렇게 하면 원격 작업의 보안 위험이 증가합니다.
원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.

## 예제

### 예 1: 클라이언트에서 CredSSP를 사용 하지 않도록 설정

```
PS C:\> Disable-WSManCredSSP -Role Client
```

이 명령은 클라이언트에서 CredSSP를 사용하지 않도록 설정하여 서버에 대한 위임을 방지합니다.

### 예 2: 서버에서 CredSSP를 사용 하지 않도록 설정

```
PS C:\> Disable-WSManCredSSP -Role Server
```

이 명령은 서버에서 CredSSP를 사용하지 않도록 설정하여 클라이언트의 위임을 방지합니다.

## PARAMETERS

### -Role
클라이언트 또는 서버로 CredSSP를 사용 하지 않도록 설정할지 여부를 지정 합니다.
이 매개 변수에 허용 되는 값은 클라이언트 및 서버입니다.

Client를 지정 하는 경우이 cmdlet은 다음 작업을 수행 합니다.

- 클라이언트에서 CredSSP를 사용 하지 않도록 설정 합니다. 이 cmdlet은 **\<localhost|computername\> \Client\auth\stststn\sts** 를 false로 설정 WS-Management 설정 합니다.
- 클라이언트의 Windows CredSSP 정책 **AllowFreshCredentials** 에서 WSMan/* 설정을 제거 합니다.

서버를 지정 하는 경우이 cmdlet은 다음 작업을 수행 합니다.

- 서버에서 CredSSP를 사용 하지 않도록 설정 합니다. 이 cmdlet은 WS-Management 설정 **\<localhost|computername\> \Service\auth\test\des** 를 false로 설정 합니다.

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
이 cmdlet은 어떠한 입력도 허용하지 않습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* CredSSP 인증을 사용하도록 설정하려면 Enable-WSManCredSSP cmdlet을 사용합니다.

*

## 관련 링크

[Connect-WSMan](Connect-WSMan.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)

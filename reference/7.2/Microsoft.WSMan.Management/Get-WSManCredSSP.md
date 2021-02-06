---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: 9830d1feb31e9cca735a7ac8d2ed9d2ec50380b5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601238"
---
# Get-WSManCredSSP

## 개요
클라이언트의 Credential Security Support Provider 관련 구성을 가져옵니다.

## SYNTAX

```
Get-WSManCredSSP [<CommonParameters>]
```

## 설명
**Enable-wsmancredssp** cmdlet은 클라이언트 및 서버의 Credential Security Support Provider 관련 구성을 가져옵니다.
출력은 CredSSP(Credential Security Support Provider) 인증의 사용 여부를 나타냅니다.
이 cmdlet은 또한 CredSSP의 **AllowFreshCredentials** 정책에 대 한 구성 정보를 표시 합니다.

CredSSP 인증을 사용 하는 경우 사용자 자격 증명이 인증을 위해 원격 컴퓨터에 전달 됩니다.
이 인증 유형은 다른 원격 세션에서 원격 세션을 만드는 명령을 위해 설계 되었습니다.
예를 들어 원격 컴퓨터에서 백그라운드 작업을 실행 하려는 경우 이러한 종류의 인증을 사용 합니다.

이 cmdlet은 다음 작업을 수행합니다.

- 클라이언트의 WS-Management CredSSP 설정 (**\<localhost|computername\> \Client\auth\stststst\sts**)을 가져옵니다.
- Windows CredSSP 정책 설정 **AllowFreshCredentials** 을 가져옵니다.
- 서버에 대 한 WS-Management CredSSP 설정을 가져옵니다 (**\Service\\auth\stst\stst\stst\des \<localhost|computername\>**)

주의: CredSSP 인증은 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.
이렇게 하면 원격 작업의 보안 위험이 증가합니다.
원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.

## 예제

### 예제 1: CredSSP 구성 표시

```
PS C:\> Get-WSManCredSSP
```

이 명령은 클라이언트와 서버 둘 다의 CredSSP 구성 정보를 표시합니다.

출력에서 이 컴퓨터가 CredSSP에 대해 구성되었는지 여부가 식별됩니다.

컴퓨터가 CredSSP에 대해 구성된 경우 출력은 다음과 같습니다.

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

컴퓨터가 CredSSP에 대해 구성되지 않은 경우 출력은 다음과 같습니다.

`The machine is not configured to allow delegating fresh credentials.`

## PARAMETERS

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet은 어떠한 입력도 허용하지 않습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* CredSSP 인증을 사용하지 않도록 설정하려면 Disable-WSManCredSSP cmdlet을 사용합니다. CredSSP 인증을 사용하도록 설정하려면 Enable-WSManCredSSP cmdlet을 사용합니다.

## 관련 링크

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)


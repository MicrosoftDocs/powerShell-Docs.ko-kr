---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disconnect-wsman?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-WSMan
ms.openlocfilehash: 211f1f1129a5497226dfa2d716955cf65c87ecbb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212537"
---
# Disconnect-WSMan

## 개요
원격 컴퓨터의 WinRM 서비스에서 클라이언트 연결을 끊습니다.

## SYNTAX

```
Disconnect-WSMan [[-ComputerName] <String>] [<CommonParameters>]
```

## 설명
**연결 끊기** cmdlet은 원격 컴퓨터의 WinRM 서비스에서 클라이언트 연결을 끊습니다.
WS-Management 세션을 변수에 저장 한 경우 세션 개체는 변수에 유지 되지만 WS-Management 세션의 상태는 닫힙니다.
WSMan 공급자의 컨텍스트 내에서 이 cmdlet을 사용하여 원격 컴퓨터의 WinRM 서비스에서 클라이언트 연결을 끊을 수 있습니다.
그러나 WSMan 공급자로 변경하기 전에 이 cmdlet을 사용하여 원격 컴퓨터의 WinRM 서비스에서 연결을 끊을 수도 있습니다.

원격 컴퓨터의 WinRM 서비스에 연결하는 방법에 대한 자세한 내용은 Connect-WSMan을 참조하세요.

## 예제

### 예 1: 원격 컴퓨터에 대 한 연결 삭제

```
PS C:\> Disconnect-WSMan -computer server01
PS C:\> cd WSMan:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
```

이 명령은 server01 라는 원격 컴퓨터에 대 한 연결을 삭제 합니다.

이 cmdlet은 일반적으로 원격 컴퓨터(이 경우 server01 컴퓨터)에서 연결을 끊기 위해 WSMan 공급자의 컨텍스트 내에서 사용됩니다.
그러나 WSMan 공급자로 변경 하기 전에 연결 **끊기** 를 사용 하 여 원격 컴퓨터에 대 한 연결을 제거할 수도 있습니다.
이러한 연결은 ComputerName 목록에 표시 되지 않습니다.

## PARAMETERS

### -ComputerName
관리 작업을 실행할 컴퓨터를 지정 합니다.
이 값은 정규화된 도메인 이름, NetBIOS 이름 또는 IP 주소일 수 있습니다.
로컬 컴퓨터 이름, localhost 또는 점(.)을 사용하여 로컬 컴퓨터를 지정합니다.
로컬 컴퓨터가 기본값입니다.
원격 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름을 사용해야 합니다.
이 cmdlet에 이 매개 변수 값을 파이프할 수 있습니다.

로컬 호스트와의 연결을 끊을 수 없습니다.
즉, 로컬 컴퓨터에 대 한 기본 연결의 연결을 끊을 수 없습니다.
그러나 로컬 컴퓨터에 대 한 별도의 연결을 만드는 경우 (예: 컴퓨터 이름을 사용 하 여)

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
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

## 관련 링크

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

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

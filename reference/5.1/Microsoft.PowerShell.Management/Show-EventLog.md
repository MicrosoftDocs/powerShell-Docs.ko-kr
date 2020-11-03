---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-EventLog
ms.openlocfilehash: e8dbcf1aa4280c0481714a8a9fb24f2e5ef79ffe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214409"
---
# Show-EventLog

## 개요
로컬 또는 원격 컴퓨터의 이벤트 뷰어에 있는 이벤트 로그를 표시합니다.

## SYNTAX

```
Show-EventLog [[-ComputerName] <String>] [<CommonParameters>]
```

## 설명
**이벤트 표시** cmdlet은 로컬 컴퓨터에서 이벤트 뷰어를 열고 로컬 컴퓨터 또는 원격 컴퓨터의 모든 클래식 이벤트 로그에 표시 합니다.

Windows Vista 이상 버전의 Windows 운영 체제에서 이벤트 뷰어를 열려면 현재 사용자가 로컬 컴퓨터에서 Administrators 그룹의 구성원 이어야 합니다.

**Eventlog** 명사를 포함 하는 Cmdlet ( **eventlog** cmdlet)은 클래식 이벤트 로그 에서만 작동 합니다.
Windows Vista 이상 버전의 windows 운영 체제에서 Windows 이벤트 로그 기술을 사용 하는 로그에서 이벤트를 가져오려면 Get-WinEvent cmdlet을 사용 합니다.

## 예제

### 예 1: 로컬 컴퓨터에 대 한 이벤트 로그 표시

```
PS C:\> Show-EventLog
```

이 명령은 이벤트 뷰어를 열고 로컬 컴퓨터에 있는 기본 이벤트 로그를 표시합니다.

### 예 2: 원격 컴퓨터에 대 한 이벤트 로그 표시

```
PS C:\> Show-EventLog -ComputerName "Server01"
```

이 명령은 이벤트 뷰어를 열고 Server01 컴퓨터에 있는 기본 이벤트 로그를 표시합니다.

## PARAMETERS

### -ComputerName
원격 컴퓨터를 지정합니다.
**표시-** 이벤트 로그를 로컬 컴퓨터의 이벤트 뷰어 지정 된 컴퓨터에 표시 합니다.
기본값은 로컬 컴퓨터입니다.

원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.

이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.
원격 명령을 실행하도록 컴퓨터를 구성하지 않은 경우에도 *ComputerName* 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

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
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* 이벤트 뷰어를 열면 Windows PowerShell 명령 프롬프트가 나타납니다. 이벤트 뷰어가 열려 있는 동안 현재 세션에서 작업할 수 있습니다.

  이 cmdlet은 사용자 인터페이스가 필요하므로 Windows Server의 Server Core 설치에서 작동하지 않습니다.

*

## 관련 링크

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Write-EventLog](Write-EventLog.md)

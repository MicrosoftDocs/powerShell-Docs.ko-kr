---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSnapin
ms.openlocfilehash: 472a4c8fbb9eb0d37827aff4fcfd6bb9a67f4743
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212001"
---
# Get-PSSnapin

## 개요
컴퓨터의 Windows PowerShell 스냅인을 가져옵니다.

## SYNTAX

```
Get-PSSnapin [[-Name] <String[]>] [-Registered] [<CommonParameters>]
```

## 설명
**Add-pssnapin** cmdlet은 현재 세션에 추가 되었거나 시스템에 등록 된 Windows PowerShell 스냅인을 가져옵니다.
이 cmdlet은 검색 된 순서 대로 스냅인을 나열 합니다.

**Add-pssnapin** 는 등록 된 스냅인만 가져옵니다. Windows PowerShell 스냅인을 등록 하려면 Microsoft .NET Framework 2.0에 포함 된 Installutil.exe 도구를 사용 합니다.
자세한 내용은 MSDN library에서 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](https://go.microsoft.com/fwlink/?LinkID=143619) 을 참조 하십시오.

Windows PowerShell 3.0 부터는 Windows PowerShell에 포함 된 핵심 명령이 모듈에 패키지 됩니다.
단, 스냅인(PSSnapin)인 **Microsoft.PowerShell.Core** 는 예외입니다.
기본적으로 **Microsoft.PowerShell.Core** 스냅인만 세션에 추가됩니다.
모듈은 처음 사용할 때 자동으로 가져오며 Import-Module cmdlet을 사용 하 여 가져올 수 있습니다.

## 예제

### 예제 1: 현재 로드 된 스냅인 가져오기

```
PS C:\> Get-PSSnapIn
```

이 명령은 세션에 현재 로드된 Windows PowerShell 스냅인을 가져옵니다.
여기에는 Windows PowerShell과 함께 설치된 스냅인과 세션에 추가된 스냅인이 포함됩니다.

### 예제 2: 등록 된 스냅인 가져오기

```
PS C:\> get-PSSnapIn -Registered
```

이 명령은 세션에 이미 추가된 스냅인을 비롯하여 컴퓨터에 등록된 Windows PowerShell 스냅인을 가져옵니다.
Windows PowerShell과 함께 설치된 스냅인이나 시스템에 아직 등록되지 않은 Windows PowerShell 스냅인 DLL(동적 연결 라이브러리)은 출력에 포함되지 않습니다.

### 예제 3: 문자열과 일치 하는 현재 스냅인 가져오기

```
PS C:\> Get-PSSnapIn -Name smp*
```

이 명령은 현재 세션에서 이름이 smp로 시작 하는 Windows PowerShell 스냅인을 가져옵니다.

## PARAMETERS

### -Name
스냅인 이름 배열을 지정 합니다.
이 cmdlet은 지정 된 Windows PowerShell 스냅인만 가져옵니다. 와일드 카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -등록 됨
이 cmdlet은 세션에 아직 추가 되지 않은 경우에도 시스템에 등록 된 Windows PowerShell 스냅인을 가져옵니다.

Windows PowerShell과 함께 설치된 스냅인은 이 목록에 나타나지 않습니다.

이 매개 변수를 **사용** 하지 않으면 add-pssnapin은 세션에 추가 된 Windows PowerShell 스냅인을 가져옵니다.

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

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### PSSnapInInfo.
Get-PSSnapin은 가져오는 각 스냅인에 대한 개체를 반환합니다.

## 참고

* Windows PowerShell 3.0 부터는 Windows PowerShell과 함께 설치 되는 핵심 명령이 모듈에 패키지 됩니다. Windows PowerShell 2.0 및 이후 버전의 Windows PowerShell에서 이전 스타일의 세션을 만드는 호스트 프로그램에서 핵심 명령은 스냅인 ( **add-pssnapin** )으로 패키지 됩니다. 예외는 항상 스냅인 인 **Microsoft. PowerShell. Core** 입니다. 또한 New-PSSession cmdlet에서 시작한 것과 같은 원격 세션은 코어 스냅인을 포함 하는 이전 스타일의 세션입니다.

  핵심 모듈을 사용 하 여 최신 스타일의 세션을 만드는 **initialsessionstate.createdefault2** 메서드에 대 한 자세한 내용은 MSDN Library의 [initialsessionstate.createdefault2 메서드](https://msdn.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.createdefault2) 를 참조 하세요.

## 관련 링크

[Add-PSSnapin](Add-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)

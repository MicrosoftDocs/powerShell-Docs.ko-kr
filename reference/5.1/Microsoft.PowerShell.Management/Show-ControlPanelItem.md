---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-ControlPanelItem
ms.openlocfilehash: 368e385d51437f9ac93b700c929b185dce30a644
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214402"
---
# Show-ControlPanelItem

## 개요
제어판 항목을 엽니다.

## SYNTAX

### RegularName (기본값)

```
Show-ControlPanelItem [-Name] <String[]> [<CommonParameters>]
```

### CanonicalName

```
Show-ControlPanelItem -CanonicalName <String[]> [<CommonParameters>]
```

### Get-controlpanelitem

```
Show-ControlPanelItem [[-InputObject] <ControlPanelItem[]>] [<CommonParameters>]
```

## 설명

`Show-ControlPanelItem`Cmdlet은 로컬 컴퓨터에서 제어판 항목을 엽니다. 이를 사용 하 여 사용자 인터페이스가 없는 시스템 에서도 이름, 범주 또는 설명으로 제어판 항목을 열 수 있습니다. Cmdlet의 제어판 항목을로 파이프 할 수 있습니다 `Get-ControlPanelItem` `Show-ControlPanelItem` .

`Show-ControlPanelItem` 시스템에서 열 수 있는 제어판 항목만 검색 합니다. **제어판** 또는 **파일 탐색기** 가 없는 컴퓨터에서는 `Show-ControlPanelItem` 이러한 구성 요소 없이 열 수 있는 제어판 항목만 검색 합니다.

이 cmdlet은 Windows PowerShell 3.0에서 도입 되었으며 Windows 8, Windows Server 2012 이상 버전에서 작동 합니다.

## 예제

### 예제 1: 제어판 항목 표시

이 예제에서는 **자동 재생** 제어판 항목을 시작 합니다.

```powershell
Show-ControlPanelItem -Name "AutoPlay"
```

### 예제 2:이 cmdlet에 대 한 제어판 항목 파이프

이 예에서는 로컬 컴퓨터의 **Windows Defender 방화벽** 제어판 항목을 엽니다.
Windows 버전에서 Windows 방화벽 제어판 항목의 이름이 변경 되었습니다. 이 예제에서는 와일드 카드 패턴을 사용 하 여 제어판 항목을 찾습니다.

```powershell
Get-ControlPanelItem -Name "*Firewall" | Show-ControlPanelItem
```

`Get-ControlPanelItem` 제어판 항목을 가져오고 `Show-ControlPanelItem` cmdlet이 항목을 엽니다.

### 예제 3: 파일 이름을 사용 하 여 제어판 항목 열기

이 예제에서는 응용 프로그램 이름을 사용 하 여 **프로그램 및 기능** 제어판 항목을 엽니다.

```powershell
appwiz.cpl
```

이 메서드는 명령을 사용 하는 대신 사용할 수 `Show-ControlPanelItem` 있습니다.

> [!NOTE]
> PowerShell에서 제어판 파일의 .cpl 파일 확장명은 환경 변수의 값에 포함 되어 있으므로 생략할 수 있습니다. `$env:PathExt`

## PARAMETERS

### -CanonicalName

지정 된 정식 이름 또는 이름 패턴을 사용 하 여 제어판 항목을 지정 합니다. 와일드카드 문자를 사용할 수 있습니다. 여러 이름을 입력 하는 경우이 cmdlet은 이름 목록의 항목이 **OR** 연산자로 구분 된 것 처럼 이름 중 하 나와 일치 하는 제어판 항목을 엽니다.

```yaml
Type: System.String[]
Parameter Sets: CanonicalName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

제어판 항목 개체를 제출 하 여 열 제어판 항목을 지정 합니다. 제어판 항목 개체를 포함 하는 변수를 입력 하거나 제어판 항목 개체를 가져오는 명령 또는 식 (예:)을 입력 `Get-ControlPanelItem` 합니다.

```yaml
Type: Microsoft.PowerShell.Commands.ControlPanelItem[]
Parameter Sets: ControlPanelItem
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

제어판 항목의 이름을 지정 합니다. 와일드카드 문자를 사용할 수 있습니다. 여러 이름을 입력 하는 경우이 cmdlet은 이름 목록의 항목이 **OR** 연산자로 구분 된 것 처럼 이름 중 하 나와 일치 하는 제어판 항목을 엽니다.

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### Get-controlpanelitem, Microsoft. PowerShell.

이름 또는 제어판 항목 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

## 관련 링크

[Get-ControlPanelItem](Get-ControlPanelItem.md)

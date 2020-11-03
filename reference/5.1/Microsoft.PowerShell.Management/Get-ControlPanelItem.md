---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ControlPanelItem
ms.openlocfilehash: 51bc04b4de901a611330266b6b0f58471f998432
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215474"
---
# Get-ControlPanelItem

## 개요
제어판 항목을 가져옵니다.

## SYNTAX

### RegularName (기본값)

```
Get-ControlPanelItem [[-Name] <String[]>] [-Category <String[]>] [<CommonParameters>]
```

### CanonicalName

```
Get-ControlPanelItem -CanonicalName <String[]> [-Category <String[]>] [<CommonParameters>]
```

## 설명

`Get-ControlPanelItem`Cmdlet은 로컬 컴퓨터에서 제어판 항목을 가져옵니다. 이 cmdlet을 사용하면 사용자 인터페이스가 없는 시스템에서도 이름, 범주 또는 설명으로 제어판 항목을 찾을 수 있습니다.

이 cmdlet은 시스템에서 열 수 있는 제어판 항목만 가져옵니다. 제어판 또는 파일 탐색기가 없는 컴퓨터에서는이 cmdlet을 사용 하 여 이러한 구성 요소 없이 열 수 있는 제어판 항목만 가져옵니다.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다. Windows 8 및 Windows Server 2012 이상 에서만 작동 합니다.

## 예제

### 예제 1: 모든 제어판 항목 가져오기

이 명령은 로컬 컴퓨터에 있는 모든 제어판 항목을 가져옵니다.

```powershell
Get-ControlPanelItem
```

```Output
Name                          CanonicalName                 Category                      Description
----                          -------------                 --------                      -----------
Action Center                 Microsoft.ActionCenter        {System and Security}         Review recent messages and...
Administrative Tools          Microsoft.AdministrativeTools {System and Security}         Configure administrative s...
AutoPlay                      Microsoft.AutoPlay            {Hardware}                    Change default settings fo...
BitLocker Drive Encryption    Microsoft.BitLockerDriveEn... {System and Security}         Protect your computer usin...
Color Management              Microsoft.ColorManagement     {All Control Panel Items}     Change advanced color mana...
Credential Manager            Microsoft.CredentialManager   {User Accounts}               Manage your Windows Creden...
Date and Time                 Microsoft.DateAndTime         {Clock, Language, and Region} Set the date, time, and ti...
...
```

### 예 2: 이름별로 제어판 항목 가져오기

이 예제에서는 이름에 프로그램 또는 앱이 있는 제어판 항목을 가져옵니다.

```powershell
Get-ControlPanelItem -Name "*Program*", "*App*"
```

### 예제 3: 범주별로 제어판 항목 가져오기

이 명령은 범주에서 이름에 보안을 갖는 모든 제어판 항목을 가져옵니다.

```powershell
Get-ControlPanelItem -Category "*Security*"
```

### 예제 4: 제어판 항목 열기

이 예제에서는 로컬 컴퓨터에서 Windows 방화벽 제어판 항목을 엽니다.

```powershell
Get-ControlPanelItem -Name "Windows Firewall" | Show-ControlPanelItem
```

`Get-ControlPanelItem`Cmdlet은 제어판 항목을 가져옵니다. `Show-ControlPanelItem`Cmdlet에서 해당 파일을 엽니다.

### 예 5: 원격 컴퓨터에서 제어판 항목 가져오기

이 예제에서는 Server01 원격 컴퓨터의 BitLocker 드라이브 암호화 제어판 항목을 가져옵니다.
Cmdlet은이 `Invoke-Command` `Get-ControlPanelItem` cmdlet을 원격으로 실행 합니다.

```powershell
Invoke-Command -ComputerName "Server01" {Get-ControlPanelItem -Name "BitLocker*" }
```

### 예제 6: 제어판 항목의 설명 검색

이 예에서는 제어판 항목의 **Description** 속성을 검색 하 여 이름 **장치** 를 포함 하는 항목만 가져옵니다.

```powershell
Get-ControlPanelItem | Where-Object {$_.Description -like "*Device*"}
```

```Output
Name                    CanonicalName                 Category    Description
----                    -------------                 --------    -----------
AutoPlay                Microsoft.AutoPlay            {Hardware}  Change default settings fo...
Devices and Printers    Microsoft.DevicesAndPrinters  {Hardware}  View and manage devices, p...
Sound                   Microsoft.Sound               {Hardware}  Configure your audio devic...
```

`Get-ControlPanelItem`Cmdlet은 모든 제어판 항목을 가져옵니다. `Where-Object`Cmdlet은 **Description** 속성의 값을 기준으로 항목을 필터링 합니다.

## PARAMETERS

### -CanonicalName

이 cmdlet이 가져오는 정식 이름 또는 이름 패턴으로 제어판 항목을 문자열 배열로 지정 합니다. 와일드카드가 지원됩니다. 여러 이름을 입력 하는 경우이 cmdlet은 이름 목록의 항목이 "or" 연산자로 구분 되어 있는 것 처럼 모든 이름과 일치 하는 제어판 항목을 가져옵니다.

기본적으로이 cmdlet은 시스템의 모든 제어판 항목을 가져옵니다.

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

### -범주

이 cmdlet이 가져오는 지정 된 범주에 있는 제어판 항목의 범주를 문자열 배열로 지정 합니다. 범주 이름 또는 이름 패턴을 입력합니다. 와일드카드가 지원됩니다. 여러 이름을 입력 하는 경우이 cmdlet은 이름 목록의 항목이 "or" 연산자로 구분 되어 있는 것 처럼 모든 이름과 일치 하는 제어판 항목을 가져옵니다. 기본적으로이 cmdlet은 시스템의 모든 제어판 항목을 가져옵니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

이 cmdlet이 가져오는 컨트롤 패널의 이름 또는 이름 패턴을 문자열 배열로 지정 합니다.
와일드카드가 지원됩니다. 이름 또는 이름 패턴을이 cmdlet으로 파이프 할 수도 있습니다.

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

이름 또는 이름 패턴을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### Get-controlpanelitem.

이 cmdlet은 로컬 컴퓨터에 있는 제어판 항목을 가져옵니다.

## 참고

## 관련 링크

[Show-ControlPanelItem](Show-ControlPanelItem.md)

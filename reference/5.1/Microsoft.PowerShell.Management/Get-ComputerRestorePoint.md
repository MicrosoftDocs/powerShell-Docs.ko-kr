---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerrestorepoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerRestorePoint
ms.openlocfilehash: 73819aafee9ed1911354daf9af23eedff0a3e14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215481"
---
# Get-ComputerRestorePoint

## 개요
로컬 컴퓨터에 있는 복원 지점을 가져옵니다.

## SYNTAX

### ID (기본값)

```
Get-ComputerRestorePoint [[-RestorePoint] <Int32[]>] [<CommonParameters>]
```

### LastStatus

```
Get-ComputerRestorePoint -LastStatus [<CommonParameters>]
```

## 설명

`Get-ComputerRestorePoint`Cmdlet은 로컬 컴퓨터의 시스템 복원 위치를 가져옵니다. 또한 가장 최근의 컴퓨터 복원 시도 상태를 표시할 수 있습니다.

의 정보를 사용 하 여 `Get-ComputerRestorePoint` 복원 지점을 선택할 수 있습니다. 예를 들어 시퀀스 번호를 사용 하 여 cmdlet에 대 한 복원 지점을 식별 `Restore-Computer` 합니다.

시스템 복원 지점과 `Get-ComputerRestorePoint` cmdlet은 windows 10, windows 7, Windows Vista 및 WINDOWS XP와 같은 클라이언트 운영 체제 에서만 지원 됩니다.

## 예제

### 예제 1: 모든 시스템 복원 시점 가져오기

이 예에서는 `Get-ComputerRestorePoint` 로컬 컴퓨터의 시스템 복원 지점이 모두 가져옵니다.

```powershell
Get-ComputerRestorePoint
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
8/7/2019  12:56:45     Installed PowerShell 6-x64     6                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

### 예제 2: 특정 시퀀스 번호 가져오기

이 예에서는 특정 시퀀스 번호에 대 한 시스템 복원 지점이 있습니다.

```powershell
Get-ComputerRestorePoint -RestorePoint 4, 5
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

`Get-ComputerRestorePoint`**RestorePoint** 매개 변수를 사용 하 여 쉼표로 구분 된 시퀀스 번호 배열을 지정 합니다.

### 예 3: 시스템 복원 상태 표시

이 예에서는 로컬 컴퓨터의 가장 최근 시스템 복원 상태를 표시 합니다.

```powershell
Get-ComputerRestorePoint -LastStatus
```

```Output
The last attempt to restore the computer failed.
```

`Get-ComputerRestorePoint`**LastStatus** 매개 변수를 사용 하 여 최근 시스템 복원의 결과를 표시 합니다.

### 예제 4: 식를 사용 하 여 CreationTime 변환

`Get-ComputerRestorePoint`**CreationTime** 을 WMI (WMI(Windows Management Instrumentation)) 날짜 및 시간 문자열로 출력 합니다.

이 예에서는 변수가 **CreationTime** 문자열을 **DateTime** 개체로 변환 하는 식을 저장 합니다. 변환 하기 전에 **CreationTime** 문자열을 보려면과 같은 명령을 사용 `((Get-ComputerRestorePoint).CreationTime)` 합니다. WMI 날짜 및 시간 문자열에 대 한 자세한 내용은 [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime)를 참조 하세요.

```powershell
$date = @{Label="Date"; Expression={$_.ConvertToDateTime($_.CreationTime)}}
Get-ComputerRestorePoint | Select-Object -Property SequenceNumber, $date, Description
```

```Output
SequenceNumber   Date                 Description
--------------   ----                 -----------
             4   7/30/2019 09:17:24   Windows Update
             5   8/5/2019  08:15:37   Installed PowerShell 7-preview-x64
             6   8/7/2019  12:56:45   Installed PowerShell 6-x64
```

`$date`변수는 **ConvertToDateTime** 메서드를 사용 하는 식을 사용 하 여 해시 테이블을 저장 합니다. 식은 **CreationTime** 속성의 값을 WMI 문자열에서 **DateTime** 개체로 변환 합니다.

`Get-ComputerRestorePoint` 시스템 복원 지점 개체를 파이프라인으로 보냅니다. `Select-Object`**Property** 매개 변수를 사용 하 여 표시할 속성을 지정 합니다. 파이프라인의 각 개체에 대해의 식은 `$date` **CreationTime** 를 변환 하 고 **Date** 속성의 결과를 출력 합니다.

### 예 5: 속성을 사용 하 여 시퀀스 번호 가져오기

이 예에서는 **SequenceNumber** 속성 및 배열 인덱스를 사용 하 여 시퀀스 번호를 가져옵니다. 출력에는 시퀀스 번호만 포함 됩니다.

```powershell
((Get-ComputerRestorePoint).SequenceNumber)[-1]
```

```Output
6
```

`Get-ComputerRestorePoint` 배열 인덱스에 **SequenceNumber** 속성을 사용 합니다. 의 배열 인덱스는 `-1` 배열에서 가장 최근의 시퀀스 번호를 가져옵니다.

## PARAMETERS

### -LastStatus

에서 `Get-ComputerRestorePoint` 가장 최근의 시스템 복원 작업의 상태를 가져옵니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LastStatus
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestorePoint

시스템 복원 지점의 시퀀스 번호를 지정 합니다. 단일 시퀀스 번호 또는 쉼표로 구분 된 일련 번호 배열을 지정할 수 있습니다.

**RestorePoint** 매개 변수를 지정 하지 않으면는 `Get-ComputerRestorePoint` 로컬 컴퓨터의 시스템 복원 지점이 모두 반환 됩니다.

```yaml
Type: System.Int32[]
Parameter Sets: ID
Aliases:

Required: False
Position: 0
Default value: All restore points
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

파이프라인에서로 개체를 보낼 수 없습니다 `Get-ComputerRestorePoint` .

## 출력

### System.object # root\default\SystemRestore 또는 String

`Get-ComputerRestorePoint`WMI (WMI(Windows Management Instrumentation)) **SystemRestore** 클래스 인스턴스인 **SystemRestore** 개체를 반환 합니다.

**LastStatus** 매개 변수를 사용 하는 경우는 `Get-ComputerRestorePoint` 문자열을 반환 합니다.

## 참고

`Get-ComputerRestorePoint`Windows Vista 및 이후 버전의 windows에서 명령을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 엽니다.

`Get-ComputerRestorePoint` WMI **SystemRestore** 클래스를 사용 합니다.

## 관련 링크

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[about_Arrays](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Restart-Computer](Restart-Computer.md)

[Restore-Computer](Restore-Computer.md)

[SystemRestore](/windows/win32/sr/systemrestore)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 9314aaf7c444f9a1159b301135d4130737daa439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215553"
---
# Clear-RecycleBin

## 개요
휴지통의 내용을 지웁니다.

## SYNTAX

### 모두

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Clear-RecycleBin`Cmdlet은 컴퓨터 휴지통의 콘텐츠를 삭제 합니다. 이 작업은 Windows **빈 휴지통** 을 사용 하는 것과 같습니다.

## 예제

### 1: 모든 휴지통 지우기

이 예제에서는 모든 로컬 컴퓨터의 휴지통이 지워집니다.

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

`Clear-RecycleBin` 로컬 컴퓨터의 모든 휴지통을 지우도록 사용자에 게 확인 메시지를 표시 합니다.

### 2: 지정 된 휴지통 지우기

이 예제에서는 지정 된 드라이브 문자에 대 한 휴지통을 지웁니다.

```powershell
Clear-RecycleBin -DriveLetter C
```

`Clear-RecycleBin`**r** 매개 변수를 사용 하 여 **C** 볼륨의 휴지통을 지정 합니다. 사용자에 게 명령을 실행 하기 위한 확인 메시지가 표시 됩니다.

### 3: 확인 하지 않고 모든 휴지통 지우기

이 예에서는 로컬 컴퓨터의 휴지통을 지우도록 확인 하는 메시지를 표시 하지 않습니다.

```powershell
Clear-RecycleBin -Force
```

`Clear-RecycleBin` 는 **Force** 매개 변수를 사용 하 고 로컬 컴퓨터의 모든 휴지통을 지우도록 사용자에 게 확인 메시지를 표시 하지 않습니다.

대신을 `-Force` 로 바꿉니다 `-Confirm:$false` .

## PARAMETERS

### -R

단일 드라이브 문자 또는 드라이브 문자 배열에 대해 지울 휴지통을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

사용자에 게 휴지통 선택을 취소 하기 위한 확인 메시지가 표시 되지 않도록 지정 합니다.

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

### -Confirm

Cmdlet을 실행 하기 전에 사용자 확인 메시지를 표시 합니다. **Confirm** 매개 변수가 지정 되지 않은 경우에도 사용자에 게 확인 메시지를 표시 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Clear-RecycleBin` . Cmdlet이 실행 되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

### 없음

## 참고

## 관련 링크

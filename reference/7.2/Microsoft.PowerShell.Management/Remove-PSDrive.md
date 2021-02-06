---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: d20a348f3f5ba193eb85e0f9d0e2cc11ad083b47
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605235"
---
# Remove-PSDrive

## 개요
임시 PowerShell 드라이브를 삭제 하 고 매핑된 네트워크 드라이브의 연결을 끊습니다.

## SYNTAX

### 이름 (기본값)

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralName

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

Cmdlet은 `Remove-PSDrive` cmdlet을 사용 하 여 만든 임시 PowerShell 드라이브를 삭제 합니다 `New-PSDrive` .

Windows PowerShell 3.0부터는 `Remove-PSDrive` 의 매개 변수를 사용 하 여 만든 드라이브를 비롯 하 여 매핑된 네트워크 드라이브의 연결을 끊습니다 `Persist` `New-PSDrive` .

`Remove-PSDrive` Windows 실제 또는 논리적 드라이브를 삭제할 수 없습니다.

Windows PowerShell 3.0부터 외부 드라이브가 컴퓨터에 연결 된 경우 PowerShell에서 자동으로 새 드라이브를 나타내는 PSDrive를 파일 시스템에 추가 합니다.
PowerShell을 다시 시작할 필요는 없습니다.
마찬가지로 컴퓨터에서 외부 드라이브의 연결이 끊어지면 PowerShell에서 제거 된 드라이브를 나타내는 PSDrive를 자동으로 삭제 합니다.

## 예제

### 예 1: 파일 시스템 드라이브 제거

이 명령은 "smp"라는 임시 파일 시스템 드라이브를 제거합니다.

```powershell
Remove-PSDrive -Name smp
```

### 예 2: 매핑된 네트워크 드라이브 제거

이 명령은 `Remove-PSDrive` 를 사용 하 여 X: 및 S: 매핑된 네트워크 드라이브의 연결을 끊습니다.

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## PARAMETERS

### -Force

현재 PowerShell 드라이브를 제거 합니다.

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

### -LiteralName

드라이브의 이름을 지정합니다.

**LiteralName** 값은 입력한 대로 사용됩니다.
어떠한 문자도 와일드카드로 해석되지 않습니다.
이름에 이스케이프 문자가 포함된 경우 이름을 작은따옴표(')로 묶어야 합니다.
작은따옴표는 PowerShell이 어떤 문자도 이스케이프 시퀀스로 해석 하지 않도록 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

제거할 드라이브의 이름을 지정합니다.
드라이브 이름 뒤에 콜론(:)을 입력하지 마세요.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PSProvider

**Psprovider** 개체의 배열을 지정 합니다.
이 cmdlet은 지정 된 PowerShell 공급자와 연결 된 모든 드라이브를 제거 하 고 연결을 끊습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -범위

드라이브의 범위를 지정합니다.
이 매개 변수에 허용 되는 값은 전역, 로컬 및 스크립트 이거나 현재 범위를 기준으로 하는 숫자입니다. 범위는 0에서 범위 수 까지입니다. 현재 범위 번호는 0이 고 해당 부모는 1입니다.
자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

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

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.Management.Automation.PSDriveInfo

Cmdlet 등의 드라이브 개체를 cmdlet으로 파이프 할 수 있습니다 `Get-PSDrive` `Remove-PSDrive` .

## 출력

### 없음

이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

- `Remove-PSDrive`Cmdlet은 PowerShell 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다. 세션의 공급자를 나열 하려면 cmdlet을 사용 합니다 `Get-PSProvider` . 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Get-PSDrive](Get-PSDrive.md)

[New-PSDrive](New-PSDrive.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)


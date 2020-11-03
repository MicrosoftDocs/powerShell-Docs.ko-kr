---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 9ae9c0e7c17a6a63da5487cce138ddce129b975b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214546"
---
# Remove-ItemProperty

## 개요
항목에서 속성 및 해당 값을 삭제합니다.

## SYNTAX

### Path (기본값)

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## 설명

`Remove-ItemProperty`Cmdlet은 항목에서 속성 및 해당 값을 삭제 합니다.
이 cmdlet을 사용하여 레지스트리 값과 이 값에 저장된 데이터를 삭제할 수 있습니다.

## 예제

### 예제 1: 레지스트리 값 삭제

이 명령은 "HKEY_LOCAL_MACHINE\Software" 레지스트리 키의 "SmpApplication" 하위 키에서 "SmpProperty" 레지스트리 값과 해당 데이터를 삭제 합니다.

명령은 파일 시스템 드라이브 ()에서 실행 되기 때문에 `PS C:\>` 드라이브, `HKLM:` 및 "소프트웨어" 키를 포함 하 여 "SmpApplication" 하위 키의 정규화 된 경로를 포함 합니다.

**Name** 매개 변수를 사용 하 여 삭제할 레지스트리 값을 식별 합니다.

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

### 예 2: HKCU 위치에서 레지스트리 값 삭제

이러한 명령은 "HKEY_CURRENT_USER\Software\MyCompany"의 "MyApp" 하위 키에서 "Options" 레지스트리 값과 해당 데이터를 삭제 합니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Set-Location` 현재 위치를 **HKEY_CURRENT_USER** 드라이브 ( `HKCU:` ) 및 "Software\MyCompany\MyApp" 하위 키로 변경 합니다.

두 번째 명령은를 사용 하 여 " `Remove-ItemProperty` MyApp" 하위 키에서 "Options" 레지스트리 값과 해당 데이터를 제거 합니다.
**Path** 가 필요 하기 때문에 명령은 점 ('. ')을 사용 하 여 현재 위치를 표시 합니다.
**Name** 을 사용 하 여 삭제할 레지스트리 값을 지정 합니다.
**Confirm** 매개 변수를 사용 하 여 값을 삭제 하기 전에 사용자 프롬프트를 요청 합니다.

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

### 예제 3: 파이프라인을 사용 하 여 레지스트리 값 제거

이 명령은 "HKLM\Software\MyCompany" 레지스트리 키에서 "NoOfEmployees" 레지스트리 값과 해당 데이터를 삭제 합니다.

이 명령은 cmdlet을 사용 하 여 `Get-Item` 레지스트리 키를 나타내는 항목을 가져옵니다.
파이프라인 연산자 ()를 사용 하 여 `|` 개체를로 보냅니다 `Remove-ItemProperty` .
그런 다음의 **name** 매개 변수를 사용 하 여 `Remove-ItemProperty` 레지스트리 값의 이름을 지정 합니다.

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

## PARAMETERS

### -Credential

> [!NOTE]
> 이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.
> 이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -제외

이 cmdlet이 생략 하는 항목을 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.
경로 요소 또는 패턴(예: "*.txt")을 입력합니다.
와일드카드 문자를 사용할 수 있습니다.

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

### -Filter

공급자의 형식 또는 언어로 필터를 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.

와일드 카드 문자를 포함 한 필터 구문은 공급자에 따라 달라 집니다.
필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

Cmdlet이 다른 방법으로는 사용자가 액세스할 수 없는 개체의 속성을 강제로 제거 합니다.
구현은 공급자에 따라 다릅니다.
자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

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

### -포함

이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.
경로 요소 또는 패턴(예: "*.txt")을 입력합니다.
와일드카드 문자를 사용할 수 있습니다.

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

### -LiteralPath

속성의 현재 위치에 대한 경로를 지정합니다.
**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.
어떠한 문자도 와일드카드로 해석되지 않습니다.
이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.
작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

제거할 속성의 이름을 지정 합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Path

속성이 제거 되는 항목의 경로를 지정 합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -UseTransaction

활성 트랜잭션에 명령을 포함합니다.
이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.
자세한 내용은 about_Transactions를 참조하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
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

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

경로를 포함 하지만 리터럴 경로를 포함 하지 않는 문자열을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

PowerShell 레지스트리 공급자에서 레지스트리 값은 레지스트리 키 또는 하위 키의 속성으로 간주 됩니다. **Get-itemproperty** cmdlet을 사용 하 여 이러한 값을 관리할 수 있습니다.

`Remove-ItemProperty` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 About_Providers를 참조하세요.

## 관련 링크

[Get-Item](Get-Item.md)

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-Item](Remove-Item.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

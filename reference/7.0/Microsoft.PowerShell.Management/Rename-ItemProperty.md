---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-itemproperty?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-ItemProperty
ms.openlocfilehash: d9403a2572926101a7ccab8992013b60e4fb77f4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210865"
---
# Rename-ItemProperty

## 개요
항목의 속성 이름을 바꿉니다.

## SYNTAX

### Path (기본값)

```
Rename-ItemProperty [-Path] <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Rename-ItemProperty -LiteralPath <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Rename-ItemProperty`Cmdlet은 지정 된 항목 속성의 이름을 변경 합니다.
속성의 값은 변경되지 않습니다.
예를 들어를 사용 `Rename-ItemProperty` 하 여 레지스트리 항목의 이름을 변경할 수 있습니다.

## 예제

### 예제 1: 레지스트리 항목 이름 바꾸기

이 명령은 키에 포함 된 구성 레지스트리 항목의 이름을 `HKEY_LOCAL_MACHINE\Software\SmpApplication` "oldconfig"로 바꿉니다.

```powershell
Rename-ItemProperty -Path HKLM:\Software\SmpApplication -Name config -NewName oldconfig
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

이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다. 와일드카드 문자를 사용할 수 있습니다. **Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .

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

**Path** 매개 변수를 한정 하는 필터를 지정 합니다. [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다. [About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.
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

Cmdlet이 다른 방법으로는 사용자가 액세스할 수 없는 개체의 속성 이름을 강제로 바꿉니다.
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

이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다. 와일드카드 문자를 사용할 수 있습니다. **Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .

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

하나 이상의 위치에 대한 경로를 지정합니다. **LiteralPath** 의 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

이름을 바꿀 속성의 현재 이름을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NewName

속성의 새 이름을 지정합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

항목 속성을 나타내는 개체를 반환 합니다.
기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -Path

이름을 바꿀 항목의 경로를 지정 합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
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

### None, PSCustomObject

이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 이름이 바뀐 항목 속성을 나타내는 **PSCustomObject** 를 생성 합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

`Remove-ItemProperty` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-Item](Rename-Item.md)

[Set-ItemProperty](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

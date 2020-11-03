---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Item
ms.openlocfilehash: 6a6bffbdbf0b619b4ac07391a4b4be368c932777
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212297"
---
# Set-Item

## 개요
항목의 값을 명령에 지정된 값으로 변경합니다.

## SYNTAX

### Path (기본값)

```
Set-Item [-Path] <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Set-Item -LiteralPath <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Set-Item`Cmdlet은 변수 또는 레지스트리 키와 같은 항목의 값을 명령에 지정 된 값으로 변경 합니다.

## 예제

### 예제 1: 별칭 만들기

이 명령은 Notepad의 np 별칭을 만듭니다.

```powershell
Set-Item -Path alias:np -Value "c:\windows\notepad.exe"
```

### 예제 2: 환경 변수 값 변경

이 명령은 UserRole 환경 변수의 값을 Administrator로 변경 합니다.

```powershell
Set-Item -Path env:UserRole -Value "Administrator"
```

### 예제 3: prompt 함수 수정

이 명령은 경로 앞에 시간을 표시 하도록 prompt 함수를 변경 합니다.

```powershell
Set-Item -Path function:prompt -Value {'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '}
```

### 예제 4: 프롬프트 함수에 대 한 옵션 설정

이 명령은 prompt 함수에 대 한 **AllScope** 및 **ReadOnly** 옵션을 설정 합니다.
이 명령은의 **Options** 동적 매개 변수를 사용 `Set-Item` 합니다.
**옵션** 매개 변수는 `Set-Item` **별칭** 또는 **함수** 공급자와 함께 사용 하는 경우에만 사용할 수 있습니다.

```powershell
Set-Item -Path function:prompt -Options "AllScope,ReadOnly"
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

Cmdlet이 읽기 전용 별칭 또는 변수와 같이 다른 방법으로는 변경할 수 없는 항목을 강제로 설정 합니다. 이 cmdlet은 지속적인 별칭 또는 변수를 변경할 수 없습니다.
구현은 공급자에 따라 다릅니다.
자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.
*Force* 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.

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
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

항목을 나타내는 개체를 파이프라인으로 전달 합니다.
기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -Path

항목 위치의 경로를 지정 합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Value

항목의 새 값을 지정합니다.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### System.Object

항목의 새 값을 나타내는 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음 또는 새 항목 또는 변경 된 항목을 나타내는 개체입니다.

이 cmdlet은 *PassThru* 매개 변수를 지정 하는 경우 항목을 나타내는 개체를 생성 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

- `Set-Item` 은 (는) PowerShell FileSystem 공급자에서 지원 되지 않습니다. 파일 시스템에 있는 항목의 값을 변경 하려면 cmdlet을 사용 `Set-Content` 합니다.
- 및 레지스트리 드라이브에서 `HKLM:` `HKCU:` `Set-Item` 레지스트리 키의 (기본값) 값에 있는 데이터를 변경 합니다.
  - 레지스트리 키의 이름을 만들고 변경 하려면 `New-Item` 및 cmdlet을 사용 `Rename-Item` 합니다.
  - 레지스트리 값의 이름과 데이터를 변경 하려면 `New-ItemProperty` , 및 cmdlet을 사용 `Set-ItemProperty` `Rename-ItemProperty` 합니다.
- `Set-Item` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.
  세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다.
  자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

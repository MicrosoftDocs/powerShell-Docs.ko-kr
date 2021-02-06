---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Item
ms.openlocfilehash: fb3f95f51578f9dc02d9f68b3c0be5a6531aca17
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603255"
---
# Clear-Item

## 개요
항목의 내용을 지우면 항목을 삭제 하지 않습니다.

## SYNTAX

### Path (기본값)

```
Clear-Item [-Path] <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Clear-Item -LiteralPath <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Clear-Item`Cmdlet은 항목의 내용을 지우고 항목은 삭제 하지 않습니다.
예를 들어 `Clear-Item` cmdlet은 변수의 값을 삭제할 수 있지만 변수를 삭제 하지는 않습니다. 지워진 항목을 나타내는 데 사용 되는 값은 각 PowerShell 공급자에 의해 정의 됩니다.
이 cmdlet은와 유사 `Clear-Content` 하지만 파일 대신 별칭 및 변수에서 작동 합니다.

## 예제

### 예제 1: 변수 값 지우기

이 명령은 이라는 변수의 값을 지웁니다 `TestVar1` .
변수는 그대로 유지 되지만 유효 하지만 해당 값은로 설정 됩니다 `$null` .
변수 이름에는 `Variable:` PowerShell 변수 공급자를 나타내는 접두사가 붙습니다.

대체 명령은 동일한 결과를 얻기 위해 PowerShell 드라이브로 전환 하 `Variable:` 고 명령을 실행할 수 있음을 보여 줍니다 `Clear-Item` .

```powershell
Clear-Item Variable:TestVar1
```

```
Set-Location Variable:
PS Variable:\> Clear-Item TestVar1
```

### 예제 2: 모든 레지스트리 항목 지우기

이 명령은 "MyKey" 하위 키의 모든 레지스트리 항목을 지웁니다. 단, 사용자의 의도를 확인 하 라는 메시지가 표시 된 후에만 표시 됩니다.
"MyKey" 하위 키를 삭제 하거나 다른 레지스트리 키 또는 항목에 영향을 주지 않습니다.
**Include** 및 **Exclude** 매개 변수를 사용하여 특정 레지스트리 키(레지스트리 항목은 해당되지 않음)를 식별할 수 있습니다.

- 특정 레지스트리 항목을 삭제 하려면 cmdlet을 사용 `Remove-ItemProperty` 합니다.
- 레지스트리 항목의 값을 삭제 하려면를 사용 `Clear-ItemProperty cmdlet` 합니다.

```powershell
Clear-Item HKLM:\Software\MyCompany\MyKey -Confirm
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

Cmdlet이 다른 방법으로는 변경할 수 없는 항목 (예: 읽기 전용 별칭)을 지우도록 지정 합니다.
그러나 상수는 지울 수 없습니다.
구현은 공급자에 따라 다릅니다.
자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.
**Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.

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

### -Path

지울 항목의 경로를 지정합니다.
와일드카드 문자를 사용할 수 있습니다.
이 매개 변수는 필수 이지만 매개 변수 이름 **경로** 는 선택 사항입니다.

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

이 cmdlet에 경로 문자열을 파이프 하 여 지정할 수 있습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

- `Clear-Item`Cmdlet은 **별칭**, **환경**, **함수**, **레지스트리** 및 **변수** 공급자를 비롯 한 여러 PowerShell 공급자만 지원 합니다. 따라서를 사용 `Clear-Item` 하 여 공급자 네임 스페이스에 있는 항목의 내용을 삭제할 수 있습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.
- `Clear-Item`PowerShell FileSystem 공급자가이 cmdlet을 지원 하지 않으므로를 사용 하 여 파일의 내용을 삭제할 수는 없습니다. 파일을 지우려면를 사용 `Clear-Content` 합니다.

## 관련 링크

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)


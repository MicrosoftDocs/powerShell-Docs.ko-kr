---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: 2569f4778f54f6cdad22e10cf92e727b73c323e3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214610"
---
# New-ItemProperty

## 개요
항목의 새 속성을 만들고 해당 값을 설정합니다.

## SYNTAX

### Path (기본값)

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## 설명

`New-ItemProperty`Cmdlet은 지정 된 항목에 대 한 새 속성을 만들고 해당 값을 설정 합니다.
레지스트리 값은 레지스트리 키 항목의 속성이기 때문에 일반적으로 이 cmdlet은 새 레지스트리 값을 만드는 데 사용됩니다.

이 cmdlet은 개체에 속성을 추가하지는 않습니다.

- 개체의 인스턴스에 속성을 추가 하려면 cmdlet을 사용 `Add-Member` 합니다.
- 특정 유형의 모든 개체에 속성을 추가 하려면 Types.ps1xml 파일을 수정 합니다.

## 예제

### 예제 1: 레지스트리 항목 추가

이 명령은 새 레지스트리 항목인 "NoOfEmployees"를 "HKLM: \ Software hive"의 "MyCompany" 키에 추가 합니다.

첫 번째 명령은 **path** 매개 변수를 사용 하 여 "MyCompany" 레지스트리 키의 경로를 지정 합니다.
**Name** 매개 변수를 사용 하 여 항목의 이름을 지정 하 고 **value** 매개 변수를 사용 하 여 해당 값을 지정 합니다.

두 번째 명령은 cmdlet을 사용 하 여 `Get-ItemProperty` 새 레지스트리 항목을 확인 합니다.

```powershell
New-ItemProperty -Path "HKLM:\Software\MyCompany" -Name "NoOfEmployees" -Value 822
Get-ItemProperty "HKLM:\Software\MyCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\mycompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : mycompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 822
```

### 예제 2: 레지스트리 항목을 키에 추가

이 명령은 새 레지스트리 항목을 레지스트리 키에 추가합니다. 키를 지정 하기 위해 파이프라인 연산자 (|)를 사용 하 여 키를 나타내는 개체를로 보냅니다 `New-ItemProperty` .

명령의 첫 번째 부분에서는 cmdlet을 사용 하 여 `Get-Item` "MyCompany" 레지스트리 키를 가져옵니다. 파이프라인 연산자는 명령 결과를에 보냅니다 .이 명령은 `New-ItemProperty` 새 레지스트리 항목 ("NoOfLocations") 및 해당 값 (3)을 "MyCompany" 키에 추가 합니다.

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

이 명령은 Windows PowerShell의 매개 변수 바인딩 기능이 `RegistryKey` `Get-Item` 의 **LiteralPath** 매개 변수와 함께 반환 되는 개체의 경로를 연결 하기 때문에 작동 합니다 `New-ItemProperty` . 자세한 내용은 [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md)를 참조 하세요.

### 예제 3: Here-String을 사용 하 여 레지스트리에 다중 문자열 값 만들기

이 예제에서는 다음 문자열을 사용 하 여 다중 문자열 값을 만듭니다.

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'HereString' -PropertyType MultiString -Value @"
This is text which contains newlines
It can also contain "quoted" strings
"@
$newValue.multistring
```

```output
This is text which contains newlines
It can also contain "quoted" strings
```

### 예제 4: 배열을 사용 하 여 레지스트리에 다중 문자열 값 만들기

예제에서는 값 배열을 사용 하 여 값을 만드는 방법을 보여 줍니다 `MultiString` .

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
```

## PARAMETERS

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.
기본값은 현재 사용자입니다.

"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

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

이 cmdlet이 작업에서 제외 하는 속성 또는 속성을 문자열 배열로 지정 합니다.
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
Accept wildcard characters: False
```

### -Filter

공급자의 형식 또는 언어로 필터를 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.

와일드 카드 문자를 포함 한 필터 구문은 공급자에 따라 달라 집니다. 필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Cmdlet이 다른 방법으로는 사용자가 액세스할 수 없는 개체에 대 한 속성을 강제로 만들도록 합니다.
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
Accept wildcard characters: False
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

새 속성의 이름을 지정합니다.
속성이 레지스트리 항목인 경우 이 매개 변수는 항목의 이름을 지정합니다.

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

### -Path

항목의 경로를 지정 합니다.
이 매개 변수는이 cmdlet이 새 속성을 추가 하는 항목을 식별 합니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PropertyType

이 cmdlet이 추가 하는 속성의 유형을 지정 합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- **String** : null로 끝나는 문자열을 지정 합니다. **REG_SZ** 와 동일 합니다.
- **ExpandString** : 값을 검색할 때 확장 되는 환경 변수에 대 한 확장 되지 않은 참조를 포함 하는 null로 끝나는 문자열을 지정 합니다. **REG_EXPAND_SZ** 와 동일 합니다.
- **Binary** : 임의의 형식으로 된 이진 데이터를 지정 합니다. **REG_BINARY** 와 동일 합니다.
- **DWord** : 32 비트 이진수를 지정 합니다. **REG_DWORD** 와 동일 합니다.
- **다중 문자열** : 두 null 문자로 끝나는 null로 끝나는 문자열의 배열을 지정 합니다.
  **REG_MULTI_SZ** 와 동일 합니다.
- **Qword(64** : 64 비트 이진수를 지정 합니다. **REG_QWORD** 와 동일 합니다.
- **Unknown** : **REG_RESOURCE_LIST** 와 같은 지원 되지 않는 레지스트리 데이터 형식을 나타냅니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
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

### -Value

속성 값을 지정합니다.
속성이 레지스트리 항목인 경우 이 매개 변수는 항목의 이름을 지정합니다.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### PSCustomObject.

`New-ItemProperty` 새 속성을 포함 하는 사용자 지정 개체를 반환 합니다.

## 참고

`New-ItemProperty` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

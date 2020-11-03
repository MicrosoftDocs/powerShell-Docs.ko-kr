---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: 969cb181758dc1ac40b9d8fca2c22fa97f87c693
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214457"
---
# Set-ItemProperty

## 개요
항목의 속성 값을 만들거나 변경합니다.

## SYNTAX

### propertyValuePathSet (기본값)

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### propertyPSObjectPathSet

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### propertyValueLiteralPathSet

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### propertyPSObjectLiteralPathSet

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## 설명

`Set-ItemProperty`Cmdlet은 지정 된 항목의 속성 값을 변경 합니다. 이 cmdlet을 사용하여 항목 속성을 설정하거나 변경할 수 있습니다. 예를 들어를 사용 `Set-ItemProperty` 하 여 파일 개체의 **IsReadOnly** 속성 값을로 설정할 수 있습니다 `$True` .

또한를 사용 `Set-ItemProperty` 하 여 레지스트리 값과 데이터를 만들고 변경할 수 있습니다.
예를 들어 새 레지스트리 항목을 키에 추가하고 해당 값을 구성하거나 변경할 수 있습니다.

## 예제

### 예제 1: 파일의 속성 설정

이 명령은 "final.doc" 파일의 **IsReadOnly** 속성 값을 "true"로 설정 합니다. **경로** 를 사용 하 여 파일을 지정 하 고, **이름을** 지정 하 여 속성의 이름을 지정 하 고, pazrameter **값** 을 사용 하 여 새 값을 지정 합니다.

이 파일은 IsReadOnly **개체이** 고, 해당 속성 중 **IsReadOnly** 하나일 뿐입니다.
모든 속성을 보려면를 입력 `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType Property` 합니다.

`$true`자동 변수는 "TRUE" 값을 나타냅니다.
자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### 예제 2: 레지스트리 항목 및 값 만들기

이 예제에서는를 사용 하 여 `Set-ItemProperty` 새 레지스트리 항목을 만들고 항목에 값을 할당 하는 방법을 보여 줍니다. "HKLM\Software" 키의 "ContosoCompany" 키에 "NoOfEmployees" 항목을 만들고 해당 값을 823로 설정 합니다.

레지스트리 항목은 레지스트리 키 (항목)의 속성으로 간주 되기 때문에를 사용 하 여 `Set-ItemProperty` 레지스트리 항목을 만들고 해당 값을 설정 및 변경할 수 있습니다.

첫 번째 명령은 레지스트리 항목을 만듭니다.
**경로** 를 사용 하 여 드라이브의 경로를 지정 하 `HKLM:` 고 "software\mycompany" 키를 지정 합니다.
이 명령은 **name** 을 사용 하 여 항목 이름 및 **값** 을 지정 하 고 값을 지정 합니다.

두 번째 명령은 cmdlet을 사용 하 여 `Get-ItemProperty` 새 레지스트리 항목을 확인 합니다. 또는 cmdlet을 사용 하는 경우 항목 `Get-Item` `Get-ChildItem` 은 항목이 나 자식 항목이 아닌 키의 속성 이므로 표시 되지 않습니다.

세 번째 명령은 **Noofemployees** 항목의 값을 824로 변경 합니다.

Cmdlet을 사용 하 여 `New-ItemProperty` 레지스트리 항목 및 해당 값을 만든 다음를 사용 하 여 `Set-ItemProperty` 값을 변경할 수도 있습니다.

드라이브에 대 한 자세한 내용을 보려면 `HKLM:` 를 입력 하십시오 `Get-Help Get-PSDrive` .
PowerShell을 사용 하 여 레지스트리를 관리 하는 방법에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help Registry` .

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 823

```

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 824
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

### 예제 3: 파이프라인을 사용 하 여 항목 수정

이러한 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 항목을로 보내는 방법을 보여 줍니다 `Set-ItemProperty` .

명령의 첫 번째 부분에서는를 사용 `Get-ChildItem` 하 여 "Weekly.txt" 파일을 나타내는 개체를 가져옵니다.
이 명령은 파이프라인 연산자를 사용 하 여 파일 개체를로 보냅니다 `Set-ItemProperty` .
이 `Set-ItemProperty` 명령은 **Name** 및 **value** 매개 변수를 사용 하 여 속성 및 속성의 새 값을 지정 합니다.

이 명령은 **InputObject** 매개 변수를 사용 하 여를 가져오는 개체를 지정 하는 것과 같습니다 `Get-ChildItem` .

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
```

## PARAMETERS

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.
기본값은 현재 사용자입니다.

"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .
사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

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

Cmdlet이 작동 하지 않는 항목을 지정 하 고 다른 모든 항목을 포함 합니다.
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

Cmdlet이 다른 방법으로는 사용자가 액세스할 수 없는 항목에 대 한 속성을 설정 하도록 합니다.
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

다른 모든 항목을 제외 하는 cmdlet이 작동 하는 항목만 지정 합니다.
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

### -InputObject

이 cmdlet이 변경 하는 속성을 가진 개체를 지정 합니다.
개체가 포함된 변수 또는 개체를 가져오는 명령을 입력하세요.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: propertyPSObjectPathSet, propertyPSObjectLiteralPathSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

항목 속성의 경로를 지정 합니다.
**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.
어떠한 문자도 와일드카드로 해석되지 않습니다.
이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.
작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: propertyValueLiteralPathSet, propertyPSObjectLiteralPathSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

속성의 이름을 지정합니다.

```yaml
Type: System.String
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases: PSProperty

Required: True
Position: 1
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

수정할 속성이 포함 된 항목의 경로를 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Type

**Type** 은 레지스트리 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Set-ItemProperty` .
이 매개 변수는 레지스트리 드라이브 에서만 작동 합니다.

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
Type: RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseTransaction

활성 트랜잭션에 명령을 포함합니다.
이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.
자세한 내용은 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)를 참조하세요.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

속성의 값을 지정합니다.

```yaml
Type: Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: SwitchParameter
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
Type: SwitchParameter
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

### System.web. PSObject

개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### None, PSCustomObject

이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 변경 된 항목 및 새 속성 값을 나타내는 **PSCustomObject** 개체를 생성 합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

`Set-ItemProperty` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-TypeData
ms.openlocfilehash: 1314d388bff5a46bcf335f3da7908a65233aa46e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600837"
---
# Update-TypeData

## 개요
세션에 있는 확장 유형 데이터를 업데이트합니다.

## Syntax

### FileSet (기본값)

```
Update-TypeData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DynamicTypeSet

```
Update-TypeData [-MemberType <PSMemberTypes>] [-MemberName <String>] [-Value <Object>]
 [-SecondValue <Object>] [-TypeConverter <Type>] [-TypeAdapter <Type>]
 [-SerializationMethod <String>] [-TargetTypeForDeserialization <Type>]
 [-SerializationDepth <Int32>] [-DefaultDisplayProperty <String>]
 [-InheritPropertySerializationSet <Nullable`1>] [-StringSerializationSource <String>]
 [-DefaultDisplayPropertySet <String[]>] [-DefaultKeyPropertySet <String[]>]
 [-PropertySerializationSet <String[]>] -TypeName <String> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### TypeDataSet

```
Update-TypeData [-Force] [-TypeData] <TypeData[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Update-TypeData`Cmdlet은 `Types.ps1xml` 파일을 메모리로 다시 로드 하 고 새 확장 유형 데이터를 추가 하 여 세션에서 확장 유형 데이터를 업데이트 합니다.

기본적으로 PowerShell은 필요에 따라 확장 유형 데이터를 로드 합니다. 매개 변수가 없으면는 `Update-TypeData` `Types.ps1xml` 추가한 형식 파일을 포함 하 여 세션에 로드 된 모든 파일을 다시 로드 합니다. 의 매개 변수를 사용 `Update-TypeData` 하 여 새 형식 파일을 추가 하 고 확장 형식 데이터를 추가 하 고 바꿀 수 있습니다.

`Update-TypeData`Cmdlet을 사용 하 여 모든 형식 데이터를 미리 로드할 수 있습니다. 이 기능은 유형을 개발하는 도중에 테스트를 위해 이러한 새 유형을 로드하려는 경우에 특히 유용합니다.

Windows PowerShell 3.0부터를 사용 하 여 `Update-TypeData` 파일을 사용 하지 않고 세션에서 확장 유형 데이터를 추가 하 고 바꿀 수 있습니다 `Types.ps1xml` . 파일 없이 동적으로 추가된 유형 데이터는 현재 세션에만 추가됩니다. 모든 세션에 형식 데이터를 추가 하려면 `Update-TypeData` PowerShell 프로필에 명령을 추가 합니다. 자세한 내용은 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)를 참조 하세요.

또한 Windows PowerShell 3.0부터 cmdlet을 사용 하 여 `Get-TypeData` 현재 세션에서 확장 유형을 가져오고 cmdlet을 사용 하 여 `Remove-TypeData` 현재 세션에서 확장 유형을 삭제할 수 있습니다.

속성에서 발생 하거나 명령에 속성을 추가할 때 발생 하는 예외는 `Update-TypeData` 오류를 보고 하지 않습니다. 이는 형식 지정 및 출력 중 많은 일반 유형에서 발생하는 예외를 표시하지 않기 위한 것입니다. .NET 속성을 가져오는 경우 다음 예제와 같이 메서드 구문을 대신 사용 하 여 예외를 제거 하는 문제를 해결할 수 있습니다.

`"hello".get_Length()`

메서드 구문은 .NET 속성에만 사용할 수 있습니다. Cmdlet을 실행 하 여 추가 된 속성은 `Update-TypeData` 메서드 구문을 사용할 수 없습니다.

PowerShell의 파일에 대 한 자세한 내용은 `Types.ps1xml` [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)을 참조 하세요.

## 예

### 예제 1: 확장 형식 업데이트

```powershell
Update-TypeData
```

이 명령은 `Types.ps1xml` 세션에 이미 사용 된 파일에서 확장 유형 구성을 업데이트 합니다.

### 예제 2: 여러 번 형식 업데이트

이 예제에서는 동일한 세션에서 유형 파일의 유형을 여러 번 업데이트 하는 방법을 보여 줍니다.

첫 번째 명령은 파일에서 확장 유형 구성을 업데이트 하 `Types.ps1xml` `TypesA.types.ps1xml` 고 먼저 및 파일을 처리 합니다 `TypesB.types.ps1xml` .

두 번째 명령은를 다시 업데이트 하는 방법을 보여 줍니다 `TypesA.types.ps1xml` . 예를 들어 파일에서 형식을 추가 하거나 변경 하는 경우를 들 수 있습니다. `TypesA.types.ps1xml` `Update-TypeData` `TypesA.types.ps1xml` 현재 세션에 대 한 형식 파일 목록에가 이미 있으므로 파일에 대해 이전 명령을 반복 하거나 매개 변수 없이 명령을 실행할 수 있습니다.

```powershell
Update-TypeData -PrependPath TypesA.types.ps1xml, TypesB.types.ps1xml
Update-TypeData -PrependPath TypesA.types.ps1xml
```

### 예제 3: DateTime 개체에 스크립트 속성 추가

이 예에서는 `Update-TypeData` 를 사용 하 여 cmdlet에서 반환 된 것과 같은 현재 세션의 **DateTime** 개체에 **Quarter** 스크립트 속성을 추가 합니다. `Get-Date`

```powershell
Update-TypeData -TypeName "System.DateTime" -MemberType ScriptProperty -MemberName "Quarter" -Value {
  if ($this.Month -in @(1,2,3)) {"Q1"}
  elseif ($this.Month -in @(4,5,6)) {"Q2"}
  elseif ($this.Month -in @(7,8,9)) {"Q3"}
  else {"Q4"}
}
(Get-Date).Quarter
```

```Output
Q1
```

`Update-TypeData` **TypeName** 매개 변수를 사용 하 여 system.string 형식을 지정 하 고, **MemberName** 매개 변수를 사용 하 여 새 속성의 이름을 지정 하 고, **MemberType** 속성을 사용 하 여 **scriptproperty** 유형을 지정 하 고, **Value** 매개 변수를 사용 하 여 연간 사분기를 결정 하는 스크립트를 지정 **합니다.**

**Value** 속성 값은 현재 연간 분기를 계산하는 스크립트입니다. 스크립트 블록은 자동 변수를 사용 하 여 `$this` 개체의 현재 인스턴스를 나타내고 In 연산자를 사용 하 여 월 값이 각 정수 배열에 표시 되는지 여부를 확인 합니다. 연산자에 대 한 자세한 내용은 `-in` [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md)를 참조 하세요.

두 번째 명령은 현재 날짜의 새 Quarter 속성을 가져옵니다.

### 예제 4: 기본적으로 목록에 표시 되는 형식 업데이트

이 예제에서는 기본적으로 (즉, 속성이 지정 되지 않은 경우) 목록에 표시 되는 형식의 속성을 설정 하는 방법을 보여 줍니다. 형식 데이터는 파일에 지정 되지 않기 때문에 `Types.ps1xml` 현재 세션 에서만 적용 됩니다.

```powershell
Update-TypeData -TypeName "System.DateTime" -DefaultDisplayPropertySet "DateTime, DayOfYear, Quarter"
Get-Date | Format-List
```

```Output
Thursday, March 15, 2012 12:00:00 AM
DayOfYear : 75
Quarter   : Q1
```

첫 번째 명령은 cmdlet을 사용 하 여 `Update-TypeData` **DateTime** 형식의 기본 목록 속성을 설정 합니다. **TypeName** 매개 변수를 사용하여 유형을 지정하고 **DefaultDisplayPropertySet** 매개 변수를 사용하여 목록의 기본 속성을 지정합니다. 선택한 속성에는 이전 예제에서 추가한 새 **Quarter** 스크립트 속성이 포함 됩니다.

두 번째 명령은 cmdlet을 사용 하 여 `Get-Date` 현재 날짜를 나타내는 **시스템 DateTime** 개체를 가져옵니다. 이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` **DateTime** 개체를 cmdlet으로 보냅니다 `Format-List` . `Format-List`이 명령은 목록에 표시할 속성을 지정 하지 않으므로 PowerShell은 명령에 의해 설정 된 기본값을 사용 합니다 `Update-TypeData` .

### 예 5: 파이프 된 개체에 대 한 형식 데이터 업데이트

```powershell
Get-Module | Update-TypeData -MemberType ScriptProperty -MemberName "SupportsUpdatableHelp" -Value {
  if ($this.HelpInfoUri) {$True} else {$False}
}
Get-Module -ListAvailable | Format-Table Name, SupportsUpdatableHelp
```

```Output
Name                             SupportsUpdatableHelp
----                             ---------------------
Microsoft.PowerShell.Diagnostics                  True
Microsoft.PowerShell.Host                         True
Microsoft.PowerShell.Management                   True
Microsoft.PowerShell.Security                     True
Microsoft.PowerShell.Utility                      True
Microsoft.WSMan.Management                        True
PSDiagnostics                                    False
PSScheduledJob                                    True
PSWorkflow                                        True
ServerManager                                     True
TroubleshootingPack                              False
```

이 예제에서는 개체를로 파이프 하는 경우 `Update-TypeData` `Update-TypeData` 개체 형식에 대 한 확장 형식 데이터를 추가 하는 방법을 보여 줍니다.

이 기법은 cmdlet 또는 메서드를 사용 하 여 `Get-Member` `Get-Type` 개체 형식을 가져오는 것 보다 빠릅니다. 그러나 개체의 컬렉션을로 파이프 하면 `Update-TypeData` 첫 번째 개체 형식의 형식 데이터가 업데이트 된 다음 해당 멤버가 형식에 이미 정의 되어 있기 때문에 컬렉션의 다른 모든 개체에 대해 오류가 반환 됩니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Module` PSScheduledJob 모듈을 가져옵니다. 명령을 사용 하 여 모듈 개체를 cmdlet으로 파이프 합니다. `Update-TypeData` 이 cmdlet은  `Get-Module` **ListAvailable** 매개 변수를 사용 하는 경우 반환 되는 moduleinfogrouping 유형과 같이 여기에서 파생 된 형식 및 해당 형식에 대 한 형식 데이터를 업데이트 합니다.

`Update-TypeData`명령은 가져온 모든 모듈에 **SupportsUpdatableHelp** script 속성을 추가 합니다. **Value** 매개 변수 값은 `$True` 모듈의 **HelpInfoUri** 속성이 채워져 있는 경우를 반환 하 고 그렇지 않으면를 반환 하는 스크립트입니다 `$False` .

두 번째 명령은 모듈 개체를에서 cmdlet으로 파이프 합니다 `Get-Module` `Format-Table` . 그러면이 cmdlet이 목록에 있는 모든 모듈의 **Name** 및 **SupportsUpdatableHelp** 속성을 표시 합니다.

## 매개 변수

### -AppendPath

선택적 파일의 경로를 지정 합니다 `.ps1xml` . 지정한 파일은 기본 제공 파일이 로드된 후 나열된 순서대로 로드됩니다. **Appendpath** 값을로 파이프 할 수도 있습니다 `Update-TypeData` .

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -DefaultDisplayProperty

`Format-Wide`다른 속성이 지정 되지 않은 경우 cmdlet에 의해 표시 되는 형식의 속성을 지정 합니다.

유형의 표준 또는 확장 속성 이름을 입력합니다. 이 매개 변수 값은 동일한 명령에서 추가된 유형의 이름일 수 있습니다.

이 값은 파일의 형식에 대해 정의 된 와이드 뷰가 없는 경우에만 적용 됩니다 `Format.ps1xml` .

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultDisplayPropertySet

유형의 속성을 하나 이상 지정합니다. 이러한 속성은 `Format-List` 다른 속성이 지정 되지 않은 경우 cmdlet에 의해 표시 됩니다.

유형의 표준 또는 확장 속성 이름을 입력합니다. 이 매개 변수 값은 동일한 명령에서 추가된 유형의 이름일 수 있습니다.

이 값은 파일의 형식에 대해 정의 된 목록 뷰가 없는 경우에만 적용 됩니다 `Format.ps1xml` .

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultKeyPropertySet

유형의 속성을 하나 이상 지정합니다. 이러한 속성은 `Group-Object` `Sort-Object` 다른 속성이 지정 되지 않은 경우 및 cmdlet에서 사용 됩니다.

유형의 표준 또는 확장 속성 이름을 입력합니다. 이 매개 변수 값은 동일한 명령에서 추가된 유형의 이름일 수 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

해당 형식에 대해 형식 데이터가 이미 지정 된 경우에도 cmdlet에서 지정 된 형식 데이터를 사용 함을 나타냅니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DynamicTypeSet, TypeDataSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InheritPropertySerializationSet

Serialize 된 속성 집합이 상속 되는지 여부를 나타냅니다. 기본값은 `$Null`입니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- `$True`. 속성 집합이 상속됩니다.
- `$False`. 속성 집합이 상속되지 않습니다.
- `$Null`. 상속이 정의되지 않습니다.

이 매개 변수는 **SerializationMethod** 매개 변수의 값이 인 경우에만 유효 `SpecificProperties` 합니다. 이 매개 변수 값이 이면 `$False` **PropertySerializationSet** 매개 변수가 필요 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Nullable`1[System.Boolean]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MemberName

속성 또는 메서드의 이름을 지정합니다.

**TypeName**, **MemberType**, **Value** 및 **SecondValue** 매개 변수와 함께 이 매개 변수를 사용하여 유형의 속성 또는 메서드를 추가하거나 변경할 수 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MemberType

추가하거나 변경할 멤버의 유형을 지정합니다.

**TypeName**, **MemberType**, **Value** 및 **SecondValue** 매개 변수와 함께 이 매개 변수를 사용하여 유형의 속성 또는 메서드를 추가하거나 변경할 수 있습니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- AliasProperty
- CodeMethod
- CodeProperty
- Noteproperty
- ScriptMethod
- ScriptProperty

이러한 값에 대 한 자세한 내용은 [PSMemberTypes 열거형](/dotnet/api/system.management.automation.psmembertypes)을 참조 하세요.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: DynamicTypeSet
Aliases:
Accepted values: NoteProperty, AliasProperty, ScriptProperty, CodeProperty, ScriptMethod, CodeMethod

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PrependPath

선택적 파일의 경로를 지정 합니다 `.ps1xml` . 지정한 파일은 기본 제공 파일이 로드되기 전에 나열된 순서대로 로드됩니다.

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PropertySerializationSet

직렬화된 속성의 이름을 지정합니다. **SerializationMethod** 매개 변수 값이 **SpecificProperties** 인 경우 이 매개 변수를 사용합니다.

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecondValue

**AliasProperty**, **ScriptProperty**, **CodeProperty** 또는 **CodeMethod** 멤버에 대한 추가 값을 지정합니다.

이 매개 변수를 **TypeName**, **MemberType**, **Value** 및 **SecondValue** 매개 변수와 함께 사용 하 여 형식의 속성이 나 메서드를 추가 하거나 변경할 수 있습니다.

**MemberType** 매개 변수의 값이 인 경우 `AliasProperty` **SecondValue** 매개 변수 값은 데이터 형식 이어야 합니다. PowerShell은 alias 속성의 값을 지정 된 형식으로 변환 (즉, 캐스팅) 합니다. 예를 들어 문자열 속성에 대 한 대체 이름을 제공 하는 별칭 속성을 추가 하는 경우 **SecondValue** 의 값을 지정 하 여 별칭이 지정 된 문자열 값을 정수로 변환할 수도 있습니다 **.**

**MemberType** 매개 변수의 값이 인 경우 `ScriptProperty` **SecondValue** 매개 변수를 사용 하 여 추가 스크립트 블록을 지정할 수 있습니다. **Value** 매개 변수 값에 있는 스크립트 블록은 변수 값을 가져옵니다. **SecondValue** 매개 변수 값에 있는 스크립트 블록은 변수 값을 설정합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SerializationDepth

문자열로 직렬화되는 유형 개체의 수준 수를 지정합니다. 기본값은 `1` 개체와 해당 속성을 serialize 합니다. 값은 `0` 개체를 serialize 하지만 해당 속성은 serialize 하지 않습니다. 값은 `2` 개체, 해당 속성 및 속성 값에 있는 모든 개체를 serialize 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Int32
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### -SerializationMethod

유형의 직렬화 메서드를 지정합니다. 직렬화 메서드는 직렬화되는 유형의 속성과 직렬화에 사용되는 기술을 결정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- `AllPublicProperties`. 유형의 모든 공용 속성을 직렬화합니다. **SerializationDepth** 매개 변수를 사용하여 자식 속성을 직렬화할지 여부를 결정할 수 있습니다.
- `String`. 유형을 문자열로 직렬화합니다. **StringSerializationSource** 를 사용하여 직렬화 결과로 사용할 유형의 속성을 지정할 수 있습니다. 그러지 않으면 유형이 개체의 **ToString** 메서드를 사용하여 직렬화됩니다.
- `SpecificProperties`. 이 형식의 지정 된 속성만 직렬화 합니다. **PropertySerializationSet** 매개 변수를 사용하여 직렬화할 유형의 속성을 지정할 수 있습니다.
  **InheritPropertySerializationSet** 매개 변수를 사용하여 속성 집합을 상속할지 여부를 결정하고 **SerializationDepth** 매개 변수를 사용하여 자식 속성을 직렬화할지 여부를 결정할 수도 있습니다.

PowerShell에서 직렬화 메서드는 **Psstandardmembers** 내부 개체에 저장 됩니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StringSerializationSource

유형의 속성 이름을 지정합니다. 지정한 속성 값은 직렬화 결과로 사용됩니다. 이 매개 변수는 **SerializationMethod** 매개 변수 값이 문자열인 경우에만 유효 합니다.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetTypeForDeserialization

역직렬화 시 이 유형의 개체가 변환되는 유형을 지정합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeAdapter

유형 어댑터의 유형 (예: **CimInstanceAdapter**)을 지정 합니다. 형식 어댑터를 사용 하면 PowerShell에서 형식의 멤버를 가져올 수 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeConverter

유형 간에 값을 변환할 유형 변환기를 지정합니다. 유형에 대한 유형 변환기를 정의하면 유형 변환기 인스턴스가 변환에 사용됩니다.

**System.ComponentModel.TypeConverter** 또는 **System.Management.Automation.PSTypeConverter** 클래스에서 파생된 **System.Type** 값을 입력합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Update-typedata

이 cmdlet이 세션에 추가 하는 형식 데이터의 배열을 지정 합니다. **Update-typedata** 개체가 포함 된 변수를 입력 하거나 **update-typedata** 개체를 가져오는 명령 (예: 명령)을 입력 `Get-TypeData` 합니다. **Update-typedata** 개체를로 파이프 할 수도 있습니다 `Update-TypeData` .

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.Runspaces.TypeData[]
Parameter Sets: TypeDataSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -TypeName

확장할 유형의 이름을 지정합니다.

**System** 네임스페이스에 있는 유형의 경우 짧은 이름을 입력합니다. 그러지 않으면 전체 유형 이름이 필요합니다. 와일드카드는 지원되지 않습니다.

형식 이름을로 파이프 할 수 있습니다 `Update-TypeData` . 개체를로 파이프 하는 경우 개체 `Update-TypeData` `Update-TypeData` 의 형식 이름과 개체 형식에 대 한 데이터를 가져옵니다.

**MemberName**, **MemberType**, **Value** 및 **SecondValue** 매개 변수와 함께이 매개 변수를 사용 하 여 형식의 속성이 나 메서드를 추가 하거나 변경할 수 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Value

속성 또는 메서드의 값을 지정합니다.

,, 또는 멤버를 추가 하는 경우 `AliasProperty` `CodeProperty` `ScriptProperty` `CodeMethod` **SecondValue** 매개 변수를 사용 하 여 추가 정보를 추가할 수 있습니다.

**MemberName**, **MemberType**, **Value** 및 **SecondValue** 매개 변수와 함께이 매개 변수를 사용 하 여 형식의 속성이 나 메서드를 추가 하거나 변경할 수 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
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

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

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

### System.String

**Appendpath**, **TypeName** 또는 **update-typedata** 매개 변수의 값이 포함 된 문자열을로 파이프 할 수 있습니다 `Update-TypeData` .

## 출력

### 없음

이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

## 관련 링크

[about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Get-TypeData](Get-TypeData.md)

[Remove-TypeData](Remove-TypeData.md)


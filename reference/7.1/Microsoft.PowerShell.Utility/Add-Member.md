---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-member?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Member
ms.openlocfilehash: f6cc98f31d42f3468fd864782fb7252b064302b8
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389473"
---
# Add-Member

## 개요
사용자 지정 속성 및 메서드를 PowerShell 개체의 인스턴스에 추가 합니다.

## SYNTAX

### TypeNameSet (기본값)

```
Add-Member -InputObject <PSObject> -TypeName <String> [-PassThru] [<CommonParameters>]
```

### 참고 Propertymultimemberset

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru]
 [-NotePropertyMembers] <IDictionary> [<CommonParameters>]
```

### NotePropertySingleMemberSet

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru] [-NotePropertyName] <String>
 [-NotePropertyValue] <Object> [<CommonParameters>]
```

### 집합

```
Add-Member -InputObject <PSObject> [-MemberType] <PSMemberTypes> [-Name] <String> [[-Value] <Object>]
 [[-SecondValue] <Object>] [-TypeName <String>] [-Force] [-PassThru] [<CommonParameters>]
```

## 설명

`Add-Member`Cmdlet을 사용 하면 PowerShell 개체의 인스턴스에 멤버 (속성 및 메서드)를 추가할 수 있습니다. 예를 들어 개체에 대 한 설명이 포함 된 메모 속성 멤버를 추가 하거나 스크립트를 실행 하 여 개체를 변경 하는 **ScriptMethod** 멤버를 추가할 수 있습니다.

를 사용 하려면 `Add-Member` 개체를로 파이프 `Add-Member` 하거나 **InputObject** 매개 변수를 사용 하 여 개체를 지정 합니다.

**MemberType** 매개 변수는 추가 하려는 멤버의 유형을 나타냅니다. **Name** 매개 변수는 새 멤버에 이름을 할당 하 고 **value** 매개 변수는 멤버의 값을 설정 합니다.

추가한 속성 및 메서드는 지정한 개체의 특정 인스턴스에만 추가됩니다. `Add-Member` 는 개체 유형을 변경 하지 않습니다. 새 개체 유형을 만들려면 cmdlet을 사용 `Add-Type` 합니다.

Cmdlet을 사용 하 여 `Export-Clixml` 추가 멤버를 비롯 한 개체의 인스턴스를 파일에 저장할 수도 있습니다. 그런 다음 cmdlet을 사용 `Import-Clixml` 하 여 내보낸 파일에 저장 된 정보에서 개체의 인스턴스를 다시 만들 수 있습니다.

Windows PowerShell 3.0부터에는 `Add-Member` 개체에 메모 속성을 더 쉽게 추가할 수 있도록 하는 새로운 기능이 있습니다.
**NotePropertyName** 및 **NotePropertyValue** 매개 변수를 사용하여 메모 속성을 정의하거나 **NotePropertyMembers** 매개 변수를 사용하여 메모 속성 이름 및 값의 해시 테이블을 사용합니다.

또한 Windows PowerShell 3.0부터는 출력 개체를 생성하는 **PassThru** 매개 변수의 필요성이 줄어듭니다. `Add-Member` 이제는 더 많은 형식의 입력 개체에 직접 새 멤버를 추가 합니다. 자세한 내용은 **PassThru** 매개 변수 설명을 참조하세요.

## 예제

### 예제 1: PSObject에 메모 속성 추가

다음 예에서는 값이 "Done" 인 **상태** 메모 속성을 파일을 나타내는 **FileInfo** 개체에 추가 합니다 `Test.txt` .

첫 번째 명령은 cmdlet을 사용 하 여 `Get-ChildItem` 파일을 나타내는 **FileInfo** 개체를 가져옵니다 `Test.txt` . `$a`변수에 저장 합니다.

두 번째 명령은 메모 속성을의 개체에 추가 합니다 `$a` .

세 번째 명령은 점 표기법을 사용 하 여에서 개체의 **Status** 속성 값을 가져옵니다 `$a` . 출력에서 볼 수 있듯이 값은 "Done"입니다.

```powershell
$A = Get-ChildItem c:\ps-test\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

```Output
Done
```

### 예제 2: PSObject에 별칭 속성 추가

다음 예에서는 파일을 나타내는 개체에 **크기** 별칭 속성을 추가 합니다 `Test.txt` . 새 속성은 **Length** 속성에 대 한 별칭입니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Get-ChildItem` `Test.txt` **FileInfo** 개체를 가져옵니다.

두 번째 명령은 **크기** 별칭 속성을 추가 합니다.
세 번째 명령은 점 표기법을 사용 하 여 새 **크기** 속성의 값을 가져옵니다.

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$A | Add-Member -MemberType AliasProperty -Name Size -Value Length
$A.Size
```

```Output
2394
```

### 예제 3: 문자열에 StringUse 메모 속성 추가

이 예에서는 문자열에 **Stringuse** note 속성을 추가 합니다.
는 `Add-Member` **문자열** 입력 개체에 형식을 추가할 수 없으므로 **PassThru** 매개 변수를 지정 하 여 출력 개체를 생성할 수 있습니다. 예제의 마지막 명령은 새 속성을 표시합니다.

이 예에서는 **참고 Propertymembers** 매개 변수를 사용 합니다. **NotePropertyMembers** 매개 변수 값은 해시 테이블입니다. 키는 메모 속성 이름인 **Stringuse** 이 고 값은 메모 속성 값인 **Display** 입니다.

```powershell
$A = "A string"
$A = $A | Add-Member -NotePropertyMembers @{StringUse="Display"} -PassThru
$A.StringUse
```

```Output
Display
```

### 예제 4: FileInfo 개체에 스크립트 메서드 추가

이 예에서는 파일 크기를 가장 가까운 메가바이트 수로 계산 하는 **FileInfo** 개체에 **sizeinmb** 스크립트 메서드를 추가 합니다. 두 번째 명령은 형식의 **round** 정적 메서드를 사용 하 여 **ScriptBlock** `[math]` 파일 크기를 두 번째 소수 자리로 반올림 하는 ScriptBlock을 만듭니다.

또한 **Value** 매개 변수는 `$This` 현재 개체를 나타내는 자동 변수를 사용 합니다. `$This`변수는 새 속성 및 메서드를 정의 하는 스크립트 블록 에서만 유효 합니다.

마지막 명령은 점 표기법을 사용 하 여 변수의 개체에서 새 **Sizeinmb** 스크립트 메서드를 호출 합니다 `$A` .

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$S = {[math]::Round(($this.Length / 1MB), 2)}
$A | Add-Member -MemberType ScriptMethod -Name "SizeInMB" -Value $S
$A.SizeInMB()
```

```Output
0.43
```

### 예제 5: 개체의 모든 속성을 다른 개체에 복사

이 함수는 한 개체의 모든 속성을 다른 개체에 복사합니다.

루프는 cmdlet을 사용 하 여 `foreach` `Get-Member` **From** 개체의 각 속성을 가져옵니다. 루프 내의 명령은 `foreach` 각 속성에서 계열로 수행 됩니다.

이 `Add-Member` 명령은 **From** 개체의 속성을 **To** 개체에 **메모 속성** 으로 추가 합니다. 값은 **value** 매개 변수를 사용 하 여 복사 됩니다. **Force** 매개 변수를 사용 하 여 멤버 이름이 같은 멤버를 추가 합니다.

```powershell
function Copy-Property ($From, $To)
{
    $properties = Get-Member -InputObject $From -MemberType Property
    foreach ($p in $properties)
    {
        $To | Add-Member -MemberType NoteProperty -Name $p.Name -Value $From.$($p.Name) -Force
    }
}
```

### 예제 6: 사용자 지정 개체 만들기

이 예제에서는 **Asset** 사용자 지정 개체를 만듭니다.

이 `New-Object` cmdlet은 **PSObject** 를 만듭니다. 이 예에서는 **PSObject** 를 변수에 저장 합니다 `$Asset` .

두 번째 명령은 형식 액셀러레이터를 사용 하 여 `[ordered]` 이름 및 값의 정렬 된 사전을 만듭니다. 이 명령은 결과를 `$D` 변수에 저장 합니다.

세 번째 명령은 cmdlet의 **참고 Propertymembers** 매개 변수를 사용 하 여 `Add-Member` `$D` 변수의 사전을 **PSObject** 에 추가 합니다.
**TypeName** 속성은 새 이름인 **Asset** 를 **PSObject** 에 할당 합니다.

마지막 명령은 새 **자산** 개체를 cmdlet으로 파이프 합니다 `Get-Member` . 출력은 개체에 **자산의** 형식 이름과 정렬 된 사전에 정의한 메모 속성이 있음을 보여 줍니다.

```powershell
$Asset = New-Object -TypeName PSObject
$d = [ordered]@{Name="Server30";System="Server Core";PSVersion="4.0"}
$Asset | Add-Member -NotePropertyMembers $d -TypeName Asset
$Asset | Get-Member
```

```Output
   TypeName: Asset

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty System.String Name=Server30
PSVersion   NoteProperty System.String PSVersion=4.0
System      NoteProperty System.String System=Server Core
```

## PARAMETERS

### -Force

개체에 이름이 같은 사용자 지정 멤버가 있는 경우에도이 cmdlet이 새 멤버를 추가 함을 나타냅니다.
**Force** 매개 변수를 사용 하 여 형식의 표준 멤버를 바꿀 수 없습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MemberSet, NotePropertySingleMemberSet, NotePropertyMultiMemberSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

새 멤버를 추가할 개체를 지정합니다.
개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MemberType

추가할 멤버의 형식을 지정 합니다.
이 매개 변수는 필수적 요소입니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- NoteProperty
- AliasProperty
- ScriptProperty
- CodeProperty
- ScriptMethod
- CodeMethod

이러한 값에 대 한 자세한 내용은 PowerShell SDK의 [PSMemberTypes 열거](/dotnet/api/system.management.automation.psmembertypes) 를 참조 하세요.

모든 개체가 모든 멤버 유형을 포함하는 것은 아닙니다.
개체에 포함 되지 않은 멤버 유형을 지정 하면 PowerShell에서 오류를 반환 합니다.

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: MemberSet
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

이 cmdlet이 추가 하는 멤버의 이름을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: MemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -참고 Propertymembers

메모 속성 이름 및 값의 해시 테이블 또는 순서가 지정된 사전을 지정합니다.
키는 메모 속성 이름이고 값은 메모 속성 값인 해시 테이블이나 사전을 입력합니다.

PowerShell의 해시 테이블 및 순서가 지정 된 사전에 대 한 자세한 내용은 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)를 참조 하세요.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: NotePropertyMultiMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -참고 Propertyname

메모 속성 이름을 지정 합니다.

이 매개 변수는 **NotePropertyValue** 매개 변수와 함께 사용합니다.
이 매개 변수는 선택 사항입니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -참고 Propertyvalue

메모 속성 값을 지정 합니다.

이 매개 변수는 **메모 propertyname** 매개 변수와 함께 사용 합니다.
이 매개 변수는 선택 사항입니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Object
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

작업 중인 항목을 나타내는 개체를 반환합니다.
기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

대부분의 개체에 대해는 `Add-Member` 입력 개체에 새 멤버를 추가 합니다.
그러나 입력 개체가 문자열이 면는 `Add-Member` 입력 개체에 멤버를 추가할 수 없습니다.
이러한 개체의 경우 **PassThru** 매개 변수를 사용하여 출력 개체를 만듭니다.

Windows PowerShell 2.0에서 `Add-Member` 개체가 아닌 개체의 **PSObject** 래퍼로 멤버를 추가 했습니다.
**PassThru** 매개 변수를 사용 하 여 **PSObject** 래퍼가 있는 모든 개체에 대 한 출력 개체를 만듭니다.

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

### -SecondValue

**AliasProperty** , **ScriptProperty** , **CodeProperty** 또는 **CodeMethod** 멤버에 대한 선택적 추가 정보를 지정합니다.

**AliasProperty** 를 추가할 때 사용 하는 경우이 매개 변수는 데이터 형식 이어야 합니다.
지정 된 데이터 형식으로의 변환은 **AliasProperty** 의 값에 추가 됩니다.

예를 들어 문자열 속성에 대 한 대체 이름을 제공 하는 **AliasProperty** 을 추가 하는 경우 해당 **AliasProperty** 를 사용 하 여 액세스할 때 해당 문자열 속성의 값이 정수로 변환 되어야 함을 나타내도록 **SecondValue의** 매개 변수를 지정할 수도 **있습니다.**

**Scriptproperty** 멤버를 추가할 때 **SecondValue** 매개 변수를 사용 하 여 추가 **ScriptBlock** 을 지정할 수 있습니다. **값** 매개 변수에 지정 된 첫 번째 **ScriptBlock** 은 변수의 값을 가져오는 데 사용 됩니다. **SecondValue** 매개 변수에 지정 된 두 번째 **ScriptBlock** 은 변수의 값을 설정 하는 데 사용 됩니다.

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

추가된 멤버의 초기값을 지정합니다.
**AliasProperty** , **codeproperty** , **scriptproperty** 또는 **codeproperty** 멤버를 추가 하는 경우 **SecondValue** 매개 변수를 사용 하 여 선택적 추가 정보를 제공할 수 있습니다.

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

형식의 이름을 지정합니다.

형식이 **시스템** 네임 스페이스의 클래스 이거나 형식이 액셀러레이터 인 형식이 면 형식의 짧은 이름을 입력할 수 있습니다. 그러지 않으면 전체 유형 이름이 필요합니다.
이 매개 변수는 **InputObject** 가 **PSObject** 인 경우에만 적용 됩니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: TypeNameSet, NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: True (TypeNameSet), False (NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.web. PSObject

모든 개체 형식을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### None 또는 System.object

**PassThru** 매개 변수를 사용 하는 경우이 cmdlet은 새로 확장 된 개체를 반환 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

**PSObject** 개체에만 멤버를 추가할 수 있습니다. 개체가 **PSObject** 개체 인지 여부를 확인 하려면 연산자를 사용 `-is` 합니다.

예를 들어 변수에 저장 된 개체를 테스트 하려면 `$obj` 을 입력 `$obj -is [PSObject]` 합니다.

**MemberType** , **Name** , **Value** 및 **SecondValue** 매개 변수의 이름은 선택 사항입니다.
매개 변수 이름을 생략 하는 경우 명명 되지 않은 매개 변수 값은 **MemberType** , **Name** , **Value** 및 **SecondValue** 순서로 표시 되어야 합니다.

매개 변수 이름을 포함할 경우 원하는 순서대로 매개 변수를 표시할 수 있습니다.

`$this`새 속성 및 메서드의 값을 정의 하는 스크립트 블록에서 자동 변수를 사용할 수 있습니다.
`$this`변수는 속성 및 메서드가 추가 되는 개체의 인스턴스를 참조 합니다. 변수에 대 한 자세한 내용은 `$this` [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.

## 관련 링크

[Export-Clixml](Export-Clixml.md)

[Get-Member](Get-Member.md)

[Import-Clixml](Import-Clixml.md)

[New-Object](New-Object.md)

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)


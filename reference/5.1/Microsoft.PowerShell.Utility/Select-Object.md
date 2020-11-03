---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 59cbba88e3c21d740b774d95e7c0e734cd8e3fdc
ms.sourcegitcommit: f9ae48d026d65833b9c8ca881058dda0bbd067b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "93220098"
---
# Select-Object

## 개요
개체 또는 개체 속성을 선택합니다.

## SYNTAX

### DefaultParameter (기본값)

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### SkipLastParameter

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### IndexParameter

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

## 설명

`Select-Object`Cmdlet은 개체 또는 개체 집합의 지정 된 속성을 선택 합니다. 또한 고유한 개체, 지정된 수의 개체 또는 배열에서 지정된 위치에 있는 개체를 선택할 수 있습니다.

컬렉션에서 개체를 선택하려면 **First** , **Last** , **Unique** , **Skip** 및 **Index** 매개 변수를 사용합니다. 개체 속성을 선택하려면 **Property** 매개 변수를 사용합니다. 속성을 선택 하면에서 `Select-Object` 지정 된 속성만 있는 새 개체를 반환 합니다.

Windows PowerShell 3.0 이상에 `Select-Object` 는 명령에서 사용 되지 않는 개체를 만들고 처리 하지 못하게 하는 최적화 기능이 포함 되어 있습니다.

명령 `Select-Object` 파이프라인에 **첫 번째** 또는 **인덱스** 매개 변수를 사용 하 여 명령을 포함 하는 경우 개체를 생성 하는 명령이 파이프라인의 명령 앞에 표시 되는 경우에도 PowerShell에서 개체를 생성 하는 명령을 중지 합니다 `Select-Object` . 이 최적화 동작을 끄려면 **Wait** 매개 변수를 사용합니다.

## 예제

### 예제 1: 속성으로 개체 선택

이 예에서는 process 개체의 **이름** , **ID** 및 **WS** (작업 집합) 속성이 있는 개체를 만듭니다.

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### 예제 2: 속성으로 개체 선택 및 결과 서식 지정

이 예에서는 컴퓨터의 프로세스에서 사용 하는 모듈에 대 한 정보를 가져옵니다. Cmdlet을 사용 하 여 `Get-Process` 컴퓨터의 프로세스를 가져옵니다.

Cmdlet을 사용 하 여에 `Select-Object` `[System.Diagnostics.ProcessModule]` 의해 출력 되는 각 인스턴스의 **Modules** 속성에 포함 된 인스턴스의 배열을 출력 `System.Diagnostics.Process` `Get-Process` 합니다.

Cmdlet의 **Property** 매개 변수는 `Select-Object` 프로세스 이름을 선택 합니다. `ProcessName`모든 인스턴스에 대 한 **참고 속성** 을 추가 하 `[System.Diagnostics.ProcessModule]` 고 현재 프로세스의 **ProcessName** 속성 값으로 채웁니다.

마지막으로 `Format-List` cmdlet은 각 프로세스의 이름과 모듈을 목록에 표시 하는 데 사용 됩니다.

```powershell
Get-Process Explorer | Select-Object -Property ProcessName -ExpandProperty Modules | Format-List
```

```Output
ProcessName       : explorer
ModuleName        : explorer.exe
FileName          : C:\WINDOWS\explorer.exe
BaseAddress       : 140697278152704
ModuleMemorySize  : 3919872
EntryPointAddress : 140697278841168
FileVersionInfo   : File:             C:\WINDOWS\explorer.exe
                    InternalName:     explorer
                    OriginalFilename: EXPLORER.EXE.MUI
                    FileVersion:      10.0.17134.1 (WinBuild.160101.0800)
                    FileDescription:  Windows Explorer
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.17134.1
...
```

### 예제 3: 메모리를 가장 많이 사용 하는 프로세스 선택

이 예제에서는 메모리를 가장 많이 사용 하는 5 개의 프로세스를 가져옵니다. `Get-Process`Cmdlet은 컴퓨터의 프로세스를 가져옵니다. `Sort-Object`Cmdlet은 메모리 (작업 집합) 사용에 따라 프로세스를 정렬 하 고, `Select-Object` cmdlet은 개체의 결과 배열에서 마지막 5 개의 멤버만 선택 합니다.

는 **Wait** `Sort-Object` `Sort-Object` 모든 개체를 처리 한 다음 컬렉션을 반환 하기 때문에 cmdlet을 포함 하는 명령에는 Wait 매개 변수가 필요 하지 않습니다. `Select-Object`최적화는 개체를 처리 하는 동안 개별적으로 반환 하는 명령에만 사용할 수 있습니다.

```powershell
Get-Process | Sort-Object -Property WS | Select-Object -Last 5
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VS(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
2866     320       33432      45764   203   222.41   1292 svchost
577      17        23676      50516   265    50.58   4388 WINWORD
826      11        75448      76712   188    19.77   3780 Ps
1367     14        73152      88736   216    61.69    676 Ps
1612     44        66080      92780   380   900.59   6132 INFOPATH
```

### 예제 4: 배열에서 고유한 문자 선택

이 예제에서는의 **unique** 매개 변수를 사용 하 여 `Select-Object` 문자 배열에서 고유한 문자를 가져옵니다.

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### 예 5: 이벤트 로그에서 최신 이벤트 및 가장 오래 된 이벤트 선택

이 예제에서는 Windows PowerShell 이벤트 로그에서 첫 번째 (최신) 및 마지막 (가장 오래 된) 이벤트를 가져옵니다.

`Get-EventLog` Windows PowerShell 로그의 모든 이벤트를 가져와 `$a` 변수에 저장 합니다.
그런 다음 `$a` 가 cmdlet으로 파이프 됩니다 `Select-Object` . 이 `Select-Object` 명령은 **Index** 매개 변수를 사용 하 여 변수의 이벤트 배열에서 이벤트를 선택 합니다 `$a` . 첫 번째 이벤트의 인덱스는 0입니다. 마지막 이벤트의 인덱스는의 항목 수에서 1을 뺀 값입니다 `$a` .

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### 예제 6: 첫 번째 개체를 제외한 모든 개체를 선택 합니다.

이 예제에서는 첫 번째 항목을 제외 하 고 Servers.txt 파일에 나열 된 각 컴퓨터에 새 PSSession을 만듭니다.

`Select-Object` 컴퓨터 이름 목록에서 첫 번째 컴퓨터를 제외한 모든 컴퓨터를 선택 합니다. 결과 컴퓨터 목록은 cmdlet의 **ComputerName** 매개 변수 값으로 설정 됩니다 `New-PSSession` .

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### 예 7: 파일 이름 바꾸기 및 검토할 몇 가지 선택

이 예에서는 읽기 전용 특성이 있는 텍스트 파일의 기본 이름에 "-ro" 접미사를 추가한 다음 사용자가 결과 샘플을 볼 수 있도록 처음 다섯 개 파일을 표시 합니다.

`Get-ChildItem`**ReadOnly** 동적 매개 변수를 사용 하 여 읽기 전용 파일을 가져옵니다. 결과 파일은 cmdlet으로 파이프 되어 `Rename-Item` 파일의 이름을 바꿉니다. 의 **Passthru** 매개 변수를 사용 하 여 `Rename-Item` 이름을 바꾼 파일을 cmdlet으로 보냅니다 `Select-Object` .이 cmdlet은 표시를 위해 처음 5 개를 선택 합니다.

의 **Wait** 매개 변수는 `Select-Object` `Get-ChildItem` 처음 5 개의 읽기 전용 텍스트 파일을 가져온 후 PowerShell에서 cmdlet을 중지 하지 못하도록 합니다. 이 매개 변수를 사용하지 않으면 처음 다섯 개 읽기 전용 파일만 이름이 바뀝니다.

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### 예 8:-ExpandProperty 매개 변수를 복잡 하 게 보여 줍니다.

이 예에서는 **ExpandProperty** 매개 변수를 복잡 하 게 보여 줍니다.

생성 된 출력은 인스턴스의 배열입니다 `[System.Int32]` . 인스턴스는 **출력 뷰의** 표준 서식 지정 규칙을 따릅니다. 이는 *확장* 된 속성에 대해 적용 됩니다. 출력 된 개체에 특정 표준 형식이 있으면 확장 된 속성이 표시 되지 않을 수 있습니다.

```powershell
# Create a custom object to use for the Select-Object example.
$object = [pscustomobject]@{Name="CustomObject";Expand=@(1,2,3,4,5)}
# Use the ExpandProperty parameter to Expand the property.
$object | Select-Object -ExpandProperty Expand -Property Name
```

```Output
1
2
3
4
5
```

```powershell
# The output did not contain the Name property, but it was added successfully.
# Use Get-Member to confirm the Name property was added and populated.
$object | Select-Object -ExpandProperty Expand -Property Name | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType   Definition
----        ----------   ----------
CompareTo   Method       int CompareTo(System.Object value), int CompareTo(int value), int IComparable.CompareTo(System.Object obj)...
Equals      Method       bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int].Equals(int other)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
GetTypeCode Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar      Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime  Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal   Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble    Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16     Method       int16 IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32     Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64     Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte     Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle    Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString    Method       string ToString(), string ToString(string format), string ToString(System.IFormatProvider provider)...
ToType      Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16    Method       uint16 IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32    Method       uint32 IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64    Method       uint64 IConvertible.ToUInt64(System.IFormatProvider provider)
Name        NoteProperty string Name=CustomObject
```

### 예제 9: 개체에 대 한 사용자 지정 속성 만들기

다음 예제에서는를 사용 하 여 `Select-Object` 사용자 지정 속성을 개체에 추가 하는 방법을 보여 줍니다.
존재 하지 않는 속성 이름을 지정 하면 `Select-Object` 는 전달 된 각 개체에 대해 해당 속성을 **참고 속성** 으로 만듭니다.

```powershell
$customObject = 1 | Select-Object -Property MyCustomProperty
$customObject.MyCustomProperty = "New Custom Property"
$customObject
```

```Output
MyCustomProperty
----------------
New Custom Property
```

### 예 10: 각 InputObject에 대해 계산 된 속성 만들기

이 예제에서는를 사용 하 여 `Select-Object` 계산 된 속성을 입력에 추가 하는 방법을 보여 줍니다. **ScriptBlock** 을 **Property** 매개 변수에 전달 하면가 `Select-Object` 전달 된 각 개체에 대해 식을 평가 하 고 결과를 출력에 추가 합니다. **ScriptBlock** 내에서 변수를 사용 하 여 `$_` 파이프라인의 현재 개체를 참조할 수 있습니다.

기본적으로에서는 `Select-Object` **ScriptBlock** 문자열을 속성 이름으로 사용 합니다. **Hashtable** 을 사용 하 여 각 개체에 추가 된 사용자 지정 속성으로 **ScriptBlock** 의 출력에 레이블을 지정할 수 있습니다. 에 전달 된 각 개체에 여러 계산 된 속성을 추가할 수 있습니다 `Select-Object` .

```powershell
# Create a calculated property called $_.StartTime.DayOfWeek
Get-Process | Select-Object -Property ProcessName,{$_.StartTime.DayOfWeek}
```

```Output
ProcessName  $_.StartTime.DayOfWeek
----         ----------------------
alg                       Wednesday
ati2evxx                  Wednesday
ati2evxx                   Thursday
...
```

```powershell
# Add a custom property to calculate the size in KiloBytes of each FileInfo object you pass in.
# Use the pipeline variable to divide each file's length by 1 KiloBytes
$size = @{label="Size(KB)";expression={$_.length/1KB}}
# Create an additional calculated property with the number of Days since the file was last accessed.
# You can also shorten the key names to be 'l', and 'e', or use Name instead of Label.
$days = @{l="Days";e={((Get-Date) - $_.LastAccessTime).Days}}
# You can also shorten the name of your label key to 'l' and your expression key to 'e'.
Get-ChildItem $PSHOME -File | Select-Object Name, $size, $days
```

```Output
Name                        Size(KB)        Days
----                        --------        ----
Certificate.format.ps1xml   12.5244140625   223
Diagnostics.Format.ps1xml   4.955078125     223
DotNetTypes.format.ps1xml   134.9833984375  223
```

## PARAMETERS

### -ExcludeProperty

이 cmdlet이 작업에서 제외 하는 속성을 지정 합니다. 와일드카드가 지원됩니다. 이 매개 변수는 명령에 **Property** 매개 변수도 포함되는 경우에만 적용됩니다.

```yaml
Type: System.String[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ExpandProperty

선택할 속성을 지정하고 해당 속성을 확장하려고 시도해야 함을 나타냅니다.

- 지정 된 속성이 배열인 경우 배열의 각 값이 출력에 포함 됩니다.
- 지정 된 속성이 개체 이면 모든 **InputObject** 에 대해 개체 속성이 확장 됩니다.

두 경우 모두 출력 되는 개체의 **형식은** 확장 된 속성의 **형식과** 일치 합니다.

**Property** 매개 변수가 지정 된 경우는 `Select-Object` 모든 출력 된 개체에 대해 선택한 각 속성을 **메모 속성** 으로 추가 하려고 합니다.

> [!WARNING]
> 다음 오류가 표시 되는 경우: Select: 속성은 이미 존재 하기 때문에 처리할 수 없습니다 `<PropertyName>` . 다음을 고려 하십시오.
> 를 사용 하는 `-ExpandProperty` 경우 `Select-Object` 기존 속성을 바꿀 수 없습니다.
> 이것은 다음을 의미합니다.
>
> - 확장 된 개체에 같은 이름의 속성이 있는 경우 오류가 발생 합니다.
> - *선택한* 개체에 *확장* 된 개체 속성과 같은 이름의 속성이 있는 경우 오류가 발생 합니다.

```yaml
Type: System.String
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -첫 번째

입력 개체 배열의 시작에서 선택할 개체 수를 지정합니다.

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -인덱스

인덱스 값을 기준으로 배열에서 개체를 선택합니다. 인덱스를 쉼표로 구분된 목록으로 입력합니다. 배열의 인덱스는 0에서 시작하는데 여기서 0은 첫 번째 값을 나타내고 (n-1)은 마지막 값을 나타냅니다.

```yaml
Type: System.Int32[]
Parameter Sets: IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

파이프라인을 통해 cmdlet에 보낼 개체를 지정합니다. 이 매개 변수를 사용 하 여 개체를에 연결할 수 있습니다 `Select-Object` .

개체를 **inputobject** 매개 변수에 전달 하는 경우 파이프라인을 사용 하는 대신는 `Select-Object` 값이 컬렉션인 경우에도 **inputobject** 를 단일 개체로 처리 합니다. 로 컬렉션을 전달할 때 파이프라인을 사용 하는 것이 좋습니다 `Select-Object` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -마지막

입력 개체 배열의 끝에서 선택할 개체 수를 지정합니다.

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -속성

선택할 속성을 지정합니다. 이러한 속성은 output 개체에 **메모 속성** 멤버로 추가 됩니다. 와일드카드가 지원됩니다.

**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다. 계산된 속성을 만들려면 해시 테이블을 사용하세요.

유효한 키는 다음과 같습니다.

- 이름 (또는 레이블)- `<string>`
- 식 `<string>` 또는 `<script block>`

자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Skip

지정된 개수의 항목을 선택하지 않고 건너뜁니다. **Skip** 매개 변수는 기본적으로 개체 목록 또는 배열의 처음부터 계산 하지만, 명령에서 **마지막** 매개 변수를 사용 하는 경우 목록 또는 배열의 끝부터 계산 합니다.

0에서 계산을 시작하는 **Index** 매개 변수와 달리 **Skip** 매개 변수는 1에서 시작합니다.

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipLast

목록 또는 배열의 끝부터 지정 된 수의 항목을 건너뜁니다 (선택 하지 않음). 는 **마지막** 매개 변수와 함께 **Skip** 을 사용 하는 것과 동일한 방식으로 작동 합니다.

0에서 계산을 시작 하는 **인덱스** 매개 변수와 달리 **SkipLast** 매개 변수는 1부터 시작 합니다.

```yaml
Type: System.Int32
Parameter Sets: SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -고유

입력 개체의 하위 집합 속성과 값이 동일한 경우 하위 집합의 멤버 하나만 선택되도록 지정합니다.

이 매개 변수는 대/소문자를 구분합니다. 따라서 문자의 대/소문자만 다른 문자열은 고유한 것으로 간주합니다.

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

### -Wait

Cmdlet이 최적화를 해제 함을 나타냅니다. PowerShell은 명령 파이프라인에 나타나는 순서 대로 명령을 실행 하 고 모든 개체를 생성할 수 있도록 합니다. 기본적으로 명령 `Select-Object` 파이프라인에 **첫 번째** 또는 **인덱스** 매개 변수를 사용 하 여 명령을 포함 하는 경우 PowerShell은 선택한 개체 수가 생성 되는 즉시 개체를 생성 하는 명령을 중지 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultParameter, IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.web. PSObject

모든 개체를로 파이프 할 수 있습니다 `Select-Object` .

## 출력

### System.web. PSObject

## 참고

- 또한 `Select-Object` 해당 기본 제공 별칭인에서 cmdlet을 참조할 수 있습니다 `select` . 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.

- 의 최적화 기능은 `Select-Object` 개체를 처리할 때 파이프라인에 개체를 쓰는 명령에만 사용할 수 있습니다. 처리된 개체를 버퍼링하고 컬렉션으로 작성하는 명령에는 적용되지 않습니다. 개체를 즉시 기록하는 것이 cmdlet 설계 모범 사례입니다. 자세한 내용은 [강력한 개발 지침](/powershell/scripting/developer/windows-powershell)에서 _파이프라인에 단일 레코드 쓰기_ 를 참조 하세요.

## 관련 링크

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Group-Object](Group-Object.md)

[Sort-Object](Sort-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

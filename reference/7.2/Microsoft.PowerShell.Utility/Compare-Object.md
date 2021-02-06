---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/compare-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compare-Object
ms.openlocfilehash: 6bed0e8d13cb834fab97dc0265ef7d46a2caea97
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605256"
---
# Compare-Object

## 개요
두 개체 집합을 비교합니다.

## 구문

```
Compare-Object [-ReferenceObject] <PSObject[]> [-DifferenceObject] <PSObject[]>
 [-SyncWindow <Int32>] [-Property <Object[]>] [-ExcludeDifferent] [-IncludeEqual] [-PassThru]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## Description

`Compare-Object`Cmdlet은 두 개체 집합을 비교 합니다. 한 개체 집합은 **참조** 이 고 다른 개체 집합은 서로 **다릅니다**.

`Compare-Object` 전체 개체를 비교 하는 사용 가능한 메서드를 확인 합니다. 적절 한 메서드를 찾을 수 없는 경우 입력 개체의 **ToString ()** 메서드를 호출 하 고 문자열 결과를 비교 합니다. 비교에 사용할 속성을 하나 이상 제공할 수 있습니다. 속성이 제공 되는 경우 cmdlet은 해당 속성의 값만 비교 합니다.

비교 결과는 속성 값이 **참조** 개체에만 표시 되는지 ( `<=` ) 아니면 **차이점** 개체 () 에서만 표시 되는지 여부를 나타냅니다 `=>` . **Includeequal** 매개 변수가 사용 되는 경우 ( `==` )는 두 개체 모두에 값이 있음을 나타냅니다.

**참조** 또는 **차이점** 개체가 null ( `$null` ) 이면에서 `Compare-Object` 종료 오류를 생성 합니다.

일부 예제에서는 스 플랫를 사용 하 여 코드 샘플의 줄 길이를 줄입니다. 자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.

## 예

### 예제 1-두 텍스트 파일의 내용 비교

이 예에서는 두 텍스트 파일의 내용을 비교 합니다. 이 예제에서는 다음 두 텍스트 파일을 사용 하며, 각 값은 별도의 줄에 있습니다.

- `Testfile1.txt` dog, squirrel 및 bird 값을 포함 합니다.
- `Testfile2.txt` cat, bird 및 racoon 값을 포함 합니다.

출력에는 파일 간에 다른 줄만 표시 됩니다. `Testfile1.txt` 는 **참조** 개체 ( `<=` )이 고 `Testfile2.txt` 은 **차이** 개체 ( `=>` )입니다. 내용이 두 파일에 모두 표시 되는 줄은 표시 되지 않습니다.

```powershell
Compare-Object -ReferenceObject (Get-Content -Path C:\Test\Testfile1.txt) -DifferenceObject (Get-Content -Path C:\Test\Testfile2.txt)
```

```Output
InputObject SideIndicator
----------- -------------
cat         =>
racoon      =>
dog         <=
squirrel    <=
```

### 예제 2-콘텐츠의 각 줄 비교 및 차이점 제외

이 예제에서는 **Excludedifferent** 매개 변수를 사용 하 여 두 텍스트 파일의 각 내용 줄을 비교 합니다.

PowerShell 7.1을 기준으로 **Excludedifferent** 매개 변수를 사용 하는 경우 **includeequal** 가 유추 되 고 출력에 두 파일에 **포함 된 줄** 만 포함 됩니다 ( `==` ).

```powershell
$objects = @{
  ReferenceObject = (Get-Content -Path C:\Test\Testfile1.txt)
  DifferenceObject = (Get-Content -Path C:\Test\Testfile2.txt)
}
Compare-Object @objects -ExcludeDifferent
```

```Output
InputObject SideIndicator
----------- -------------
bird        ==
```

<a id="ex3" />

### 예 3-PassThru 매개 변수를 사용 하는 경우의 차이점 표시

일반적으로는 `Compare-Object` 다음 속성을 사용 하 여 **PSCustomObject** 형식을 반환 합니다.

- 비교할 **InputObject** 입니다.
- 출력이 속한 입력 개체를 표시 하는가 중 **표시기** 속성

**PassThru** 매개 변수를 사용 하는 경우 개체의 **형식은** 변경 되지 않지만 반환 되는 개체의 인스턴스에는 ' 이름 ' 이라는 추가 된 **참고 속성이** **있습니다.** 나란히 **표시기** 는 출력이 속한 입력 개체를 표시 합니다.

다음 예에서는 다양 한 출력 형식을 보여 줍니다.

```powershell
$a = $True
Compare-Object -IncludeEqual $a $a
(Compare-Object -IncludeEqual $a $a) | Get-Member
```

```Output
InputObject SideIndicator
----------- -------------
       True ==

   TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
InputObject   NoteProperty System.Boolean InputObject=True
SideIndicator NoteProperty string SideIndicator===
```

```powershell
Compare-Object -IncludeEqual $a $a -PassThru
(Compare-Object -IncludeEqual $a $a -PassThru) | Get-Member
```

```Output
True

   TypeName: System.Boolean
Name          MemberType   Definition
----          ----------   ----------
CompareTo     Method       int CompareTo(System.Object obj), int CompareTo(bool value), int IComparable.CompareTo(Syst
Equals        Method       bool Equals(System.Object obj), bool Equals(bool obj), bool IEquatable[bool].Equals(bool ot
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
GetTypeCode   Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean     Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte        Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar        Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime    Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal     Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble      Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16       Method       short IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32       Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64       Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte       Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle      Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString      Method       string ToString(), string ToString(System.IFormatProvider provider), string IConvertible.To
ToType        Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16      Method       ushort IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32      Method       uint IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64      Method       ulong IConvertible.ToUInt64(System.IFormatProvider provider)
TryFormat     Method       bool TryFormat(System.Span[char] destination, [ref] int charsWritten)
SideIndicator NoteProperty string SideIndicator===
```

**PassThru** 를 사용 하는 경우 원래 개체 형식 (**system.string)이 반환 됩니다.** System.string 개체의 기본 형식으로 표시 된 출력에는 함께 표시 된 **표시기** 속성이 표시 **되지 않습니다.** 그러나 반환 된 system.string 개체에는 추가 된 **참고 속성이** **있습니다.**

### 예제 4-속성을 사용 하 여 두 개의 단순 개체 비교

이 예제에서는 길이가 같은 두 개의 서로 다른 문자열을 비교 합니다.

```powershell
Compare-Object -ReferenceObject 'abc' -DifferenceObject 'xyz' -Property Length -IncludeEqual
```

```Output
Length SideIndicator
------ -------------
     3 ==
```

### 예 5: 속성을 사용 하 여 복합 개체 비교

이 예제에서는 복합 개체를 비교할 때의 동작을 보여 줍니다. 이 예에서는 PowerShell의 각 인스턴스에 대해 서로 다른 두 개의 프로세스 개체를 저장 합니다. 두 변수에 모두 동일한 이름의 프로세스 개체가 포함 되어 있습니다. **속성** 매개 변수를 지정 하지 않고 개체를 비교할 때 cmdlet은 개체가 동일한 것으로 간주 합니다. **InputObject** 값은 **ToString ()** 메서드의 결과와 동일 합니다. **System.object** 클래스는 **IComparable** 인터페이스를 포함 하지 않으므로 cmdlet은 개체를 문자열로 변환 하 고 결과를 비교 합니다.

```powershell
PS> Get-Process pwsh

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    101   123.32     139.10      35.81   11168   1 pwsh
     89   107.55      66.97      11.44   17600   1 pwsh

PS> $a = Get-Process -Id 11168
PS> $b = Get-Process -Id 17600
PS> $a.ToString()
System.Diagnostics.Process (pwsh)
PS> $b.ToString()
System.Diagnostics.Process (pwsh)
PS> Compare-Object $a $b -IncludeEqual

InputObject                       SideIndicator
-----------                       -------------
System.Diagnostics.Process (pwsh) ==

PS> Compare-Object $a $b -Property ProcessName, Id, CPU

ProcessName    Id       CPU SideIndicator
-----------    --       --- -------------
pwsh        17600   11.4375 =>
pwsh        11168 36.203125 <=
```

비교할 속성을 지정 하는 경우 cmdlet에서 차이점을 보여 줍니다.

### 예 6-IComparable을 구현 하는 복잡 한 개체 비교

개체가 **IComparable** 을 구현 하는 경우이 cmdlet은 개체를 비교 하는 방법을 검색 합니다. 개체가 다른 유형인 경우 **차이** 개체가 **referenceobject** 의 형식으로 변환 된 다음 비교 됩니다.

이 예제에서는 문자열을 **TimeSpan** 개체와 비교 합니다. 첫 번째 경우에는 문자열이 **TimeSpan** 으로 변환 되므로 개체가 동일 합니다.

```powershell
Compare-Object ([TimeSpan]"0:0:1") "0:0:1" -IncludeEqual
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    ==
```

```powershell
Compare-Object "0:0:1" ([TimeSpan]"0:0:1")
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    =>
0:0:1       <=
```

두 번째 경우에는 **TimeSpan** 이 문자열로 변환 되어 개체가 달라 집니다.

## 매개 변수

### -CaseSensitive

비교할 때 대/소문자를 구분해야 함을 나타냅니다.

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

### -문화권

비교할 때 사용할 문화권을 지정합니다.

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

### -DifferenceObject

**참조** 개체와 비교할 개체를 지정 합니다.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ExcludeDifferent

이 cmdlet이 같은 비교 개체의 특성만 표시 함을 나타냅니다. 개체 간의 차이점은 무시 됩니다.

**Includeequal** 와 함께 **excludedifferent** 사용 하 여 **참조** 와 **차이점** 개체 사이에 일치 하는 선만 표시 합니다.

**Includeequal** 없이 **excludedifferent** 가 지정 된 경우에는 출력이 없습니다.

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

### -IncludeEqual

**Includeequal** 는 **참조** 와 **차이점** 개체 간의 일치 항목을 표시 합니다.

기본적으로 출력에는 **참조** 와 **차이점** 개체 간의 차이점이 포함 됩니다.

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

### -PassThru

**PassThru** 매개 변수를 사용 하는 경우는 `Compare-Object` 비교 된 개체 주위의 **PSCustomObject** 래퍼를 생략 하 고 다른 개체는 변경 되지 않은 상태로 반환 합니다.

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

### -속성

비교할 **참조** 및 **차이점** 개체의 속성 배열을 지정 합니다.

**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다. 계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다. 유효한 키-값 쌍은 다음과 같습니다.

- 식 `<string>` 또는 `<script block>`

자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferenceObject

비교를 위해 참조로 사용 되는 개체의 배열을 지정 합니다.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SyncWindow

`Compare-Object`개체의 컬렉션에서 일치 하는 항목을 찾는 동안 검사 하는 인접 개체의 수를 지정 합니다. `Compare-Object` 컬렉션의 동일한 위치에서 개체를 찾을 수 없는 경우 인접 개체를 검사 합니다. 기본값은입니다 `[Int32]::MaxValue` . 즉, `Compare-Object` 전체 개체 컬렉션을 검사 합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: [Int32]::MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

파이프라인에서 **DifferenceObject** 매개 변수로 개체를 보낼 수 있습니다.

## 출력

### 없음

**참조** 개체와 **차이점** 개체가 같으면 **includeequal** 매개 변수를 사용 하지 않는 한 출력이 없습니다.

### PSCustomObject.

개체가 다른 경우는 차이점을 `Compare-Object` `PSCustomObject` 참조 하기 위해 함께 사용 **표시기** 속성을 사용 하 여 다른 개체를 래퍼로 래핑합니다.

**PassThru** 매개 변수를 사용 하는 경우 개체의 **형식은** 변경 되지 않지만 반환 되는 개체의 인스턴스에는 ' 이름 ' 이라는 추가 된 **참고 속성이** **있습니다.** 나란히 **표시기** 는 출력이 속한 입력 개체를 표시 합니다.

## 참고

**PassThru** 매개 변수를 사용 하는 경우 콘솔에 표시 되는 출력에는 외부 **표시기** 속성이 포함 되지 않을 수 있습니다. 에서 출력 하는 개체 형식에 대 한의 기본 형식 뷰에는 외부 `Compare-Object` **표시기** 속성이 포함 되지 않습니다. 자세한 내용은이 문서의 [예제 3](#ex3) 을 참조 하세요.

## 관련 링크

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)

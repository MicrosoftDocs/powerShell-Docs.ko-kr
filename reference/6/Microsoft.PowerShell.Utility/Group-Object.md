---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/group-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Group-Object
ms.openlocfilehash: f430dd1f9d9f820dda88ba5ad40023650204604d
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219394"
---
# Group-Object

## 개요
지정한 속성에 대해 같은 값이 있는 개체를 그룹화합니다.

## SYNTAX

### 테이블

```
Group-Object [-NoElement] [-AsHashTable] [-AsString] [-InputObject <PSObject>]
 [[-Property] <Object[]>] [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## 설명

`Group-Object`Cmdlet은 지정 된 속성의 값을 기준으로 개체를 그룹으로 표시 합니다.
`Group-Object` 각 속성 값에 대해 하나의 행이 있는 테이블을 반환 하 고 해당 값을 가진 항목 수를 표시 하는 열을 반환 합니다.

둘 이상의 속성을 지정 하는 경우 먼저 `Group-Object` 첫 번째 속성의 값을 기준으로 그룹화 한 다음 각 속성 그룹 내에서 다음 속성의 값을 기준으로 그룹화 합니다.

## 예제

### 예제 1: 확장명으로 파일 그룹화

이 예제에서는 파일을 재귀적으로 가져와 `$PSHOME` 파일 이름 확장명 별로 그룹화 합니다. 출력은 cmdlet으로 전송 됩니다 `Sort-Object` .이 cmdlet은 지정 된 확장에 대해 발견 된 카운트 파일을 기준으로 출력을 정렬 합니다. 빈 **이름은** 디렉터리를 나타냅니다.

이 예제에서는 **Noelement** 매개 변수를 사용 하 여 그룹의 멤버를 생략 합니다.

```powershell
$files = Get-ChildItem -Path $PSHOME -Recurse
$files | Group-Object -Property extension -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  365 .xml
  231 .cdxml
  197
  169 .ps1xml
  142 .txt
  114 .psd1
   63 .psm1
   49 .xsd
   36 .dll
   15 .mfl
   15 .mof
...
```

### 예제 2: 영향을 받은 것과 같은 방식으로 정수 그룹화

이 예제에서는 스크립트 블록을 **Property** 매개 변수의 값으로 사용 하는 방법을 보여 줍니다. 이 명령은 1에서 20 사이의 정수를 표시 합니다.

```powershell
1..20 | Group-Object -Property {$_ % 2}
```

```Output
Count Name                      Group
----- ----                      -----
   10 0                         {2, 4, 6, 8...}
   10 1                         {1, 3, 5, 7...}
```

### 예 3: Entrytype 관련이에서 이벤트 로그 이벤트 그룹화

이 예에서는 시스템 이벤트 로그에 **entrytype 관련이** 별로 그룹화 된 가장 최근의 1000 항목을 표시 합니다.

출력에서 **Count** 열은 각 그룹의 항목 수를 나타냅니다. **이름** 열은 그룹을 정의 하는 **EventType** 값을 나타냅니다. **그룹** 열은 각 그룹의 개체를 나타냅니다.

```powershell
Get-WinEvent -LogName System -MaxEvents 1000 | Group-Object -Property LevelDisplayName
```

```Output
Count Name          Group
----- ----          -----
  153 Error         {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  722 Information   {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  125 Warning       {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
```

### 예제 4: 우선 순위 클래스 별로 프로세스 그룹화

이 예제에서는 **Noelement** 매개 변수의 효과를 보여 줍니다. 이 명령은 우선 순위 클래스를 기준으로 컴퓨터의 프로세스를 그룹화합니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Process` 컴퓨터의 프로세스를 가져온 후 해당 개체를 파이프라인으로 보냅니다. `Group-Object`프로세스의 **PriorityClass** 속성 값을 기준으로 개체를 그룹화 합니다.

두 번째 예제에서는 **Noelement** 매개 변수를 사용 하 여 출력에서 그룹의 멤버를 제거 합니다. 결과는 **Count** 및 **Name** 속성 값만 있는 테이블입니다.

결과는 다음과 같은 샘플 출력에 표시됩니다.

```powershell
Get-Process | Group-Object -Property PriorityClass
```

```Output
Count Name         Group
----- ----         -----
   55 Normal       {System.Diagnostics.Process (AdtAgent), System.Diagnosti...
    1              {System.Diagnostics.Process (Idle)}
    3 High         {System.Diagnostics.Process (Newproc), System.Diagnostic...
    2 BelowNormal  {System.Diagnostics.Process (winperf),
```

```powershell
Get-Process | Group-Object -Property PriorityClass -NoElement
```

```Output
Count Name
----- ----
   55 Normal
    1
    3 High
    2 BelowNormal
```

### 예 5: 이름별로 프로세스 그룹화

다음 예에서는 `Group-Object` 를 사용 하 여 로컬 컴퓨터에서 실행 중인 프로세스의 여러 인스턴스를 그룹화 합니다. `Where-Object` 둘 이상의 인스턴스가 있는 프로세스를 표시 합니다.

```powershell
Get-Process | Group-Object -Property Name -NoElement | Where-Object {$_.Count -gt 1}
```

```Output
Count Name
----- ----
2     csrss
5     svchost
2     winlogon
2     wmiprvse
```

### 예 6: 해시 테이블의 개체 그룹화

이 예에서는 **ashashtable** 및 **asstring** 매개 변수를 사용 하 여 해시 테이블의 그룹을 키-값 쌍의 컬렉션으로 반환 합니다.

그 결과로 생성되는 해시 테이블에서 각 속성 값은 키이고 그룹 요소는 값입니다.
각 키는 해시 테이블 개체의 속성이므로 점 표기법으로 값을 표시할 수 있습니다.

첫 번째 명령은 `Get` 세션에서 및 cmdlet을 가져오고, 동사로 그룹화 하 `Set` 고, 그룹을 해시 테이블로 반환 하 고, 해시 테이블을 변수에 저장 합니다 `$A` .

두 번째 명령은의 해시 테이블을 표시 합니다 `$A` . `Get`Cmdlet 및 cmdlet에 대해 하나씩 두 개의 키-값 쌍이 있습니다 `Set` .

세 번째 명령은 점 표기법을 사용 하 여 `$A.Get` 의 **Get** 키 값을 표시 합니다 `$A` . 값은 **Cmdletinfo** 개체입니다. **Asstring** 매개 변수는 그룹의 개체를 문자열로 변환 하지 않습니다.

```powershell
$A = Get-Command Get-*, Set-* -CommandType cmdlet | Group-Object -Property Verb -AsHashTable -AsString
$A
```

```Output
Name     Value
----     -----
Get      {Get-Acl, Get-Alias, Get-AppLockerFileInformation, Get-AppLockerPolicy...}
Set      {Set-Acl, Set-Alias, Set-AppBackgroundTaskResourcePolicy, Set-AppLockerPolicy...}
```

```powershell
$A.Get
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Cmdlet          Get-Acl                            6.1.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-Alias                          6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-AuthenticodeSignature          6.1.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-ChildItem                      6.1.0.0    Microsoft.PowerShell.Management
...
```

## PARAMETERS

### -AsHashTable

이 cmdlet이 그룹을 해시 테이블로 반환 함을 나타냅니다. 해시 테이블의 키는 개체를 그룹화하는 기준인 속성 값입니다. 해시 테이블의 값은 속성 값을 포함하는 개체입니다.

기본적으로 **ashashtable** 매개 변수는 각 키가 그룹화 된 개체의 인스턴스인 각 해시 테이블을 반환 합니다. **Asstring** 매개 변수와 함께 사용 하는 경우 해시 테이블의 키는 문자열입니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: AHT

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsString

이 cmdlet이 해시 테이블 키를 문자열로 변환 함을 나타냅니다. 기본적으로 해시 테이블 키는 그룹화된 개체의 인스턴스입니다. 이 매개 변수는 **Ashashtable** 매개 변수와 함께 사용 하는 경우에만 유효 합니다.

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

### -CaseSensitive

이 cmdlet을 통해 대/소문자를 구분 하 여 그룹화 함을 나타냅니다. 이 매개 변수를 사용하지 않으면 그룹에 포함된 개체 속성 값의 대/소문자가 달라질 수 있습니다.

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

문자열을 비교할 때 사용할 문화권을 지정합니다.

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

### -InputObject

그룹화할 개체를 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

**InputObject** 매개 변수를 사용 하 여 개체의 컬렉션을에 제출 하면는 `Group-Object` 컬렉션을 `Group-Object` 나타내는 개체 하나를 수신 합니다. 따라서 해당 개체가 포함된 단일 그룹을 멤버로 만듭니다.

컬렉션에 있는 개체를 그룹화 하려면 개체를로 파이프 `Group-Object` 합니다.

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

### -NoElement

이 cmdlet이 결과에서 그룹의 멤버를 생략 함을 나타냅니다.

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

그룹화할 속성을 지정합니다. 개체는 지정된 속성의 값을 기반으로 하여 그룹으로 정렬됩니다.

**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다. 계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다. 유효한 키-값 쌍은 다음과 같습니다.

- 식 `<string>` 또는 `<script block>`

자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

모든 개체를로 파이프 할 수 있습니다 `Group-Object` .

## 출력

### GroupInfo 또는 System.object. 해시 테이블

**Ashashtable** 매개 변수를 사용 하는 경우는 `Group-Object` **Hashtable** 개체를 반환 합니다.
그렇지 않으면 **GroupInfo** 개체를 반환 합니다.

## 참고

서식 지정 cmdlet의 **GroupBy** 매개 변수 (예: 및)를 `Format-Table` 사용 `Format-List` 하 여 개체를 그룹화 할 수 있습니다. `Group-Object`각 속성 값에 대 한 행이 포함 된 단일 테이블을 만드는와는 달리, **GroupBy** 매개 변수는 속성 값이 있는 각 항목에 대 한 행이 포함 된 각 속성 값에 대 한 테이블을 만듭니다.

`Group-Object` 그룹화 중인 개체가 동일한 Microsoft .NET 코어 유형인 경우를 필요로 하지 않습니다. 다른 .NET Core 형식의 개체를 그룹화 하는 경우는 `Group-Object` 다음 규칙을 사용 합니다.

- 동일한 속성 이름 및 형식입니다.

  개체에 지정 된 이름을 가진 속성이 있고 속성 값이 동일한 .NET Core 유형인 경우 속성 값은 동일한 유형의 개체에 사용 되는 것과 동일한 규칙을 사용 하 여 그룹화 됩니다.

- 동일한 속성 이름, 다른 형식

  개체에 지정 된 이름의 속성이 있지만 속성 값에 다른 개체의 .NET Core 형식이 있는 경우 `Group-Object` 는 처음 발견 되는 속성의 .Net core 형식을 해당 속성 그룹의 .Net core 형식으로 사용 합니다. 개체에 유형이 다른 속성이 있으면 속성 값은 해당 그룹의 유형으로 변환됩니다. 형식 변환에 실패 하면 개체가 그룹에 포함 되지 않습니다.

- 속성이 없습니다.

  지정 된 속성이 없는 개체는 그룹화 할 수 없습니다. 그룹화 되지 않은 개체는 라는 그룹의 최종 **GroupInfo** 개체 출력에 표시 `AutomationNull.Value` 됩니다.

## 관련 링크

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

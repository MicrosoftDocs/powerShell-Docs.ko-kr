---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-table?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Table
ms.openlocfilehash: 1a90bfada7a21da24cd41ae2ceb8920f13c17c5d
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219465"
---
# Format-Table

## 개요
출력 형식을 테이블로 지정합니다.

## SYNTAX

### 모두

```
Format-Table [-AutoSize] [-RepeatHeader] [-HideTableHeaders] [-Wrap] [[-Property] <Object[]>]
 [-GroupBy <Object>] [-View <String>] [-ShowError] [-DisplayError] [-Force] [-Expand <String>]
 [-InputObject <PSObject>] [<CommonParameters>]
```

## 설명

`Format-Table`Cmdlet은 각 열에서 개체의 선택 된 속성을 사용 하 여 명령 출력의 형식을 지정 합니다. 개체 유형은 각 열에 표시 되는 기본 레이아웃 및 속성을 결정 합니다. **Property** 매개 변수를 사용 하 여 표시할 속성을 선택할 수 있습니다.

PowerShell은 기본 포맷터를 사용 하 여 개체 유형을 표시 하는 방법을 정의 합니다. 파일을 사용 하 여 `.ps1xml` 지정 된 속성의 출력 테이블을 표시 하는 사용자 지정 보기를 만들 수 있습니다. 사용자 지정 뷰를 만든 후 **view** 매개 변수를 사용 하 여 사용자 지정 보기와 함께 테이블을 표시 합니다. 보기에 대 한 자세한 내용은 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)을 참조 하세요.

해시 테이블을 사용 하 여 개체를 표시 하기 전에 개체에 계산 된 속성을 추가 하 고 테이블에 열 머리글을 지정할 수 있습니다. 계산 된 속성을 추가 하려면 **property** 또는 **GroupBy** 매개 변수를 사용 합니다. 해시 테이블에 대한 자세한 내용은 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)를 참조하세요.

## 예제

### 예제 1: PowerShell 호스트 포맷

이 예에서는 테이블의 PowerShell에 대 한 호스트 프로그램 정보를 표시 합니다.

```powershell
Get-Host | Format-Table -AutoSize
```

`Get-Host`Cmdlet은 호스트를 나타내는 **system.web** .. n a m. 개체는 파이프라인에서로 전송 되 `Format-Table` 고 테이블에 표시 됩니다. **AutoSize** 매개 변수는 잘림을 최소화 하도록 열 너비를 조정 합니다.

### 예제 2: BasePriority로 프로세스 서식 지정

이 예제에서는 동일한 **Basepriority** 속성이 있는 그룹에 프로세스를 표시 합니다.

```powershell
Get-Process | Sort-Object -Property BasePriority | Format-Table -GroupBy BasePriority -Wrap
```

`Get-Process`Cmdlet은 컴퓨터의 각 프로세스를 나타내는 개체를 가져와 파이프라인에서로 보냅니다 `Sort-Object` . 개체는 **Basepriority** 속성의 순서 대로 정렬 됩니다.

정렬 된 개체는 파이프라인에서로 전송 됩니다 `Format-Table` . **GroupBy** 매개 변수는 **basepriority** 속성의 값을 기준으로 프로세스 데이터를 그룹으로 정렬 합니다. **Wrap** 매개 변수는 데이터가 잘리지 않도록 합니다.

### 예 3: 시작 날짜별로 프로세스 서식 지정

이 예에서는 컴퓨터에서 실행 중인 프로세스에 대 한 정보를 표시 합니다. 개체는 정렬 되 고 `Format-Table` 뷰를 사용 하 여 개체를 시작 날짜별로 그룹화 합니다.

```powershell
Get-Process | Sort-Object StartTime | Format-Table -View StartTime
```

`Get-Process` 컴퓨터에서 실행 중인 프로세스를 나타내는 **시스템 진단** 개체를 가져옵니다. 개체는 파이프라인에서로 전송 되 `Sort-Object` 고 **StartTime** 속성을 기준으로 정렬 됩니다.

정렬 된 개체는 파이프라인에서로 전송 됩니다 `Format-Table` . **View** 매개 변수는 PowerShell 파일에서 system.object에 대해 정의 된 **StartTime** 뷰를 지정 합니다. `DotNetTypes.format.ps1xml` **System.Diagnostics.Process** **StartTime** 보기는 각 프로세스 시작 시간을 간단한 날짜로 변환한 다음 시작 날짜별로 프로세스를 그룹화 합니다.

파일에는 `DotNetTypes.format.ps1xml` 프로세스에 대 한 **우선 순위** 보기가 포함 되어 있습니다. `format.ps1xml`사용자 지정 보기를 사용 하 여 파일을 직접 만들 수 있습니다.

### 예 4: 테이블 출력에 사용자 지정 보기 사용

이 예제에서 사용자 지정 보기에는 디렉터리의 내용이 표시 됩니다. 사용자 지정 뷰는에서 만든 **system.io.directoryinfo** 및 CreationTime 개체에 **대 한 테이블** 출력에 **CreationTime** 열을 추가 합니다 `Get-ChildItem` .

이 예제의 사용자 지정 보기는 PowerShell 소스 코드에 정의 된 뷰에서 만들었습니다. 이 예제의 뷰를 만드는 데 사용 되는 뷰 및 코드에 대 한 자세한 내용은 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view)을 참조 하세요.

```powershell
Get-ChildItem  -Path C:\Test | Format-Table -View mygciview
```

```Output
    Directory: C:\Test

Mode                LastWriteTime              CreationTime         Length Name
----                -------------              ------------         ------ ----
d-----        11/4/2019     15:54       9/24/2019     15:54                Archives
d-----        8/27/2019     14:22       8/27/2019     14:22                Drawings
d-----       10/23/2019     09:38       2/25/2019     09:38                Files
-a----        11/7/2019     11:07       11/7/2019     11:07          11345 Alias.txt
-a----        2/27/2019     15:15       2/27/2019     15:15            258 alias_out.txt
-a----        2/27/2019     15:16       2/27/2019     15:16            258 alias_out2.txt
```

`Get-ChildItem` 현재 디렉터리의 콘텐츠를 가져옵니다 `C:\Test` . **System.io.directoryinfo** 및 **system.object** 개체는 파이프라인으로 전송 됩니다.
`Format-Table`**view** 매개 변수를 사용 하 여 **CreationTime** 열을 포함 하는 사용자 지정 뷰 **mygciview** 를 지정 합니다.

`Format-Table`에 대 한 기본 출력에는 `Get-ChildItem` **CreationTime** 열이 포함 되지 않습니다.

### 예 5: 테이블 출력에 속성 사용

이 예에서는 **Property** 매개 변수를 사용 하 여 **Name** 및 **DependentServices** 속성을 표시 하는 두 열로 된 테이블에 모든 컴퓨터의 서비스를 표시 합니다.

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

`Get-Service` 컴퓨터의 모든 서비스를 가져오고 **ServiceController** 개체를 파이프라인 아래로 보냅니다. `Format-Table`**Property** 매개 변수를 사용 하 여 **Name** 및 **DependentServices** 속성이 테이블에 표시 되도록 지정 합니다.

**Name** 및 **DependentServices** 는 개체 형식의 속성 중 두 가지입니다. 모든 `Get-Service | Get-Member -MemberType Properties` 속성을 보려면:

### 예제 6: 프로세스의 형식을 지정 하 고 실행 시간 계산

이 예에서는 로컬 컴퓨터의 **메모장** 프로세스에 대 한 프로세스 이름과 총 실행 시간이 있는 테이블을 표시 합니다. 총 실행 시간은 현재 시간에서 각 프로세스의 시작 시간을 빼서 계산합니다.

```powershell
Get-Process notepad |
  Format-Table ProcessName, @{Label="TotalRunningTime"; Expression={(Get-Date) - $_.StartTime}}
```

```Output
ProcessName TotalRunningTime
----------- ----------------
notepad     03:20:00.2751767
notepad     00:00:16.7710520
```

`Get-Process` 모든 로컬 컴퓨터의 **메모장** 프로세스를 가져오고 개체를 파이프라인으로 보냅니다. `Format-Table`**ProcessName** , `Get-Process` 속성 및 **TotalRunningTime** (계산 된 속성)의 두 열이 포함 된 테이블을 표시 합니다.

**TotalRunningTime** 속성은 **Label** 과 **Expression** 이라는 두 개의 키가 있는 해시 테이블에 의해 지정 됩니다. **레이블** 키는 속성 이름을 지정 합니다. **식** 키는 계산을 지정 합니다. 식은 각 프로세스 개체의 **StartTime** 속성을 가져온 다음 `Get-Date` 현재 날짜 및 시간을 가져오는 명령의 결과에서 뺍니다.

### 예 7: 메모장 프로세스 서식 지정

이 예에서는 `Get-CimInstance` 를 사용 하 여 로컬 컴퓨터에 있는 모든 **메모장** 프로세스의 실행 시간을 가져옵니다. `Get-CimInstance` **ComputerName** 매개 변수와 함께를 사용 하 여 원격 컴퓨터에서 정보를 가져올 수 있습니다.

```powershell
$Processes = Get-CimInstance -Class win32_process -Filter "name='notepad.exe'"
$Processes | Format-Table ProcessName, @{ Label = "Total Running Time"; Expression={(Get-Date) - $_.CreationDate}}
```

```Output
ProcessName Total Running Time
----------- ------------------
notepad.exe 03:39:39.6260693
notepad.exe 00:19:56.1376922
```

`Get-CimInstance`**notepad.exe** 이라는 모든 로컬 컴퓨터의 프로세스를 설명 하는 WMI **Win32_Process** 클래스의 인스턴스를 가져옵니다. 프로세스 개체는 변수에 저장 됩니다 `$Processes` .

변수의 프로세스 개체는 `$Processes` `Format-Table` **ProcessName** 속성 및 새 계산 된 속성 ( **총 실행 시간** )을 표시 하는 파이프라인으로 전송 됩니다.

이 명령은 새 계산 속성의 이름 ( **총 실행 시간** )을 **레이블** 키에 할당 합니다. **식** 키의 스크립트 블록은 현재 날짜에서 프로세스 만든 날짜를 빼서 프로세스 실행 시간을 계산 합니다. `Get-Date`Cmdlet은 현재 날짜를 가져옵니다. 만든 날짜를 현재 날짜에서 뺍니다. 결과는 **총 실행 시간** 값입니다.

### 예 8: 형식 오류 문제 해결

다음 예에서는 식을 사용 하 여 **displayerror** 또는 **showerror** 매개 변수를 추가 하는 결과를 보여 줍니다.

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -DisplayError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday #ERR
```

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -ShowError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday

InvalidArgument: Failed to evaluate expression " $_ / $null ".
```

## PARAMETERS

### -AutoSize

Cmdlet이 데이터의 너비에 따라 열 크기 및 열 수를 조정 함을 나타냅니다. 기본적으로 열 크기 및 수는 뷰에 따라 결정됩니다.

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

### -DisplayError

Cmdlet이 명령줄에 오류를 표시 함을 나타냅니다. 이 매개 변수는 명령에서 식의 형식을 지정할 때 `Format-Table` 식의 문제를 해결 해야 하는 경우 디버깅 도구로 사용할 수 있습니다.

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

### -확장

컬렉션 개체의 형식 및 컬렉션의 개체를 지정 합니다. 이 매개 변수는 [ICollection](/dotnet/api/system.collections.icollection) ([system.object](/dotnet/api/system.collections)) 인터페이스를 지 원하는 개체의 형식을 지정 하도록 디자인 되었습니다. 기본값은 **Enumonly** 입니다.
이 매개 변수에 허용 되는 값은 다음과 같습니다.

- **Enumonly** : 컬렉션에 있는 개체의 속성을 표시 합니다.
- **CoreOnly** : 컬렉션 개체의 속성을 표시 합니다.
- **Both** : 컬렉션 개체의 속성과 컬렉션에 있는 개체의 속성을 표시 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Cmdlet이 모든 오류 정보를 표시 하도록 cmdlet에 지시 함을 나타냅니다. **Displayerror** 또는 **showerror** 매개 변수와 함께 사용 합니다. 기본적으로 오류 또는 표시 스트림에 오류 개체를 쓰는 경우 일부 오류 정보만 표시됩니다.

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

### -GroupBy

속성 값에 따라 별도의 테이블에 정렬 된 출력을 지정 합니다. 예를 들어 **GroupBy** 를 사용 하 여 해당 상태에 따라 별도의 테이블에 서비스를 나열할 수 있습니다.

식 또는 속성을 입력 합니다. **GroupBy** 매개 변수는 개체가 정렬 되어 있어야 합니다.
`Sort-Object`를 사용 하기 전에 cmdlet을 사용 하 여 `Format-Table` 개체를 그룹화 합니다.

**GroupBy** 매개 변수 값은 새 계산 된 속성 일 수 있습니다. 계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다. 유효한 키-값 쌍은 다음과 같습니다.

- 이름 (또는 레이블)- `<string>`
- 식 `<string>` 또는 `<script block>`
- FormatString `<string>`

자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HideTableHeaders

테이블에서 열 머리글을 생략합니다.

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

### -InputObject

형식을 지정할 개체를 지정 합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

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

### -속성

표시에 나타나는 개체 속성 및 표시되는 순서를 지정합니다. 하나 이상의 속성 이름을 쉼표로 구분 하 여 입력 하거나 해시 테이블을 사용 하 여 계산 된 속성을 표시 합니다. 와일드카드가 지원됩니다.

이 매개 변수를 생략 하는 경우 표시에 표시 되는 속성은 첫 번째 개체의 속성에 따라 달라 집니다. 예를 들어 첫 번째 개체에 **propertya** 및 **propertya** 가 있지만 후속 개체에 **propertya** , **propertya** 및 **propertya** 가 있는 경우 **propertya** 및 **propertya** 머리글만 표시 됩니다.

**Property** 매개 변수는 선택 사항입니다. 동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.

**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다. 계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다. 유효한 키-값 쌍은 다음과 같습니다.

- 이름 (또는 레이블) `<string>`
- 식 `<string>` 또는 `<script block>`
- FormatString `<string>`
- Width- `<int32>` -다음 보다 커야 함 `0`
- 맞춤-값은 `Left` , `Center` 또는 일 수 있습니다. `Right`

자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -RepeatHeader

모든 화면이 가득 찬 후 테이블의 머리글을 표시 합니다. 반복 되는 헤더는 출력이 `less` 또는 `more` 화면 판독기를 사용 하 여 페이징과 같이 페이저에 파이프 되는 경우에 유용 합니다.

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

### -ShowError

이 매개 변수는 파이프라인을 통해 오류를 보냅니다. 이 매개 변수는 명령에서 식의 형식을 지정할 때 `Format-Table` 식의 문제를 해결 해야 하는 경우 디버깅 도구로 사용할 수 있습니다.

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

### -보기

PowerShell 6 부터는 기본 보기가 PowerShell 소스 코드에 정의 되어 `C#` 있습니다. Powershell `*.format.ps1xml` 5.1 이전 버전의 파일은 powershell 6 이상 버전에 없습니다.

**View** 매개 변수를 사용 하 여 테이블에 대 한 대체 형식 또는 사용자 지정 뷰를 지정할 수 있습니다. 기본 PowerShell 뷰를 사용 하거나 사용자 지정 보기를 만들 수 있습니다. 사용자 지정 보기를 만드는 방법에 대 한 자세한 내용은 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)을 참조 하세요.

**View** 매개 변수에 대 한 대체 및 사용자 지정 뷰에서는 테이블 형식을 사용 해야 합니다. 그렇지 않으면이 `Format-Table` 실패 합니다. 대체 뷰가 목록이 면 cmdlet을 사용 합니다 `Format-List` . 대체 뷰가 목록이 나 테이블이 아닌 경우 cmdlet을 사용 합니다 `Format-Custom` .

동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.

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

### -Wrap

다음 줄에 열 너비를 초과하는 텍스트를 표시합니다. 기본적으로 열 너비를 초과하는 텍스트는 잘립니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

파이프라인에서 모든 개체를로 보낼 수 있습니다 `Format-Table` .

## 출력

### Microsoft. PowerShell. Internal. Format

`Format-Table` 테이블을 나타내는 형식 개체를 반환 합니다.

## 참고

## 관련 링크

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[Export-FormatData](Export-FormatData.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Wide](Format-Wide.md)

[Get-FormatData](Get-FormatData.md)

[Get-Member](Get-Member.md)

[Get-CimInstance](../CimCmdlets/Get-CimInstance.md)

[Update-FormatData](Update-FormatData.md)

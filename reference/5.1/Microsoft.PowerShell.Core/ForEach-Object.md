---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 327add884077083d37e1f58ab8f78b784a870362
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "93219881"
---
# ForEach-Object

## 개요
입력 개체 컬렉션에 있는 각 항목에 대해 작업을 수행합니다.

## 구문

### ScriptBlockSet (기본값)

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PropertyAndMethodSet

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## Description

`ForEach-Object`Cmdlet은 입력 개체 컬렉션의 각 항목에 대해 작업을 수행 합니다. 입력 개체를 cmdlet으로 파이프 하거나 **InputObject** 매개 변수를 사용 하 여 지정할 수 있습니다.

Windows PowerShell 3.0부터 명령을 생성 하는 방법에는 두 가지가 있습니다 `ForEach-Object` .

- **스크립트 블록** 입니다. 스크립트 블록을 사용하여 작업을 지정할 수 있습니다. 스크립트 블록 내에서 변수를 사용 `$_` 하 여 현재 개체를 나타냅니다. 스크립트 블록은 **Process** 매개 변수 값입니다. 스크립트 블록에는 모든 PowerShell 스크립트가 포함 될 수 있습니다.

  예를 들어 다음 명령은 컴퓨터에 있는 각 프로세스의 **ProcessName** 속성 값을 가져옵니다.

  `Get-Process | ForEach-Object {$_.ProcessName}`

  `ForEach-Object``begin` `process` `end` [about_functions](about/about_functions.md#piping-objects-to-functions)에 설명 된 대로, 및 블록을 지원 합니다.

  > [!NOTE]
  > 스크립트 블록은 호출자의 범위에서 실행 됩니다. 따라서 블록은 해당 범위의 변수에 액세스할 수 있으며 cmdlet이 완료 된 후 해당 범위에 유지 되는 새 변수를 만들 수 있습니다.

- **Operation 문**. 자연어와 유사한 작업 문을 작성할 수도 있습니다. 작업 문을 사용하여 속성 값을 지정하거나 메서드를 호출할 수 있습니다. 작업 문은 Windows PowerShell 3.0에서 도입되었습니다.

  예를 들어 다음 명령도 컴퓨터에 있는 각 프로세스의 **ProcessName** 속성 값을 가져옵니다.

  `Get-Process | ForEach-Object ProcessName`

## 예

### 예제 1: 배열의 정수 나누기

이 예제에서는 세 개의 정수로 이루어진 배열을 사용 하 여 각 정수를 1024으로 나눕니다.

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### 예 2: 디렉터리에 있는 모든 파일의 길이 가져오기

이 예에서는 PowerShell 설치 디렉터리의 파일 및 디렉터리를 처리 `$PSHOME` 합니다.

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

개체가 디렉터리가 아닌 경우 스크립트 블록은 파일의 이름을 가져오고, **길이** 속성의 값을 1024로 나누고, 공백 ("")을 추가 하 여 다음 항목과 구분 합니다. 이 cmdlet은 **PSISContainer** 속성을 사용 하 여 개체가 디렉터리 인지 여부를 확인 합니다.

### 예 3: 최신 시스템 이벤트에 대 한 운영

이 예제에서는 시스템 이벤트 로그의 최신 이벤트 1000을 텍스트 파일에 기록 합니다. 현재 시간은 이벤트를 처리 하기 전과 후에 표시 됩니다.

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

`Get-EventLog` 시스템 이벤트 로그에서 1000 개의 최신 이벤트를 가져와 변수에 저장 합니다 `$Events` . `$Events` 가 cmdlet으로 파이프 됩니다 `ForEach-Object` . **Begin** 매개 변수는 현재 날짜와 시간을 표시합니다. 그런 다음 **Process** 매개 변수는 cmdlet을 사용 하 여 `Out-File` events.txt 라는 텍스트 파일을 만들고 해당 파일에 있는 각 이벤트의 메시지 속성을 저장 합니다. 마지막으로, **End** 매개 변수는 모든 처리가 완료된 후 날짜와 시간을 표시하는 데 사용됩니다.

### 예제 4: 레지스트리 키 값 변경

이 예에서는 키 아래의 모든 하위 키에 있는 **RemotePath** 레지스트리 항목의 값을 `HKCU:\Network` 대문자 텍스트로 변경 합니다.

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

이 형식을 사용하여 레지스트리 항목 값의 형식이나 내용을 변경할 수 있습니다.

**Network** 키의 각 하위 키는 로그온 시 다시 연결할 매핑된 네트워크 드라이브를 나타냅니다.
**RemotePath** 항목에는 연결된 드라이브의 UNC 경로가 포함됩니다. 예를 들어 E: 드라이브를에 매핑하면 `\\Server\Share` 의 **e** 하위 키가 `HKCU:\Network` 있으며 **e** 하위 키에 있는 **RemotePath** 레지스트리 항목의 값은입니다 `\\Server\Share` .

이 명령은 cmdlet을 사용 하 여 `Get-ItemProperty` **네트워크** 키의 모든 하위 키를 가져오고 cmdlet을 사용 하 여 `Set-ItemProperty` 각 키에서 **RemotePath** 레지스트리 항목의 값을 변경 합니다.
명령에서 `Set-ItemProperty` 경로는 레지스트리 키의 **PSPath** 속성 값입니다. 레지스트리 항목이 아니라 레지스트리 키를 나타내는 Microsoft .NET Framework 개체의 속성입니다. 이 명령은 문자열 (REG_SZ) 인 **RemotePath** 값의 **ToUpper ()** 메서드를 사용 합니다.

`Set-ItemProperty`는 각 키의 속성을 변경 하기 때문에 `ForEach-Object` 속성에 액세스 하려면 cmdlet이 필요 합니다.

### 예 5: $Null 자동 변수 사용

이 예에서는 `$Null` cmdlet에 자동 변수를 파이프 하는 결과를 보여 줍니다 `ForEach-Object` .

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

PowerShell은 null을 명시적 자리 표시자로 처리 하기 때문에 `ForEach-Object` 이 cmdlet은 `$Null` 파이프 하는 다른 개체와 마찬가지로에 대 한 값을 생성 합니다.

### 예제 6: 속성 값 가져오기

이 예에서는 cmdlet의 **MemberName** 매개 변수를 사용 하 여 설치 된 모든 PowerShell 모듈의 **Path** 속성 값을 가져옵니다 `ForEach-Object` .

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

두 번째 명령은 첫 번째 명령과 같습니다. `Foreach`Cmdlet의 별칭을 사용 하 `ForEach-Object` 고 **MemberName** 매개 변수 (선택 사항)의 이름을 생략 합니다.

Cmdlet은 속성 값 `ForEach-Object` 형식을 변경 하는 **Format** cmdlet 또는 cmdlet과 달리 형식을 변경 하지 않고 값을 가져오기 때문에 속성 값을 가져오는 데 매우 유용 합니다 `Select-Object` .

### 예 7: 모듈 이름을 구성 요소 이름으로 분할

이 예제에서는 점으로 구분 된 두 개의 모듈 이름을 해당 구성 요소 이름으로 분할 하는 세 가지 방법을 보여 줍니다.

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

명령에서 문자열의 **Split** 메서드를 호출합니다. 세 명령은 서로 다른 구문을 사용하지만 동일하며 교환해서 사용할 수 있습니다.

첫 번째 명령은 스크립트 블록과 현재 개체 연산자를 포함 하는 일반적인 구문을 사용 합니다 `$_` . 점 구문을 사용하여 메서드를 지정하고 괄호를 사용하여 구분 기호 인수를 묶습니다.

두 번째 명령은 **MemberName** 매개 변수를 사용하여 **Split** 메서드를 지정하고 **ArgumentName** 매개 변수를 사용하여 점(".")을 분할 구분 기호로 식별합니다.

세 번째 명령은 cmdlet의 **Foreach** 별칭을 사용 하 `ForEach-Object` 고 **MemberName** 및 **argumentlist** 매개 변수의 이름을 생략 합니다 (선택 사항).

### 예 8: 두 스크립트 블록을 사용 하 여 ForEach-Object 사용

이 예제에서는 메서드에 액세스할 스크립트 블록 두 개를 전달 합니다. 모든 스크립트 블록은 **Process** 매개 변수에 바인딩됩니다. 그러나 **Begin** 및 **Process** 매개 변수에 전달 된 것 처럼 처리 됩니다.

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### 예제 9: 두 개 이상의 스크립트 블록을 사용 하 여 ForEach-Object 사용

이 예제에서는 메서드에 액세스할 스크립트 블록 두 개를 전달 합니다. 모든 스크립트 블록은 **Process** 매개 변수에 바인딩됩니다. 그러나 **Begin** , **Process** 및 **End** 매개 변수에 전달 된 것 처럼 처리 됩니다.

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> 첫 번째 스크립트 블록은 항상 블록에 매핑되고 `begin` , 마지막 블록은 블록에 매핑되고 `end` , between의 블록은 모두 블록에 매핑됩니다 `process` .

### 예 10: 각 파이프라인 항목에 대해 여러 스크립트 블록 실행

위의 예제와 같이 **Process** 매개 변수를 사용 하 여 전달 된 여러 스크립트 블록은 **Begin** 및 **End** 매개 변수에 매핑됩니다. 이 매핑을 방지 하려면 **Begin** 및 **End** 매개 변수에 대 한 명시적 값을 제공 해야 합니다.

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

## 매개 변수

### -ArgumentList

메서드 호출에 대 한 인수 배열을 지정 합니다. **Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)를 참조 하세요.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Begin

이 cmdlet이 입력 개체를 처리 하기 전에 실행 되는 스크립트 블록을 지정 합니다. 이 스크립트 블록은 전체 파이프라인에 대해 한 번만 실행 됩니다. 블록에 대 한 자세한 내용은 `begin` [about_Functions](about/about_functions.md#piping-objects-to-functions)를 참조 하세요.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -끝

이 cmdlet이 모든 입력 개체를 처리 한 후 실행 되는 스크립트 블록을 지정 합니다. 이 스크립트 블록은 전체 파이프라인에 대해 한 번만 실행 됩니다. 블록에 대 한 자세한 내용은 `end` [about_Functions](about/about_functions.md#piping-objects-to-functions)를 참조 하세요.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

입력 개체를 지정합니다. `ForEach-Object` 각 입력 개체에 대해 스크립트 블록 또는 작업 문을 실행 합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

에 **inputobject** 매개 변수를 사용 하는 경우 `ForEach-Object` 명령 결과를로 파이프 하는 대신 `ForEach-Object` **inputobject** 값은 단일 개체로 처리 됩니다. 이는 값이 명령 결과인 컬렉션 (예:) 인 경우에도 마찬가지입니다 `-InputObject (Get-Process)` .
**InputObject** 는 배열 또는 개체 컬렉션의 개별 속성을 반환할 수 없으므로를 사용 `ForEach-Object` 하 여 정의 된 속성에 특정 값이 있는 개체의 개체 컬렉션에 대 한 작업을 수행 하는 경우 `ForEach-Object` 이 항목의 예제에 나와 있는 것 처럼 파이프라인에서를 사용 하는 것이 좋습니다.

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

### -MemberName

가져올 속성이나 호출할 메서드를 지정합니다.

와일드 카드 문자를 사용할 수 있지만 결과 문자열이 고유한 값으로 확인 되는 경우에만 작동 합니다.
예를 들어를 실행 하는 경우 `Get-Process | ForEach -MemberName *Name` **ProcessName** 및 **Name** 속성과 같이 문자열 이름을 포함 하는 이름으로 두 개 이상의 멤버가 있으면 명령이 실패 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Process

각 입력 개체에 대해 수행되는 작업을 지정합니다. 이 스크립트 블록은 파이프라인의 모든 개체에 대해 실행 됩니다. 블록에 대 한 자세한 내용은 `process` [about_Functions](about/about_functions.md#piping-objects-to-functions)를 참조 하세요.

**프로세스** 매개 변수에 여러 스크립트 블록을 제공 하는 경우 첫 번째 스크립트 블록은 항상 블록에 매핑됩니다 `begin` . 두 개의 스크립트 블록만 있는 경우 두 번째 블록은 블록에 매핑됩니다 `process` . 스크립트 블록이 3 개 이상 있는 경우 첫 번째 스크립트 블록은 항상 블록에 매핑되고 `begin` , 마지막 블록은 블록에 매핑되고, `end` 사이에 있는 블록은 모두 블록에 매핑됩니다 `process` .

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemainingScripts

**Process** 매개 변수에서 사용 하지 않는 모든 스크립트 블록을 지정 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
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

### System.web. PSObject

모든 개체를이 cmdlet으로 파이프 할 수 있습니다.

## outputs

### System.web. PSObject

이 cmdlet은 입력에 의해 결정 되는 개체를 반환 합니다.

## 메모

- 이 cmdlet은 foreach 문과 `ForEach-Object` 매우 **Foreach** 유사 하 게 작동 합니다. 단, **foreach** 문에는 입력을 파이프 하지 않아도 됩니다. **Foreach** 문에 대 한 자세한 내용은 [about_Foreach](./About/about_Foreach.md)를 참조 하세요.

- PowerShell 4.0부터 `Where` `ForEach` 컬렉션과 함께 사용 하기 위해 메서드가 추가 되었습니다. 이러한 새 메서드에 대 한 자세한 내용은 여기를 참조 하세요 [about_arrays](./About/about_Arrays.md)

## 관련 링크

[Compare-Object](../Microsoft.PowerShell.Utility/Compare-Object.md)

[Where-Object](Where-Object.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Measure-Object](../Microsoft.PowerShell.Utility/Measure-Object.md)

[New-Object](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sort-Object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Tee-Object](../Microsoft.PowerShell.Utility/Tee-Object.md)

---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: e05c9b5e44d26b1e16c82f734ec60ca4cc73ab4d
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "93219898"
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

### ParallelParameterSet

```
ForEach-Object -Parallel <scriptblock> [-InputObject <PSObject>] [-ThrottleLimit <int>]
[-UseNewRunspace] [-TimeoutSeconds <int>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
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

- **병렬 실행 스크립트 블록** 입니다. PowerShell 7.0부터 각 스크립트 블록을 병렬로 실행 하는 세 번째 매개 변수 집합을 사용할 수 있습니다. **ThrottleLimit** 매개 변수는 한 번에 실행 되는 병렬 스크립트의 수를 제한 합니다. 이전 처럼 변수를 사용 `$_` 하 여 스크립트 블록의 현재 입력 개체를 나타냅니다. 키워드를 사용 `$using:` 하 여 실행 중인 스크립트에 변수 참조를 전달 합니다.

  PowerShell 7에서 최대 격리를 보장 하기 위해 각 루프 반복에 대 한 새 runspace가 만들어집니다.
  이는 새 runspace를 만드는 것과 비교 하 여 수행 하는 작업의 양이 적거나, 많은 작업이 많은 반복이 발생 하는 경우 성능이 저하 될 수 있습니다. PowerShell 7.1을 기준으로 runspace 풀에서 runspace는 기본적으로 다시 사용 됩니다. Runspace 풀 크기는 **ThrottleLimit** 매개 변수로 지정 됩니다. 기본 runspace 풀 크기는 5입니다. **UseNewRunspace** 스위치를 사용 하 여 각 반복에 대해 새 runspace를 만들 수 있습니다.

  기본적으로 병렬 scriptblocks은 병렬 작업을 시작한 호출자의 현재 작업 디렉터리를 사용 합니다.

  종료 되지 않는 오류는 scriptblocks를 병렬로 실행 하는 경우에 발생 하므로 cmdlet 오류 스트림에 기록 됩니다. 병렬 scriptblock 실행 순서를 확인할 수 없기 때문에 오류 스트림에 오류가 표시 되는 순서는 임의적입니다. 마찬가지로, 경고, 자세한 정보 표시 또는 정보와 같은 다른 데이터 스트림에 기록 된 메시지는 해당 데이터 스트림에 확정 되지 않은 순서로 기록 됩니다.

  예외와 같은 종료 오류는 발생 하는 scriptblocks의 개별 병렬 인스턴스를 종료 합니다. 하나의 scriptblocks에서 종료 오류가 발생 하면 cmdlet이 종료 되지 않을 수 있습니다 `Foreach-Object` . 동시에 실행 되는 다른 scriptblocks는 종료 오류가 발생 하지 않는 한 계속 실행 됩니다. 종료 오류는 **FullyQualifiedErrorId** 가 인 **ErrorRecord** 으로 오류 데이터 스트림에 기록 됩니다 `PSTaskException` .
  PowerShell try/catch 또는 트랩 블록을 사용 하 여 종료 오류를 종료 되지 않는 오류로 변환할 수 있습니다.

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

**네트워크** 키의 각 하위 키는 로그온 할 때 다시 연결 되는 매핑된 네트워크 드라이브를 나타냅니다. **RemotePath** 항목에는 연결된 드라이브의 UNC 경로가 포함됩니다. 예를 들어 E: 드라이브를에 매핑하면 `\\Server\Share` **e** 하위 키가에 생성 되 `HKCU:\Network` 고 **RemotePath** 레지스트리 값이로 설정 됩니다 `\\Server\Share` .

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

Cmdlet은 속성 값 `ForEach-Object` 형식을 변경 하는 **Format** cmdlet 또는 cmdlet과 달리 형식을 변경 하지 않고 값을 가져오기 때문에 속성 값을 가져오는 데 유용 합니다 `Select-Object` .

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

### 예 11: 병렬 일괄 처리에서 느림 스크립트 실행

이 예에서는 문자열을 계산 하 고 1 초 동안 대기 하는 간단한 스크립트 블록을 실행 합니다.

```powershell
$Message = "Output:"

1..8 | ForEach-Object -Parallel {
    "$using:Message $_"
    Start-Sleep 1
} -ThrottleLimit 4
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
```

**ThrottleLimit** 매개 변수 값은 4로 설정 되므로 입력이 4 개의 일괄 처리로 처리 됩니다.
`$using:`키워드는 `$Message` 각 병렬 스크립트 블록에 변수를 전달 하는 데 사용 됩니다.

### 예 12: 병렬로 로그 항목 검색

이 예제에서는 로컬 Windows 컴퓨터에 있는 5 개의 시스템 로그에서 5만 로그 항목을 검색 합니다.

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count
```

```Output
50000
```

**Parallel** 매개 변수는 각 입력 로그 이름에 대해 병렬로 실행되는 스크립트 블록을 지정합니다. **ThrottleLimit** 매개 변수를 사용 하면 5 개의 스크립트 블록이 모두 동시에 실행 됩니다.

### 예제 13: 작업으로 병렬로 실행

이 예제에서는 간단한 스크립트 블록을 병렬로 실행 하 여 한 번에 두 개의 백그라운드 작업을 만듭니다.

```powershell
$job = 1..10 | ForEach-Object -Parallel {
    "Output: $_"
    Start-Sleep 1
} -ThrottleLimit 2 -AsJob

$job | Receive-Job -Wait
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
Output: 9
Output: 10
```

`$job`변수는 출력 데이터를 수집 하 고 실행 상태를 모니터링 하는 작업 개체를 받습니다.
작업 개체는 `Receive-Job` **Wait** 스위치 매개 변수를 사용 하 여로 파이프 됩니다. 이 스트림은 `ForEach-Object -Parallel` **AsJob** 없이 실행 된 것 처럼 콘솔에 출력 됩니다.

### 예제 14: 스레드로부터 안전한 변수 참조 사용

이 예에서는 고유 하 게 명명 된 프로세스 개체를 수집 하기 위해 스크립트 블록을 병렬로 호출 합니다.

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
Get-Process | ForEach-Object -Parallel {
    $dict = $using:threadSafeDictionary
    $dict.TryAdd($_.ProcessName, $_)
}

$threadSafeDictionary["pwsh"]
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     82    82.87     130.85      15.55    2808   2 pwsh
```

**ConcurrentDictionary** 개체의 단일 인스턴스는 각 스크립트 블록에 전달 되어 개체를 수집 합니다. **ConcurrentDictionary** 은 스레드로부터 안전 하기 때문에 각 병렬 스크립트에 의해 안전 하 게 수정 됩니다. **System.object** 와 같은 스레드로부터 안전 하지 않은 개체는 여기에서 사용 하기에 안전 하지 않습니다.

> [!NOTE]
> 이 예에서는 **병렬** 매개 변수를 매우 비효율적으로 사용 합니다. 스크립트는 단순히 입력 개체를 동시 사전 개체에 추가 합니다. 별도의 스레드에서 각 스크립트를 호출 하는 오버 헤드가 중요 하지 않습니다. `ForEach-Object` **병렬** 스위치 없이 정상적으로 실행 하는 것이 훨씬 더 효율적이 고 빠릅니다. 이 예제는 스레드 안전 변수를 사용 하는 방법을 보여 주기 위한 것입니다.

### 예 15: 병렬 실행으로 오류 작성

이 예제에서는 기록 된 오류의 순서가 무작위로 오류 스트림에 동시에 씁니다.

```powershell
1..3 | ForEach-Object -Parallel {
    Write-Error "Error: $_"
}
```

```Output
Write-Error: Error: 1
Write-Error: Error: 3
Write-Error: Error: 2
```

### 예 16: 병렬 실행에서 오류 종료

이 예제에서는 하나의 병렬 실행 scriptblock에서 종료 오류를 보여 줍니다.

```powershell
1..5 | ForEach-Object -Parallel {
    if ($_ -eq 3)
    {
        throw "Terminating Error: $_"
    }

    Write-Output "Output: $_"
}
```

```Output
Exception: Terminating Error: 3
Output: 1
Output: 4
Output: 2
Output: 5
```

`Output: 3` 해당 반복에 대 한 병렬 scriptblock이 종료 되었기 때문에 작성 되지 않습니다.

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
예를 들어를 실행 하 `Get-Process | ForEach -MemberName *Name` 는 경우 와일드 카드 패턴은 두 개 이상의 멤버와 일치 하므로 명령이 실패 합니다.

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

### -Parallel

입력 개체의 병렬 처리에 사용할 스크립트 블록을 지정 합니다. 작업을 설명하는 스크립트 블록을 입력합니다.

이 매개 변수는 PowerShell 7.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ParallelParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

병렬로 스크립트 블록 수를 지정 합니다. 입력 개체는 실행 중인 스크립트 블록 수가 **ThrottleLimit** 아래로 떨어질 때까지 차단 됩니다. 기본값은 `5`입니다.

이 매개 변수는 PowerShell 7.0에서 도입 되었습니다.

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSeconds

모든 입력이 병렬로 처리 될 때까지 대기 하는 시간 (초)을 지정 합니다. 지정 된 제한 시간 후에는 실행 중인 모든 스크립트가 중지 됩니다. 그리고 처리할 나머지 모든 입력 개체는 무시 됩니다. 의 기본값 `0` 은 시간 제한을 사용 하지 않도록 설정 하 고 `ForEach-Object -Parallel` 무기한 실행 될 수 있습니다. 명령줄에서 <kbd>Ctrl</kbd> + <kbd>C</kbd> 를 입력 하면 실행 중인 `ForEach-Object -Parallel` 명령이 중지 됩니다. 이 매개 변수는 **AsJob** 매개 변수와 함께 사용할 수 없습니다.

이 매개 변수는 PowerShell 7.0에서 도입 되었습니다.

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseNewRunspace

병렬 호출이 runspace 풀에서 runspace를 다시 사용 하는 대신 모든 루프 반복에 대해 새 runspace를 만들도록 합니다.

이 매개 변수는 PowerShell 7.1에서 도입 되었습니다.

```yml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

병렬 호출이 PowerShell 작업으로 실행 되도록 합니다. 실행 중인 스크립트 블록에서 출력 하는 대신 단일 작업 개체가 반환 됩니다. 작업 개체에는를 실행 하는 각 병렬 스크립트 블록에 대 한 자식 작업이 포함 됩니다. 작업 개체는 모든 PowerShell 작업 cmdlet에서 실행 상태를 모니터링 하 고 데이터를 검색 하는 데 사용할 수 있습니다.

이 매개 변수는 PowerShell 7.0에서 도입 되었습니다.

```yaml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
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

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

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

- `ForEach-Object -Parallel`매개 변수 집합은 PowerShell의 내부 API를 사용 하 여 각 스크립트 블록을 실행 합니다. 이는 `ForEach-Object` 순차적 처리를 통해 정상적으로 실행 하는 것 보다 훨씬 더 많은 오버 헤드가 발생 합니다. 병렬로 실행 하는 오버 헤드가 스크립트 블록에서 수행 하는 작업에 비해 작은 경우 **병렬** 를 사용 하는 것이 중요 합니다. 다음은 그 예입니다. 

  - 다중 코어 컴퓨터에서 계산 집약적인 스크립트
  - 결과를 기다리거나 파일 작업을 수행 하는 데 시간을 소비 하는 스크립트

  **Parallel** 매개 변수를 사용 하면 스크립트가 평소 보다 훨씬 느리게 실행 될 수 있습니다. 특히 병렬 스크립트가 trivial 인 경우 **병렬** 로 실험 하 여 유용할 수 있는 위치를 검색 합니다.

  > [!IMPORTANT]
  > `ForEach-Object -Parallel`매개 변수 집합은 별도의 프로세스 스레드에서 스크립트 블록을 병렬로 실행 합니다. `$using:`키워드를 사용 하면 cmdlet 호출 스레드에서 실행 중인 각 스크립트 블록 스레드로 변수 참조를 전달할 수 있습니다. 스크립트 블록은 다른 스레드에서 실행 되므로 참조로 전달 되는 개체 변수를 안전 하 게 사용 해야 합니다. 일반적으로 변경 되지 않는 참조 된 개체를 읽을 수 있습니다. 하지만 개체 상태를 수정 하는 경우에는 .Net **system.object** 와 같은 스레드로부터 안전한 개체를 사용 해야 합니다 (예 11 참조).

## 관련 링크

[Compare-Object](../Microsoft.PowerShell.Utility/Compare-Object.md)

[Where-Object](Where-Object.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Measure-Object](../Microsoft.PowerShell.Utility/Measure-Object.md)

[New-Object](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sort-Object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Tee-Object](../Microsoft.PowerShell.Utility/Tee-Object.md)

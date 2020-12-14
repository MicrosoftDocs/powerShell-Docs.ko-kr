---
external help file: Microsoft.PowerShell.ThreadJob.dll-Help.xml
Locale: en-US
Module Name: ThreadJob
ms.date: 12/05/2020
online version: https://docs.microsoft.com/powershell/module/threadjob/start-threadjob?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-ThreadJob
ms.openlocfilehash: bced2b87c3843833414ebfd189d003e83af9718f
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96777750"
---
# Start-ThreadJob

## 개요
Cmdlet과 비슷한 백그라운드 작업을 만듭니다 `Start-Job` .

## SYNTAX

### ScriptBlock

```
Start-ThreadJob [-ScriptBlock] <ScriptBlock> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

### FilePath

```
Start-ThreadJob [-FilePath] <String> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

## 설명

`Start-ThreadJob` cmdlet과 비슷한 백그라운드 작업을 만듭니다 `Start-Job` . 주요 차이점은 생성 된 작업은 로컬 프로세스 내에서 별도의 스레드에서 실행 된다는 것입니다. 기본적으로 작업은 작업을 시작한 호출자의 현재 작업 디렉터리를 사용 합니다.

또한 cmdlet은 **ThrottleLimit** 매개 변수를 지원 하 여 한 번에 실행 되는 작업 수를 제한 합니다. 더 많은 작업이 시작 되 면 큐에 대기 하 고 현재 작업 수가 제한 한도 아래로 떨어질 때까지 기다립니다.

## 예제

### 예제 1-스레드 한도가 2 인 백그라운드 작업 만들기

```powershell
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } } -ThrottleLimit 2
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Get-Job
```

```Output
Id   Name   PSJobTypeName   State        HasMoreData   Location     Command
--   ----   -------------   -----        -----------   --------     -------
1    Job1   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
2    Job2   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
3    Job3   ThreadJob       NotStarted   False         PowerShell   1..100 | % { sleep 1;...
```

### 예 2-Start-Job 및 Start-ThreadJob의 성능 비교

이 예에서는와 간의 차이점을 보여 줍니다 `Start-Job` `Start-ThreadJob` . 작업은 cmdlet을 `Start-Sleep` 1 초 동안 실행 합니다. 작업은 병렬로 실행 되므로 총 실행 시간은 약 1 초 이며 작업을 만드는 데 필요한 시간을 더한 시간입니다.

```powershell
# start five background jobs each running 1 second
Measure-Command {1..5 | % {Start-Job {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
Measure-Command {1..5 | % {Start-ThreadJob {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
```

```Output
TotalSeconds
------------
   5.7665849
   1.5735008
```

실행 시간에 대해 1 초를 뺀 후 `Start-Job` 5 개의 작업을 만드는 데 약 4.8 초가 소요 될 수 있습니다. `Start-ThreadJob` 는 5 배 더 빠르며 5 개의 작업을 만드는 데 0.6 초 정도 걸립니다. 결과는 사용자 환경에서 다를 수 있지만 상대적 향상은 동일 해야 합니다.

### 예제 3-InputObject를 사용 하 여 작업 만들기

이 예에서 스크립트 블록은 변수를 사용 하 여 `$input` **InputObject** 매개 변수에서 입력을 받습니다. 개체를로 파이프 하 여이 작업을 수행할 수도 있습니다 `Start-ThreadJob` .

```powershell
$j = Start-ThreadJob -InputObject (Get-Process pwsh) -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

```powershell
$j = Get-Process pwsh | Start-ThreadJob -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

### 예제 4-부모 호스트에 작업 출력 스트림

**Streaminghost** 매개 변수를 사용 하 여 모든 호스트 출력을 특정 호스트로 보내도록 작업에 지시할 수 있습니다. 이 매개 변수를 사용 하지 않으면 출력은 작업 데이터 스트림 컬렉션으로 이동 하 고 작업에서 출력을 받을 때까지 호스트 콘솔에 표시 되지 않습니다.

이 예에서는 `Start-ThreadJob` 자동 변수를 사용 하 여 현재 호스트를 전달 합니다 `$Host` .

```powershell
PS> Start-ThreadJob -ScriptBlock { Read-Host 'Say hello'; Write-Warning 'Warning output' } -StreamingHost $Host

Id   Name   PSJobTypeName   State         HasMoreData     Location      Command
--   ----   -------------   -----         -----------     --------      -------
7    Job7   ThreadJob       NotStarted    False           PowerShell    Read-Host 'Say hello'; �

PS> Say hello: Hello
WARNING: Warning output
PS> Receive-Job -Id 7
Hello
WARNING: Warning output
PS>
```

에서 프롬프트가 `Read-Host` 표시 되 고 입력을 입력할 수 있습니다. 그런 다음에서 메시지가 `Write-Warning` 표시 됩니다. `Receive-Job`Cmdlet은 작업의 모든 출력을 반환 합니다.

## PARAMETERS

### -ArgumentList

**FilePath** 또는 **ScriptBlock** 매개 변수로 지정 된 스크립트에 대 한 인수 또는 매개 변수 값의 배열을 지정 합니다.

**Argumentlist** 는 명령줄에서 마지막 매개 변수 여야 합니다. 매개 변수 이름 다음에 오는 모든 값은 인수 목록에서 해석 되는 값입니다.

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

### -FilePath

백그라운드 작업으로 실행할 스크립트 파일을 지정 합니다. 스크립트의 경로와 파일 이름을 입력 합니다. 스크립트는 로컬 컴퓨터에 있거나 로컬 컴퓨터에서 액세스할 수 있는 폴더에 있어야 합니다.

이 매개 변수를 사용 하는 경우 PowerShell은 지정 된 스크립트 파일의 내용을 스크립트 블록으로 변환 하 고 스크립트 블록을 백그라운드 작업으로 실행 합니다.

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -또한 initializationscript

작업을 시작하기 전에 실행되는 명령을 지정합니다. 명령을 중괄호 ()로 묶어 `{}` 스크립트 블록을 만듭니다.

이 매개 변수를 사용하여 작업이 실행되는 세션을 준비할 수 있습니다. 예를 들어이를 사용 하 여 함수 및 모듈을 세션에 추가할 수 있습니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

스크립트 블록의 입력으로 사용 되는 개체를 지정 합니다. 파이프라인 입력도 허용 됩니다. `$input`스크립트 블록의 자동 변수를 사용 하 여 입력 개체에 액세스 합니다.

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

### -Name

새 작업의 이름을 지정합니다. 이 이름을 사용 하 여 cmdlet과 같은 다른 작업 cmdlet에 대 한 작업을 식별할 수 있습니다 `Stop-Job` .

기본 이름은 "Job #" 이며, 여기서 "#"은 각 작업에 대해 증가 하는 서 수입니다.

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

### -ScriptBlock

백그라운드 작업에서 실행할 명령을 지정합니다. 명령을 중괄호 ()로 묶어 `{}` 스크립트 블록을 만듭니다. `$Input`자동 변수를 사용 하 여 **InputObject** 매개 변수의 값에 액세스 합니다. 이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StreamingHost

이 매개 변수는 `Write-Host` 출력을 전달 된 **PSHost** 개체로 바로 이동할 수 있는 스레드로부터 안전한 방법을 제공 합니다. 이를 사용 하지 않으면 `Write-Host` 출력은 작업 정보 데이터 스트림 컬렉션으로 이동 하 고 작업 실행이 완료 될 때까지 호스트 콘솔에 나타나지 않습니다.

```yaml
Type: System.Management.Automation.Host.PSHost
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

이 매개 변수는 한 번에 실행 되는 작업 수를 제한 합니다. 작업이 시작 되 면 큐에 대기 하 고 스레드 풀에서 스레드를 사용 하 여 작업을 실행할 때까지 대기 합니다. 기본 제한은 5 개의 스레드입니다.

스레드 풀 크기는 PowerShell 세션의 전역입니다. 한 호출에 **ThrottleLimit** 를 지정 하면 동일한 세션에서 후속 호출에 대 한 제한이 설정 됩니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

## 출력

### ThreadJob. ThreadJob

## 참고

## 관련 링크

[Start-Job](../Microsoft.PowerShell.Core/Start-Job.md)

[Stop-Job](../Microsoft.PowerShell.Core/Stop-Job.md)

[Receive-Job](../Microsoft.PowerShell.Core/Receive-Job.md)

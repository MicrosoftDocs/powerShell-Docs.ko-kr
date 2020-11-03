---
description: PowerShell에서 텍스트 파일로 출력을 리디렉션하는 방법에 대해 설명 합니다.
keywords: PowerShell, cmdlet
Locale: en-US
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: 7e6dcadc3bcabd4dc0521a158db87ca2bba41af8
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224241"
---
# <a name="about-redirection"></a>리디렉션 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 텍스트 파일로 출력을 리디렉션하는 방법에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

기본적으로 PowerShell은 출력을 PowerShell 호스트로 보냅니다. 일반적으로 콘솔 응용 프로그램입니다. 그러나 출력을 텍스트 파일로 보낼 수 있으며, 오류 출력을 일반 출력 스트림으로 리디렉션할 수 있습니다.

다음 메서드를 사용 하 여 출력을 리디렉션할 수 있습니다.

- Cmdlet을 사용 하 여 `Out-File` 명령 출력을 텍스트 파일로 보냅니다.
  일반적으로 `Out-File` `Encoding` ,, `Force` `Width` 또는 매개 변수와 같은 매개 변수를 사용 해야 하는 경우 cmdlet을 사용 `NoClobber` 합니다.

- Cmdlet을 사용 하 여 `Tee-Object` 명령 출력을 텍스트 파일로 보내고 파이프라인으로 보냅니다.

- PowerShell 리디렉션 연산자를 사용 합니다. File 대상과 함께 리디렉션 연산자를 사용 하는 것은 추가 매개 변수 없이로 파이프 하는 것과 동일 `Out-File` 합니다.

스트림에 대 한 자세한 내용은 [about_Output_Streams](about_Output_Streams.md)를 참조 하세요.

### <a name="redirectable-output-streams"></a>리디렉션할 때 출력 스트림

PowerShell은 다음 출력 스트림의 리디렉션을 지원 합니다.

| 스트림 # |      Description       | 에 도입 됨  |    쓰기 Cmdlet     |
| -------- | ---------------------- | -------------- | ------------------- |
| 1        | **성공** 스트림     | PowerShell 2.0 | `Write-Output`      |
| 2        | **오류** 스트림       | PowerShell 2.0 | `Write-Error`       |
| 3        | **경고** 스트림     | PowerShell 3.0 | `Write-Warning`     |
| 4        | **자세한 정보** 스트림     | PowerShell 3.0 | `Write-Verbose`     |
| 5        | **디버그** 스트림       | PowerShell 3.0 | `Write-Debug`       |
| 6        | **정보** 스트림 | PowerShell 5.0 | `Write-Information` |
| *        | 모든 스트림            | PowerShell 3.0 |                     |

> [!NOTE]
> PowerShell에는 **진행률** 스트림도 있지만 리디렉션을 지원 하지 않습니다.

### <a name="powershell-redirection-operators"></a>PowerShell 리디렉션 운영자

PowerShell 리디렉션 연산자는 다음과 같습니다. 여기서은 `n` 스트림 번호를 나타냅니다. 스트림이 지정 되지 않은 경우 **성공** 스트림 ( `1` )이 기본값입니다.

| 연산자 |                         Description                         | 구문 |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | 지정 된 스트림을 파일에 보냅니다.                            | `n>`   |
| `>>`     | 지정 된 스트림을 파일에 **추가** 합니다.                      | `n>>`  |
| `>&1`    | 지정 된 스트림을 **성공** 스트림으로 _리디렉션합니다_ . | `n>&1` |

> [!NOTE]
> 일부 Unix 셸과 달리 다른 스트림은 **성공** 스트림으로만 리디렉션할 수 있습니다.

## <a name="examples"></a>예

### <a name="example-1-redirect-errors-and-output-to-a-file"></a>예제 1: 오류 및 출력을 파일로 리디렉션

이 예제는 `dir` 성공 하는 한 항목 및 오류가 발생 한 항목에서 실행 됩니다.

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

를 사용 `2>&1` 하 여 **오류** 스트림을 **성공** 스트림으로 리디렉션하고 `>` 결과 **성공** 스트림을 라는 파일로 보냅니다. `dir.log`

### <a name="example-2-send-all-success-stream-data-to-a-file"></a>예제 2: 모든 성공 스트림 데이터를 파일로 보내기

이 예에서는 라는 파일에 모든 **성공** 스트림 데이터를 보냅니다 `script.log` .

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a>예 3: 파일에 성공, 경고 및 오류 스트림 보내기

이 예에서는 리디렉션 연산자를 결합 하 여 원하는 결과를 얻을 수 있는 방법을 보여 줍니다.

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > P:\Temp\redirection.log
```

- `3>&1`**경고** 스트림을 **성공** 스트림으로 리디렉션합니다.
- `2>&1`**오류** 스트림을 **성공** 스트림으로 리디렉션합니다 (이제 모든 **경고** 스트림 데이터를 포함).
- `>`**성공** 스트림 (이제 **경고** 및 **오류** 스트림 모두 `C:\temp\redirection.log` 포함)을 라는 파일로 리디렉션합니다.

### <a name="example-4-redirect-all-streams-to-a-file"></a>예제 4: 모든 스트림을 파일로 리디렉션

이 예제에서는 라는 스크립트의 모든 스트림 출력 `script.ps1` 을 이라는 파일로 보냅니다. `script.log`

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a>예 5: 모든 Write-Host 및 정보 스트림 데이터 표시 안 함

이 예에서는 모든 정보 스트림 데이터를 표시 하지 않습니다. **정보** 스트림 cmdlet에 대 한 자세한 내용은 [쓰기-호스트](xref:Microsoft.PowerShell.Utility.Write-Host) 및 [쓰기 정보](xref:Microsoft.PowerShell.Utility.Write-Information) 를 참조 하세요.

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a>예 6: 작업 기본 설정의 효과 표시

작업 기본 설정 변수 및 매개 변수는 특정 스트림에 기록 되는 내용을 변경할 수 있습니다. 이 예제의 스크립트는의 값이 `$ErrorActionPreference` **오류** 스트림에 쓰여지는 항목에 미치는 영향을 보여 줍니다.

```powershell
$ErrorActionPreference = 'Continue'
$ErrorActionPreference > log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'SilentlyContinue'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Stop'
$ErrorActionPreference >> log.txt
Try {
    get-item /not-here 2>&1 >> log.txt
}
catch {
    "`tError caught!" >> log.txt
}
$ErrorActionPreference = 'Ignore'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Inquire'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Continue'
```

이 스크립트를 실행 하면 `$ErrorActionPreference` 가로 설정 된 경우 메시지가 표시 됩니다 `Inquire` .

```powershell
PS C:\temp> .\test.ps1

Confirm
Cannot find path 'C:\not-here' because it does not exist.
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): H
Get-Item: C:\temp\test.ps1:23
Line |
  23 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The running command stopped because the user selected the Stop option.
```

로그 파일을 검토 하면 다음이 표시 됩니다.

```
PS C:\temp> Get-Content .\log.txt
Continue

Get-Item: C:\temp\test.ps1:3
Line |
   3 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | Cannot find path 'C:\not-here' because it does not exist.

SilentlyContinue
Stop
    Error caught!
Ignore
Inquire
```

## <a name="notes"></a>메모

데이터를 추가 하지 않는 리디렉션 연산자 ( `>` 및 `n>` )는 지정 된 파일의 현재 내용을 경고 없이 덮어씁니다.

그러나 파일이 읽기 전용, 숨김 또는 시스템 파일인 경우 리디렉션이 **실패** 합니다. 추가 리디렉션 연산자 ( `>>` 및 `n>>` )는 읽기 전용 파일에 쓰지 않지만 시스템이 나 숨겨진 파일에는 콘텐츠를 추가 합니다.

콘텐츠를 읽기 전용, 숨김 또는 시스템 파일로 강제로 리디렉션할 수 있도록 하려면 cmdlet에 매개 변수를 사용 `Out-File` `Force` 합니다.

파일에 쓰는 경우 리디렉션 연산자는 `UTF8NoBOM` 인코딩을 사용 합니다. 파일의 인코딩이 다른 경우 출력의 형식이 잘못 된 것일 수 있습니다. 다른 인코딩을 사용 하 여 파일에 쓰려면 `Out-File` cmdlet에 매개 변수를 사용 `Encoding` 합니다.

### <a name="potential-confusion-with-comparison-operators"></a>비교 연산자와 혼동 될 수 있습니다.

`>`연산자는 [보다 큼](about_Comparison_Operators.md#-gt) 비교 연산자와 혼동 하지 않습니다 (종종 `>` 다른 프로그래밍 언어에서로 표시 됨).

비교 되는 개체에 따라를 사용 하는 출력은 `>` 올바른 것으로 표시 될 수 있습니다 (36가 42 보다 크지 않기 때문).

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

그러나 로컬 파일 시스템에 대 한 검사를 통해 라는 파일을 기록 하는 내용을 확인할 수 있습니다 `42` `36` .

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

역방향 비교 `<` (보다 작음)를 사용 하려고 하면 시스템 오류가 발생 합니다.

```powershell
PS> if (36 < 42) { "true" } else { "false" }
At line:1 char:8
+ if (36 < 42) { "true" } else { "false" }
+        ~
The '<' operator is reserved for future use.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : RedirectionNotSupported
```

숫자 비교가 필요한 작업 인 경우에 `-lt` 는를 `-gt` 사용 해야 합니다. 참조: [ `-gt` 비교 연산자](about_Comparison_Operators.md#-gt)

## <a name="see-also"></a>참고 항목

- [Out-File](xref:Microsoft.PowerShell.Utility.Out-File)
- [Tee-Object](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [쓰기 오류](xref:Microsoft.PowerShell.Utility.Write-Error)
- [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host)
- [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)
- [Write-Output](xref:Microsoft.PowerShell.Utility.Write-Output)
- [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [about_Output_Streams](about_Output_Streams.md)
- [about_Operators](about_Operators.md)
- [about_Command_Syntax](about_Command_Syntax.md)
- [about_Path_Syntax](about_Path_Syntax.md)

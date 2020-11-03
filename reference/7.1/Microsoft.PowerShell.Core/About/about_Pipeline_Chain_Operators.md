---
description: '`&&`PowerShell에서 및 연산자를 사용 하 여 파이프라인을 연결 하는 방법을 설명 합니다 `||` .'
ms.date: 09/30/2019
schema: 2.0.0
Locale: en-US
keywords: powershell,cmdlet
title: about_Pipeline_Chain_Operators
ms.openlocfilehash: 38895ff9acda9ead031c9be58904ac132364a584
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222026"
---
# <a name="about-pipeline-chain-operators"></a>파이프라인 체인 연산자 정보

## <a name="short-description"></a>간단한 설명

`&&`PowerShell에서 및 연산자를 사용 하 여 파이프라인을 연결 하는 방법을 설명 합니다 `||` .

## <a name="long-description"></a>자세한 설명입니다.

PowerShell 7부터 PowerShell은 `&&` 및 연산자를 구현 `||` 하 여 조건부로 파이프라인을 연결 합니다. 이러한 연산자는 PowerShell에서 *파이프라인 체인 연산자로* 알려져 있으며, bash, zsh 및 sh와 같은 POSIX 셸 [및](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) Windows 명령 셸에서의 [조건부 처리 기호](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) (cmd.exe)와 유사 합니다.

`&&` 연산자는 왼쪽 파이프라인이 성공한 경우 오른쪽 파이프라인을 실행합니다. 반대로, `||` 연산자는 왼쪽 파이프라인이 실패한 경우 오른쪽 파이프라인을 실행합니다.

이러한 연산자는 `$?` 및 `$LASTEXITCODE` 변수를 사용하여 파이프라인이 실패했는지 확인합니다. 이렇게 하면 cmdlet 또는 함수뿐만 아니라 네이티브 명령과 함께 사용할 수 있습니다. 다음은 그 예입니다.

```powershell
# Create an SSH key pair - if successful copy the public key to clipboard
ssh-keygen -t rsa -b 2048 && Get-Content -Raw ~\.ssh\id_rsa.pub | clip
```

### <a name="examples"></a>예

#### <a name="two-successful-commands"></a>두 개의 성공한 명령

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

#### <a name="first-command-fails-causing-second-not-to-be-executed"></a>첫 번째 명령이 실패 하 고 두 번째 명령이 실행 되지 않습니다.

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

#### <a name="first-command-succeeds-so-the-second-command-is-not-executed"></a>첫 번째 명령은 성공 하므로 두 번째 명령이 실행 되지 않습니다.

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

#### <a name="first-command-fails-so-the-second-command-is-executed"></a>첫 번째 명령이 실패 하므로 두 번째 명령이 실행 됩니다.

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error: Bad
Second
```

파이프라인 성공은 변수의 값으로 정의 됩니다 `$?` . PowerShell은 실행 상태에 따라 파이프라인을 실행 한 후 자동으로 설정 됩니다.
즉, 파이프라인 체인 연산자의 동일성은 다음과 같습니다.

```powershell
Test-Command '1' && Test-Command '2'
```

는와 동일 하 게 작동 합니다.

```powershell
Test-Command '1'; if ($?) { Test-Command '2' }
```

를 갖는

```powershell
Test-Command '1' || Test-Command '2'
```

는와 동일 하 게 작동 합니다.

```powershell
Test-Command '1'; if (-not $?) { Test-Command '2' }
```

### <a name="assignment-from-pipeline-chains"></a>파이프라인 체인에서 할당

파이프라인 체인에서 변수를 할당 하면 체인에 있는 모든 파이프라인이 연결 됩니다.

```powershell
$result = Write-Output '1' && Write-Output '2'
$result
```

```Output
1
2
```

파이프라인 체인에서 할당 하는 동안 스크립트 종료 오류가 발생 하면 할당에 성공 하지 않습니다.

```powershell
try
{
    $result = Write-Output 'Value' && $(throw 'Bad')
}
catch
{
    # Do nothing, just squash the error
}

"Result: $result"
```

```Output
Result:
```

### <a name="operator-syntax-and-precedence"></a>연산자 구문 및 우선 순위

예를 들어 다른 연산자와 달리 `&&` 및는 `||` 또는와 같은 식이 아니라 파이프라인에서 작동 `+` `-and` 합니다.

`&&` 및는 `||` 파이프 () `|` 또는 리디렉션 () 보다 우선 순위가 낮으므로 `>` 작업 연산자 ( `&` ), 할당 ( `=` ) 또는 세미콜론 () 보다 우선 순위가 높습니다 `;` . 즉, 파이프라인 체인 내의 파이프라인은 개별적으로 리디렉션될 수 있으며 전체 파이프라인 체인을 backgrounded 하거나 변수에 할당 하거나 문으로 구분할 수 있습니다.

파이프라인 체인 내에서 낮은 우선 순위 구문을 사용 하려면 괄호를 사용 하는 것이 좋습니다 `(...)` .
마찬가지로 파이프라인 체인 내에 문을 포함 하려면 하위 식을 `$(...)` 사용할 수 있습니다.
이는 네이티브 명령과 제어 흐름을 결합 하는 데 유용할 수 있습니다.

```powershell
foreach ($file in 'file1','file2','file3')
{
    # When find succeeds, the loop breaks
    find $file && Write-Output "Found $file" && $(break)
}
```

```Output
find: file1: No such file or directory
file2
Found file2
```

PowerShell 7을 통해 이러한 구문에 대 한 동작이 변경 되어 `$?` 괄호 또는 하위 식 내에서 명령이 성공 하거나 실패 하는 경우가 예상 대로 설정 됩니다.

PowerShell에서 대부분의 다른 연산자와 마찬가지로 `&&` 및 `||` 은 *왼쪽* 에서 그룹화 하는 것을 의미 합니다. 예를 들면 다음과 같습니다.

```powershell
Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist" && Get-Content -Raw ./file.txt
```

그룹화 할 위치:

```
[Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist"] && Get-Content -Raw ./file.txt
```

다음과 동일 합니다.

```powershell
Get-ChildItem -Path ./file.txt

if (-not $?) { Write-Error "file.txt does not exist" }

if ($?) { Get-Content -Raw ./file.txt }
```

### <a name="error-interaction"></a>오류 상호 작용

파이프라인 체인 연산자에는 오류가 발생 하지 않습니다. 파이프라인 체인의 문이 스크립트 종료 오류를 throw 하는 경우 파이프라인 체인이 종료 됩니다.

예를 들면 다음과 같습니다.

```powershell
$(throw 'Bad') || Write-Output '2'
```

```Output
Exception: Bad
```

오류가 catch 되어도 파이프라인 체인이 여전히 종료 됩니다.

```powershell
try
{
    $(throw 'Bad') || Write-Output '2'
}
catch
{
    Write-Output "Caught: $_"
}
Write-Output 'Done'
```

```Output
Caught: Bad
Done
```

오류가 종료 되지 않거나 파이프라인을 종료 하는 경우 파이프라인 체인은 다음 값을 준수 합니다 `$?` .

```powershell
function Test-NonTerminatingError
{
    [CmdletBinding()]
    param()

    $exception = [System.Exception]::new('BAD')
    $errorId = 'BAD'
    $errorCategory = 'NotSpecified'

    $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

    $PSCmdlet.WriteError($errorRecord)
}

Test-NonTerminatingError || Write-Output 'Second'
```

```Output
Test-NonTerminatingError: BAD
Second
```

### <a name="chaining-pipelines-rather-than-commands"></a>명령 대신 파이프라인 연결

파이프라인 체인 연산자는 이름을 기준으로 하 여 단순히 명령만이 아니라 파이프라인을 연결 하는 데 사용할 수 있습니다. 이는 다른 셸의 동작과 일치 하지만 *성공을* 확인 하기 어려울 수 있습니다.

```powershell
function Test-NotTwo
{
    [CmdletBinding()]
    param(
      [Parameter(ValueFromPipeline)]
      $Input
    )

    process
    {
        if ($Input -ne 2)
        {
            return $Input
        }

        $exception = [System.Exception]::new('Input is 2')
        $errorId = 'InputTwo'
        $errorCategory = 'InvalidData'

        $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

        $PSCmdlet.WriteError($errorRecord)
    }
}

1,2,3 | Test-NotTwo && Write-Output 'All done!'
```

```Output
1
Test-NotTwo : Input is 2
3
```

가 `Write-Output 'All done!'` `Test-NotTwo` 종료 되지 않는 오류를 생성 한 후에 실패 한 것으로 간주 되므로이 실행 되지 않습니다.

## <a name="see-also"></a>참고 항목

- [about_Operators](about_Operators.md)
- [about_Automatic_Variables](about_Automatic_Variables.md)
- [about_pipelines](about_pipelines.md)


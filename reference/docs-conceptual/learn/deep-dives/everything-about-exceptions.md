---
title: 예외에 대해 알고 싶은 모든 것
description: 코드 작성에서 오류 처리는 일상적인 일입니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 3ecb1669fa8d58bc742d4e8e77051b3ace4452a0
ms.sourcegitcommit: 4a40e3ea3601c02366be3495a5dcc7f4cac9f1ea
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84337185"
---
# <a name="everything-you-wanted-to-know-about-exceptions"></a>예외에 대해 알고 싶은 모든 것

코드 작성에서 오류 처리는 일상적인 일입니다. 예상되는 동작에 대한 조건을 자주 확인하고 검사할 수 있습니다. 예기치 않은 상황이 발생하면 예외 처리로 전환됩니다. 다른 사용자의 코드에서 생성한 예외를 쉽게 처리하거나 다른 사용자가 처리할 예외를 직접 생성할 수 있습니다.

> [!NOTE]
> 이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다. PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다. [PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.

## <a name="basic-terminology"></a>기본 용어

이 주제를 살펴보기 전에 먼저 몇 가지 기본적인 용어를 살펴봐야 합니다.

### <a name="exception"></a>예외

예외는 일반적인 오류 처리로는 문제를 처리할 수 없을 때 생성되는 이벤트와 비슷합니다.
예외를 생성하는 대표적인 예는 숫자를 0으로 나누려고 하거나 메모리가 부족한 상황입니다. 사용 중인 코드 작성자가 특정 문제 발생 시 예외를 생성하기도 합니다.

### <a name="throw-and-catch"></a>Throw 및 Catch

예외가 발생하면 예외가 throw되었다고 표현합니다. Throw된 예외를 처리하려면 예외를 catch해야 합니다. 예외가 throw되고 어떻게든 catch되지 않으면 스크립트 실행이 중지됩니다.

### <a name="the-call-stack"></a>호출 스택

호출 스택은 서로를 호출한 함수 목록입니다. 호출된 함수는 스택이나 목록 맨 위에 추가됩니다. 함수는 종료되거나 반환되면 스택에서 제거됩니다.

예외가 throw되면 관련 호출 스택을 확인해 예외 처리기가 예외를 catch합니다.

### <a name="terminating-and-non-terminating-errors"></a>종료 또는 종료되지 않는 오류

예외 대부분 종료 오류입니다. Throw된 예외를 catch하지 않으면 현재 실행이 종료됩니다. 기본적으로 종료되지 않는 오류는 `Write-Error`에 의해 생성되며, 예외를 throw하지 않고 출력 스트림에 오류를 추가합니다.

이 점을 강조하는 이유는 `Write-Error` 및 다른 종료되지 않는 오류는 `catch`를 트리거하지 않기 때문입니다.

### <a name="swallowing-an-exception"></a>예외 받아들이기

오류를 단순히 무시하기 위해 catch하는 작업입니다. 문제 해결이 대단히 어려워질 수 있으니 이 작업은 주의해서 진행해야 합니다.

## <a name="basic-command-syntax"></a>기본 명령 구문

다음은 PowerShell에서 사용하는 기본 예외 처리 구문에 관한 간략한 개요입니다.

### <a name="throw"></a>Throw

자체 예외 이벤트를 만들려면 `throw` 키워드로 예외를 throw합니다.

```powershell
function Start-Something
{
    throw "Bad thing happened"
}
```

종료 오류인 런타임 예외가 생성됩니다. 호출 함수에서 `catch`로 처리하지 않으면 다음과 비슷한 메시지와 함께 스크립트가 종료됩니다.

```powershell
PS> Start-Something

Bad thing happened
At line:1 char:1
+ throw "Bad thing happened"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (Bad thing happened:String) [], RuntimeException
    + FullyQualifiedErrorId : Bad thing happened
```

#### <a name="write-error--erroraction-stop"></a>Write-Error -ErrorAction Stop

앞에서 `Write-Error`는 기본적으로 종료 오류를 throw하지 않는다고 했죠. `-ErrorAction Stop`을 지정하면 `Write-Error`는 `catch`로 처리할 수 있는 종료 오류를 생성합니다.

```powershell
Write-Error -Message "Houston, we have a problem." -ErrorAction Stop
```

이 방법으로 `-ErrorAction Stop`을 사용할 수 있음을 알려준 Lee Daily에게 감사의 말을 전합니다.

#### <a name="cmdlet--erroraction-stop"></a>Cmdlet -ErrorAction Stop

고급 함수 또는 cmdlet에 `-ErrorAction Stop`을 지정하면 모든 `Write-Error` 문이 실행을 중지하거나 `catch`로 처리할 수 있는 종료 오류로 바뀝니다.

```powershell
Start-Something -ErrorAction Stop
```

### <a name="trycatch"></a>Try/Catch

PowerShell로 (그리고 다른 많은 언어로) 오류 처리 수행할 때 사용자는 먼저 코드 일부를 `try`한 다음 오류가 throw되면 `catch`합니다. 다음은 이에 관한 간단한 예제입니다.

```powershell
try
{
    Start-Something
}
catch
{
    Write-Output "Something threw an exception"
}

try
{
    Start-Something -ErrorAction Stop
}
catch
{
    Write-Output "Something threw an exception or used Write-Error"
}
```

`catch` 스크립트는 종료 오류가 있을 때만 실행됩니다. `try`가 올바르게 실행된다면 `catch`는 건너뜁니다.

### <a name="tryfinally"></a>Try/Finally

오류를 처리할 필요는 없지만 예외 발생 여부에 따라 코드를 실행해야 할 때도 있습니다. `finally` 스크립트는 바로 이 작업을 수행합니다.

이 예제를 살펴보세요.

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
$command.Connection.Open()
$command.ExecuteNonQuery()
$command.Connection.Close()
```

리소스를 열거나 연결했다면 항상 해당 리소스를 닫아야 합니다. `ExecuteNonQuery()`에서 예외를 throw한다면 연결이 닫히지 않았다는 뜻입니다. 다음은 `try/finally` 블록에 있는 동일한 코드입니다.

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
try
{
    $command.Connection.Open()
    $command.ExecuteNonQuery()
}
finally
{
    $command.Connection.Close()
}
```

이 예제에서는 오류가 있다면 연결이 닫힙니다. 오류가 없어도 연결은 닫힙니다. `finally` 스크립트는 매번 실행됩니다.

여러분이 예외를 catch하지 않기 때문에 여전히 호출 스택으로 전파됩니다.

### <a name="trycatchfinally"></a>Try/Catch/Finally

`catch`와 `finally`를 함께 사용해도 됩니다. 대부분의 경우 하나만 사용하지만 두 가지를 모두 사용하는 시나리오도 있습니다.

## <a name="psitem"></a>$PSItem

이제 기본 사항을 확인했으니 좀 더 자세한 내용을 살펴보겠습니다.

`catch` 블록에는 예외 관련 세부 정보를 포함하는 `ErrorRecord` 유형의 자동 변수(`$PSItem`또는 `$_`)가 있습니다. 다음은 몇 가지 주요 속성에 대한 간략한 개요입니다.

예제에서는 이 예외를 생성하기 위해 `ReadAllText`에 잘못된 경로를 사용했습니다.

```powershell
[System.IO.File]::ReadAllText( '\\test\no\filefound.log')
```

### <a name="psitemtostring"></a>PSItem.ToString()

로깅 및 일반 출력에 사용할 가장 깔끔한 메시지입니다. `ToString()`은 `$PSItem`이 문자열 안에 배치되면 자동으로 호출됩니다.

```powershell
catch
{
    Write-Output "Ran into an issue: $($PSItem.ToString())"
}

catch
{
    Write-Output "Ran into an issue: $PSItem"
}
```

### <a name="psiteminvocationinfo"></a>$PSItem.InvocationInfo

이 속성은 예외가 throw된 함수 또는 스크립트에 대해 PowerShell에서 수집한 추가 정보를 포함합니다. 다음은 제가 만든 샘플 예외의 `InvocationInfo`입니다.

```powershell
PS> $PSItem.InvocationInfo | Format-List *

MyCommand             : Get-Resource
BoundParameters       : {}
UnboundArguments      : {}
ScriptLineNumber      : 5
OffsetInLine          : 5
ScriptName            : C:\blog\throwerror.ps1
Line                  :     Get-Resource
PositionMessage       : At C:\blog\throwerror.ps1:5 char:5
                        +     Get-Resource
                        +     ~~~~~~~~~~~~
PSScriptRoot          : C:\blog
PSCommandPath         : C:\blog\throwerror.ps1
InvocationName        : Get-Resource
```

중요 세부 정보에서 `ScriptName`, 코드 `Line`과 호출이 시작된 `ScriptLineNumber`를 확인할 수 있습니다.

### <a name="psitemscriptstacktrace"></a>$PSItem.ScriptStackTrace

이 속성은 예외가 생성된 코드를 알려주는 함수 호출의 순서를 보여줍니다.

```powershell
PS> $PSItem.ScriptStackTrace
at Get-Resource, C:\blog\throwerror.ps1: line 13
at Start-Something, C:\blog\throwerror.ps1: line 5
at <ScriptBlock>, C:\blog\throwerror.ps1: line 18
```

저는 동일한 스크립트에 있는 함수를 호출하지만 여러 스크립트가 관련된다면 호출을 추적할 수도 있습니다.

### <a name="psitemexception"></a>$PSItem.Exception

Throw된 실제 예외입니다.

#### <a name="psitemexceptionmessage"></a>$PSItem.Exception.Message

예외를 설명해주며 훌륭한 문제 해결 출발점인 일반 메시지입니다. 대부분의 예외에는 기본 메시지가 있지만 예외가 throw될 때 표시할 사용자 지정 메시지를 설정할 수도 있습니다.

```powershell
PS> $PSItem.Exception.Message

Exception calling "ReadAllText" with "1" argument(s): "The network path was not found."
```

이 메시지는 `ErrorRecord`에 설정하지 않았다면 `$PSItem.ToString()`을 호출할 때 반환되는 메시지이기도 합니다.

#### <a name="psitemexceptioninnerexception"></a>$PSItem.Exception.InnerException

예외는 내부 예외를 포함할 수 있습니다. 호출하는 코드가 예외를 catch하고 다른 예외를 throw할 때 자주 발생합니다. 원래 예외는 새 예외 안에 배치됩니다.

```powershell
PS> $PSItem.Exception.InnerExceptionMessage
The network path was not found.
```

이 주제는 예외를 다시 throw하는 방법을 설명할 때 다시 살펴보겠습니다.

#### <a name="psitemexceptionstacktrace"></a>$PSItem.Exception.StackTrace

예외에 대한 `StackTrace`입니다. 앞에서 `ScriptStackTrace`를 보여드렸지만, $PSItem.Exception.StackTrace는 관리 코드 호출에 사용합니다.

```Output
at System.IO.FileStream.Init(String path, FileMode mode, FileAccess access, Int32 rights, Boolean
 useRights, FileShare share, Int32 bufferSize, FileOptions options, SECURITY_ATTRIBUTES secAttrs,
 String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean checkHost)
at System.IO.FileStream..ctor(String path, FileMode mode, FileAccess access, FileShare share, Int32
 bufferSize, FileOptions options, String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean
 checkHost)
at System.IO.StreamReader..ctor(String path, Encoding encoding, Boolean detectEncodingFromByteOrderMarks,
 Int32 bufferSize, Boolean checkHost)
at System.IO.File.InternalReadAllText(String path, Encoding encoding, Boolean checkHost)
at CallSite.Target(Closure , CallSite , Type , String )
```

관리 코드에서 이벤트가 throw될 때만 이 스택 추적을 가져옵니다. .NET framework 함수를 직접 호출했기 때문에 이 예제에서 이것밖에 볼 수 없습니다. 일반적으로 스택 추적을 확인할 때는 코드가 중단된 지점과 시스템 호출이 시작된 지점을 확인합니다.

## <a name="working-with-exceptions"></a>예외 처리 작업

예외는 기본 구문 및 예외 속성만으로 구성되지 않습니다.

### <a name="catching-typed-exceptions"></a>형식화된 예외 catch

Catch할 예외를 선택할 수 있습니다. 예외에는 형식이 있으며 사용자는 catch할 예외의 형식을 지정할 수 있습니다.

```powershell
try
{
    Start-Something -Path $path
}
catch [System.IO.FileNotFoundException]
{
    Write-Output "Could not find $path"
}
catch [System.IO.IOException]
{
        Write-Output "IO error with the file: $path"
}
```

사용자의 예상과 일치하는 항목이 발견될 때까지 각 `catch` 블록을 상대로 예외 형식을 확인합니다.
예외를 다른 예외에서 상속할 수 있다는 점도 반드시 알고 있어야 합니다. 위의 예제에서 `FileNotFoundException`은 `IOException`에서 상속합니다. 따라서 `IOException`이 첫 번째라면 이것이 대신 호출됩니다. 여러 항목이 일치하더라도 catch 블록은 하나만 호출됩니다.

`System.IO.PathTooLongException`이 있었다면 `IOException`이 일치할 수 있지만 `InsufficientMemoryException`이 있었다면 이것은 catch되지 않고 스택에서 전파됩니다.

### <a name="catch-multiple-types-at-once"></a>한 번에 여러 형식 catch

동일한 `catch` 문으로 여러 예외 형식을 catch할 수 있습니다.

```powershell
try
{
    Start-Something -Path $path -ErrorAction Stop
}
catch [System.IO.DirectoryNotFoundException],[System.IO.FileNotFoundException]
{
    Write-Output "The path or file was not found: [$path]"
}
catch [System.IO.IOException]
{
    Write-Output "IO error with the file: [$path]"
}
```

이 내용을 추가하도록 제안하신 `/u/Sheppard_Ra`에게 감사의 말을 전합니다.

### <a name="throwing-typed-exceptions"></a>형식화된 예외 catch

PowerShell에서 형식화된 예외를 throw할 수 있습니다. 문자열을 사용하여 `throw`를 호출하는 대신

```powershell
throw "Could not find: $path"
```

다음과 같은 예외 액셀러레이터를 사용해야 합니다.

```powershell
throw [System.IO.FileNotFoundException] "Could not find: $path"
```

하지만 이 방법을 사용할 때는 메시지를 지정해야 합니다.

Throw될 예외의 새 인스턴스를 만들 수도 있습니다. 이 작업을 할 때 메시지는 선택사항입니다. 시스템에는 모든 기본 제공 예외에 대한 기본 메시지가 있기 때문입니다.

```powershell
throw [System.IO.FileNotFoundException]::new()
throw [System.IO.FileNotFoundException]::new("Could not find path: $path")
```

PowerShell 5.0 이상을 사용하지 않는다면 예전 방법인 `New-Object`를 사용해야 합니다.

```powershell
throw (New-Object -TypeName System.IO.FileNotFoundException )
throw (New-Object -TypeName System.IO.FileNotFoundException -ArgumentList "Could not find path: $path")
```

형식화된 예외를 사용하면 여러분(또는 다른 사용자)은 이전 섹션에서 설명한 것처럼 형식을 기준으로 예외를 catch할 수 있습니다.

#### <a name="write-error--exception"></a>Write-Error -Exception

이러한 형식화된 예외를 `Write-Error` 에 추가하고 예외 형식을 기준으로 오류를 `catch`할 수 있습니다. `Write-Error`는 다음 예제에서처럼 사용합니다.

```powershell
# with normal message
Write-Error -Message "Could not find path: $path" -Exception ([System.IO.FileNotFoundException]::new()) -ErrorAction Stop

# With message inside new exception
Write-Error -Exception ([System.IO.FileNotFoundException]::new("Could not find path: $path")) -ErrorAction Stop

# Pre PS 5.0
Write-Error -Exception ([System.IO.FileNotFoundException]"Could not find path: $path") -ErrorAction Stop

Write-Error -Message "Could not find path: $path" -Exception ( New-Object -TypeName System.IO.FileNotFoundException ) -ErrorAction Stop
```

그러면 다음과 같이 이를 catch할 수 있습니다.

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Log $PSItem.ToString()
}
```

#### <a name="the-big-list-of-net-exceptions"></a>.NET 예외 종합 목록

이 게시물을 보완하기 위해 [Reddit/r/PowerShell 커뮤니티][]의 도움을 받아 .NET 예외 수백 개를 포함하는 종합 목록을 작성했습니다.

- [.NET 예외 종합 목록][]

먼저 목록에서 제 상황에 적합할 것 같은 예외를 검색하겠습니다. 여러분은 기본 `System` 네임스페이스에서 예외를 사용해야 합니다.

### <a name="exceptions-are-objects"></a>예외는 개체입니다

수많은 형식화된 예외를 사용할 때는 예외가 개체라는 사실을 명심해야 합니다. 예외는 저마다 생성자와 속성이 다릅니다. [FileNotFoundException][] 설명서의 `System.IO.FileNotFoundException` 항목을 살펴보면 메시지와 파일 경로를 전달할 수 있음을 알게 됩니다.

```powershell
[System.IO.FileNotFoundException]::new("Could not find file", $path)
```

그리고 파일 경로를 노출하는 `FileName` 속성도 존재합니다.

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Output $PSItem.Exception.FileName
}
```

다른 생성자와 개체 속성 관련 정보는 [.NET 설명서][]를 참조해야 합니다.

### <a name="re-throwing-an-exception"></a>예외 다시 throw

`catch` 블록에서 같은 예외를 `throw`하기만 할 생각이라면 예외를 `catch`해선 안 됩니다. 발생하면 처리하거나 특정 작업을 수행할 계획을 세운 예외만 `catch`해야 합니다.

예외에 특정 작업을 수행하고 싶지만 다운스트림에서 처리할 수 있도록 예외를 다시 throw해야 할 때도 있습니다. 문제를 발견한 지점 근처에서 메시지를 작성하거나 문제를 기록할 수 있지만, 문제 처리는 스택 위쪽에서 해야 합니다.

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw $PSItem
}
```

흥미롭게도 `catch` 내에서 `throw`를 호출하고 현재 예외를 다시 throw할 수 있습니다.

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw
}
```

소스 스크립트나 줄 번호 같은 원래 실행 정보를 유지하기 위해 예외를 다시 throw하려 합니다. 이 시점에서 새 예외를 throw하면 예외가 시작된 위치가 표시되지 않습니다.

#### <a name="re-throwing-a-new-exception"></a>새 예외 다시 throw

예외를 catch했지만 다른 예외를 throw하고 싶다면 원래 예외를 새 예외 안에 배치해야 합니다. 이렇게 하면 스택 아래에 있는 사람이 이 예외를 `$PSItem.Exception.InnerException`으로 액세스할 수 있습니다.

```powershell
catch
{
    throw [System.MissingFieldException]::new('Could not access field',$PSItem.Exception)
}
```

#### <a name="pscmdletthrowterminatingerror"></a>$PSCmdlet.ThrowTerminatingError()

제가 원시 예외에 `throw`를 사용하길 꺼리는 이유는 오류 메시지가 `throw` 문을 가리키며 해당 줄이 문제가 있는 곳이라 표시하기 때문입니다.

```Output
Unable to find the specified file.
At line:31 char:9
+         throw [System.IO.FileNotFoundException]::new()
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], FileNotFoundException
    + FullyQualifiedErrorId : Unable to find the specified file.
```

31번째 줄에서 `throw`를 호출했기 때문에 스크립트가 손상되었다고 말하는 오류 메시지는 여러분의 스크립트 사용자에게 표시되면 안 되는 메시지입니다. 어떤 유익한 정보도 전달하지 못하죠.

Dexter Dhami가 `ThrowTerminatingError()`를 이용하면 이 문제를 해결할 수 있다고 알려주었습니다.

```powershell
$PSCmdlet.ThrowTerminatingError(
    [System.Management.Automation.ErrorRecord]::new(
        ([System.IO.FileNotFoundException]"Could not find $Path"),
        'My.ID',
        [System.Management.Automation.ErrorCategory]::OpenError,
        $MyObject
    )
)
```

`ThrowTerminatingError()`가 `Get-Resource`라는 함수 내에서 호출되었다고 한다면, 이 오류 메시지는 적절한 메시지입니다.

```Output
Get-Resource : Could not find C:\Program Files (x86)\Reference
Assemblies\Microsoft\Framework\.NETPortable\v4.6\System.IO.xml
At line:6 char:5
+     Get-Resource -Path $Path
+     ~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (:) [Get-Resource], FileNotFoundException
    + FullyQualifiedErrorId : My.ID,Get-Resource
```

`Get-Resource` 함수가 문제의 원인이라 말하고 있죠? 사용자에게 도움이 되는 정보입니다.

`$PSItem`은 `ErrorRecord`이기 때문에 `ThrowTerminatingError`를 이 방식으로 이용하여 다시 throw할 수도 있습니다.

```powershell
catch
{
    $PSCmdlet.ThrowTerminatingError($PSItem)
}
```

이렇게 하면 오류가 발생 한 소스가 Cmdlet으로 변경되고 Cmdlet 사용자가 함수 내부 구조를 볼 수 없게 됩니다.

## <a name="try-can-create-terminating-errors"></a>Try를 이용하면 종료 오류를 만들 수 있습니다.

Kirk Munro는 일부 예외는 `try/catch` 블록 내부에서 실행될 때는 반드시 종료 오류라는 점을 지적합니다. 다음은 그가 알려준 0으로 나누는 런타임 예외를 생성하는 예시입니다.

```powershell
function Start-Something { 1/(1-1) }
```

그런 다음 이런 식으로 호출하면 오류가 생성되고 메시지가 계속 출력됩니다.

```powershell
&{ Start-Something; Write-Output "We did it. Send Email" }
```

하지만 `try/catch` 내에 동일한 코드를 배치하면 다른 현상이 발생합니다.

```powershell
try
{
    &{ Start-Something; Write-Output "We did it. Send Email" }
}
catch
{
    Write-Output "Notify Admin to fix error and send email"
}
```

오류가 종료 오류가 되며 첫 번째 메시지가 출력되지 않습니다. 제가 이 코드를 싫어하는 이유는 함수에 이 코드를 배치했을 때 다른 사용자가 `try/catch`를 사용하면 동작이 달라지기 때문입니다.

제가 직접 겪은 적은 없지만 이 문제는 반드시 유념해야 하는 코너 케이스입니다.

### <a name="pscmdletthrowterminatingerror-inside-trycatch"></a>$PSCmdlet.ThrowTerminatingError() inside try/catch

`$PSCmdlet.ThrowTerminatingError()`의 한 가지 특징은 Cmdlet 내에서는 종료 오류를 생성하지만 Cmdlet을 나가면 종료되지 않는 오류로 변한다는 점입니다. 따라서 함수 호출자가 오류 처리 방법을 결정해야 합니다. `-ErrorAction Stop`을 이용하거나 `try{...}catch{...}` 내에서 호출하면 다시 종료 오류로 만들 수 있습니다.

### <a name="public-function-templates"></a>공개 함수 템플릿

Kirk Munro와의 대화에서 배운 마지막 교훈은 그가 모든 고급 함수의 `begin`, `process`, `end` 블록에 `try{...}catch{...}`를 배치한다는 사실이었습니다. 이러한 일반 catch 블록에서 그는 `$PSCmdlet.ThrowTerminatingError($PSItem)`를 사용하여 한 줄로 함수를 종료하는 모든 예외를 처리합니다.

```powershell
function Start-Something
{
    [CmdletBinding()]
    param()

    process
    {
        try
        {
            ...
        }
        catch
        {
            $PSCmdlet.ThrowTerminatingError($PSItem)
        }
    }
}
```

모든 요소가 함수 내의 `try` 문에 있기 때문에 모든 요소가 일관되게 작동합니다. 이렇게 하면 생성된 오류의 내부 코드가 표시되지 않는 깔끔한 오류가 최종 사용자가 전달되는 효과도 있습니다.

## <a name="trap"></a>Trap

예외의 `try/catch` 요소를 중점적으로 살펴보았습니다. 하지만 마무리하기 전에 언급해야 할 레거시 기능이 하나 있습니다.

`trap`은 관련 범위에서 발생하는 모든 예외를 catch하기 위해 스크립트나 함수에 배치됩니다. 예외가 발생하면 `trap`에 있는 코드가 실행된 다음 일반 코드가 계속 실행됩니다. 여러 예외가 발생하면 trap이 반복해서 호출됩니다.

```powershell
trap
{
    Write-Log $PSItem.ToString()
}

throw [System.Exception]::new('first')
throw [System.Exception]::new('second')
throw [System.Exception]::new('third')
```

개인적으로는 채택하지 않는 방법이지만 모든 예외를 기록한 다음 계속 실행하는 관리 또는 컨트롤러 스크립트도 그만한 가치가 있습니다.

## <a name="closing-remarks"></a>맺음말

스크립트에 적절한 예외 처리를 추가하면 안전성을 강화하고, 나아가 이러한 예외를 더 쉽게 해결할 수 있습니다.

예외 처리의 핵심 개념이기 때문에 `throw`를 집중적으로 설명했죠. 또한 PowerShell을 이용하면 `Write-Error`로 `throw`를 사용하는 모든 상황을 처리할 수 있습니다. 그러니 이 글을 읽은 후에는 `throw`를 사용하지 않아도 될 겁니다.

오류 처리에 관해서는 여기에 자세히 기록했으니, 지금부터는 `Write-Error -Stop`를 사용하여 코드에서 오류를 생성하겠습니다. 또한 Kirk의 조언을 받아들여 `ThrowTerminatingError`를 모든 함수에 대한 goto 예외 처리기로 만들었습니다.

<!-- link references -->
[powershellexplained.com]: https://powershellexplained.com/
[원래 버전]: https://powershellexplained.com/2017-04-10-Powershell-exceptions-everything-you-ever-wanted-to-know/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Reddit/r/PowerShell 커뮤니티]: https://www.reddit.com/r/PowerShell/comments/64866o/kevmar_all_net_46_exceptions_list_for_use_with/
[.NET 예외 종합 목록]: https://powershellexplained.com/2017-04-07-all-dotnet-exception-list
[FileNotFoundException]: https://docs.microsoft.com/dotnet/api/System.IO.FileNotFoundException
[.NET 설명서]: https://docs.microsoft.com/dotnet/api

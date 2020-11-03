---
description: 스 플랫를 사용 하 여 PowerShell에서 명령에 매개 변수를 전달 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Splatting
ms.openlocfilehash: 0cf9702adcc7d19a19d9aaa9673fb42e3af715fa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223241"
---
# <a name="about-splatting"></a>스 플랫 정보

## <a name="short-description"></a>간단한 설명

스 플랫를 사용 하 여 PowerShell에서 명령에 매개 변수를 전달 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

스 플랫는 명령에 대 한 매개 변수 값의 컬렉션을 하나의 단위로 전달 하는 방법입니다. PowerShell은 컬렉션의 각 값을 명령 매개 변수와 연결 합니다. Splatted 매개 변수 값은 표준 변수 처럼 보이지만 `@` 달러 기호 () 대신에 기호 ()로 시작 하는 명명 된 스 플랫 변수에 저장 됩니다 `$` . At 기호는 단일 값 대신 값 컬렉션을 전달 하 고 있음을 PowerShell에 알려 줍니다.

스 플랫를 사용 하면 명령을 더 짧고 읽기 쉽게 만들 수 있습니다. 다른 명령 호출에서 스 플랫 값을 다시 사용 하 고 스 플랫를 사용 하 여 `$PSBoundParameters` 자동 변수에서 다른 스크립트 및 함수로 매개 변수 값을 전달할 수 있습니다.

Windows PowerShell 3.0 부터는 스 플랫를 사용 하 여 명령의 모든 매개 변수를 나타낼 수도 있습니다.

## <a name="syntax"></a>구문

```
<CommandName> <optional parameters> @<HashTable> <optional parameters>
<CommandName> <optional parameters> @<Array> <optional parameters>
```

매개 변수 이름이 필요 하지 않은 위치 매개 변수에 대 한 매개 변수 값을 제공 하려면 배열 구문을 사용 합니다. 매개 변수 이름 및 값 쌍을 제공 하려면 해시 테이블 구문을 사용 합니다. Splatted 값은 매개 변수 목록의 어디에 나 나타날 수 있습니다.

스 플랫 경우 모든 매개 변수를 전달 하기 위해 해시 테이블 또는 배열을 사용할 필요가 없습니다. 스 플랫를 사용 하 여 일부 매개 변수를 전달 하 고 위치나 매개 변수 이름을 사용 하 여 다른 매개 변수를 전달할 수 있습니다. 또한 각 매개 변수에 두 개 이상의 값을 전달 하지 않도록 단일 명령으로 여러 개체를 스 플랫 수 있습니다.

## <a name="splatting-with-hash-tables"></a>해시 테이블이 있는 스 플랫

해시 테이블을 사용 하 여 매개 변수 이름 및 값 쌍을 스 플랫 합니다. 위치 및 스위치 매개 변수를 포함 하 여 모든 매개 변수 형식에 대해이 형식을 사용할 수 있습니다.
위치 매개 변수는 이름으로 할당 해야 합니다.

다음 예에서는 `Copy-Item` Test.txt 파일을 동일한 디렉터리의 Test2.txt 파일에 복사 하는 두 명령을 비교 합니다.

첫 번째 예제에서는 매개 변수 이름이 포함 된 일반 형식을 사용 합니다.

```powershell
Copy-Item -Path "test.txt" -Destination "test2.txt" -WhatIf
```

두 번째 예제에서는 해시 테이블 스 플랫를 사용 합니다. 첫 번째 명령은 매개 변수 이름 및 매개 변수-값 쌍의 해시 테이블을 만들어 변수에 저장 합니다 `$HashArguments` . 두 번째 명령은 `$HashArguments` 스 플랫를 사용 하 여 명령에 변수를 사용 합니다. At 기호 ( `@HashArguments` )는 명령에서 달러 기호 ()를 대체 합니다 `$HashArguments` .

**WhatIf** 스위치 매개 변수에 대 한 값을 제공 하려면 또는를 사용 `$True` `$False` 합니다.

```powershell
$HashArguments = @{
  Path = "test.txt"
  Destination = "test2.txt"
  WhatIf = $true
}
Copy-Item @HashArguments
```

> [!NOTE]
> 첫 번째 명령에서 At 기호 ()는 `@` splatted 값이 아닌 해시 테이블을 나타냅니다. PowerShell의 해시 테이블에 대 한 구문은 다음과 같습니다. `@{<name>=<value>; <name>=<value>; ...}`

## <a name="splatting-with-arrays"></a>배열이 있는 스 플랫

배열을 사용 하 여 매개 변수 이름이 필요 하지 않은 위치 매개 변수의 값을 스 플랫 합니다. 값은 배열의 위치 번호 순서 여야 합니다.

다음 예에서는 `Copy-Item` Test.txt 파일을 동일한 디렉터리의 Test2.txt 파일에 복사 하는 두 명령을 비교 합니다.

첫 번째 예제에서는 매개 변수 이름을 생략 하는 일반적인 형식을 사용 합니다. 매개 변수 값은 명령에서 위치 순서 대로 표시 됩니다.

```powershell
Copy-Item "test.txt" "test2.txt" -WhatIf
```

두 번째 예제에서는 스 플랫 배열을 사용 합니다. 첫 번째 명령은 매개 변수 값의 배열을 만들어 변수에 저장 합니다 `$ArrayArguments` . 값은 배열의 위치 순서에 있습니다. 두 번째 명령은 `$ArrayArguments` 스 플랫의 명령에서 변수를 사용 합니다. At 기호 ( `@ArrayArguments` )는 명령에서 달러 기호 ()를 대체 합니다 `$ArrayArguments` .

```powershell
$ArrayArguments = "test.txt", "test2.txt"
Copy-Item @ArrayArguments -WhatIf
```

### <a name="using-the-argumentlist-parameter"></a>ArgumentList 매개 변수 사용

여러 cmdlet에는 매개 변수 값을 cmdlet에 의해 실행 되는 스크립트 블록에 전달 하는 데 사용 되는 **Argumentlist** 매개 변수가 있습니다. **Argumentlist** 매개 변수는 스크립트 블록으로 전달 되는 값의 배열을 사용 합니다. PowerShell은 효과적으로 배열 스 플랫를 사용 하 여 값을 스크립트 블록의 매개 변수에 바인딩합니다. **Argumentlist** 를 사용 하는 경우 단일 매개 변수에 바인딩된 단일 개체로 배열을 전달 해야 하는 경우에는 배열을 다른 배열의 유일한 요소로 래핑해야 합니다.

다음 예제에는 문자열 배열인 단일 매개 변수를 사용 하는 스크립트 블록이 있습니다.

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList $array
```

이 예제에서는의 첫 번째 항목만 `$array` 스크립트 블록으로 전달 됩니다.
```Output
Hello
```

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList (,$array)
```

이 예제에서 `$array` 는 전체 배열이 스크립트 블록에 단일 개체로 전달 되도록 배열에 래핑됩니다.

```Output
Hello World!
```

## <a name="examples"></a>예

이 예제에서는 다양 한 명령에서 splatted 값을 다시 사용 하는 방법을 보여 줍니다. 이 예제의 명령은 cmdlet을 사용 `Write-Host` 하 여 호스트 프로그램 콘솔에 메시지를 씁니다. 스 플랫를 사용 하 여 전경 색과 배경색을 지정 합니다.

모든 명령의 색을 변경 하려면 변수 값을 변경 하면 `$Colors` 됩니다.

첫 번째 명령은 매개 변수 이름 및 값의 해시 테이블을 만들고 해시 테이블을 변수에 저장 합니다 `$Colors` .

```powershell
$Colors = @{ForegroundColor = "black"; BackgroundColor = "white"}
```

두 번째 및 세 번째 명령은 `$Colors` 명령에 스 플랫에 대 한 변수를 사용 합니다 `Write-Host` . 을 사용 하려면 `$Colors variable` 달러 기호 ( `$Colors` )를 At 기호 ()로 바꿉니다 `@Colors` .

```powershell
#Write a message with the colors in $Colors
Write-Host "This is a test." @Colors

#Write second message with same colors. The position of splatted
#hash table does not matter.
Write-Host @Colors "This is another test."
```

이 예에서는 스 플랫 및 자동 변수를 사용 하 여 다른 명령에 매개 변수를 전달 하는 방법을 보여 줍니다 `$PSBoundParameters` .

`$PSBoundParameters`자동 변수는 스크립트나 함수를 실행할 때 사용 되는 모든 매개 변수 이름 및 값을 포함 하는 사전 개체 (Collections)입니다.

다음 예에서는 변수를 사용 하 여 `$PSBoundParameters` 함수에서 함수로 전달 된 매개 변수 값을 함수에서 함수로 전달 `Test2` `Test1` 합니다. 에서 함수에 대 한 두 호출은 모두 `Test1` `Test2` 스 플랫를 사용 합니다.

```powershell
function Test1
{
    param($a, $b, $c)

    $a
    $b
    $c
}

function Test2
{
    param($a, $b, $c)

    #Call the Test1 function with $a, $b, and $c.
    Test1 @PsBoundParameters

    #Call the Test1 function with $b and $c, but not with $a
    $LimitedParameters = $PSBoundParameters
    $LimitedParameters.Remove("a") | Out-Null
    Test1 @LimitedParameters
}
```

```Output
Test2 -a 1 -b 2 -c 3
1
2
3
2
3
```

## <a name="splatting-command-parameters"></a>스 플랫 명령 매개 변수

스 플랫를 사용 하 여 명령의 매개 변수를 나타낼 수 있습니다. 이 기법은 프록시 함수, 즉 다른 명령을 호출 하는 함수를 만들 때 유용 합니다. 이 기능은 Windows PowerShell 3.0에서 도입 되었습니다.

명령의 매개 변수를 스 플랫 하려면 `@Args` 를 사용 하 여 명령 매개 변수를 나타냅니다. 이 기법은 명령 매개 변수를 열거 하는 것 보다 쉽지만 호출 된 명령의 매개 변수가 변경 되는 경우에도 수정 하지 않고 작동 합니다.

이 기능은 할당 되지 `$Args` 않은 모든 매개 변수 값을 포함 하는 자동 변수를 사용 합니다.

예를 들어 다음 함수는 cmdlet를 호출 합니다 `Get-Process` . 이 함수에서는 `@Args` cmdlet의 모든 매개 변수를 나타냅니다 `Get-Process` .

```powershell
function Get-MyProcess { Get-Process @Args }
```

함수를 사용 하는 경우 `Get-MyProcess` `@Args` 다음 명령에 표시 된 것 처럼 할당 되지 않은 모든 매개 변수 및 매개 변수 값이에 전달 됩니다.

```powershell
Get-MyProcess -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    463      46   225484     237196   719    15.86   3228 powershell
```

```powershell
Get-MyProcess -Name PowerShell_Ise -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.2.9200.16384   6.2.9200.1638... C:\Windows\system32\WindowsPowerShell\...
```

`@Args`명시적으로 선언 된 매개 변수가 있는 함수에서을 사용할 수 있습니다. 함수에서 두 번 이상 사용할 수 있지만 `@Args` 다음 예제와 같이 입력 하는 모든 매개 변수는의 모든 인스턴스에 전달 됩니다.

```powershell
function Get-MyCommand
{
    Param ([switch]$P, [switch]$C)
    if ($P) { Get-Process @Args }
    if ($C) { Get-Command @Args }
}

Get-MyCommand -P -C -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
408      28    75568      83176   620     1.33   1692 powershell

Path               : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Extension          : .exe
Definition         : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Visibility         : Public
OutputType         : {System.String}
Name               : powershell.exe
CommandType        : Application
ModuleName         :
Module             :
RemotingCapability : PowerShell
Parameters         :
ParameterSets      :
HelpUri            :
FileVersionInfo    : File:             C:\Windows\System32\WindowsPowerShell
                     \v1.0\powershell.exe
                     InternalName:     POWERSHELL
                     OriginalFilename: PowerShell.EXE.MUI
                     FileVersion:      10.0.14393.0 (rs1_release.160715-1616
                     FileDescription:  Windows PowerShell
                     Product:          Microsoft Windows Operating System
                     ProductVersion:   10.0.14393.0
                     Debug:            False
                     Patched:          False
                     PreRelease:       False
                     PrivateBuild:     False
                     SpecialBuild:     False
                     Language:         English (United States)
```

## <a name="notes"></a>메모

**Cmdletbinding** 또는 **매개 변수** 특성을 사용 하 여 고급 함수로 함수를 만드는 경우 `$args` 함수에서 자동 변수를 더 이상 사용할 수 없습니다. 고급 함수에는 명시적 매개 변수 정의가 필요 합니다.

PowerShell DSC (필요한 상태 구성)가 스 플랫를 사용 하도록 설계 되지 않았습니다.
스 플랫를 사용 하 여 DSC 리소스에 값을 전달할 수 없습니다. 자세한 내용은 Gael Colas ' 문서 [의사 (Pseudo) 스 플랫 DSC 리소스](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Arrays](about_Arrays.md)

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Parameters](about_Parameters.md)

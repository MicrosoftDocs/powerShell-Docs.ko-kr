---
title: 흐름 제어
description: PowerShell은 스크립트에서 루프를 만들고, 결정을 내리고, 코드 흐름을 논리적으로 제어하는 방법을 제공합니다.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4f0d7b7f5f3c12bb9475af5aed42b2d32cfbc14d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84437994"
---
# <a name="chapter-6---flow-control"></a>6장 - 흐름 제어

## <a name="scripting"></a>스크립팅

PowerShell 원라이너 작성에서 스크립트 작성으로 전환하는 경우 실제로 그런 것보다 훨씬 복잡하게 들립니다. 스크립트는 `.PS1` 파일로 저장된다는 점을 제외하면 PowerShell 콘솔에서 대화형으로 실행하는 동일한 또는 비슷한 명령일 뿐입니다. `foreach` 루프와 같이 `ForEach-Object` cmdlet 대신 사용할 수 있는 몇 가지 스크립팅 구문이 있습니다. `foreach`가 스크립팅 구문이기도 하고 `ForEach-Object` cmdlet의 별칭이기도 하다는 점을 고려하면 초보자에게는 이러한 차이가 혼동스러울 수 있습니다.

## <a name="looping"></a>반복

PowerShell의 편리한 점 한 가지는 하나의 항목에 대해 작업을 수행하는 방법을 이해하면 수백 개의 항목에 대해 동일한 작업을 쉽게 수행할 수 있다는 것입니다. PowerShell에서 다양한 유형의 루프 중 하나를 사용하여 항목을 반복하면 되기 때문입니다.

### <a name="foreach-object"></a>ForEach-Object

`ForEach-Object`는 PowerShell 원라이너와 같은 파이프라인에서 항목을 반복하기 위한 cmdlet입니다. `ForEach-Object`는 파이프라인을 통해 개체를 스트리밍합니다.

`Get-Command`의 **Module** 매개 변수는 여러 개의 문자열 값을 허용하지만 파이프라인 입력을 통해 속성 이름 기준으로 또는 파라미터 입력을 통해서만 값을 받습니다. 다음 시나리오에서는 **Module** 매개 변수와 함께 사용하기 위해 값 기준으로 두 문자열을 `Get-Command`로 파이프하려면 `ForEach-Object` cmdlet을 사용해야 합니다.

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

이전 예제에서 `$_`는 현재 개체입니다. PowerShell 버전 3.0부터 `$_` 대신 `$PSItem`을 사용할 수 있습니다. 하지만 대부분의 숙련된 PowerShell 사용자는 여전히 `$_`를 사용합니다. 이전 버전과 호환되고 타이핑할 필요가 적기 때문입니다.

`foreach` 키워드를 사용하는 경우 항목을 반복하기 전에 메모리에 모든 항목을 저장해야 합니다. 작업하는 항목의 수를 모르는 경우에는 어려움이 있을 수 있습니다.

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

많은 경우에 `foreach` 또는 `ForEach-Object`와 같은 루프가 필요합니다. 그렇지 않으면 오류 메시지가 표시됩니다.

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

다른 경우에는 루프를 완전히 배제하면서 동일한 결과를 얻을 수 있습니다. 어떤 옵션이 있는지 알아보려면 cmdlet 도움말을 참조하세요.

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

이전 예제에서 볼 수 있듯이 `Get-ADComputer`의 **Identity** 매개 변수는 매개 변수 입력을 통해 제공되는 경우 단일 값만 허용하지만 입력이 파이프라인 입력을 통해 제공되는 경우 여러 항목을 허용합니다.

### <a name="for"></a>For

지정된 조건이 true인 동안 `for` 루프가 반복됩니다. `for` 루프는 자주 사용되지는 않지만 나름대로의 용도가 있습니다.

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

이전 예제에서 루프는 숫자 1부터 시작하여 카운터 변수 `$i`가 5보다 작은 동안 계속되어 총 4번 반복됩니다. 총 10초 동안 일시 중지됩니다.

### <a name="do"></a>해야 할 일

PowerShell에는 두 가지 `do` 루프가 있습니다. `Do Until`은 지정된 조건이 false인 동안 실행됩니다.

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

이전 예제는 추측하는 값이 `Get-Random` cmdlet에서 생성한 것과 동일한 숫자가 될 때까지 계속되는 숫자 게임입니다.

`Do While`은 반대입니다. 지정된 조건이 true로 평가되는 동안 실행됩니다.

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

테스트 조건을 같지 않음으로 뒤집어 `Do While` 루프를 사용하면 동일한 결과를 얻을 수 있습니다.

`Do` 루프는 항상 한 번 이상 실행됩니다. 루프의 끝에서 조건이 평가되기 때문입니다.

### <a name="while"></a>While

`While` 루프는 `Do While` 루프와 마찬가지로 지정된 조건이 true인 동안 실행됩니다. 그러나 `While` 루프는 코드가 실행되기 전에 루프 맨 위에 있는 조건을 평가한다는 것이 차이점입니다. 따라서 조건이 false로 평가되는 경우 실행되지 않습니다.

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

이전 예제에서는 미국에서 추수감사절 날짜를 계산합니다. 추수감사절은 항상 11월의 네 번째 목요일입니다. 따라서 루프가 11월의 22번째 날부터 시작하고 요일이 목요일이 아닌 동안 하루를 추가합니다. 22번째가 목요일이면 루프가 전혀 실행되지 않습니다.

## <a name="break-continue-and-return"></a>중단, 계속 및 반환

`Break`는 루프를 중단하도록 설계되었습니다. 일반적으로 `switch` 문과 함께 사용됩니다.

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

이전 예제에 표시된 `break` 문을 실행하면 첫 번째 반복에서 루프가 종료됩니다.

Continue는 루프의 다음 반복으로 건너뛰도록 설계되었습니다.

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

이전 예제는 숫자 1, 2, 4, 5를 출력합니다. 숫자 3을 건너뛰고 루프의 다음 반복을 계속 진행합니다. `continue`는 현재 반복에 대해서라는 점만 제외하고 `break`와 마찬가지로 루프를 중단합니다. Execution은 루프를 중단하고 중지하는 대신 다음 반복에서 실행이 계속됩니다.

Return은 기존 범위에서 종료되도록 설계되었습니다.

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

이전 예제에서 return은 첫 번째 결과를 출력한 다음 루프에서 종료됩니다. 결과 문에 대한 자세한 설명은 다음 블로그 게시물 중 하나에서 찾을 수 있습니다. ["PowerShell return 카워드"][].

## <a name="summary"></a>요약

이 장에서는 PowerShell에 존재하는 다양한 유형의 루프에 대해 알아보았습니다.

## <a name="review"></a>검토

1. `ForEach-Object` cmdlet과 foreach 스크립팅 구문의 차이점은 무엇인가요?
1. Do While 또는 Do Until 루프를 사용하는 대신 While 루프를 사용할 때의 주요 이점은 무엇인가요?
1. break 문과 continue 문은 어떻게 다른가요?

## <a name="recommended-reading"></a>권장 참조 항목

- [ForEach-Object][]
- [about_ForEach][]
- [about_For][]
- [about_Do][]
- [about_While][]
- [about_Break][]
- [about_Continue][]
- [about_Return][]

<!-- link references -->
[ForEach-Object]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
["PowerShell return 카워드"]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/

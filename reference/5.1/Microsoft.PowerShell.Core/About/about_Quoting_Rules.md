---
description: PowerShell에서 작은따옴표와 큰따옴표를 사용 하는 규칙을 설명 합니다.
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: b100ff8ab4be84b7117efc5724119221351ba4bf
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490672"
---
# <a name="about-quoting-rules"></a>따옴표 규칙 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 작은따옴표와 큰따옴표를 사용 하는 규칙을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

리터럴 문자열을 지정 하는 데 따옴표가 사용 됩니다. 문자열을 작은따옴표 ( `'` ) 또는 큰따옴표 ()로 묶을 수 있습니다 `"` .

또한 따옴표를 사용 하 여 _문자열_ 을 만들 수 있습니다. 여기에 표시 되는 문자열은 따옴표를 문자 그대로 해석 하는 작은따옴표 또는 큰따옴표로 묶인 문자열입니다. 여기에 있는 문자열은 여러 줄에 걸쳐 있을 수 있습니다. 여기에 표시 된 문자열의 모든 줄은 따옴표로 묶여 있지 않더라도 문자열로 해석 됩니다.

원격 컴퓨터에 대 한 명령에서 인용 부호는 원격 컴퓨터에서 실행 되는 명령의 일부를 정의 합니다. 원격 세션에서 따옴표는 명령의 변수가 로컬 컴퓨터 또는 원격 컴퓨터에서 먼저 해석 되는지 여부도 결정 합니다.

## <a name="single-and-double-quoted-strings"></a>작은따옴표 및 이중 따옴표 문자열

큰따옴표로 묶인 문자열은 _확장 가능한_ 문자열입니다. 달러 기호 () 뒤에 오는 변수 이름은 `$` 문자열을 처리 하기 위해 명령에 전달 하기 전에 변수의 값으로 대체 됩니다.

예를 들면 다음과 같습니다.

```powershell
$i = 5
"The value of $i is $i."
```

이 명령의 출력은 다음과 같습니다.

```Output
The value of 5 is 5.
```

또한 이중 따옴표 붙은 문자열에서 식이 계산 되 고 결과가 문자열에 삽입 됩니다. 예를 들면 다음과 같습니다.

```powershell
"The value of $(2+3) is 5."
```

이 명령의 출력은 다음과 같습니다.

```Output
The value of 5 is 5.
```

작은따옴표로 묶인 문자열은 _축 자_ 문자열입니다. 문자열은 입력 한 대로 정확 하 게 명령에 전달 됩니다. 대체가 수행 되지 않습니다.
예를 들면 다음과 같습니다.

```powershell
$i = 5
'The value of $i is $i.'
```

이 명령의 출력은 다음과 같습니다.

```Output
The value $i is $i.
```

마찬가지로, 작은따옴표로 묶은 문자열의 식은 계산 되지 않습니다. 리터럴으로 해석 됩니다. 예를 들면 다음과 같습니다.

```powershell
'The value of $(2+3) is 5.'
```

이 명령의 출력은 다음과 같습니다.

```Output
The value of $(2+3) is 5.
```

큰따옴표로 묶은 문자열에서 변수 값을 대체 하지 않도록 하려면 PowerShell 이스케이프 문자인 억음 문자 ( `` ` `` ) (ASCII 96)를 사용 합니다.

다음 예제에서 첫 번째 변수 앞의 억음 문자는 `$i` PowerShell에서 변수 이름을 해당 값으로 바꾸지 못하도록 합니다.
예를 들면 다음과 같습니다.

```powershell
$i = 5
"The value of `$i is $i."
```

이 명령의 출력은 다음과 같습니다.

```Output
The value $i is 5.
```

문자열에 큰따옴표가 표시 되도록 하려면 전체 문자열을 작은따옴표로 묶습니다. 예를 들면 다음과 같습니다.

```powershell
'As they say, "live and learn."'
```

이 명령의 출력은 다음과 같습니다.

```Output
As they say, "live and learn."
```

작은따옴표로 묶은 문자열을 큰따옴표로 묶을 수도 있습니다. 예를 들면 다음과 같습니다.

```powershell
"As they say, 'live and learn.'"
```

이 명령의 출력은 다음과 같습니다.

```Output
As they say, 'live and learn.'
```

또는 큰따옴표를 큰따옴표로 묶어야 합니다. 예를 들면 다음과 같습니다.

```powershell
"As they say, ""live and learn."""
```

이 명령의 출력은 다음과 같습니다.

```Output
As they say, "live and learn."
```

작은따옴표로 묶은 단일 문자열에 작은따옴표를 포함 하려면 두 번째 연속 작은따옴표를 사용 합니다. 예를 들면 다음과 같습니다.

```powershell
'don''t'
```

이 명령의 출력은 다음과 같습니다.

```Output
don't
```

PowerShell에서 큰따옴표를 문자 그대로 해석 하도록 하려면 억음 문자를 사용 합니다. 이렇게 하면 PowerShell에서 따옴표를 문자열 구분 기호로 해석 하지 않습니다. 예를 들면 다음과 같습니다.

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

작은따옴표로 묶인 단일 문자열의 내용이 리터럴로 해석 되기 때문에 억음 문자는 리터럴 문자로 취급 되 고 출력에 표시 됩니다.

## <a name="here-strings"></a>다음 문자열

여기서는 문자열에 대 한 따옴표 규칙이 약간 다릅니다.

여기에 표시 되는 문자열은 따옴표를 문자 그대로 해석 하는 작은따옴표 또는 큰따옴표로 묶인 문자열입니다. 여기에 있는 문자열은 여러 줄에 걸쳐 있을 수 있습니다. 여기에 표시 된 문자열의 모든 줄은 따옴표로 묶여 있지 않더라도 문자열로 해석 됩니다.

일반 문자열과 마찬가지로 변수는 큰따옴표로 묶은 문자열의 값으로 대체 됩니다. 여기에 있는 작은따옴표로 묶은 문자열에서는 변수가 해당 값으로 대체 되지 않습니다.

텍스트에는 여기에 문자열을 사용할 수 있지만 특히 다음과 같은 종류의 텍스트에 유용 합니다.

- 리터럴 따옴표를 포함 하는 텍스트입니다.
- HTML 또는 XML의 텍스트와 같은 여러 줄의 텍스트
- 스크립트 또는 함수 문서에 대 한 도움말 텍스트입니다.

여기서 문자열은 다음 형식 중 하나를 사용할 수 있습니다. 여기서는 `<Enter>` <kbd>enter</kbd> 키를 누를 때 추가 되는 줄 바꿈 또는 줄 바꿈 문자를 나타냅니다.

큰따옴표:

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

작은따옴표:

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

두 형식에서 닫는 따옴표는 줄의 첫 번째 문자 여야 합니다.

여기에 표시 되는 문자열은 두 숨겨진 문자 사이의 모든 텍스트를 포함 합니다. 여기 문자열에서 모든 따옴표는 문자 그대로 해석 됩니다. 예를 들면 다음과 같습니다.

```powershell
@"
For help, type "get-help"
"@
```

이 명령의 출력은 다음과 같습니다.

```Output
For help, type "get-help"
```

다음 문자열을 사용 하면 명령에서 문자열을 사용 하 여 단순화할 수 있습니다. 예를 들면 다음과 같습니다.

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

이 명령의 출력은 다음과 같습니다.

```Output
Use a quotation mark (') to begin a string.
```

여기에 있는 작은따옴표로 묶은 문자열에서 변수는 문자 그대로 해석 되어 정확히 재현 됩니다. 예를 들면 다음과 같습니다.

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

이 명령의 출력은 다음과 같습니다.

```Output
The $profile variable contains the path
of your PowerShell profile.
```

여기에 큰따옴표로 묶은 문자열에서는 변수가 해당 값으로 대체 됩니다. 예를 들면 다음과 같습니다.

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

이 명령의 출력은 다음과 같습니다.

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

여기에서 문자열은 일반적으로 변수에 여러 줄을 할당 하는 데 사용 됩니다. 예를 들어 다음은 $page 변수에 XML 페이지를 할당 하는 문자열입니다.

```powershell
$page = [XML] @"
<command:command xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
<command:details>
        <command:name>
               Format-Table
        </command:name>
        <maml:description>
            <maml:para>Formats the output as a table.</maml:para>
        </maml:description>
        <command:verb>format</command:verb>
        <command:noun>table</command:noun>
        <dev:version></dev:version>
</command:details>
...
</command:command>
"@
```

여기에서 문자열은 cmdlet에 대 한 입력에 사용할 수 있는 편리한 형식이 며 `ConvertFrom-StringData` , 여기서 문자열을 해시 테이블로 변환 합니다.
자세한 내용은 `ConvertFrom-StringData`를 참조하세요.

## <a name="see-also"></a>참조

[about_Special_Characters](about_Special_Characters.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

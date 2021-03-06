---
description: PowerShell에서 시퀀스의 다음 문자를 해석 하는 방법을 제어 하는 특수 문자 시퀀스에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: 7e0ea9298dd85627c08298917464cb005f4f37ff
ms.sourcegitcommit: 364c3fe46b2069b810107d840be59fe519ea7b4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/10/2021
ms.locfileid: "100100736"
---
# <a name="about-special-characters"></a>특수 문자 정보

## <a name="short-description"></a>간단한 설명

PowerShell에서 시퀀스의 다음 문자를 해석 하는 방법을 제어 하는 특수 문자 시퀀스에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell은 표준 문자 집합에 속하지 않는 문자를 나타내는 데 사용 되는 일련의 특수 문자 시퀀스를 지원 합니다. 시퀀스를 일반적으로 _이스케이프 시퀀스_ 라고 합니다.

이스케이프 시퀀스는 억음 악센트 문자 (ASCII 96)로 시작 하 고 대/소문자를 구분 합니다. 억음 문자를 _이스케이프 문자_ 라고도 합니다.

이스케이프 시퀀스는 이중 따옴표 붙은 () 문자열에 포함 된 경우에만 해석 됩니다 `"` .

PowerShell은 다음과 같은 이스케이프 시퀀스를 인식 합니다.

|  시퀀스   |       Description       |
| ----------- | ----------------------- |
| `` `0 ``    | Null                    |
| `` `a ``    | 경고                   |
| `` `b ``    | 백스페이스               |
| `` `f ``    | 폼 피드               |
| `` `n ``    | 줄 바꿈                |
| `` `r ``    | 캐리지 리턴         |
| `` `t ``    | 가로 탭          |
| `` `v ``    | 세로 탭            |

또한 PowerShell에는 구문 분석을 중지할 위치를 표시 하는 특수 토큰이 있습니다. 이 토큰을 따르는 모든 문자는 해석 되지 않는 리터럴 값으로 사용 됩니다.

특수 구문 분석 토큰:

| 시퀀스 |            Description             |
| -------- | ---------------------------------- |
| `--%`    | 다음에 나오는 모든 항목 구문 분석 중지 |

## <a name="null-0"></a>Null (' 0 ')

Null ( `` `0 `` ) 문자가 PowerShell 출력에 빈 공간으로 나타납니다.
이 기능을 통해 PowerShell을 사용 하 여 문자열 종료 또는 레코드 종료 표시기와 같은 null 문자를 사용 하는 텍스트 파일을 읽고 처리할 수 있습니다. Null 특수 문자는 `$null` **null** 값을 저장 하는 변수와 동일 하지 않습니다.

## <a name="alert-a"></a>경고 (' a)

경고 ( `` `a `` ) 문자는 컴퓨터의 스피커로 경고음 신호를 보냅니다.
이 문자를 사용 하 여 사용자에 게 임박한 작업을 경고할 수 있습니다. 다음 예에서는 두 개의 경고음 신호를 로컬 컴퓨터의 스피커로 보냅니다.

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a>백스페이스 (' b)

백스페이스 ( `` `b `` ) 문자는 커서를 한 문자 뒤로 이동 하지만 문자를 삭제 하지는 않습니다.

이 예에서는 word **backup** 을 작성 한 다음 커서를 다시 두 번 이동 합니다.
그런 다음 새 위치에서 공백을 쓴 다음 단어를 **출력** 합니다.

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="form-feed-f"></a>양식 피드 (' f)

양식 피드 ( `` `f `` ) 문자는 현재 페이지를 배출 하 고 다음 페이지에서 인쇄를 계속 하는 인쇄 명령입니다. 양식 피드 문자는 인쇄 된 문서에만 영향을 줍니다. 화면 출력에는 영향을 주지 않습니다.

## <a name="new-line-n"></a>줄 바꿈 (' n)

새 줄 ( `` `n `` ) 문자는 문자 바로 뒤에 줄 바꿈을 삽입 합니다.

이 예제에서는 줄 바꿈 문자를 사용 하 여 명령에서 줄 바꿈을 만드는 방법을 보여 줍니다 `Write-Host` .

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a>캐리지 리턴 (' r ')

캐리지 리턴 ( `` `r `` ) 문자는 출력 커서를 현재 줄의 시작으로 이동 하 고 쓰기를 계속 합니다. 현재 줄에 있는 모든 문자를 덮어씁니다.

이 예제에서는 캐리지 리턴 전의 텍스트를 덮어씁니다.

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

문자 앞의 텍스트는 `` `r `` 삭제 되지 않으며 덮어쓰여집니다.

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a>가로 탭 (' t)

가로 탭 ( `` `t `` ) 문자는 다음 탭 정지로 이동 하 여 해당 지점에서 계속 작성 합니다. 기본적으로 PowerShell 콘솔은 여덟 번째 모든 공간에서 탭 정지를 포함 합니다.

이 예에서는 각 열 사이에 두 개의 탭을 삽입 합니다.

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="vertical-tab-v"></a>세로 탭 (' v)

세로 탭 ( `` `v `` ) 문자는 다음 세로 탭 정지로 이동 하 고 해당 지점에서 나머지 출력을 씁니다. 세로 탭의 렌더링은 장치 및 터미널에 종속 됩니다.

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

다음 예에서는 몇 가지 일반적인 환경에서 세로 탭의 렌더링 된 출력을 보여 줍니다.

Windows 콘솔 호스트 응용 프로그램은 ( `` `v `` )를 추가 간격이 추가 되지 않은 특수 문자로 해석 합니다.

```Output
There is a vertical tab♂between the words.
```

[Windows 터미널](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701) 에서는 세로 탭 문자를 캐리지 리턴 및 줄 바꿈으로 렌더링 합니다. 출력의 나머지 부분은 다음 줄의 시작 부분에 인쇄 됩니다.

```Output
There is a vertical tab
between the words.
```

프린터 또는 unix 기반 콘솔에서 세로 탭 문자는 다음 줄로 이동 하 여 해당 지점에 나머지 출력을 씁니다.

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a>토큰 구문 분석 (--%)

구문 분석 ( `--%` ) 토큰은 powershell에서 문자열을 powershell 명령 및 식으로 해석 하는 것을 방지 합니다. 이렇게 하면 해당 문자열을 다른 프로그램에 전달 하 여 해석할 수 있습니다.

프로그램 이름 및 오류를 발생 시킬 수 있는 프로그램 인수 앞에 중지 구문 분석 토큰을 넣습니다.

이 예제에서 `Icacls` 명령은 중지 구문 분석 토큰을 사용 합니다.

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

PowerShell에서 다음 문자열을로 보냅니다 `Icacls` .

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

또는 다음과 같은 예도 있습니다. **Sho워 gs** 함수는 전달 된 값을 출력 합니다. 이 예제에서는 라는 변수를 `$HOME` 함수에 두 번 전달 합니다.

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

출력에서 첫 번째 매개 변수의 경우 변수 `$HOME` 값이 함수에 전달 되도록 PowerShell에서 변수를 해석 하는 것을 볼 수 있습니다. 두 번째 사용은 `$HOME` 중지 구문 분석 토큰 후에 제공 되므로 "$HOME" 문자열이 해석 없이 함수에 전달 됩니다.

```Output
$args = C:\Users\username|--%|$HOME
```

중지 구문 분석 토큰에 대 한 자세한 내용은 [about_Parsing](about_Parsing.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Quoting_Rules](about_Quoting_Rules.md)

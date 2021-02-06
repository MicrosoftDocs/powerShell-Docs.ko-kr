---
description: ', 및 블록을 사용 하 여 `Try` `Catch` 종료 오류를 처리 하는 방법을 설명 합니다 `Finally` .'
Locale: en-US
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_try_catch_finally?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Try_Catch_Finally
ms.openlocfilehash: c93fa69e3badd7777950a850dfe81b79f9197f68
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599952"
---
# <a name="about-try-catch-finally"></a>Try Catch Finally 정보

## <a name="short-description"></a>간단한 설명
, 및 블록을 사용 하 여 `Try` `Catch` 종료 오류를 처리 하는 방법을 설명 합니다 `Finally` .

## <a name="long-description"></a>자세한 설명

`Try`, `Catch` 및 블록을 사용 하 여 스크립트에 `Finally` 응답 하거나 스크립트의 종료 오류를 처리 합니다. `Trap`문을 사용 하 여 스크립트의 종료 오류를 처리할 수도 있습니다. 자세한 내용은 [about_Trap](about_Trap.md)를 참조 하세요.

종료 오류가 발생 하면 문이 실행 되지 않습니다. PowerShell에서 어떤 방식으로든 종료 오류를 처리 하지 않는 경우 PowerShell은 현재 파이프라인을 사용 하 여 함수 또는 스크립트의 실행을 중지 합니다. C와 같은 다른 언어에서는 \# 종료 오류를 예외 라고 합니다.

블록을 사용 하 여 `Try` PowerShell에서 오류를 모니터링 하도록 할 스크립트의 섹션을 정의 합니다. 블록 내에서 오류가 발생 하면 `Try` 먼저 자동 변수에 오류가 저장 됩니다 `$Error` . 그러면 PowerShell에서 오류를 `Catch` 처리 하기 위해 블록을 검색 합니다. `Try`문에 일치 하는 블록이 없으면 PowerShell은 `Catch` `Catch` 부모 범위에서 적절 한 블록이 나 문을 계속 검색 `Trap` 합니다. `Catch`블록이 완료 된 후 또는 적절 한 `Catch` 블록이 나 문이 없는 경우 `Trap` `Finally` 블록이 실행 됩니다. 오류를 처리할 수 없는 경우 오류가 오류 스트림에 기록 됩니다.

`Catch`블록은 오류를 추적 하거나 스크립트의 예상 흐름을 복구 하기 위한 명령을 포함할 수 있습니다. `Catch`블록은 catch 하는 오류 형식을 지정할 수 있습니다. 문에는 여러 `Try` 종류의 `Catch` 오류에 대 한 여러 블록이 포함 될 수 있습니다.

`Finally`블록을 사용 하 여 스크립트에 더 이상 필요 하지 않은 리소스를 해제할 수 있습니다.

`Try`, `Catch` 및는 `Finally` `Try` `Catch` `Finally` C 프로그래밍 언어에서 사용 되는, 및 키워드와 유사 \# 합니다.

### <a name="syntax"></a>SYNTAX

`Try`문에는 `Try` 블록, 0 개 이상의 블록 `Catch` 및 0 개 또는 1 개 블록이 포함 되어 있습니다 `Finally` . `Try`문에는 `Catch` 블록이 나 블록이 하나 이상 있어야 합니다 `Finally` .

다음은 `Try` 블록 구문을 보여 줍니다.

```powershell
try {<statement list>}
```

`Try`키워드 뒤에 중괄호의 문 목록이 옵니다. 문 목록의 문이 실행 되는 동안 종료 오류가 발생 하면 스크립트는 블록의 오류 개체를 `Try` 적절 한 블록으로 전달 합니다 `Catch` .

다음은 `Catch` 블록 구문을 보여 줍니다.

```powershell
catch [[<error type>][',' <error type>]*] {<statement list>}
```

오류 형식은 대괄호 안에 표시 됩니다. 가장 바깥쪽 대괄호는 요소가 선택 사항임을 의미 합니다.

`Catch`키워드 뒤에는 오류 유형 사양 및 문 목록의 선택적인 목록이 있습니다. 블록에서 종료 오류가 발생 하면 `Try` PowerShell에서 적절 한 블록을 검색 `Catch` 합니다. 블록의 문이 있는 경우 블록의 문이 `Catch` 실행 됩니다.

`Catch`블록은 하나 이상의 오류 유형을 지정할 수 있습니다. 오류 형식은 Microsoft .NET Framework 예외 이거나 .NET Framework 예외에서 파생 된 예외입니다. 블록은 지정 된 `Catch` .NET Framework 예외 클래스 또는 지정 된 클래스에서 파생 되는 클래스의 오류를 처리 합니다.

블록에서 `Catch` 오류 유형을 지정 하는 경우 해당 `Catch` 블록은 해당 유형의 오류를 처리 합니다. 블록에 `Catch` 오류 형식이 지정 되지 않은 경우 해당 블록 `Catch` 은 블록에서 발생 한 모든 오류를 처리 `Try` 합니다. `Try`문에는 `Catch` 지정 된 다른 오류 유형에 대 한 여러 블록이 포함 될 수 있습니다.

다음은 `Finally` 블록 구문을 보여 줍니다.

```powershell
finally {<statement list>}
```

키워드 뒤에는 문이 `Finally` `Try` 오류 없이 실행 되었거나 문에서 오류가 catch 된 경우에도 스크립트가 실행 될 때마다 실행 되는 문 목록이 나옵니다 `Catch` .

<kbd>Ctrl</kbd> + <kbd>C</kbd> 키를 누르면 파이프라인이 중지 됩니다. 파이프라인으로 전송 되는 개체는 출력으로 표시 되지 않습니다. 따라서 "Finally 블록이 실행 되었습니다."와 같이 표시할 문을 포함 하 <kbd></kbd> + 는 경우 블록이 실행 된 경우에도 ctrl<kbd>C</kbd>를 누르면 표시 되지 않습니다 `Finally` .

### <a name="catching-errors"></a>오류 CATCH

다음 샘플 스크립트는 블록이 포함 된 블록을 보여 줍니다 `Try` `Catch` .

```powershell
try { NonsenseString }
catch { "An error occurred." }
```

`Catch`키워드는 `Try` 블록 또는 다른 블록 바로 뒤에와 야 합니다 `Catch` .

PowerShell에서 cmdlet 또는 다른 항목으로 "NonsenseString"을 인식 하지 못합니다.
이 스크립트를 실행 하면 다음과 같은 결과가 반환 됩니다.

```powershell
An error occurred.
```

스크립트에서 "NonsenseString"이 발견 되 면 종료 오류가 발생 합니다. 블록 `Catch` 내부에서 문 목록을 실행 하 여 오류를 처리 합니다.

### <a name="using-multiple-catch-statements"></a>여러 CATCH 문 사용

`Try`문에는 여러 개의 블록이 있을 수 있습니다 `Catch` . 예를 들어 다음 스크립트는 `Try` 를 다운로드 하는 블록을 `MyDoc.doc` 포함 하며 두 개의 블록을 포함 합니다 `Catch` .

```powershell
try {
   $wc = new-object System.Net.WebClient
   $wc.DownloadFile("http://www.contoso.com/MyDoc.doc","c:\temp\MyDoc.doc")
}
catch [System.Net.WebException],[System.IO.IOException] {
    "Unable to download MyDoc.doc from http://www.contoso.com."
}
catch {
    "An error occurred that could not be resolved."
}

```

첫 번째 `Catch` 블록은 **system WebException** 및 system.string **예외** 형식의 오류를 처리 합니다. 두 번째 `Catch` 블록은 오류 유형을 지정 하지 않습니다. 두 번째 `Catch` 블록은 발생 하는 다른 종료 오류를 처리 합니다.

PowerShell은 상속을 통해 오류 유형을 일치 시킵니다. 블록은 지정 된 `Catch` .NET Framework 예외 클래스 또는 지정 된 클래스에서 파생 되는 클래스의 오류를 처리 합니다. 다음 예제에는 `Catch` "명령 찾을 수 없음" 오류를 catch 하는 블록이 포함 되어 있습니다.

```powershell
catch [System.Management.Automation.CommandNotFoundException]
{"Inherited Exception" }
```

지정 된 오류 형식 **CommandNotFoundException** 는 **System.SystemException** 형식에서 상속 됩니다. 다음 예에서는 명령을 찾을 수 없음 오류를 catch 합니다.

```powershell
catch [System.SystemException] {"Base Exception" }
```

이 `Catch` 블록은 "명령 찾을 수 없음" 오류 및 **systemexception** 형식에서 상속 되는 기타 오류를 처리 합니다.

오류 클래스와 해당 파생 클래스 중 하나를 지정 하는 경우에는 `Catch` 일반 클래스의 블록 앞에 파생 클래스의 블록을 추가 `Catch` 합니다.

### <a name="using-traps-in-a-try-catch"></a>Try Catch에서 트랩 사용

블록 내에서 정의 된가 있는 블록에서 종료 오류가 발생할 경우 `Try` `Trap` `Try` 일치 하는 `Catch` 블록이 있더라도 `Trap` 문은 제어를 사용 합니다.

가 `Trap` 보다 높은 블록에 있고 `Try` 현재 범위 내에 일치 하는 블록이 없으면 `Catch` `Trap` 부모 범위에 일치 하는 블록이 있는 경우에도이 제어를 사용 합니다 `Catch` .

### <a name="accessing-exception-information"></a>예외 정보 액세스

블록 내에서 `Catch` 현재 오류는 라고도 하는를 사용 하 여 액세스할 수 있습니다 `$_` `$PSItem` . 개체의 형식은 **ErrorRecord** 입니다.

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_
}
```

이 스크립트를 실행 하면 다음과 같은 결과가 반환 됩니다.

```Output
An Error occurred:
The term 'NonsenseString' is not recognized as the name of a cmdlet, function,
script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
```

**ScriptStackTrace**, **Exception** 및 **errordetails** 와 같이 액세스할 수 있는 추가 속성이 있습니다.  예를 들어 스크립트를 다음과 같이 변경 합니다.

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_.ScriptStackTrace
}
```

결과는 다음과 유사 합니다.

```
An Error occurred:
at <ScriptBlock>, <No file>: line 2
```

### <a name="freeing-resources-by-using-finally"></a>FINALLY를 사용 하 여 리소스 해제

스크립트에서 사용 하는 리소스를 해제 하려면 `Finally` 및 블록 뒤에 블록을 추가 `Try` `Catch` 합니다. 블록 `Finally` 문은 블록에 종료 오류가 발생 하는지 여부에 관계 없이 실행 `Try` 됩니다. PowerShell은 `Finally` 스크립트가 종료 되기 전이나 현재 블록이 범위를 벗어나기 전에 블록을 실행 합니다.

`Finally` <kbd>CTRL</kbd> + <kbd>C</kbd> 를 사용 하 여 스크립트를 중지 하는 경우에도 블록이 실행 됩니다. 블록은 `Finally` Exit 키워드가 블록 내에서 스크립트를 중지 하는 경우에도 실행 됩니다 `Catch` .

### <a name="see-also"></a>참고 항목

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)


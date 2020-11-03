---
description: 스크립트에서 사용자에 게 UI (사용자 인터페이스) 언어로 메시지와 지침을 쉽게 표시할 수 있도록 하는 스크립트 국제화 기능에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_internationalization?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Internationalization
ms.openlocfilehash: dddf090ba18ca9eb703b307db9fddcdb88e4a5ac
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220609"
---
# <a name="about-script-internationalization"></a>스크립트 국제화 정보

## <a name="short-description"></a>간단한 설명
스크립트에서 사용자에 게 UI (사용자 인터페이스) 언어로 메시지와 지침을 쉽게 표시할 수 있도록 하는 스크립트 국제화 기능에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell 스크립트 국제화 기능을 사용 하면 사용자의 언어로 도움말 및 사용자 메시지를 표시 하 여 전 세계 사용자에 게 더 나은 서비스를 제공할 수 있습니다.

스크립트 국제화 기능은 실행 중 운영 체제의 UI 문화권을 쿼리하고, 적절 하 게 번역 된 텍스트 문자열을 가져와 사용자에 게 표시 합니다. 데이터 섹션에서는 쉽게 식별 하 고 추출할 수 있도록 텍스트 문자열을 코드와 구분 하 여 저장할 수 있습니다. 새 cmdlet는 `ConvertFrom-StringData` 텍스트 문자열을 사전 유사 해시 테이블로 변환 하 여 변환을 용이 하 게 합니다.

국가별 도움말 텍스트를 지원 하기 위해 PowerShell에는 다음과 같은 기능이 포함 되어 있습니다.

- 텍스트 문자열을 코드 명령과 구분 하는 데이터 섹션입니다. 데이터 섹션에 대 한 자세한 내용은 [about_Data_Sections](about_Data_Sections.md)를 참조 하세요.

- 새 자동 변수 `$PSCulture` 및 `$PSUICulture` 입니다. `$PSCulture` 날짜, 시간 및 통화와 같은 요소에 대해 시스템에서 사용 되는 UI 언어의 이름을 저장 합니다. `$PSUICulture`변수는 메뉴 및 텍스트 문자열과 같은 사용자 인터페이스 요소에 대해 시스템에서 사용 되는 UI 언어의 이름을 저장 합니다.

- `ConvertFrom-StringData`텍스트 문자열을 사전 유사 해시 테이블로 변환 하 여 변환을 용이 하 게 하는 cmdlet입니다. 자세한 내용은 [convertfrom-csv-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)를 참조 하세요.

- `.psd1`번역 된 텍스트 문자열을 저장 하는 새 파일 형식입니다. `.psd1`파일은 스크립트 디렉터리의 언어별 하위 디렉터리에 저장 됩니다.

- Cmdlet는 `Import-LocalizedData` 지정 된 언어에 대 한 번역 된 텍스트 문자열을 런타임에 스크립트에 가져오는 cmdlet입니다. 이 cmdlet은 Windows에서 지 원하는 언어로 문자열을 인식 하 고 가져옵니다. 자세한 내용은 [import-localizeddata](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)를 참조 하세요.

### <a name="the-data-section-storing-default-strings"></a>데이터 섹션: 기본 문자열 저장

스크립트의 데이터 섹션을 사용 하 여 텍스트 문자열을 기본 언어로 저장 합니다. 문자열을 여기에 있는 키/값 쌍으로 정렬 합니다. 각 키/값 쌍은 별도의 줄에 있어야 합니다. 주석을 포함 하는 경우 주석은 별도의 줄에 있어야 합니다.

`ConvertFrom-StringData`Cmdlet은 다음 문자열의 키/값 쌍을 데이터 섹션 변수 값에 저장 된 사전 형식의 해시 테이블로 변환 합니다.

다음 예에서 스크립트의 데이터 섹션에는 `World.ps1` 스크립트에 대 한 프롬프트 메시지의 English-United 상태 (en-us)가 포함 되어 있습니다. `ConvertFrom-StringData`Cmdlet은 문자열을 해시 테이블로 변환 하 고 변수에 저장 합니다 `$msgtable` .

```powershell
$msgTable = Data {
    #culture="en-US"
    ConvertFrom-StringData @'
    helloWorld = Hello, World.
    errorMsg1 = You cannot leave the user name field blank.
    promptMsg = Please enter your user name.
'@
}
```

이러한 문자열에 대 한 자세한 내용은 [about_Quoting_Rules](about_Quoting_Rules.md)를 참조 하세요.

### <a name="psd1-files-storing-translated-strings"></a>PSD1 Files: 번역 된 문자열 저장

각 UI 언어에 대 한 스크립트 메시지를 스크립트 및 파일 이름 확장명과 동일한 이름으로 별도의 텍스트 파일에 저장 `.psd1` 합니다. 다음 형식의 문화권 이름을 사용 하 여 스크립트 디렉터리의 하위 디렉터리에 파일을 저장 합니다.

`<language>-<region>`

예: de-de, ar-SA 및 zh-cn-Hans

예를 들어 스크립트를 `World.ps1` 디렉터리에 저장 하는 경우 `C:\Scripts` 다음과 같은 파일 디렉터리 구조를 만듭니다.

```
C:\Scripts
C:\Scripts\World.ps1
C:\Scripts\de-DE\World.psd1
C:\Scripts\ar-SA\World.psd1
C:\Scripts\zh-CN\World.psd1
...
```

`World.psd1`스크립트 디렉터리의 de 하위 디렉터리에 있는 파일에는 다음 문이 포함 될 수 있습니다.

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = Hallo, Welt.
errorMsg1 = Das Feld Benutzername darf nicht leer sein.
promptMsg = Geben Sie Ihren Benutzernamen ein.
'@
```

마찬가지로 `World.psd1` 스크립트 디렉터리의 ar-SA 하위 디렉터리에 있는 파일에는 다음 문이 포함 될 수 있습니다.

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = مرحبًا أيها العالَم
errorMsg1 = لا يمكنك ترك حقل اسم المستخدم فارغًا
promptMsg = يرجى إدخال اسم المستخدم الخاص بك
'@
```

### <a name="import-localizeddata-dynamic-retrieval-of-translated-strings"></a>Import-localizeddata: 번역 된 문자열의 동적 검색

현재 사용자의 UI 언어에서 문자열을 검색 하려면 cmdlet을 사용 `Import-LocalizedData` 합니다.

`Import-LocalizedData` 자동 변수의 값을 찾아 해당 `$PSUICulture` `<script-name>.psd1` 값과 일치 하는 하위 디렉터리에 있는 파일의 내용을 가져옵니다 `$PSUICulture` . 그런 다음 **bindingvariable** 매개 변수의 값으로 지정 된 변수에 가져온 콘텐츠를 저장 합니다.

```powershell
Import-LocalizedData -BindingVariable msgTable
```

예를 들어 `Import-LocalizedData` 명령이 스크립트에 표시 되 `C:\Scripts\World.ps1` 고의 값 `$PSUICulture` 이 "ar-SA" 이면 `Import-LocalizedData` 다음 파일을 찾습니다.

`C:\Scripts\ar-SA\World.psd1`

그런 다음 파일에서 변수로 아랍어 텍스트 문자열을 가져와 `$msgTable` 스크립트의 데이터 섹션에서 정의 될 수 있는 기본 문자열을 대체 합니다 `World.ps1` .

따라서 스크립트에서 변수를 사용 하 여 `$msgTable` 사용자 메시지를 표시할 때 메시지는 아랍어로 표시 됩니다.

예를 들어 다음 스크립트는 아랍어의 "사용자 이름을 입력 하십시오." 메시지를 표시 합니다.

```powershell
if (!($username)) { $msgTable.promptMsg }
```

`Import-LocalizedData` `.psd1` 가의 값과 일치 하는 파일을 찾을 수 없는 경우 `$PSUIculture` 의 값은 `$msgTable` 대체 되지 않으며에 대 한 호출은 `$msgTable.promptMsg` 대체 en-us 문자열을 표시 합니다.

## <a name="examples"></a>예

이 예에서는 스크립트에서 스크립트 국제화 기능을 사용 하 여 컴퓨터에 설정 된 언어로 사용자에 게 요일을 표시 하는 방법을 보여 줍니다.

다음은 Sample1.ps1 스크립트 파일의 전체 목록입니다.

이 스크립트는 명령을 포함 하는 Day ($Day) 라는 데이터 섹션으로 시작 합니다 `ConvertFrom-StringData` . 에 제출 된 식은 `ConvertFrom-StringData` 키/값 쌍의 기본 UI 문화권 en-us에서 요일 이름을 포함 하는 문자열입니다. `ConvertFrom-StringData`Cmdlet은이 문자열의 키/값 쌍을 해시 테이블로 변환한 다음 변수 값에 저장 합니다 `$Day` .

`Import-LocalizedData` `.psd1` 이 명령은 자동 변수의 값과 일치 하는 디렉터리에 있는 파일의 내용을 가져온 `$PSUICulture` 다음 변수에 저장 하 여 `$Day` `$Day` 데이터 섹션에 정의 된 값을 대체 합니다.

나머지 명령은 문자열을 배열로 로드 하 고 표시 합니다.

```powershell
$Day = Data {
#culture="en-US"
ConvertFrom-StringData -StringData @'
    messageDate = Today is
    d0 = Sunday
    d1 = Monday
    d2 = Tuesday
    d3 = Wednesday
    d4 = Thursday
    d5 = Friday
    d6 = Saturday
'@
}

Import-LocalizedData -BindingVariable Day

#Build an array of weekdays.
$a = $Day.d0, $Day.d1, $Day.d2, $Day.d3, $Day.d4, $Day.d5, $Day.d6

# Get the day of the week as a number (Monday = 1).
# Index into $a to get the name of the day.
# Use string formatting to build a sentence.

"{0} {1}" -f $Day.messageDate, $a[(Get-Date -UFormat %u)] | Out-Host
```

`.psd1`스크립트를 지 원하는 파일은 해당 값과 일치 하는 이름을 가진 스크립트 디렉터리의 하위 디렉터리에 저장 됩니다 `$PSUICulture` .

다음은의 전체 목록입니다 `.\de-DE\sample1.psd1` .

```powershell
# culture="de-DE"
ConvertFrom-StringData @'
    messageDate = Heute ist
    d0 = Sonntag
    d1 = Montag
    d2 = Dienstag
    d3 = Mittwoch
    d4 = Donnerstag
    d5 = Freitag
    d6 = Samstag
'@
```

따라서 값이 de-de 인 시스템에서 Sample.ps1를 실행 하는 경우 `$PSUICulture` 스크립트의 출력은 다음과 같습니다.

```Output
Heute ist Freitag
```

## <a name="see-also"></a>참고 항목

- [about_Data_Sections](about_Data_Sections.md)
- [about_Automatic_Variables](about_Automatic_Variables.md)
- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Quoting_Rules](about_Quoting_Rules.md)
- [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
- [Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

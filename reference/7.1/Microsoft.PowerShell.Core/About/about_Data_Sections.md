---
description: 스크립트 논리에서 텍스트 문자열과 기타 읽기 전용 데이터를 격리 하는 데이터 섹션에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_data_sections?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Data_Sections
ms.openlocfilehash: a5eed0056fe572760415f62537b5a69942d819ae
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222121"
---
# <a name="about-data-sections"></a>데이터 섹션 정보

## <a name="short-description"></a>간단한 설명
스크립트 논리에서 텍스트 문자열과 기타 읽기 전용 데이터를 격리 하는 데이터 섹션에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell 용으로 설계 된 스크립트에는 데이터만 포함 된 하나 이상의 데이터 섹션이 있을 수 있습니다. 모든 스크립트, 함수 또는 고급 함수에 하나 이상의 데이터 섹션을 포함할 수 있습니다. 데이터 섹션의 내용은 PowerShell 스크립트 언어의 지정 된 하위 집합으로 제한 됩니다.

코드 논리에서 데이터를 분리 하면 논리와 데이터를 더 쉽게 식별 하 고 관리할 수 있습니다. 오류 메시지 및 도움말 문자열과 같은 텍스트에 대 한 별도의 문자열 리소스 파일을 사용할 수 있습니다. 또한 보안 및 유효성 검사 테스트를 용이 하 게 하는 코드 논리를 격리 합니다.

PowerShell에서 데이터 섹션은 스크립트 국제화를 지 원하는 데 사용 됩니다.
데이터 섹션을 사용 하 여 여러 UI (사용자 인터페이스) 언어로 변환 되는 문자열을 보다 쉽게 격리 하 고 찾고 처리할 수 있습니다.

데이터 섹션은 PowerShell 2.0 기능입니다. 데이터 섹션이 포함 된 스크립트는 수정 없이 PowerShell 1.0에서 실행 되지 않습니다.

### <a name="syntax"></a>구문

데이터 섹션의 구문은 다음과 같습니다.

```
DATA [<variable-name>] [-supportedCommand <cmdlet-name>] {
    <Permitted content>
}
```

Data 키워드가 필요 합니다. 대/소문자를 구분하지 않습니다. 허용 되는 콘텐츠는 다음 요소로 제한 됩니다.

- 모든 PowerShell 연산자 (제외) `-match`
- `If`, `Else` 및 `ElseIf` 문
- 자동 변수는,, `$PsCulture` `$PsUICulture` `$True` , `$False` 및입니다. `$Null`
- 주석
- 파이프라인
- 세미콜론 ()으로 구분 된 문 `;`
- 다음과 같은 리터럴입니다.

  ```powershell
  a
  1
  1,2,3
  "PowerShell 2.0"
  @( "red", "green", "blue" )
  @{ a = 0x1; b = "great"; c ="script" }
  [XML] @'
  <p> Hello, World </p>
  '@
  ```

- 데이터 섹션에서 허용 되는 cmdlet입니다. 기본적으로 `ConvertFrom-StringData` cmdlet만 허용 됩니다.
- 매개 변수를 사용 하 여 데이터 섹션에서 허용 하는 cmdlet입니다 `-SupportedCommand` .

데이터 섹션에서 cmdlet을 사용 하는 경우 `ConvertFrom-StringData` 키-값 쌍을 작은따옴표 또는 큰따옴표로 묶은 문자열이 나 작은따옴표로 묶은 작은따옴표 또는 큰따옴표로 묶을 수 있습니다. 그러나 변수와 부분식을 포함 하는 문자열은 변수가 확장 되지 않고 하위 식이 실행 되지 않도록 작은따옴표로 묶은 문자열 또는 작은따옴표로 묶은 작은따옴표로 묶어야 합니다.

### <a name="-supportedcommand"></a>-SupportedCommand

`-SupportedCommand`매개 변수를 사용 하 여 cmdlet 또는 함수에서 데이터만 생성 하도록 지정할 수 있습니다. 사용자가 작성 하거나 테스트 한 데이터 섹션에 cmdlet 및 함수를 포함할 수 있도록 설계 되었습니다.

값은 `-SupportedCommand` 하나 이상의 cmdlet 또는 함수 이름의 쉼표로 구분 된 목록입니다.

예를 들어 다음 데이터 섹션에는 `Format-XML` XML 파일의 데이터 형식을 지정 하는 사용자 작성 cmdlet이 포함 되어 있습니다.

```powershell
DATA -supportedCommand Format-Xml
{
    Format-Xml -Strings string1, string2, string3
}
```

### <a name="using-a-data-section"></a>데이터 섹션 사용

데이터 섹션의 내용을 사용 하려면 변수를 변수에 할당 하 고 변수 표기법을 사용 하 여 콘텐츠에 액세스 합니다.

예를 들어 다음 데이터 섹션에는 `ConvertFrom-StringData` 문자열을 해시 테이블로 변환 하는 명령이 포함 되어 있습니다. 해시 테이블은 변수에 할당 됩니다 `$TextMsgs` .

`$TextMsgs`변수가 데이터 섹션의 일부가 아닙니다.

```powershell
$TextMsgs = DATA {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

에서 해시 테이블의 키 및 값에 액세스 하려면 `$TextMsgs` 다음 명령을 사용 합니다.

```powershell
$TextMsgs.Text001
$TextMsgs.Text002
```

또는 변수 이름을 데이터 섹션의 정의에 배치할 수 있습니다. 다음은 그 예입니다. 

```powershell
DATA TextMsgs {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}

$TextMsgs
```

결과는 이전 예제와 동일 합니다.

```Output
Name                           Value
----                           -----
Text001                        Windows 7
Text002                        Windows Server 2008 R2
```

### <a name="examples"></a>예

단순 데이터 문자열.

```powershell
DATA {
    "Thank you for using my PowerShell Organize.pst script."
    "It is provided free of charge to the community."
    "I appreciate your comments and feedback."
}
```

허용 된 변수를 포함 하는 문자열입니다.

```powershell
DATA {
    if ($null) {
        "To get help for this cmdlet, type get-help new-dictionary."
    }
}
```

Cmdlet을 사용 하는 작은따옴표로 묶은 문자열입니다 `ConvertFrom-StringData` .

```powershell
DATA {
    ConvertFrom-StringData -stringdata @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

Cmdlet을 사용 하는 큰따옴표로 묶인 문자열입니다 `ConvertFrom-StringData` .

```powershell
DATA  {
    ConvertFrom-StringData -stringdata @"
Msg1 = To start, press any key.
Msg2 = To exit, type "quit".
"@
}
```

데이터를 생성 하는 사용자 작성 cmdlet을 포함 하는 데이터 섹션:

```powershell
DATA -supportedCommand Format-XML {
    Format-Xml -strings string1, string2, string3
}
```

## <a name="see-also"></a>참고 항목

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_If](about_If.md)

[about_Operators](about_Operators.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Script_Internationalization](about_Script_Internationalization.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)


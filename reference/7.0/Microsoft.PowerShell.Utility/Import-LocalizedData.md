---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-localizeddata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-LocalizedData
ms.openlocfilehash: 8a68b81df81f281e5aac3128430c90525f83aed4
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239874"
---
# Import-LocalizedData

## 개요
운영 체제에 대해 선택한 UI 문화권을 기준으로 하여 언어별 데이터를 스크립트 및 함수로 가져옵니다.

## SYNTAX

```
Import-LocalizedData [[-BindingVariable] <String>] [[-UICulture] <String>] [-BaseDirectory <String>]
 [-FileName <String>] [-SupportedCommand <String[]>] [<CommonParameters>]
```

## 설명

`Import-LocalizedData`Cmdlet은 이름이 운영 체제의 현재 사용자에 대해 설정 된 UI 언어와 일치 하는 하위 디렉터리에서 문자열을 동적으로 검색 합니다. 이 cmdlet을 통해 스크립트는 현재 사용자가 선택한 UI 언어로 사용자 메시지를 표시할 수 있습니다.

`Import-LocalizedData``.psd1`스크립트 디렉터리의 언어별 하위 디렉터리에 있는 파일에서 데이터를 가져와 명령에 지정 된 지역 변수에 저장 합니다. Cmdlet은 자동 변수의 값을 기준으로 하위 디렉터리 및 파일을 선택 합니다 `$PSUICulture` . 스크립트의 지역 변수를 사용하여 사용자 메시지를 표시하는 경우 메시지는 사용자의 UI 언어로 표시됩니다.

의 매개 변수를 사용 하 여 `Import-LocalizedData` 대체 UI 문화권, 경로 및 파일 이름을 지정 하 고, 지원 되는 명령을 추가 하 고, 파일을 찾을 수 없는 경우 표시 되는 오류 메시지를 표시 하지 않을 수 있습니다 `.psd1` .

`Import-LocalizedData`Cmdlet은 Windows PowerShell 2.0에 도입 된 스크립트 국제화 이니셔티브를 지원 합니다. 이 이니셔티브는 스크립트에서 사용자 메시지를 현재 사용자의 UI 언어로 쉽게 표시할 수 있도록 설정하여 전 세계 사용자에게 더 나은 서비스를 제공하기 위한 것입니다. 이에 대 한 자세한 내용과 파일 형식에 대 한 자세한 내용은 `.psd1` [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)를 참조 하세요.

## 예제

### 예제 1: 텍스트 문자열 가져오기

이 예에서는 텍스트 문자열을 `$Messages` 변수로 가져옵니다. 그리고 다른 모든 cmdlet의 매개 변수에 기본값을 사용합니다.

```powershell
Import-LocalizedData -BindingVariable "Messages"
```

명령이 디렉터리의 Archives.ps1 스크립트에 포함 되 `C:\Test` 고 `$PsUICulture` 자동 변수 값이 zh-cn 인 경우는 `Import-LocalizedData` `Archives.psd1` 디렉터리의 파일을 `C:\test\zh-CN` 변수로 가져옵니다 `$Messages` .

### 예제 2: 지역화 된 데이터 문자열 가져오기

이 예제는 스크립트가 아닌 명령줄에서 실행 됩니다. Test.psd1 파일에서 지역화된 데이터를 가져와 명령줄에 표시합니다. 이 명령은 스크립트에서 사용되지 않으므로 **FileName** 매개 변수는 필수입니다. 이 명령은 **UICulture** 매개 변수를 사용 하 여 en-us 문화권을 지정 합니다.

```powershell
Import-LocalizedData -FileName "Test.psd1" -UICulture "en-US"
```

```Output
Name                           Value
----                           -----
Msg3                           "Use $_ to represent the object that is being processed."
Msg2                           "This command requires the credentials of a member of the Administrators group on the...
Msg1                           "The Name parameter is missing from the command."
```

`Import-LocalizedData` 지역화 된 데이터 문자열을 포함 하는 해시 테이블을 반환 합니다.

### 예제 3: UI 문화권 문자열 가져오기

```powershell
Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

이 명령은 텍스트 문자열을 `$MsgTbl` 스크립트의 변수로 가져옵니다.

**UICulture** 매개 변수를 사용 하 여 cmdlet이 `Simple.psd1` 의 하위 디렉터리에 있는 파일에서 데이터를 가져오도록 지시 합니다 `ar-SA` `C:\Data\Localized` .

### 예제 4: 스크립트로 지역화 된 데이터 가져오기

이 예제에서는 간단한 스크립트에서 데이터를 지역화하는 방법을 보여 줍니다.

```powershell
PS C:\> # In C:\Test\en-US\Test.psd1:

ConvertFrom-StringData @'

# English strings

Msg1 = "The Name parameter is missing from the command."
Msg2 = "This command requires the credentials of a member of the Administrators group on the computer."
Msg3 = "Use $_ to represent the object that is being processed."
'@

# In C:\Test\Test.ps1

Import-LocalizedData -BindingVariable "Messages"
Write-Host $Messages.Msg2

# In Windows PowerShell

PS C:\> .\Test.ps1

This command requires the credentials of a member of the Administrators group on the computer.
```

이 예제의 첫 번째 부분에서는 파일의 내용을 보여 줍니다 `Test.psd1` . 여기에는 `ConvertFrom-StringData` 일련의 명명 된 텍스트 문자열을 해시 테이블로 변환 하는 명령이 포함 되어 있습니다. `Test.psd1`이 파일은 `C:\Test` 스크립트가 포함 된 디렉터리의 en-us 하위 디렉터리에 있습니다.

예제의 두 번째 부분에서는 스크립트의 내용을 보여 줍니다 `Test.ps1` . 이 파일에는 `Import-LocalizedData` 일치 하는 파일에서 변수로 데이터를 가져오는 명령과 `.psd1` `$Messages` `Write-Host` 변수에 있는 메시지 중 하나를 `$Messages` 호스트 프로그램에 기록 하는 명령이 포함 되어 있습니다.

이 예제의 마지막 부분에서는 스크립트를 실행합니다. 출력을 보면 운영 체제의 현재 사용자에 대해 설정된 UI 언어로 올바른 사용자 메시지가 표시되는 것을 확인할 수 있습니다.

### 예 5: 스크립트에서 기본 텍스트 문자열 바꾸기

이 예에서는를 사용 하 여 `Import-LocalizedData` 스크립트의 데이터 섹션에 정의 된 기본 텍스트 문자열을 바꾸는 방법을 보여 줍니다.

```powershell
PS C:\> # In TestScript.ps1
$UserMessages = DATA

{    ConvertFrom-StringData @'

    # English strings

        Msg1 = "Enter a name."
        Msg2 = "Enter your employee ID."
        Msg3 = "Enter your building number."
'@
}

Import-LocalizedData -BindingVariable "UserMessages"
$UserMessages.Msg1...
```

이 예에서 TestScript.ps1 스크립트의 데이터 섹션에는 `ConvertFrom-StringData` 데이터 섹션의 내용을 해시 테이블로 변환 하 고 변수 값에 저장 하는 명령이 포함 되어 있습니다 `$UserMessages` .

스크립트에는 `Import-LocalizedData` 변수 값으로 지정 된 하위 디렉터리의 TestScript.psd1 파일에서 번역 된 텍스트 문자열의 해시 테이블을 가져오는 명령도 포함 되어 있습니다 `$PsUICulture` . 이 명령은 파일을 찾은 경우 `.psd1` 파일의 번역 된 문자열을 동일한 변수의 값에 저장 `$UserMessages` 하 여 데이터 섹션 논리에 의해 저장 된 해시 테이블을 덮어씁니다.

세 번째 명령은 변수의 첫 번째 메시지를 표시 합니다 `$UserMessages` .

명령에서 `Import-LocalizedData` `.psd1` 언어에 대 한 파일을 찾은 경우 `$PsUICulture` 변수 값에는 `$UserMessages` 번역 된 텍스트 문자열이 포함 됩니다. 어떤 이유로든 명령이 실패하면 명령이 스크립트의 DATA 섹션에 정의된 기본 텍스트 문자열을 표시합니다.

### 예제 6: UI 문화권을 찾을 수 없는 경우 오류 메시지 표시 안 함

이 예제에서는 `Import-LocalizedData` 가 사용자의 UI 문화권과 일치 하는 디렉터리를 찾을 수 없거나 `.psd1` 해당 디렉터리에서 스크립트에 대 한 파일을 찾을 수 없는 경우 표시 되는 오류 메시지를 표시 하지 않도록 하는 방법을 보여 줍니다.

```powershell
PS C:\> # In Day1.ps1

Import-LocalizedData -BindingVariable "Day"

# In Day2.ps1

Import-LocalizedData -BindingVariable "Day" -ErrorAction:SilentlyContinue

PS C:\> .\Day1.ps1
Import-LocalizedData : Cannot find PowerShell data file 'Day1.psd1' in directory 'C:\ps-test\fr-BE\' or any parent culture directories.
At C:\ps-test\Day1.ps1:17 char:21+ Import-LocalizedData <<<<  Day
Today is Tuesday

PS C:\> .\Day2.ps1
Today is Tuesday
```

SilentlyContinue 값과 함께 **Erroraction** 일반 매개 변수를 사용 하 여 오류 메시지를 표시 하지 않을 수 있습니다. 이는 기본 또는 대체 언어로 사용자 메시지를 제공 하 고 오류 메시지가 필요 하지 않은 경우에 특히 유용 합니다.

이 예제에서는 `Day1.ps1` 명령을 포함 하는 두 개의 스크립트와 Day2.ps1를 비교 `Import-LocalizedData` 합니다. 출력만는 값이 인 **Erroraction** 일반 매개 변수를 사용 한다는 점을 제외 하 고 스크립트는 동일 `SilentlyContinue` 합니다.

샘플 출력에서는 UI 문화권이로 설정 되 `fr-BE` 고 해당 ui 문화권에 일치 하는 파일 또는 디렉터리가 없을 때 두 스크립트를 모두 실행 한 결과를 보여 줍니다. `Day1.ps1` 오류 메시지 및 영어 출력을 표시 합니다. `Day2.ps1` 영어 출력만 표시 합니다.

## PARAMETERS

### -BaseDirectory

파일이 있는 기본 디렉터리를 지정 합니다 `.psd1` . 기본값은 스크립트가 있는 디렉터리입니다. `Import-LocalizedData``.psd1`기본 디렉터리의 언어별 하위 디렉터리에서 스크립트에 대 한 파일을 검색 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BindingVariable

텍스트 문자열을 가져와 넣을 변수를 지정합니다. 달러 기호 () 없이 변수 이름을 입력 `$` 합니다.

Windows PowerShell 2.0에서는 이 매개 변수가 필수이지만 Windows PowerShell 3.0에서는 이 매개 변수가 선택 사항입니다. 이 매개 변수를 생략 하면는 `Import-LocalizedData` 텍스트 문자열의 해시 테이블을 반환 합니다. 해시 테이블은 파이프라인으로 전달되거나 명령줄에 표시됩니다.

를 사용 하 여 `Import-LocalizedData` 스크립트의 데이터 섹션에 지정 된 기본 텍스트 문자열을 바꿀 때 데이터 섹션을 변수에 할당 하 고 **bindingvariable** 매개 변수 값에 data section 변수의 이름을 입력 합니다. 그러면에서 `Import-LocalizedData` 가져온 콘텐츠를 **bindingvariable** 에 저장할 때 가져온 데이터는 기본 텍스트 문자열을 대체 합니다. 기본 텍스트 문자열을 지정하지 않으면 어떤 변수 이름이든 선택할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Variable

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FileName

가져올 데이터 파일의 이름을 지정 합니다 `.psd1)` . 파일 이름을 입력합니다. 파일 이름 확장명을 포함 하지 않는 파일 이름을 지정 하거나 파일 이름 확장명을 포함 하는 파일 이름을 지정할 수 있습니다 `.psd1` `.psd1` . 데이터 파일은 Unicode 또는 u t f-8로 저장 해야 합니다.

**파일 이름** 매개 변수는 `Import-LocalizedData` 가 스크립트에서 사용 되지 않는 경우에 필요 합니다.
그러지 않으면 이 매개 변수는 선택 사항이며 기본값은 스크립트의 기본 이름입니다. 이 매개 변수를 사용 하 여 `Import-LocalizedData` 다른 파일을 검색 하도록 지시할 수 있습니다 `.psd1` .

예를 들어 **파일 이름이** 생략 되 고 스크립트 이름이 FindFiles.ps1 인 경우는 `Import-LocalizedData` FindFiles.psd1 데이터 파일을 검색 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportedCommand

데이터만 생성하는 cmdlet 및 함수를 지정합니다.

이 매개 변수를 사용하면 사용자가 작성하거나 테스트한 cmdlet 및 함수를 포함할 수 있습니다. 자세한 내용은 [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)를 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UICulture

대체 UI 문화권을 지정합니다.
기본값은 `$PsUICulture` 자동 변수의 값입니다.
UI 문화권을 형식 (예 `<language>-<region>` :, 또는)으로 입력 `en-US` `de-DE` `ar-SA` 합니다.

**UICulture** 매개 변수 값은 `Import-LocalizedData` `.psd1` 스크립트에 대 한 파일을 가져오는의 언어별 하위 디렉터리 (기본 디렉터리 내)를 결정 합니다.

Cmdlet은 **UICulture** 매개 변수 값과 같은 이름 또는 `$PsUICulture` 자동 변수 (예: 또는)를 사용 하 여 하위 디렉터리를 검색 합니다 `de-DE` `ar-SA` . 디렉터리를 찾을 수 없거나 디렉터리에 스크립트에 대 한 파일이 포함 되어 있지 않은 경우에는 `.psd1` 언어 코드 (예: de 또는 ar)의 이름을 사용 하 여 하위 디렉터리를 검색 합니다. 하위 디렉터리 또는 파일을 찾을 수 없는 경우 `.psd1` 명령이 실패 하 고 데이터가 스크립트에 지정 된 기본 언어로 표시 됩니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### System.Collections.Hashtable

`Import-LocalizedData`**bindingvariable** 매개 변수의 값으로 지정 된 변수에 해시 테이블을 저장 합니다.

## 참고

- 를 사용 하기 전에 `Import-LocalizedData` 사용자 메시지를 지역화 합니다. 키-값 쌍의 해시 테이블에서 각 로캘 (UI 문화권)에 대 한 메시지의 형식을 지정 하 고, 스크립트 및 파일 이름 확장명과 이름이 같은 파일에 해시 테이블을 저장 `.psd1` 합니다. 지원 되는 각 UI 문화권에 대 한 스크립트 디렉터리에 디렉터리를 만든 다음 `.psd1` ui 문화권 이름을 사용 하 여 디렉터리에 각 ui 문화권에 대 한 파일을 저장 합니다.

  예를 들어 사용자 메시지를 de-DE 로캘로 지역화하여 해시 테이블에서 해당 메시지의 형식을 지정하고,
  해시 테이블을 파일에 저장 `<ScriptName>.psd1` 합니다. 그런 다음 `de-DE` 스크립트 디렉터리 아래에 하위 디렉터리를 만들고 독일어 파일을 `<ScriptName\>.psd1` `de-DE` 하위 디렉터리에 저장 합니다.
  지원하는 각 로캘에 대해 이 방법을 반복합니다.

- `Import-LocalizedData` 스크립트에 대 한 지역화 된 사용자 메시지에 대해 구조화 된 검색을 수행 합니다.

  `Import-LocalizedData` 스크립트 파일이 있는 디렉터리 (또는 **BaseDirectory** 매개 변수 값)에서 검색을 시작 합니다. 그런 다음 기본 디렉터리 내에서 `$PsUICulture` 또는와 같은 변수 값 (또는 **UICulture** 매개 변수 값)과 동일한 이름의 하위 디렉터리를 검색 합니다 `de-DE` `ar-SA` . 그런 다음 `.psd1` 스크립트 (또는 **FileName** 매개 변수 값)와 이름이 같은 파일을 해당 하위 디렉터리에서 검색 합니다.

  에서 `Import-LocalizedData` UI 문화권의 이름을 가진 하위 디렉터리를 찾을 수 없거나 하위 디렉터리에 스크립트에 대 한 파일이 포함 되어 있지 않은 경우에는 `.psd1` `.psd1` 언어 코드 (예: de 또는 ar)의 이름을 사용 하 여 하위 디렉터리에서 스크립트에 대 한 파일을 검색 합니다. 하위 디렉터리 또는 파일을 찾을 수 없는 경우 `.psd1` 명령이 실패 하 고 데이터가 스크립트의 기본 언어로 표시 되 고 데이터를 가져올 수 없다는 오류 메시지가 표시 됩니다. 메시지를 표시 하지 않고 정상적으로 실패 하려면 SilentlyContinue 값과 함께 **Erroraction** 일반 매개 변수를 사용 합니다.

  `Import-LocalizedData`에서 하위 디렉터리와 `.psd1` 파일을 찾으면 사용자 메시지의 해시 테이블을 명령의 **bindingvariable** 매개 변수 값으로 가져옵니다. 그러면 해시 테이블의 메시지를 변수에 표시할 때 지역화된 메시지가 표시됩니다.

  자세한 내용은 [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md)를 참조 하세요.

## 관련 링크

[Write-Host](Write-Host.md)

[Import-PowerShellDataFile](Import-PowerShellDataFile.md)

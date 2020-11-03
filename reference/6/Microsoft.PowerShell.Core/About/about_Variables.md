---
description: 변수가 PowerShell에서 사용할 수 있는 값을 저장 하는 방법에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: e301d323fff8f8519c60f8916a019acea324a589
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221050"
---
# <a name="about-variables"></a>변수 정보

## <a name="short-description"></a>간단한 설명

변수가 PowerShell에서 사용할 수 있는 값을 저장 하는 방법에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

모든 유형의 값을 PowerShell 변수에 저장할 수 있습니다. 예를 들어 명령 결과를 저장 하 고 명령 및 식에 사용 되는 요소 (예: 이름, 경로, 설정 및 값)를 저장 합니다.

변수는 값이 저장 되는 메모리의 단위입니다. PowerShell에서 변수는 `$` , 또는와 같이 달러 기호 ()로 시작 하는 텍스트 문자열로 표시 됩니다 `$a` `$process` `$my_var` .

변수 이름은 대/소문자를 구분 하지 않으며 공백과 특수 문자를 포함할 수 있습니다. 그러나 특수 문자 및 공백을 포함 하는 변수 이름은 사용 하기 어렵고 사용 하지 않아야 합니다. 자세한 내용은 [특수 문자를 포함 하는 변수 이름](#variable-names-that-include-special-characters)을 참조 하세요.

PowerShell에는 여러 가지 유형의 변수가 있습니다.

- 사용자가 만든 변수: 사용자가 만든 변수를 사용자가 만들고 유지 관리 합니다. 기본적으로 powershell 명령줄에서 만든 변수는 PowerShell 창이 열려 있는 동안에만 존재 합니다. PowerShell 창이 닫히면 변수가 삭제 됩니다. 변수를 저장 하려면 PowerShell 프로필에 변수를 추가 합니다. 전역, 스크립트 또는 로컬 범위를 사용 하 여 스크립트에서 변수를 만들 수도 있습니다.

- 자동 변수: 자동 변수는 PowerShell의 상태를 저장 합니다. 이러한 변수는 PowerShell에서 만들어지며 PowerShell은 정확성을 유지 하기 위해 필요에 따라 해당 값을 변경 합니다. 사용자는 이러한 변수의 값을 변경할 수 없습니다. 예를 들어 `$PSHOME` 변수는 PowerShell 설치 디렉터리에 대 한 경로를 저장 합니다.

  자동 변수에 대 한 자세한 내용, 목록 및 설명은 [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.

- 기본 설정 변수: 기본 설정 변수는 PowerShell에 대 한 사용자 기본 설정을 저장 합니다. 이러한 변수는 PowerShell에서 만들어지며 기본값으로 채워집니다. 사용자는 이러한 변수의 값을 변경할 수 있습니다. 예를 들어 `$MaximumHistoryCount` 변수는 세션 기록의 최대 항목 수를 결정 합니다.

  기본 설정 변수에 대 한 자세한 내용, 목록 및 설명은 [about_Preference_Variables](about_Preference_Variables.md)를 참조 하세요.

## <a name="working-with-variables"></a>변수 작업

새 변수를 만들려면 대입문을 사용 하 여 변수에 값을 할당 합니다. 변수를 사용 하기 전에 선언 하지 않아도 됩니다. 모든 변수의 기본값은 `$null` 입니다.

PowerShell 세션의 모든 변수 목록을 가져오려면를 입력 `Get-Variable` 합니다. 변수 이름은 `$` 변수를 참조 하는 데 사용 되는 앞에 달러 () 기호 없이 표시 됩니다.

다음은 그 예입니다. 

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

변수는 명령 결과를 저장 하는 데 유용 합니다.

다음은 그 예입니다. 

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

변수의 값을 표시 하려면 변수 이름 앞에 달러 기호 ()를 입력 `$` 합니다.

다음은 그 예입니다. 

```powershell
$MyVariable
```

```Output
1
2
3
```

```powershell
$Today
```

```Output
Tuesday, September 3, 2019 09:46:46
```

변수의 값을 변경 하려면 변수에 새 값을 할당 합니다.

다음 예에서는 변수의 값을 표시 `$MyVariable` 하 고 변수 값을 변경한 다음 새 값을 표시 합니다.

```powershell
$MyVariable = 1, 2, 3
$MyVariable
```

```Output
1
2
3
```

```powershell
$MyVariable = "The green cat."
$MyVariable
```

```Output
The green cat.
```

변수 값을 삭제 하려면 cmdlet을 사용 `Clear-Variable` 하거나 값을로 변경 `$null` 합니다.

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

변수를 삭제 하려면 [변수 제거](xref:Microsoft.PowerShell.Utility.Remove-Variable) 또는 [항목 제거](xref:Microsoft.PowerShell.Management.Remove-Item)를 사용 합니다.

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

## <a name="types-of-variables"></a>변수 유형

정수, 문자열, 배열 및 해시 테이블을 포함 하 여 모든 형식의 개체를 변수에 저장할 수 있습니다. 프로세스, 서비스, 이벤트 로그 및 컴퓨터를 나타내는 개체입니다.

PowerShell 변수는 느슨하게 형식화 됩니다. 즉, 특정 유형의 개체로 제한 되지 않습니다. 단일 변수에는 서로 다른 형식의 개체에 대 한 컬렉션 또는 배열을 동시에 포함할 수도 있습니다.

변수의 데이터 형식은 변수의 값에 대 한 .NET 형식에 의해 결정 됩니다. 변수의 개체 유형을 보려면 [Get 멤버](xref:Microsoft.PowerShell.Utility.Get-Member)를 사용 합니다.

다음은 그 예입니다. 

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

형식 특성 및 캐스트 표기법을 사용 하 여 해당 형식으로 변환할 수 있는 특정 개체 형식이 나 개체만이 변수에 포함 될 수 있도록 할 수 있습니다. 다른 형식의 값을 할당 하려고 하면 PowerShell에서 값을 해당 형식으로 변환 하려고 합니다. 형식을 변환할 수 없는 경우 대입문은 실패 합니다.

Cast 표기법을 사용 하려면 변수 이름 앞에 대괄호로 묶인 유형 이름 (대입문의 왼쪽에 있는)을 입력 합니다. 다음 예에서는 `$number` 정수만 포함할 수 있는 변수, 문자열만 포함할 수 있는 `$words` 변수 및 `$dates` **DateTime** 개체만 포함할 수 있는 변수를 만듭니다.

```powershell
[int]$number = 8
$number = "12345"  # The string is converted to an integer.
$number = "Hello"
```

```Output
Cannot convert value "Hello" to type "System.Int32". Error: "Input string was
 not in a correct format."
At line:1 char:1
+ $number = "Hello"
+ ~~~~~~~~~~~~~~~~~
+ CategoryInfo          : MetadataError: (:) [],
    ArgumentTransformationMetadataException
+ FullyQualifiedErrorId : RuntimeException
```

```powershell
[string]$words = "Hello"
$words = 2       # The integer is converted to a string.
$words += 10     # The plus (+) sign concatenates the strings.
$words
```

```Output
210
```

```powershell
[datetime] $dates = "09/12/91"  # The string is converted to a DateTime object.
$dates
```

```Output
Thursday, September 12, 1991 00:00:00
```

```powershell
$dates = 10    # The integer is converted to a DateTime object.
$dates
```

```Output
Monday, January 1, 0001 00:00:00
```

## <a name="using-variables-in-commands-and-expressions"></a>명령 및 식에서 변수 사용

명령 또는 식에서 변수를 사용 하려면 변수 이름 앞에 달러 () 기호를 입력 합니다 `$` .

변수 이름 및 달러 기호가 따옴표로 묶여 있지 않거나 큰따옴표 ()로 묶은 경우에는 `"` 변수 값이 명령 또는 식에 사용 됩니다.

변수 이름과 달러 기호가 작은따옴표 ()로 묶여 있으면 `'` 식에 변수 이름이 사용 됩니다.

PowerShell에서 따옴표를 사용 하는 방법에 대 한 자세한 내용은 [about_Quoting_Rules](about_Quoting_Rules.md)를 참조 하세요.

이 예에서는 `$PROFILE` powershell 콘솔의 powershell 사용자 프로필 파일 경로에 해당 하는 변수의 값을 가져옵니다.

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

이 예제에서는 **notepad.exe** 에서 PowerShell 프로필을 열 수 있는 두 명령이 표시 됩니다. 큰따옴표 () 표시가 있는 예제는 `"` 변수의 값을 사용 합니다.

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

다음 예에서는 `'` 변수를 리터럴 텍스트로 처리 하는 작은따옴표 ()를 사용 합니다.

```powershell
'$PROFILE'
```

```Output
$PROFILE
```

```powershell
'Use the $PROFILE variable.'
```

```Output
Use the $PROFILE variable.
```

## <a name="variable-names-that-include-special-characters"></a>특수 문자를 포함 하는 변수 이름

변수 이름은 달러 ( `$` ) 기호로 시작 하 고 영숫자 문자 및 특수 문자를 포함할 수 있습니다. 변수 이름 길이는 사용 가능한 메모리에 의해서만 제한 됩니다.

가장 좋은 방법은 변수 이름에 영숫자 문자와 밑줄 () 문자만 포함 하는 것입니다 `_` . 공백과 기타 특수 문자를 포함 하는 변수 이름은 사용 하기 어렵고 사용 하지 않아야 합니다.

영숫자 변수 이름에는 다음 문자를 사용할 수 있습니다.

- 이러한 범주의 유니코드 문자는 **Lu** , **Ll** , **Lt** , **Lm** ,가 **Lo** 중 또는 **Nd** 입니다.
- 밑줄 ( `_` ) 문자.
- 물음표 ( `?` ) 문자를 표시 합니다.

다음 목록에는 유니코드 범주 설명이 포함 되어 있습니다. 자세한 내용은 [자세한 내용은 system.globalization.unicodecategory](/dotnet/api/system.globalization.unicodecategory)를 참조 하세요.

- **Lu** -UppercaseLetter
- **Ll** -LowercaseLetter
- **Lt** -TitlecaseLetter
- **Lm** -ModifierLetter
- **가-** otherletter
- **Nd** -DecimalDigitNumber

공백 또는 특수 문자를 포함 하는 변수 이름을 만들거나 표시 하려면 변수 이름을 중괄호 ( `{}` ) 문자로 묶습니다.
변수 이름 문자를 리터럴로 해석 하는 중괄호 직접 PowerShell입니다.

특수 문자 변수 이름에는 다음 문자를 사용할 수 있습니다.

- 다음 예외를 제외 하 고 모든 유니코드 문자.
  - 닫는 중괄호 ( `}` ) 문자 (U + 007D)입니다.
  - 억음 ( `` ` `` ) 문자 (U + 0060)입니다. 억음은 리터럴로 처리 되도록 유니코드 문자를 이스케이프 하는 데 사용 됩니다.

PowerShell에는 `$$` `$?` `$^` `$_` 영숫자 및 특수 문자를 포함 하는,,, 등의 예약 된 변수가 있습니다. 자세한 내용은 [about_Automatic_Variables](about_automatic_variables.md)를 참조 하세요.

예를 들어 다음 명령은 라는 변수를 만듭니다 `save-items` . 변수 이름에는 `{}` 하이픈 () 특수 문자를 포함 하므로 중괄호 ()가 필요 합니다 `-` .

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

다음 명령은 환경 변수로 표시 되는 디렉터리의 자식 항목을 가져옵니다 `ProgramFiles(x86)` .

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

중괄호를 포함 하는 변수 이름을 참조 하려면 변수 이름을 중괄호로 묶고 중괄호를 이스케이프 하려면 억음 문자를 사용 합니다. 예를 들어 형식 이라는 변수를 만들려면 `this{value}is` 다음을 수행 합니다.

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a>변수 및 범위

기본적으로 변수는 생성 된 범위 에서만 사용할 수 있습니다.

예를 들어 함수에서 만든 변수는 함수 내 에서만 사용할 수 있습니다. 스크립트에서 만든 변수는 스크립트 내 에서만 사용할 수 있습니다. 스크립트를 점으로 원본으로 만들면 변수가 현재 범위에 추가 됩니다. 자세한 내용은 [about_Scopes](about_Scopes.md)를 참조 하세요.

범위 한정자를 사용 하 여 변수의 기본 범위를 변경할 수 있습니다. 다음 식에서는 라는 변수를 만듭니다 `Computers` . 변수는 스크립트나 함수에서 생성 된 경우에도 전역 범위를 가집니다.

```powershell
$Global:Computers = "Server01"
```

세션에서 실행 되지 않는 스크립트나 명령의 경우 범위 한정자를 사용 하 여 `Using` 호출 세션 범위의 변수 값을 포함 해야 합니다. 이렇게 하면 세션 외부 코드에서 해당 값에 액세스할 수 있습니다.

자세한 내용은 [about_Remote_Variables](about_Remote_Variables.md)를 참조 하세요.

## <a name="saving-variables"></a>변수 저장

만든 변수는 해당 변수를 만든 세션 에서만 사용할 수 있습니다. 세션을 닫으면 손실 됩니다.

시작 하는 모든 PowerShell 세션에서 변수를 만들려면 PowerShell 프로필에 변수를 추가 합니다.

예를 들어 `$VerbosePreference` 모든 powershell 세션에서 변수의 값을 변경 하려면 다음 명령을 powershell 프로필에 추가 합니다.

```powershell
$VerbosePreference = "Continue"
```

`$PROFILE` **notepad.exe** 와 같은 텍스트 편집기에서 파일을 열어 PowerShell 프로필에이 명령을 추가할 수 있습니다. PowerShell 프로필에 대 한 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.

## <a name="the-variable-drive"></a>변수: 드라이브

PowerShell 변수 공급자는 `Variable:` 파일 시스템 드라이브를 검색 하 고 작동 하는 드라이브를 만들지만 세션의 변수와 해당 값을 포함 합니다.

드라이브로 변경 하려면 `Variable:` 다음 명령을 사용 합니다.

```powershell
Set-Location Variable:
```

드라이브의 항목 및 변수를 나열 하려면 `Variable:` 또는 cmdlet을 사용 `Get-Item` `Get-ChildItem` 합니다.

```powershell
Get-ChildItem Variable:
```

특정 변수 값을 가져오려면 파일 시스템 표기법을 사용 하 여 드라이브의 이름과 변수의 이름을 지정 합니다. 예를 들어 `$PSCulture` 자동 변수를 가져오려면 다음 명령을 사용 합니다.

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

드라이브 및 PowerShell 변수 공급자에 대 한 자세한 정보를 표시 하려면 `Variable:` 다음을 입력 합니다.

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a>공급자 경로를 사용 하는 변수 구문

공급자 경로에 달러 ( `$` ) 기호를 접두사로 사용 하 고 [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) 인터페이스를 구현 하는 모든 공급자의 콘텐츠에 액세스할 수 있습니다.

다음 기본 제공 PowerShell 공급자는이 표기법을 지원 합니다.

- [about_Environment_Provider](about_Environment_Provider.md)
- [about_Variable_Provider](about_Variable_Provider.md)
- [about_Function_Provider](about_Function_Provider.md)
- [about_Alias_Provider](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a>변수 cmdlet

PowerShell에는 변수를 관리 하도록 설계 된 cmdlet 집합이 포함 되어 있습니다.

Cmdlet을 나열 하려면 다음을 입력 합니다.

```powershell
Get-Command -Noun Variable
```

특정 cmdlet에 대 한 도움말을 보려면 다음을 입력 합니다.

```powershell
Get-Help <cmdlet-name>
```

| Cmdlet 이름       | Description                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | 변수 값을 삭제합니다.           |
| `Get-Variable`    | 현재 콘솔에 있는 변수를 가져옵니다. |
| `New-Variable`    | 새 변수를 만듭니다.                    |
| `Remove-Variable` | 변수와 그 값을 삭제합니다.          |
| `Set-Variable`    | 변수의 값을 변경 합니다.           |

## <a name="see-also"></a>참고 항목

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Scopes](about_Scopes.md)

[about_Remote_Variables](about_Remote_Variables.md)

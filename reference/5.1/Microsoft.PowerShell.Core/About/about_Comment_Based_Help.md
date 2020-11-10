---
description: 함수 및 스크립트에 대 한 주석 기반 도움말 항목을 작성 하는 방법에 대해 설명 합니다.
keywords: powershell,cmdlet
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comment_based_help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comment_Based_Help
ms.openlocfilehash: c3e02edd6ca33f373b1632160e4a18dc4fb744f2
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94386974"
---
# <a name="about-comment-based-help"></a>주석 기반 도움말 정보

## <a name="short-description"></a>간단한 설명
함수 및 스크립트에 대 한 주석 기반 도움말 항목을 작성 하는 방법에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

특수 도움말 주석 키워드를 사용 하 여 함수 및 스크립트에 대 한 주석 기반 도움말 항목을 작성할 수 있습니다.

[Get-help](xref:Microsoft.PowerShell.Core.Get-Help) CMDLET은 XML 파일에서 생성 된 cmdlet 도움말 항목을 표시 하는 것과 동일한 형식으로 주석 기반 도움말을 표시 합니다. 사용자는 `Get-Help` **자세히** , **전체** , **예** 및 **온라인** 등의 모든 매개 변수를 사용 하 여 주석 기반 도움말의 내용을 표시할 수 있습니다.

함수 및 스크립트에 대 한 XML 기반 도움말 파일을 작성할 수도 있습니다. Cmdlet을 사용 하 여 `Get-Help` 함수 또는 스크립트에 대 한 XML 기반 도움말 파일을 찾으려면 키워드를 사용 `.ExternalHelp` 합니다. 이 키워드가 없으면 `Get-Help` 함수 또는 스크립트에 대 한 XML 기반 도움말 항목을 찾을 수 없습니다.

이 항목에서는 함수 및 스크립트에 대 한 도움말 항목을 작성 하는 방법에 대해 설명 합니다. 함수 및 스크립트에 대 한 도움말 항목을 표시 하는 방법에 대 한 자세한 내용은 [get-help](xref:Microsoft.PowerShell.Core.Get-Help)를 참조 하세요.

[Update-help](xref:Microsoft.PowerShell.Core.Update-Help) 및 [Save HELP](xref:Microsoft.PowerShell.Core.Save-Help) cmdlet은 XML 파일에 대해서만 작동 합니다. 업데이트할 수 있는 도움말은 주석 기반 도움말 항목을 지원 하지 않습니다.

## <a name="syntax-for-comment-based-help"></a>주석 기반 도움말 구문

주석 기반 도움말의 구문은 다음과 같습니다.

```
# .<help keyword>
# <help content>
```

또는

```
<#
.<help keyword>
<help content>
#>
```

주석 기반 도움말은 일련의 주석으로 작성 됩니다. 주석의 각 줄 앞에 주석 기호를 입력 `#` 하거나 `<#` 및 기호를 사용 하 여 `#>` 주석 블록을 만들 수 있습니다. 주석 블록 내의 모든 줄은 주석으로 해석 됩니다.

주석 기반 도움말 항목의 모든 줄은 연속적 이어야 합니다. 주석 기반 도움말 항목이 도움말 항목에 포함 되지 않은 주석을 따르는 경우에는 마지막으로 지원 되지 않는 주석 줄과 주석 기반 도움말의 시작 부분 사이에 하나 이상의 빈 줄이 있어야 합니다.

키워드는 주석 기반 도움말의 각 섹션을 정의 합니다. 각 주석 기반 도움말 키워드 앞에는 점이 `.` 있습니다. 키워드는 순서에 관계 없이 나타날 수 있습니다. 키워드 이름은 대/소문자를 구분 하지 않습니다.

예를 들어 키워드는 함수 또는 스크립트에 대 한 설명 앞에와 야 `.Description` 합니다.

```
<#
.Description
Get-Function displays the name and syntax of all functions in the session.
#>
```

주석 블록은 키워드를 하나 이상 포함 해야 합니다. 과 같은 일부 키워드는 `.EXAMPLE` 동일한 주석 블록에 여러 번 나타날 수 있습니다. 각 키워드에 대 한 도움말 콘텐츠는 키워드 뒤의 줄에서 시작 하 여 여러 줄에 걸쳐 있을 수 있습니다.

## <a name="syntax-for-comment-based-help-in-functions"></a>함수의 주석 기반 도움말 구문

함수에 대 한 주석 기반 도움말은 다음 세 위치 중 하나에 표시 될 수 있습니다.

- 함수 본문의 시작 부분에 있습니다.
- 함수 본문의 끝에 있습니다.
- 키워드 앞에 `function` 있습니다. 함수 도움말의 마지막 줄과 키워드 사이에는 빈 줄이 둘 이상 있을 수 없습니다 `function` .

예를 들면 다음과 같습니다.

```powershell
function Get-Function
{
<#
.<help keyword>
<help content>
#>

  # function logic
}
```

또는

```powershell
function Get-Function
{
   # function logic

<#
.<help keyword>
<help content>
#>
}
```

또는

```powershell
<#
.<help keyword>
<help content>
#>
function Get-Function { }
```

## <a name="syntax-for-comment-based-help-in-scripts"></a>스크립트의 주석 기반 도움말 구문

스크립트에 대 한 주석 기반 도움말은 스크립트의 다음 두 위치 중 하나에 표시 될 수 있습니다.

- 스크립트 파일의 시작 부분에 있습니다. 스크립트 도움말은 주석 및 빈 줄만 스크립트에 추가할 수 있습니다.

  스크립트 본문의 첫 번째 항목 (도움말)이 함수 선언 인 경우 스크립트 도움말과 함수 선언 끝 사이에 두 개 이상의 빈 줄이 있어야 합니다. 그렇지 않으면 도움말은 스크립트에 대 한 도움말이 아니라 함수에 대 한 도움말로 해석 됩니다.

- 스크립트 파일의 끝에 있습니다. 그러나 스크립트가 서명 된 경우 스크립트 파일의 시작 부분에 주석 기반 도움말을 추가 합니다. 스크립트 끝은 서명 블록에 의해 점유 됩니다.

예를 들면 다음과 같습니다.

```powershell
<#
.<help keyword>
<help content>
#>


function Get-Function { }
```

또는

```powershell
function Get-Function { }

<#
.<help keyword>
<help content>
#>
```

## <a name="syntax-for-comment-based-help-in-script-modules"></a>스크립트 모듈의 주석 기반 도움말 구문

스크립트 모듈에서 `.psm1` 주석 기반 도움말은 스크립트에 대 한 구문이 아니라 함수의 구문을 사용 합니다. 스크립트 모듈에 정의 된 모든 함수에 대 한 도움말을 제공 하기 위해 스크립트 구문을 사용할 수는 없습니다.

예를 들어 키워드를 사용 하 여 `.ExternalHelp` 스크립트 모듈의 함수에 대 한 XML 기반 도움말 파일을 식별 하는 경우 `.ExternalHelp` 각 함수에 주석을 추가 해야 합니다.

```powershell
# .ExternalHelp <XML-file-name>
function <function-name>
{
  ...
}
```

## <a name="comment-based-help-keywords"></a>주석 기반 도움말 키워드

다음은 유효한 주석 기반 도움말 키워드입니다. 이러한 항목은 일반적으로 원하는 용도와 함께 도움말 항목에 표시 되는 순서 대로 나열 됩니다. 이러한 키워드는 주석 기반 도움말에서 순서에 관계 없이 나타날 수 있으며 대/소문자를 구분 하지 않습니다.

### <a name="synopsis"></a>. 개요

함수 또는 스크립트에 대 한 간단한 설명입니다. 이 키워드는 각 항목에서 한 번만 사용할 수 있습니다.

### <a name="description"></a>. 한

함수 또는 스크립트에 대 한 자세한 설명입니다. 이 키워드는 각 항목에서 한 번만 사용할 수 있습니다.

### <a name="parameter"></a>. 변수에

매개 변수에 대 한 설명입니다. `.PARAMETER`함수 또는 스크립트 구문에서 각 매개 변수에 대 한 키워드를 추가 합니다.

키워드와 같은 줄에 매개 변수 이름을 입력 합니다 `.PARAMETER` . 키워드 뒤의 줄에 매개 변수 설명을 입력 합니다 `.PARAMETER` . Windows PowerShell은 `.PARAMETER` 줄과 다음 키워드나 주석 블록의 끝 사이에 있는 모든 텍스트를 매개 변수 설명의 일부로 해석 합니다.
설명에는 단락 나누기가 포함 될 수 있습니다.

```
.PARAMETER  <Parameter-Name>
```

매개 변수 키워드는 주석 블록에서 순서에 관계 없이 나타날 수 있지만 함수 또는 스크립트 구문은 도움말 항목에서 매개 변수 및 해당 설명이 표시 되는 순서를 결정 합니다. 순서를 변경 하려면 구문을 변경 합니다.

또한 함수에 주석을 추가 하거나 매개 변수 이름 바로 앞에 스크립트 구문을 추가 하 여 매개 변수 설명을 지정할 수 있습니다. 이 작업을 수행 하려면 키워드를 하나 이상 포함 하는 주석 블록만 있어야 합니다.

구문 주석과 키워드를 모두 사용 하는 경우 `.PARAMETER` 키워드와 연결 된 설명이 `.PARAMETER` 사용 되며 구문 주석이 무시 됩니다.

```powershell
<#
.SYNOPSIS
    Short description here
#>
function Verb-Noun {
    [CmdletBinding()]
    param (
        # This is the same as .Parameter
        [string]$Computername
    )
    # Verb the Noun on the computer
}
```

### <a name="example"></a>. 예 들어

함수 또는 스크립트를 사용 하 고 선택적으로 샘플 출력과 설명을 차례로 사용 하는 샘플 명령입니다. 각 예제에 대해이 키워드를 반복 합니다.

### <a name="inputs"></a>. 내용

함수 또는 스크립트로 파이프 될 수 있는 .NET 형식의 개체입니다. 입력 개체에 대 한 설명을 포함할 수도 있습니다.

### <a name="outputs"></a>. 출력

Cmdlet이 반환 하는 개체의 .NET 형식입니다. 반환 된 개체에 대 한 설명을 포함할 수도 있습니다.

### <a name="notes"></a>. 메모란

함수 또는 스크립트에 대 한 추가 정보입니다.

### <a name="link"></a>. 링크나

관련 항목의 이름입니다. 값은 "의 아래 줄에 표시 됩니다. LINK "키워드와 앞에는 주석 기호를 추가 `#` 하거나 주석 블록에 포함 해야 합니다.

`.LINK`각 관련 항목에 대해 키워드를 반복 합니다.

이 콘텐츠는 도움말 항목의 관련 링크 섹션에 나타납니다.

`.Link`키워드 콘텐츠에는 동일한 도움말 항목의 온라인 버전에 대 한 URI (Uniform Resource Identifier)가 포함 될 수도 있습니다. 온라인 버전은의 **online** 매개 변수를 사용할 때 열립니다 `Get-Help` . URI는 "http" 또는 "https"로 시작 해야 합니다.

### <a name="component"></a>. 구성 요소

함수나 스크립트에서 사용 하는 기술 또는 기능의 이름 또는 관련 된 기능입니다. 의 **구성 요소** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .

### <a name="role"></a>. 역할

도움말 항목에 대 한 사용자 역할의 이름입니다. 의 **Role** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .

### <a name="functionality"></a>. 기능성

함수의 용도를 설명 하는 키워드입니다. 의 **기능** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .

### <a name="forwardhelptargetname"></a>. FORWARDHELPTARGETNAME

지정 된 명령에 대 한 도움말 항목으로 리디렉션합니다. 함수, 스크립트, cmdlet 또는 공급자에 대 한 도움말 항목을 포함 하 여 사용자를 도움말 항목으로 리디렉션할 수 있습니다.

```powershell
# .FORWARDHELPTARGETNAME <Command-Name>
```

### <a name="forwardhelpcategory"></a>. FORWARDHELPCATEGORY

항목의 도움말 범주를 지정 합니다 `.ForwardHelpTargetName` . 유효한 값은,,,,,,,,,, `Alias` `Cmdlet` `HelpFile` `Function` `Provider` `General` `FAQ` `Glossary` `ScriptCommand` `ExternalScript` `Filter` 또는 `All` 입니다. 동일한 이름을 가진 명령이 있는 경우 충돌을 방지 하려면이 키워드를 사용 합니다.

```powershell
# .FORWARDHELPCATEGORY <Category>
```

### <a name="remotehelprunspace"></a>. REMOTEHELPRUNSPACE

도움말 항목을 포함 하는 세션을 지정 합니다. **PSSession** 개체를 포함 하는 변수를 입력 합니다. 이 키워드는 [내보내기 PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) cmdlet에서 내보낸 명령에 대 한 도움말 항목을 찾는 데 사용 됩니다.

```powershell
# .REMOTEHELPRUNSPACE <PSSession-variable>
```

### <a name="externalhelp"></a>. .EXTERNALHELP 설명을

스크립트나 함수에 대 한 XML 기반 도움말 파일을 지정 합니다.

```powershell
# .EXTERNALHELP <XML Help File>
```

`.ExternalHelp`키워드는 함수 또는 스크립트가 XML 파일에 설명 되어 있는 경우에 필요 합니다. 이 키워드가 없으면 `Get-Help` 함수 또는 스크립트에 대 한 XML 기반 도움말 파일을 찾을 수 없습니다.

`.ExternalHelp`키워드는 다른 주석 기반 도움말 키워드 보다 우선적으로 적용 됩니다. `.ExternalHelp`가 있는 경우는 `Get-Help` 키워드의 값과 일치 하는 도움말 항목을 찾을 수 없는 경우에도 주석 기반 도움말을 표시 하지 않습니다 `.ExternalHelp` .

모듈에서 함수를 내보내는 경우 키워드의 값을 `.ExternalHelp` 경로 없이 파일 이름으로 설정 합니다. `Get-Help` 모듈 디렉터리의 언어별 하위 디렉터리에서 지정 된 파일 이름을 찾습니다. 함수에 대 한 XML 기반 도움말 파일의 이름에 대 한 요구 사항은 없지만 다음 형식을 사용 하는 것이 가장 좋습니다.

```
<ScriptModule.psm1>-help.xml
```

함수가 모듈에 포함 되지 않은 경우 XML 기반 도움말 파일에 대 한 경로를 포함 합니다. 값에 경로가 포함 되 고 경로에 UI 문화권별 하위 디렉터리가 포함 된 경우는 `Get-Help` 모듈 디렉터리에서와 마찬가지로 Windows에 설정 된 언어 대체 표준에 따라 스크립트나 함수 이름을 사용 하 여 XML 파일에 대해 재귀적으로 하위 디렉터리를 검색 합니다.

Cmdlet 도움말 XML 기반 도움말 파일 형식에 대 한 자세한 내용은 [Cmdlet 도움말을 작성 하는 방법](/powershell/scripting/developer/help/writing-comment-based-help-topics)을 참조 하십시오.

## <a name="autogenerated-content"></a>자동으로 생성 되는 콘텐츠

이름, 구문, 매개 변수 목록, 매개 변수 특성 테이블, 일반 매개 변수 및 설명이 cmdlet에 의해 자동으로 생성 됩니다 `Get-Help` .

### <a name="name"></a>name

함수 도움말 항목의 **name** 섹션은 함수 구문의 함수 이름에서 가져옵니다. 스크립트 파일 이름에서 스크립트 도움말 항목의 **이름을** 가져옵니다. 이름 또는 해당 대문자 표시를 변경 하려면 함수 구문이 나 스크립트 파일 이름을 변경 합니다.

### <a name="syntax"></a>구문

도움말 항목의 **구문** 섹션은 함수 또는 스크립트 구문에서 생성 됩니다. 도움말 항목 구문 (예: .NET 형식의 매개 변수)에 세부 정보를 추가 하려면 구문에 세부 정보를 추가 합니다. 매개 변수 형식을 지정 하지 않으면 **개체** 형식이 기본값으로 삽입 됩니다.

### <a name="parameter-list"></a>매개 변수 목록

도움말 항목의 매개 변수 목록은 함수 또는 스크립트 구문과 키워드를 사용 하 여 추가 하는 설명에서 생성 됩니다 `.Parameter` . 함수 매개 변수는 함수 또는 스크립트 구문에 표시 되는 것과 동일한 순서로 도움말 항목의 **매개 변수** 섹션에 표시 됩니다. 매개 변수 이름의 철자 및 대/소문자도 구문에서 가져옵니다. 키워드에 지정 된 매개 변수 이름의 영향을 받지 않습니다 `.Parameter` .

### <a name="common-parameters"></a>일반 매개 변수

**일반 매개 변수** 는 영향을 주지 않는 경우에도 도움말 항목의 구문 및 매개 변수 목록에 추가 됩니다. 일반 매개 변수에 대 한 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조 하세요.

### <a name="parameter-attribute-table"></a>Parameter 특성 표

`Get-Help` 의 **Full** 또는 **parameter** 매개 변수를 사용할 때 표시 되는 매개 변수 특성의 테이블을 생성 합니다 `Get-Help` . **필수** , **위치** 및 **기본** 값 특성의 값은 함수 또는 스크립트 구문에서 가져옵니다.

함수 또는 스크립트에서 정의 된 경우에도 기본값 및 **와일드 카드 문자 허용** 값은 매개 변수 특성 테이블에 나타나지 않습니다. 사용자를 돕기 위해 매개 변수 설명에이 정보를 제공 합니다.

### <a name="remarks"></a>설명

도움말 항목의 **설명** 섹션은 함수 또는 스크립트 이름에서 자동으로 생성 됩니다. 콘텐츠를 변경 하거나 영향을 줄 수는 없습니다.

## <a name="examples"></a>예

### <a name="comment-based-help-for-a-function"></a>함수에 대 한 주석 기반 도움말

다음 샘플 함수는 주석 기반 도움말을 포함 합니다.

```powershell
function Add-Extension
{
param ([string]$Name,[string]$Extension = "txt")
$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name.
Takes any strings for the file name or extension.

.PARAMETER Name
Specifies the file name.

.PARAMETER Extension
Specifies the extension. "Txt" is the default.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension
or file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

결과는 다음과 같습니다.

```powershell
Get-Help -Name "Add-Extension" -Full
```

```Output
NAME

Add-Extension

SYNOPSIS

Adds a file name extension to a supplied name.

SYNTAX

Add-Extension [[-Name] <String>] [[-Extension] <String>]
[<CommonParameters>]

DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

PARAMETERS

-Name
Specifies the file name.

Required?                    false
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-Extension
Specifies the extension. "Txt" is the default.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type
"get-help about_commonparameters".

INPUTS
None. You cannot pipe objects to Add-Extension.

OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

Example 1

PS> extension -name "File"
File.txt

Example 2

PS> extension -name "File" -extension "doc"
File.doc

Example 3

PS> extension "File" "doc"
File.doc

RELATED LINKS

http://www.fabrikam.com/extension.html
Set-Item
```

### <a name="parameter-descriptions-in-function-syntax"></a>함수 구문의 매개 변수 설명

이 예제는 매개 변수 설명이 함수 구문에 삽입 된다는 점을 제외 하 고는 이전 예제와 동일 합니다. 이 형식은 설명이 간단한 경우에 가장 유용 합니다.

```powershell
function Add-Extension
{
param
(

[string]
#Specifies the file name.
$name,

[string]
#Specifies the file name extension. "Txt" is the default.
$extension = "txt"
)

$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

### <a name="comment-based-help-for-a-script"></a>스크립트에 대 한 주석 기반 도움말

다음 샘플 스크립트는 주석 기반 도움말을 포함 합니다. Closing 문과 문 사이에 빈 줄을 확인 `#>` `Param` 합니다. 문이 없는 스크립트에서 `Param` 도움말 항목의 마지막 주석과 첫 번째 함수 선언 사이에는 두 개 이상의 빈 줄이 있어야 합니다. 이러한 빈 줄이 없으면에서 `Get-Help` 도움말 항목을 스크립트가 아니라 함수와 연결 합니다.

```powershell
<#
.SYNOPSIS

Performs monthly data updates.

.DESCRIPTION

The Update-Month.ps1 script updates the registry with new data generated
during the past month and generates a report.

.PARAMETER InputPath
Specifies the path to the CSV-based input file.

.PARAMETER OutputPath
Specifies the name and path for the CSV-based output file. By default,
MonthlyUpdates.ps1 generates a name from the date and time it runs, and
saves the output in the local directory.

.INPUTS

None. You cannot pipe objects to Update-Month.ps1.

.OUTPUTS

None. Update-Month.ps1 does not generate any output.

.EXAMPLE

PS> .\Update-Month.ps1

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath `
C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
...
```

다음 명령은 스크립트 도움말을 가져옵니다. 스크립트는 환경 변수에 나열 된 디렉터리에 있지 않기 때문에 스크립트 `$env:Path` `Get-Help` 도움말을 가져오는 명령은 스크립트 경로를 지정 해야 합니다.

```powershell
Get-Help -Path .\update-month.ps1 -Full
```

```Output
# NAME

C:\ps-test\Update-Month.ps1

# SYNOPSIS

Performs monthly data updates.

# SYNTAX

C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
<String>] [<CommonParameters>]

# DESCRIPTION

The Update-Month.ps1 script updates the registry with new data
generated during the past month and generates a report.

# PARAMETERS

-InputPath
Specifies the path to the CSV-based input file.

Required?                    true
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-OutputPath
Specifies the name and path for the CSV-based output file. By
default, MonthlyUpdates.ps1 generates a name from the date
and time it runs, and saves the output in the local directory.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type,
"get-help about_commonparameters".

# INPUTS

None. You cannot pipe objects to Update-Month.ps1.

# OUTPUTS

None. Update-Month.ps1 does not generate any output.

Example 1

PS> .\Update-Month.ps1

Example 2

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

Example 3

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
C:\Reports\2009\January.csv

# RELATED LINKS
```

### <a name="redirecting-to-an-xml-file"></a>XML 파일로 리디렉션

함수 및 스크립트에 대 한 XML 기반 도움말 항목을 작성할 수 있습니다. 주석 기반 도움말을 보다 쉽게 구현할 수 있지만 업데이트할 수 있는 도움말에는 XML 기반 도움말이 필요 하며 여러 언어로 된 도움말 항목을 제공 합니다.

다음 예에서는 Update-Month.ps1 스크립트의 처음 몇 줄을 보여 줍니다.
스크립트는 키워드를 사용 하 여 `.ExternalHelp` 스크립트에 대 한 XML 기반 도움말 항목의 경로를 지정 합니다.

키워드 값은 `.ExternalHelp` 키워드와 같은 줄에 표시 됩니다. 다른 모든 배치가 비효율적입니다.

```powershell
# .ExternalHelp C:\MyScripts\Update-Month-Help.xml

param ([string]$InputPath, [string]$OutPutPath)
function Get-Data { }
...
```

다음 예에서는 `.ExternalHelp` 함수에 있는 키워드의 세 가지 유효한 위치를 보여 줍니다.

```powershell
function Add-Extension
{
# .ExternalHelp C:\ps-test\Add-Extension.xml

param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

```powershell
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name

# .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

```powershell
# .ExternalHelp C:\ps-test\Add-Extension.xml
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

### <a name="redirecting-to-a-different-help-topic"></a>다른 도움말 항목으로 리디렉션

다음 코드는 한 번에 하나의 도움말 텍스트 화면을 표시 하는 PowerShell의 기본 제공 도움말 함수 시작 부분에서 발췌 한 것입니다.
Cmdlet에 대 한 도움말 항목에서는 `Get-Help` 도움말 함수를 설명 하므로 도움말 함수는 및 키워드를 사용 하 여 `.ForwardHelpTargetName` `.ForwardHelpCategory` 사용자를 `Get-Help` cmdlet 도움말 항목으로 리디렉션합니다.

```powershell
function help
{

<#
.FORWARDHELPTARGETNAME Get-Help
.FORWARDHELPCATEGORY Cmdlet
#>
[CmdletBinding(DefaultParameterSetName='AllUsersView')]
param(
[Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
[System.String]
${Name},
...
```

다음 명령은이 기능을 사용 합니다.

```powershell
Get-Help -Name help
```

```Output
NAME

Get-Help

SYNOPSIS

Displays information about PowerShell cmdlets and concepts.
...
```

## <a name="see-also"></a>참조

[about_Functions](about_Functions.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Scripts](about_Scripts.md)

[Cmdlet 도움말을 작성 하는 방법](https://go.microsoft.com/fwlink/?LinkID=123415)

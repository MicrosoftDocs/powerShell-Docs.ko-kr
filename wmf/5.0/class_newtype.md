---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a96a4a58dafa01fb43f5bdffb52ef833816148e7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058372"
---
# <a name="new-language-features-in-powershell-50"></a>PowerShell 5.0의 새로운 언어 기능

PowerShell 5.0은 Windows PowerShell에서 다음과 같은 새로운 언어 요소를 소개합니다.

## <a name="class-keyword"></a>Class 키워드

**class** 키워드는 새 클래스를 정의하며, 진정한 .NET Framework 형식입니다.
클래스 멤버는 공용이지만 모듈 범위 내에서만 공용입니다.
형식 이름을 문자열로 참조할 수 없으며(예를 들어 `New-Object`는 작동하지 않음), 이 릴리스에서는 형식 리터럴(예: 클래스가 정의된 스크립트/모듈 파일 외부의 `[MyClass]`)을 사용할 수 없습니다.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Enum 키워드 및 열거형

**enum** 키워드에 대한 지원이 추가되어 줄 바꿈을 구분 기호로 사용합니다.
현재 제한 사항: 다음 예제와 같이 열거자 자체와 관련하여 열거자를 정의할 수 없지만 다른 열거형 측면에서 열거형을 초기화할 수는 있습니다.
또한 기본 형식을 현재 지정할 수 없으며, 항상 [int]입니다.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

열거자 값은 구문 분석 시간 상수여야 하며, 호출된 명령의 결과로 설정할 수 없습니다.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

열거형은 다음 예제와 같이 산술 연산자를 지원합니다.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a>Import-DscResource

**Import-DscResource**는 이제 진정한 동적 키워드입니다.
PowerShell은 지정된 모듈의 루트 모듈을 구문 분석하여 **DscResource** 특성이 포함된 클래스를 검색합니다.

## <a name="implementingassembly"></a>ImplementingAssembly

새 필드인 **ImplementingAssembly**가 ModuleInfo에 추가되었습니다. 이 필드는 스크립트에서 클래스를 정의하는 경우 스크립트 모듈에 대해 만들어진 동적 어셈블리 또는 이진 모듈에 대해 로드된 어셈블리로 설정됩니다. ModuleType = Manifest인 경우에는 설정되지 않습니다.

**ImplementingAssembly** 필드에서 리플렉션하면 모듈에서 리소스를 검색합니다. 즉, PowerShell이나 다른 관리 언어로 작성된 리소스를 검색할 수 있습니다.

이니셜라이저가 있는 필드:

```powershell
[int] $i = 5
```

정적 필드가 지원되며 특성처럼 작동합니다. 형식 제약 조건과 마찬가지로 순서대로 지정할 수 있습니다.

```powershell
static [int] $count = 0
```

형식은 선택 사항입니다.

```powershell
$s = "hello"
```

모든 멤버는 공용입니다.

## <a name="constructors-and-instantiation"></a>생성자 및 인스턴스화

Windows PowerShell 클래스에는 생성자가 있을 수 있으며, 이름은 클래스와 동일합니다. 생성자는 오버로드할 수 있습니다. 정적 생성자가 지원됩니다. 초기화 식이 있는 속성은 생성자에서 코드를 실행하기 전에 초기화됩니다. 정적 속성은 정적 생성자의 본문보다 먼저 초기화되고, 인스턴스 속성은 비정적 생성자의 본문보다 먼저 초기화됩니다. 현재는 다른 생성자에서 생성자를 호출하는 구문(예: C\# 구문 ": this()")이 없습니다. 해결 방법은 일반적인 Init 메서드를 정의하는 것입니다.

다음은 이 릴리스에서 클래스를 인스턴스화하는 방법입니다.

기본 생성자를 사용하여 인스턴스화합니다. New-Object는 이 릴리스에서 지원되지 않습니다.

```powershell
$a = [MyClass]::new()
```

매개 변수를 사용하여 생성자를 호출합니다.

```powershell
$b = [MyClass]::new(42)
```

매개 변수가 여러 개인 생성자에 배열을 전달합니다.
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

이 릴리스에서는 New-Object가 Windows PowerShell에 정의된 클래스에서 작동하지 않습니다. 또한 이 릴리스의 경우 형식 이름이 어휘적으로만 표시됩니다. 즉, 클래스를 정의하는 모듈이나 스크립트 외부에는 표시되지 않습니다. 함수는 Windows PowerShell에 정의된 클래스의 인스턴스를 반환하며 인스턴스는 모듈 또는 스크립트 외부에서 잘 작동합니다.

`Get-Member -Static`은 생성자를 나열하므로 다른 모든 메서드처럼 오버로드를 볼 수 있습니다. 이 구문의 성능 또한 New-Object보다 현저하게 빠릅니다.

**new**라는 의사 정적 메서드는 다음 예제와 같이 .NET 형식에서 작동합니다.

```powershell
[hashtable]::new()
```

이제 Get-Member를 사용하거나 다음 예제와 같이 생성자 오버로드를 확인할 수 있습니다.

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a>메서드

Windows PowerShell 클래스 메서드는 끝 블록만 있는 ScriptBlock으로 구현됩니다. 모든 메서드는 공용입니다. 다음에서는 **DoSomething**이라는 메서드를 정의하는 예제를 보여 줍니다.

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x) # method syntax
    }
    private _doSomething($a) {}
}
```

메서드 호출:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

오버로드된 메서드 즉, 기존 메서드와 동일하게 이름이 지정되지만 지정된 값으로 구별되는 메서드도 지원됩니다.

## <a name="properties"></a>속성

모든 속성은 공용입니다. 속성에는 줄 바꿈이나 세미콜론이 필요합니다. 개체 형식이 지정되지 않은 경우 속성 형식은 개체입니다.

유효성 검사 특성이나 인수 변환 특성(예: `[ValidateSet("aaa")]`)을 사용하는 속성은 예상대로 작동합니다.

## <a name="hidden"></a>숨김

새로운 키워드 **Hidden**이 추가되었습니다. **Hidden**은 생성자를 비롯하여 속성 및 메서드에 적용할 수 있습니다.

숨겨진 멤버는 공용이지만 -Force 매개 변수를 추가하지 않는 한 Get-Member의 출력에 표시되지 않습니다.

탭이 완료되거나 Intellisense를 사용할 때 숨겨진 멤버를 정의하는 클래스에서 완료되지 않으면 숨겨진 멤버가 포함되지 않습니다.

새로운 특성 **System.Management.Automation.HiddenAttribute**가 추가되어 C# 코드가 Windows PowerShell 내에서 동일한 의미 체계를 가질 수 있습니다.

## <a name="return-types"></a>반환 형식

반환 형식은 계약이며, 반환 값은 필요한 형식으로 변환됩니다. 반환 형식이 지정되지 않은 경우 반환 형식은 void입니다. 개체의 스트리밍이 없으며 의도적으로 또는 실수로 개체를 파이프라인에 쓸 수 없습니다.

## <a name="attributes"></a>특성

두 개의 새로운 특성 **DscResource** 및 **DscProperty**가 추가되었습니다.

## <a name="lexical-scoping-of-variables"></a>변수의 어휘 범위 지정

다음에서는 이 릴리스에서 어휘 범위 지정이 작동하는 방식에 대한 예를 보여 줍니다.

```powershell
$d = 42 # Script scope

function bar
{
    $d = 0 # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d # error, not found dynamically
        return $script:d # no error
        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="end-to-end-example"></a>종단 간 예제

다음 예제에서는 여러 가지 새로운 사용자 지정 클래스를 만들어 HTML DSL(동적 스타일시트 언어)을 구현합니다.
그런 다음 예제에서는 모듈의 범위 외부에서 형식을 사용할 수 없기 때문에 도우미 함수를 추가하여 요소 클래스의 일부로 제목 스타일 및 표와 같은 특정 요소 형식을 만듭니다.

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $this.Head
        $text += "`n</head>`n<body>`n"
        $text += $this.Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$($this.Title)</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($this.Attributes)
        {
            foreach ($attr in $this.Attributes.Keys)
            {
                #BUGBUG - need to validate keys against attribute
                $attributesText += " $attr=`"$($this.Attributes[$attr])\`""
            }
        }
        return "<$($this.tag)${attributesText}>$($this.text)</$($this.tag)>`n"
    }
[string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren’t visible outside of the module.
#

function H1 { [Element] @{ Tag = "H1" ; Text = $args.foreach{$_} -join " " }}
function H2 { [Element] @{ Tag = "H2" ; Text = $args.foreach{$_} -join " " }}
function H3 { [Element] @{ Tag = "H3" ; Text = $args.foreach{$_} -join " " }}
function P { [Element] @{ Tag = "P" ; Text = $args.foreach{$_} -join " " }}
function B { [Element] @{ Tag = "B" ; Text = $args.foreach{$_} -join " " }}
function I { [Element] @{ Tag = "I" ; Text = $args.foreach{$_} -join " " }}
function HREF
{
    param (
        $Name,
        $Link
    )
    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
    [Parameter(Mandatory)]
    [object[]]
        $Data,
    [Parameter()]
    [string[]]
        $Properties = "*",
    [Parameter()]
    [hashtable]
        $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )
$bodyText = ""
# Add the header tags
$bodyText += $Properties.foreach{TH $_}
# Add the rows
$bodyText += foreach ($row in $Data)
    {
        TR (-join $Properties.Foreach{ TD ($row.$_) } )
    }

    $table = [Element] @{
        Tag = "Table"
        Attributes = $Attributes
        Text = $bodyText
    }
$table
}
function TH { ([Element] @{ Tag = "TH" ; Text = $args.foreach{$_} -join " " }) }
function TR { ([Element] @{ Tag = "TR" ; Text = $args.foreach{$_} -join " " }) }
function TD { ([Element] @{ Tag = "TD" ; Text = $args.foreach{$_} -join " " }) }
function Style

{
    return [Element] @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```

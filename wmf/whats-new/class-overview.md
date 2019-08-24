---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: PowerShell 클래스를 사용하여 사용자 지정 형식 만들기
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470941"
---
# <a name="creating-custom-types-using-powershell-classes"></a>PowerShell 클래스를 사용하여 사용자 지정 형식 만들기

PowerShell 5.0에서는 다른 개체 지향 프로그래밍 언어와 유사한 형식 구문 및 의미 체계를 사용하여 클래스 및 기타 사용자 정의 형식을 정의하는 기능을 추가했습니다. 목표는 개발자 및 IT 전문가가 보다 광범위한 사용 사례에 PowerShell을 적용하고, PowerShell 아티팩트(예: DSC 리소스)의 개발을 간소화하며, 관리 화면의 적용을 가속화할 수 있도록 하는 것입니다.

## <a name="supported-scenarios-in-this-release"></a>이 릴리스에서 지원되는 시나리오

- PowerShell 언어를 사용하여 DSC 리소스 및 관련 형식 정의
- 클래스, 속성, 메서드 등 친숙한 개체 지향 프로그래밍 구문을 사용하여 PowerShell에서 사용자 지정 형식 정의
- PowerShell 및 클래스 기본 DSC 리소스에서 클래스로 상속 지원
- PowerShell 언어를 사용하여 형식 디버그
- 적절한 수준에서 정식 메커니즘을 사용하여 예외 생성 및 처리

## <a name="declare-base-class"></a>기본 클래스 선언

PowerShell 클래스를 다른 PowerShell 클래스의 기본 형식으로 선언할 수 있습니다.

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

또한 기존 .NET Framework 형식을 기본 클래스로 사용할 수 있습니다.

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a>기본 클래스 생성자 호출

하위 클래스에서 기본 클래스 생성자를 호출하려면 **base** 키워드를 사용합니다.

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

기본 클래스에 기본(매개 변수 없음) 생성자가 있는 경우 명시적 생성자 호출을 생략할 수 있습니다.

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a>기본 클래스 메서드 호출

하위 클래스에서 기존 메서드를 재정의할 수 있습니다. 이렇게 하려면 동일한 이름과 서명을 사용하여 메서드를 선언합니다.

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

재정의된 구현에서 기본 클래스 메서드를 호출하려면 호출할 때 기본 클래스(`[baseClass]$this`)로 캐스팅합니다.

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

모든 PowerShell 메서드는 가상입니다. 동일한 이름과 서명으로 메서드를 선언하면 재정의에 사용한 것과 동일한 구문을 사용하여 하위 클래스에서 비가상 .NET 메서드를 숨길 수 있습니다.

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="declare-implemented-interface"></a>구현된 인터페이스 선언

구현된 인터페이스는 기본 형식 다음이나 지정된 기본 형식이 없는 경우 콜론(:) 바로 다음에 선언할 수 있습니다. 쉼표를 사용하여 모든 형식 이름을 구분합니다. C# 구문과 유사합니다.

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="new-language-features-in-powershell-50"></a>PowerShell 5.0의 새로운 언어 기능

PowerShell 5.0은 PowerShell에서 다음과 같은 새로운 언어 요소를 소개합니다.

### <a name="class-keyword"></a>Class 키워드

`class` 키워드는 새 클래스를 정의하며, 진정한 .NET Framework 형식입니다. 클래스 멤버는 공용이지만 모듈 범위 내에서만 공용입니다. 형식 이름을 문자열로 참조할 수 없으며(예를 들어 `New-Object`는 작동하지 않음), 이 릴리스에서는 형식 리터럴(예: 클래스가 정의된 스크립트 또는 모듈 파일 외부의 `[MyClass]`)을 사용할 수 없습니다.

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a>Enum 키워드 및 열거형

`enum` 키워드에 대한 지원이 추가되어 줄 바꿈을 구분 기호로 사용합니다. 현재는 열거자 자체와 관련하여 열거자를 정의할 수 없습니다. 그러나 다음 예제와 같이 다른 열거형 측면에서 열거형을 초기화할 수는 있습니다. 또한 기본 형식은 지정할 수 없으며, 항상 `[int]`입니다.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

열거자 값은 구문 분석 시간 상수여야 합니다. 이 값을 호출된 명령의 결과로 설정할 수 없습니다.

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

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource`는 이제 진정한 동적 키워드입니다. PowerShell은 지정된 모듈의 루트 모듈을 구문 분석하여 **DscResource** 특성이 포함된 클래스를 검색합니다.

### <a name="implementingassembly"></a>ImplementingAssembly

새 필드인 **ImplementingAssembly**가 **ModuleInfo**에 추가되었습니다. 이 필드는 스크립트에서 클래스를 정의하는 경우 스크립트 모듈에 대해 만들어진 동적 어셈블리 또는 이진 모듈에 대해 로드된 어셈블리로 설정됩니다. **ModuleType**이 **Manifest**인 경우에는 설정되지 않습니다.

**ImplementingAssembly** 필드에서 리플렉션하면 모듈에서 리소스를 검색합니다. 즉, PowerShell이나 다른 관리 언어로 작성된 리소스를 검색할 수 있습니다.

이니셜라이저가 있는 필드:

```powershell
[int] $i = 5
```

`Static`이 지원됩니다. 형식 제약 조건과 마찬가지로 특성처럼 작동합니다. 순서에 관계없이 지정할 수 있습니다.

```powershell
static [int] $count = 0
```

형식은 선택 사항입니다.

```powershell
$s = "hello"
```

모든 멤버는 공용입니다.

### <a name="constructors-and-instantiation"></a>생성자 및 인스턴스화

PowerShell 클래스에는 생성자가 포함될 수 있습니다. 해당 이름은 클래스와 동일합니다. 생성자는 오버로드할 수 있습니다. 정적 생성자가 지원됩니다. 초기화 식이 있는 속성은 생성자에서 코드를 실행하기 전에 초기화됩니다. 정적 속성은 정적 생성자의 본문보다 먼저 초기화되고, 인스턴스 속성은 비정적 생성자의 본문보다 먼저 초기화됩니다. 현재는 다른 생성자에서 생성자를 호출하는 구문(예: C\# 구문 ": this()")이 없습니다. 해결 방법은 일반적인 `Init()` 메서드를 정의하는 것입니다.

#### <a name="creating-instances"></a>인스턴스 만들기

> [!NOTE]
> PowerShell 5.0에서는 `New-Object`가 PowerShell에 정의된 클래스에서 작동하지 않습니다. 또한 형식 이름이 어휘적으로만 표시됩니다. 즉, 클래스를 정의하는 모듈이나 스크립트 외부에는 표시되지 않습니다. 함수는 PowerShell에 정의된 클래스의 인스턴스를 반환할 수 있습니다. 해당 인스턴스는 모듈 또는 스크립트 외부에서 작동합니다.

1. 기본 생성자를 사용하여 인스턴스화합니다.

   ```powershell
   $a = [MyClass]::new()
   ```

1. 매개 변수를 사용하여 생성자를 호출합니다.

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. 매개 변수가 여러 개인 생성자에 배열을 전달합니다.

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

`new()`라는 의사 정적 메서드는 다음 예제와 같이 .NET 형식에서 작동합니다.

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a>생성자 검색

이제 `Get-Member`를 사용하거나 다음 예제와 같이 생성자 오버로드를 확인할 수 있습니다.

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

`Get-Member -Static`은 생성자를 나열하므로 다른 모든 메서드처럼 오버로드를 볼 수 있습니다. 이 구문의 성능 또한 `New-Object`보다 현저하게 빠릅니다.

### <a name="methods"></a>메서드

PowerShell 클래스 메서드는 끝 블록만 있는 **ScriptBlock**으로 구현됩니다. 모든 메서드는 공용입니다. 다음에서는 **DoSomething**이라는 메서드를 정의하는 예제를 보여 줍니다.

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

오버로드된 메서드도 지원됩니다.

### <a name="properties"></a>속성

모든 속성은 공용입니다. 속성에는 줄 바꿈이나 세미콜론이 필요합니다. 개체 형식이 지정되지 않은 경우 속성 형식은 개체입니다.

유효성 검사 또는 인수 변형 특성(예: `[ValidateSet("aaa")]`)을 사용하는 속성은 예상대로 작동합니다.

### <a name="hidden"></a>숨김

새로운 키워드 `Hidden`이 추가되었습니다. `Hidden`은 생성자를 비롯하여 속성 및 메서드에 적용할 수 있습니다.

숨겨진 구성원은 공용이지만 `-Force` 매개 변수를 추가하지 않는 한 `Get-Member`의 출력에 표시되지 않습니다. 탭이 완료되거나 Intellisense를 사용할 때 숨겨진 멤버를 정의하는 클래스에서 완료되지 않으면 숨겨진 멤버가 포함되지 않습니다.

새로운 특성 **System.Management.Automation.HiddenAttribute**가 추가되어 C\# 코드가 PowerShell 내에서 동일한 의미 체계를 가질 수 있습니다.

### <a name="return-types"></a>반환 형식

반환 형식은 계약입니다. 반환 값은 필요한 형식으로 변환됩니다. 반환 형식이 지정되지 않은 경우 반환 형식은 **void**입니다. 개체의 스트리밍이 없습니다. 의도적으로 또는 실수로 개체를 파이프라인에 쓸 수 없습니다.

### <a name="attributes"></a>특성

두 개의 새로운 특성 **DscResource** 및 **DscProperty**가 추가되었습니다.

### <a name="lexical-scoping-of-variables"></a>변수의 어휘 범위 지정

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

## <a name="end-to-end-example"></a>엔드투엔드 예제

다음 예제에서는 몇 가지 새로운 사용자 지정 클래스를 만들어 HTML DSL(동적 스타일시트 언어)을 구현합니다. 그런 다음 예제에서는 모듈의 범위 외부에서 형식을 사용할 수 없기 때문에 도우미 함수를 추가하여 요소 클래스의 일부로 제목 스타일 및 표와 같은 특정 요소 형식을 만듭니다.

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
# These are required because types aren't visible outside of the module.
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

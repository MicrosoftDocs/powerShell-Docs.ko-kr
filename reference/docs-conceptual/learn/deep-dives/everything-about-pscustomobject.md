---
title: PSCustomObject에 대해 알고 싶은 모든 것
description: PSCustomObject는 구조화된 데이터를 만드는 단순한 방법입니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: fbc8b5b6d2cfafaa75fa820f420762a1804074ac
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149496"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a>PSCustomObject에 대해 알고 싶은 모든 것

`PSCustomObject`는 PowerShell 도구 벨트에 추가하는 작업을 처리하는 탁월한 도구입니다. 기본 사항부터 시작한 다음 고급 기능을 살펴보겠습니다. `PSCustomObject` 사용의 기본 목적은 구조화된 데이터를 간단하게 만드는 것입니다. 첫 번째 예제를 살펴보면 무슨 말인지 잘 알 수 있습니다.

> [!NOTE]
> 이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다. PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다. [PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.

## <a name="creating-a-pscustomobject"></a>PSCustomObject 만들기

저는 PowerShell에서 `[PSCustomObject]`를 즐겨 사용합니다. 사용 가능한 개체를 만들기가 그 어느 때보다도 쉬워졌습니다.
따라서 개체를 만드는 다른 방법은 설명하지 않겠습니다. 여기에 있는 예제 대부분은 PowerShell v3.0 이상을 기준으로 한다는 점만 말씀드리겠습니다.

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

거의 모든 요소에 해시 테이블을 사용하기 때문에 이 방법이 효과적입니다. 하지만 PowerShell에서 해시 테이블을 개체처럼 처리할 때도 있습니다. 가장 큰 차이점은 `Format-Table`이나 `Export-CSV`를 사용할 때는 해시 테이블은 단순한 키/값 쌍 컬렉션에 불과하다는 것입니다.

그런 다음 일반 개체처럼 값에 액세스하고 값을 사용할 수 있습니다.

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a>해시 테이블 변환

지금은 이 주제를 다루고 있지만, 여러분은 다음과 같은 작업도 수행할 수 있습니다.

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

개체를 완전히 새로 만드는 방법을 선호하지만 간혹 해시 테이블을 먼저 작업해야 할 때도 있습니다. 이 예제는 생성자가 개체 속성에 해시 테이블을 사용하기 때문에 작동합니다. 한 가지 중요한 점은 이 메서드가 작동하는 동안에는 정확하게 동등하지 않다는 것입니다. 가장 큰 차이점은 속성의 순서가 유지되지 않는다는 것입니다.

### <a name="legacy-approach"></a>기존의 접근 방식

사람들이 `New-Object`를 이용해 사용자 지정 개체를 만다는 모습을 보셨을 겁니다.

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

이 방법은 속도는 조금 느리지만 PowerShell 초기 버전에서는 가장 적합한 방법일 수 있습니다.

### <a name="saving-to-a-file"></a>폴더에 저장

해시 테이블을 파일에 저장하는 가장 좋은 방법은 JSON으로 저장하는 것입니다. `[PSCusomObject]`로 다시 가져오면 됩니다.

```powershell
$myObject | ConvertTo-Json -depth 1- | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

제 게시물인 [파일 읽기 및 쓰기를 수행하는 다양한 방법][]에서 파일에 개체를 저장하는 다른 방법을 확인할 수 있습니다.

## <a name="working-with-properties"></a>속성 작업

### <a name="adding-properties"></a>속성 추가

`Add-Member`를 사용하여 `PSCustomObject`에 새 속성을 추가할 수 있습니다.

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name `ID` -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a>속성 제거

개체에서 속성을 제거할 수도 있습니다.

```powershell
$myObject.psobject.properties.remove('ID')
```

`psobject`는 기본 개체 메타데이터에 대 한 액세스를 제공하는 숨겨진 속성입니다.

### <a name="enumerating-property-names"></a>속성 이름 열거

개체에 모든 속성 이름 목록이 필요할 때가 있습니다.

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

`psobject` 속성에서도 동일한 목록을 가져올 수 있습니다.

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a>속성에 동적으로 액세스

속성 값에 직접 액세스할 수 있다는 사실은 이미 설명했습니다.

```powershell
$myObject.Name
```

속성 이름에는 문자열을 사용할 수 있으며, 작동에는 아무런 영향을 주지 않습니다.

```powershell
$myObject.'Name'
```

이 추가 단계를 수행하고 속성 이름에 변수를 사용해도 됩니다.

```powershell
$property = 'Name'
$myObject.$property
```

이상하게 보이겠지만 작동에는 문제가 없습니다.

### <a name="convert-pscustomboject-into-a-hashtable"></a>pscustomboject를 해시 테이블로 변환

마지막 섹션에서 계속 진행하려면 속성을 동적으로 탐색하고 해당 속성에서 해시 테이블을 만들어야 합니다.

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a>속성 테스트

속성 존재 여부를 확인해야 한다면 속성에 값이 있는지 확인하기만 하면 됩니다.

```powershell
if( $null -ne $myObject.ID )
```

하지만 값이 `$null`이며 이를 확인해야 한다면 `psobject.properties`를 확인하면 됩니다.

```powershell
if( $myobject.psobject.properties.match('ID') )
```

## <a name="adding-object-methods"></a>개체 메서드 추가

개체에 스크립트 메서드를 추가해야 한다면 `Add-Member` 및 `ScriptBlock`을 사용하면 됩니다. `this` 자동 변수를 사용하여 현재 개체를 참조해야 합니다. 다음은 개체를 해시 테이블로 변환하는 `scriptblock`입니다. (마지막 예제와 동일한 코드 형식)

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

그런 다음 이를 스크립트 속성으로 개체에 추가합니다.

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

그러면 다음과 같이 함수를 호출할 수 있습니다.

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a>개체 및 값 형식

개체 형식과 값 형식은 서로 다른 방식으로 변수 할당을 처리합니다. 값 형식을 서로 할당하면 값만 새 변수에 복사됩니다.

```powershell
$first = 1
$second = $first
$second = 2
```

이 경우 `$first`는 1이고 `$second`는 2입니다.

개체 변수는 실제 개체에 대한 참조를 유지합니다. 한 개체를 새 변수에 추가해도 여전히 같은 개체를 참조합니다.

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

`$third`와 `$fourth`는 개체의 같은 인스턴스를 참조하므로 `$third.key`와 `$fourth.Key`는 모두 4입니다.

### <a name="psobjectcopy"></a>psobject.copy()

개체의 실제 복사본이 필요하다면 개체를 복제하면 됩니다.

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

복제는 개체의 단순 복사본을 만듭니다. 이제 서로 다른 인스턴스가 존재하며 이 예제에서 `$third.key`는 3이고 `$fourth.Key`는 4입니다.

중첩된 개체가 있으므로 저는 이것을 단순 복사본이라고 합니다. (속성에 다른 개체가 포함된 경우). 최상위 값만 복사됩니다. 자식 개체는 서로를 참조합니다.

### <a name="pstypename-for-custom-object-types"></a>사용자 지정 개체 형식에 대한 PSTypeName

이제 개체가 있으므로 개체를 이용해 모호할 수 있는 몇 가지 추가 작업을 수행할 수 있습니다. 제일 먼저 할 일은 `PSTypeName`을 부여하는 것입니다. 이것은 사람들이 가장 많이 선택하는 방법입니다.

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

얼마 전 [/u/markekraus의 게시물][]에서 다른 수행 방법을 확인했습니다. 그리고 다른 게시물을 살펴보면서 [Adam Bertram][]과 [Mike Shepard][]가 말하는 인라인으로 정의하는 방법을 알게 되었습니다.

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

언어에도 아주 잘 어울리는 방법입니다. 이제 적절한 형식 이름을 가진 개체가 있으니 더 많은 작업을 수행할 수 있습니다.

## <a name="using-defaultpropertyset-the-long-way"></a>DefaultPropertySet 사용(긴 방식)

PowerShell은 사용자를 대신하여 기본적으로 표시할 속성을 결정합니다. 많은 네이티브 명령에는 어려운 일을 모두 처리하는 `.ps1xml` [서식 지정 파일][]이 있습니다. 이 [Boe Prox가 게시][]에서는 PowerShell만 이용해 사용자 지정 개체에서 이 작업을 하는 다른 방법을 확인할 수 있습니다. PowerShell에서 사용할 `MemberSet`를 제공할 수 있습니다.

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet(‘DefaultDisplayPropertySet’,[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

개체가 셸에 들어가면 기본적으로 이러한 속성만 표시합니다.

### <a name="update-typedata-with-defaultpropertyset"></a>DefaultPropertySet가 있는 Update-TypeData

좋은 방법이긴 하지만 얼마 전에 [Jeffrey Snover 및 Don Jones외의 PowerShell 언플러그드 2016][psunplugged]을 시청하면서 더 좋은 방법을 발견했습니다. Jeffrey는 [Update-TypeData][]를 이용해 기본 속성을 지정했습니다.

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

너무나 간단해서 이 게시물을 참조하지 않고도 모든 내용을 기억할 정도입니다. 이제 많은 속성을 사용하여 개체를 쉽게 만들 수 있으며 셸에서 해당 개체를 살펴볼 때도 여전히 쉽게 확인할 수 있습니다. 다른 속성에 액세스하거나 속성을 확인해야 한다면 여기서 할 수 있습니다.

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a>ScriptProperty가 있는 Update-TypeData

이 동영상에서 알게 된 또 다른 내용은 개체에 대한 스크립트 속성 생성이었습니다. 기존 개체에도 적용된다는 사실을 말씀드려야 할 것 같네요.

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

이 작업은 개체 작성 전후 언제든 해도 됩니다. 바로 이점 때문에 이 방법은 스크립트 속성이 있는 `Add-Member` 사용과는 다릅니다. 앞에서 설명한 방식으로 `Add-Member`를 사용하면 개체의 특정 인스턴스에만 존재하게 됩니다. 이것은 이 `TypeName`이 있는 모든 개체에 적용됩니다.

## <a name="function-parameters"></a>함수 매개 변수

이제 함수 및 스크립트의 매개 변수에도 이러한 사용자 지점 형식을 사용할 수 있습니다. 특정 함수로 이러한 사용자 지정 개체를 만든 다음 다른 함수로 전달할 수도 있습니다.

```powershell
param( [PSTypeName('My.Object')]$Data )
```

PowerShell을 이용할 때는 개체가 사용자가 지정한 형식이어야 합니다. 형식이 자동으로 일치하지 않는다면 유효성 검사 오류가 발생하여 코드에서 이를 테스트하는 단계를 건너뛰게 됩니다. PowerShell이 가장 적합한 작업을 수행하게 하는 대표적인 방법입니다.

### <a name="function-outputtype"></a>함수 OutputType

고급 기능에 대해 `OutputType`를 정의할 수도 있습니다.

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

**OutputType** 특성 값은 문서 참고일뿐입니다. 함수 코드에서 파생되거나 실제 함수 출력과 비교되지 않습니다.

출력 유형을 사용하는 주된 이유는 함수의 메타데이터 정보 사용자의 의도를 반영한다는 점입니다. 개발 환경에서 `Get-Command`와 `Get-Help` 같은 요소를 활용할 수 있습니다. 추가 정보가 필요하다면 도움말인 [about_Functions_OutputTypeAttribute][]를 참조하세요.

말이 나온 김에 설명하자면, Pester를 사용하여 함수를 단위 테스트하는 경우에는 **OutputType**과 일치하는 출력 개체의 유효성을 검사하는 것이 좋습니다. 이렇게 하면 잘못된 변수가 파이프에 속하는지를 확인할 수 있습니다.

## <a name="closing-thoughts"></a>맺음말

이 문서에서 다룬 내용은 모두 `[PSCustomObject]`를 기준으로 하지만, 여기에 나온 정보 상당수는 개체에도 대체로 적용됩니다.

진행 과정에서 기능을 언급하는 모습은 보았지만 `PSCustomObject` 관련 정보 모음으로 제공되는 모습은 보지 못했습니다. 지난주 우연히 이를 접했는데 생전 처음 본다는 사실에 놀라고 말았습니다. 여러분이 큰 그림을 보고 이러한 정보를 활용할 기회를 놓치지 않도록 모든 정보를 한곳에 모으고 싶었습니다. 유용한 내용을 배우고 스크립트에서 활용하는 방법을 확인하시길 바랍니다.

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Boe Prox가 게시]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[서식 지정 파일]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[파일 읽기 및 쓰기를 수행하는 다양한 방법]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[/u/markekraus의 게시물]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Update-TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata

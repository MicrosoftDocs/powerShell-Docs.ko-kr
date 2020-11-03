---
description: 컴파일된 cmdlet 처럼 함수가 작동 하 게 하는 특성에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_CmdletBindingAttribute
ms.openlocfilehash: c4090910a72e2f68b5a710c76b20cc8af532c04b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221593"
---
# <a name="about-functions-cmdletbindingattribute"></a>함수 CmdletBindingAttribute 정보

## <a name="short-description"></a>간단한 설명
컴파일된 cmdlet 처럼 함수가 작동 하 게 하는 특성에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

`CmdletBinding`특성은 c #으로 작성 된 컴파일된 cmdlet 처럼 작동 하 게 하는 함수의 특성입니다. Cmdlet의 기능에 대 한 액세스를 제공 합니다.

PowerShell은 특성이 포함 된 함수의 매개 변수를 `CmdletBinding` 컴파일된 cmdlet의 매개 변수를 바인딩하는 것과 동일한 방식으로 바인딩합니다. `$PSCmdlet`자동 변수는 특성을 사용 하는 함수에 사용할 수 `CmdletBinding` 있지만 `$Args` 변수를 사용할 수 없습니다.

특성이 있는 함수에서 `CmdletBinding` , 위치 매개 변수가 일치 하지 않는 위치 인수를 알 수 없는 경우 매개 변수 바인딩이 실패 합니다.

> [!NOTE]
> 컴파일된 cmdlet은 `Cmdlet` 이 항목에 설명 된 특성과 비슷한 필수 특성을 사용 `CmdletBinding` 합니다.

## <a name="syntax"></a>구문

다음 예에서는 특성의 모든 선택적 인수를 지정 하는 함수의 형식을 보여 줍니다 `CmdletBinding` . 각 인수에 대 한 간략 한 설명은이 예제를 따릅니다.

```powershell
{
    [CmdletBinding(ConfirmImpact=<String>,
    DefaultParameterSetName=<String>,
    HelpURI=<URI>,
    SupportsPaging=<Boolean>,
    SupportsShouldProcess=<Boolean>,
    PositionalBinding=<Boolean>)]

    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

## <a name="confirmimpact"></a>ConfirmImpact

인수 동작 인수는 **Shouldprocess** 메서드를 호출 하 여 함수의 동작을 확인 해야 **하는 경우** 를 지정 합니다. **Shouldprocess** 메서드를 호출 하는 경우에는 기본 설정 **인수 값** 이 `$ConfirmPreference` 기본 설정 변수 값 보다 크거나 같은 경우에만 확인 프롬프트가 표시 됩니다. 인수의 기본값은 **Medium** 입니다. **Supportsshouldprocess** 인수도 지정 된 경우에만이 인수를 지정 합니다.

확인 요청에 대 한 자세한 내용은 [확인 요청](/powershell/scripting/developer/cmdlet/requesting-confirmation)을 참조 하세요.

## <a name="defaultparametersetname"></a>DefaultParameterSetName

**DefaultParameterSetName** 인수는 사용할 매개 변수 집합을 확인할 수 없는 경우 PowerShell에서 사용 하려고 하는 매개 변수 집합의 이름을 지정 합니다. 각 매개 변수의 고유한 매개 변수를 필수 매개 변수로 설정 하면이 문제를 방지할 수 있습니다.

## <a name="helpuri"></a>HelpURI

**HelpURI** 인수는 함수를 설명 하는 온라인 버전의 도움말 항목에 대 한 인터넷 주소를 지정 합니다. **HelpURI** 인수의 값은 "http" 또는 "https"로 시작 해야 합니다.

**HelpURI** 인수 값은 함수에 대해를 반환 하는 **Commandinfo** 개체의 **HelpURI** 속성 값에 사용 됩니다 `Get-Command` .

그러나 도움말 파일이 컴퓨터에 설치 되어 있고 도움말 파일의 **RelatedLinks** 섹션에 있는 첫 번째 링크의 값이 uri 이거나 주석 기반 도움말의 첫 번째 지시문의 값이 uri 인 경우에는 `.Link` 도움말 파일의 Uri가 함수의 **HelpUri** 속성 값으로 사용 됩니다.

`Get-Help`명령에의 **online** 매개 변수가 지정 된 경우 cmdlet은 **HelpURI** 속성의 값을 사용 하 여 함수 도움말 항목의 온라인 버전을 찾습니다 `Get-Help` .

## <a name="supportspaging"></a>SupportsPaging

**Supportspaging** 인수는 **첫 번째** , **Skip** 및 **IncludeTotalCount** 매개 변수를 함수에 추가 합니다. 이러한 매개 변수를 통해 사용자는 매우 큰 결과 집합에서 출력을 선택할 수 있습니다. 이 인수는 SQL database와 같은 데이터 선택을 지 원하는 대량 데이터 저장소에서 데이터를 반환 하는 cmdlet 및 함수를 위해 설계 되었습니다.

이 인수는 Windows PowerShell 3.0에서 도입 되었습니다.

- **First** : 첫 번째 ' n ' 개의 개체만 가져옵니다.
- **Skip** : 첫 번째 ' n ' 개체를 무시 한 다음 나머지 개체를 가져옵니다.
- **IncludeTotalCount** : 데이터 집합의 개체 수 (정수)와 개체를 보고 합니다. Cmdlet이 총 개수를 확인할 수 없으면 "알 수 없는 총 개수"를 반환 합니다.

PowerShell에는 반환할 총 개수 값을 가져오고 총 개수 값의 정확도를 포함 하는 도우미 메서드인 **NewTotalCount** 이 포함 되어 있습니다.

다음 샘플 함수는 고급 함수에 페이징 매개 변수에 대 한 지원을 추가 하는 방법을 보여 줍니다.

```powershell
function Get-Numbers {
    [CmdletBinding(SupportsPaging = $true)]
    param()

    $FirstNumber = [Math]::Min($PSCmdlet.PagingParameters.Skip, 100)
    $LastNumber = [Math]::Min($PSCmdlet.PagingParameters.First +
      $FirstNumber - 1, 100)

    if ($PSCmdlet.PagingParameters.IncludeTotalCount) {
        $TotalCountAccuracy = 1.0
        $TotalCount = $PSCmdlet.PagingParameters.NewTotalCount(100,
          $TotalCountAccuracy)
        Write-Output $TotalCount
    }
    $FirstNumber .. $LastNumber | Write-Output
}
```

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

**Supportsshouldprocess** 인수는 **Confirm** 및 **WhatIf** 매개 변수를 함수에 추가 합니다. **Confirm** 매개 변수는 파이프라인의 각 개체에 대해 명령을 실행 하기 전에 사용자에 게 메시지를 표시 합니다. **WhatIf** 매개 변수는 명령을 실행 하는 대신 명령이 수행 하는 변경 내용을 나열 합니다.

## <a name="positionalbinding"></a>PositionalBinding

**Positionalbinding** 인수는 함수의 매개 변수가 기본적으로 위치 인지 여부를 결정 합니다. 기본값은 `$True`입니다. 값으로 **Positionalbinding** 인수를 사용 `$False` 하 여 위치 바인딩을 사용 하지 않도록 설정할 수 있습니다.

**Positionalbinding** 인수는 Windows PowerShell 3.0에서 도입 되었습니다.

매개 변수가 위치 이면 매개 변수 이름은 선택 사항입니다.
PowerShell은 함수 명령에 있는 명명 되지 않은 매개 변수 값의 순서나 위치에 따라 함수 매개 변수와 명명 되지 않은 매개 변수 값을 연결 합니다.

매개 변수가 위치 ("명명 된")가 아닌 경우 명령에 매개 변수 이름 (또는 이름의 약어 또는 별칭)이 필요 합니다.

**Positionalbinding** 이 인 경우 `$True` 함수 매개 변수는 기본적으로 위치입니다. PowerShell은 함수에 선언 된 순서 대로 매개 변수에 위치 번호를 할당 합니다.

**Positionalbinding** 이 인 경우 `$False` 함수 매개 변수는 기본적으로 위치에 있지 않습니다. **매개 변수 특성의** **Position** 인수를 매개 변수에 선언 하지 않으면 매개 변수가 함수에 사용 될 때 매개 변수 이름 (또는 별칭 또는 약어)이 포함 되어야 합니다.

**매개 변수** 특성의 **Position** 인수가 **positionalbinding** 기본값 보다 우선적으로 적용 됩니다. **Position** 인수를 사용 하 여 매개 변수에 대 한 위치 값을 지정할 수 있습니다. **Position** 인수에 대 한 자세한 내용은 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)를 참조 하세요.

## <a name="notes"></a>참고

**SupportsTransactions** 인수는 고급 함수에서 지원 되지 않습니다.

## <a name="keywords"></a>키워드

about_Functions_CmdletBinding_Attribute

## <a name="see-also"></a>참고 항목

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

---
description: PowerShell에서 명령 매개 변수를 사용 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 02/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters
ms.openlocfilehash: c9d7ab62c13a7cafcf93103f9a70f6575d5dd7b8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600867"
---
# <a name="about-parameters"></a>매개 변수 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 명령 매개 변수를 사용 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

Cmdlet, 함수 및 스크립트와 같은 대부분의 PowerShell 명령은 사용자가 옵션을 선택 하거나 입력을 제공할 수 있도록 매개 변수를 사용 합니다. 매개 변수는 명령 이름 뒤에 다음과 같은 형식으로 되어 있습니다.

```
-<parameter_name> <parameter_value>
-<parameter_name>:<parameter_value>
```

매개 변수의 이름 앞에는 하이픈 (-)이 붙습니다 .이는 하이픈 뒤의 단어가 매개 변수 이름 임을 PowerShell에 신호로 보냅니다. 매개 변수 이름 및 값은 공백이 나 콜론 문자로 구분할 수 있습니다. 일부 매개 변수는 매개 변수 값을 요구 하거나 허용 하지 않습니다. 다른 매개 변수에는 값이 필요 하지만 명령에는 매개 변수 이름이 필요 하지 않습니다.

매개 변수의 형식과 해당 매개 변수의 요구 사항은 서로 다릅니다. 명령의 매개 변수에 대 한 정보를 확인 하려면 cmdlet을 사용 `Get-Help` 합니다. 예를 들어 cmdlet의 매개 변수에 대 한 정보 `Get-ChildItem` 를 찾으려면 다음을 입력 합니다.

```powershell
Get-Help Get-ChildItem
```

스크립트의 매개 변수에 대 한 정보를 찾으려면 스크립트 파일의 전체 경로를 사용 합니다. 다음은 그 예입니다. 

```powershell
Get-Help $home\Documents\Scripts\Get-Function.ps1
```

`Get-Help`Cmdlet은 설명, 명령 구문, 매개 변수에 대 한 정보 및 명령에서 매개 변수를 사용 하는 방법을 보여 주는 예제를 포함 하 여 명령에 대 한 다양 한 세부 정보를 반환 합니다.

Cmdlet의 Parameter 매개 변수를 사용 하 여 `Get-Help` 특정 매개 변수에 대 한 정보를 찾을 수도 있습니다. 또는 **매개** 변수 매개 변수를 와일드 카드 문자 () 값과 함께 사용 `*` 하 여 명령의 모든 매개 변수에 대 한 정보를 찾을 수 있습니다. 예를 들어 다음 명령은 cmdlet의 모든 매개 변수에 대 한 정보를 가져옵니다 `Get-Member` .

```powershell
Get-Help Get-Member -Parameter *
```

### <a name="default-parameter-values"></a>기본 매개 변수 값

선택적 매개 변수에는 매개 변수가 명령에 지정 되지 않은 경우 사용 되거나 사용 되는 값인 기본값이 있습니다.

예를 들어 많은 cmdlet의 **ComputerName** 매개 변수 기본값은 로컬 컴퓨터의 이름입니다. 따라서 **ComputerName** 매개 변수가 지정 되지 않은 경우 로컬 컴퓨터 이름이 명령에 사용 됩니다.

기본 매개 변수 값을 찾으려면 cmdlet에 대 한 도움말 항목을 참조 하세요. 매개 변수 설명은 기본값을 포함 해야 합니다.

Cmdlet 또는 고급 함수의 매개 변수에 대해 사용자 지정 기본값을 설정할 수도 있습니다. 사용자 지정 기본값을 설정 하는 방법에 대 한 자세한 내용은 [about_Parameters_Default_Values](about_Parameters_Default_Values.md)를 참조 하세요.

### <a name="parameter-attribute-table"></a>Parameter 특성 표

Cmdlet의 **Full**, **Parameter** 또는 **Online** 매개 변수를 사용 하는 경우 매개 변수에 `Get-Help` `Get-Help` 대 한 자세한 정보를 포함 하는 매개 변수 특성 테이블을 표시 합니다.

이 정보는 매개 변수를 사용 하기 위해 알아야 하는 세부 정보를 포함 합니다.
예를 들어 cmdlet에 대 한 도움말 항목에는 `Get-ChildItem` Path 매개 변수에 대 한 다음과 같은 세부 정보가 포함 됩니다.

```
-path <string[]>
    Specifies a path of one or more locations. Wildcard characters are
    permitted. The default location is the current directory (.).

Required?                    false
Position?                    0
Default value                Current directory
Accept pipeline input?       true (ByValue, ByPropertyName)
Accept wildcard characters?  true
```

매개 변수 정보에는 매개 변수 구문, 매개 변수에 대 한 설명 및 매개 변수 특성이 포함 됩니다. 다음 섹션에서는 매개 변수 특성에 대해 설명 합니다.

#### <a name="parameter-required"></a>매개 변수가 필요 합니다.

이 설정은 매개 변수가 필수 인지 여부, 즉이 cmdlet을 사용 하는 모든 명령에이 매개 변수가 포함 되어야 하는지 여부를 나타냅니다. 값이 **True** 이 고 매개 변수가 명령에 없으면 PowerShell에서 매개 변수의 값을 묻는 메시지를 표시 합니다.

#### <a name="parameter-position"></a>매개 변수 위치

`Position`설정이 양의 정수로 설정 된 경우 매개 변수 이름은 필요 하지 않습니다. 이 형식의 매개 변수는 위치 매개 변수 라고 하며, 숫자는 다른 위치 매개 변수와 관련 하 여 매개 변수가 표시 되어야 하는 위치를 나타냅니다. 명명 된 매개 변수는 cmdlet 이름 다음의 임의 위치에 나열 될 수 있습니다. 위치 매개 변수에 대 한 매개 변수 이름을 포함 하는 경우 매개 변수는 cmdlet 이름 다음의 임의 위치에 나열 될 수 있습니다.

예를 들어 cmdlet에는 `Get-ChildItem` Path 및 Exclude 매개 변수가 있습니다. `Position` **Path** 에 대 한 설정은 위치 매개 변수 임을 의미 하는 **0** 입니다. `Position` **Exclude** 의 설정은로 **지정** 됩니다.

즉, **경로** 에 매개 변수 이름이 필요 하지 않지만 매개 변수 값이 명령의 첫 번째 또는 유일한 명명 되지 않은 매개 변수 값 이어야 합니다.
그러나 Exclude 매개 변수는 명명 된 매개 변수 이므로 명령에서 임의의 위치에 배치할 수 있습니다.

`Position`이러한 두 매개 변수에 대 한 설정의 결과로 다음 명령 중 하나를 사용할 수 있습니다.

```powershell
Get-ChildItem -Path c:\techdocs -Exclude *.ppt
Get-ChildItem c:\techdocs -Exclude *.ppt
Get-ChildItem -Exclude *.ppt -Path c:\techdocs
Get-ChildItem -Exclude *.ppt c:\techdocs
```

매개 변수 이름을 포함 하지 않고 다른 위치 매개 변수를 포함 하는 경우 해당 매개 변수는 설정에 지정 된 순서에 따라 배치 되어야 합니다 `Position` .

#### <a name="parameter-type"></a>매개 변수 유형

이 설정은 매개 변수 값의 Microsoft .NET Framework 유형을 지정 합니다. 예를 들어, 형식이 **Int32** 인 경우 매개 변수 값은 정수 여야 합니다. 형식이 문자열인 경우 매개 변수 값은 문자열 이어야 합니다. 문자열에 공백이 포함 된 경우에는 값을 따옴표로 묶어야 합니다. 그렇지 않으면 공백이 이스케이프 문자 (') 뒤에와 야 합니다.

#### <a name="default-value"></a>기본값

이 설정은 다른 값이 제공 되지 않은 경우 매개 변수에 의해 가정 되는 값을 지정 합니다. 예를 들어 Path 매개 변수의 기본값은 대개 현재 디렉터리입니다. 필수 매개 변수에는 기본값이 없습니다.
여러 선택적 매개 변수의 경우 매개 변수가 사용 되지 않는 경우에는이 매개 변수가 적용 되지 않기 때문에 기본값이 없습니다.

#### <a name="accepts-multiple-values"></a>여러 값 허용

이 설정은 매개 변수에서 여러 매개 변수 값을 허용 하는지 여부를 나타냅니다.
매개 변수가 여러 값을 허용 하는 경우 쉼표로 구분 된 목록을 명령의 매개 변수 값으로 입력 하거나 쉼표로 구분 된 목록 (배열)을 변수에 저장 한 다음 변수를 매개 변수 값으로 지정할 수 있습니다.

예를 들어 cmdlet의 ServiceName 매개 변수는 `Get-Service` 여러 값을 허용 합니다. 다음 명령은 모두 유효 합니다.

```powershell
Get-Service -servicename winrm, netlogon
```

```powershell
$s = "winrm", "netlogon"
Get-Service -servicename $s
```

#### <a name="accepts-pipeline-input"></a>파이프라인 입력 허용

이 설정은 파이프라인 연산자 ()를 사용 `|` 하 여 값을 매개 변수로 보낼지 여부를 나타냅니다.

```
Value                    Description
-----                    -----------
False                    Indicates that you cannot pipe a value to the
                         parameter.

True (by Value)          Indicates that you can pipe any value to the
                         parameter, just so the value has the .NET
                         Framework type specified for the parameter or the
                         value can be converted to the specified .NET
                         Framework type.
```

매개 변수가 "True (값으로)" 인 경우 PowerShell은 다른 메서드를 사용 하 여 명령을 해석 하기 전에 파이프 된 모든 값을 해당 매개 변수와 연결 하려고 시도 합니다.

```
True (by Property Name)  Indicates that you can pipe a value to the
                         parameter, but the .NET Framework type of the
                         parameter must include a property with the same
                         name as the parameter.
```

예를 들어 값에 **name** 속성이 있는 경우에만 값을 **이름** 매개 변수로 파이프 할 수 있습니다.

> [!NOTE]
> 파이프라인 입력 () 또는 ()를 허용 하는 형식화 된 매개 변수는 `by Value` `by PropertyName` 매개 변수에 대해 **지연 바인딩** 스크립트 블록을 사용할 수 있도록 합니다.
>
> **지연 바인드** 스크립트 블록은 **parameterbinding** 중에 자동으로 실행 됩니다. 결과는 매개 변수에 바인딩됩니다. 또는 형식으로 정의 된 매개 변수에 대해서는 지연 바인딩이 작동 **하지** 않습니다 `ScriptBlock` `System.Object` . 스크립트 블록은 호출 되지 **않고** 를 통해 전달 됩니다.
>
> About_Script_Blocks **에서 지연 바인딩** 스크립트 블록에 대해 읽을 수 있습니다 [.](about_Script_Blocks.md)

#### <a name="accepts-wildcard-characters"></a>와일드 카드 문자 허용

이 설정은 매개 변수 값이 대상 컨테이너에 있는 둘 이상의 기존 항목에 일치할 수 있도록 매개 변수의 값에 와일드 카드 문자를 포함할 수 있는지 여부를 나타냅니다.

#### <a name="common-parameters"></a>일반 매개 변수

일반 매개 변수는 모든 cmdlet에서 사용할 수 있는 매개 변수입니다. 일반 매개 변수에 대 한 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Command_syntax](about_Command_syntax.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Parameters_Default_Values](about_Parameters_Default_Values.md)

[about_Pipelines](about_Pipelines.md)

[about_Wildcards](about_Wildcards.md)


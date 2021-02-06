---
description: 에서는 스크립트를 사용 하 여 cmdlet을 만드는 방법 인 고급 함수를 소개 합니다.
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced
ms.openlocfilehash: a0b8b027c91f2adedfcecd07bfc80392c1b1e071
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599571"
---
# <a name="about-functions-advanced"></a>함수 고급 정보

## <a name="short-description"></a>간단한 설명
에서는 스크립트를 사용 하 여 cmdlet을 만드는 방법 인 고급 함수를 소개 합니다.

## <a name="long-description"></a>자세한 설명

Cmdlet은 PowerShell의 파이프라인 의미 체계에 참여 하는 단일 명령입니다. 여기에는 이진 cmdlet, 고급 스크립트 함수, CDXML 및 워크플로가 포함 됩니다.

고급 기능을 사용 하면 PowerShell 함수로 작성 된 cmdlet을 만들 수 있습니다. 고급 함수를 사용 하면 이진 cmdlet을 작성 하 고 컴파일하지 않고도 cmdlet을 보다 쉽게 만들 수 있습니다. 이진 cmdlet은 c #과 같은 .NET 언어로 작성 된 .NET 클래스입니다.

고급 함수 `CmdletBinding` 는 특성을 사용 하 여 cmdlet 처럼 동작 하는 함수로 식별 합니다. `CmdletBinding`특성은 컴파일된 cmdlet 클래스에서 클래스를 cmdlet으로 식별 하는 데 사용 되는 cmdlet 특성과 유사 합니다. 이 특성에 대 한 자세한 내용은 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)를 참조 하세요.

다음 예제에서는 이름을 받아들인 다음 제공 된 이름을 사용 하 여 인사말을 출력 하는 함수를 보여 줍니다. 또한이 함수는 컴파일된 cmdlet의 동사-명사 쌍과 같은 동사 (보내기) 및 명사 (인사말) 쌍을 포함 하는 이름을 정의 합니다. 그러나 함수에는 동사 명사 이름을 사용할 필요가 없습니다.

```powershell
function Send-Greeting
{
    [CmdletBinding()]
    Param(
        [Parameter(Mandatory=$true)]
        [string] $Name
    )

    Process
    {
        Write-Host ("Hello " + $Name + "!")
    }
}
```

함수의 매개 변수는 매개 변수 특성을 사용 하 여 선언 됩니다.
이 특성은 단독으로 사용 하거나 별칭 특성 또는 다른 여러 매개 변수 유효성 검사 특성과 함께 사용할 수 있습니다. 매개 변수를 선언 하는 방법에 대 한 자세한 내용은 (런타임에 추가 되는 동적 매개 변수 포함) [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)을 참조 하세요.

이전 함수의 실제 작업은 cmdlet에 전달 되는 데이터를 처리 하기 위해 컴파일된 cmdlet에서 사용 하는 ProcessingRecord 메서드와 동일한 프로세스 블록에서 수행 됩니다. 이 블록은 Begin 및 End 블록과 함께 [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) 항목에 설명 되어 있습니다.

고급 함수는 다음과 같은 방법으로 컴파일된 cmdlet과 다릅니다.

- 문자열 배열이 부울 매개 변수에 바인딩되면 고급 함수 매개 변수 바인딩이 예외를 throw 하지 않습니다.
- ValidateSet 특성 및 ValidatePattern 특성은 명명 된 매개 변수를 전달할 수 없습니다.
- 고급 함수는 트랜잭션에서 사용할 수 없습니다.

## <a name="see-also"></a>참고 항목

[about_Functions](about_Functions.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

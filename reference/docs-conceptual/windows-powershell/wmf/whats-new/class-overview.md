---
ms.date: 07/29/2020
title: PowerShell 5.0의 새로운 언어 기능
description: PowerShell 5.0에서는 다른 개체 지향 프로그래밍 언어와 유사한 형식 구문 및 의미 체계를 사용하여 클래스 및 기타 사용자 정의 형식을 정의하는 기능을 추가했습니다.
ms.openlocfilehash: 31ff54ba6f2800a0680c1a2db3832ca97246973d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663314"
---
# <a name="new-language-features-in-powershell-50"></a>PowerShell 5.0의 새로운 언어 기능

PowerShell 5.0에서는 다른 개체 지향 프로그래밍 언어와 유사한 형식 구문 및 의미 체계를 사용하여 클래스 및 기타 사용자 정의 형식을 정의하는 기능을 추가했습니다. 목표는 개발자 및 IT 전문가가 보다 광범위한 사용 사례에 PowerShell을 적용하고, PowerShell 아티팩트(예: DSC 리소스)의 개발을 간소화하며, 관리 화면의 적용을 가속화할 수 있도록 하는 것입니다.

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

새 필드인 **ImplementingAssembly** 가 **ModuleInfo** 에 추가되었습니다. 이 필드는 스크립트에서 클래스를 정의하는 경우 스크립트 모듈에 대해 만들어진 동적 어셈블리 또는 이진 모듈에 대해 로드된 어셈블리로 설정됩니다. **ModuleType** 이 **Manifest** 인 경우에는 설정되지 않습니다.

**ImplementingAssembly** 필드에서 리플렉션하면 모듈에서 리소스를 검색합니다. 즉, PowerShell이나 다른 관리 언어로 작성된 리소스를 검색할 수 있습니다.

## <a name="further-reading"></a>추가 정보

- [about_Classes](/powershell/module/microsoft.powershell.core/about/about_classes)
- [about_Enum](/powershell/module/microsoft.powershell.core/about/about_enum)
- [about_Classes_and_DSC](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)

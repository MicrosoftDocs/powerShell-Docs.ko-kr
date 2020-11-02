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
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="cc97e-103">PowerShell 5.0의 새로운 언어 기능</span><span class="sxs-lookup"><span data-stu-id="cc97e-103">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="cc97e-104">PowerShell 5.0에서는 다른 개체 지향 프로그래밍 언어와 유사한 형식 구문 및 의미 체계를 사용하여 클래스 및 기타 사용자 정의 형식을 정의하는 기능을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="cc97e-105">목표는 개발자 및 IT 전문가가 보다 광범위한 사용 사례에 PowerShell을 적용하고, PowerShell 아티팩트(예: DSC 리소스)의 개발을 간소화하며, 관리 화면의 적용을 가속화할 수 있도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

<span data-ttu-id="cc97e-106">PowerShell 5.0은 PowerShell에서 다음과 같은 새로운 언어 요소를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-106">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="cc97e-107">Class 키워드</span><span class="sxs-lookup"><span data-stu-id="cc97e-107">Class keyword</span></span>

<span data-ttu-id="cc97e-108">`class` 키워드는 새 클래스를 정의하며,</span><span class="sxs-lookup"><span data-stu-id="cc97e-108">The `class` keyword defines a new class.</span></span> <span data-ttu-id="cc97e-109">진정한 .NET Framework 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-109">This is a true .NET Framework type.</span></span> <span data-ttu-id="cc97e-110">클래스 멤버는 공용이지만 모듈 범위 내에서만 공용입니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-110">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="cc97e-111">형식 이름을 문자열로 참조할 수 없으며(예를 들어 `New-Object`는 작동하지 않음), 이 릴리스에서는 형식 리터럴(예: 클래스가 정의된 스크립트 또는 모듈 파일 외부의 `[MyClass]`)을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-111">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="cc97e-112">Enum 키워드 및 열거형</span><span class="sxs-lookup"><span data-stu-id="cc97e-112">Enum keyword and enumerations</span></span>

<span data-ttu-id="cc97e-113">`enum` 키워드에 대한 지원이 추가되어 줄 바꿈을 구분 기호로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-113">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="cc97e-114">현재는 열거자 자체와 관련하여 열거자를 정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-114">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="cc97e-115">그러나 다음 예제와 같이 다른 열거형 측면에서 열거형을 초기화할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-115">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="cc97e-116">또한 기본 형식은 지정할 수 없으며, 항상 `[int]`입니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-116">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="cc97e-117">열거자 값은 구문 분석 시간 상수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-117">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="cc97e-118">이 값을 호출된 명령의 결과로 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-118">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="cc97e-119">열거형은 다음 예제와 같이 산술 연산자를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-119">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="cc97e-120">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="cc97e-120">Import-DscResource</span></span>

<span data-ttu-id="cc97e-121">`Import-DscResource`는 이제 진정한 동적 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-121">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="cc97e-122">PowerShell은 지정된 모듈의 루트 모듈을 구문 분석하여 **DscResource** 특성이 포함된 클래스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-122">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="cc97e-123">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="cc97e-123">ImplementingAssembly</span></span>

<span data-ttu-id="cc97e-124">새 필드인 **ImplementingAssembly** 가 **ModuleInfo** 에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-124">A new field, **ImplementingAssembly** , has been added to **ModuleInfo** .</span></span> <span data-ttu-id="cc97e-125">이 필드는 스크립트에서 클래스를 정의하는 경우 스크립트 모듈에 대해 만들어진 동적 어셈블리 또는 이진 모듈에 대해 로드된 어셈블리로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-125">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="cc97e-126">**ModuleType** 이 **Manifest** 인 경우에는 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-126">It is not set when **ModuleType** is **Manifest** .</span></span>

<span data-ttu-id="cc97e-127">**ImplementingAssembly** 필드에서 리플렉션하면 모듈에서 리소스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-127">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="cc97e-128">즉, PowerShell이나 다른 관리 언어로 작성된 리소스를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc97e-128">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

## <a name="further-reading"></a><span data-ttu-id="cc97e-129">추가 정보</span><span class="sxs-lookup"><span data-stu-id="cc97e-129">Further reading</span></span>

- [<span data-ttu-id="cc97e-130">about_Classes</span><span class="sxs-lookup"><span data-stu-id="cc97e-130">about_Classes</span></span>](/powershell/module/microsoft.powershell.core/about/about_classes)
- [<span data-ttu-id="cc97e-131">about_Enum</span><span class="sxs-lookup"><span data-stu-id="cc97e-131">about_Enum</span></span>](/powershell/module/microsoft.powershell.core/about/about_enum)
- [<span data-ttu-id="cc97e-132">about_Classes_and_DSC</span><span class="sxs-lookup"><span data-stu-id="cc97e-132">about_Classes_and_DSC</span></span>](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)

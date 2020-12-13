---
ms.date: 09/13/2016
ms.topic: reference
title: 매개 변수로 속성 선언
description: 매개 변수로 속성 선언
ms.openlocfilehash: ade7928e2ca277da8bbd1a5e04997bd1d05f1e5d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653152"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="1903b-103">매개 변수로 속성 선언</span><span class="sxs-lookup"><span data-stu-id="1903b-103">Declaring Properties as Parameters</span></span>

<span data-ttu-id="1903b-104">이 항목에서는 cmdlet의 매개 변수를 선언 하기 전에 이해 해야 하는 기본적인 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1903b-104">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="1903b-105">Cmdlet 클래스 내에서 cmdlet의 매개 변수를 선언 하려면 각 매개 변수를 나타내는 공용 속성을 정의한 다음 각 속성에 하나 이상의 매개 변수 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1903b-105">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="1903b-106">Windows PowerShell 런타임에서는 매개 변수 특성을 사용 하 여 속성을 cmdlet 매개 변수로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="1903b-106">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="1903b-107">매개 변수 특성을 선언 하는 기본 구문은 `[Parameter()]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="1903b-107">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="1903b-108">필수 매개 변수로 정의 된 속성의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1903b-108">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="1903b-109">매개 변수에 대해 기억할 몇 가지 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1903b-109">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="1903b-110">매개 변수는 명시적으로 public으로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1903b-110">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="1903b-111">공용 기본으로 표시 되지 않은 매개 변수는 Windows PowerShell 런타임에 의해 검색 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1903b-111">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="1903b-112">매개 변수는 매개 변수 유효성 검사를 향상 시킬 수 있도록 Microsoft .NET Framework 형식으로 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1903b-112">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="1903b-113">예를 들어 값 집합에서 하나의 값으로 제한 되는 매개 변수는 열거형 형식으로 정의 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1903b-113">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="1903b-114">URI (Uniform Resource Identifier) 값을 사용 하는 매개 변수는 system.string [형식 이어야 합니다.](/dotnet/api/System.Uri)</span><span class="sxs-lookup"><span data-stu-id="1903b-114">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="1903b-115">자유 형식 텍스트 속성에 대 한 기본 문자열 매개 변수를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1903b-115">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="1903b-116">매개 변수를 원하는 수 만큼 매개 변수 집합에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1903b-116">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="1903b-117">매개 변수 집합에 대 한 자세한 내용은 [Cmdlet 매개 변수 집합](./cmdlet-parameter-sets.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1903b-117">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="1903b-118">또한 Windows PowerShell에서는 모든 cmdlet에 자동으로 사용할 수 있는 공통 매개 변수 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1903b-118">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="1903b-119">이러한 매개 변수 및 해당 별칭에 대 한 자세한 내용은 [Cmdlet 일반 매개 변수](./common-parameter-names.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1903b-119">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1903b-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1903b-120">See Also</span></span>

[<span data-ttu-id="1903b-121">Cmdlet 일반 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1903b-121">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="1903b-122">Cmdlet 매개 변수의 유형</span><span class="sxs-lookup"><span data-stu-id="1903b-122">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

<span data-ttu-id="1903b-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="1903b-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

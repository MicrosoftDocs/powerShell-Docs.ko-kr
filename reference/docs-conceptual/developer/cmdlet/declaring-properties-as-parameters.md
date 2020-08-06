---
title: 속성을 매개 변수로 선언 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 63113f541df534b1f720ceb06e14b5031f2311b2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774646"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="d3ec0-102">매개 변수로 속성 선언</span><span class="sxs-lookup"><span data-stu-id="d3ec0-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="d3ec0-103">이 항목에서는 cmdlet의 매개 변수를 선언 하기 전에 이해 해야 하는 기본적인 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="d3ec0-104">Cmdlet 클래스 내에서 cmdlet의 매개 변수를 선언 하려면 각 매개 변수를 나타내는 공용 속성을 정의한 다음 각 속성에 하나 이상의 매개 변수 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="d3ec0-105">Windows PowerShell 런타임에서는 매개 변수 특성을 사용 하 여 속성을 cmdlet 매개 변수로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="d3ec0-106">매개 변수 특성을 선언 하는 기본 구문은 `[Parameter()]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="d3ec0-107">필수 매개 변수로 정의 된 속성의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="d3ec0-108">매개 변수에 대해 기억할 몇 가지 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="d3ec0-109">매개 변수는 명시적으로 public으로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="d3ec0-110">공용 기본으로 표시 되지 않은 매개 변수는 Windows PowerShell 런타임에 의해 검색 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="d3ec0-111">매개 변수는 매개 변수 유효성 검사를 향상 시킬 수 있도록 Microsoft .NET Framework 형식으로 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="d3ec0-112">예를 들어 값 집합에서 하나의 값으로 제한 되는 매개 변수는 열거형 형식으로 정의 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="d3ec0-113">URI (Uniform Resource Identifier) 값을 사용 하는 매개 변수는 system.string [형식 이어야 합니다.](/dotnet/api/System.Uri)</span><span class="sxs-lookup"><span data-stu-id="d3ec0-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="d3ec0-114">자유 형식 텍스트 속성에 대 한 기본 문자열 매개 변수를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="d3ec0-115">매개 변수를 원하는 수 만큼 매개 변수 집합에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="d3ec0-116">매개 변수 집합에 대 한 자세한 내용은 [Cmdlet 매개 변수 집합](./cmdlet-parameter-sets.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="d3ec0-117">또한 Windows PowerShell에서는 모든 cmdlet에 자동으로 사용할 수 있는 공통 매개 변수 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="d3ec0-118">이러한 매개 변수 및 해당 별칭에 대 한 자세한 내용은 [Cmdlet 일반 매개 변수](./common-parameter-names.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d3ec0-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d3ec0-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3ec0-119">See Also</span></span>

[<span data-ttu-id="d3ec0-120">Cmdlet 일반 매개 변수</span><span class="sxs-lookup"><span data-stu-id="d3ec0-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="d3ec0-121">Cmdlet 매개 변수의 유형</span><span class="sxs-lookup"><span data-stu-id="d3ec0-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="d3ec0-122">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="d3ec0-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

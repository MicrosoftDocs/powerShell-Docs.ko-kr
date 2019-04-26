---
title: 속성을 매개 변수로 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068269"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="d22fb-102">매개 변수로 속성 선언</span><span class="sxs-lookup"><span data-stu-id="d22fb-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="d22fb-103">이 항목에서는 cmdlet의 매개 변수를 선언 하기 전에 이해 해야 하는 기본 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="d22fb-104">Cmdlet 클래스 내에서 cmdlet의 매개 변수를 선언 하려면 각 매개 변수를 나타내는 공용 속성을 정의 하 고 각 속성에 하나 이상의 매개 변수 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="d22fb-105">Windows PowerShell 런타임에 cmdlet 매개 변수로 속성을 식별 하는 매개 변수 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="d22fb-106">매개 변수 특성을 선언 하기 위한 기본 구문은 `[Parameter()]`합니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="d22fb-107">필수 매개 변수로 정의 속성의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="d22fb-108">몇 가지 매개 변수를 기억해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="d22fb-109">매개 변수 해야 명시적으로 공용으로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="d22fb-110">매개 변수를 내부 공용 기본으로 표시 되지 않은 및 Windows PowerShell 런타임에 의해 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="d22fb-111">매개 변수는 더 나은 매개 변수 유효성 검사를 제공 하려면 Microsoft.NET Framework 형식으로 정의 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="d22fb-112">예를 들어, 매개 변수 값 집합에서 하나의 값으로 제한 되는 열거형 형식으로 정의 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="d22fb-113">리소스 URI (Uniform Identifier) 값을 사용 하는 매개 변수 형식 이어야 [System.Uri](/dotnet/api/System.Uri)합니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="d22fb-114">자유 형식 제외한 모든 텍스트 속성에 대 한 기본 문자열 매개 변수를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="d22fb-115">임의 개수의 매개 변수 집합에 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="d22fb-116">매개 변수 집합에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수 설정](./cmdlet-parameter-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="d22fb-117">Windows PowerShell에는 또한 모든 cmdlet에 자동으로 사용할 수 있는 일반적인 매개 변수 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="d22fb-118">이러한 매개 변수 및 해당 별칭에 대 한 자세한 내용은 참조 하세요. [cmdlet은 공통 매개 변수](./common-parameter-names.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d22fb-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d22fb-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d22fb-119">See Also</span></span>

[<span data-ttu-id="d22fb-120">Cmdlet은 공통 매개 변수</span><span class="sxs-lookup"><span data-stu-id="d22fb-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="d22fb-121">Cmdlet 매개 변수 형식</span><span class="sxs-lookup"><span data-stu-id="d22fb-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

<span data-ttu-id="d22fb-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="d22fb-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

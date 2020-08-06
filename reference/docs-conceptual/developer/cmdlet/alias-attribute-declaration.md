---
title: Alias 특성 선언 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.openlocfilehash: 4c1ff34a244611173ca919a44d6598189b19dc98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782415"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="74abf-102">Alias 특성 선언</span><span class="sxs-lookup"><span data-stu-id="74abf-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="74abf-103">Alias 특성을 사용 하면 사용자가 cmdlet 매개 변수에 대해 다른 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74abf-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="74abf-104">별칭을 사용 하 여 매개 변수 이름에 대 한 바로 가기를 제공 하거나 다양 한 시나리오에 적합 한 다른 이름을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74abf-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="74abf-105">구문</span><span class="sxs-lookup"><span data-stu-id="74abf-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="74abf-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="74abf-106">Parameters</span></span>

<span data-ttu-id="74abf-107">`aliasName`(String []) 필수.</span><span class="sxs-lookup"><span data-stu-id="74abf-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="74abf-108">Cmdlet 매개 변수에 대 한 쉼표로 구분 된 별칭 이름 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74abf-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="74abf-109">설명</span><span class="sxs-lookup"><span data-stu-id="74abf-109">Remarks</span></span>

- <span data-ttu-id="74abf-110">Alias 특성은 cmdlet 매개 변수를 지정할 때 Parameter 특성과 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74abf-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="74abf-111">이러한 특성을 선언 하는 방법에 대 한 자세한 내용은 [Cmdlet 매개 변수를 선언 하는 방법](./how-to-declare-cmdlet-parameters.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="74abf-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="74abf-112">각 별칭 이름은 cmdlet 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74abf-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="74abf-113">Windows PowerShell은 중복 된 별칭 이름을 확인 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74abf-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="74abf-114">별칭 특성은 cmdlet의 각 매개 변수에 대해 한 번만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74abf-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="74abf-115">Alias 특성은 [Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74abf-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="74abf-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74abf-116">See Also</span></span>

[<span data-ttu-id="74abf-117">매개 변수 별칭</span><span class="sxs-lookup"><span data-stu-id="74abf-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="74abf-118">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="74abf-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

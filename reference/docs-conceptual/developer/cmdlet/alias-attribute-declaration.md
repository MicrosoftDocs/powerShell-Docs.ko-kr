---
ms.date: 09/13/2016
ms.topic: reference
title: Alias 특성 선언
description: Alias 특성 선언
ms.openlocfilehash: f2fe49578da2c795643b1f80fa44deefe1dbff09
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668306"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="9fcbd-103">Alias 특성 선언</span><span class="sxs-lookup"><span data-stu-id="9fcbd-103">Alias Attribute Declaration</span></span>

<span data-ttu-id="9fcbd-104">Alias 특성을 사용 하면 사용자가 cmdlet 매개 변수에 대해 다른 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fcbd-104">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="9fcbd-105">별칭을 사용 하 여 매개 변수 이름에 대 한 바로 가기를 제공 하거나 다양 한 시나리오에 적합 한 다른 이름을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fcbd-105">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="9fcbd-106">구문</span><span class="sxs-lookup"><span data-stu-id="9fcbd-106">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="9fcbd-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9fcbd-107">Parameters</span></span>

<span data-ttu-id="9fcbd-108">`aliasName` (String []) 필수.</span><span class="sxs-lookup"><span data-stu-id="9fcbd-108">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="9fcbd-109">Cmdlet 매개 변수에 대 한 쉼표로 구분 된 별칭 이름 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fcbd-109">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="9fcbd-110">설명</span><span class="sxs-lookup"><span data-stu-id="9fcbd-110">Remarks</span></span>

- <span data-ttu-id="9fcbd-111">Alias 특성은 cmdlet 매개 변수를 지정할 때 Parameter 특성과 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fcbd-111">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="9fcbd-112">이러한 특성을 선언 하는 방법에 대 한 자세한 내용은 [Cmdlet 매개 변수를 선언 하는 방법](./how-to-declare-cmdlet-parameters.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9fcbd-112">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="9fcbd-113">각 별칭 이름은 cmdlet 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fcbd-113">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="9fcbd-114">Windows PowerShell은 중복 된 별칭 이름을 확인 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fcbd-114">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="9fcbd-115">별칭 특성은 cmdlet의 각 매개 변수에 대해 한 번만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fcbd-115">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="9fcbd-116">Alias 특성은 [Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fcbd-116">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fcbd-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9fcbd-117">See Also</span></span>

[<span data-ttu-id="9fcbd-118">매개 변수 별칭</span><span class="sxs-lookup"><span data-stu-id="9fcbd-118">Parameter Aliases</span></span>](./parameter-aliases.md)

<span data-ttu-id="9fcbd-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="9fcbd-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

---
title: Alias 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72370022"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="86e07-102">Alias 특성 선언</span><span class="sxs-lookup"><span data-stu-id="86e07-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="86e07-103">Alias 특성을 사용 하면 사용자가 cmdlet 매개 변수에 대해 다른 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86e07-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="86e07-104">별칭을 사용 하 여 매개 변수 이름에 대 한 바로 가기를 제공 하거나 다양 한 시나리오에 적합 한 다른 이름을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86e07-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="86e07-105">구문</span><span class="sxs-lookup"><span data-stu-id="86e07-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="86e07-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="86e07-106">Parameters</span></span>

<span data-ttu-id="86e07-107">`aliasName` (String [])이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="86e07-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="86e07-108">Cmdlet 매개 변수에 대 한 쉼표로 구분 된 별칭 이름 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86e07-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="86e07-109">설명</span><span class="sxs-lookup"><span data-stu-id="86e07-109">Remarks</span></span>

- <span data-ttu-id="86e07-110">Alias 특성은 cmdlet 매개 변수를 지정할 때 Parameter 특성과 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86e07-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="86e07-111">이러한 특성을 선언 하는 방법에 대 한 자세한 내용은 [Cmdlet 매개 변수를 선언 하는 방법](./how-to-declare-cmdlet-parameters.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86e07-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="86e07-112">각 별칭 이름은 cmdlet 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86e07-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="86e07-113">Windows PowerShell은 중복 된 별칭 이름을 확인 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86e07-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="86e07-114">별칭 특성은 cmdlet의 각 매개 변수에 대해 한 번만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86e07-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="86e07-115">Alias 특성은 [Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86e07-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="86e07-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86e07-116">See Also</span></span>

[<span data-ttu-id="86e07-117">매개 변수 별칭</span><span class="sxs-lookup"><span data-stu-id="86e07-117">Parameter Aliases</span></span>](./parameter-aliases.md)

<span data-ttu-id="86e07-118">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="86e07-118">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

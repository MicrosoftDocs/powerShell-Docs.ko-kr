---
title: 매개 변수 별칭 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853319"
---
# <a name="parameter-aliases"></a><span data-ttu-id="a14e6-102">매개 변수 별칭</span><span class="sxs-lookup"><span data-stu-id="a14e6-102">Parameter Aliases</span></span>

<span data-ttu-id="a14e6-103">Cmdlet 매개 변수 별칭을 가질 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="a14e6-104">입력 또는 명령에서 매개 변수를 지정 하는 경우 매개 변수 이름 대신 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="a14e6-105">별칭을 사용할 때의 이점</span><span class="sxs-lookup"><span data-stu-id="a14e6-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="a14e6-106">매개 변수 별칭 추가 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="a14e6-107">바로 가기를 사용자는 cmdlet를 호출할 때 전체 매개 변수 이름을 사용 하지 않아도 되도록 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="a14e6-108">예를 들어, 매개 변수 이름 "컴퓨터 이름" 대신 "CN" 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="a14e6-109">동일한 매개 변수에 다른 이름을 제공 하려는 경우 여러 별칭을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="a14e6-110">다른 방법으로 동일한 데이터를 참조 하는 여러 사용자 그룹을 사용 해야 할 경우 여러 별칭을 정의 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="a14e6-111">제공할 수 있습니다 이전 버전과 호환성 기존 스크립트에 대 한 매개 변수의 이름을 변경 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="a14e6-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="a14e6-112">Alias 특성 ValueFromPipelineByName 특성 함께 사용 하면 cmdlet에 다른 개체 형식에 바인딩할 수 있도록 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="a14e6-113">예를 들어 서로 다른 형식의 두 개체를 해야 하 고 첫 번째 개체 작성기 속성 있어 두 번째 개체는 편집기 속성 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="a14e6-114">Cmdlet 매개 변수 있는 경우 기록기 및 편집기 별칭 및 cmdlet은 속성 이름에 따라 파이프라인 입력 허용, cmdlet은 두 개의 매개 변수 별칭을 사용 하 여 두 개체에 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="a14e6-115">특정 매개 변수를 사용 하 여 사용할 수 있는 별칭에 대 한 자세한 내용은 참조 하세요. [일반 매개 변수 이름](./common-parameter-names.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="a14e6-116">매개 변수 별칭을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="a14e6-117">매개 변수의 별칭을 정의 하려면 다음 매개 변수 선언에 표시 된 것과 같이 Alias 특성을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="a14e6-118">이 예제에서는 여러 개의 별칭은 동일한 매개 변수에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a14e6-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="a14e6-119">(자세한 내용은[Cmdlet 매개 변수를 선언 하는 방법을](./how-to-declare-cmdlet-parameters.md).)</span><span class="sxs-lookup"><span data-stu-id="a14e6-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a><span data-ttu-id="a14e6-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a14e6-120">See Also</span></span>

[<span data-ttu-id="a14e6-121">일반 매개 변수 이름</span><span class="sxs-lookup"><span data-stu-id="a14e6-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="a14e6-122">Cmdlet 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="a14e6-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

<span data-ttu-id="a14e6-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="a14e6-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

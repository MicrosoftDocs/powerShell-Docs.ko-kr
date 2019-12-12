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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369592"
---
# <a name="parameter-aliases"></a><span data-ttu-id="6a7de-102">매개 변수 별칭</span><span class="sxs-lookup"><span data-stu-id="6a7de-102">Parameter Aliases</span></span>

<span data-ttu-id="6a7de-103">cmdlet 매개 변수에는 별칭을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7de-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="6a7de-104">명령에서 매개 변수를 입력 하거나 지정 하는 경우 매개 변수 이름 대신 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7de-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="6a7de-105">별칭 사용의 이점</span><span class="sxs-lookup"><span data-stu-id="6a7de-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="6a7de-106">매개 변수에 별칭을 추가 하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7de-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="6a7de-107">사용자가 cmdlet을 호출할 때 전체 매개 변수 이름을 사용 하지 않아도 되도록 바로 가기를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7de-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="6a7de-108">예를 들어 "ComputerName" 매개 변수 이름 대신 "CN" 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7de-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="6a7de-109">동일한 매개 변수에 다른 이름을 제공 하려는 경우 여러 별칭을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7de-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="6a7de-110">여러 다른 방법으로 동일한 데이터를 참조 하는 여러 사용자 그룹으로 작업 해야 하는 경우 여러 별칭을 정의 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7de-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="6a7de-111">매개 변수 이름이 변경 되는 경우 기존 스크립트에 대 한 이전 버전과의 호환성을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7de-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="6a7de-112">ValueFromPipelineByName 특성과 함께 Alias 특성을 사용 하 여 cmdlet이 다른 개체 형식에 바인딩할 수 있도록 하는 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7de-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="6a7de-113">예를 들어 다른 형식의 개체가 두 개 있고 첫 번째 개체에는 기록기 속성이 있고 두 번째 개체에는 편집기 속성이 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7de-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="6a7de-114">Cmdlet에 작성기 및 편집기 별칭이 있는 매개 변수가 있고 속성 이름을 기반으로 하는 cmdlet의 파이프라인 입력이 허용 되는 경우 cmdlet은 두 개의 매개 변수 별칭을 사용 하 여 두 개체에 모두 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7de-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="6a7de-115">특정 매개 변수와 함께 사용할 수 있는 별칭에 대 한 자세한 내용은 [일반 매개 변수 이름](./common-parameter-names.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6a7de-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="6a7de-116">매개 변수 별칭 정의</span><span class="sxs-lookup"><span data-stu-id="6a7de-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="6a7de-117">매개 변수에 대 한 별칭을 정의 하려면 다음 매개 변수 선언에 표시 된 것 처럼 별칭 특성을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7de-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="6a7de-118">이 예제에서는 동일한 매개 변수에 대 한 여러 별칭을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7de-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="6a7de-119">(자세한 내용은[Cmdlet 매개 변수를 선언 하는 방법](./how-to-declare-cmdlet-parameters.md)을 참조 하세요.)</span><span class="sxs-lookup"><span data-stu-id="6a7de-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6a7de-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a7de-120">See Also</span></span>

[<span data-ttu-id="6a7de-121">일반 매개 변수 이름</span><span class="sxs-lookup"><span data-stu-id="6a7de-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="6a7de-122">Cmdlet 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="6a7de-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

<span data-ttu-id="6a7de-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="6a7de-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

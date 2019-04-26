---
title: 매개 변수 집합을 선언 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067895"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="05a2c-102">매개 변수 집합을 선언하는 방법</span><span class="sxs-lookup"><span data-stu-id="05a2c-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="05a2c-103">이 예제에서는 cmdlet에 대 한 매개 변수를 선언 하는 경우 두 매개 변수 집합을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="05a2c-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="05a2c-104">각 매개 변수 집합에는 고유한 매개 변수 및 매개 변수 집합 모두에서 사용 되는 공유 매개 변수 모두에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05a2c-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="05a2c-105">매개 변수 집합을 기본 매개 변수 집합을 지정 하는 방법을 포함 하는 방법에 대 한 자세한 내용은 참조 [Cmdlet 매개 변수 설정](./cmdlet-parameter-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="05a2c-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05a2c-106">가능 하면 필수 매개 변수로 설정할 매개 변수의 고유한 매개 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="05a2c-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="05a2c-107">그러나 매개 변수를 지정 하지 않고 실행 하려면 cmdlet을 사용 하도록 하려는 경우 고유한 매개 변수는 선택적 매개 변수를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05a2c-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="05a2c-108">예를 들어, 고유한 매개 변수는 `Get-Command` cmdlet은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="05a2c-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="05a2c-109">두 매개 변수 집합을 정의 하는 방법</span><span class="sxs-lookup"><span data-stu-id="05a2c-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="05a2c-110">추가 된 `ParameterSet` 키워드를 첫 번째 매개 변수 집합의 고유한 매개 변수, 매개 변수 속성.</span><span class="sxs-lookup"><span data-stu-id="05a2c-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. <span data-ttu-id="05a2c-111">추가 된 `ParameterSet` 키워드를 두 번째 매개 변수 집합의 고유한 매개 변수, 매개 변수 속성.</span><span class="sxs-lookup"><span data-stu-id="05a2c-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. <span data-ttu-id="05a2c-112">두 매개 변수 집합에 속하는 매개 변수에 각 매개 변수 집합에 대 한 매개 변수 특성을 추가한 다음 추가 `ParameterSet` 각 집합에는 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="05a2c-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="05a2c-113">각 매개 변수 특성의 해당 매개 변수를 정의 하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05a2c-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="05a2c-114">하나의 집합에는 선택 사항이 며 다른 필수 매개 변수 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05a2c-114">A parameter can be optional in one set and mandatory in another.</span></span>

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a><span data-ttu-id="05a2c-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05a2c-115">See Also</span></span>

[<span data-ttu-id="05a2c-116">Cmdlet 매개 변수 집합</span><span class="sxs-lookup"><span data-stu-id="05a2c-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

<span data-ttu-id="05a2c-117">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="05a2c-117">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

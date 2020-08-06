---
title: 매개 변수 집합을 선언 하는 방법 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e6d06a9a78356693fe7a338dc5c9207044b23441
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784166"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="33bae-102">매개 변수 집합을 선언하는 방법</span><span class="sxs-lookup"><span data-stu-id="33bae-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="33bae-103">이 예에서는 cmdlet에 대 한 매개 변수를 선언할 때 두 개의 매개 변수 집합을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="33bae-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="33bae-104">각 매개 변수 집합에는 고유한 매개 변수 및 두 매개 변수 집합에서 사용 하는 공유 매개 변수가 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33bae-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="33bae-105">기본 매개 변수 집합을 지정 하는 방법을 비롯 하 여 매개 변수 집합에 대 한 자세한 내용은 [Cmdlet 매개 변수 집합](./cmdlet-parameter-sets.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33bae-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="33bae-106">가능 하면 매개 변수 집합의 unique 매개 변수를 필수 매개 변수로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="33bae-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="33bae-107">그러나 매개 변수를 지정 하지 않고 cmdlet을 실행 하려는 경우에는 unique 매개 변수를 선택적 매개 변수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33bae-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="33bae-108">예를 들어 cmdlet의 unique 매개 변수는 `Get-Command` 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="33bae-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="33bae-109">두 매개 변수 집합을 정의 하는 방법</span><span class="sxs-lookup"><span data-stu-id="33bae-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="33bae-110">`ParameterSet`첫 번째 매개 변수 집합의 고유 매개 변수에 대 한 매개 변수 특성에 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="33bae-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

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

2. <span data-ttu-id="33bae-111">`ParameterSet`두 번째 매개 변수 집합의 고유 매개 변수에 대 한 매개 변수 특성에 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="33bae-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

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

3. <span data-ttu-id="33bae-112">두 매개 변수 집합에 속하는 매개 변수의 경우 각 매개 변수 집합에 대 한 매개 변수 특성을 추가한 다음 `ParameterSet` 각 집합에 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="33bae-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="33bae-113">각 매개 변수 특성에서 매개 변수를 정의 하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33bae-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="33bae-114">매개 변수는 한 집합에서 선택 사항이 며 다른 집합에서 필수 매개 변수가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33bae-114">A parameter can be optional in one set and mandatory in another.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="33bae-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="33bae-115">See Also</span></span>

[<span data-ttu-id="33bae-116">Cmdlet 매개 변수 집합</span><span class="sxs-lookup"><span data-stu-id="33bae-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="33bae-117">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="33bae-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

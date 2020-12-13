---
ms.date: 09/13/2016
ms.topic: reference
title: 매개 변수 집합을 선언하는 방법
description: 매개 변수 집합을 선언하는 방법
ms.openlocfilehash: bd4d504a9fe6c7f7626901c49bc08851244f0995
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667065"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="2b343-103">매개 변수 집합을 선언하는 방법</span><span class="sxs-lookup"><span data-stu-id="2b343-103">How to Declare Parameter Sets</span></span>

<span data-ttu-id="2b343-104">이 예에서는 cmdlet에 대 한 매개 변수를 선언할 때 두 개의 매개 변수 집합을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b343-104">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="2b343-105">각 매개 변수 집합에는 고유한 매개 변수 및 두 매개 변수 집합에서 사용 하는 공유 매개 변수가 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b343-105">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="2b343-106">기본 매개 변수 집합을 지정 하는 방법을 비롯 하 여 매개 변수 집합에 대 한 자세한 내용은 [Cmdlet 매개 변수 집합](./cmdlet-parameter-sets.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2b343-106">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b343-107">가능 하면 매개 변수 집합의 unique 매개 변수를 필수 매개 변수로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b343-107">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="2b343-108">그러나 매개 변수를 지정 하지 않고 cmdlet을 실행 하려는 경우에는 unique 매개 변수를 선택적 매개 변수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b343-108">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="2b343-109">예를 들어 cmdlet의 unique 매개 변수는 `Get-Command` 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2b343-109">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="2b343-110">두 매개 변수 집합을 정의 하는 방법</span><span class="sxs-lookup"><span data-stu-id="2b343-110">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="2b343-111">`ParameterSet`첫 번째 매개 변수 집합의 고유 매개 변수에 대 한 매개 변수 특성에 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b343-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

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

2. <span data-ttu-id="2b343-112">`ParameterSet`두 번째 매개 변수 집합의 고유 매개 변수에 대 한 매개 변수 특성에 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b343-112">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

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

3. <span data-ttu-id="2b343-113">두 매개 변수 집합에 속하는 매개 변수의 경우 각 매개 변수 집합에 대 한 매개 변수 특성을 추가한 다음 `ParameterSet` 각 집합에 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b343-113">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="2b343-114">각 매개 변수 특성에서 매개 변수를 정의 하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b343-114">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="2b343-115">매개 변수는 한 집합에서 선택 사항이 며 다른 집합에서 필수 매개 변수가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b343-115">A parameter can be optional in one set and mandatory in another.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2b343-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2b343-116">See Also</span></span>

[<span data-ttu-id="2b343-117">Cmdlet 매개 변수 집합</span><span class="sxs-lookup"><span data-stu-id="2b343-117">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

<span data-ttu-id="2b343-118">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="2b343-118">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

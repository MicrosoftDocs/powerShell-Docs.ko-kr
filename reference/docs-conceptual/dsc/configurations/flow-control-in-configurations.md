---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 구성의 조건문 및 루프
description: 이 문서에서는 조건문 및 루프를 사용하여 더 동적인 구성을 만드는 방법을 보여 줍니다. 조건문 및 루프를 매개 변수 및 구성 데이터와 결합하면 구성을 컴파일할 때 유연성을 높이고 제어를 강화할 수 있습니다.
ms.openlocfilehash: 7af8a360c17a0842fa2b95d1d1fb288323c327ef
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658457"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a><span data-ttu-id="cc014-105">구성의 조건문 및 루프</span><span class="sxs-lookup"><span data-stu-id="cc014-105">Conditional statements and loops in a Configuration</span></span>

<span data-ttu-id="cc014-106">PowerShell 흐름 제어 키워드를 사용하여 더 동적인 [구성](configurations.md)을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-106">You can make your [Configuration](configurations.md) more dynamic by using PowerShell flow-control keywords.</span></span> <span data-ttu-id="cc014-107">이 문서에서는 조건문 및 루프를 사용하여 더 동적인 `Configuration`을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-107">This article shows you how you can use conditional statements and loops to make your `Configuration` more dynamic.</span></span> <span data-ttu-id="cc014-108">조건문 및 루프를 [매개 변수](add-parameters-to-a-configuration.md) 및 [구성 데이터](configData.md)와 결합하면 `Configuration`을 컴파일할 때 유연성을 높이고 제어를 강화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-108">Combining conditional statements and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your `Configuration`.</span></span>

<span data-ttu-id="cc014-109">함수 및 스크립트 블록처럼, `Configuration` 내에서 모든 PowerShell 언어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-109">Just like a function or a script block, you can use any PowerShell language feature within a `Configuration`.</span></span> <span data-ttu-id="cc014-110">사용하는 문은 `Configuration`을 호출하여 `.mof` 파일을 컴파일할 때만 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-110">The statements you use will only be evaluated when you call your `Configuration` to compile a `.mof` file.</span></span> <span data-ttu-id="cc014-111">아래 예제에서는 개념을 설명하는 시나리오를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-111">The examples below show scenarios to demonstrate concepts.</span></span> <span data-ttu-id="cc014-112">조건문 및 루프는 매개 변수 및 구성 데이터에서 더 자주 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-112">Conditional statements and loops are more often used with parameters and configuration Data.</span></span>

<span data-ttu-id="cc014-113">이 간단한 예제에서 **Service** 리소스 블록은 컴파일 시간에 서비스의 현재 상태를 검색하여 현재 상태를 유지 관리하는 `.mof` 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-113">In this  example, the **Service** resource block retrieves the current state of a service at compile time to generate a `.mof` file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="cc014-114">동적 리소스 블록을 사용하면 IntelliSense의 효과를 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-114">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="cc014-115">PowerShell 파서는 `Configuration`이 컴파일될 때까지 지정된 값이 허용 가능한지 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-115">The PowerShell parser cannot determine if the values specified are acceptable until the `Configuration` is compiled.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

<span data-ttu-id="cc014-116">또한 `foreach` 루프를 사용하여 현재 머신에 있는 모든 서비스의 **Service** 리소스 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-116">Additionally, you could create a **Service** resource block for every service on the current machine using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

<span data-ttu-id="cc014-117">`if` 문을 사용하여 온라인 상태인 컴퓨터에 대해서만 `Configuration`을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-117">You could also create a `Configuration` only for machines that are online by using an `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="cc014-118">위 예제의 동적 리소스 블록은 현재 머신을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-118">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="cc014-119">이 경우 현재 머신은 대상 노드가 아니라 `Configuration`을 작성 중인 머신입니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-119">In this instance, that would be the machine you are authoring the `Configuration` on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="cc014-120">요약</span><span class="sxs-lookup"><span data-stu-id="cc014-120">Summary</span></span>

<span data-ttu-id="cc014-121">요약하면, `Configuration` 내에서 모든 PowerShell 언어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-121">In summary, you can use any PowerShell language feature within a `Configuration`.</span></span>

<span data-ttu-id="cc014-122">여기에는 다음과 같은 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-122">This includes things like:</span></span>

- <span data-ttu-id="cc014-123">사용자 지정 개체</span><span class="sxs-lookup"><span data-stu-id="cc014-123">Custom Objects</span></span>
- <span data-ttu-id="cc014-124">해시 테이블</span><span class="sxs-lookup"><span data-stu-id="cc014-124">Hashtables</span></span>
- <span data-ttu-id="cc014-125">문자열 조작</span><span class="sxs-lookup"><span data-stu-id="cc014-125">String manipulation</span></span>
- <span data-ttu-id="cc014-126">원격 통신</span><span class="sxs-lookup"><span data-stu-id="cc014-126">Remoting</span></span>
- <span data-ttu-id="cc014-127">WMI 및 CIM</span><span class="sxs-lookup"><span data-stu-id="cc014-127">WMI and CIM</span></span>
- <span data-ttu-id="cc014-128">ActiveDirectory 개체</span><span class="sxs-lookup"><span data-stu-id="cc014-128">ActiveDirectory objects</span></span>
- <span data-ttu-id="cc014-129">추가...</span><span class="sxs-lookup"><span data-stu-id="cc014-129">and more...</span></span>

<span data-ttu-id="cc014-130">`Configuration`에 정의된 모든 PowerShell 코드는 컴파일 시간에 평가되지만, `Configuration`을 포함하는 스크립트에 코드를 넣을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-130">Any PowerShell code defined in a `Configuration` is evaluated at compile time, but you can also place code in the script containing your `Configuration`.</span></span> <span data-ttu-id="cc014-131">`Configuration` 블록 외부의 코드는 `Configuration`을 가져올 때 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc014-131">Any code outside of the `Configuration` block is executed when you import your `Configuration`.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc014-132">추가 정보</span><span class="sxs-lookup"><span data-stu-id="cc014-132">See also</span></span>

- [<span data-ttu-id="cc014-133">구성에 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="cc014-133">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="cc014-134">구성과 구성 데이터 분리</span><span class="sxs-lookup"><span data-stu-id="cc014-134">Separate Configuration data from Configurations</span></span>](configData.md)

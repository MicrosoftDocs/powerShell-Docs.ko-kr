---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 구성의 조건문 및 루프
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080138"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="c326e-103">구성의 조건문 및 루프</span><span class="sxs-lookup"><span data-stu-id="c326e-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="c326e-104">PowerShell 흐름 제어 키워드를 사용하여 더 동적인 [구성](configurations.md)을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="c326e-105">이 문서에서는 조건문 및 루프를 사용하여 더 동적인 구성을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="c326e-106">조건 및 루프를 [매개 변수](add-parameters-to-a-configuration.md) 및 [구성 데이터](configData.md)와 결합하면 구성을 컴파일할 때 유연성을 높이고 제어를 강화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="c326e-107">함수 및 스크립트 블록처럼, 구성 내에서 모든 PowerShell 언어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="c326e-108">사용하는 문은 구성을 호출하여 ".mof" 파일을 컴파일할 때만 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="c326e-109">아래 예제에서는 개념을 설명하는 간단한 시나리오를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="c326e-110">조건 및 루프는 매개 변수 및 구성 데이터에서 더 자주 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="c326e-111">이 간단한 예제에서 **Service** 리소스 블록은 컴파일 시간에 서비스의 현재 상태를 검색하여 현재 상태를 유지 관리하는 ".mof" 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="c326e-112">동적 리소스 블록을 사용하면 IntelliSense의 효과를 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="c326e-113">PowerShell 파서는 구성이 컴파일될 때까지 지정된 값이 허용 가능한지 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

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

<span data-ttu-id="c326e-114">또한 `foreach` 루프를 사용하여 현재 머신에 있는 모든 서비스의 **Service** 블록 리소스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
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

<span data-ttu-id="c326e-115">간단한 `if` 문을 사용하여 온라인 상태의 머신에 대한 구성만 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> <span data-ttu-id="c326e-116">위 예제의 동적 리소스 블록은 현재 머신을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="c326e-117">이 경우 현재 머신은 대상 노드가 아니라 구성을 작성 중인 머신입니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="c326e-118">요약</span><span class="sxs-lookup"><span data-stu-id="c326e-118">Summary</span></span>

<span data-ttu-id="c326e-119">요약하면, 구성 내에서 모든 PowerShell 언어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="c326e-120">여기에는 다음과 같은 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-120">This includes things like:</span></span>

- <span data-ttu-id="c326e-121">사용자 지정 개체</span><span class="sxs-lookup"><span data-stu-id="c326e-121">Custom Objects</span></span>
- <span data-ttu-id="c326e-122">해시 테이블</span><span class="sxs-lookup"><span data-stu-id="c326e-122">Hashtables</span></span>
- <span data-ttu-id="c326e-123">문자열 조작</span><span class="sxs-lookup"><span data-stu-id="c326e-123">String manipulation</span></span>
- <span data-ttu-id="c326e-124">원격</span><span class="sxs-lookup"><span data-stu-id="c326e-124">Remoting</span></span>
- <span data-ttu-id="c326e-125">WMI 및 CIM</span><span class="sxs-lookup"><span data-stu-id="c326e-125">WMI and CIM</span></span>
- <span data-ttu-id="c326e-126">ActiveDirectory 개체</span><span class="sxs-lookup"><span data-stu-id="c326e-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="c326e-127">추가...</span><span class="sxs-lookup"><span data-stu-id="c326e-127">and more...</span></span>

<span data-ttu-id="c326e-128">구성에 정의된 모든 PowerShell 코드는 컴파일 시간에 평가되지만, 구성을 포함하는 스크립트에 코드를 넣을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="c326e-129">구성 블록 외부의 모든 코드는 구성을 가져올 때 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c326e-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="c326e-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c326e-130">See also</span></span>

- [<span data-ttu-id="c326e-131">구성에 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="c326e-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="c326e-132">구성과 구성 데이터 분리</span><span class="sxs-lookup"><span data-stu-id="c326e-132">Separate Configuration data from Configurations</span></span>](configData.md)

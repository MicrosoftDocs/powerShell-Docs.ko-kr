---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 구성의 조건문 및 루프
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402316"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="4abe5-103">구성의 조건문 및 루프</span><span class="sxs-lookup"><span data-stu-id="4abe5-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="4abe5-104">할 수 있습니다 하 [구성을](configurations.md) PowerShell 흐름 제어 키워드를 사용 하 여 더 동적입니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="4abe5-105">이 문서는 구성을 보다 동적인 있도록 조건문 및 루프를 사용 하는 방법을 보여드리겠습니다를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="4abe5-106">결합 조건부 및 사용 하 여 루프 [매개 변수](add-parameters-to-a-configuration.md) 하 고 [구성 데이터](configData.md) 구성을 컴파일할 때 더 많은 유연성과 제어 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="4abe5-107">함수 또는 스크립트 블록 처럼 구성 내에서 모든 PowerShell 언어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="4abe5-108">"Mof" 파일을 컴파일하는 데 구성을 호출 하는 경우에 사용 하는 문은 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="4abe5-109">아래 예제에서는 개념을 설명 하는 간단한 시나리오를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="4abe5-110">매개 변수 및 구성 데이터를 사용 하 여 더 자주 사용 하 여 루프가 하는 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="4abe5-111">이 간단한 예제는 **서비스** 리소스 블록의 현재 상태를 유지 관리 하는 ".mof" 파일을 생성 하려면 컴파일 시간에 서비스의 현재 상태를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="4abe5-112">동적 리소스 블록을 사용 하 여 Intellisense의 효과 선점 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="4abe5-113">PowerShell 파서를 지정 된 값은 허용 되는 구성이 컴파일될 때까지 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

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

<span data-ttu-id="4abe5-114">또한 만들 수 있습니다는 **서비스** 차단 현재 컴퓨터의 모든 서비스에 대 한 리소스를 사용 하 여를 `foreach` 루프.</span><span class="sxs-lookup"><span data-stu-id="4abe5-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

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

<span data-ttu-id="4abe5-115">Online을 사용 하 여 간단한 컴퓨터용 구성만 만들 수 있습니다 `if` 문입니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

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
> <span data-ttu-id="4abe5-116">위 예 참조는 현재 컴퓨터 동적 리소스 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="4abe5-117">컴퓨터 구성에서 제작 하는 것에이 예에서는 대상 노드가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="4abe5-118">요약</span><span class="sxs-lookup"><span data-stu-id="4abe5-118">Summary</span></span>

<span data-ttu-id="4abe5-119">요약 하자면, 구성 내에서 모든 PowerShell 언어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="4abe5-120">이 등이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-120">This includes things like:</span></span>

- <span data-ttu-id="4abe5-121">사용자 지정 개체</span><span class="sxs-lookup"><span data-stu-id="4abe5-121">Custom Objects</span></span>
- <span data-ttu-id="4abe5-122">해시 테이블</span><span class="sxs-lookup"><span data-stu-id="4abe5-122">Hashtables</span></span>
- <span data-ttu-id="4abe5-123">문자열 조작</span><span class="sxs-lookup"><span data-stu-id="4abe5-123">String manipulation</span></span>
- <span data-ttu-id="4abe5-124">원격</span><span class="sxs-lookup"><span data-stu-id="4abe5-124">Remoting</span></span>
- <span data-ttu-id="4abe5-125">WMI 및 CIM</span><span class="sxs-lookup"><span data-stu-id="4abe5-125">WMI and CIM</span></span>
- <span data-ttu-id="4abe5-126">Active Directory 개체</span><span class="sxs-lookup"><span data-stu-id="4abe5-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="4abe5-127">추가...</span><span class="sxs-lookup"><span data-stu-id="4abe5-127">and more...</span></span>

<span data-ttu-id="4abe5-128">구성에 정의 된 모든 PowerShell 코드를 컴파일 시간에 평가 되지만 구성을 포함 하는 스크립트에서 코드를 배치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="4abe5-129">구성 블록 외부에서 코드 구성을 가져올 때 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4abe5-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="4abe5-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4abe5-130">See also</span></span>

- [<span data-ttu-id="4abe5-131">구성에 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="4abe5-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="4abe5-132">구성과 구성 데이터 분리</span><span class="sxs-lookup"><span data-stu-id="4abe5-132">Separate Configuration data from Configurations</span></span>](configData.md)

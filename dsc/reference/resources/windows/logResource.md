---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 로그 리소스
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679883"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="c169c-103">DSC 로그 리소스</span><span class="sxs-lookup"><span data-stu-id="c169c-103">DSC Log Resource</span></span>

> <span data-ttu-id="c169c-104">‘적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0’</span><span class="sxs-lookup"><span data-stu-id="c169c-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="c169c-105">Windows PowerShell DSC(필요한 상태 구성)의 __Log__ 리소스에서는 메시지를 Microsoft-Windows-필요한 상태 구성/분석 이벤트 로그에 쓰는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c169c-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="c169c-106">기본적으로 DSC에 대한 작업 로그만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c169c-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="c169c-107">분석 로그를 사용할 수 있거나 볼 수 있으려면 먼저 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c169c-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="c169c-108">자세한 내용은 [DSC 이벤트 로그는 어디에 있나요?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c169c-108">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="c169c-109">속성</span><span class="sxs-lookup"><span data-stu-id="c169c-109">Properties</span></span>

| <span data-ttu-id="c169c-110">속성</span><span class="sxs-lookup"><span data-stu-id="c169c-110">Property</span></span> | <span data-ttu-id="c169c-111">설명</span><span class="sxs-lookup"><span data-stu-id="c169c-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="c169c-112">메시지</span><span class="sxs-lookup"><span data-stu-id="c169c-112">Message</span></span>| <span data-ttu-id="c169c-113">Microsoft-Windows-필요한 상태 구성/분석 이벤트 로그에 쓸 메시지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c169c-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="c169c-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c169c-114">DependsOn</span></span> | <span data-ttu-id="c169c-115">이 로그 메시지가 작성되려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c169c-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="c169c-116">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = '[ResourceType]ResourceName'`입니다.</span><span class="sxs-lookup"><span data-stu-id="c169c-116">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="c169c-117">예제</span><span class="sxs-lookup"><span data-stu-id="c169c-117">Example</span></span>

<span data-ttu-id="c169c-118">다음 예제에서는 Microsoft-Windows-필요한 상태 구성/분석 이벤트 로그에 메시지를 포함하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c169c-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="c169c-119">이 리소스를 구성한 상태에서 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)을 실행하는 경우 항상 **$false**를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c169c-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```

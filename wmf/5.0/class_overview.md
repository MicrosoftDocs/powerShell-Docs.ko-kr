---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5919a68c87ae8827a1b97befc653bb74713f33fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085782"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="4a19d-102">PowerShell 클래스를 사용하여 사용자 지정 형식 만들기</span><span class="sxs-lookup"><span data-stu-id="4a19d-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="4a19d-103">다른 개체 지향 프로그래밍 언어와 유사한 의미 체계 및 정식 구문을 사용하여 클래스 및 기타 사용자 정의 형식을 정의하는 PowerShell 언어를 개선했습니다.</span><span class="sxs-lookup"><span data-stu-id="4a19d-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="4a19d-104">목표는 개발자 및 IT 전문가가 보다 광범위한 사용 사례에 PowerShell을 적용하고, PowerShell 아티팩트(예: DSC 리소스)의 개발을 간소화하며, 관리 화면의 적용을 가속화할 수 있도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4a19d-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="4a19d-105">이 릴리스에서 지원되는 시나리오</span><span class="sxs-lookup"><span data-stu-id="4a19d-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="4a19d-106">PowerShell 언어를 사용하여 DSC 리소스 및 관련 형식 정의</span><span class="sxs-lookup"><span data-stu-id="4a19d-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="4a19d-107">클래스, 속성, 메서드 등 친숙한 개체 지향 프로그래밍 구문을 사용하여 PowerShell에서 사용자 지정 형식 정의</span><span class="sxs-lookup"><span data-stu-id="4a19d-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="4a19d-108">PowerShell 및 클래스 기본 DSC 리소스에서 클래스로 상속 지원</span><span class="sxs-lookup"><span data-stu-id="4a19d-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="4a19d-109">PowerShell 언어를 사용하여 형식 디버그</span><span class="sxs-lookup"><span data-stu-id="4a19d-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="4a19d-110">적절한 수준에서 정식 메커니즘을 사용하여 예외 생성 및 처리</span><span class="sxs-lookup"><span data-stu-id="4a19d-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

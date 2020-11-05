---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSCAutomationHostEnabled 레지스트리 키
description: 이 문서에서는 DSCAutomationHostEnabled 레지스트리 키에 설정할 수 있는 값을 정의합니다.
ms.openlocfilehash: 50f752dd882e9b0787ed4a4cbc22731fc1d608f5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656187"
---
# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="3959f-104">DSCAutomationHostEnabled 레지스트리 키</span><span class="sxs-lookup"><span data-stu-id="3959f-104">DSCAutomationHostEnabled registry key</span></span>

> <span data-ttu-id="3959f-105">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="3959f-105">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="3959f-106">DSC에서는 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** 아래의 **DSCAutomationHostEnabled** 레지스트리 키를 사용하여 초기 부팅 시 컴퓨터를 구성할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3959f-106">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span> <span data-ttu-id="3959f-107">**DSCAutomationHostEnabled** 는 다음의 세 가지 모드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3959f-107">**DSCAutomationHostEnabled** supports three modes:</span></span>

| <span data-ttu-id="3959f-108">DSCAutomationHostEnabled 값</span><span class="sxs-lookup"><span data-stu-id="3959f-108">DSCAutomationHostEnabled Value</span></span> |                                              <span data-ttu-id="3959f-109">Description</span><span class="sxs-lookup"><span data-stu-id="3959f-109">Description</span></span>                                              |
| ------------------------------ | ----------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="3959f-110">0</span><span class="sxs-lookup"><span data-stu-id="3959f-110">0</span></span>                              | <span data-ttu-id="3959f-111">부팅 시 컴퓨터를 구성하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3959f-111">Disable configuring the machine at boot-up.</span></span>                                                           |
| <span data-ttu-id="3959f-112">1</span><span class="sxs-lookup"><span data-stu-id="3959f-112">1</span></span>                              | <span data-ttu-id="3959f-113">부팅 시 컴퓨터를 구성하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3959f-113">Enable configuring the machine at boot-up.</span></span>                                                            |
| <span data-ttu-id="3959f-114">2</span><span class="sxs-lookup"><span data-stu-id="3959f-114">2</span></span>                              | <span data-ttu-id="3959f-115">DSC가 보류 중 또는 현재 상태인 경우에만 컴퓨터를 구성하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3959f-115">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="3959f-116">이것은 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="3959f-116">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="3959f-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3959f-117">See Also</span></span>

<span data-ttu-id="3959f-118">이 기능을 사용하여 초기 부팅 시 구성을 실행하는 방법에 대한 예는 [초기 부팅 시 DSC를 사용하여 가상 컴퓨터 구성](bootstrapDsc.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3959f-118">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>

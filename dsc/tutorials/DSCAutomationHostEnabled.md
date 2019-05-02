---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSCAutomationHostEnabled 레지스트리 키
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076493"
---
><span data-ttu-id="55b52-103">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="55b52-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="55b52-104">DSCAutomationHostEnabled 레지스트리 키</span><span class="sxs-lookup"><span data-stu-id="55b52-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="55b52-105">DSC에서는 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** 아래의 **DSCAutomationHostEnabled** 레지스트리 키를 사용하여 초기 부팅 시 컴퓨터를 구성할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b52-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="55b52-106">**DSCAutomationHostEnabled**는 다음의 세 가지 모드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="55b52-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="55b52-107">DSCAutomationHostEnabled 값</span><span class="sxs-lookup"><span data-stu-id="55b52-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="55b52-108">설명</span><span class="sxs-lookup"><span data-stu-id="55b52-108">Description</span></span>   |
|---|---|
<span data-ttu-id="55b52-109">0</span><span class="sxs-lookup"><span data-stu-id="55b52-109">0</span></span> | <span data-ttu-id="55b52-110">부팅 시 컴퓨터를 구성하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="55b52-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="55b52-111">1</span><span class="sxs-lookup"><span data-stu-id="55b52-111">1</span></span> | <span data-ttu-id="55b52-112">부팅 시 컴퓨터를 구성하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="55b52-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="55b52-113">2</span><span class="sxs-lookup"><span data-stu-id="55b52-113">2</span></span> | <span data-ttu-id="55b52-114">DSC가 보류 중 또는 현재 상태인 경우에만 컴퓨터를 구성하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="55b52-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="55b52-115">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="55b52-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="55b52-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55b52-116">See Also</span></span>

<span data-ttu-id="55b52-117">이 기능을 사용하여 초기 부팅 시 구성을 실행하는 방법에 대한 예는 [초기 부팅 시 DSC를 사용하여 가상 컴퓨터 구성](bootstrapDsc.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55b52-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>

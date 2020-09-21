---
ms.date: 07/14/2020
keywords: dsc,powershell,configuration,setup
title: ApplyConfiguration 메서드
ms.openlocfilehash: bec74ccd6f75448484adfd26bf8a4af4e224eb3f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463842"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="45f32-103">ApplyConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="45f32-103">ApplyConfiguration method</span></span>

<span data-ttu-id="45f32-104">구성 에이전트를 사용해 보류 중인 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="45f32-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="45f32-105">보류 중인 구성이 없으면 이 메서드는 현재 구성을 다시 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="45f32-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="45f32-106">구문</span><span class="sxs-lookup"><span data-stu-id="45f32-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="45f32-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="45f32-107">Parameters</span></span>

### <a name="force"></a><span data-ttu-id="45f32-108">force</span><span class="sxs-lookup"><span data-stu-id="45f32-108">force</span></span>

<span data-ttu-id="45f32-109">**true**인 경우 현재 구성이 다시 적용됩니다. 보류 중인 구성이 있더라도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="45f32-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="45f32-110">반환 값</span><span class="sxs-lookup"><span data-stu-id="45f32-110">Return value</span></span>

<span data-ttu-id="45f32-111">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="45f32-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="45f32-112">설명</span><span class="sxs-lookup"><span data-stu-id="45f32-112">Remarks</span></span>

<span data-ttu-id="45f32-113">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="45f32-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="45f32-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="45f32-114">Requirements</span></span>

<span data-ttu-id="45f32-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="45f32-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="45f32-116">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="45f32-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="45f32-117">참조</span><span class="sxs-lookup"><span data-stu-id="45f32-117">See also</span></span>

[<span data-ttu-id="45f32-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="45f32-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

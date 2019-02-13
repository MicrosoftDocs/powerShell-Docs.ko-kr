---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 ApplyConfiguration 메서드
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679694"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ba86d-103">MSFT_DSCLocalConfigurationManager 클래스의 ApplyConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="ba86d-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ba86d-104">구성 에이전트를 사용해 보류 중인 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ba86d-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="ba86d-105">보류 중인 구성이 없으면 이 메서드는 현재 구성을 다시 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ba86d-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="ba86d-106">구문</span><span class="sxs-lookup"><span data-stu-id="ba86d-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="ba86d-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ba86d-107">Parameters</span></span>

<span data-ttu-id="ba86d-108">*force* \[in\] **true**인 경우 현재 구성이 다시 적용됩니다. 보류 중인 구성이 있더라도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="ba86d-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="ba86d-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="ba86d-109">Return value</span></span>

<span data-ttu-id="ba86d-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ba86d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba86d-111">설명</span><span class="sxs-lookup"><span data-stu-id="ba86d-111">Remarks</span></span>

<span data-ttu-id="ba86d-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="ba86d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba86d-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ba86d-113">Requirements</span></span>

<span data-ttu-id="ba86d-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ba86d-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ba86d-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba86d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ba86d-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba86d-116">See also</span></span>

[<span data-ttu-id="ba86d-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ba86d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: StopConfiguration 메서드
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953360"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="b9501-103">StopConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="b9501-103">StopConfiguration method</span></span>

<span data-ttu-id="b9501-104">진행 중인 구성 변경을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b9501-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9501-105">구문</span><span class="sxs-lookup"><span data-stu-id="b9501-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="b9501-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b9501-106">Parameters</span></span>

<span data-ttu-id="b9501-107">*force* \[in\] **true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b9501-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="b9501-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="b9501-108">Return value</span></span>

<span data-ttu-id="b9501-109">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b9501-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9501-110">설명</span><span class="sxs-lookup"><span data-stu-id="b9501-110">Remarks</span></span>

<span data-ttu-id="b9501-111">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="b9501-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b9501-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b9501-112">Requirements</span></span>

<span data-ttu-id="b9501-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b9501-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b9501-114">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b9501-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b9501-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9501-115">See also</span></span>

[<span data-ttu-id="b9501-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b9501-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

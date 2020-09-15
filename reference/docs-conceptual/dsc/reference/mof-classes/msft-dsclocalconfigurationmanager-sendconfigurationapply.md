---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApply 메서드
ms.openlocfilehash: 9b684790e5a7d6c7bdf074caca6040e13807f1ca
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464318"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="0e457-103">SendConfigurationApply 메서드</span><span class="sxs-lookup"><span data-stu-id="0e457-103">SendConfigurationApply method</span></span>

<span data-ttu-id="0e457-104">구성 문서를 관리 노드로 보내고, 구성 에이전트를 사용해 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="0e457-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e457-105">구문</span><span class="sxs-lookup"><span data-stu-id="0e457-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="0e457-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0e457-106">Parameters</span></span>

<span data-ttu-id="0e457-107">**ConfigurationData** \[in\] 구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="0e457-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="0e457-108">**force** \[in\] **true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="0e457-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="0e457-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="0e457-109">Return value</span></span>

<span data-ttu-id="0e457-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0e457-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e457-111">설명</span><span class="sxs-lookup"><span data-stu-id="0e457-111">Remarks</span></span>

<span data-ttu-id="0e457-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="0e457-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e457-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="0e457-113">Requirements</span></span>

<span data-ttu-id="0e457-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0e457-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0e457-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0e457-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0e457-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e457-116">See also</span></span>

[<span data-ttu-id="0e457-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0e457-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

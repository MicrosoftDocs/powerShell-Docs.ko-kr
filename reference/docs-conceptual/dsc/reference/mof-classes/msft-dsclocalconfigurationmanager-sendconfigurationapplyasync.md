---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApplyAsync 메서드
ms.openlocfilehash: 4cfac5edb5fed94ee69deb98d7aa6be56b51c5b3
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463740"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="95cc6-103">SendConfigurationApplyAsync 메서드</span><span class="sxs-lookup"><span data-stu-id="95cc6-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="95cc6-104">구성 문서를 비동기적으로 관리 노드로 보내고, 구성 에이전트를 사용해 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="95cc6-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="95cc6-105">구문</span><span class="sxs-lookup"><span data-stu-id="95cc6-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="95cc6-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="95cc6-106">Parameters</span></span>

<span data-ttu-id="95cc6-107">**ConfigurationData** \[in\] 구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="95cc6-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="95cc6-108">**force** \[in\] **true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="95cc6-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="95cc6-109">**jobId** \[in\] 구성을 보낼 작업의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="95cc6-109">**jobId** \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="95cc6-110">반환 값</span><span class="sxs-lookup"><span data-stu-id="95cc6-110">Return value</span></span>

<span data-ttu-id="95cc6-111">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95cc6-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="95cc6-112">설명</span><span class="sxs-lookup"><span data-stu-id="95cc6-112">Remarks</span></span>

<span data-ttu-id="95cc6-113">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="95cc6-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="95cc6-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="95cc6-114">Requirements</span></span>

<span data-ttu-id="95cc6-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="95cc6-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="95cc6-116">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="95cc6-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="95cc6-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95cc6-117">See also</span></span>

[<span data-ttu-id="95cc6-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="95cc6-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

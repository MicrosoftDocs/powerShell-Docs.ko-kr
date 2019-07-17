---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApplyAsync 메서드
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734308"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="e869d-103">SendConfigurationApplyAsync 메서드</span><span class="sxs-lookup"><span data-stu-id="e869d-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="e869d-104">구성 문서를 비동기적으로 관리 노드로 보내고, 구성 에이전트를 사용해 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="e869d-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="e869d-105">구문</span><span class="sxs-lookup"><span data-stu-id="e869d-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="e869d-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e869d-106">Parameters</span></span>

<span data-ttu-id="e869d-107">*ConfigurationData* \[in\] 구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="e869d-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="e869d-108">*force* \[in\] **true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e869d-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="e869d-109">*jobId* \[in\] 구성을 보낼 작업의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="e869d-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="e869d-110">반환 값</span><span class="sxs-lookup"><span data-stu-id="e869d-110">Return value</span></span>

<span data-ttu-id="e869d-111">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e869d-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e869d-112">설명</span><span class="sxs-lookup"><span data-stu-id="e869d-112">Remarks</span></span>

<span data-ttu-id="e869d-113">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="e869d-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e869d-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e869d-114">Requirements</span></span>

<span data-ttu-id="e869d-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e869d-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e869d-116">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e869d-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e869d-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e869d-117">See also</span></span>

[<span data-ttu-id="e869d-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e869d-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

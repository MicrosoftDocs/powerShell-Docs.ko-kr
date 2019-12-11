---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApply 메서드
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954890"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="d5a11-103">SendConfigurationApply 메서드</span><span class="sxs-lookup"><span data-stu-id="d5a11-103">SendConfigurationApply method</span></span>

<span data-ttu-id="d5a11-104">구성 문서를 관리 노드로 보내고, 구성 에이전트를 사용해 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a11-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="d5a11-105">구문</span><span class="sxs-lookup"><span data-stu-id="d5a11-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="d5a11-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d5a11-106">Parameters</span></span>

<span data-ttu-id="d5a11-107">*ConfigurationData* \[in\] 구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="d5a11-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="d5a11-108">*force* \[in\] **true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a11-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d5a11-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="d5a11-109">Return value</span></span>

<span data-ttu-id="d5a11-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a11-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d5a11-111">설명</span><span class="sxs-lookup"><span data-stu-id="d5a11-111">Remarks</span></span>

<span data-ttu-id="d5a11-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="d5a11-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d5a11-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d5a11-113">Requirements</span></span>

<span data-ttu-id="d5a11-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d5a11-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d5a11-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d5a11-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d5a11-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d5a11-116">See also</span></span>

[<span data-ttu-id="d5a11-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d5a11-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

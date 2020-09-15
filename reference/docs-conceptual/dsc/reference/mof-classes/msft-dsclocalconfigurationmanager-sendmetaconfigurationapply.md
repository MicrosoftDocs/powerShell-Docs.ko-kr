---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: SendMetaConfigurationApply 메서드
ms.openlocfilehash: 896afe2f3370e108b48583aafb33ee7b0eb1301b
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463723"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="60ff0-103">SendMetaConfigurationApply 메서드</span><span class="sxs-lookup"><span data-stu-id="60ff0-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="60ff0-104">구성 에이전트를 제어하는 데 사용되는 로컬 구성 관리자 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="60ff0-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="60ff0-105">구문</span><span class="sxs-lookup"><span data-stu-id="60ff0-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="60ff0-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="60ff0-106">Parameters</span></span>

<span data-ttu-id="60ff0-107">**ConfigurationData** \[in\] 구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="60ff0-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="60ff0-108">**force** \[in\] **true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="60ff0-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="60ff0-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="60ff0-109">Return value</span></span>

<span data-ttu-id="60ff0-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="60ff0-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="60ff0-111">설명</span><span class="sxs-lookup"><span data-stu-id="60ff0-111">Remarks</span></span>

<span data-ttu-id="60ff0-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="60ff0-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="60ff0-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="60ff0-113">Requirements</span></span>

<span data-ttu-id="60ff0-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="60ff0-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="60ff0-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="60ff0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="60ff0-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="60ff0-116">See also</span></span>

[<span data-ttu-id="60ff0-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="60ff0-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

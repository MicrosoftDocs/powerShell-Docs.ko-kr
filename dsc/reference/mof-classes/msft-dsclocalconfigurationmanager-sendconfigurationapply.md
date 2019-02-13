---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 SendConfigurationApply 메서드
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680539"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bdd1b-103">MSFT_DSCLocalConfigurationManager 클래스의 SendConfigurationApply 메서드</span><span class="sxs-lookup"><span data-stu-id="bdd1b-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bdd1b-104">구성 문서를 관리 노드로 보내고, 구성 에이전트를 사용해 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="bdd1b-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="bdd1b-105">구문</span><span class="sxs-lookup"><span data-stu-id="bdd1b-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="bdd1b-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="bdd1b-106">Parameters</span></span>

<span data-ttu-id="bdd1b-107">*ConfigurationData* \[in\] 구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="bdd1b-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="bdd1b-108">*force* \[in\] **true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="bdd1b-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="bdd1b-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="bdd1b-109">Return value</span></span>

<span data-ttu-id="bdd1b-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bdd1b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bdd1b-111">설명</span><span class="sxs-lookup"><span data-stu-id="bdd1b-111">Remarks</span></span>

<span data-ttu-id="bdd1b-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="bdd1b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bdd1b-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="bdd1b-113">Requirements</span></span>

<span data-ttu-id="bdd1b-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bdd1b-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="bdd1b-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bdd1b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="bdd1b-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bdd1b-116">See also</span></span>

[<span data-ttu-id="bdd1b-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bdd1b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
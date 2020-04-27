---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfiguration 메서드
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953390"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="fb30a-103">SendConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="fb30a-103">SendConfiguration method</span></span>

<span data-ttu-id="fb30a-104">구성 문서를 관리 노드로 보내고 보류 중인 변경으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="fb30a-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb30a-105">구문</span><span class="sxs-lookup"><span data-stu-id="fb30a-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="fb30a-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="fb30a-106">Parameters</span></span>

<span data-ttu-id="fb30a-107">*ConfigurationData* \[in\] 구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="fb30a-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="fb30a-108">*force* \[in\] **true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="fb30a-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="fb30a-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="fb30a-109">Return value</span></span>

<span data-ttu-id="fb30a-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fb30a-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fb30a-111">설명</span><span class="sxs-lookup"><span data-stu-id="fb30a-111">Remarks</span></span>

<span data-ttu-id="fb30a-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="fb30a-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fb30a-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="fb30a-113">Requirements</span></span>

<span data-ttu-id="fb30a-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fb30a-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fb30a-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fb30a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fb30a-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb30a-116">See also</span></span>

[<span data-ttu-id="fb30a-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fb30a-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

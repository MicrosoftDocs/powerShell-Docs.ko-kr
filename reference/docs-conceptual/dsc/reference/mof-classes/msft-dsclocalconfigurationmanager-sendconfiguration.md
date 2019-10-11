---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfiguration 메서드
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953390"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="63cfc-103">SendConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="63cfc-103">SendConfiguration method</span></span>

<span data-ttu-id="63cfc-104">구성 문서를 관리 노드로 보내고 보류 중인 변경으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="63cfc-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="63cfc-105">구문</span><span class="sxs-lookup"><span data-stu-id="63cfc-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="63cfc-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="63cfc-106">Parameters</span></span>

<span data-ttu-id="63cfc-107">*ConfigurationData* \[in\] 구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="63cfc-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="63cfc-108">*force* \[in\] **true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="63cfc-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="63cfc-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="63cfc-109">Return value</span></span>

<span data-ttu-id="63cfc-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="63cfc-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="63cfc-111">설명</span><span class="sxs-lookup"><span data-stu-id="63cfc-111">Remarks</span></span>

<span data-ttu-id="63cfc-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="63cfc-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="63cfc-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="63cfc-113">Requirements</span></span>

<span data-ttu-id="63cfc-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="63cfc-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="63cfc-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="63cfc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="63cfc-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63cfc-116">See also</span></span>

[<span data-ttu-id="63cfc-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="63cfc-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

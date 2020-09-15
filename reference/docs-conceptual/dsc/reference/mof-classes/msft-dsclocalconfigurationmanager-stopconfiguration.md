---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: StopConfiguration 메서드
ms.openlocfilehash: 76e50c98b09dca86983320918c6899082580672a
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463706"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="52107-103">StopConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="52107-103">StopConfiguration method</span></span>

<span data-ttu-id="52107-104">진행 중인 구성 변경을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="52107-105">구문</span><span class="sxs-lookup"><span data-stu-id="52107-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="52107-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="52107-106">Parameters</span></span>

<span data-ttu-id="52107-107">**force** \[in\] **true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-107">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="52107-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="52107-108">Return value</span></span>

<span data-ttu-id="52107-109">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="52107-110">설명</span><span class="sxs-lookup"><span data-stu-id="52107-110">Remarks</span></span>

<span data-ttu-id="52107-111">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="52107-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="52107-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="52107-112">Requirements</span></span>

<span data-ttu-id="52107-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="52107-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="52107-114">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="52107-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="52107-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52107-115">See also</span></span>

[<span data-ttu-id="52107-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="52107-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

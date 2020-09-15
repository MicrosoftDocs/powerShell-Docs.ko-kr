---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: RollBack 메서드
ms.openlocfilehash: 301b8926d2ebf1ebe524f52a67928d34e26d860e
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464335"
---
# <a name="rollback-method"></a><span data-ttu-id="b2158-103">RollBack 메서드</span><span class="sxs-lookup"><span data-stu-id="b2158-103">RollBack method</span></span>

<span data-ttu-id="b2158-104">이전 버전으로 구성을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="b2158-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2158-105">구문</span><span class="sxs-lookup"><span data-stu-id="b2158-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="b2158-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b2158-106">Parameters</span></span>

<span data-ttu-id="b2158-107">**configurationNumber** \[in\] 요청된 구성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2158-107">**configurationNumber** \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="b2158-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="b2158-108">Return value</span></span>

<span data-ttu-id="b2158-109">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b2158-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2158-110">설명</span><span class="sxs-lookup"><span data-stu-id="b2158-110">Remarks</span></span>

<span data-ttu-id="b2158-111">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="b2158-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b2158-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b2158-112">Requirements</span></span>

<span data-ttu-id="b2158-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b2158-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b2158-114">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2158-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b2158-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b2158-115">See also</span></span>

[<span data-ttu-id="b2158-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b2158-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

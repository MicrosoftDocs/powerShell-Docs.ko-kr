---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RollBack 메서드
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954940"
---
# <a name="rollback-method"></a><span data-ttu-id="3f631-103">RollBack 메서드</span><span class="sxs-lookup"><span data-stu-id="3f631-103">RollBack method</span></span>

<span data-ttu-id="3f631-104">이전 버전으로 구성을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="3f631-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="3f631-105">구문</span><span class="sxs-lookup"><span data-stu-id="3f631-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="3f631-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="3f631-106">Parameters</span></span>

<span data-ttu-id="3f631-107">*configurationNumber* \[in\] 요청된 구성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3f631-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="3f631-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="3f631-108">Return value</span></span>

<span data-ttu-id="3f631-109">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3f631-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3f631-110">설명</span><span class="sxs-lookup"><span data-stu-id="3f631-110">Remarks</span></span>

<span data-ttu-id="3f631-111">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="3f631-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3f631-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="3f631-112">Requirements</span></span>

<span data-ttu-id="3f631-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3f631-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3f631-114">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3f631-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3f631-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3f631-115">See also</span></span>

[<span data-ttu-id="3f631-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3f631-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

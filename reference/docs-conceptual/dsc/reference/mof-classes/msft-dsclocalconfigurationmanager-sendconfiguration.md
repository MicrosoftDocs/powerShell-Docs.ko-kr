---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfiguration 메서드
description: SendConfiguration 메서드
ms.openlocfilehash: 3939a76ab6672b49559847b0ef1408f1c7be6d0c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650554"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="e7944-103">SendConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="e7944-103">SendConfiguration method</span></span>

<span data-ttu-id="e7944-104">구성 문서를 관리 노드로 보내고 보류 중인 변경으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e7944-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="e7944-105">구문</span><span class="sxs-lookup"><span data-stu-id="e7944-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="e7944-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e7944-106">Parameters</span></span>

<span data-ttu-id="e7944-107">**ConfigurationData** \[in\] 구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="e7944-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="e7944-108">**force** \[in\] **true** 이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e7944-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e7944-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="e7944-109">Return value</span></span>

<span data-ttu-id="e7944-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e7944-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7944-111">설명</span><span class="sxs-lookup"><span data-stu-id="e7944-111">Remarks</span></span>

<span data-ttu-id="e7944-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="e7944-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7944-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e7944-113">Requirements</span></span>

<span data-ttu-id="e7944-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e7944-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e7944-115">**네임스페이스** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e7944-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e7944-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7944-116">See also</span></span>

[<span data-ttu-id="e7944-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e7944-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

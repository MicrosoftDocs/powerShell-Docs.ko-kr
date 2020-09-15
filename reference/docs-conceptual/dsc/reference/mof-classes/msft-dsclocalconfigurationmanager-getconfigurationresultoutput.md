---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: GetConfigurationResultOutput 메서드
ms.openlocfilehash: 9c81082c28b2ffcc329264d29784782deaa9779d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464080"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="b0696-103">GetConfigurationResultOutput 메서드</span><span class="sxs-lookup"><span data-stu-id="b0696-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="b0696-104">특정 작업에 연결된 구성 에이전트 출력을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b0696-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0696-105">구문</span><span class="sxs-lookup"><span data-stu-id="b0696-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="b0696-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b0696-106">Parameters</span></span>

<span data-ttu-id="b0696-107">**jobId** \[in\] 출력 데이터를 가져올 작업의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="b0696-107">**jobId** \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="b0696-108">**resumeOutputBookmark** \[in\] 출력이 이전 책갈피의 연속이어야 함을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0696-108">**resumeOutputBookmark** \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="b0696-109">**output** \[out\] 지정된 작업의 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="b0696-109">**output** \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="b0696-110">반환 값</span><span class="sxs-lookup"><span data-stu-id="b0696-110">Return value</span></span>

<span data-ttu-id="b0696-111">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b0696-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0696-112">설명</span><span class="sxs-lookup"><span data-stu-id="b0696-112">Remarks</span></span>

<span data-ttu-id="b0696-113">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="b0696-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0696-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b0696-114">Requirements</span></span>

<span data-ttu-id="b0696-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b0696-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b0696-116">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b0696-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b0696-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b0696-117">See also</span></span>

[<span data-ttu-id="b0696-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b0696-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationResultOutput 메서드
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047578"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5d765-103">MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationResultOutput 메서드</span><span class="sxs-lookup"><span data-stu-id="5d765-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5d765-104">특정 작업에 연결된 구성 에이전트 출력을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="5d765-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d765-105">구문</span><span class="sxs-lookup"><span data-stu-id="5d765-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="5d765-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="5d765-106">Parameters</span></span>

<span data-ttu-id="5d765-107">*jobId* \[in\] 출력 데이터를 가져올 작업의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="5d765-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="5d765-108">*resumeOutputBookmark* \[in\] 출력이 이전 책갈피의 연속이어야 함을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5d765-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="5d765-109">*output* \[out\] 지정된 작업의 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="5d765-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d765-110">반환 값</span><span class="sxs-lookup"><span data-stu-id="5d765-110">Return value</span></span>

<span data-ttu-id="5d765-111">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5d765-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d765-112">설명</span><span class="sxs-lookup"><span data-stu-id="5d765-112">Remarks</span></span>

<span data-ttu-id="5d765-113">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="5d765-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d765-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="5d765-114">Requirements</span></span>

<span data-ttu-id="5d765-115">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5d765-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5d765-116">{0} 네임스페이스 Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5d765-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5d765-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d765-117">See also</span></span>

[<span data-ttu-id="5d765-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5d765-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
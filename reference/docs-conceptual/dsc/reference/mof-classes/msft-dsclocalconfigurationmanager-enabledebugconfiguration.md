---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: EnableDebugConfiguration 메서드
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953440"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="64a7a-103">EnableDebugConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="64a7a-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="64a7a-104">DSC 리소스 디버깅을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="64a7a-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="64a7a-105">구문</span><span class="sxs-lookup"><span data-stu-id="64a7a-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="64a7a-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="64a7a-106">Parameters</span></span>

<span data-ttu-id="64a7a-107">*BreakAll* \[in\] 리소스 스크립트의 모든 줄에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="64a7a-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="64a7a-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="64a7a-108">Return value</span></span>

<span data-ttu-id="64a7a-109">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="64a7a-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="64a7a-110">설명</span><span class="sxs-lookup"><span data-stu-id="64a7a-110">Remarks</span></span>

<span data-ttu-id="64a7a-111">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="64a7a-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="64a7a-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="64a7a-112">Requirements</span></span>

<span data-ttu-id="64a7a-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="64a7a-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="64a7a-114">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="64a7a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="64a7a-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64a7a-115">See also</span></span>

[<span data-ttu-id="64a7a-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="64a7a-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

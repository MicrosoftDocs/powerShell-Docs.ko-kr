---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: EnableDebugConfiguration 메서드
ms.openlocfilehash: be75b1012f49db79eb75a68c6912ffd5772bf16f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464097"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="6a53f-103">EnableDebugConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="6a53f-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="6a53f-104">DSC 리소스 디버깅을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6a53f-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="6a53f-105">구문</span><span class="sxs-lookup"><span data-stu-id="6a53f-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="6a53f-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="6a53f-106">Parameters</span></span>

<span data-ttu-id="6a53f-107">**BreakAll** \[in\] 리소스 스크립트의 모든 줄에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6a53f-107">**BreakAll** \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="6a53f-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="6a53f-108">Return value</span></span>

<span data-ttu-id="6a53f-109">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6a53f-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a53f-110">설명</span><span class="sxs-lookup"><span data-stu-id="6a53f-110">Remarks</span></span>

<span data-ttu-id="6a53f-111">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="6a53f-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6a53f-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="6a53f-112">Requirements</span></span>

<span data-ttu-id="6a53f-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6a53f-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="6a53f-114">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a53f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="6a53f-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a53f-115">See also</span></span>

[<span data-ttu-id="6a53f-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6a53f-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

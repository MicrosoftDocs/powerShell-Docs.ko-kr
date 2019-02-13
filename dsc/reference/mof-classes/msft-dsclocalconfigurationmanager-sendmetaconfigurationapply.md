---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 SendMetaConfigurationApply 메서드
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682443"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2ff38-103">MSFT_DSCLocalConfigurationManager 클래스의 SendMetaConfigurationApply 메서드</span><span class="sxs-lookup"><span data-stu-id="2ff38-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2ff38-104">구성 에이전트를 제어하는 데 사용되는 로컬 구성 관리자 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2ff38-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="2ff38-105">구문</span><span class="sxs-lookup"><span data-stu-id="2ff38-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="2ff38-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2ff38-106">Parameters</span></span>

<span data-ttu-id="2ff38-107">*ConfigurationData* \[in\] 구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="2ff38-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="2ff38-108">*force* \[in\] **true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="2ff38-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="2ff38-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="2ff38-109">Return value</span></span>

<span data-ttu-id="2ff38-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2ff38-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ff38-111">설명</span><span class="sxs-lookup"><span data-stu-id="2ff38-111">Remarks</span></span>

<span data-ttu-id="2ff38-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="2ff38-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ff38-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="2ff38-113">Requirements</span></span>

<span data-ttu-id="2ff38-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2ff38-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2ff38-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2ff38-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2ff38-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2ff38-116">See also</span></span>

[<span data-ttu-id="2ff38-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2ff38-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
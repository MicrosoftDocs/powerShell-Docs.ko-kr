---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 ApplyConfiguration 메서드
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047510"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8a04c-103">MSFT_DSCLocalConfigurationManager 클래스의 ApplyConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="8a04c-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8a04c-104">구성 에이전트를 사용해 보류 중인 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a04c-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="8a04c-105">보류 중인 구성이 없으면 이 메서드는 현재 구성을 다시 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a04c-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a04c-106">구문</span><span class="sxs-lookup"><span data-stu-id="8a04c-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="8a04c-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a04c-107">Parameters</span></span>

<span data-ttu-id="8a04c-108">*force* \[in\] **true**인 경우 현재 구성이 다시 적용됩니다. 보류 중인 구성이 있더라도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="8a04c-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="8a04c-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a04c-109">Return value</span></span>

<span data-ttu-id="8a04c-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8a04c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a04c-111">설명</span><span class="sxs-lookup"><span data-stu-id="8a04c-111">Remarks</span></span>

<span data-ttu-id="8a04c-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="8a04c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8a04c-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="8a04c-113">Requirements</span></span>

<span data-ttu-id="8a04c-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8a04c-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8a04c-115">{0} 네임스페이스 Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8a04c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8a04c-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8a04c-116">See also</span></span>

[<span data-ttu-id="8a04c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8a04c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
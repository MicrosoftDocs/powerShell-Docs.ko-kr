---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: GetConfiguration 메서드
ms.openlocfilehash: 989aeef4cd9aa5d55741b48c8565c657c4b6512c
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463825"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="adef4-103">GetConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="adef4-103">GetConfiguration method</span></span>

<span data-ttu-id="adef4-104">구성 문서를 관리 노드로 보내고, 구성 에이전트의 **Get** 메서드를 사용해 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="adef4-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="adef4-105">구문</span><span class="sxs-lookup"><span data-stu-id="adef4-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="adef4-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="adef4-106">Parameters</span></span>

<span data-ttu-id="adef4-107">**configurationData** \[in\] 보낼 구성 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="adef4-107">**configurationData** \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="adef4-108">**configurations** \[out\] 반환 시, 구성의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adef4-108">**configurations** \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="adef4-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="adef4-109">Return value</span></span>

<span data-ttu-id="adef4-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="adef4-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="adef4-111">설명</span><span class="sxs-lookup"><span data-stu-id="adef4-111">Remarks</span></span>

<span data-ttu-id="adef4-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="adef4-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="adef4-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="adef4-113">Requirements</span></span>

<span data-ttu-id="adef4-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="adef4-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="adef4-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="adef4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="adef4-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="adef4-116">See also</span></span>

[<span data-ttu-id="adef4-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="adef4-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

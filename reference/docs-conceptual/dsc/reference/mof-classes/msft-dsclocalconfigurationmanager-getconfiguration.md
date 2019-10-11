---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetConfiguration 메서드
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955050"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="1b9e9-103">GetConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="1b9e9-103">GetConfiguration method</span></span>

<span data-ttu-id="1b9e9-104">구성 문서를 관리 노드로 보내고, 구성 에이전트의 **Get** 메서드를 사용해 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9e9-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b9e9-105">구문</span><span class="sxs-lookup"><span data-stu-id="1b9e9-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="1b9e9-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1b9e9-106">Parameters</span></span>

<span data-ttu-id="1b9e9-107">*configurationData* \[in\] 보낼 구성 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9e9-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="1b9e9-108">*configurations* \[out\] 반환 시, 구성의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b9e9-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="1b9e9-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="1b9e9-109">Return value</span></span>

<span data-ttu-id="1b9e9-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9e9-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b9e9-111">설명</span><span class="sxs-lookup"><span data-stu-id="1b9e9-111">Remarks</span></span>

<span data-ttu-id="1b9e9-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="1b9e9-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b9e9-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1b9e9-113">Requirements</span></span>

<span data-ttu-id="1b9e9-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1b9e9-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="1b9e9-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1b9e9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="1b9e9-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1b9e9-116">See also</span></span>

[<span data-ttu-id="1b9e9-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1b9e9-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: TestConfiguration 메서드
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954870"
---
# <a name="testconfiguration-method"></a><span data-ttu-id="c1698-103">TestConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="c1698-103">TestConfiguration method</span></span>

<span data-ttu-id="c1698-104">구성 문서를 관리 노드로 보내고, 문서에 대해 현재 구성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c1698-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="c1698-105">구문</span><span class="sxs-lookup"><span data-stu-id="c1698-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="c1698-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c1698-106">Parameters</span></span>

<span data-ttu-id="c1698-107">*configurationData* \[in\] 구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="c1698-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="c1698-108">*InDesiredState* \[out\] 반환 시, 관리 노드가 구성 문서에서 지정한 상태인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1698-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="c1698-109">*ResourcesInDesiredState* \[out\] 반환 시, 원하는 상태인 리소스를 지정하는 **MSFT_ResourceInDesiredState** 클래스의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1698-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="c1698-110">*ResourcesNotInDesiredState* \[out\] 반환 시, 원하는 상태가 아닌 리소스를 지정하는 **MSFT_ResourceNotInDesiredState** 클래스의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1698-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="c1698-111">반환 값</span><span class="sxs-lookup"><span data-stu-id="c1698-111">Return value</span></span>

<span data-ttu-id="c1698-112">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c1698-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1698-113">설명</span><span class="sxs-lookup"><span data-stu-id="c1698-113">Remarks</span></span>

<span data-ttu-id="c1698-114">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="c1698-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c1698-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c1698-115">Requirements</span></span>

<span data-ttu-id="c1698-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c1698-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c1698-117">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c1698-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c1698-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1698-118">See also</span></span>

[<span data-ttu-id="c1698-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c1698-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

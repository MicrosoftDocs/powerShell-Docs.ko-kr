---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ResourceGet 메서드
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955000"
---
# <a name="resourceget-method"></a><span data-ttu-id="1bd03-103">ResourceGet 메서드</span><span class="sxs-lookup"><span data-stu-id="1bd03-103">ResourceGet method</span></span>

<span data-ttu-id="1bd03-104">DSC 리소스의 **Get** 메서드를 직접 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd03-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="1bd03-105">구문</span><span class="sxs-lookup"><span data-stu-id="1bd03-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="1bd03-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1bd03-106">Parameters</span></span>

<span data-ttu-id="1bd03-107">*ResourceType* \[in\] 호출할 리소스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1bd03-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="1bd03-108">*ModuleName* \[in\] 호출할 리소스를 포함하는 모듈의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1bd03-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="1bd03-109">*resourceProperty* \[in\] 해시 테이블의 리소스 속성 이름과 해당 값을 각각 키와 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd03-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="1bd03-110">[Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet을 사용하여 리소스 속성 및 해당 종류를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd03-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="1bd03-111">*configurations* \[out\] 반환 시, 구성의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bd03-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="1bd03-112">반환 값</span><span class="sxs-lookup"><span data-stu-id="1bd03-112">Return value</span></span>

<span data-ttu-id="1bd03-113">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd03-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1bd03-114">설명</span><span class="sxs-lookup"><span data-stu-id="1bd03-114">Remarks</span></span>

<span data-ttu-id="1bd03-115">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="1bd03-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1bd03-116">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1bd03-116">Requirements</span></span>

<span data-ttu-id="1bd03-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1bd03-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="1bd03-118">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1bd03-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="1bd03-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1bd03-119">See also</span></span>

[<span data-ttu-id="1bd03-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1bd03-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

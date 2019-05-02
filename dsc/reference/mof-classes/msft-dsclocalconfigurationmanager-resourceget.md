---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 ResourceGet 메서드
ms.openlocfilehash: 1b74adf2327af2e0f9416f1d00eac4e3b75e9013
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078574"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0d78c-103">MSFT_DSCLocalConfigurationManager 클래스의 ResourceGet 메서드</span><span class="sxs-lookup"><span data-stu-id="0d78c-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0d78c-104">DSC 리소스의 **Get** 메서드를 직접 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="0d78c-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d78c-105">구문</span><span class="sxs-lookup"><span data-stu-id="0d78c-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="0d78c-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0d78c-106">Parameters</span></span>

<span data-ttu-id="0d78c-107">*ResourceType* \[in\] 호출할 리소스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0d78c-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="0d78c-108">*ModuleName* \[in\] 호출할 리소스를 포함하는 모듈의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0d78c-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="0d78c-109">*resourceProperty* \[in\] 해시 테이블의 리소스 속성 이름과 해당 값을 각각 키와 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d78c-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="0d78c-110">[Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet을 사용하여 리소스 속성 및 해당 종류를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0d78c-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="0d78c-111">*configurations* \[out\] 반환 시, 구성의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d78c-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="0d78c-112">반환 값</span><span class="sxs-lookup"><span data-stu-id="0d78c-112">Return value</span></span>

<span data-ttu-id="0d78c-113">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0d78c-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d78c-114">설명</span><span class="sxs-lookup"><span data-stu-id="0d78c-114">Remarks</span></span>

<span data-ttu-id="0d78c-115">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="0d78c-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d78c-116">요구 사항</span><span class="sxs-lookup"><span data-stu-id="0d78c-116">Requirements</span></span>

<span data-ttu-id="0d78c-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0d78c-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0d78c-118">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0d78c-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0d78c-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0d78c-119">See also</span></span>

[<span data-ttu-id="0d78c-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0d78c-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
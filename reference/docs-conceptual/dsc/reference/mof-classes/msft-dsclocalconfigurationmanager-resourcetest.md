---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ResourceTest 메서드
ms.openlocfilehash: ff06fd645a94055e79aa0f8d20f2f06e16483720
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954950"
---
# <a name="resourcetest-method"></a><span data-ttu-id="cc113-103">ResourceTest 메서드</span><span class="sxs-lookup"><span data-stu-id="cc113-103">ResourceTest method</span></span>

<span data-ttu-id="cc113-104">DSC 리소스의 **Test** 메서드를 직접 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="cc113-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="cc113-105">구문</span><span class="sxs-lookup"><span data-stu-id="cc113-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="cc113-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="cc113-106">Parameters</span></span>

<span data-ttu-id="cc113-107">*ResourceType* \[in\] 호출할 리소스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="cc113-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="cc113-108">*ModuleName* \[in\] 호출할 리소스를 포함하는 모듈의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="cc113-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="cc113-109">*resourceProperty* \[in\] 해시 테이블의 리소스 속성 이름과 해당 값을 각각 키와 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cc113-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="cc113-110">[Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet을 사용하여 리소스 속성 및 해당 종류를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cc113-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="cc113-111">*InDesiredState* \[out\] 반환 시, 대상 노드가 원하는 상태이면 이 속성이 **true**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc113-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="cc113-112">반환 값</span><span class="sxs-lookup"><span data-stu-id="cc113-112">Return value</span></span>

<span data-ttu-id="cc113-113">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cc113-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cc113-114">설명</span><span class="sxs-lookup"><span data-stu-id="cc113-114">Remarks</span></span>

<span data-ttu-id="cc113-115">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="cc113-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cc113-116">요구 사항</span><span class="sxs-lookup"><span data-stu-id="cc113-116">Requirements</span></span>

<span data-ttu-id="cc113-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cc113-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cc113-118">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc113-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cc113-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cc113-119">See also</span></span>

[<span data-ttu-id="cc113-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cc113-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

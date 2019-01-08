---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 ResourceTest 메서드
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047685"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ac4cd-103">MSFT_DSCLocalConfigurationManager 클래스의 ResourceTest 메서드</span><span class="sxs-lookup"><span data-stu-id="ac4cd-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ac4cd-104">DSC 리소스의 **Test** 메서드를 직접 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="ac4cd-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="ac4cd-105">구문</span><span class="sxs-lookup"><span data-stu-id="ac4cd-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="ac4cd-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ac4cd-106">Parameters</span></span>

<span data-ttu-id="ac4cd-107">*ResourceType* \[in\] 호출할 리소스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ac4cd-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="ac4cd-108">*ModuleName* \[in\] 호출할 리소스를 포함하는 모듈의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ac4cd-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="ac4cd-109">*resourceProperty* \[in\] 해시 테이블의 리소스 속성 이름과 해당 값을 각각 키와 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac4cd-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="ac4cd-110">[Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet을 사용하여 리소스 속성 및 해당 종류를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ac4cd-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="ac4cd-111">*InDesiredState* \[out\] 반환 시, 대상 노드가 원하는 상태이면 이 속성이 **true**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac4cd-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="ac4cd-112">반환 값</span><span class="sxs-lookup"><span data-stu-id="ac4cd-112">Return value</span></span>

<span data-ttu-id="ac4cd-113">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ac4cd-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac4cd-114">설명</span><span class="sxs-lookup"><span data-stu-id="ac4cd-114">Remarks</span></span>

<span data-ttu-id="ac4cd-115">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="ac4cd-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ac4cd-116">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ac4cd-116">Requirements</span></span>

<span data-ttu-id="ac4cd-117">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ac4cd-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ac4cd-118">{0} 네임스페이스 Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ac4cd-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ac4cd-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ac4cd-119">See also</span></span>

[<span data-ttu-id="ac4cd-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ac4cd-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
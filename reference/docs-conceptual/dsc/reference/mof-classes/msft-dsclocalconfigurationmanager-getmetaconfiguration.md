---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetMetaConfiguration 메서드
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953410"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="17570-103">GetMetaConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="17570-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="17570-104">구성 에이전트를 제어하는 데 사용되는 로컬 구성 관리자 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="17570-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="17570-105">구문</span><span class="sxs-lookup"><span data-stu-id="17570-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="17570-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="17570-106">Parameters</span></span>

<span data-ttu-id="17570-107">*MetaConfiguration* \[out\] 반환 시, 설정을 정의하는 **MSFT_DSCMetaConfiguration** 클래스의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17570-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="17570-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="17570-108">Return value</span></span>

<span data-ttu-id="17570-109">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="17570-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="17570-110">설명</span><span class="sxs-lookup"><span data-stu-id="17570-110">Remarks</span></span>

<span data-ttu-id="17570-111">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="17570-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="17570-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="17570-112">Requirements</span></span>

<span data-ttu-id="17570-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="17570-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="17570-114">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="17570-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="17570-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17570-115">See also</span></span>

[<span data-ttu-id="17570-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="17570-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

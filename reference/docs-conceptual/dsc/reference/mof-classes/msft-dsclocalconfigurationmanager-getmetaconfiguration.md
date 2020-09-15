---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: GetMetaConfiguration 메서드
ms.openlocfilehash: 5111cb3b15e0fba0bf71b412580efdd3cd95b2dc
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463978"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="5d111-103">GetMetaConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="5d111-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="5d111-104">구성 에이전트를 제어하는 데 사용되는 로컬 구성 관리자 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5d111-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d111-105">구문</span><span class="sxs-lookup"><span data-stu-id="5d111-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="5d111-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="5d111-106">Parameters</span></span>

<span data-ttu-id="5d111-107">**MetaConfiguration** \[out\] 반환 시, 설정을 정의하는 **MSFT_DSCMetaConfiguration** 클래스의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d111-107">**MetaConfiguration** \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d111-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="5d111-108">Return value</span></span>

<span data-ttu-id="5d111-109">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5d111-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d111-110">설명</span><span class="sxs-lookup"><span data-stu-id="5d111-110">Remarks</span></span>

<span data-ttu-id="5d111-111">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="5d111-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d111-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="5d111-112">Requirements</span></span>

<span data-ttu-id="5d111-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5d111-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5d111-114">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5d111-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5d111-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d111-115">See also</span></span>

[<span data-ttu-id="5d111-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5d111-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

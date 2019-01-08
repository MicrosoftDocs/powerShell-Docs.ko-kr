---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationStatus 메서드
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047741"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b0fd2-103">MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationStatus 메서드</span><span class="sxs-lookup"><span data-stu-id="b0fd2-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b0fd2-104">구성 상태 기록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b0fd2-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0fd2-105">구문</span><span class="sxs-lookup"><span data-stu-id="b0fd2-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="b0fd2-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b0fd2-106">Parameters</span></span>

<span data-ttu-id="b0fd2-107">*All*\[in\] 이 메서드가 구성 애플리케이션 및 일관성 확인을 포함하여 컴퓨터에서 실행되는 모든 구성에 대한 정보를 반환하면 **true**입니다.</span><span class="sxs-lookup"><span data-stu-id="b0fd2-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="b0fd2-108">*configurationStatus* \[out\] 반환 시, 설정을 정의하는 **MSFT_DSCConfigurationStatus** 클래스의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0fd2-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="b0fd2-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="b0fd2-109">Return value</span></span>

<span data-ttu-id="b0fd2-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b0fd2-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0fd2-111">설명</span><span class="sxs-lookup"><span data-stu-id="b0fd2-111">Remarks</span></span>

<span data-ttu-id="b0fd2-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="b0fd2-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0fd2-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b0fd2-113">Requirements</span></span>

<span data-ttu-id="b0fd2-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b0fd2-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b0fd2-115">{0} 네임스페이스 Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b0fd2-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b0fd2-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b0fd2-116">See also</span></span>

[<span data-ttu-id="b0fd2-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b0fd2-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
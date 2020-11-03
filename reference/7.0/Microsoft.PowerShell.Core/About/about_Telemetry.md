---
description: PowerShell에서 수집 된 원격 분석과 옵트아웃 하는 방법에 대해 설명 합니다.
keywords: PowerShell
Locale: en-US
ms.date: 08/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_telemetry?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Telemetry
ms.openlocfilehash: 4aeab828d66d1f015946051419facd81ce2b78c1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220530"
---
# <a name="about-telemetry"></a><span data-ttu-id="d870a-104">원격 분석 정보</span><span class="sxs-lookup"><span data-stu-id="d870a-104">About Telemetry</span></span>

## <a name="short-description"></a><span data-ttu-id="d870a-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="d870a-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="d870a-106">PowerShell에서 수집 된 원격 분석과 옵트아웃 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d870a-106">Describes the telemetry collected in PowerShell and how to opt-out.</span></span>

## <a name="long-description"></a><span data-ttu-id="d870a-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="d870a-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="d870a-108">PowerShell은 기본 원격 분석 데이터를 Microsoft로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d870a-108">PowerShell sends basic telemetry data to Microsoft.</span></span>
<span data-ttu-id="d870a-109">이 데이터를 사용하면 PowerShell이 사용되는 환경을 더 잘 이해할 수 있으며, 새 기능 및 수정 사항의 우선 순위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d870a-109">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>
<span data-ttu-id="d870a-110">다음 원격 분석 지점이 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d870a-110">The following telemetry points are recorded:</span></span>

- <span data-ttu-id="d870a-111">유형별 PowerShell 시작 수 (API vs 콘솔)</span><span class="sxs-lookup"><span data-stu-id="d870a-111">Count of PowerShell Starts by type (API vs console)</span></span>
- <span data-ttu-id="d870a-112">고유한 PowerShell 사용 수</span><span class="sxs-lookup"><span data-stu-id="d870a-112">Count of unique PowerShell usage</span></span>
- <span data-ttu-id="d870a-113">다음 실행 유형의 수:</span><span class="sxs-lookup"><span data-stu-id="d870a-113">Count of the following execution types:</span></span>
  - <span data-ttu-id="d870a-114">응용 프로그램 (네이티브 명령)</span><span class="sxs-lookup"><span data-stu-id="d870a-114">Application (native commands)</span></span>
  - <span data-ttu-id="d870a-115">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="d870a-115">ExternalScript</span></span>
  - <span data-ttu-id="d870a-116">스크립트</span><span class="sxs-lookup"><span data-stu-id="d870a-116">Script</span></span>
  - <span data-ttu-id="d870a-117">함수</span><span class="sxs-lookup"><span data-stu-id="d870a-117">Function</span></span>
  - <span data-ttu-id="d870a-118">cmdlet</span><span class="sxs-lookup"><span data-stu-id="d870a-118">Cmdlet</span></span>
- <span data-ttu-id="d870a-119">PowerShell과 함께 제공 되는 Microsoft 소유의 실험적 기능 또는 실험적 기능 개수</span><span class="sxs-lookup"><span data-stu-id="d870a-119">Count of enabled Microsoft owned experimental features or experimental features shipped with PowerShell</span></span>
- <span data-ttu-id="d870a-120">호스트 된 세션 수</span><span class="sxs-lookup"><span data-stu-id="d870a-120">Count of hosted sessions</span></span>
- <span data-ttu-id="d870a-121">로드 된 Microsoft 소유 모듈 수</span><span class="sxs-lookup"><span data-stu-id="d870a-121">Count of Microsoft owned modules loaded</span></span>

<span data-ttu-id="d870a-122">이 데이터에는 OS 이름, OS 버전, PowerShell 버전 및 배포 채널이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d870a-122">This data includes the OS name, OS version, the PowerShell version, and the distribution channel.</span></span>

<span data-ttu-id="d870a-123">이 원격 분석을 옵트아웃 하려면 환경 변수 POWERSHELL_TELEMETRY_OPTOUT을 true, 예 또는 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d870a-123">To opt-out of this telemetry, set the environment variable POWERSHELL_TELEMETRY_OPTOUT to true, yes, or 1.</span></span>

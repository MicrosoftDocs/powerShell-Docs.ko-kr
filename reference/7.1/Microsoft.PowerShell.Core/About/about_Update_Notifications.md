---
description: Powershell을 시작할 때 새 버전의 PowerShell이 출시 되었음을 사용자에 게 알립니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Update_Notifications
ms.openlocfilehash: 258eb9316ba063069d032bc115bdeb4614666f37
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93224178"
---
# <a name="about-update-notifications"></a><span data-ttu-id="8680c-104">업데이트 알림 정보</span><span class="sxs-lookup"><span data-stu-id="8680c-104">About Update Notifications</span></span>

## <a name="short-description"></a><span data-ttu-id="8680c-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="8680c-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="8680c-106">Powershell을 시작할 때 새 버전의 PowerShell이 출시 되었음을 사용자에 게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-106">Notifies users on startup of PowerShell that a new version of PowerShell has been released.</span></span>

## <a name="long-description"></a><span data-ttu-id="8680c-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="8680c-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="8680c-108">Powershell 7.0부터 powershell은 업데이트 알림을 사용 하 여 PowerShell에 대 한 업데이트가 있음을 사용자에 게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-108">Beginning with PowerShell 7.0, PowerShell uses update notifications to alert users to the existence of updates to PowerShell.</span></span> <span data-ttu-id="8680c-109">PowerShell은 하루 한 번 온라인 서비스를 쿼리하여 최신 버전을 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-109">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="8680c-110">업데이트 확인은 지정 된 24 시간 동안 첫 번째 세션 중에 발생 하지만 성능상의 이유로 알림은 후속 세션의 시작 부분에만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-110">While the update check happens during the first session in a given 24-hour period, for performance reasons, the notification will only be shown on the start of subsequent sessions.</span></span> <span data-ttu-id="8680c-111">또한 성능상의 이유로 세션이 시작 될 때까지 3 초 이상이 지나면 검사가 시작 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-111">Also for performance reasons, the check will not start until at least 3 seconds after the session begins.</span></span>

<span data-ttu-id="8680c-112">기본적으로 PowerShell은 버전/분기에 따라 두 가지 알림 채널 중 하나를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-112">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="8680c-113">지원되는 GA(일반 공급) 버전의 PowerShell은 업데이트된 GA 릴리스에 대한 알림만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-113">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="8680c-114">미리 보기 및 RC(릴리스 후보) 릴리스는 미리 보기, RC 및 GA 릴리스에 대한 업데이트 알림을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-114">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="8680c-115">업데이트 알림 동작은 `POWERSHELL_UPDATECHECK` 환경 변수를 사용하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-115">The update notification behavior can be changed using the `POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="8680c-116">지원되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-116">The following values are supported:</span></span>

- <span data-ttu-id="8680c-117">`Off` 업데이트 알림 기능을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-117">`Off` turns off the update notification feature</span></span>
- <span data-ttu-id="8680c-118">`Default` 는 정의와 동일 합니다 `POWERSHELL_UPDATECHECK` .</span><span class="sxs-lookup"><span data-stu-id="8680c-118">`Default` is the same as not defining `POWERSHELL_UPDATECHECK`:</span></span>
  - <span data-ttu-id="8680c-119">GA 릴리스는 GA 릴리스 업데이트를 알림</span><span class="sxs-lookup"><span data-stu-id="8680c-119">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="8680c-120">미리 보기/RC 릴리스는 GA 및 미리 보기 릴리스 업데이트를 알림</span><span class="sxs-lookup"><span data-stu-id="8680c-120">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="8680c-121">`LTS` LTS (장기 서비스) GA 릴리스에 대 한 업데이트 알림</span><span class="sxs-lookup"><span data-stu-id="8680c-121">`LTS` only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

<span data-ttu-id="8680c-122">다음 끝점은 현재 각 채널의 최신 버전을 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-122">The following endpoints are currently used for determining the latest version of each channel:</span></span>

- <span data-ttu-id="8680c-123">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span><span class="sxs-lookup"><span data-stu-id="8680c-123">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span></span>
- <span data-ttu-id="8680c-124">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span><span class="sxs-lookup"><span data-stu-id="8680c-124">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span></span>
- <span data-ttu-id="8680c-125">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span><span class="sxs-lookup"><span data-stu-id="8680c-125">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span></span>

<span data-ttu-id="8680c-126">업데이트 알림은 PowerShell을 자동으로 업데이트 하는 방법을 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-126">The update notification doesn't provide any way to automatically update PowerShell.</span></span> <span data-ttu-id="8680c-127">나중에 PowerShell 내에서 업데이트할 추가 지침이 나 기능이 있을 수 있지만, 현재는 PowerShell을 설치 하는 데 사용한 것과 동일한 설치 메커니즘을 사용 하 여 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8680c-127">In the future, there may be more instructions or capabilities to update from within PowerShell, but today, you should use the same install mechanism you used to install PowerShell to update it.</span></span>


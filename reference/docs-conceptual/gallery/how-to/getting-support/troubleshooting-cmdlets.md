---
ms.date: 12/01/2020
title: cmdlet 문제 해결
description: 이 문서에서는 PowerShell 갤러리를 사용하여 오류를 해결하는 데 필요한 정보 및 단계를 제공합니다.
ms.openlocfilehash: 980da8ea7b8a09513f33a9939d512c437b755d8d
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913321"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="42fd6-103">cmdlet 문제 해결</span><span class="sxs-lookup"><span data-stu-id="42fd6-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="42fd6-104">"경고: '패키지 이름' 패키지를 다운로드하지 못했습니다." 문제를 해결하는 방법</span><span class="sxs-lookup"><span data-stu-id="42fd6-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="42fd6-105">`Install-Module` 또는 `Update-Module`이 일부 컴퓨터에서 실패하는 경우가 있다는 신고를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="42fd6-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="42fd6-106">조사 결과에 따르면 이 문제는 네트워킹 연결과 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42fd6-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="42fd6-107">최근에 패키지를 안정적으로 다운로드할 수 있도록 NuGet 공급자를 업데이트했습니다.</span><span class="sxs-lookup"><span data-stu-id="42fd6-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="42fd6-108">아래 지침에 따라 NuGet 공급자의 최신 빌드를 설치한 다음 모듈을 설치 또는 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42fd6-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="42fd6-109">아래에서는 'Azure' 모듈을 예로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42fd6-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

## <a name="required-network-endpoints"></a><span data-ttu-id="42fd6-110">필수 네트워크 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="42fd6-110">Required network endpoints</span></span>

<span data-ttu-id="42fd6-111">설치 및 업데이트 cmdlets에는 PowerShell 갤러리에서 사용하는 네트워크 엔드포인트로의 연결을 위해 인터넷 액세스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="42fd6-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="42fd6-112">네트워크 액세스 정책에 따라 다음 엔드포인트로 연결할 수 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="42fd6-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="42fd6-113">`psg-prod-eastus.azureedge.net` - CDN 호스트 이름</span><span class="sxs-lookup"><span data-stu-id="42fd6-113">`psg-prod-eastus.azureedge.net` - CDN hostname</span></span>
- <span data-ttu-id="42fd6-114">`az818661.vo.msecnd.net` - CDN 호스트 이름</span><span class="sxs-lookup"><span data-stu-id="42fd6-114">`az818661.vo.msecnd.net` - CDN hostname</span></span>
- <span data-ttu-id="42fd6-115">`devopsgallerystorage.blob.core.windows.net` - 스토리지 계정 호스트 이름</span><span class="sxs-lookup"><span data-stu-id="42fd6-115">`devopsgallerystorage.blob.core.windows.net` - storage account hostname</span></span>
- <span data-ttu-id="42fd6-116">`*.powershellgallery.com` - 웹 사이트</span><span class="sxs-lookup"><span data-stu-id="42fd6-116">`*.powershellgallery.com` - website</span></span>
- <span data-ttu-id="42fd6-117">`go.microsoft.com` - 리디렉션 서비스</span><span class="sxs-lookup"><span data-stu-id="42fd6-117">`go.microsoft.com` - redirection service</span></span>

> [!NOTE]
> <span data-ttu-id="42fd6-118">PowerShell 갤러리와 상호 작용하는 cmdlet은 PowerShell 갤러리 서비스의 작동이 중단될 경우 예기치 않은 오류와 함께 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42fd6-118">Cmdlets that interact with the PowerShell Gallery can fail with unexpected errors when there is an outage of the PowerShell Gallery services.</span></span> <span data-ttu-id="42fd6-119">PowerShell 갤러리의 현재 상태를 확인하려면 GitHub에서 [PowerShell 갤러리 상태](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) 페이지를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42fd6-119">To see the current status of the PowerShell Gallery, see the [PowerShell Gallery Status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) page on GitHub.</span></span>

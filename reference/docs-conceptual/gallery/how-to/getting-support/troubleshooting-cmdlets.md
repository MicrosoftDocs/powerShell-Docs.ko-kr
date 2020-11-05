---
ms.date: 06/12/2017
title: cmdlet 문제 해결
description: 이 문서에서는 PowerShell 갤러리를 사용하여 오류를 해결하는 데 필요한 정보 및 단계를 제공합니다.
ms.openlocfilehash: db9e58c185c6f3bca26ff3639af85fa2dba48909
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661060"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="56eda-103">cmdlet 문제 해결</span><span class="sxs-lookup"><span data-stu-id="56eda-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="56eda-104">"경고: '패키지 이름' 패키지를 다운로드하지 못했습니다." 문제를 해결하는 방법</span><span class="sxs-lookup"><span data-stu-id="56eda-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="56eda-105">`Install-Module` 또는 `Update-Module`이 일부 컴퓨터에서 실패하는 경우가 있다는 신고를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="56eda-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="56eda-106">조사 결과에 따르면 이 문제는 네트워킹 연결과 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56eda-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="56eda-107">최근에 패키지를 안정적으로 다운로드할 수 있도록 NuGet 공급자를 업데이트했습니다.</span><span class="sxs-lookup"><span data-stu-id="56eda-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="56eda-108">아래 지침에 따라 NuGet 공급자의 최신 빌드를 설치한 다음 모듈을 설치 또는 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56eda-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="56eda-109">아래에서는 'Azure' 모듈을 예로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="56eda-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a><span data-ttu-id="56eda-110">필수 네트워크 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="56eda-110">Required network endpoints</span></span>

<span data-ttu-id="56eda-111">설치 및 업데이트 cmdlets에는 PowerShell 갤러리에서 사용하는 네트워크 엔드포인트로의 연결을 위해 인터넷 액세스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="56eda-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="56eda-112">네트워크 액세스 정책에 따라 다음 엔드포인트로 연결할 수 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="56eda-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="56eda-113">oneget.org</span><span class="sxs-lookup"><span data-stu-id="56eda-113">oneget.org</span></span>
- <span data-ttu-id="56eda-114">go.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="56eda-114">go.microsoft.com</span></span>
- <span data-ttu-id="56eda-115">az818661.vo.msecnd.net</span><span class="sxs-lookup"><span data-stu-id="56eda-115">az818661.vo.msecnd.net</span></span>
- <span data-ttu-id="56eda-116">www.powershellgallery.com</span><span class="sxs-lookup"><span data-stu-id="56eda-116">www.powershellgallery.com</span></span>
- <span data-ttu-id="56eda-117">devopsgallerystorage.blob.core.windows.net</span><span class="sxs-lookup"><span data-stu-id="56eda-117">devopsgallerystorage.blob.core.windows.net</span></span>

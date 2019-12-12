---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: cmdlet 문제 해결
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352105"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="2a850-103">cmdlet 문제 해결</span><span class="sxs-lookup"><span data-stu-id="2a850-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="2a850-104">"경고: '패키지 이름' 패키지를 다운로드하지 못했습니다." 문제를 해결하는 방법</span><span class="sxs-lookup"><span data-stu-id="2a850-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="2a850-105">`Install-Module` 또는 `Update-Module`이 일부 컴퓨터에서 실패하는 경우가 있다는 신고를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="2a850-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="2a850-106">조사 결과에 따르면 이 문제는 네트워킹 연결과 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a850-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="2a850-107">최근에 패키지를 안정적으로 다운로드할 수 있도록 NuGet 공급자를 업데이트했습니다.</span><span class="sxs-lookup"><span data-stu-id="2a850-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="2a850-108">아래 지침에 따라 NuGet 공급자의 최신 빌드를 설치한 다음 모듈을 설치 또는 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a850-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="2a850-109">아래에서는 'Azure' 모듈을 예로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a850-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a><span data-ttu-id="2a850-110">필수 네트워크 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="2a850-110">Required network endpoints</span></span>

<span data-ttu-id="2a850-111">설치 및 업데이트 cmdlets에는 PowerShell 갤러리에서 사용하는 네트워크 엔드포인트로의 연결을 위해 인터넷 액세스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2a850-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="2a850-112">네트워크 액세스 정책에 따라 다음 엔드포인트로 연결할 수 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="2a850-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="2a850-113">oneget.org</span><span class="sxs-lookup"><span data-stu-id="2a850-113">oneget.org</span></span>
- <span data-ttu-id="2a850-114">go.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="2a850-114">go.microsoft.com</span></span>
- <span data-ttu-id="2a850-115">az818661.vo.msecnd.net</span><span class="sxs-lookup"><span data-stu-id="2a850-115">az818661.vo.msecnd.net</span></span>
- <span data-ttu-id="2a850-116">[www.powershellgallery.com](www.powershellgallery.com)</span><span class="sxs-lookup"><span data-stu-id="2a850-116">www.powershellgallery.com</span></span>
- <span data-ttu-id="2a850-117">devopsgallerystorage.blob.core.windows.net</span><span class="sxs-lookup"><span data-stu-id="2a850-117">devopsgallerystorage.blob.core.windows.net</span></span>

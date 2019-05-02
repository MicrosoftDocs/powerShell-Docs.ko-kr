---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: cmdlet 문제 해결
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084184"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="12cf0-103">cmdlet 문제 해결</span><span class="sxs-lookup"><span data-stu-id="12cf0-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="12cf0-104">"경고: '패키지 이름' 패키지를 다운로드하지 못했습니다." 문제를 해결하는 방법</span><span class="sxs-lookup"><span data-stu-id="12cf0-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="12cf0-105">`Install-Module` 또는 `Update-Module`이 일부 컴퓨터에서 실패하는 경우가 있다는 신고를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="12cf0-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="12cf0-106">조사 결과에 따르면 이 문제는 네트워킹 연결과 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12cf0-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="12cf0-107">최근에 패키지를 안정적으로 다운로드할 수 있도록 NuGet 공급자를 업데이트했습니다.</span><span class="sxs-lookup"><span data-stu-id="12cf0-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="12cf0-108">아래 지침에 따라 NuGet 공급자의 최신 빌드를 설치한 다음 모듈을 설치 또는 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12cf0-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="12cf0-109">아래에서는 'Azure' 모듈을 예로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf0-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

---
title: Docker에서 PowerShell 사용
description: Docker 이미지에 사전 설치된 PowerShell을 사용하는 방법입니다.
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: b16a31a04ca863ab55c7c9718b1a1a973e61ee46
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "80646367"
---
# <a name="using-powershell-in-docker"></a><span data-ttu-id="c4dd1-103">Docker에서 PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="c4dd1-103">Using PowerShell in Docker</span></span>

<span data-ttu-id="c4dd1-104">Microsoft는 사전 설치된 PowerShell로 Docker 이미지를 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-104">We publish Docker images with PowerShell preinstalled.</span></span> <span data-ttu-id="c4dd1-105">이 문서에는 Docker 컨테이너에서 PowerShell을 사용하여 시작하는 방법이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-105">This article shows you how to get started using PowerShell in the Docker container.</span></span>

## <a name="finding-available-images"></a><span data-ttu-id="c4dd1-106">사용 가능한 이미지 찾기</span><span class="sxs-lookup"><span data-stu-id="c4dd1-106">Finding available images</span></span>

<span data-ttu-id="c4dd1-107">릴리스된 이미지에는 Docker 17.05 이상 버전이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-107">The released images require Docker 17.05 or newer.</span></span> <span data-ttu-id="c4dd1-108">또한 `sudo` 또는 로컬 관리자 권한 없이 Docker를 실행할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-108">It is also expected that you are able to run Docker without `sudo` or local administrative rights.</span></span> <span data-ttu-id="c4dd1-109">Docker의 공식 [지침][install]에 따라 `docker`를 올바르게 설치하세요.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-109">Please follow Docker's official [instructions][install] to install `docker` correctly.</span></span>

<span data-ttu-id="c4dd1-110">릴리스 컨테이너는 `centos:7`과 같은 공식 배포 이미지에서 파생됩니다. 그런 다음 종속성을 설치하고 마지막으로 PowerShell 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-110">The release containers derive from the official distribution image, such as `centos:7`, then install dependencies, and finally install the PowerShell package.</span></span>

<span data-ttu-id="c4dd1-111">이러한 컨테이너는 [hub.docker.com/r/microsoft/powershell][docker-release]에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-111">These containers live at [hub.docker.com/r/microsoft/powershell][docker-release].</span></span>

<span data-ttu-id="c4dd1-112">이러한 Docker 이미지에 대한 자세한 내용은 GitHub의 [PowerShell-Docker][PowerShell-Docker] 리포지토리를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-112">For more information about these Docker images, visit the [PowerShell-Docker][PowerShell-Docker] repository on GitHub.</span></span>

## <a name="using-powershell-in-a-container"></a><span data-ttu-id="c4dd1-113">컨테이너에서 PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="c4dd1-113">Using PowerShell in a container</span></span>

<span data-ttu-id="c4dd1-114">다음 단계는 이미지를 다운로드하고 대화형 PowerShell 세션을 시작하는 데 필요한 Docker 명령을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-114">The following steps show the Docker commands required to download the image and start an interactive PowerShell session.</span></span>

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a><span data-ttu-id="c4dd1-115">더 이상 필요하지 않은 이미지 제거</span><span class="sxs-lookup"><span data-stu-id="c4dd1-115">Remove the image when no longer needed</span></span>

<span data-ttu-id="c4dd1-116">더 이상 필요하지 않은 경우 다음 명령이 Docker 이미지를 삭제하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-116">The following command is used to delete the Docker image when you no longer need it.</span></span>

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a><span data-ttu-id="c4dd1-117">법률 및 라이선스</span><span class="sxs-lookup"><span data-stu-id="c4dd1-117">Legal and Licensing</span></span>

<span data-ttu-id="c4dd1-118">PowerShell은 [MIT 라이선스][]에 따라 사용이 허가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-118">PowerShell is licensed under the [MIT license][].</span></span>

### <a name="windows-docker-file-and-image-licenses"></a><span data-ttu-id="c4dd1-119">Windows Docker 파일 및 이미지 라이선스</span><span class="sxs-lookup"><span data-stu-id="c4dd1-119">Windows Docker File and Image Licenses</span></span>

<span data-ttu-id="c4dd1-120">Windows 컨테이너용 컨테이너 OS 이미지를 요청하고 사용하면 Docker 허브에서 확인할 수 있는 추가 사용 조건을 승인, 이해 및 동의하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-120">By requesting and using the Container OS Image for Windows containers, you acknowledge, understand, and consent to the Supplemental License Terms available on Docker hub:</span></span>

- <span data-ttu-id="c4dd1-121">[Window Server Core][Window Server Core]</span><span class="sxs-lookup"><span data-stu-id="c4dd1-121">[Window Server Core][Window Server Core]</span></span>
- <span data-ttu-id="c4dd1-122">[Nano 서버][Nano Server]</span><span class="sxs-lookup"><span data-stu-id="c4dd1-122">[Nano Server][Nano Server]</span></span>

### <a name="telemetry"></a><span data-ttu-id="c4dd1-123">원격 분석</span><span class="sxs-lookup"><span data-stu-id="c4dd1-123">Telemetry</span></span>

<span data-ttu-id="c4dd1-124">기본적으로 PowerShell은 PowerShell의 향후 버전을 개발하는 데 도움이 되도록 개인 식별 정보를 제외한 원격 분석 데이터를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-124">By default, PowerShell collects limited telemetry without personally identifiable information to help aid development of future versions of PowerShell.</span></span> <span data-ttu-id="c4dd1-125">원격 분석 전송을 거부하려면 설치 위치에서 PowerShell을 시작하기 전에 `POWERSHELL_TELEMETRY_OPTOUT`이라는 환경 변수를 만들고 값을 `1`로 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-125">To opt-out of sending telemetry, create an environment variable called `POWERSHELL_TELEMETRY_OPTOUT` set to a value of `1` before starting PowerShell from the installed location.</span></span> <span data-ttu-id="c4dd1-126">수집한 원격 분석에는 [Microsoft 개인정보처리방침][privacy]이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4dd1-126">The telemetry we collect falls under the [Microsoft Privacy Statement][privacy].</span></span>

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[MIT 라이선스]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/

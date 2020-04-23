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
# <a name="using-powershell-in-docker"></a>Docker에서 PowerShell 사용

Microsoft는 사전 설치된 PowerShell로 Docker 이미지를 게시합니다. 이 문서에는 Docker 컨테이너에서 PowerShell을 사용하여 시작하는 방법이 나와 있습니다.

## <a name="finding-available-images"></a>사용 가능한 이미지 찾기

릴리스된 이미지에는 Docker 17.05 이상 버전이 필요합니다. 또한 `sudo` 또는 로컬 관리자 권한 없이 Docker를 실행할 수 있어야 합니다. Docker의 공식 [지침][install]에 따라 `docker`를 올바르게 설치하세요.

릴리스 컨테이너는 `centos:7`과 같은 공식 배포 이미지에서 파생됩니다. 그런 다음 종속성을 설치하고 마지막으로 PowerShell 패키지를 설치합니다.

이러한 컨테이너는 [hub.docker.com/r/microsoft/powershell][docker-release]에 있습니다.

이러한 Docker 이미지에 대한 자세한 내용은 GitHub의 [PowerShell-Docker][PowerShell-Docker] 리포지토리를 참조하세요.

## <a name="using-powershell-in-a-container"></a>컨테이너에서 PowerShell 사용

다음 단계는 이미지를 다운로드하고 대화형 PowerShell 세션을 시작하는 데 필요한 Docker 명령을 보여 줍니다.

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a>더 이상 필요하지 않은 이미지 제거

더 이상 필요하지 않은 경우 다음 명령이 Docker 이미지를 삭제하는 데 사용됩니다.

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a>법률 및 라이선스

PowerShell은 [MIT 라이선스][]에 따라 사용이 허가됩니다.

### <a name="windows-docker-file-and-image-licenses"></a>Windows Docker 파일 및 이미지 라이선스

Windows 컨테이너용 컨테이너 OS 이미지를 요청하고 사용하면 Docker 허브에서 확인할 수 있는 추가 사용 조건을 승인, 이해 및 동의하는 것입니다.

- [Window Server Core][Window Server Core]
- [Nano 서버][Nano Server]

### <a name="telemetry"></a>원격 분석

기본적으로 PowerShell은 PowerShell의 향후 버전을 개발하는 데 도움이 되도록 개인 식별 정보를 제외한 원격 분석 데이터를 수집합니다. 원격 분석 전송을 거부하려면 설치 위치에서 PowerShell을 시작하기 전에 `POWERSHELL_TELEMETRY_OPTOUT`이라는 환경 변수를 만들고 값을 `1`로 설정하세요. 수집한 원격 분석에는 [Microsoft 개인정보처리방침][privacy]이 적용됩니다.

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[MIT 라이선스]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/

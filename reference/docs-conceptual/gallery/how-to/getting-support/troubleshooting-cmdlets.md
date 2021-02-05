---
ms.date: 01/25/2021
title: cmdlet 문제 해결
description: 이 문서에서는 PowerShell 갤러리를 사용하여 오류를 해결하는 데 필요한 정보 및 단계를 제공합니다.
ms.openlocfilehash: 8139147683b655b5f8532c3068387db6df12a98f
ms.sourcegitcommit: 0f003644684422e425a59b7361121e05ac772e15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98771807"
---
# <a name="troubleshooting-cmdlets"></a>cmdlet 문제 해결

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>"경고: '패키지 이름' 패키지를 다운로드하지 못했습니다." 문제를 해결하는 방법

`Install-Module` 또는 `Update-Module`이 일부 컴퓨터에서 실패하는 경우가 있다는 신고를 받았습니다. 조사 결과에 따르면 이 문제는 네트워킹 연결과 관련이 있습니다. 최근에 패키지를 안정적으로 다운로드할 수 있도록 NuGet 공급자를 업데이트했습니다. 아래 지침에 따라 NuGet 공급자의 최신 빌드를 설치한 다음 모듈을 설치 또는 업데이트할 수 있습니다. 아래에서는 'Azure' 모듈을 예로 사용합니다.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

## <a name="required-network-endpoints"></a>필수 네트워크 엔드포인트

설치 및 업데이트 cmdlets에는 PowerShell 갤러리에서 사용하는 네트워크 엔드포인트로의 연결을 위해 인터넷 액세스가 필요합니다. 네트워크 액세스 정책에 따라 다음 엔드포인트로 연결할 수 있는지 확인하십시오.

- `psg-prod-eastus.azureedge.net` - CDN 호스트 이름
- `az818661.vo.msecnd.net` - CDN 호스트 이름
- `devopsgallerystorage.blob.core.windows.net` - 스토리지 계정 호스트 이름
- `*.powershellgallery.com` - 웹 사이트
- `go.microsoft.com` - 리디렉션 서비스
- `onegetcdn.azureedge.net` - `PowerShellGet/PackageManagement`의 NuGet 공급자 부트스트랩

> [!NOTE]
> PowerShell 갤러리와 상호 작용하는 cmdlet은 PowerShell 갤러리 서비스의 작동이 중단될 경우 예기치 않은 오류와 함께 실패할 수 있습니다. PowerShell 갤러리의 현재 상태를 확인하려면 GitHub에서 [PowerShell 갤러리 상태](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) 페이지를 참조하세요.

---
ms.date: 06/12/2017
title: PowerShell 갤러리 시작
description: 이 문서에서는 PowerShell 갤러리 및 PowerShellGet cmdlet 사용을 시작하는 방법을 설명합니다.
ms.openlocfilehash: a5045e4ecee2eb8bc9aa373a6b8ec3a940b4de33
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913284"
---
# <a name="getting-started-with-the-powershell-gallery"></a>PowerShell 갤러리 시작

PowerShell 갤러리는 다운로드하고 이용할 수 있는 스크립트, 모듈 및 DSC 리소스를 포함하는 패키지 리포지토리입니다. [PowerShellGet](/powershell/module/powershellget) 모듈에서 cmdlet을 사용하여 PowerShell 갤러리에서 패키지를 설치합니다. PowerShell 갤러리에서 항목을 다운로드하기 위해 로그인할 필요는 없습니다.

> [!NOTE]
> 패키지는 PowerShell 갤러리에서 직접 다운로드할 수 있지만 권장되는 방법이 아닙니다. 자세한 내용은 [수동 패키지 다운로드](how-to/working-with-packages/manual-download.md)를 참조하세요.

## <a name="discovering-packages-from-the-powershell-gallery"></a>PowerShell 갤러리에서 패키지 검색

PowerShell 갤러리의 [홈페이지](https://www.powershellgallery.com)에서 **검색** 컨트롤을 사용하거나 [패키지 페이지](https://www.powershellgallery.com/packages)에서 모듈 및 스크립트를 검색하여 PowerShell 갤러리에서 패키지를 찾을 수 있습니다. 패키지 유형에 따라 [Find-Module][], [Find-DscResource], and [Find-Script][] cmdlet을 `-Repository PSGallery`와 함께 사용하여 PowerShell 갤러리에서 패키지를 찾을 수도 있습니다.

다음 매개 변수를 사용하여 갤러리의 결과를 필터링할 수 있습니다.

- 이름
- AllVersions
- MinimumVersion
- RequiredVersion
- 태그
- Includes
- DscResource
- RoleCapability
- 명령
- 필터

갤러리에서 특정 DSC 리소스를 검색하는 데만 관심이 있는 경우 [Find-DscResource][] cmdlet을 실행할 수 있습니다. Find-DscResource는 갤러리에 포함된 DSC 리소스에 대한 데이터를 반환합니다. DSC 리소스는 항상 모듈의 일부로 제공되기 때문에 여전히 [Install-Module][]을 실행하여 이러한 DSC 리소스를 설치해야 합니다.

## <a name="learning-about-packages-in-the-powershell-gallery"></a>PowerShell 갤러리에 있는 패키지에 대해 알아보기

관심 있는 패키지를 찾았으면 자세히 알아보는 것이 좋습니다. 이렇게 하려면 갤러리에서 해당 패키지의 페이지를 살펴봅니다. 이 페이지에서 패키지와 함께 업로드된 메타데이터를 모두 볼 수 있습니다. 이 메타데이터는 패키지의 작성자가 제공하며 Microsoft에서 확인하지 않습니다. 패키지의 소유자는 패키지를 게시하는 데 사용되는 갤러리 계정에 강하게 연결되어 있으며 작성자 필드보다 더 신뢰할 수 있습니다.

좋은 의도로 게시되지 않은 것 같은 패키지를 발견할 경우 해당 패키지의 페이지에서 **신고하기** 를 클릭합니다.

[Find-Module][] 또는 [Find-Script][]를 실행하는 경우 반환된 PSGetModuleInfo 개체에서 이 데이터를 볼 수 있습니다. 예를 들어 `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`를 실행하면 갤러리의 PSReadLine 모듈에 대한 데이터가 반환됩니다.

## <a name="downloading-packages-from-the-powershell-gallery"></a>PowerShell 갤러리에서 패키지 다운로드

PowerShell 갤러리에서 패키지를 다운로드하려면 다음 프로세스를 사용하는 것이 좋습니다.

### <a name="inspect"></a>검사

검사를 위해 갤러리에서 패키지를 다운로드하려면 패키지 유형에 따라 [Save-Module][] 또는 [Save-Script][] cmdlet을 실행합니다. 이렇게 하면 설치하지 않고 로컬에 패키지를 저장한 다음 패키지 내용을 검사할 수 있습니다. 저장된 패키지는 수동으로 삭제해야 합니다.

이러한 패키지 중 일부는 Microsoft에서 작성되었으며 다른 항목은 PowerShell 커뮤니티에서 작성되었습니다. 설치 전에 이 갤러리에 있는 패키지의 내용과 코드를 검토하는 것이 좋습니다.

좋은 의도로 게시되지 않은 것 같은 패키지를 발견할 경우 해당 패키지의 페이지에서 **신고하기** 를 클릭합니다.

### <a name="install"></a>설치

사용을 위해 갤러리에서 패키지를 설치하려면 패키지 유형에 따라 [Install-Module][] 또는 [Install-Script][] cmdlet을 실행합니다.

[Install-Module][]은 기본적으로 `$env:ProgramFiles\WindowsPowerShell\Modules`에 모듈을 설치합니다.
이 경우 관리자 계정이 필요합니다. `-Scope CurrentUser` 매개 변수를 추가하는 경우 모듈은 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`에 설치됩니다.

[Install-Script][]는 기본적으로 `$env:ProgramFiles\WindowsPowerShell\Scripts`에 스크립트를 설치합니다.
이 경우 관리자 계정이 필요합니다. `-Scope CurrentUser` 매개 변수를 추가하는 경우 스크립트는 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`에 설치됩니다.

기본적으로 [Install-Module][] 및 [Install-Script][]는 최신 버전의 패키지를 설치합니다. 이전 버전의 패키지를 설치하려면 `-RequiredVersion` 매개 변수를 추가합니다.

### <a name="deploy"></a>배포

PowerShell 갤러리의 패키지를 Azure Automation에 배포하려면 **Azure Automation** 을 클릭한 후 패키지 세부 정보 페이지에서 **Azure Automation에 배포** 를 클릭합니다. Azure 관리 포털로 리디렉션되며, 여기서 Azure 계정 자격 증명을 사용하여 로그인합니다. 종속성과 함께 패키지를 배포하면 모든 종속성이 Azure Automation에 배포됩니다. 패키지 메타데이터에 **AzureAutomationNotSupported** 태그를 추가하면 Azure Automation에 배포 단추를 해제할 수 있습니다.

Azure Automation에 대한 자세한 내용은 [Azure Automation](/azure/automation) 설명서를 참조하세요.

## <a name="updating-packages-from-the-powershell-gallery"></a>PowerShell 갤러리에서 패키지 업데이트

PowerShell 갤러리에서 설치된 패키지를 업데이트하려면 [Update-Module][] 또는 [Update-Script][] cmdlet을 실행합니다. 추가 매개 변수 없이 실행하면 [Update-Module][]이 [Install-Module][]을 실행하여 설치된 모든 모듈을 업데이트하려고 합니다. 모듈을 선택적으로 업데이트하려면 `-Name` 매개 변수를 추가합니다.

마찬가지로, 추가 매개 변수 없이 실행하면 [Update-Script][]는 [Install-Script][]를 실행하여 설치된 모든 스크립트를 업데이트하려고 합니다. 스크립트를 선택적으로 업데이트하려면 `-Name` 매개 변수를 추가합니다.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>PowerShell 갤러리에서 설치한 패키지 나열

PowerShell 갤러리에서 설치한 모듈을 찾으려면 [Get-InstalledModule][] cmdlet을 실행합니다. 이 명령은 PowerShell 갤러리에서 직접 설치된 시스템의 모듈을 모두 나열합니다.

마찬가지로, PowerShell 갤러리에서 설치한 스크립트를 찾으려면 [Get-InstalledScript][] cmdlet을 실행합니다. 이 명령은 PowerShell 갤러리에서 직접 설치된 시스템의 스크립트를 모두 나열합니다.

## <a name="network-access-to-the-powershell-gallery"></a>PowerShell 갤러리에 대한 네트워크 액세스

PowerShell 갤러리는 다음 호스트 이름을 사용합니다.

- `psg-prod-eastus.azureedge.net` - CDN 호스트 이름
- `az818661.vo.msecnd.net` - CDN 호스트 이름
- `devopsgallerystorage.blob.core.windows.net` - 스토리지 계정 호스트 이름
- `*.powershellgallery.com` - 웹 사이트
- `go.microsoft.com` - 리디렉션 서비스

이러한 호스트 이름은 네트워크 액세스를 제어하는 허용 목록에 추가해야 합니다.

[!INCLUDE [TLS 1.2 Requirement](../../includes/tls-gallery.md)]

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
[Update-Module]: /powershell/module/powershellget/Update-Module
[Update-Script]: /powershell/module/powershellget/Update-Script

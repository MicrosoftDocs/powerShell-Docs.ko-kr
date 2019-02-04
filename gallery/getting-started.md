---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: PowerShell 갤러리 시작
ms.openlocfilehash: c8beba3009e462ce52cdecd34fc0313d9234f289
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682998"
---
# <a name="getting-started-with-the-powershell-gallery"></a>PowerShell 갤러리 시작

PowerShell 갤러리는 스크립트, 모듈 및 DSC 리소스 다운로드를 활용 하 여 포함 된 패키지 리포지토리입니다. Cmdlet을 사용 합니다 [PowerShellGet](/powershell/module/powershellget) 모듈을 PowerShell 갤러리에서 패키지를 설치 합니다. PowerShell 갤러리에서 항목을 다운로드하기 위해 로그인할 필요는 없습니다.

> [!NOTE]
> 패키지는 PowerShell 갤러리에서 직접 다운로드할 수 있지만 권장되는 방법이 아닙니다.
> 자세한 내용은 [수동 패키지 다운로드](/powershell/gallery/how-to/working-with-packages/manual-download)를 참조하세요.

## <a name="discovering-packages-from-the-powershell-gallery"></a>PowerShell 갤러리에서 패키지 검색

사용 하 여 PowerShell 갤러리에서 패키지를 찾을 수 있습니다 합니다 **검색** PowerShell 갤러리의 컨트롤 [홈페이지](https://www.powershellgallery.com), 또는 모듈 및 스크립트를 통해 이동 하 여에서 [패키지 페이지 ](https://www.powershellgallery.com/packages). PowerShell 갤러리에서 패키지를 실행 하 여 찾을 수도 있습니다는 [Find-module][]를 [Find-dscresource], 및 [Find-script][] 패키지 형식에 따라 cmdlet 사용 하 여 `-Repository PSGallery`입니다.

다음 매개 변수를 사용 하 여 갤러리의 결과 필터링 할 수 있습니다.

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

갤러리에서 특정 DSC 리소스를 검색하는 데만 관심이 있는 경우 [Find-DscResource] cmdlet을 실행할 수 있습니다. Find-DscResource는 갤러리에 포함된 DSC 리소스에 대한 데이터를 반환합니다.
DSC 리소스는 항상 모듈의 일부로 제공되기 때문에 여전히 [Install-Module][]을 실행하여 이러한 DSC 리소스를 설치해야 합니다.

## <a name="learning-about-packages-in-the-powershell-gallery"></a>PowerShell 갤러리에 있는 패키지에 대해 알아보기

관심 있는 패키지를 찾았으면 자세히 알아보는 것이 좋습니다. 이렇게 하려면 갤러리에서 해당 패키지의 페이지를 살펴봅니다. 이 페이지에서 패키지와 함께 업로드된 메타데이터를 모두 볼 수 있습니다. 이 메타데이터는 패키지의 작성자가 제공하며 Microsoft에서 확인하지 않습니다. 패키지의 소유자는 패키지를 게시하는 데 사용되는 갤러리 계정에 강하게 연결되어 있으며 작성자 필드보다 더 신뢰할 수 있습니다.

좋은 의도로 게시되지 않은 것 같은 패키지를 발견할 경우 해당 패키지의 페이지에서 **신고하기**를 클릭합니다.

[Find-Module][] 또는 [Find-Script][]를 실행하는 경우 반환된 PSGetModuleInfo 개체에서 이 데이터를 볼 수 있습니다. 예를 들어 `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`를 실행하면
갤러리에서 PSReadLine 모듈의 데이터가 반환됩니다.

## <a name="downloading-packages-from-the-powershell-gallery"></a>PowerShell 갤러리에서 패키지 다운로드

PowerShell 갤러리에서 패키지를 다운로드하려면 다음 프로세스를 사용하는 것이 좋습니다.

### <a name="inspect"></a>검사

검사를 위해 갤러리에서 패키지를 다운로드하려면 패키지 유형에 따라 [Save-Module][] 또는 [Save-Script][] cmdlet을 실행합니다. 이렇게 하면 설치하지 않고 로컬에 패키지를 저장한 다음 패키지 내용을 검사할 수 있습니다. 저장된 패키지는 수동으로 삭제해야 합니다.

이러한 패키지 중 일부는 Microsoft에서 작성되었으며 다른 항목은 PowerShell 커뮤니티에서 작성되었습니다.
설치 전에 이 갤러리에 있는 패키지의 내용과 코드를 검토하는 것이 좋습니다.

좋은 의도로 게시되지 않은 것 같은 패키지를 발견할 경우 해당 패키지의 페이지에서 **신고하기**를 클릭합니다.

### <a name="install"></a>설치

사용을 위해 갤러리에서 패키지를 설치하려면 패키지 유형에 따라 [Install-Module][] 또는 [Install-Script][] cmdlet을 실행합니다.

[Install-Module][]은 기본적으로 `$env:ProgramFiles\WindowsPowerShell\Modules`에 모듈을 설치합니다.
이 경우 관리자 계정이 필요합니다. `-Scope CurrentUser` 매개 변수를 추가하는 경우 모듈은 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`에 설치됩니다.

[Install-Script][]는 기본적으로 `$env:ProgramFiles\WindowsPowerShell\Scripts`에 스크립트를 설치합니다.
이 경우 관리자 계정이 필요합니다. `-Scope CurrentUser` 매개 변수를 추가하는 경우 스크립트는 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`에 설치됩니다.

기본적으로 [Install-Module][] 및 [Install-Script][]는 최신 버전의 패키지를 설치합니다.
이전 버전의 패키지를 설치하려면 `-RequiredVersion` 매개 변수를 추가합니다.

### <a name="deploy"></a>배포 게스트 클러스터에

Azure Automation에 PowerShell 갤러리에서 패키지를 배포 하려면 **Azure Automation**, 클릭 **Azure Automation에 배포** 패키지 세부 정보 페이지입니다. Azure 계정 자격 증명을 사용 하 여 로그인 하는 Azure 관리 포털로 리디렉션됩니다. 참고는 종속성을 사용 하 여 패키지 배포 Azure Automation에 모든 종속성을 배포 합니다. 패키지 메타데이터에 **AzureAutomationNotSupported** 태그를 추가하면 Azure Automation에 배포 단추를 해제할 수 있습니다.

Azure Automation에 대한 자세한 내용은 [Azure Automation](/azure/automation) 설명서를 참조하세요.

## <a name="updating-packages-from-the-powershell-gallery"></a>PowerShell 갤러리에서 패키지 업데이트

PowerShell 갤러리에서 설치된 패키지를 업데이트하려면 [Update-Module][] 또는 [Update-Script][] cmdlet을 실행합니다. [Update-module] 실행 하 여 설치 된 모든 모듈을 업데이트 하려고 추가 매개 변수 없이 실행 될 때 [Install-module][]합니다. 모듈을 선택적으로 업데이트하려면 `-Name` 매개 변수를 추가합니다. 

마찬가지로, 추가 매개 변수 없이 실행 될 때 [Update-script] 업데이트 하려고 모든 스크립트를 실행 하 여 설치 [Install-script][]합니다. 스크립트를 선택적으로 업데이트하려면 `-Name` 매개 변수를 추가합니다.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>PowerShell 갤러리에서 설치한 패키지 나열

PowerShell 갤러리에서 설치한 모듈을 찾으려면 [Get-InstalledModule][] cmdlet을 실행합니다. 이 명령은 PowerShell 갤러리에서 직접 설치된 시스템의 모듈을 모두 나열합니다.

마찬가지로, PowerShell 갤러리에서 설치한 스크립트를 찾으려면 [Get-InstalledScript][] cmdlet을 실행합니다. 이 명령은 PowerShell 갤러리에서 직접 설치된 시스템의 스크립트를 모두 나열합니다.

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

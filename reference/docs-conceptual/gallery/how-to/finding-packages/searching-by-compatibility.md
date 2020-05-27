---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: 호환 가능한 PowerShell 버전 또는 운영 체제가 있는 패키지
ms.openlocfilehash: fce1383fa604a555a40b050ce92c5cc45ca7054c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691456"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>호환 가능한 PowerShell 버전 또는 운영 체제가 있는 패키지

버전 5.1부터 PowerShell은 다양한 기능 세트 및 플랫폼 호환성을 나타내는 다양한 버전으로 사용 가능합니다.

## <a name="searching-by-powershell-edition"></a>PowerShell 버전으로 검색

두 버전의 PowerShell은 다음과 같습니다.

- **Desktop Edition:** .NET Framework를 기반으로 구축되며 Server Core 및 Windows Desktop과 같은 전체 버전의 Windows에서 실행되는 PowerShell 버전을 대상으로 지정하는 스크립트 및 모듈과 호환성을 제공합니다.
- **Core Edition:** .NET Framework를 기반으로 구축되며 Nano 서버 및 Windows IoT와 같은 축소된 버전의 Windows에서 실행되는 PowerShell 버전을 대상으로 지정하는 스크립트 및 모듈과 호환성을 제공합니다.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell 갤러리를 사용하면 특정 PowerShell 버전에서 호환 가능한 패키지를 필터링할 수 있습니다.

패키지에서 호환되는 PSEdition을 지정한 경우 패키지 표시 페이지 및 패키지 결과에 'PowerShell 버전'의 일부로 표시됩니다.
PowerShell을 사용하여 호환 가능한 패키지를 검색할 수도 있습니다.

![PSEditions가 있는 항목 표시 페이지](media/searching-by-compatibility/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>PowerShell Core에서 작동하는 패키지 갤러리 UI에서 검색

Tags:"PSEdition_Desktop" 및 Tags:"PSEdition_Core"를 사용하여 PowerShell 갤러리에 있는 패키지를 필터링합니다.

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a>Tags:"PSEdition_Core"를 사용하여 PowerShell Core Edition과 호환되는 항목을 검색합니다.

![Core PSEdition과 호환되는 항목에 대한 검색 결과](media/searching-by-compatibility/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Tags:"PSEdition_Desktop"을 사용하여 PowerShell Desktop Edition과 호환되는 항목을 검색합니다.

![Desktop PSEdition과 호환되는 항목에 대한 검색 결과](media/searching-by-compatibility/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>패키지를 검색하여 PowerShell을 사용하여 호환 가능한 버전 찾기
PowerShell 버전 및 OS에서 필터링할 태그를 지정할 수 있습니다.
`-Tag` 매개 변수를 지정하는 `Find-Package` cmdlet을 사용하여 대상으로 지정한 버전(및 OS)를 지정합니다.
다음과 같이:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>운영 체제로 검색

PowerShell Core가 Windows, Linux 및 MacOS에서 제공되므로 갤러리에 있는 패키지는 이러한 운영 체제 조합에 대해서 설계되었을 것입니다. 갤러리 UI에서 다음 검색 태그를 사용하여 운영 체제별로 태그가 지정된 패키지를 찾을 수 있습니다.

- 태그: "Windows"
- 태그: "Linux"
- 태그: "MacOS"

다음과 같이 `Find-Module`에서 이러한 태그(및 PowerShellGet 모듈의 다른 cmdlet)를 지정할 수 있습니다

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>여러 호환성 검색

다음 구문을 사용하여 여러 호환성을 포함하는 패키지를 찾을 수 있습니다.

태그: "Compatibility1" "Compatibility2"

예를 들어 내 Windows 및 Linux 머신 모두에서 실행되는 PowerShell Core와 호환 가능한 패키지를 찾는 경우 다음 검색 태그를 사용하세요.

태그: "PSEdition_Core" "Windows" "Linux"

PowerShell을 사용하여 검색하려면 다음과 같이 `Find-Module`(및 PowerShellGet 모듈의 다른 cmdlet)을 사용할 수 있습니다.

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>호환되는 PowerShell 버전이 있는 패키지를 작성 및 찾는 방법에 대한 자세한 내용

- [PSEditions가 있는 모듈](../../concepts/module-psedition-support.md)
- [PSEditions가 있는 스크립트](../../concepts/script-psedition-support.md)

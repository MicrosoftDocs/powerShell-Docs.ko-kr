---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: 호환 되는 PowerShell 버전이 나 운영 체제를 사용 하 여 패키지
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747707"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>호환 되는 PowerShell 버전이 또는 운영 체제를 사용 하 여 패키지

버전 5.1부터 PowerShell은 다양한 기능 세트 및 플랫폼 호환성을 나타내는 다양한 버전으로 사용 가능합니다.

## <a name="searching-by-powershell-edition"></a>PowerShell 에디션 별로 검색 
두 버전의 Powershell 다음과 같습니다.
- **Desktop Edition:** .NET Framework를 기반으로 구축되며 Server Core 및 Windows Desktop과 같은 전체 버전의 Windows에서 실행되는 PowerShell 버전을 대상 지정하는 스크립트 및 모듈과 호환성을 제공합니다.
- **Core Edition:** .NET Framework를 기반으로 구축되며 Nano 서버 및 Windows IoT와 같은 축소된 버전의 Windows에서 실행되는 PowerShell 버전을 대상 지정하는 스크립트 및 모듈과 호환성을 제공합니다.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell 갤러리를 사용 하면 특정 PowerShell 버전에 대 한 호환 되는 패키지를 필터링 하려면

패키지에 호환 되는 pseditions가 있는 지정 하면 ' PowerShell 버전 '의 일부로 나열 된 패키지 표시 페이지 및 패키지 결과입니다.
PowerShell을 사용 하 여 호환 가능한 패키지에 대 한 검색할 수 있습니다.

![PSEditions가 있는 항목 표시 페이지](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>갤러리 UI에서에서 PowerShell Core에서 작동 하는 패키지에 대 한 검색

Tags:"PSEdition_Desktop" 및 Tags:"PSEdition_Core"를 사용하여 PowerShell 갤러리에 있는 패키지를 필터링합니다.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Tags:"PSEdition_Core"를 사용하여 PowerShell Core Edition과 호환되는 항목을 검색합니다.

![Core PSEdition과 호환되는 항목에 대한 검색 결과](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Tags:"PSEdition_Desktop"을 사용하여 PowerShell Desktop Edition과 호환되는 항목을 검색합니다.

![Desktop PSEdition과 호환되는 항목에 대한 검색 결과](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>PowerShell을 사용 하 여 호환 버전을 찾으려면 패키지 검색
PowerShell 버전 및 OS에 대해 필터링 할 태그를 지정할 수 있습니다. 사용할 합니다 `Find-Package` cmdlet을 지정 하는 `-Tag` 버전 (및 OS)를 지정 하려면 매개 변수 대상으로 하는 합니다.
이런 식으로:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>운영 체제에서 검색 

PowerShell Core를 Windows, Linux 및 MacOS에 대해 사용할 수 있으므로 이러한 운영 체제의 모든 조합에 대 한 갤러리에서 패키지 디자인 됩니다. 갤러리 UI에서에서 운영 체제에서 태그가 지정 된 패키지를 찾을 수 다음 searchs 태그를 사용 합니다.

- 태그: "Windows"
- 태그: "Linux"
- 태그: "MacOS" 

이러한 태그를 지정할 수 있습니다 `Find-Module` (및 PowerShellGet 모듈의 다른 cmdlet)을 다음과 같이 합니다.

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>여러 호환성에 대 한 검색

구문을 사용 하 여 여러 호환성에는 패키지를 찾을 수 있습니다. 

태그 "Compatibility1" "Compatibility2" 

예를 들어, 내 Windows 및 Linux 컴퓨터에서 실행 되는 PowerShell Core 호환성을 사용 하 여 패키지를 찾고 검색 태그를 사용 합니다.

태그 "PSEdition_Core" "Windows" "Linux" 

PowerShell을 사용 하 여 검색을 사용할 수 있습니다는 `Find-Module` (및 PowerShellGet 모듈의 다른 cmdlet)이 같은:

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>호환되는 PowerShell 버전이 있는 패키지를 작성 및 찾는 방법에 대한 자세한 내용

- [PSEditions가 있는 모듈](../../concepts/module-psedition-support.md)
- [PSEditions가 있는 스크립트](../../concepts/script-psedition-support.md)

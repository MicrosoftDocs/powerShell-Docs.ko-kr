---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,psgallery
title: 수동 패키지 다운로드
ms.openlocfilehash: c0a96e866dfd27f9b2170ea540ec6dd0c67701fd
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215456"
---
# <a name="manual-package-download"></a>수동 패키지 다운로드

PowerShell 갤러리는 PowerShellGet cmdlet을 사용하지 않고 웹 사이트에서 패키지를 직접 다운로드하도록 지원합니다. 모든 패키지를 NuGet 패키지(`.nupkg`) 파일로 다운로드한 다음, 내부 리포지토리에 복사할 수 있습니다.

> [!NOTE]
> 수동 패키지 다운로드는 `Install-Module` cmdlet을 대체하기 위한 것이 **아닙니다**.
> 패키지를 다운로드해도 모듈이나 스크립트는 설치되지 않습니다. 종속성은 다운로드한 NuGet 패키지에 포함되어 있지 않습니다. 다음은 참조 목적으로만 제공되는 지침입니다.

## <a name="using-manual-download-to-acquire-a-package"></a>수동 다운로드를 사용하여 패키지 가져오기

각 페이지에는 다음과 같은 [수동 다운로드] 링크가 있습니다.

![수동 다운로드](../../Images/packagedisplaypagewithpseditions.png)

수동으로 다운로드하려면 **원시 nupkg 파일 다운로드**를 클릭합니다. 이 패키지의 복사본은 이름이 `<name>.<version>.nupkg`인 브라우저의 다운로드 폴더에 복사됩니다.

NuGet 패키지는 패키지의 콘텐츠에 대한 정보가 포함된 추가 파일이 있는 ZIP 보관 패키지입니다. Internet Explorer와 같은 일부 브라우저에서는 자동으로 `.nupkg` 파일 확장명을 `.zip`으로 바꿉니다. 패키지를 확장하려면 필요한 경우 `.nupkg` 파일의 이름을 `.zip`으로 바꾼 다음, 로컬 폴더에 콘텐츠를 추출합니다.

NuGet 패키지 파일에는 원래 패키지된 코드의 일부가 아닌 다음 **NuGet 관련 요소**가 포함되어 있습니다.

- `_rels` 폴더 - 종속성을 나열하는 `.rels` 파일이 있습니다
- `package` 폴더 - NuGet 관련 데이터가 있습니다.
- `[Content_Types].xml` 파일 - PowerShellGet과 같은 확장명이 NuGet에서 작동하는 방식을 설명합니다.
- `<name>.nuspec` 파일 - 대량의 메타데이터가 있습니다.

## <a name="installing-powershell-modules-from-a-nuget-package"></a>NuGet 패키지에서 PowerShell 모듈 설치

> [!NOTE]
> 이러한 지침은 `Install-Module`를 실행하는 것과 동일한 결과를 **제공하지 않으며**, 최소 요구 사항을 충족합니다. 이는 `Install-Module`을 대체하기 위한 것이 아닙니다.
> `Install-Module`에서 수행되는 일부 단계는 포함되지 않습니다.

가장 쉬운 방법은 폴더에서 NuGet 관련 요소를 제거하는 것입니다. 요소를 제거해도 패키지 작성자가 만든 PowerShell 코드가 그대로 유지됩니다.
NuGet 관련 요소 목록은 [수동 다운로드를 사용하여 패키지 가져오기](#using-manual-download-to-acquire-a-package)를 참조하세요.

단계는 다음과 같습니다.

1. 로컬 폴더에 NuGet 패키지의 콘텐츠를 추출합니다.
2. 폴더에서 NuGet 관련 요소를 삭제합니다.
3. 폴더 이름을 바꿉니다. 기본 폴더 이름은 일반적으로 `<name>.<version>`입니다. 태그가 시험판 버전으로 지정된 모듈인 경우 버전에 `-prerelease`가 포함될 수 있습니다. 폴더 이름을 모듈 이름으로만 바꿉니다. 예를 들어 `azurerm.storage.5.0.4-preview`는 `azurerm.storage`가 됩니다.
4. 폴더를 `$env:PSModulePath value`에 있는 폴더 중 하나로 복사합니다. `$env:PSModulePath`는 세미콜론으로 구분된 일련의 경로이고, PowerShell은 여기에서 모듈을 찾아야 합니다.

> [!IMPORTANT]
> 수동 다운로드에는 모듈에 필요한 종속성이 포함되어 있지 않습니다. 패키지에 종속성이 있는 경우 이 모듈이 제대로 작동하려면 시스템에 해당 패키지를 설치해야 합니다. PowerShell 갤러리에는 패키지에 필요한 모든 종속성이 표시됩니다.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>NuGet 패키지에서 PowerShell 스크립트 설치

> [!NOTE]
> 이러한 지침은 `Install-Script`를 실행하는 것과 동일한 결과를 **제공하지 않으며**, 최소 요구 사항을 충족합니다. 이는 `Install-Script`를 대체하기 위한 것이 아닙니다.

가장 쉬운 방법은 NuGet 패키지를 추출한 다음, 스크립트를 직접 사용하는 것입니다.

단계는 다음과 같습니다.

1. NuGet 패키지의 콘텐츠를 추출합니다.
2. 폴더의 `.PS1` 파일을 이 위치에서 직접 사용할 수 있습니다.
3. 폴더에 있는 NuGet 관련 요소를 삭제할 수 있습니다.

NuGet 관련 요소 목록은 [수동 다운로드를 사용하여 패키지 가져오기](#using-manual-download-to-acquire-a-package)를 참조하세요.

> [!IMPORTANT]
> 수동 다운로드에는 모듈에 필요한 종속성이 포함되어 있지 않습니다. 패키지에 종속성이 있는 경우 이 모듈이 제대로 작동하려면 시스템에 해당 패키지를 설치해야 합니다. PowerShell 갤러리에는 패키지에 필요한 모든 종속성이 표시됩니다.

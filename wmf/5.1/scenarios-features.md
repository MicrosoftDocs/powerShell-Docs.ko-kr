---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1의 새로운 시나리오 및 기능
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: 50b66cada6943784b8d3c103cebc3c1e3e286a16
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37090366"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>WMF 5.1의 새로운 시나리오 및 기능

> 참고: 이 정보는 임시로 제공되며 변경될 수 있습니다.

## <a name="powershell-editions"></a>PowerShell 버전

버전 5.1부터 PowerShell은 다양한 기능 집합 및 플랫폼 호환성을 나타내는 다양한 버전으로 사용 가능합니다.

- **Desktop Edition:** .NET Framework에서 구축되며 Server Core 및 Windows 데스크톱과 같은 전체 설치 공간 버전의 Windows에서 실행되는 PowerShell 버전을 대상으로 하는 스크립트 및 모듈과의 호환성을 제공합니다.
- **Core Edition:** .NET Core에서 구축되며 Nano Server 및 Windows IoT와 같은 축소된 설치 공간 버전의 Windows에서 실행되는 PowerShell 버전을 대상으로 하는 스크립트 및 모듈과의 호환성을 제공합니다.

**PowerShell 버전 사용 방법에 대한 자세한 정보**

- [$PSVersionTable을 사용하여 실행 중인 PowerShell 버전 확인](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [PSEdition 매개 변수를 사용하여 CompatiblePSEditions를 기준으로 Get-Module 결과 필터링](/powershell/module/microsoft.powershell.core/get-module)
- [호환되는 PowerShell 버전에서 실행하지 않는 경우 스크립트 실행 방지](/powershell/gallery/concepts/script-psedition-support)
- [특정 PowerShell 버전에 대한 모듈의 호환성 선언](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a>카탈로그 Cmdlet

두 개의 새로운 cmdlet을 [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) 모듈에 추가했습니다. 이 cmdlet은 Windows 카탈로그 파일을 생성하고 유효성을 검사합니다.

### <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

New-FileCatalog는 폴더 및 파일 집합에 대한 Windows 카탈로그 파일을 생성합니다.
이 카탈로그 파일에는 지정된 경로에 있는 모든 파일에 대한 해시가 포함됩니다.
사용자는 폴더 집합을 이러한 폴더를 나타내는 해당 카탈로그 파일과 함께 배포할 수 있습니다.
이 정보는 카탈로그 생성 시간 이후 폴더가 변경되었는지 확인하는 데 유용합니다.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

카탈로그 버전 1과 2가 지원됩니다.
버전 1은 SHA1 해시 알고리즘을 사용하여 파일 해시를 만들고 버전 2는 SHA256을 사용합니다.
*Windows Server 2008 R2* 또는 *Windows 7*에서는 카탈로그 버전 2가 지원되지 않습니다.
*Windows 8*, *Windows Server 2012* 및 이후 운영 체제에서는 카탈로그 버전 2를 사용해야 합니다.

![](../images/NewFileCatalog.jpg)

이 cmdlet은 카탈로그 파일을 만듭니다.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

카탈로그 파일(위 예에서는 Pester.cat)의 무결성을 확인하려면 [Set-authenticodesignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet을 사용하여 카탈로그 파일에 서명합니다.

### <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

Test-FileCatalog는 폴더 집합을 나타내는 카탈로그의 유효성을 검사합니다.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

이 cmdlet은 *카탈로그*에서 찾은 모든 파일 해시 및 해당 상대 경로를 *디스크*의 파일 해시 및 상대 경로와 비교합니다.
파일 해시 및 경로 간의 불일치를 발견하면 *ValidationFailed*와 같은 상태를 반환합니다.
사용자는 *-Detailed* 매개 변수를 사용하여 이 모든 정보를 검색할 수 있습니다.
또한 이 cmdlet은 카탈로그 파일에서 [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet을 호출할 때와 동일한 *Signature* 속성에 카탈로그의 서명 상태를 표시합니다.
사용자는 *-FilesToSkip* 매개 변수를 사용하여 유효성 검사 시 파일을 건너뛸 수도 있습니다.

## <a name="module-analysis-cache"></a>모듈 분석 캐시

WMF 5.1부터 PowerShell에서는 내보내는 명령과 같은 모듈에 대한 데이터를 캐시하는 데 사용되는 파일을 제어할 수 있습니다.

기본적으로 이 캐시 파일은 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 파일에 저장됩니다.
일반적으로 이 캐시는 시작 시 명령을 검색할 때 읽으며 모듈을 가져오고 잠시 후에 백그라운드 스레드에서 기록됩니다.

캐시의 기본 위치를 변경하려면 PowerShell을 시작하기 전에 `$env:PSModuleAnalysisCachePath` 환경 변수를 설정합니다.
이 환경 변수의 변경 내용은 자식 프로세스에만 적용됩니다.
PowerShell이 파일을 만들고 쓸 수 있는 전체 경로(파일 이름 포함)를 값으로 지정해야 합니다.
파일 캐시를 사용하지 않도록 설정하려면 이 값을 다음과 같은 잘못된 위치로 설정합니다.

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

이렇게 하면 잘못된 디바이스에 대한 경로가 설정됩니다.
PowerShell에서 경로에 쓸 수 없는 경우 오류가 반환되지 않지만 추적 프로그램을 사용하여 오류 보고를 확인할 수 있습니다.

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

캐시를 쓸 때 PowerShell에서는 캐시가 불필요하게 커지지 않도록 더 이상 없는 모듈을 확인합니다.
때로는 이러한 확인이 필요하지 않을 수도 있으며, 이 경우 다음을 설정하여 확인을 끌 수 있습니다.

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

이 환경 변수를 설정하면 현재 프로세스에 즉시 적용됩니다.

## <a name="specifying-module-version"></a>모듈 버전 지정

WMF 5.1에서 `using module`은 PowerShell에서 다른 모듈 관련 생성과 동일하게 동작합니다.
이전에는 특정 모듈 버전을 지정할 수 없었습니다. 따라서 여러 버전이 있는 경우 오류가 발생했습니다.

WMF 5.1에서는 다음과 같습니다.

- [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)(ModuleSpecification 생성자(해시 테이블))를 사용할 수 있습니다.
이 해시 테이블은 `Get-Module -FullyQualifiedName`과 형식이 같습니다.

**예:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- 모듈의 여러 버전이 있는 경우 PowerShell에서는 `Import-Module`과 **동일한 해결 논리**를 사용하고 오류가 발생하지 않습니다. 동작은 `Import-Module` 및 `Import-DscResource`와 동일합니다.

## <a name="improvements-to-pester"></a>Pester의 향상된 기능

WMF 5.1에서는 PowerShell과 함께 제공되는 Pester 버전이 3.3.5에서 3.4.0으로 업데이트되었고, Nano Server에서 Pester가 더 잘 동작할 수 있도록 커밋 https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e가 추가되었습니다.

[https://github.com/pester/Pester/blob/master/CHANGELOG.md](https://github.com/pester/Pester/blob/master/CHANGELOG.md)에서 ChangeLog.md 파일을 검사하여 버전 3.3.5~3.4.0의 변경 내용을 검토할 수 있습니다.

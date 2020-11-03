---
description: Windows PowerShell 5.1에 포함 된 새로운 기능에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/17/2018
online version: https://docs.microsoft.com/powershell/module/?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_5.1
ms.openlocfilehash: 567af048dd137c0287c6eba4ccc42a77055c0c92
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224906"
---
# <a name="about_windows_powershell_51"></a>about_Windows_PowerShell_5.1

## <a name="short-description"></a>간단한 설명

Windows PowerShell 5.1에 포함 된 새로운 기능에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

Windows PowerShell 5.1에는 사용을 확장 하 고, 유용성을 개선 하 고, Windows 기반 환경을 보다 쉽게 포괄적으로 제어 하 고 관리할 수 있는 중요 한 새로운 기능이 포함 되어 있습니다.

Windows PowerShell 5.1은 이전 버전과 호환 됩니다. Windows PowerShell 4.0, Windows PowerShell 3.0 및 Windows PowerShell 2.0 용으로 설계 된 cmdlet, 공급자, 모듈, 스냅인, 함수 및 프로필은 일반적으로 Windows PowerShell 5.1에서 변경 없이 작동 합니다.

- 새 cmdlet: 로컬 사용자 및 그룹; Get-ComputerInfo
- 서명된 모듈, JEA 모듈 설치 등의 PowerShellGet 개선 사항
- PackageManagement에서 컨테이너, CBS 설치, EXE 기반 설치, CAB 패키지에 대한 지원 추가
- DSC 및 PowerShell 클래스에 대한 디버깅 개선 사항
- 끌어오기 서버에서 나오는 카탈로그 서명 모듈 적용 및 PowerShellGet cmdlet을 사용할 경우를 비롯한 보안 향상
- 다양한 사용자 요청 및 문제에 대한 응답

Windows PowerShell 5.1은 windows Server 2016 및 Windows 10에 기본적으로 설치 됩니다. Windows Server 2012 R2, Windows 8.1 Enterprise 또는 Windows 8.1 Pro에서 Windows PowerShell 5.1을 설치 하려면 [WMF 5.1 설치 및 구성](/powershell/scripting/wmf/setup/install-configure)을 참조 하세요.
Windows Management Framework 5.1을 설치 하기 전에 다운로드 정보를 읽고 모든 시스템 요구 사항을 충족 해야 합니다.

Windows [powershell의 새로운 기능](/powershell/scripting/windows-powershell/whats-new/what-s-new-in-windows-powershell-50)에서 windows powershell 5.1에 대 한 변경 내용을 읽을 수도 있습니다.

## <a name="new-scenarios-and-features-in-wmf-51"></a>WMF 5.1의 새로운 시나리오 및 기능

> 참고: 이 정보는 임시로 제공되며 변경될 수 있습니다.

### <a name="powershell-editions"></a>PowerShell Edition
버전 5.1부터 PowerShell은 다양한 기능 집합 및 플랫폼 호환성을 나타내는 다양한 버전으로 사용 가능합니다.

- **Desktop Edition:** .NET Framework를 기반으로 구축되며 Server Core 및 Windows Desktop과 같은 전체 버전의 Windows에서 실행되는 PowerShell 버전을 대상 지정하는 스크립트 및 모듈과 호환성을 제공합니다.
- **Core Edition:** .NET Framework를 기반으로 구축되며 Nano 서버 및 Windows IoT와 같은 축소된 버전의 Windows에서 실행되는 PowerShell 버전을 대상 지정하는 스크립트 및 모듈과 호환성을 제공합니다.

**PowerShell 버전 사용 방법에 대한 자세한 정보**

- [$PSVersionTable을 사용하여 실행 중인 PowerShell 버전 확인](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [PSEdition 매개 변수를 사용하여 CompatiblePSEditions를 기준으로 Get-Module 결과 필터링](/powershell/module/microsoft.powershell.core/get-module)
- [호환되는 PowerShell 버전에서 실행하지 않는 경우 스크립트 실행 방지](/powershell/scripting/gallery/concepts/script-psedition-support)
- [특정 PowerShell 버전에 대한 모듈의 호환성 선언](/powershell/scripting/gallery/concepts/module-psedition-support)

### <a name="catalog-cmdlets"></a>카탈로그 Cmdlet

두 개의 새로운 cmdlet을 [Microsoft.PowerShell.Security](/previous-versions/windows/powershell-scripting/hh847877(v=wps.640)) 모듈에 추가했습니다. 이 cmdlet은 Windows 카탈로그 파일을 생성하고 유효성을 검사합니다.

#### <a name="new-filecatalog"></a>New-FileCatalog

New-FileCatalog는 폴더 및 파일 집합에 대한 Windows 카탈로그 파일을 생성합니다.
이 카탈로그 파일에는 지정된 경로에 있는 모든 파일에 대한 해시가 포함됩니다. 사용자는 폴더 집합을 이러한 폴더를 나타내는 해당 카탈로그 파일과 함께 배포할 수 있습니다. 이 정보는 카탈로그 생성 시간 이후 폴더가 변경되었는지 확인하는 데 유용합니다.

```
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>]
 [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

카탈로그 버전 1과 2가 지원됩니다. 버전 1은 SHA1 해시 알고리즘을 사용하여 파일 해시를 만들고 버전 2는 SHA256을 사용합니다. *Windows Server 2008 R2* 또는 *Windows 7* 에서는 카탈로그 버전 2가 지원되지 않습니다. *Windows 8* , *Windows Server 2012* 및 이후 운영 체제에서는 카탈로그 버전 2를 사용해야 합니다.

카탈로그 파일(위 예에서는 Pester.cat)의 무결성을 확인하려면 [Set-authenticodesignature](/powershell/module/microsoft.powershell.security/set-authenticodesignature) cmdlet을 사용하여 카탈로그 파일에 서명합니다.

#### <a name="test-filecatalog"></a>Test-FileCatalog

Test-FileCatalog는 폴더 집합을 나타내는 카탈로그의 유효성을 검사합니다.

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>]
 [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

이 cmdlet은 *카탈로그* 에서 찾은 모든 파일 해시 및 해당 상대 경로를 *디스크* 의 파일 해시 및 상대 경로와 비교합니다. 파일 해시 및 경로 간의 불일치를 발견하면 *ValidationFailed* 와 같은 상태를 반환합니다. 사용자는 *-Detailed* 매개 변수를 사용하여 이 모든 정보를 검색할 수 있습니다. 또한 이 cmdlet은 카탈로그 파일에서 [Get-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/get-authenticodesignature) cmdlet을 호출할 때와 동일한 *Signature* 속성에 카탈로그의 서명 상태를 표시합니다. 사용자는 *-FilesToSkip* 매개 변수를 사용하여 유효성 검사 시 파일을 건너뛸 수도 있습니다.

### <a name="module-analysis-cache"></a>모듈 분석 캐시

WMF 5.1부터 PowerShell에서는 내보내는 명령과 같은 모듈에 대한 데이터를 캐시하는 데 사용되는 파일을 제어할 수 있습니다.

기본적으로 이 캐시 파일은 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 파일에 저장됩니다. 일반적으로 이 캐시는 시작 시 명령을 검색할 때 읽으며 모듈을 가져오고 잠시 후에 백그라운드 스레드에서 기록됩니다.

캐시의 기본 위치를 변경하려면 PowerShell을 시작하기 전에 `$env:PSModuleAnalysisCachePath` 환경 변수를 설정합니다. 이 환경 변수의 변경 내용은 자식 프로세스에만 적용됩니다. PowerShell이 파일을 만들고 쓸 수 있는 전체 경로(파일 이름 포함)를 값으로 지정해야 합니다. 파일 캐시를 사용하지 않도록 설정하려면 이 값을 다음과 같은 잘못된 위치로 설정합니다.

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

이렇게 하면 잘못된 디바이스에 대한 경로가 설정됩니다. PowerShell에서 경로에 쓸 수 없는 경우 오류가 반환되지 않지만 추적 프로그램을 사용하여 오류 보고를 확인할 수 있습니다.

```powershell
Trace-Command -PSHost -Name Modules -Expression {
  Import-Module Microsoft.PowerShell.Management -Force
}
```

캐시를 쓸 때 PowerShell에서는 캐시가 불필요하게 커지지 않도록 더 이상 없는 모듈을 확인합니다. 때로는 이러한 확인이 필요하지 않을 수도 있으며, 이 경우 다음을 설정하여 확인을 끌 수 있습니다.

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

이 환경 변수를 설정하면 현재 프로세스에 즉시 적용됩니다.

### <a name="specifying-module-version"></a>모듈 버전 지정

WMF 5.1에서 `using module`은 PowerShell에서 다른 모듈 관련 생성과 동일하게 동작합니다. 이전에는 특정 모듈 버전을 지정할 수 없었습니다. 따라서 여러 버전이 있는 경우 오류가 발생했습니다.

WMF 5.1에서는 다음과 같습니다.

* [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor)(ModuleSpecification 생성자(해시 테이블))를 사용할 수 있습니다.
  이 해시 테이블은 `Get-Module -FullyQualifiedName`과 형식이 같습니다.

  **예제:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* 모듈의 여러 버전이 있는 경우 PowerShell에서는 `Import-Module`과 **동일한 해결 논리** 를 사용하고 오류가 발생하지 않습니다. 동작은 `Import-Module` 및 `Import-DscResource`와 동일합니다.

### <a name="improvements-to-pester"></a>Pester의 향상된 기능

WMF 5.1에서는 PowerShell과 함께 제공 되는 Pester 버전이 3.3.5에서 3.4.0로 업데이트 되었으며, GitHub [PR # 484](https://github.com/pester/Pester/pull/484)을 추가 하 여 Nano Server에서 Pester의 더 나은 동작을 사용할 수 있습니다.

[https://github.com/pester/Pester/blob/master/CHANGELOG.md](https://github.com/pester/Pester/blob/master/CHANGELOG.md)에서 ChangeLog.md 파일을 검사하여 버전 3.3.5~3.4.0의 변경 내용을 검토할 수 있습니다.

## <a name="keywords"></a>어

Windows PowerShell 5.1의 새로운 기능

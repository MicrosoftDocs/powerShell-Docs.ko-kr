---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a0b1573611c5d4232082c19ca19b4cca79d0699e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057471"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>PowerShellGet을 사용하여 PowerShell 모듈 검색, 설치 및 인벤토리에 추가

PowerShellGet은 이번 WMF 릴리스에 포함됩니다.
-   Find-Module은 -Tag 매개 변수를 사용하여 모듈 메타데이터를 필터링할 수 있습니다.
-   Find-Module은 -Filter 매개 변수를 사용하여 리포지토리 관련 검색 언어를 필터링할 수 있습니다.
-   Find-Module은 -Command, -DscResource 및 -Includes 매개 변수를 사용하여 모듈 콘텐츠를 기반으로 필터링할 수 있습니다.
-   Find-DscResource는 리포지토리에서 개별 DSC 리소스의 검색을 허용합니다.
-   NuGet을 사용하여 파일 공유에서 설치 및 파일 공유에 게시를 지원합니다.

## <a name="example-commands"></a>예제 명령
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a>PowerShellGet의 새로운 기능
-   Windows PowerShell 5.0 이상에서 Side-by-side 버전 지원
-   모듈 종속성 설치 지원
-   세 가지 새로운 cmdlet
    -   Get-InstalledModule
    -   Uninstall-Module
    -   Save-Module

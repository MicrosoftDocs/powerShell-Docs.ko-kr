---
ms.date: 11/06/2018
title: 로컬 PSRepository 작업
description: PowerShellGet 모듈은 PowerShell 갤러리 이외의 리포지토리를 지원합니다. 이 문서에서는 로컬 PowerShell 리포지토리를 설정하는 방법을 설명합니다.
ms.openlocfilehash: 24a2fd23124b3897952d64a347d103d9ee10248f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662360"
---
# <a name="working-with-private-powershellget-repositories"></a>프라이빗 PowerShellGet 리포지토리 작업

PowerShellGet 모듈은 PowerShell 갤러리 이외의 리포지토리를 지원합니다.
이 cmdlet을 통해 다음 시나리오가 가능해집니다.

- 사용자 환경에서 사용할 신뢰할 수 있는 미리 유효성 검사된 PowerShell 모듈 세트 지원
- PowerShell 모듈 또는 스크립트를 빌드하는 CI/CD 파이프라인 테스트
- 인터넷에 액세스할 수 없는 시스템에 PowerShell 스크립트 및 모듈 전달
- 조직에서만 사용할 수 있는 PowerShell 스크립트 및 모듈 전달

이 문서에서는 로컬 PowerShell 리포지토리를 설정하는 방법을 설명합니다. 또한 PowerShell 갤러리에서 사용할 수 있는 [OfflinePowerShellGetDeploy][] 모듈을 다룹니다. 이 모듈에는 최신 버전의 PowerShellGet을 로컬 리포지토리에 설치하는 cmdlet이 포함됩니다.

## <a name="local-repository-types"></a>로컬 리포지토리 유형

로컬 PSRepository를 만드는 두 가지 방법은 NuGet 서버 또는 파일 공유입니다. 각 유형에는 다음과 같은 장단점이 있습니다.

### <a name="nuget-server"></a>NuGet 서버

| 장점| 단점 |
| --- | --- |
| Powershell 갤러리 기능을 최대한 가깝게 모방 | 다중 계층 앱에 작업 계획 및 지원 필요 |
| NuGet이 Visual Studio, 기타 도구에 통합 | 인증 모델 및 NuGet 계정 관리 필요 |
| NuGet이 `.Nupkg` 패키지의 메타데이터 지원 | 게시에 API 키 관리 및 유지 관리 필요 |
| 검색, 패키지 관리 등 제공 | |

### <a name="file-share"></a>파일 공유

| 장점| 단점 |
| --- | --- |
| 간편한 설정, 백업 및 유지 관리 | PowerShellGet에서 사용되는 메타데이터를 사용할 수 없음 |
| 간단한 보안 모델 - 공유에 대한 사용자 권한 | 기본 파일 공유 이외의 UI 없음 |
| 기존 항목 바꾸기와 같은 제약 조건 없음 | 제한된 보안 및 누가 무엇을 업데이트하는지에 대한 기록 없음 |

PowerShellGet은 하나의 유형을 사용하고 버전 찾기 및 종속성 설치를 지원합니다.
그러나 PowerShell 갤러리에서 작동하는 일부 기능은 기본 NuGet 서버 또는 파일 공유에 사용할 수 없습니다.

- 모든 것이 패키지로 제공 - 스크립트, 모듈, DSC 리소스 또는 역할 기능의 구별 없음
- 파일 공유 서버에서는 태그를 포함한 패키지 메타데이터를 볼 수 없습니다.

## <a name="creating-a-local-repository"></a>로컬 리포지토리 만들기

다음 문서에는 고유한 NuGet 서버를 설정하는 단계가 나와 있습니다.

- [NuGet.Server][]

패키지를 추가하는 지점까지 단계를 수행합니다. [패키지 게시](#publishing-to-a-local-repository) 단계는 이 문서의 뒷부분에서 설명합니다.

파일 공유 기반 리포지토리의 경우 사용자에게 파일 공유에 액세스할 권한이 있는지 확인합니다.

## <a name="registering-a-local-repository"></a>로컬 리포지토리 등록

리포지토리를 사용하려면 먼저 `Register-PSRepository` 명령을 사용하여 리포지토리를 등록해야 합니다.
아래 예제에서는 고유한 리포지토리를 신뢰한다고 가정하여 **InstallationPolicy** 가 *Trusted* 로 설정됩니다.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

두 가지 명령이 **ScriptSourceLocation** 을 처리하는 방식의 차이에 주의하세요. 파일 공유 기반 리포지토리의 경우 **SourceLocation** 및 **ScriptSourceLocation** 이 일치해야 합니다. 웹 기반 리포지토리의 경우 두 항목이 달라야 하므로, 이 예제에서는 후행 "/"가 **SourceLocation** 에 추가됩니다.

새로 생성된 PSRepository를 기본 리포지토리로 설정하려면 모든 다른 PSRepository를 등록 취소해야 합니다. 다음은 그 예입니다.

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> 리포지토리 이름 'PSGallery'는 PowerShell 갤러리에서 사용하도록 예약되었습니다. PSGallery를 등록 취소할 수 있지만 이름 PSGallery를 다른 리포지토리에 사용할 수는 없습니다.

PSGallery를 복원해야 할 경우 다음 명령을 실행합니다.

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>로컬 리포지토리 게시

로컬 PSRepository를 등록한 후 로컬 PSRepository에 게시할 수 있습니다. 두 가지 기본 게시 시나리오는 고유한 모듈을 게시하는 것과 PSGallery에서 모듈을 게시하는 것입니다.

### <a name="publishing-a-module-you-authored"></a>직접 작성한 모듈 게시

`Publish-Module` 및 `Publish-Script`를 사용하여 PowerShell 갤러리에 게시한 것과 동일한 방법으로 로컬 PSRepository에 모듈을 게시합니다.

- 코드 위치 지정
- API 키 제공
- 리포지토리 이름을 지정합니다. 예를 들어 `-PSRepository LocalPSRepo`

> [!NOTE]
> NuGet 서버에서 계정을 만든 후 로그인하여 API 키를 생성하고 저장해야 합니다.
> 파일 공유의 경우 NuGetApiKey 값에 비어 있지 않은 문자열을 사용합니다.

예제:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey $nuGetApiKey
```

> [!IMPORTANT]
> 보안을 적용하려면 API 키가 스크립트에서 하드 코드되지 않아야 합니다. 보안 키 관리 시스템을 사용합니다. 명령을 수동으로 실행하는 경우 기록을 방지하기 위해 API 키를 일반 텍스트로 전달하면 안 됩니다. `Read-Host` cmdlet을 사용하여 API 키 값을 안전하게 전달할 수 있습니다.

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

### <a name="publishing-a-module-from-the-psgallery"></a>PSGallery에서 모듈 게시

PSGallery의 모듈을 로컬 PSRepository에 게시하려면 'Save-Package' cmdlet을 사용하면 됩니다.

- 패키지 이름 지정
- 'NuGet'을 공급자로 지정
- PSGallery 위치를 원본으로 지정(https://www.powershellgallery.com/api/v2)
- 로컬 리포지토리의 경로 지정

예:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

로컬 PSRepository가 웹 기반인 경우 게시할 때 nuget.exe를 사용하는 추가 단계가 필요합니다.

[nuget.exe][] 사용에 대한 설명서를 참조하세요.

## <a name="installing-powershellget-on-a-disconnected-system"></a>연결이 끊어진 시스템에 PowerShellGet 설치

시스템에서 인터넷 연결이 끊어져야 하는 환경에는 PowerShellGet을 배포하는 것이 어렵습니다. PowerShellGet에는 처음 사용될 때 최신 버전을 설치하는 부트스트랩 프로세스가 있습니다. PowerShell 갤러리의 OfflinePowerShellGetDeploy 모듈은 부트스트랩 프로세스를 지원하는 cmdlet을 제공합니다.

오프라인 배포를 부트스트랩하려면 다음을 수행해야 합니다.

- 인터넷에 연결된 시스템 및 연결이 끊어진 시스템에 OfflinePowerShellGetDeploy 다운로드 및 설치
- `Save-PowerShellGetForOffline` cmdlet을 사용하여 인터넷에 연결된 시스템에 PowerShellGet 및 해당 종속성 다운로드
- 인터넷에 연결된 시스템에서 연결이 끊어진 시스템으로 PowerShellGet 및 해당 종속성 복사
- 연결이 끊어진 시스템에서 `Install-PowerShellGetOffline`을 사용하여 PowerShellGet 및 해당 종속성을 적절한 폴더에 저장

다음 명령은 `Save-PowerShellGetForOffline`을 사용하여 모든 구성 요소를 `f:\OfflinePowerShellGet` 폴더에 삽입합니다.

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

이때 `F:\OfflinePowerShellGet`의 콘텐츠를 연결이 끊어진 시스템에서 사용할 수 있도록 설정해야 합니다. `Install-PowerShellGetOffline` cmdlet을 사용하여 연결이 끊어진 시스템에 PowerShellGet을 설치합니다.

> [!NOTE]
> 이 명령을 실행하기 전에 PowerShell 세션에서 PowerShellGet을 실행하지 않는 것이 중요합니다. PowerShellGet이 세션에 로드된 후에는 구성 요소를 업데이트할 수 없습니다. 실수로 PowerShellGet을 시작하는 경우에는 PowerShell을 종료하고 다시 시작합니다.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

이 명령을 실행하면 PowerShellGet을 로컬 리포지토리에 게시할 준비가 됩니다.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey $nuGetApiKey
```

> [!IMPORTANT]
> 보안을 적용하려면 API 키가 스크립트에서 하드 코드되지 않아야 합니다. 보안 키 관리 시스템을 사용합니다. 명령을 수동으로 실행하는 경우 기록을 방지하기 위해 API 키를 일반 텍스트로 전달하면 안 됩니다. `Read-Host` cmdlet을 사용하여 API 키 값을 안전하게 전달할 수 있습니다.

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a>패키지 솔루션을 사용하여 PowerShellGet 리포지토리 호스트

Azure Artifacts와 같은 패키지 솔루션을 사용하여 프라이빗 또는 퍼블릭 PowerShellGet 리포지토리를 호스트할 수도 있습니다. 자세한 내용 및 지침은 [Azure Artifacts 설명서](/azure/devops/artifacts/tutorials/private-powershell-library)를 참조하세요.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference

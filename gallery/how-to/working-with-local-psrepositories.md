---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget,갤러리
title: 로컬 PSRepositories 사용
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682673"
---
# <a name="working-with-local-powershellget-repositories"></a>로컬 PowerShellGet 리포지토리 작업

PowerShell 갤러리 이외의 PowerShellGet 모듈 지원 리포지토리.
이러한 cmdlet을 사용 하는 다음과 같은 시나리오:

- 사용자 환경에서 사용 하기 위해 신뢰할 수 있는, 사전 검증 된 일련의 PowerShell 모듈을 지원
- PowerShell 모듈 또는 스크립트를 작성 하는 CI/CD 파이프라인 테스트
- 인터넷에 액세스할 수 없는 시스템에 PowerShell 스크립트 및 모듈 제공

이 문서에서는 로컬 PowerShell 리포지토리를 설정 하는 방법을 설명 합니다. 문서에 대해서도 설명 합니다 [OfflinePowerShellGetDeploy][] PowerShell 갤러리에서 모듈을 사용할 수 있습니다. 이 모듈에는 로컬 리포지토리를 최신 버전의 PowerShellGet 설치 하기 위한 cmdlet 포함 되어 있습니다.

## <a name="local-repository-types"></a>로컬 저장소 유형

두 가지 방법으로 로컬 PSRepository를 만들려면: NuGet 서버 또는 파일 공유입니다. 각 형식에는 각각 장단점이 있습니다.

NuGet 서버

| 이점| 단점 |
| --- | --- |
| Powershell 갤러리 기능을 최대한 가깝게 모방합니다. | 다중 계층 앱에 필요한 계획 하는 작업 및 지원 |
| Visual Studio 나 다른 도구를 사용 하 여 NuGet 통합 | 인증 모델 및 필요한 NuGet 계정 관리 |
| NuGet 메타 데이터를 지 원하는 `.Nupkg` 패키지 | 게시를 위해 API 키 관리 및 유지 관리 |
| 검색, 패키지 관리 등을 제공합니다. | |

파일 공유

| 이점| 단점 |
| --- | --- |
| 설정, 백업 및 유지 관리 하는 작업을 쉽게 | PowerShellGet에서 사용 하는 메타 데이터를 사용할 수 없습니다. |
| 간단한 보안 모델-사용자의 공유 권한 | 기본 파일 공유 이외의 UI |
| 기존 항목 바꾸기와 같은 제약 조건이 없는 | 제한 된 보안 및 항목을 업데이트 하는 기록 없음 |

PowerShellGet 형식 및 지원 버전 및 종속성 설치를 찾는 중 하나를 사용 하 여 작동 합니다.
그러나 PowerShell 갤러리에 대해 작동 하는 일부 기능은 기본 NuGet 서버 또는 파일 공유에 사용할 수 없습니다.

- 모든 항목은 패키지-스크립트, 모듈, DSC 리소스 또는 역할 기능 차이 없습니다.
- 파일 공유 서버는 태그를 포함 하는 패키지 메타 데이터를 볼 수 없습니다.

## <a name="creating-a-local-repository"></a>로컬 리포지토리 만들기

다음 문서를 사용자 고유의 NuGet 서버를 설정 하는 단계를 나열 합니다.

- [NuGet.Server][]

패키지를 추가 하는 지점까지 단계를 따릅니다. 단계 [패키지 게시](#publishing-to-a-local-repository) 이 문서의 뒷부분에 나와 있습니다.

파일 공유 기반 저장소를 사용자가 파일 공유에 액세스할 수 있는 권한이 있는지 확인 합니다.

## <a name="registering-a-local-repository"></a>로컬 리포지토리 등록

리포지토리를 사용할 수 있습니다, 전에 등록 해야 사용 하 여 `Register-PSRepository` 명령입니다.
아래 예제에서를 **InstallationPolicy** 로 설정 되어 *신뢰할 수 있는*, 사용자 고유의 리포지토리를 신뢰 하는지 가정 합니다.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

두 명령을 처리 하는 방법 간의 차이점을 기록해 **ScriptSourceLocation**합니다. 파일 공유 기반 저장소에 대 한 합니다 **SourceLocation** 하 고 **ScriptSourceLocation** 일치 해야 합니다. 웹을 기반으로 하는 리포지토리에 대 한, 서로 달라 야 따라서이 예제의 후행 "/"에 추가 되는 **SourceLocation**합니다.

기본 리포지토리를 새로 만든된 PSRepository 원한다 면 다른 모든 PSRepositories 등록을 취소 해야 합니다. 예:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> 'PSGallery' 리포지토리 이름은 사용 하 여 PowerShell 갤러리에서 예약 되어 있습니다. PSGallery를 등록 취소할 수 있지만 다른 리포지토리에 대 한 이름을 PSGallery를 다시 사용할 수 없습니다.

PSGallery를 복원 해야 할 경우 다음 명령을 실행 합니다.

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>로컬 리포지토리 게시

로컬 PSRepository에 등록 한 후에 로컬 PSRepository에 게시할 수 있습니다. 두 가지 주요 게시 시나리오: 사용자 고유의 모듈을 게시 하 고 PSGallery에서 모듈을 게시 합니다.

### <a name="publishing-a-module-you-authored"></a>작성 하는 모듈을 게시

사용 하 여 `Publish-Module` 및 `Publish-Script` PowerShell 갤러리에서 수행한 동일한 방식으로 사용자 로컬 PSRepository에 모듈을 게시 합니다.

- 코드의 위치를 지정 합니다.
- API 키를 제공 합니다.
- 리포지토리 이름을 지정 합니다. 예를 들면 `-PSRepository LocalPSRepo`과 같습니다.

> [!NOTE]
> NuGet 서버에서 계정을 만든 다음 생성 하 고 API 키를 저장 하려면 로그인 해야 합니다.
> 파일 공유에 대 한 NuGetApiKey 값에 대 한 모든 비어 있지 않은 문자열을 사용 합니다.

예제:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> 보안을 위해 API 키 아니어야 스크립트에 하드 코딩 합니다. 안전한 키 관리 시스템을 사용 합니다.

### <a name="publishing-a-module-from-the-psgallery"></a>PSGallery에서 모듈을 게시

사용자 로컬 PSRepository PSGallery에서 모듈을 게시 하려면 ' 저장-Package' cmdlet을 사용할 수 있습니다.

- 패키지의 이름을 지정 합니다.
- 'NuGet' 공급자로 지정
- 원본 (로 PSGallery 위치를 지정 합니다. https://www.powershellgallery.com/api/v2)
- 로컬 리포지토리에 대 한 경로 지정 합니다.

예:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

로컬 PSRepository에 웹 기반 이면 게시할 nuget.exe를 사용 하는 추가 단계가 필요 합니다.

사용 하 여 설명서를 참조 하십시오 [nuget.exe][]합니다.

## <a name="installing-powershellget-on-a-disconnected-system"></a>연결이 끊긴된 시스템에서 PowerShellGet 설치

PowerShellGet을 배포 하는 것은 인터넷에서 연결을 끊을 수 시스템을 필요로 하는 환경에서 어렵습니다. PowerShellGet에 처음으로 사용 되는 최신 버전을 설치 하는 부트스트랩 프로세스를 있습니다. PowerShell 갤러리에 있는 OfflinePowerShellGetDeploy 모듈이 부트스트랩 프로세스를 지 원하는 cmdlet을 제공 합니다.

오프 라인 배포를 부트스트랩할 해야 합니다.

- 인터넷 연결 OfflinePowerShellGetDeploy 시스템 및 연결이 끊긴된 시스템 다운로드 및 설치
- PowerShellGet을 사용 하 여 인터넷에 연결 된 시스템에 대 한 종속성을 다운로드 합니다 `Save-PowerShellGetForOffline` cmdlet
- 인터넷에 연결 된 시스템에서 PowerShellGet 및 해당 종속성을 연결이 끊긴된 시스템에 복사
- 사용 된 `Install-PowerShellGetOffline` PowerShellGet 및 해당 종속성을 적합 한 폴더를 배치할 연결이 끊긴된 시스템에서

다음 명령을 사용 하 여 `Save-PowerShellGetForOffline` 폴더에 모든 구성 요소를 배치 하려면 `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

이 시점에서 내용의 해야 `F:\OfflinePowerShellGet` 연결이 끊긴된 시스템에 사용할 수 있습니다. 실행 된 `Install-PowerShellGetOffline` 연결이 끊긴된 시스템에서 PowerShellGet을 설치 하려면 cmdlet.

> [!NOTE]
> PowerShellGet 이러한 명령을 실행 하기 전에 PowerShell 세션에서 실행 하지 않는 것입니다. PowerShellGet을 세션으로 로드 되 면 구성 요소를 업데이트할 수 없습니다. PowerShellGet을 실수로 시작 수행 하는 경우 종료 하 고 PowerShell을 다시 시작 하십시오.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

이러한 명령은 실행 한 후 준비가 PowerShellGet 로컬 리포지토리에 게시 합니다.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> 보안을 위해 API 키 아니어야 스크립트에 하드 코딩 합니다. 안전한 키 관리 시스템을 사용 합니다.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference

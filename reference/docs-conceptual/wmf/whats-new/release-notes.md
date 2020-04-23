---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.x 릴리스 정보
ms.openlocfilehash: 3fc712dbcbe184c60ae248b260c8f6800f111fdd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "79402360"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>WMF(Windows Management Framework) 5.x 릴리스 정보

## <a name="wmf-50-changes"></a>WMF 5.0 변경 내용

- PowerShell 5.0에서는 새 구조적 **정보** 스트림 추가
- 4개의 새 DSC 리소스를 포함하는 DSC의 개선 사항:
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- PowerShell 원격을 통해 역할 기반 관리를 가능하게 하는 충분한 관리 추가
- PowerShell 5.0에서 사용자 정의 클래스 및 열거형을 포함하도록 언어 확장
- PowerShell ISE의 디버깅 기능 향상 및 원격 디버깅 추가
- PowerShellGet 및 PackageManagement 모듈 추가
- PowerShell 스크립트 로깅 및 스크립트 향상
- 암호화 메시지 구문 cmdlet 추가
- WMF 5.0에 Windows용 NetworkSwitchManager 모듈 포함
- Microsoft.PowerShell.ODataUtils 모듈 추가
- SIL(소프트웨어 인벤토리 로깅) 지원 추가
- 사용자 요청 및 문제에 대한 응답으로 신규 또는 업데이트 cmdlet 제공

## <a name="wmf-51-changes"></a>WMF 5.1 변경 내용

WMF 5.1에는 Windows Server 2016과 함께 릴리스된 PowerShell, WMI, WinRM 및 SIL(소프트웨어 인벤토리 로깅) 구성 요소가 포함됩니다. WMF 5.1은 Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 및 2012 R2에 설치할 수 있으며 WMF 5.0보다 개선된 여러 기능을 제공합니다.

- 새로운 cmdlet
- 서명된 모듈, JEA 모듈 설치 등의 PowerShellGet 개선 사항
- PackageManagement에서 컨테이너, CBS 설치, EXE 기반 설치, CAB 패키지에 대한 지원 추가
- DSC 및 PowerShell 클래스에 대한 디버깅 개선 사항
- 끌어오기 서버에서 나오는 카탈로그 서명 모듈 적용 및 PowerShellGet cmdlet을 사용할 경우를 비롯한 보안 향상
- 다양한 사용자 요청 및 문제에 대한 응답

> [!IMPORTANT]
> Windows Server 2008 또는 Windows 7에 WMF 5.1을 설치하기 전에 WMF 3.0이 설치되어 있지 않은지 확인합니다. 자세한 내용은 [Windows Server 2008 R2 SP1 및 Windows 7 SP1에 대한 WMF 5.1 필수 조건](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1)을 참조하세요.

## <a name="powershell-editions"></a>PowerShell 버전

버전 5.1부터 PowerShell은 다양한 기능 집합 및 플랫폼 호환성을 나타내는 다양한 버전으로 사용 가능합니다.

- **Desktop Edition:** .NET Framework를 기반으로 구축되며 Server Core 및 Windows Desktop과 같은 전체 버전의 Windows에서 실행되는 PowerShell 버전을 대상 지정하는 스크립트 및 모듈과 호환성을 제공합니다.
- **Core Edition:** .NET Framework를 기반으로 구축되며 Nano 서버 및 Windows IoT와 같은 축소된 버전의 Windows에서 실행되는 PowerShell 버전을 대상 지정하는 스크립트 및 모듈과 호환성을 제공합니다.

### <a name="learn-more-about-using-powershell-editions"></a>PowerShell 버전 사용 방법에 대한 자세한 정보

- [$PSVersionTable을 사용하여 실행 중인 PowerShell 버전 확인](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [PSEdition 매개 변수를 사용하여 CompatiblePSEditions를 기준으로 Get-Module 결과 필터링](/powershell/module/microsoft.powershell.core/get-module)
- [호환되는 PowerShell 버전에서 실행하지 않는 경우 스크립트 실행 방지](/powershell/scripting/gallery/concepts/script-psedition-support)
- [특정 PowerShell 버전에 대한 모듈의 호환성 선언](/powershell/scripting/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>모듈 분석 캐시

WMF 5.1부터 PowerShell에서는 내보내는 명령과 같은 모듈에 대한 데이터를 캐시하는 데 사용되는 파일을 제어할 수 있습니다.

기본적으로 이 캐시 파일은 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 파일에 저장됩니다. 일반적으로 이 캐시는 시작 시 명령을 검색할 때 읽으며 모듈을 가져오고 잠시 후에 백그라운드 스레드에서 기록됩니다.

캐시의 기본 위치를 변경하려면 PowerShell을 시작하기 전에 `$env:PSModuleAnalysisCachePath` 환경 변수를 설정합니다. 이 환경 변수의 변경 내용은 자식 프로세스에만 적용됩니다. PowerShell이 파일을 만들고 쓸 수 있는 전체 경로(파일 이름 포함)를 값으로 지정해야 합니다. 파일 캐시를 사용하지 않도록 설정하려면 이 값을 다음과 같은 잘못된 위치로 설정합니다.

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

이렇게 하면 잘못된 디바이스에 대한 경로가 설정됩니다. PowerShell에서 경로에 쓸 수 없는 경우 오류가 반환되지 않지만 추적 프로그램을 사용하여 오류 보고를 확인할 수 있습니다.

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

캐시를 쓸 때 PowerShell에서는 캐시가 불필요하게 커지지 않도록 더 이상 없는 모듈을 확인합니다. 때로는 이러한 확인이 필요하지 않을 수도 있으며, 이 경우 다음을 설정하여 확인을 끌 수 있습니다.

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

  **예제:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- 모듈의 여러 버전이 있는 경우 PowerShell에서는 **과** 동일한 해결 논리`Import-Module`를 사용하고 오류가 발생하지 않습니다. 동작은 `Import-Module` 및 `Import-DscResource`와 동일합니다.

## <a name="improvements-to-pester"></a>Pester의 향상된 기능

WMF 5.1에서는 PowerShell과 함께 제공되는 Pester 버전이 3.3.5에서 3.4.0으로 업데이트되었습니다.
이 업데이트는 Nano Server에서 Pester가 더 잘 동작할 수 있습니다.

GitHub 리포지토리에서 [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md)를 검사하여 Pest의 변경 내용을 검토할 수 있습니다.

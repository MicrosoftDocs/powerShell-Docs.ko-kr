---
title: Windows PowerShell 5.1에서 PowerShell 7로 마이그레이션
description: Windows 플랫폼의 PowerShell을 5.1에서 7로 업데이트.
ms.date: 03/25/2020
ms.openlocfilehash: 8f19297bdb4825f3bbd50544dc5737997e3c83e3
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81440495"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a>Windows PowerShell 5.1에서 PowerShell 7로 마이그레이션

클라우드, 온-프레미스 및 하이브리드 환경에 맞게 설계된 PowerShell 7은 다수의 고급 기능과 [새로운 기능](What-s-New-in-PowerShell-70.md)을 갖추고 있습니다.

- Windows PowerShell과 함께 설치 및 실행
- 기존 Windows PowerShell 모듈과의 호환성 향상
- 삼항 연산자 및 `ForEach-Object -Parallel`과 같은 새로운 언어 기능
- 성능 향상
- SSH 기반 원격 기능
- 플랫폼 간 상호 운용성
- Docker 컨테이너에 대한 지원

PowerShell 7은 Windows PowerShell과 함께 작동하므로 배포 전에 손쉽게 여러 버전을 테스트하고 버전 간 비교를 할 수 있습니다. 간편하고 빠르고 안전하게 마이그레이션할 수 있습니다. 실패.

PowerShell 7이 지원되는 Windows 운영 체제는 다음과 같습니다.

- Windows 8.1 및 10
- Windows Server 2012, 2012 R2, 2016, 2019

PowerShell 7은 macOS와 몇 가지 Linux 배포에서도 실행됩니다. 지원되는 운영 체제의 목록과 지원 수명 주기에 대한 정보는 [PowerShell 지원 수명 주기](/powershell/scripting/powershell-support-lifecycle)를 참조하세요.

## <a name="installing-powershell-7"></a>PowerShell 7 설치

유연성을 갖추고 IT, DevOps 엔지니어 및 개발자를 지원하기 위한 PowerShell 7 설치 옵션이 몇 가지 있습니다. 대다수의 경우에 사용되는 설치 옵션을 요약하면 다음과 같습니다.

- [MSI 패키지](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)를 사용해 PowerShell 배포
- [ZIP 패키지](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)를 사용해 PowerShell 배포

> [!NOTE]
> MSI 패키지는 [System Center Configuration Manager(SCCM)](/configmgr/apps/)와 같은 관리 제품으로 배포하고 업데이트할 수 있습니다. [GitHub 릴리스 페이지](https://github.com/PowerShell/PowerShell/releases)에서 패키지를 다운로드합니다.

MSI 패키지를 배포하려면 관리자 권한이 필요합니다. ZIP 패키지는 모든 사용자가 배포할 수 있습니다. ZIP 패키지는 전체 설치로 커밋하기 전에 PowerShell 7을 가장 쉽게 테스트 설치해볼 수 있는 방법입니다.

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a>PowerShell 7을 Windows PowerShell 5.1과 함께 사용

PowerShell 7은 Windows PowerShell 5.1과 함께 사용하도록 설계되었습니다. 다음 기능을 통해 PowerShell에 대한 투자가 보호되고 PowerShell 7로의 마이그레이션이 간편해집니다.

- 별도의 설치 경로와 실행 파일 이름
- 별도의 PSModulePath
- 버전별 프로파일
- 향상된 모듈 호환성
- 새로운 원격 엔드포인트
- 그룹 정책 지원
- 별도의 이벤트 로그

### <a name="separate-installation-path-and-executable-name"></a>별도의 설치 경로와 실행 파일 이름

PowerShell 7은 새 디렉터리에 설치되므로 Windows PowerShell 5.1과 함께 실행됩니다.

버전별 설치 위치:

- Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`
- PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`
- PowerShell 7: `$env:ProgramFiles\PowerShell\7`

경로에 새 위치가 추가되면 Windows PowerShell 5.1 및 PowerShell 7을 모두 실행할 수 있습니다. PowerShell Core 6.x에서 PowerShell 7로 마이그레이션하는 경우 PowerShell 6이 제거되고 경로가 바뀝니다.

Windows PowerShell에서 PowerShell 실행 파일의 이름은 `powershell.exe`입니다. 버전 6 이상에서 실행 파일의 이름은 `pwsh.exe`입니다. 이름을 새로 지정하면 두 버전의 병렬 실행을 지원하기 쉬워집니다.

### <a name="separate-psmodulepath"></a>별도의 PSModulePath

기본적으로 Windows PowerShell 및 PowerShell 7은 다른 위치에 모듈을 저장합니다. PowerShell 7은 `$Env:PSModulePath` 환경 변수로 이 위치들을 결합합니다. 이름에 따라 모듈을 가져올 때 PowerShell은 `$Env:PSModulePath`에서 지정하는 위치를 확인합니다. 이를 통해 PowerShell 7은 코어 및 데스크톱 모듈을 모두 로드할 수 있습니다.

|            설치 범위            |                Windows PowerShell 5.1                 |             PowerShell 7.0             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| PowerShell 모듈                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| 사용자 설치<br>AllUsers 범위    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| 사용자 설치<br>CurrentUser 범위 | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

다음 예에서는 각 버전별로 `$Env:PSModulePath`의 기본값을 보여 줍니다.

- Windows PowerShell 5.1의 경우:

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- PowerShell 7의 경우:

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

PowerShell 7에는 모듈 자동 로드를 제공하기 위한 Windows PowerShell 경로 및 PowerShell 7 경로가 포함되어 있습니다.

> [!NOTE]
> PSModulePath 환경 변수 또는 설치된 사용자 지정 모듈 또는 애플리케이션을 변경한 경우 더 많은 경로가 있을 수 있습니다.

자세한 내용은 [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences)의 `PSModulePath`를 참조하세요.

모듈에 대한 자세한 내용은 [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules)를 참조하세요.

### <a name="separate-profiles"></a>별도의 프로필

PowerShell 프로필은 PowerShell이 시작될 때 실행되는 스크립트입니다. 이 스크립트에서는 명령, 별칭, 함수, 변수, 모듈, PowerShell 드라이브를 추가하여 환경을 사용자 지정합니다. 프로필 스크립트 덕분에 이러한 사용자 지정 항목을 수동으로 다시 만들지 않고도 모든 세션에서 사용할 수 있습니다.

PowerShell 7에서 프로필의 위치를 가리키는 경로가 변경되었습니다.

- Windows PowerShell 5.1에서 프로필의 위치는 `$HOME\Documents\WindowsPowerShell`입니다.
- PowerShell 7에서 프로필의 위치는 `$HOME\Documents\PowerShell`입니다.

프로필 파일 이름도 변경되었습니다.

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

자세한 내용은 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)를 참조하세요.

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a>PowerShell 7의 Windows PowerShell 5.1 모듈과의 호환성

Azure PowerShell, Active Directory 등 Windows PowerShell 5.1에서 사용하는 대부분의 모듈은 이미 PowerShell 7과 함께 작동합니다. 다른 팀과 협력하여 Microsoft Graph, Office 365 등 더 많은 모듈에 대해 기본 PowerShell 7 지원을 추가하는 작업을 계속 진행하고 있습니다. 지원되는 모듈의 현재 목록은 [PowerShell 7 모듈 호환성](/powershell/scripting/whats-new/module-compatibility)을 참조하세요.

> [!NOTE]
> 또한 Windows에서는 호환되지 않는 모듈을 사용하는 사용자가 PowerShell 7로 쉽게 전환할 수 있도록 **UseWindowsPowerShell** 스위치를 `Import-Module`에 추가하였습니다. 이 기능에 대한 자세한 내용은 [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility)를 참조하세요.

### <a name="powershell-remoting"></a>PowerShell 원격 기능

PowerShell 원격 기능을 사용하면 한 대 이상의 원격 컴퓨터에서 어떤 PowerShell 명령이라도 실행할 수 있습니다. 원격 컴퓨터에서 영구 연결을 설정하고, 대화형 세션을 시작하고, 스크립트를 실행할 수 있습니다.

#### <a name="ws-management-remoting"></a>WS-Management 원격 기능

Windows PowerShell 5.1 이하에서는 연결 협상 및 데이터 전송을 위해 WSMAN(WS-Management) 프로토콜을 사용합니다. WinRM(Windows 원격 관리)에서는 WSMAN 프로토콜을 사용합니다. WinRM이 사용하도록 설정된 경우 PowerShell 7에서는 원격 연결을 위해 `Microsoft.PowerShell`이라는 이름의 기존 Windows PowerShell 5.1 엔드포인트를 사용합니다. 자체 엔드포인트를 포함하도록 PowerShell 7을 업데이트하려면 `Enable-PSRemoting` cmdlet을 실행하세요. 특정 엔드포인트에 연결하는 방법에 대한 자세한 내용은 [PowerShell Core의 WS-Management 원격 기능](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)을 참조하세요.

Windows PowerShell 원격 작업을 사용하려면 원격 관리를 위해 원격 컴퓨터를 구성해야 합니다.
자세한 내용과 지침은 [원격 요구 사항 정보](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)를 참조하세요.

원격 기능을 이용한 작업에 대한 자세한 내용은 [원격 기능에 대한 정보](/powershell/module/microsoft.powershell.core/about/about_remote)를 참조하세요.

#### <a name="ssh-based-remoting"></a>SSH 기반 원격 기능

**WinRM**과 같은 Windows 네이티브 구성 요소를 사용할 수 없는 다른 운영 체제를 지원하기 위해 PowerShell Core 6.x에 SSH 기반 원격 기능을 추가하였습니다. SSH 원격 기능은 대상 컴퓨터에 SSH 하위 시스템으로 PowerShell 호스트 프로세스를 만듭니다. Windows 또는 Linux에서 SSH 기반 원격 기능을 설정하는 방법에 대한 자세한 내용과 예를 보려면 다음을 참조하세요. [SSH를 통한 PowerShell 원격 작업](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

> [!NOTE]
> PowerShell 갤러리(PSGallery)에는 SSH 기반 원격 기능을 자동으로 구성하는 모듈 및 cmdlet이 포함되어 있습니다. [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0)에서 `Microsoft.PowerShell.RemotingTools` 모듈을 설치하고 `Enable-SSH` cmdlet을 실행하세요.

`New-PSSession`, `Enter-PSSession` 및 `Invoke-Command` cmdlet에는 SSH 연결을 지원하는 새로운 매개 변수 집합이 있습니다.

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

원격 세션을 만들려면 **HostName** 매개 변수를 사용하여 대상 컴퓨터를 지정하고 **UserName**을 사용하여 사용자 이름을 제공하세요. cmdlet을 대화형으로 실행하면 암호를 묻는 메시지가 나타납니다.

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

또는 **HostName** 매개 변수를 사용할 때 사용자 이름 정보를 제공하세요. 이 이름 다음에는 `@` 기호와 컴퓨터 이름이 차례로 나옵니다.

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

**KeyFilePath** 매개 변수와 함께 프라이빗 키 파일을 사용하여 SSH 키 인증을 설정할 수 있습니다.
자세한 내용은 [OpenSSH 키 관리](/windows-server/administration/openssh/openssh_keymanagement)를 참조하세요.

### <a name="group-policy-supported"></a>지원되는 그룹 정책

PowerShell에는 엔터프라이즈 환경에서 서버에 대해 일관된 옵션 값을 정의하는 데 도움이 되는 그룹 정책 설정이 포함되어 있습니다. 이러한 설정에는 다음이 포함됩니다.

- 콘솔 세션 구성: PowerShell이 실행되는 구성 엔드포인트를 설정합니다.
- 모듈 로깅 켜기: 모듈의 LogPipelineExecutionDetails 속성을 설정합니다.
- PowerShell 스크립트 블록 로깅 켜기: 모든 PowerShell 스크립트의 자세한 로깅을 사용합니다.
- 스크립트 실행 켜기: PowerShell 실행 정책을 설정합니다.
- PowerShell 기록 켜기: PowerShell 명령의 입력 및 출력을 텍스트 기반 기록으로 캡처하는 기능을 사용합니다.
- Update-Help의 기본 원본 경로 설정: Updatable Help의 원본을 인터넷이 아닌 디렉터리로 설정합니다.

자세한 내용은 [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings)를 참조하세요.

PowerShell 7의 경우 `$PSHOME`에 그룹 정책 템플릿과 설치 스크립트가 포함되어 있습니다.

그룹 정책 도구에서는 관리 템플릿 파일(`.admx`, `.adml`)을 사용하여 사용자 인터페이스에 정책 설정을 입력합니다. 이를 통해 관리자는 레지스트리 기반 정책 설정을 관리할 수 있습니다. `InstallPSCorePolicyDefinitions.ps1` 스크립트를 통해 로컬 컴퓨터에 PowerShell Core 관리 템플릿이 설치됩니다.

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a>별도의 이벤트 로그

Windows PowerShell과 PowerShell 7은 별도의 이벤트 로그에 이벤트를 로그합니다. PowerShell 로그의 목록을 가져오려면 다음 명령을 사용하세요.

```powershell
Get-WinEvent -ListLog *PowerShell*
```

자세한 내용은 [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows)를 참조하세요.

## <a name="improved-editing-experience-with-visual-studio-code"></a>Visual Studio Code로 향상된 편집 환경

[PowerShell 확장](https://code.visualstudio.com/docs/languages/powershell)이 포함된 [Visual Studio Code(VSCode)](https://code.visualstudio.com/)는 PowerShell 7에 대해 지원되는 스크립팅 환경입니다. Windows PowerShell ISE(통합 스크립팅 환경)는 Windows PowerShell만 지원합니다.

업데이트된 PowerShell 확장은 다음을 포함합니다.

- 새로운 ISE 호환 모드
- 구문 강조 표시, 여러 줄 편집, 역검색을 포함한 통합 콘솔의 PSReadLine
- 안정성 및 성능 향상
- 새로운 CodeLens 통합
- 향상된 경로 자동 완성 기능

Visual Studio로 더 쉽게 전환하려면 **명령 팔레트**에서 제공하는 **ISE 모드 사용** 함수를 사용하세요. 이 함수를 통해 VSCode가 ISE 스타일 레이아웃으로 전환됩니다. ISE 스타일 레이아웃은 친숙한 사용자 환경에서 PowerShell의 모든 새로운 기능을 제공합니다.

새로운 ISE 레이아웃으로 전환하려면 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>를 눌러 **명령 팔레트**를 열고, `PowerShell`을 입력한 후 **PowerShell: ISE 모드 사용**을 선택하세요.

레이아웃을 원본 레이아웃으로 설정하려면 **명령 팔레트**를 열고, **PowerShell: ISE 모드 사용 안 함(기본값으로 복원)** 을 선택하세요.

ISE에 맞게 VSCode 레이아웃을 사용자 지정하는 방법에 대한 자세한 내용은 [Visual Studio Code에서 ISE 환경을 복제하는 방법](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)을 참조하세요.

> [!NOTE]
> ISE를 새 기능으로 업데이트할 계획이 없습니다. 이제 ISE 기능은 최신 버전의 Windows 10 및 Windows Server에서 사용자가 제거할 수 있습니다. ISE를 영구적으로 제거할 계획이 없습니다. PowerShell 팀과 파트너는 Visual Studio Code에 대한 PowerShell 확장의 스크립팅 환경을 개선하는 데 집중하고 있습니다.

## <a name="next-steps"></a>다음 단계

효율적으로 마이그레이션할 수 있는 지식을 갖추었으니 이제 [PowerShell 7를 설치](/powershell/scripting/install/installing-powershell-core-on-windows)해 보세요!

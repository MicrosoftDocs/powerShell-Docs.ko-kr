---
title: MacOS에 PowerShell 설치
description: macOS에서 PowerShell을 설치하는 방법에 대한 정보
ms.date: 08/24/2020
ms.openlocfilehash: 8f38d573d9d67276dbc95cfb70f1fde80af62bb6
ms.sourcegitcommit: ea9270bacee7dd1b9df2519384de277576357ce2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88857898"
---
# <a name="installing-powershell-on-macos"></a>MacOS에 PowerShell 설치

PowerShell은 macOS 10.12 이상을 지원합니다. PowerShell 7.0.3 이상 및 PowerShell 미리 보기 7.1.0 이상에는 macOS 10.13 이상이 필요합니다. 모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다. 패키지를 설치한 후 실행하려면 터미널에서 `pwsh`를 실행합니다.

> [!NOTE]
> PowerShell 7은 PowerShell Core 6.x를 제거하는 현재 위치 업그레이드입니다.
>
> `/usr/local/microsoft/powershell/6` 폴더가 `/usr/local/microsoft/powershell/7`로 바뀝니다.
>
> PowerShell 6과 PowerShell 7을 함께 실행해야 하는 경우 [이진 아카이브](#binary-archives) 메서드를 사용하여 PowerShell 6을 다시 설치합니다.

macOS에 PowerShell을 설치하는 방법에는 여러 가지가 있습니다. 다음 방법 중 하나를 선택합니다.

- Homebrew를 사용하여 설치. Homebrew는 macOS용 기본 패키지 관리자입니다.
- [직접 다운로드](#installation-via-direct-download)를 통해 PowerShell 설치
- [이진 보관](#binary-archives)에서 설치

PowerShell을 설치한 후 [OpenSSL](#installing-dependencies)을 설치해야 합니다. OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다.

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a>macOS 10.13 이상에서 Homebrew를 통해 안정적인 최신 릴리스 설치

`brew` 명령이 없을 경우 [해당 지침][brew]에 따라 Homebrew를 설치해야 합니다.

이제 PowerShell을 설치할 수 있습니다.

```sh
brew cask install powershell
```

최종적으로, 설치가 제대로 작동하는지 확인합니다.

```sh
pwsh
```

PowerShell의 새 버전이 릴리스되면 Homebrew의 Formula를 업데이트하고 PowerShell을 업그레이드합니다.

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> 위의 명령은 PowerShell(pwsh) 호스트 내에서 호출할 수 있지만 이때 PowerShell 셸을 종료하고 다시 시작하여 업그레이드를 완료하고 `$PSVersionTable`에 표시된 값을 새로 고쳐야 합니다.

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a>macOS 10.13 이상에서 Homebrew를 통해 최신 미리 보기 릴리스 설치

Homebrew를 설치한 후 PowerShell을 설치할 수 있습니다. 먼저 [Cask-Versions][cask-versions] 패키지를 설치합니다. 그러면 cask 패키지의 대체 버전을 설치할 수 있습니다.

```sh
brew tap homebrew/cask-versions
```

이제 PowerShell을 설치할 수 있습니다.

```sh
brew cask install powershell-preview
```

최종적으로, 설치가 제대로 작동하는지 확인합니다.

```sh
pwsh-preview
```

PowerShell의 새 버전이 릴리스되면 Homebrew의 Formula를 업데이트하고 PowerShell을 업그레이드합니다.

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> 위의 명령은 PowerShell(pwsh) 호스트 내에서 호출할 수 있지만, 업그레이드를 완료하기 위해 PowerShell 셸을 종료하고 다시 시작해야 합니다.
> 그리고 `$PSVersionTable`에 표시된 값을 새로 고칩니다.

안정적인 LTS 버전의 경우 Homebrew tap 메서드를 사용하여 PowerShell을 설치하는 방법도 지원됩니다.

```sh
brew install powershell/tap/powershell
```

이제 설치를 확인할 수 있습니다.

```sh
pwsh
```

PowerShell의 새 버전이 릴리스되면 간단하게 다음 명령을 실행합니다.

```sh
brew upgrade powershell
```

> [!NOTE]
> cask 또는 tap 메서드를 사용하는지 여부에 관계없이 최신 버전의 PowerShell로 업데이트하는 경우 처음에 PowerShell을 설치하는 데 사용한 것과 동일한 메서드를 사용합니다. 다른 메서드를 사용하는 경우 새 pwsh 세션을 여는 데는 계속해서 이전 버전의 PowerShell을 사용합니다.
>
> 다른 메서드를 사용하기로 결정하면 [Homebrew 연결 메서드](https://docs.brew.sh/Manpage#link-ln-options-formula)를 사용하여 문제를 해결하는 방법이 있습니다.

## <a name="installation-via-direct-download"></a>직접 다운로드를 통해 설치

[릴리스][] 페이지의 PKG 패키지 `powershell-lts-7.0.3-osx-x64.pkg`를 macOS 컴퓨터로 다운로드합니다.

파일을 두 번 클릭하고 메시지를 따르거나 터미널에서 설치할 수 있습니다.

```sh
sudo installer -pkg powershell-lts-7.0.3-osx-x64.pkg -target /
```

[OpenSSL](#installing-dependencies)을 설치합니다. OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다.

## <a name="install-as-a-net-global-tool"></a>.NET 전역 도구로 설치

[.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.

```
dotnet tool install --global PowerShell
```

dotnet 도구 설치 프로그램은 `PATH` 환경 변수에 `~/.dotnet/tools`를 추가합니다. 그러나 현재 실행 중인 셸에는 `PATH`가 업데이트되지 않습니다. 새 셸에서 `pwsh`를 입력하여 PowerShell을 시작할 수 있습니다.

[OpenSSL](#installing-dependencies)을 설치합니다. OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다.

## <a name="binary-archives"></a>이진 아카이브

고급 배포 시나리오를 위해 macOS 플랫폼에 대해 PowerShell 이진 `tar.gz` 보관이 제공됩니다. 해당 메서드를 사용하여 설치하는 경우 모든 종속성도 수동으로 설치해야 합니다.

[OpenSSL](#installing-dependencies)을 설치합니다. OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다.

### <a name="installing-binary-archives-on-macos"></a>macOS에서 이진 보관 설치

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.0.3

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.0.3

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.0.3/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.0.3/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a>종속성 설치

OpenSSL은 PowerShell 원격 및 CIM 작업에 필요합니다. 필요한 경우 MacPorts를 통해 OpenSSL를 설치할 수 있습니다.

> [!NOTE]
> MacPorts 및 Homebrew는 동일한 시스템에서 함께 사용될 경우 문제가 있을 수 있습니다. 그러나 Homebrew에는 OpenSSL 1.0용 패키지가 없습니다. 자세한 내용은 [MacPorts FAQ](https://trac.macports.org/wiki/FAQ)를 참조하세요.

1. Xcode 명령줄 도구를 설치합니다. MacPorts에는 Xcode 도구가 필요합니다.

   ```sh
   xcode-select --install
   ```

1. MacPorts를 설치합니다. 지침이 필요한 경우 [설치 가이드](https://www.macports.org/install.php)를 참조하세요.
1. `sudo port selfupdate`를 실행하여 MacPorts를 업데이트합니다.
1. `sudo port upgrade outdated`를 실행하여 MacPorts 패키지를 업그레이드합니다.
1. `sudo port install openssl10`을 실행하여 OpenSSL을 설치합니다.
1. 라이브러리를 연결하여 PowerShell에 대해 사용할 수 있도록 만듭니다.

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
   ```

## <a name="uninstalling-powershell"></a>PowerShell 제거

Homebrew를 사용하여 PowerShell을 설치한 경우 다음 명령을 사용하여 제거합니다.

```sh
brew cask uninstall powershell
```

직접 다운로드를 통해 PowerShell을 설치한 경우에는 PowerShell을 수동으로 제거해야 합니다.

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

추가 PowerShell 경로를 제거하려면 이 문서의 [경로](#paths) 섹션을 참조하고 `sudo rm`을 사용하여 경로를 제거합니다.

> [!NOTE]
> Homebrew를 사용하여 설치한 경우에는 필요하지 않습니다.

## <a name="paths"></a>경로

- `$PSHOME`은 `/usr/local/microsoft/powershell/7.0.3/`입니다.
- 사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.
- 기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.
- 사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.
- 공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.
- 기본 모듈은 `$PSHOME/Modules`에서 읽습니다.
- PSReadline 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.

프로필은 PowerShell의 호스트별 구성을 반영합니다. 따라서 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.

PowerShell은 macOS의 [XDG 기본 디렉터리 사양][xdg-bds]을 따릅니다.

macOS는 BSD에서 파생된 운영체제이므로 `/opt` 대신 `/usr/local`이 접두사로 사용됩니다. 따라서 `$PSHOME`은 `/usr/local/microsoft/powershell/7.0.3/`이며 기호화된 링크는 `/usr/local/bin/pwsh`에 있습니다.

## <a name="installation-support"></a>설치 지원

Microsoft는 이 문서의 설치 방법을 지원합니다. 다른 원본에서 사용 가능한 다른 설치 방법이 있을 수 있습니다. 관련 도구 및 방법이 유효하더라도 Microsoft에서는 해당 방법을 지원할 수 없습니다.

## <a name="additional-resources"></a>추가 리소스

- [Homebrew 웹][brew]
- [Homebrew Github 리포지토리][GitHub]
- [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

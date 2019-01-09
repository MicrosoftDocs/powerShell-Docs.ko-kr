---
title: macOS에서 PowerShell Core 설치
description: macOS에서 PowerShell Core를 설치하는 방법에 대한 정보
ms.date: 12/12/2018
ms.openlocfilehash: 91e64cace7d4ed988da56109dde9bf2a80528eb4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402559"
---
# <a name="installing-powershell-core-on-macos"></a>macOS에서 PowerShell Core 설치

PowerShell Core는 macOS 10.12 이상을 지원합니다.
모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다.
패키지를 설치한 후 실행 `pwsh` 터미널에서.

## <a name="about-brew"></a>Brew 정보

[Homebrew][brew]는 macOS용 기본 패키지 관리자입니다.
`brew` 명령이 없을 경우 [해당 지침][brew]에 따라 Homebrew를 설치해야 합니다.

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>macOS 10.12 이상에서 Homebrew를 통해 안정적인 최신 릴리스 설치

Brew에 대한 자세한 내용은 [Brew정보](#about-brew)를 참조하세요.

이제 PowerShell을 설치할 수 있습니다.

```sh
brew cask install powershell
```

최종적으로, 설치가 제대로 작동하는지 확인합니다.

```sh
pwsh
```

PowerShell의 새 버전이 릴리스되면 Homebrew의 공식을 업데이트 및 PowerShell을 업그레이드 합니다.

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> 위의 명령은 PowerShell (pwsh) 호스트 내에서 호출할 수 있지만 PowerShell 셸 해야 종료 및에 표시 된 값을 새로 고침 및 업그레이드를 완료 하려면 다시 시작 후 `$PSVersionTable`합니다.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>macOS 10.12 이상에서 Homebrew를 통해 최신 미리 보기 릴리스 설치

Brew에 대한 자세한 내용은 [Brew정보](#about-brew)를 참조하세요.

Homebrew를 설치한 후에 PowerShell을 설치할 수 있습니다.
먼저 설치 합니다 [Cask 버전] [ cask-versions] cask 패키지의 다른 버전을 설치할 수 있는 패키지:

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

PowerShell의 새 버전이 릴리스되면 Homebrew의 공식을 업데이트 및 PowerShell을 업그레이드 합니다.

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> 위의 명령은 PowerShell(pwsh) 호스트 내에서 호출할 수 있지만, 업그레이드를 완료하기 위해 PowerShell 셸을 종료하고 다시 시작해야 합니다.
> 에 표시 된 값을 새로 고칩니다 `$PSVersionTable`합니다.

## <a name="installation-via-direct-download"></a>직접 다운로드를 통해 설치

PKG 패키지 `powershell-6.1.0-osx-x64.pkg`를
[릴리스][] 페이지에서 macOS 머신으로 다운로드합니다.

파일을 두 번 클릭하고 메시지를 따르거나 터미널에서 설치할 수 있습니다.

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

[OpenSSL](#install-openssl)를 설치합니다. OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다.

## <a name="binary-archives"></a>이진 아카이브

고급 배포 시나리오를 사용하도록 설정하려면 macOS 플랫폼에 대해 PowerShell 이진 `tar.gz` 보관이 제공됩니다.

### <a name="installing-binary-archives-on-macos"></a>macOS에서 이진 보관 설치

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

[OpenSSL](#install-openssl)를 설치합니다. OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다.

## <a name="installing-dependencies"></a>종속성 설치

### <a name="install-xcode-command-line-tools"></a>XCode 명령줄 도구 설치

```sh
xcode-select --install
```

### <a name="install-openssl"></a>OpenSSL 설치

OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다. MacPorts 또는 Brew를 통해 설치할 수 있습니다.

#### <a name="install-openssl-via-brew"></a>Brew를 통해 OpenSSL 설치

Brew에 대한 자세한 내용은 [Brew정보](#about-brew)를 참조하세요.

OpenSSL을 설치 하려면 실행 `brew install openssl`합니다.

#### <a name="install-openssl-via-macports"></a>MacPorts를 통해 OpenSSL 설치

1. 설치 합니다 [XCode 명령줄 도구](#install-xcode-command-line-tools)합니다.
1. MacPorts를 설치합니다.
   지침이 필요한 경우 참조를 [설치 가이드](https://guide.macports.org/chunked/installing.macports.html)합니다.
1. `sudo port selfupdate`를 실행하여 MacPorts를 업데이트합니다.
1. `sudo port upgrade outdated`를 실행하여 MacPorts 패키지를 업그레이드합니다.
1. 실행 하 여 OpenSSL을 설치 `sudo port install openssl`합니다.
1. PowerShell을 사용할 수 있게 하려면 라이브러리를 링크 합니다.

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a>PowerShell Core 제거

Homebrew를 사용 하 여 PowerShell을 설치한 경우 다음 명령을 사용 하 여 제거 하려면:

```sh
brew cask uninstall powershell
```

직접 다운로드를 통해 PowerShell을 설치한 경우에는 PowerShell을 수동으로 제거해야 합니다.

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

추가 PowerShell 경로 제거 하려면 참조는 [경로](#paths) 사용 하 여 경로 제거 하 고이 문서의 섹션 `sudo rm`합니다.

> [!NOTE]
> Homebrew를 사용하여 설치한 경우에는 필요하지 않습니다.

## <a name="paths"></a>경로

* `$PSHOME`은 `/usr/local/microsoft/powershell/6.1.0/`입니다.
* 사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.
* 기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.
* 사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.
* 공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.
* 기본 모듈은 `$PSHOME/Modules`에서 읽습니다.
* PSReadline 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.

프로필은 PowerShell의 호스트별 구성을 반영합니다.
기본 호스트별 프로필에 존재 하므로 `Microsoft.PowerShell_profile.ps1` 동일한 위치에 있습니다.

PowerShell은 macOS의 [XDG 기본 디렉터리 사양][xdg-bds]을 따릅니다.

macOS는 BSD에서 파생된 것이므로 `/opt` 대신 `/usr/local`이 접두사로 사용됩니다.
따라서 `$PSHOME` 됩니다 `/usr/local/microsoft/powershell/6.1.0/`, 기호화 된 링크에 배치 `/usr/local/bin/pwsh`합니다.

## <a name="additional-resources"></a>추가 리소스

* [Homebrew 웹][brew]
* [Homebrew Github 리포지토리][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

---
Download Help Link: https://go.microsoft.com/fwlink/?LinkId=393271
Help Version: 5.2.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 130582b1b9f18a8f6ada7c009c6d25a7dab75e46
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890715"
---
# PowerShellGet 모듈

## 설명

PowerShellGet은 모듈, DSC 리소스, 역할 기능 및 스크립트와 같은 PowerShell 아티팩트를 검색, 설치, 업데이트 및 게시 하기 위한 명령이 포함 된 모듈입니다.

> [!IMPORTANT]
> 2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다. TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다. 다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.

## PowerShellGet cmdlet

### [Find-Command](Find-Command.md)
모듈에서 PowerShell 명령을 찾습니다.

### [Find-DscResource](Find-DscResource.md)
DSC 리소스를 찾습니다.

### [Find-Module](Find-Module.md)
리포지토리에서 지정 된 조건과 일치 하는 모듈을 찾습니다.

### [Find-RoleCapability](Find-RoleCapability.md)
모듈에서 역할 기능을 찾습니다.

### [Find-Script](Find-Script.md)
스크립트를 찾습니다.

### [Get-InstalledModule](Get-InstalledModule.md)
PowerShellGet에 의해 설치 된 컴퓨터의 모듈 목록을 가져옵니다.

### [Get-InstalledScript](Get-InstalledScript.md)
설치 된 스크립트를 가져옵니다.

### [Get-PSRepository](Get-PSRepository.md)
PowerShell 리포지토리를 가져옵니다.

### [Install-Module](Install-Module.md)
리포지토리에서 하나 이상의 모듈을 다운로드 하 고 로컬 컴퓨터에 설치 합니다.

### [Install-Script](Install-Script.md)
스크립트를 설치 합니다.

### [New-ScriptFileInfo](New-ScriptFileInfo.md)
메타데이터를 사용하여 스크립트 파일을 만듭니다.

### [Publish-Module](Publish-Module.md)
로컬 컴퓨터에서 지정된 모듈을 온라인 갤러리에 게시합니다.

### [Publish-Script](Publish-Script.md)
스크립트를 게시 합니다.

### [Register-PSRepository](Register-PSRepository.md)
PowerShell 리포지토리를 등록 합니다.

### [Save-Module](Save-Module.md)
모듈 및 해당 종속성을 로컬 컴퓨터에 저장 하지만 모듈을 설치 하지는 않습니다.

### [Save-Script](Save-Script.md)
스크립트를 저장 합니다.

### [Set-PSRepository](Set-PSRepository.md)
등록 된 리포지토리에 대 한 값을 설정 합니다.

### [Test-ScriptFileInfo](Test-ScriptFileInfo.md)
스크립트에 대 한 주석 블록의 유효성을 검사 합니다.

### [Uninstall-Module](Uninstall-Module.md)
모듈을 제거 합니다.

### [Uninstall-Script](Uninstall-Script.md)
스크립트를 제거 합니다.

### [Unregister-PSRepository](Unregister-PSRepository.md)
리포지토리 등록을 취소합니다.

### [Update-Module](Update-Module.md)
온라인 갤러리에서 지정된 모듈의 최신 버전을 로컬 컴퓨터에 다운로드하여 설치합니다.

### [Update-ModuleManifest](Update-ModuleManifest.md)
모듈 매니페스트 파일을 업데이트합니다.

### [Update-Script](Update-Script.md)
스크립트를 업데이트 합니다.

### [Update-ScriptFileInfo](Update-ScriptFileInfo.md)
스크립트에 대 한 정보를 업데이트 합니다.

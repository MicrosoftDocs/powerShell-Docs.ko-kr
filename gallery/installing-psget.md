---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: PowerShellGet 설치
ms.openlocfilehash: 23a53a9117c9f6a7ad157b635cd7ff4b3b3444c5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054832"
---
# <a name="installing-powershellget"></a>PowerShellGet 설치

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet은 다음 릴리스에서 제공되는 모듈입니다.

- [Windows 10](https://www.microsoft.com/windows) 이상
- [Windows Server 2016](/windows-server/windows-server) 이상
- [WMF(Windows Management Framework) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 이상
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>PowerShell 버전 3.0 및 4.0용 PowerShellGet 모듈 가져오기

- [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>PowerShell 갤러리에서 최신 버전 가져오기

- PowerShellGet을 업데이트하기 전에 항상 최신 Nuget 공급자를 설치해야 합니다. 이렇게 하려면 관리자 권한 PowerShell 세션에서 다음 명령을 실행합니다.

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>PowerShell 5.0 이상이 설치된 시스템에 최신 PowerShellGet을 설치할 수 있습니다.

- Windows 10, Windows Server 2016, WMF 5.0/5.1이 설치된 시스템 또는 PowerShell 6이 설치된 시스템에서 PowerShellGet을 설치하려면 관리자 권한 PowerShell 세션에서 다음 명령을 실행합니다.

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- `Update-Module`을 사용하여 최신 버전을 가져옵니다.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a>PowerShell 3 또는 PowerShell 4를 실행하며 [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)를 설치한 시스템

- 관리자 권한 PowerShell 세션에서 아래의 PowerShellGet cmdlet을 사용하여 로컬 디렉터리에 모듈을 저장합니다.

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- PowerShellGet 및 PackageManagement 모듈이 다른 프로세스에서 로드되지 않았는지 확인합니다.
- `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 및 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` 폴더의 내용을 삭제합니다.
- 관리자 권한으로 PS 콘솔을 다시 열고 다음 명령을 실행합니다.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```

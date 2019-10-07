---
ms.date: 09/19/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: PowerShellGet 설치
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328204"
---
# <a name="installing-powershellget"></a>PowerShellGet 설치

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet은 다음 릴리스에서 제공되는 모듈입니다.

- [Windows 10](https://www.microsoft.com/windows) 이상
- [Windows Server 2016](/windows-server/windows-server) 이상
- [WMF(Windows Management Framework) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 이상
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a>PowerShell 갤러리에서 최신 버전 가져오기

**PowerShellGet**을 업데이트하기 전에 항상 최신 **NuGet** 공급자를 설치해야 합니다. 관리자 권한 PowerShell 세션에서 다음 명령을 실행합니다.

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>PowerShell 5.0 이상이 설치된 시스템에 최신 PowerShellGet을 설치할 수 있습니다.

Windows 10, Windows Server 2016, WMF 5.0/5.1이 설치된 시스템 또는 PowerShell 6이 설치된 시스템에서 PowerShellGet을 설치하려면 관리자 권한 PowerShell 세션에서 다음 명령을 실행합니다.

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

`Update-Module`을 사용하여 최신 버전을 가져옵니다.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a>PowerShell 3.0 또는 PowerShell 4.0을 실행하는 컴퓨터의 경우

이러한 지침은 **PackageManagement 미리 보기**가 설치되어 있거나 **PowerShellGet** 버전이 설치되어 있지 않은 컴퓨터에 적용됩니다.

`Save-Module` cmdlet은 두 명령 세트에 모두 사용됩니다. `Save-Module`은 등록된 리포지토리에서 모듈 및 모든 종속성을 다운로드하여 저장합니다. 모듈의 최신 버전은 로컬 컴퓨터의 지정된 경로에 저장되지만 설치되지는 않습니다. 자세한 내용은 [Save-Module](/powershell/module/PowershellGet/Save-Module)을 참조하세요.

#### <a name="computers-with-the-packagemanagement-preview-installed"></a>PackageManagement 미리 보기가 설치된 컴퓨터

1. PowerShell 세션에서 `Save-Module`을 사용하여 로컬 디렉터리에 모듈을 저장합니다.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. **PowerShellGet** 및 **PackageManagement** 모듈이 다른 프로세스에서 로드되지 않았는지 확인합니다.
1. `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 및 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` 폴더에서 콘텐츠 내용을 삭제합니다.
1. 관리자 권한으로 PowerShell 콘솔을 다시 열고 다음 명령을 실행합니다.

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a>PowerShellGet이 없는 컴퓨터

**PowerShellGet** 버전이 설치되어 있지 않은 컴퓨터의 경우 모듈을 다운로드하려면 **PowerShellGet**이 설치된 컴퓨터가 필요합니다.

1. **PowerShellGet**이 설치된 컴퓨터에서 `Save-Module`를 사용하여 현재 버전의 **PowerShellGet**를 다운로드합니다. 다운로드되는 폴더는 다음의 두 가지입니다. **PowerShellGet** 및 **PackageManagement**. 각 폴더에는 버전 번호가 있는 하위 폴더가 있습니다.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. **PowerShellGet** 및 **PackageManagement** 폴더를 **PowerShellGet**가 설치되지 않은 컴퓨터에 복사합니다.

   대상 디렉터리는 `$env:ProgramFiles\WindowsPowerShell\Modules`입니다.

---
ms.date: 09/19/2019
title: PowerShellGet 설치
description: 이 문서에서는 다양한 PowerShell 버전에 PowerShellGet 모듈을 설치하는 방법을 설명합니다.
ms.openlocfilehash: 06ec331446849784bb8464912fbce0e5a940823f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662145"
---
# <a name="installing-powershellget"></a>PowerShellGet 설치

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet은 다음 릴리스에서 제공되는 모듈입니다.

- [Windows 10](https://www.microsoft.com/windows) 이상
- [Windows Server 2016](/windows-server/windows-server) 이상
- [WMF(Windows Management Framework) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 이상
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a>PowerShell 갤러리에서 최신 버전 가져오기

**PowerShellGet** 을 업데이트하기 전에 항상 최신 **NuGet** 공급자를 설치해야 합니다. 관리자 권한 PowerShell 세션에서 다음 명령을 실행합니다.

```powershell
Install-PackageProvider -Name NuGet -Force
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>PowerShell 5.0 이상이 설치된 시스템에 최신 PowerShellGet을 설치할 수 있습니다.

Windows 10, Windows Server 2016, WMF 5.0/5.1이 설치된 시스템 또는 PowerShell 6이 설치된 시스템에서 PowerShellGet을 설치하려면 관리자 권한 PowerShell 세션에서 다음 명령을 실행합니다.

```powershell
Install-Module -Name PowerShellGet -Force
```

`Update-Module`을 사용하여 최신 버전을 가져옵니다.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a>PowerShell 3.0 또는 PowerShell 4.0을 실행하는 컴퓨터의 경우

이러한 지침은 **PackageManagement 미리 보기** 가 설치되어 있거나 **PowerShellGet** 버전이 설치되어 있지 않은 컴퓨터에 적용됩니다.

`Save-Module` cmdlet은 두 명령 세트에 모두 사용됩니다. `Save-Module`은 등록된 리포지토리에서 모듈 및 모든 종속성을 다운로드하여 저장합니다. 모듈의 최신 버전은 로컬 컴퓨터의 지정된 경로에 저장되지만 설치되지는 않습니다. PowerShell 3.0 또는 4.0에서 모듈을 설치하려면 모듈이 저장된 폴더를 `$env:ProgramFiles\WindowsPowerShell\Modules`에 복사합니다.

자세한 내용은 [Save-Module](/powershell/module/PowershellGet/Save-Module)을 참조하세요.

> [!NOTE]
> PowerShell 3.0 및 PowerShell 4.0은 한 가지 버전의 모듈만 지원합니다. PowerShell 5.0부터 모듈은 `<modulename>\<version>`에 설치됩니다. 이렇게 하면 여러 버전을 나란히 설치할 수 있습니다. `Save-Module`을 사용하여 모듈을 다운로드한 후 아래 지침에 표시된 대로 파일을 `<modulename>\<version>`에서 대상 머신의 `<modulename>` 폴더로 복사해야 합니다.

#### <a name="preparatory-step-on-computers-running-powershell-30"></a>PowerShell 3.0을 실행하는 컴퓨터에서 준비 단계

아래 섹션의 지침은 디렉터리 `$env:ProgramFiles\WindowsPowerShell\Modules`에 모듈을 설치합니다.
PowerShell 3.0에서 해당 디렉터리는 기본적으로 `$env:PSModulePath`에 나열되지 않으므로 모듈을 자동으로 로드하려면 해당 디렉터리를 추가해야 합니다.

관리자 권한 PowerShell 세션을 열고 다음 명령(이후 세션에서 적용됨)을 실행합니다.

```powershell
[Environment]::SetEnvironmentVariable(
  'PSModulePath',
  ((([Environment]::GetEnvironmentVariable('PSModulePath', 'Machine') -split ';') + "$env:ProgramFiles\WindowsPowerShell\Modules") -join ';'),
  'Machine'
)
```

#### <a name="computers-with-the-packagemanagement-preview-installed"></a>PackageManagement 미리 보기가 설치된 컴퓨터

> [!NOTE]
> PackageManagement 미리 보기는 PowerShell 버전 3 및 4에서 PowerShellGet을 사용할 수 있게 만든 다운로드 가능한 구성 요소이지만 더 이상 사용할 수 없습니다.
> 지정된 컴퓨터에 설치되었는지 테스트하려면 `Get-Module -ListAvailable PowerShellGet`을 실행합니다.

1. PowerShell 세션에서 `Save-Module`을 사용하여 **PowerShellGet** 의 현재 버전을 다운로드합니다. 다운로드되는 폴더는 다음의 두 가지입니다. **PowerShellGet** 및 **PackageManagement**. 각 폴더에는 버전 번호가 있는 하위 폴더가 있습니다.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. **PowerShellGet** 및 **PackageManagement** 모듈이 다른 프로세스에서 로드되지 않았는지 확인합니다.

1. 관리자 권한으로 PowerShell 콘솔을 다시 열고 다음 명령을 실행합니다.

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     Remove-Item $targetDir\* -Recurse -Force
     Copy-Item C:\LocalFolder\$_\*\* $targetDir\ -Recurse -Force
   }
   ```

#### <a name="computers-without-powershellget"></a>PowerShellGet이 없는 컴퓨터

**PowerShellGet** 버전이 설치되어 있지 않은 컴퓨터의 경우(`Get-Module -ListAvailable PowerShellGet`으로 테스트) 모듈을 다운로드하려면 **PowerShellGet** 이 설치된 컴퓨터가 필요합니다.

1. **PowerShellGet** 이 설치된 컴퓨터에서 `Save-Module`를 사용하여 현재 버전의 **PowerShellGet** 를 다운로드합니다. 다운로드되는 폴더는 다음의 두 가지입니다. **PowerShellGet** 및 **PackageManagement**. 각 폴더에는 버전 번호가 있는 하위 폴더가 있습니다.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. **PowerShellGet** 이 설치되지 않은 컴퓨터에 대한 **PowerShellGet** 및 **PackageManagement** 폴더의 각 `<version>` 하위 폴더를 관리자 권한 세션이 필요한 `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 및 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` 폴더로 각각 복사합니다.

1. 예를 들어 다른 컴퓨터의 다운로드 폴더(예: `ws1`)에 액세스할 수 있는 경우 UNC 경로(예: `\\ws1\C$\LocalFolder`)를 통해 대상 컴퓨터에서 관리자 권한으로 PowerShell 콘솔을 열고 다음 명령을 실행합니다.

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     $null = New-Item -Type Directory -Force $targetDir
     $fromComputer = 'ws1'  # Specify the name of the other computer here.
     Copy-Item \\$fromComputer\C$\LocalFolder\$_\*\* $targetDir -Recurse -Force
     if (-not (Get-ChildItem $targetDir)) { Throw "Copying failed." }
   }
   ```

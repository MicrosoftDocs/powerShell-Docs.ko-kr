---
title: PowerShell 모듈 설치 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6a4e9ac2884d0b300b5c1ad8b6156525438a1650
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784863"
---
# <a name="installing-a-powershell-module"></a>PowerShell 모듈 설치

PowerShell 모듈을 만든 후에는 사용자 또는 다른 사용자가 사용할 수 있도록 시스템에 모듈을 설치 하는 것이 좋습니다. 일반적으로이는 모듈 파일 (즉, .psm1 또는 이진 어셈블리, 모듈 매니페스트 및 기타 관련 파일)을 해당 컴퓨터의 디렉터리에 복사 하는 것으로 구성 됩니다. 매우 작은 프로젝트의 경우 Windows 탐색기를 사용 하 여 파일을 단일 원격 컴퓨터에 복사 하 여 붙여 넣는 것 만큼 간단할 수 있습니다. 그러나 대규모 솔루션의 경우 더 복잡 한 설치 프로세스를 사용 하는 것이 좋습니다. 모듈을 시스템에 가져오는 방법에 관계 없이 PowerShell은 사용자가 모듈을 찾아서 사용할 수 있도록 하는 다양 한 기술을 사용할 수 있습니다. 따라서 설치의 주요 문제는 PowerShell이 모듈을 찾을 수 있는지 확인 하는 것입니다. 자세한 내용은 [PowerShell 모듈 가져오기](./importing-a-powershell-module.md)를 참조 하세요.

## <a name="rules-for-installing-modules"></a>모듈 설치 규칙

사용자가 직접 만든 모듈, 다른 파티에서 가져온 모듈 및 다른 사용자에 게 배포 하는 모듈을 포함 하 여 모든 모듈에 대 한 정보는 다음과 같습니다.

### <a name="install-modules-in-psmodulepath"></a>PSModulePath에 모듈 설치

가능 하면 **PSModulePath** 환경 변수에 나열 된 경로에 모든 모듈을 설치 하거나 **PSModulePath** 환경 변수 값에 모듈 경로를 추가 합니다.

**PSModulePath** 환경 변수 ($Env:P SModulePath)에는 Windows PowerShell 모듈의 위치가 포함 되어 있습니다. Cmdlet은이 환경 변수의 값을 사용 하 여 모듈을 찾습니다.

기본적으로 **PSModulePath** 환경 변수 값에는 다음 시스템 및 사용자 모듈 디렉터리가 포함 되지만 값을 추가 하 고 편집할 수 있습니다.

- `$PSHome\Modules`%Windir%\System32\WindowsPowerShell\v1.0\Modules

  > [!WARNING]
  > 이 위치는 Windows와 함께 제공 되는 모듈에 대해 예약 되어 있습니다. 이 위치에 모듈을 설치 하지 마세요.

- `$Home\Documents\WindowsPowerShell\Modules`(%UserProfile%\Documents\WindowsPowerShell\Modules)

- `$Env:ProgramFiles\WindowsPowerShell\Modules`(%ProgramFiles%\WindowsPowerShell\Modules)

  **PSModulePath** 환경 변수의 값을 가져오려면 다음 명령 중 하나를 사용 합니다.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  **PSModulePath** 환경 변수 값 값에 모듈 경로를 추가 하려면 다음 명령 형식을 사용 합니다. 이 형식은 **system.object** 클래스의 **SetEnvironmentVariable** 메서드를 사용 하 여 **PSModulePath** 환경 변수에 대 한 세션 독립적 변경을 수행 합니다.

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > **PSModulePath**에 대 한 경로를 추가한 후에는 변경 내용에 대 한 환경 메시지를 브로드캐스트합니다. 변경을 브로드캐스팅 하면 셸과 같은 다른 응용 프로그램에서 변경 내용을 선택할 수 있습니다. 변경을 브로드캐스트하려면 제품 설치 코드에서를 **WM_SETTINGCHANGE** `lParam` "환경" 문자열로 설정 하 여 WM_SETTINGCHANGE 메시지를 보냅니다. 모듈 설치 코드에서 **PSModulePath**를 업데이트 한 후 메시지를 보내야 합니다.

### <a name="use-the-correct-module-directory-name"></a>올바른 모듈 디렉터리 이름 사용

올바른 형식의 모듈은 모듈 디렉터리에서 하나 이상의 파일에 대 한 기본 이름과 이름이 동일한 디렉터리에 저장 된 모듈입니다. 모듈이 제대로 구성 되지 않은 경우 Windows PowerShell은 모듈을 인식 하지 못합니다.

파일의 "기본 이름"은 파일 이름 확장명이 없는 이름입니다. 잘 구성 된 모듈에서 모듈 파일을 포함 하는 디렉터리의 이름은 모듈에 있는 하나 이상의 파일에 대 한 기본 이름과 일치 해야 합니다.

예를 들어 sample Fabrikam 모듈에서 모듈 파일을 포함 하는 디렉터리의 이름은 "Fabrikam"이 고 하나 이상의 파일에는 "Fabrikam" 기본 이름이 있습니다. 이 경우 Fabrikam.psd1과 Fabrikam.dll에 모두 "Fabrikam" 기본 이름이 있습니다.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>잘못 된 설치의 영향

모듈이 제대로 구성 되지 않은 경우 해당 위치가 **PSModulePath** 환경 변수의 값에 포함 되어 있지 않으면 다음과 같은 Windows PowerShell의 기본 검색 기능이 작동 하지 않습니다.

- 모듈 자동 로드 기능은 모듈을 자동으로 가져올 수 없습니다.

- `ListAvailable`Import-module cmdlet의 매개 [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) 변수는 모듈을 찾을 수 없습니다.

- Import-module [cmdlet은](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 모듈을 찾을 수 없습니다. 모듈을 가져오려면 루트 모듈 파일 또는 모듈 매니페스트 파일의 전체 경로를 제공 해야 합니다.

  모듈을 세션으로 가져오지 않은 경우 다음과 같은 추가 기능을 사용할 수 없습니다. **PSModulePath** 환경 변수의 잘 구성 된 모듈에서는 모듈을 세션으로 가져오지 않은 경우에도 이러한 기능이 작동 합니다.

- [Get 명령](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet은 모듈에서 명령을 찾을 수 없습니다.

- [업데이트-도움말](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 및 [저장-도움말](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet은 모듈에 대 한 도움말을 업데이트 하거나 저장할 수 없습니다.

- [표시 명령](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet은 모듈의 명령을 찾아 표시할 수 없습니다.

  `Show-Command`Windows POWERSHELL ISE (통합 스크립팅 환경)의 창에 모듈의 명령이 없습니다.

## <a name="where-to-install-modules"></a>모듈을 설치 하는 위치

이 섹션에서는 Windows PowerShell 모듈을 설치 하는 파일 시스템의 위치에 대해 설명 합니다. 위치는 모듈이 사용 되는 방식에 따라 달라 집니다.

### <a name="installing-modules-for-a-specific-user"></a>특정 사용자에 대 한 모듈 설치

사용자 고유의 모듈을 만들거나 Windows PowerShell 커뮤니티 웹 사이트와 같은 다른 파티에서 모듈을 가져올 경우 해당 모듈을 사용자 계정에만 사용할 수 있도록 하려면 사용자 특정 모듈 디렉터리에 모듈을 설치 합니다.

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

사용자 전용 모듈 디렉터리는 기본적으로 **PSModulePath** 환경 변수 값에 추가 됩니다.

### <a name="installing-modules-for-all-users-in-program-files"></a>프로그램 파일에 모든 사용자에 대 한 모듈 설치

컴퓨터의 모든 사용자 계정에 모듈을 사용할 수 있도록 하려면 Program Files 위치에 모듈을 설치 합니다.

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> Program Files 위치는 Windows PowerShell 4.0 이상에서 기본적으로 PSModulePath 환경 변수의 값에 추가 됩니다. 이전 버전의 Windows PowerShell에서는 프로그램 파일 위치 ((%ProgramFiles%\WindowsPowerShell\Modules)를 수동으로 만들고 위에서 설명한 대로 PSModulePath 환경 변수에이 경로를 추가할 수 있습니다.

### <a name="installing-modules-in-a-product-directory"></a>제품 디렉터리에 모듈 설치

다른 파티에 모듈을 배포 하는 경우 위에 설명 된 기본 프로그램 파일 위치를 사용 하거나% ProgramFiles% 디렉터리의 고유한 회사 또는 제품별 하위 디렉터리를 만듭니다.

예를 들어, 가상 회사인 Fabrikam 기술은 Fabrikam 관리자 제품에 대 한 Windows PowerShell 모듈을 제공 합니다. 모듈 설치 관리자는 Fabrikam Manager product 하위 디렉터리에 Modules 하위 디렉터리를 만듭니다.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Windows PowerShell 모듈 검색 기능을 사용 하 여 Fabrikam 모듈을 찾기 위해 Fabrikam 모듈 설치 관리자는 **PSModulePath** 환경 변수의 값에 모듈 위치를 추가 합니다.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Common Files 디렉터리에 모듈 설치

제품의 여러 구성 요소 또는 여러 버전의 제품에서 모듈을 사용 하는 경우%ProgramFiles%\Common Files\Modules 하위 디렉터리의 모듈별 하위 디렉터리에 모듈을 설치 합니다.

다음 예제에서 Fabrikam 모듈은 하위 디렉터리의 Fabrikam 하위 디렉터리에 설치 됩니다 `%ProgramFiles%\Common Files\Modules` . 각 모듈은 Modules 하위 디렉터리에 있는 자체 하위 디렉터리에 있습니다.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

그런 다음 설치 관리자는 **PSModulePath** 환경 변수의 값에 공용 파일 모듈 하위 디렉터리의 경로를 포함 합니다.

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a>여러 버전의 모듈 설치

동일한 모듈의 여러 버전을 설치 하려면 다음 절차를 따르십시오.

1. 모듈의 각 버전에 대 한 디렉터리를 만듭니다. 디렉터리 이름에 버전 번호를 포함 합니다.
2. 모듈의 각 버전에 대 한 모듈 매니페스트를 만듭니다. 매니페스트의 **ModuleVersion** 키 값에 모듈 버전 번호를 입력 합니다. 모듈에 대 한 버전별 디렉터리에 매니페스트 파일 (. psd1)을 저장 합니다.
3. 다음 예제에 표시 된 것 처럼 **PSModulePath** 환경 변수의 값에 module root 폴더 경로를 추가 합니다.

모듈의 특정 버전을 가져오기 위해 최종 사용자는 `MinimumVersion` `RequiredVersion` [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet의 또는 매개 변수를 사용할 수 있습니다.

예를 들어 Fabrikam 모듈을 버전 8.0 및 9.0에서 사용할 수 있는 경우 Fabrikam 모듈 디렉터리 구조는 다음과 유사할 수 있습니다.

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

설치 관리자는 두 모듈 경로를 모두 **PSModulePath** 환경 변수 값에 추가 합니다.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

이러한 단계가 완료 되 면 ListAvailable [cmdlet의](/powershell/module/Microsoft.PowerShell.Core/Get-Module) **ListAvailable** 매개 변수가 Fabrikam 모듈을 모두 가져옵니다. 특정 모듈을 가져오려면 `MinimumVersion` `RequiredVersion` [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet의 또는 매개 변수를 사용 합니다.

두 모듈을 동일한 세션으로 가져올 때 모듈에 동일한 이름의 cmdlet이 포함 된 경우 마지막으로 가져온 cmdlet은 세션에서 적용 됩니다.

## <a name="handling-command-name-conflicts"></a>명령 이름 충돌 처리

명령 이름 충돌은 모듈이 내보내는 명령의 이름이 사용자 세션의 명령과 동일한 경우에 발생할 수 있습니다.

세션에 이름이 같은 두 개의 명령이 포함 된 경우 Windows PowerShell은 우선 순위가 높은 명령 유형을 실행 합니다. 세션에 이름과 형식이 같은 명령이 두 개 포함 된 경우 Windows PowerShell은 가장 최근에 세션에 추가 된 명령을 실행 합니다. 기본적으로 실행 되지 않는 명령을 실행 하려면 사용자가 모듈 이름으로 명령 이름을 한정할 수 있습니다.

예를 들어 세션에 함수 및 cmdlet이 포함 되어 있으면 `Get-Date` `Get-Date` Windows PowerShell은 기본적으로 함수를 실행 합니다. Cmdlet을 실행 하려면 명령 앞에 모듈 이름 (예:)을 사용 합니다.

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

이름 충돌을 방지 하기 위해 모듈 작성자는 모듈 매니페스트의 **Defaultcommandprefix** 키를 사용 하 여 모듈에서 내보낸 모든 명령의 명사 접두사를 지정할 수 있습니다.

사용자는 cmdlet의 **prefix** 매개 변수를 사용 `Import-Module` 하 여 대체 접두사를 사용할 수 있습니다. **Prefix** 매개 변수 값은 **defaultcommandprefix** 키의 값 보다 우선 합니다.

## <a name="see-also"></a>참고 항목

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Windows PowerShell 모듈 작성](./writing-a-windows-powershell-module.md)

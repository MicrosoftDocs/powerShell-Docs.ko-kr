---
ms.date: 09/13/2016
ms.topic: reference
title: PowerShell 모듈 설치
description: PowerShell 모듈 설치
ms.openlocfilehash: 3c7a4413168934ca4de1912c9615a6ae0fc45788
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645335"
---
# <a name="installing-a-powershell-module"></a>PowerShell 모듈 설치

PowerShell 모듈을 만든 후에는 사용자가 사용할 수 있도록 시스템에 모듈을 설치해야 할 것입니다. 일반적으로 설치는 모듈 파일(즉, .psm1 또는 이진 어셈블리, 모듈 매니페스트 및 기타 관련 파일)을 해당 컴퓨터의 디렉터리에 복사하는 작업으로 구성됩니다. 소규모 프로젝트라면 Windows 탐색기를 사용하여 파일을 단일 원격 컴퓨터에 복사하여 붙여넣는 정도로 간단할 수 있지만, 대규모 솔루션의 경우에는 더 정교한 설치 프로세스를 사용하는 것이 좋습니다. 모듈을 시스템에 가져오는 방법에 관계없이 PowerShell은 사용자가 모듈을 찾아 사용할 수 있도록 하는 다양한 기술을 사용할 수 있습니다. 따라서 설치에서 기본 문제는 PowerShell이 모듈을 검색할 수 있도록 하는 것입니다. 자세한 내용은 [PowerShell 모듈 가져오기](./importing-a-powershell-module.md)를 참조하세요.

## <a name="rules-for-installing-modules"></a>모듈 설치 규칙

다음 정보는 사용자가 직접 만든 모듈, 다른 당사자에서 가져온 모듈, 다른 사용자에게 배포하는 모듈을 포함한 모든 모듈에 해당됩니다.

### <a name="install-modules-in-psmodulepath"></a>PSModulePath에 모듈 설치

가능하면 **PSModulePath** 환경 변수에 나열된 경로에 모든 모듈을 설치하거나 **PSModulePath** 환경 변수 값에 모듈 경로를 추가합니다.

**PSModulePath** 환경 변수($Env:PSModulePath)에는 Windows PowerShell 모듈의 위치가 포함되어 있습니다. Cmdlet은 이 환경 변수의 값을 사용하여 모듈을 검색합니다.

기본적으로 **PSModulePath** 환경 변수 값에는 다음 시스템 및 사용자 모듈 디렉터리가 포함되지만 이 값은 추가하고 편집할 수 있습니다.

- `$PSHome\Modules`(%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > 이 위치는 Windows와 함께 제공되는 모듈을 위해 예약되어 있습니다. 이 위치에 모듈을 설치하지 마세요.

- `$Home\Documents\WindowsPowerShell\Modules`(%UserProfile%\Documents\WindowsPowerShell\Modules)

- `$Env:ProgramFiles\WindowsPowerShell\Modules`(%ProgramFiles%\WindowsPowerShell\Modules)

  **PSModulePath** 환경 변수의 값을 가져오려면 다음 명령 중 하나를 사용합니다.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  **PSModulePath** 환경 변수 값의 값에 모듈 경로를 추가하려면 다음 명령 형식을 사용합니다. 이 형식은 **System.Environment** 클래스의 **SetEnvironmentVariable** 메서드를 사용하여 **PSModulePath** 환경 변수를 세션 독립적으로 변경합니다.

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > **PSModulePath** 에 경로를 추가한 후에는 변경 내용에 대한 환경 메시지를 브로드캐스트해야 합니다. 변경 내용을 브로드캐스트하면 셸과 같은 다른 애플리케이션에서 변경 내용을 반영할 수 있습니다. 변경 내용을 브로드캐스트하려면 제품 설치 코드에서 `lParam`를 문자열 "Environment"로 설정하여 **WM_SETTINGCHANGE** 메시지를 보냅니다. 메시지는 모듈 설치 코드가 **PSModulePath** 를 업데이트한 후에 보내야 합니다.

### <a name="use-the-correct-module-directory-name"></a>올바른 모듈 디렉터리 이름 사용

잘 구성된(Well-Formed) 모듈은 모듈 디렉터리에 있는 하나 이상의 파일의 기본 이름과 동일한 이름을 갖는 디렉터리에 저장된 모듈입니다. 모듈이 제대로 구성되지 않은 경우 Windows PowerShell이 모듈을 인식하지 못합니다.

파일의 "기본 이름"은 파일 이름 확장명이 없는 파일 이름입니다. 잘 구성된(Well-Formed) 모듈에서 모듈 파일이 포함된 디렉터리의 이름은 모듈에 있는 하나 이상의 파일에 대한 기본 이름과 일치해야 합니다.

예를 들어 샘플 Fabrikam 모듈에서 모듈 파일이 포함된 디렉터리의 이름은 "Fabrikam"이고 하나 이상의 파일에는 "Fabrikam" 기본 이름이 있습니다. 이 경우 Fabrikam.psd1 및 Fabrikam.dll 모두에 "Fabrikam" 기본 이름이 있습니다.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>잘못된 설치의 영향

모듈이 제대로 구성되지 않고 해당 위치가 **PSModulePath** 환경 변수의 값에 포함되어 있지 않으면 다음과 같은 Windows PowerShell의 기본 검색 기능이 작동하지 않습니다.

- 모듈 자동 로드 기능이 모듈을 자동으로 가져올 수 없습니다.

- [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet의 `ListAvailable` 매개 변수가 모듈을 검색할 수 없습니다.

- [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet이 모듈을 검색할 수 없습니다. 모듈을 가져오려면 루트 모듈 파일 또는 모듈 매니페스트 파일의 전체 경로를 제공해야 합니다.

  모듈을 세션으로 가져오지 않은 경우 다음과 같은 추가 기능을 사용할 수 없습니다. **PSModulePath** 환경 변수의 잘 구성된(Well-Formed) 모듈에서는 모듈을 세션으로 가져오지 않은 경우에도 이러한 기능이 작동합니다.

- [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet이 모듈의 명령을 검색할 수 없습니다.

- [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 및 [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet이 모듈에 대한 도움말을 업데이트하거나 저장할 수 없습니다.

- [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet이 모듈의 명령을 검색하여 표시할 수 없습니다.

  모듈의 명령이 Windows PowerShell ISE(통합 스크립팅 환경)의 `Show-Command` 창에서 누락됩니다.

## <a name="where-to-install-modules"></a>모듈을 설치하는 위치

이 섹션에서는 파일 시스템에서 Windows PowerShell 모듈을 설치할 위치에 대해 설명합니다. 이 위치는 모듈이 사용되는 방식에 따라 달라집니다.

### <a name="installing-modules-for-a-specific-user"></a>특정 사용자용 모듈 설치

사용자 고유의 모듈을 만들거나 Windows PowerShell 커뮤니티 웹 사이트와 같은 다른 당사자에서 모듈을 가져와 사용자 계정에서만 사용할 수 있도록 하려면 사용자별 Modules 디렉터리에 모듈을 설치합니다.

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

사용자별 Modules 디렉터리는 기본적으로 **PSModulePath** 환경 변수의 값에 추가됩니다.

### <a name="installing-modules-for-all-users-in-program-files"></a>Program Files에 모든 사용자용 모듈 설치

컴퓨터의 모든 사용자 계정에서 모듈을 사용할 수 있도록 하려면 Program Files 위치에 모듈을 설치합니다.

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> Program Files 위치는 Windows PowerShell 4.0 이상에서 기본적으로 PSModulePath 환경 변수의 값에 추가됩니다. 이전 버전의 Windows PowerShell에서는 수동으로 Program Files 위치(%ProgramFiles%\WindowsPowerShell\Modules)를 만들고 위에서 설명한 대로 PSModulePath 환경 변수에 이 경로를 추가할 수 있습니다.

### <a name="installing-modules-in-a-product-directory"></a>Product 디렉터리에 모듈 설치

다른 당사자에게 모듈을 배포하는 경우 위에 설명된 기본 Program Files 위치를 사용하거나 %ProgramFiles% 디렉터리의 회사별 또는 제품별 하위 디렉터리를 만듭니다.

예를 들어, 가상 회사인 Fabrikam Technologies는 Fabrikam Manager 제품용 Windows PowerShell 모듈을 제공합니다. Fabrikam 모듈 설치 관리자는 Fabrikam Manager 제품 하위 디렉터리에 Modules 하위 디렉터리를 만듭니다.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Windows PowerShell 모듈 검색 기능을 사용하여 Fabrikam 모듈을 찾기 위해 Fabrikam 모듈 설치 관리자는 **PSModulePath** 환경 변수의 값에 모듈 위치를 추가합니다.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Common Files 디렉터리에 모듈 설치

제품의 여러 구성 요소 또는 여러 버전의 제품에서 한 모듈을 사용하는 경우 %ProgramFiles%\Common Files\Modules 하위 디렉터리의 모듈별 하위 디렉터리에 모듈을 설치합니다.

다음 예제에서 Fabrikam 모듈은 `%ProgramFiles%\Common Files\Modules` 하위 디렉터리의 Fabrikam 하위 디렉터리에 설치됩니다. 각 모듈은 Modules 하위 디렉터리 아래의 자체 하위 디렉터리에 있습니다.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

그런 다음 설치 관리자는 **PSModulePath** 환경 변수의 값에 Common Files Modules 하위 디렉터리의 경로를 포함합니다.

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

동일한 모듈의 여러 버전을 설치하려면 다음 절차를 따릅니다.

1. 각 모듈 버전에 대한 디렉터리를 만듭니다. 디렉터리 이름에 버전 번호를 포함합니다.
2. 각 모듈 버전에 대한 모듈 매니페스트를 만듭니다. 매니페스트의 **ModuleVersion** 키 값에 모듈 버전 번호를 입력합니다. 모듈의 버전별 디렉터리에 매니페스트 파일(. psd1)을 저장합니다.
3. 다음 예제와 같이 **PSModulePath** 환경 변수의 값에 모듈 루트 폴더 경로를 추가합니다.

특정 버전의 모듈을 가져오기 위해 최종 사용자는 [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet의 `MinimumVersion` 또는 `RequiredVersion` 매개 변수를 사용할 수 있습니다.

예를 들어 Fabrikam 모듈의 버전 8.0 및 9.0을 사용할 수 있는 경우 Fabrikam 모듈 디렉터리 구조는 다음과 비슷할 수 있습니다.

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

설치 관리자는 **PSModulePath** 환경 변수 값에 두 모듈 경로를 추가합니다.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

이러한 단계가 완료되면 [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet의 **ListAvailable** 매개 변수가 두 Fabrikam 모듈을 모두 가져옵니다. 특정 모듈을 가져오려면 [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet의 `MinimumVersion` 또는 `RequiredVersion` 매개 변수를 사용합니다.

두 모듈을 동일한 세션으로 가져올 때 모듈에 동일한 이름의 cmdlet이 포함된 경우 마지막으로 가져온 cmdlet이 세션에서 유효합니다.

## <a name="handling-command-name-conflicts"></a>명령 이름 충돌 처리

명령 이름 충돌은 모듈이 내보내는 명령의 이름이 사용자 세션의 명령과 동일한 경우에 발생할 수 있습니다.

한 세션에 이름이 같은 명령이 두 개 포함된 경우 Windows PowerShell은 우선 순위가 높은 명령 유형을 실행합니다. 한 세션에 이름 및 유형이 같은 명령이 두 개 포함된 경우 Windows PowerShell은 가장 최근에 세션에 추가된 명령을 실행합니다. 기본적으로 실행되지 않는 명령을 실행하려면 사용자가 모듈 이름을 사용하여 명령 이름을 한정할 수 있습니다.

예를 들어 세션에 `Get-Date` 함수와 `Get-Date` cmdlet이 포함되어 있으면 Windows PowerShell은 기본적으로 함수를 실행합니다. Cmdlet을 실행하려면 명령 앞에 다음과 같은 모듈 이름을 사용합니다.

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

이름 충돌을 방지하기 위해 모듈 작성자는 모듈 매니페스트에 **DefaultCommandPrefix** 키를 사용하여 모듈에서 내보낸 모든 명령에 대한 명사 접두사를 지정할 수 있습니다.

사용자는 `Import-Module` cmdlet의 **Prefix** 매개 변수를 사용하여 대체 접두사를 사용할 수 있습니다. **Prefix** 매개 변수 값은 **DefaultCommandPrefix** 키보다 우선합니다.

## <a name="see-also"></a>참고 항목

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Windows PowerShell 모듈 작성](./writing-a-windows-powershell-module.md)

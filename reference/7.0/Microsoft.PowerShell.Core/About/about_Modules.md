---
description: PowerShell 모듈을 설치, 가져오기 및 사용 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Modules
ms.openlocfilehash: ab4e9658ed4820c3ae84ac1cd9a55b59cc8017ab
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564482"
---
# <a name="about-modules"></a>모듈 정보

## <a name="short-description"></a>간단한 설명
PowerShell 모듈을 설치, 가져오기 및 사용 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

모듈은 cmdlet, 공급자, 함수, 워크플로, 변수, 별칭 등의 PowerShell 멤버를 포함 하는 패키지입니다.

명령을 작성하는 사용자는 모듈을 사용하여 자신의 명령을 구성하고 다른 사용자와 공유할 수 있습니다. 모듈을 받는 사용자는 모듈의 명령을 PowerShell 세션에 추가 하 고 기본 제공 명령과 같은 방법으로 사용할 수 있습니다.

이 항목에서는 PowerShell 모듈을 사용 하는 방법에 대해 설명 합니다. PowerShell 모듈을 작성 하는 방법에 대 한 자세한 내용은 [Powershell 모듈 작성](/powershell/scripting/developer/module/writing-a-windows-powershell-module)을 참조 하세요.

## <a name="what-is-a-module"></a>모듈 이란?

모듈은 cmdlet, 공급자, 함수, 워크플로, 변수, 별칭 등의 PowerShell 멤버를 포함 하는 패키지입니다. 이 패키지의 멤버는 PowerShell 스크립트, 컴파일된 DLL 또는 둘의 조합으로 구현 될 수 있습니다. 이러한 파일은 일반적으로 단일 디렉터리에 함께 그룹화 됩니다. 자세한 내용은 SDK 설명서에서 [Windows PowerShell 모듈 이해](/powershell/scripting/developer/module/understanding-a-windows-powershell-module) 를 참조 하세요.

## <a name="module-auto-loading"></a>모듈 자동 로드

PowerShell 3.0부터 PowerShell은 설치 된 모듈에서 명령을 처음 실행할 때 자동으로 모듈을 가져옵니다. 이제는 설정 및 프로필 구성 없이도 모듈의 명령을 사용할 수 있으므로 컴퓨터에 모듈을 설치한 후에 모듈을 관리할 필요가 없습니다.

또한 모듈의 명령이 보다 쉽게 찾을 수 있습니다. `Get-Command`이제 cmdlet은 아직 세션에 있지 않더라도 설치 된 모든 모듈에서 모든 명령을 가져옵니다. 모듈을 먼저 가져올 필요 없이 명령을 찾아서 사용할 수 있습니다.

다음의 각 예에서는를 포함 하는 CimCmdlets 모듈을 `Get-CimInstance` 세션으로 가져옵니다.

- 명령 실행

  ```powershell
  Get-CimInstance Win32_OperatingSystem
  ```

- 명령 가져오기

  ```powershell
  Get-Command Get-CimInstance
  ```

- 명령에 대 한 도움말 보기

  ```powershell
  Get-Help Get-CimInstance
  ```

`Get-Command` 와일드 카드 문자 ()를 포함 하는 명령은 `*` 검색을 위해 사용 하지 않는 것으로 간주 되며 모듈을 가져오지 않습니다.

PSModulePath 환경 변수에 지정 된 위치에 저장 된 모듈만 자동으로 가져옵니다. Cmdlet을 실행 하면 다른 위치의 모듈을 가져와야 합니다 `Import-Module` .

또한 PowerShell 공급자를 사용 하는 명령은 모듈을 자동으로 가져오지 않습니다. 예를 들어 cmdlet과 같이 WSMan: 드라이브가 필요한 명령을 사용 하는 경우이 cmdlet을 `Get-PSSessionConfiguration` 실행 하 여 `Import-Module` 드라이브를 포함 하는 **Microsoft-wsman. 관리** 모듈을 가져와야 할 수 있습니다. `WSMan:`

명령을 계속 실행 하 여 `Import-Module` 모듈을 가져오고 변수를 사용 하 여 `$PSModuleAutoloadingPreference` 모듈 자동 가져오기를 사용 하거나 사용 하지 않도록 설정 하 고 구성할 수 있습니다. 자세한 내용은 [about_Preference_Variables](about_Preference_Variables.md)를 참조 하세요.

## <a name="how-to-use-a-module"></a>모듈을 사용 하는 방법

모듈을 사용하려면 다음 작업을 수행합니다.

1. 모듈을 설치합니다. 대부분의 경우 이 작업은 자동으로 수행됩니다.
1. 모듈에서 추가한 명령을 찾습니다.
1. 모듈에서 추가한 명령을 사용합니다.

항목에서는 이러한 작업을 수행하는 방법에 대해 설명합니다. 또한 모듈 관리에 대한 유용한 정보를 제공합니다.

## <a name="how-to-install-a-module"></a>모듈을 설치 하는 방법

파일이 포함 된 폴더로 모듈을 수신 하는 경우 PowerShell에서 사용 하기 전에 컴퓨터에 설치 해야 합니다.

대부분의 모듈은 자동으로 설치됩니다. PowerShell은 몇 가지 미리 설치 된 모듈 ( _핵심_ 모듈 이라고 함)과 함께 제공 됩니다. Windows 기반 컴퓨터에서 운영 체제에 포함 된 기능에 관리 하는 cmdlet이 있는 경우 해당 모듈은 사전 설치 됩니다. Windows 기능을 설치 하는 경우 예를 들어 서버 관리자의 역할 및 기능 추가 마법사 또는 제어판의 Windows 기능 사용/사용 안 함 대화 상자를 사용 하 여 기능에 포함 된 모든 PowerShell 모듈을 설치 합니다. 다른 대부분의 모듈은 모듈을 설치하는 설치 관리자나 설치 프로그램에 함께 제공됩니다.

다음 명령을 사용 하 여 현재 사용자의 **Modules** 디렉터리를 만듭니다.

```powershell
New-Item -Type Directory -Path $HOME\Documents\PowerShell\Modules
```

전체 모듈 폴더를 Modules 디렉터리에 복사합니다. 모든 방법을 사용 하 여 Windows 탐색기, Cmd.exe 및 PowerShell을 포함 하 여 폴더를 복사할 수 있습니다. PowerShell에서 cmdlet을 사용 `Copy-Item` 합니다. 예를 들어에서 MyModule 폴더를 `C:\ps-test\MyModule` Modules 디렉터리에 복사 하려면 다음을 입력 합니다.

```powershell
Copy-Item -Path C:\ps-test\MyModule -Destination `
    $HOME\Documents\PowerShell\Modules
```

원하는 어떤 위치에도 모듈을 설치할 수 있지만 기본 모듈 위치에 모듈을 설치하면 관리하기가 더 쉽습니다. 기본 모듈 위치에 대 한 자세한 내용은 [모듈 및 DSC 리소스 위치 및 PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) 섹션을 참조 하세요.

## <a name="how-to-find-installed-modules"></a>설치 된 모듈을 찾는 방법

기본 모듈 위치에 설치되었으나 세션에 아직 가져오지 않은 모듈을 찾으려면 다음과 같이 입력하세요.

```powershell
Get-Module -ListAvailable
```

이미 세션으로 가져온 모듈을 찾으려면 PowerShell 프롬프트에서 다음을 입력 합니다.

```powershell
Get-Module
```

Cmdlet에 대 한 자세한 내용은 `Get-Module` [import-module](xref:Microsoft.PowerShell.Core.Get-Module)을 참조 하세요.

## <a name="how-to-find-the-commands-in-a-module"></a>모듈의 명령을 찾는 방법

Cmdlet을 사용 `Get-Command` 하 여 사용 가능한 모든 명령을 찾습니다. Cmdlet의 매개 변수를 사용 `Get-Command` 하 여 모듈, 이름 및 명사 등의 명령을 필터링 할 수 있습니다.

모듈의 명령을 모두 찾으려면 다음과 같이 입력하세요.

```powershell
Get-Command -Module <module-name>
```

예를 들어 BitsTransfer 모듈의 명령을 찾으려면 다음을 입력 합니다.

```powershell
Get-Command -Module BitsTransfer
```

Cmdlet에 대 한 자세한 내용은 `Get-Command` [get-help](xref:Microsoft.PowerShell.Core.Get-Command)를 참조 하세요.

## <a name="how-to-get-help-for-the-commands-in-a-module"></a>모듈의 명령에 대 한 도움말을 가져오는 방법

모듈에 내보내는 명령에 대 한 도움말 파일이 포함 되어 있는 경우 `Get-Help` cmdlet에 도움말 항목이 표시 됩니다. `Get-Help`PowerShell에서 명령에 대 한 도움말을 가져오는 데 사용 하는 것과 동일한 명령 형식을 사용 합니다.

PowerShell 3.0부터 모듈에 대 한 도움말 파일을 다운로드 하 고 도움말 파일에 대 한 업데이트를 다운로드 하 여 사용 되지 않도록 할 수 있습니다.

모듈의 명령에 대한 도움말을 보려면 다음과 같이 입력하세요.

```powershell
Get-Help <command-name>
```

모듈의 명령에 대 한 온라인 도움말을 보려면 다음을 입력 합니다.

```powershell
Get-Help <command-name> -Online
```

모듈의 명령에 대 한 도움말 파일을 다운로드 하 여 설치 하려면 다음을 입력 합니다.

```powershell
Update-Help -Module <module-name>
```

자세한 내용은 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 및 [update-help](xref:Microsoft.PowerShell.Core.Update-Help)를 참조 하세요.

## <a name="how-to-import-a-module"></a>모듈을 가져오는 방법

모듈을 가져오거나 모듈 파일을 가져와야 할 수 있습니다. 가져오기는 모듈이 **PSModulePath** 환경 변수, 또는로 지정 된 위치에 설치 되어 있지 않거나, `$env:PSModulePath` 모듈이 폴더로 배달 되는 일반적인 모듈이 아니라 .dll 또는. .psm1 파일과 같은 파일로 구성 된 경우에 필요 합니다.

`Import-Module`가져온 모든 명령의 명사 이름에 고유한 접두사를 추가 하는 prefix 매개 변수 또는 모듈이 세션의 기존 명령을 숨기 거 나 바꾸는 명령을 추가 하지 못하게 하는 **NoClobber** 매개 변수 등 명령의 매개 변수를 사용할 수 있도록 모듈을 가져오도록 선택할 수도 있습니다.

모듈을 가져오려면 cmdlet을 사용 `Import-Module` 합니다.

PSModulePath 위치의 모듈을 현재 세션으로 가져오려면 다음 명령 형식을 사용합니다.

```powershell
Import-Module <module-name>
```

예를 들어 다음 명령은 BitsTransfer 모듈을 현재 세션으로 가져옵니다.

```powershell
Import-Module BitsTransfer
```

기본 모듈 위치에 없는 모듈을 가져오려면 명령에서 모듈 폴더에 대한 정규화된 경로를 사용합니다.

예를 들어 디렉터리의 TestCmdlets 모듈을 `C:\ps-test` 세션에 추가 하려면 다음을 입력 합니다.

```powershell
Import-Module C:\ps-test\TestCmdlets
```

모듈 폴더에 없는 모듈 파일을 가져오려면 명령에 모듈 파일에 대한 정규화된 경로를 사용합니다.

예를 들어 디렉터리의 TestCmdlets.dll 모듈을 `C:\ps-test` 세션에 추가 하려면 다음을 입력 합니다.

```powershell
Import-Module C:\ps-test\TestCmdlets.dll
```

세션에 모듈을 추가 하는 방법에 대 한 자세한 내용은 [import-module](xref:Microsoft.PowerShell.Core.Import-Module)을 참조 하세요.

## <a name="how-to-import-a-module-into-every-session"></a>모듈을 모든 세션으로 가져오는 방법

이 `Import-Module` 명령은 모듈을 현재 PowerShell 세션으로 가져옵니다. 시작 하는 모든 PowerShell 세션으로 모듈을 가져오려면 `Import-Module` powershell 프로필에 명령을 추가 합니다.

프로필에 대한 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조하세요.

## <a name="how-to-remove-a-module"></a>모듈을 제거 하는 방법

모듈을 제거하면 모듈에서 추가한 명령이 세션에서 삭제됩니다.

세션에서 모듈을 제거 하려면 다음 명령 형식을 사용 합니다.

```powershell
Remove-Module <module-name>
```

예를 들어 다음 명령은 현재 세션에서 BitsTransfer 모듈을 제거 합니다.

```powershell
Remove-Module BitsTransfer
```

모듈을 제거하는 작업은 모듈을 가져오는 작업과 반대입니다. 모듈을 제거해도 모듈이 제거되지는 않습니다. 자세한 내용은 [Remove 모듈](xref:Microsoft.PowerShell.Core.Remove-Module)을 참조 하세요.

## <a name="module-and-dsc-resource-locations-and-psmodulepath"></a>모듈 및 DSC 리소스 위치 및 PSModulePath

`$env:PSModulePath`환경 변수는 모듈 및 리소스를 찾기 위해 검색 되는 폴더 위치 목록을 포함 합니다.

기본적으로에 할당 되는 유효 위치는 `$env:PSModulePath` 다음과 같습니다.

- 시스템 차원의 위치: `$PSHOME\Modules`

  이러한 폴더에는 Windows 및 PowerShell과 함께 제공 되는 모듈이 포함 되어 있습니다.

  PowerShell에 포함 된 DSC 리소스는 폴더에 저장 됩니다 `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` .

- 사용자 지정 모듈: 사용자의 범위에 사용자가 설치 하는 모듈입니다. `Install-Module` 에는 현재 사용자 또는 모든 사용자에 대해 모듈이 설치 되어 있는지 여부를 지정할 수 있는 **범위** 매개 변수가 있습니다. 자세한 내용은 [모듈 설치](xref:PowerShellGet.Install-Module)를 참조 하세요.

  Windows의 사용자 관련 **CurrentUser** 위치는 `PowerShell\Modules` 사용자 프로필의 **문서** 위치에 있는 폴더입니다. 해당 위치의 특정 경로는 Windows의 버전에 따라 다르며 폴더 리디렉션을 사용 하는지 여부에 따라 다릅니다. Microsoft OneDrive는 **문서** 폴더의 위치를 변경할 수도 있습니다.

  기본적으로 Windows 10의 경우 해당 위치는 `$HOME\Documents\PowerShell\Modules` 입니다. Linux 또는 Mac에서 **CurrentUser** 위치는 `$HOME/.local/share/powershell/Modules` 입니다.

  > [!NOTE]
  > 다음 명령을 사용 하 여 **문서** 폴더의 위치를 확인할 수 있습니다 `[Environment]::GetFolderPath('MyDocuments')` .

- **AllUsers** 위치는 `$env:PROGRAMFILES\PowerShell\Modules` Windows에 있습니다. Linux 또는 Mac에서 모듈은에 저장 됩니다 `/usr/local/share/powershell/Modules` .

> [!NOTE]
> 디렉터리에서 파일을 추가 하거나 변경 하려면 `$env:Windir\System32` **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.

**PSModulePath** 환경 변수의 값을 변경 하 여 시스템에서 기본 모듈 위치를 변경할 수 있습니다 `$Env:PSModulePath` . **PSModulePath** 환경 변수는 Path 환경 변수에서 모델링 되며 동일한 형식을 갖습니다.

기본 모듈 위치를 보려면 다음을 입력합니다.

```powershell
$Env:PSModulePath
```

기본 모듈 위치를 추가하려면 다음 명령 형식을 사용합니다.

```powershell
$Env:PSModulePath = $Env:PSModulePath + ";<path>"
```

명령의 세미콜론 ()은 `;` 목록에서 앞에 나오는 경로와 새 경로를 분리 합니다.

예를 들어 디렉터리를 추가 하려면 `C:\ps-test\Modules` 다음을 입력 합니다.

```powershell
$Env:PSModulePath + ";C:\ps-test\Modules"
```

Linux 또는 MacOS에서 기본 모듈 위치를 추가 하려면 다음 명령 형식을 사용 합니다.

```powershell
$Env:PSModulePath += ":<path>"
```

예를 들어 `/usr/local/Fabrikam/Modules` **PSModulePath** 환경 변수의 값에 디렉터리를 추가 하려면 다음을 입력 합니다.

```powershell
$Env:PSModulePath += ":/usr/local/Fabrikam/Modules"
```

Linux 또는 MacOS에서 명령의 콜론 ( `:` )은 목록에서 앞에 나오는 경로와 새 경로를 분리 합니다.

**PSModulePath** 에 경로를 추가 하면 `Get-Module` 및 명령에 `Import-Module` 해당 경로에 있는 모듈이 포함 됩니다.

설정한 값은 현재 세션에만 적용됩니다. 변경 내용을 영구적으로 적용 하려면 PowerShell 프로필에 명령을 추가 하거나 제어판의 시스템을 사용 하 여 레지스트리에서 **PSModulePath** 환경 변수의 값을 변경 합니다.

또한 변경 내용을 영구적으로 적용 하려면 SetEnvironmentVariable 클래스의  메서드를 사용 하 여 **PSModulePath** 환경 변수에 대 한 경로를 추가할 수 **있습니다.**

**PSModulePath** 변수에 대 한 자세한 내용은 [about_Environment_Variables](about_Environment_Variables.md)를 참조 하세요.

## <a name="modules-and-name-conflicts"></a>모듈 및 이름 충돌

세션에 이름이 동일한 명령이 두 개 이상 있을 경우 이름이 충돌합니다. 모듈의 명령이 세션의 명령 또는 항목과 동일한 이름을 가질 경우 모듈을 가져올 때 이름 충돌을 발생합니다.

이름 충돌로 인해 명령이 숨겨지거나 바뀔 수 있습니다.

### <a name="hidden"></a>숨김

명령 이름을 입력할 때 실행되는 명령이 아니고 명령을 시작한 모듈이나 스냅인의 이름으로 명령 이름을 정규화하는 것과 같은 기타 방법을 사용하여 실행할 수 있을 때 명령은 숨겨집니다.

### <a name="replaced"></a>대체됨

동일한 이름의 명령 파일로 덮어쓰였으므로 명령을 실행할 수 없는 경우 명령이 바뀝니다. 충돌을 유발한 모듈을 제거하더라도 세션을 다시 시작해야만 바뀐 명령을 실행할 수 있습니다.

`Import-Module` 현재 세션의 명령을 숨기 거 나 바꾸는 명령을 추가할 수 있습니다. 또한 세션의 명령이 모듈에서 추가한 명령을 숨길 수 있습니다.

이름 충돌을 검색 하려면 cmdlet의 **All** 매개 변수를 사용 합니다 `Get-Command` . PowerShell 3.0부터 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령만 가져옵니다. **All** 매개 변수는 세션에서 특정 이름의 명령을 모두 가져옵니다.

이름 충돌을 방지 하려면 cmdlet의 **NoClobber** 또는 **Prefix** 매개 변수를 사용 합니다 `Import-Module` . **Prefix** 매개 변수는 세션에서 고유 하도록 가져온 명령의 이름에 접두사를 추가 합니다. **NoClobber** 매개 변수는 세션의 기존 명령을 숨기 거 나 바꾸는 명령은 가져오지 않습니다.

의 **Alias**, **Cmdlet**, **Function** 및 **Variable** 매개 변수를 사용 `Import-Module` 하 여 가져올 명령만 선택할 수 있으며, 세션에서 이름 충돌을 일으키는 명령을 제외할 수도 있습니다.

모듈 작성자는 모듈 매니페스트의 **Defaultcommandprefix** 속성을 사용 하 여 모든 명령 이름에 기본 접두사를 추가 함으로써 이름 충돌을 방지할 수 있습니다.
**Prefix** 매개 변수 값은 **defaultcommandprefix** 값 보다 우선 합니다.

명령이 숨겨지더라도 명령을 시작한 모듈이나 스냅인의 이름으로 명령 이름을 정규화하여 명령을 실행할 수 있습니다.

PowerShell 명령 우선 순위 규칙은 세션에 같은 이름의 명령이 포함 된 경우 실행 되는 명령을 결정 합니다.

예를 들어 세션에 이름이 같은 함수 및 cmdlet이 포함 되어 있는 경우 PowerShell은 기본적으로 함수를 실행 합니다. 세션에 이름과 형식이 같은 명령이 포함된 경우(예: 이름이 같은 두 개의 cmdlet) 기본적으로 가장 최근에 추가한 명령이 실행됩니다.

선행 규칙에 대 한 설명 및 숨겨진 명령 실행에 대 한 지침을 비롯 한 자세한 내용은 [about_Command_Precedence](about_Command_Precedence.md)를 참조 하세요.

## <a name="modules-and-snap-ins"></a>모듈 및 스냅인

모듈 및 스냅인에서 세션에 명령을 추가할 수 있습니다. 모듈은 cmdlet, 공급자, 함수 및 항목 (예: 변수, 별칭 및 PowerShell 드라이브)을 비롯 한 모든 유형의 명령을 추가할 수 있습니다. 스냅인에서는 cmdlet과 공급자만 추가할 수 있습니다.

사용자 세션에서 모듈이나 스냅인을 제거하기 전에 다음 명령을 사용하여 제거할 명령을 결정합니다.

세션에서 cmdlet의 원본을 찾으려면 다음 명령 형식을 사용 합니다.

```powershell
Get-Command <cmdlet-name> | Format-List -Property verb,noun,pssnapin,module
```

예를 들어 cmdlet의 원본을 찾으려면 다음과 같이 `Get-Date` 입력 합니다.

```powershell
Get-Command Get-Date | Format-List -Property verb,noun,module
```

## <a name="module-related-warnings-and-errors"></a>모듈 관련 경고 및 오류

모듈에서 내보내는 명령은 PowerShell 명령 명명 규칙을 따라야 합니다. 가져오는 모듈이 이름에 승인 되지 않은 동사가 포함 된 cmdlet 또는 함수를 내보내는 경우 `Import-Module` cmdlet은 다음 경고 메시지를 표시 합니다.

> 경고: 일부 가져온 명령 이름에는 검색 하기 어려울 수 있는 승인 되지 않은 동사가 포함 되어 있습니다. 자세한 내용을 보려면 Verbose 매개 변수를 사용하거나 승인된 동사 목록을 보려면 Get-Verb를 입력하세요.

이 메시지는 경고일 뿐입니다. 비준수 명령을 포함하여 전체 모듈을 계속 가져옵니다. 메시지가 모듈 사용자에게 표시되더라도 명명 문제는 모듈 작성자가 수정해야 합니다.

경고 메시지를 표시 하지 않으려면 cmdlet의 **DisableNameChecking** 매개 변수를 사용 합니다 `Import-Module` .

## <a name="built-in-modules-and-snap-ins"></a>기본 제공 모듈 및 스냅인

Powershell 2.0 및 powershell 3.0 이상의 이전 스타일 호스트 프로그램에서 powershell과 함께 설치 되는 핵심 명령은 모든 PowerShell 세션에 자동으로 추가 되는 스냅인에 패키지 됩니다.

PowerShell 3.0부터 초기 세션 상태 API를 구현 하는 호스트 프로그램의 경우 `InitialSessionState.CreateDefault2` 기본적으로 모든 세션에 Microsoft. PowerShell. 코어 스냅인이 추가 됩니다. 모듈은 처음 사용할 때 자동으로 로드됩니다.

> [!NOTE]
> Cmdlet을 사용 하 여 시작 된 세션을 비롯 한 원격 세션 `New-PSSession` 은 기본 제공 명령이 스냅인에 패키지 되는 이전 스타일의 세션입니다.

다음 모듈 (또는 스냅인)은 PowerShell과 함께 설치 됩니다.

- CimCmdlets
- Microsoft.PowerShell.Archive
- Microsoft.PowerShell.Core
- Microsoft.PowerShell.Diagnostics
- Microsoft.PowerShell.Host
- Microsoft.PowerShell.Management
- Microsoft.PowerShell.Security
- Microsoft.PowerShell.Utility
- Microsoft.WSMan.Management
- PackageManagement
- PowerShellGet
- PSDesiredStateConfiguration
- PSDiagnostics
- PSReadline

## <a name="logging-module-events"></a>모듈 이벤트 로깅

PowerShell 3.0부터 모듈 및 스냅인의 **LogPipelineExecutionDetails** 속성을로 설정 하 여 powershell 모듈 및 스냅인의 cmdlet 및 함수에 대 한 실행 이벤트를 기록할 수 있습니다 `$True` .
그룹 정책 설정인 모듈 로깅을 설정 하 여 모든 PowerShell 세션에서 모듈 로깅을 사용 하도록 설정할 수도 있습니다. 자세한 내용은 로깅 및 그룹 정책 문서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Logging_Windows](about_Logging_Windows.md)

[about_Logging_Non-Windows](about_Logging_Non-Windows.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Command_Precedence](about_Command_Precedence.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Get-Module](xref:Microsoft.PowerShell.Core.Get-Module)

[모듈 가져오기](xref:Microsoft.PowerShell.Core.Import-Module)

[Remove-Module](xref:Microsoft.PowerShell.Core.Remove-Module)

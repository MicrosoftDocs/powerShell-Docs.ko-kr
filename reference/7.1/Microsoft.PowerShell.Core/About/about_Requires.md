---
description: 필요한 요소 없이 스크립트가 실행 되지 않도록 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: 5c4eb4e272f214ffe906fd1a3f1c127824183d4a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223945"
---
# <a name="about-requires"></a>필요한 정보

## <a name="short-description"></a>간단한 설명
필요한 요소 없이 스크립트가 실행 되지 않도록 합니다.

## <a name="long-description"></a>자세한 설명입니다.

`#Requires`문은 PowerShell 버전, 모듈 (및 버전) 또는 스냅인 (및 버전) 및 버전 필수 구성 요소가 충족 되지 않으면 스크립트가 실행 되지 않도록 합니다. 필수 구성 요소가 충족 되지 않으면 PowerShell에서 스크립트를 실행 하지 않습니다.

### <a name="syntax"></a>구문

```
#Requires -Assembly { <Path to .dll> | <.NET assembly specification> }
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

구문에 대 한 자세한 내용은 [Scriptrequirements 사항](/dotnet/api/system.management.automation.language.scriptrequirements)을 참조 하세요.

### <a name="rules-for-use"></a>사용할 규칙

스크립트는 둘 이상의 문을 포함할 수 있습니다 `#Requires` . `#Requires`문은 스크립트의 모든 줄에 표시 될 수 있습니다.

`#Requires`문을 함수 안에 두면 해당 범위가 제한 되지 않습니다. 모든 `#Requires` 문은 항상 전역적으로 적용 되며 스크립트가 실행 되기 전에 충족 되어야 합니다.

> [!WARNING]
> `#Requires`스크립트의 모든 줄에 문이 표시 될 수 있지만 스크립트의 해당 위치는 응용 프로그램의 순서에 영향을 주지 않습니다. `#Requires`스크립트를 실행 하기 전에 문이 제공 하는 전역 상태를 충족 해야 합니다.

예제:

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

필요한 모듈이 문 앞에서 제거 되었으므로 위의 코드는 실행 되지 않는 것으로 간주할 수 있습니다 `#Requires` . 그러나 `#Requires` 스크립트를 실행 하기 전에 상태를 충족 해야 합니다. 그런 다음 스크립트의 첫 번째 줄에서 필요한 상태를 무효화 합니다.

### <a name="parameters"></a>매개 변수

#### <a name="-assembly-assembly-path--net-assembly-specification"></a>-어셈블리 \<Assembly path> |\<.NET assembly specification>

어셈블리 DLL 파일 또는 .NET 어셈블리 이름에 대 한 경로를 지정 합니다. **Assembly** 매개 변수는 PowerShell 5.0에서 도입 되었습니다. .NET 어셈블리에 대 한 자세한 내용은 [어셈블리 이름](/dotnet/standard/assembly/names)을 참조 하세요.

예를 들면 다음과 같습니다.

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a>-Version \<N\> [. \<n\> ]

스크립트에 필요한 PowerShell의 최소 버전을 지정 합니다. 주 버전 번호 및 부 버전 번호 (선택 사항)를 입력 합니다.

예를 들면 다음과 같습니다.

```powershell
#Requires -Version 6.0
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a>-Add-pssnapin \<PSSnapin-Name\> [-Version \<N\> [. \<n\> ]]

스크립트에 필요한 PowerShell 스냅인을 지정 합니다. 스냅인 이름과 버전 번호 (선택 사항)를 입력 합니다.

예를 들면 다음과 같습니다.

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a>-모듈 \<Module-Name\> |\<Hashtable\>

스크립트에 필요한 PowerShell 모듈을 지정 합니다. 모듈 이름 및 버전 번호 (선택 사항)를 입력 합니다.

필수 모듈이 현재 세션에 없으면 PowerShell에서 해당 모듈을 가져옵니다.
모듈을 가져올 수 없는 경우 PowerShell에서 종료 오류를 throw 합니다.

각 모듈에 대해 모듈 이름 ( \<String\> ) 또는 해시 테이블을 입력 합니다. 값은 문자열과 해시 테이블의 조합일 수 있습니다. 해시 테이블에는 다음과 같은 키가 있습니다.

- `ModuleName` - **필수** 모듈 이름을 지정 합니다.
- `GUID` - **선택 사항** 모듈의 GUID를 지정 합니다.
- 또한 아래 세 키 중 하나를 지정 **해야** 합니다. 이러한 키는 함께 사용할 수 없습니다.
  - `ModuleVersion` -모듈의 허용 가능한 최소 버전을 지정 합니다.
  - `RequiredVersion` -필요한 모듈의 정확한 버전을 지정 합니다.
  - `MaximumVersion` -모듈의 허용 되는 최대 버전을 지정 합니다.

> [!NOTE]
> `RequiredVersion` 는 Windows PowerShell 5.0에 추가 되었습니다.
> `MaximumVersion` 는 Windows PowerShell 5.1에 추가 되었습니다.

예를 들면 다음과 같습니다.

`AzureRM.Netcore`(버전 `0.12.0` 이상)이 설치 되어 있어야 합니다.

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; ModuleVersion="0.12.0" }
```

`AzureRM.Netcore`(버전 **만** `0.12.0` )이 설치 되어 있어야 합니다.

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12.0" }
```

`AzureRM.Netcore`(버전 `0.12.0` 이상)이 설치 되어 있어야 합니다.

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; MaximumVersion="0.12.0" }
```

및의 모든 버전을 `AzureRM.Netcore` `PowerShellGet` 설치 해야 합니다.

```powershell
#Requires -Modules AzureRM.Netcore, PowerShellGet
```

키를 사용 하는 경우 `RequiredVersion` 버전 문자열이 필요한 버전 문자열과 정확 하 게 일치 하는지 확인 합니다.

```powershell
Get-Module AzureRM.Netcore -ListAvailable
```

```Output
    Directory: /home/azureuser/.local/share/powershell/Modules

ModuleType Version Name            PSEdition ExportedCommands
---------- ------- ----            --------- ----------------
Script     0.12.0  AzureRM.Netcore Core
```

**0.12** 는 **0.12.0** 와 정확히 일치 하지 않기 때문에 다음 예제는 실패 합니다.

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12" }
```

#### <a name="-psedition-psedition-name"></a>-PSEdition \<PSEdition-Name\>

스크립트에 필요한 PowerShell 버전을 지정 합니다. 유효한 값은 PowerShell Core에 대 한 **Core** 및 Windows Powershell의 **데스크톱** 입니다.

예를 들면 다음과 같습니다.

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a>-ShellId

스크립트에 필요한 셸을 지정 합니다. 셸 ID를 입력 합니다. **ShellId** 매개 변수를 사용 하는 경우 **add-pssnapin** 매개 변수도 포함 해야 합니다.
자동 변수를 쿼리하여 현재 **ShellId** 을 찾을 수 있습니다 `$ShellId` .

예를 들면 다음과 같습니다.

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> 이 매개 변수는 더 이상 사용 되지 않는 미니 셸에서 사용 하기 위한 것입니다.

#### <a name="-runasadministrator"></a>-RunAsAdministrator

이 스위치 매개 변수는 문에 추가 될 때 스크립트를 실행 하는 `#Requires` PowerShell 세션을 관리자 권한으로 시작 해야 함을 지정 합니다. **RunAsAdministrator** 매개 변수는 Windows 이외의 운영 체제에서 무시 됩니다. **RunAsAdministrator** 매개 변수는 PowerShell 4.0에서 도입 되었습니다.

다음은 그 예입니다.

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a>예

다음 스크립트에는 두 개의 `#Requires` 문이 있습니다. 두 문에 지정 된 요구 사항이 충족 되지 않으면 스크립트가 실행 되지 않습니다. 각 `#Requires` 문은 줄의 첫 번째 항목 이어야 합니다.

```powershell
#Requires -Modules AzureRM.Netcore
#Requires -Version 6.0
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a>참고 항목

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Language_Keywords](about_Language_Keywords.md)


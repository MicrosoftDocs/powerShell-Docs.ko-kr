---
ms.date: 10/16/2019
ms.topic: reference
title: PowerShell 모듈 매니페스트를 작성하는 방법
description: PowerShell 모듈 매니페스트를 작성하는 방법
ms.openlocfilehash: 42db71968ccac1cc3c1c05c5be2e72327e5e28d9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647703"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>PowerShell 모듈 매니페스트를 작성 하는 방법

PowerShell 모듈을 작성 한 후 모듈에 대 한 정보를 포함 하는 선택적 모듈 매니페스트를 추가할 수 있습니다. 예를 들어 작성자를 설명 하 고 모듈의 파일 (예: 중첩 모듈)을 지정 하 고, 스크립트를 실행 하 여 사용자 환경을 사용자 지정 하 고, 형식 및 서식 파일을 로드 하 고, 시스템 요구 사항을 정의 하 고, 모듈이 내보내는 멤버를 제한할 수 있습니다.

## <a name="creating-a-module-manifest"></a>모듈 매니페스트 만들기

모듈 **매니페스트** 는 모듈 `.psd1` 의 내용을 설명 하 고 모듈이 처리 되는 방법을 결정 하는 PowerShell 데이터 파일 ()입니다. 매니페스트 파일은 키와 값의 해시 테이블을 포함 하는 텍스트 파일입니다. 매니페스트 이름을 모듈과 동일 하 게 지정 하 고 모듈의 루트 디렉터리에 매니페스트를 저장 하 여 매니페스트 파일을 모듈에 연결 합니다.

단일 어셈블리나 이진 어셈블리만 포함 하는 간단한 모듈의 경우 `.psm1` 모듈 매니페스트는 선택 사항입니다. 그러나 가능 하면 항상 모듈 매니페스트를 사용 하는 것이 좋습니다 .이는 코드를 구성 하 고 버전 관리 정보를 유지 하는 데 유용 합니다. 그리고 모듈 매니페스트는 [전역 어셈블리 캐시](/dotnet/framework/app-domains/gac)에 설치 된 어셈블리를 내보내는 데 필요 합니다. 모듈 매니페스트는 업데이트할 수 있는 도움말 기능을 지 원하는 모듈에도 필요 합니다. 업데이트할 수 있는 도움말은 모듈 매니페스트의 **HelpInfoUri** 키를 사용 하 여 모듈에 대 한 업데이트 된 도움말 파일의 위치를 포함 하는 도움말 정보 (HelpInfo XML) 파일을 찾습니다. 업데이트할 수 있는 도움말에 대 한 자세한 내용은 업데이트할 수 있는 [도움말 지원](./supporting-updatable-help.md)을 참조 하세요.

### <a name="to-create-and-use-a-module-manifest"></a>모듈 매니페스트를 만들고 사용 하려면

1. 모듈 매니페스트를 만드는 가장 좋은 방법은 [new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet을 사용 하는 것입니다. 매개 변수를 사용 하 여 매니페스트의 기본 키 및 값 중 하나 이상을 지정할 수 있습니다. 유일한 요구 사항은 파일의 이름을로 하는 것입니다. `New-ModuleManifest` 지정 된 값을 사용 하 여 모듈 매니페스트를 만들고 나머지 키와 해당 기본값을 포함 합니다. 여러 모듈을 만들어야 하는 경우를 사용 `New-ModuleManifest` 하 여 다른 모듈에 대해 수정할 수 있는 모듈 매니페스트 템플릿을 만듭니다. 기본 모듈 매니페스트의 예제는 [샘플 모듈 매니페스트](#sample-module-manifest)를 참조 하세요.

   `New-ModuleManifest -Path C:\myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   대신, 필요한 최소한의 정보 인 **ModuleVersion** 을 사용 하 여 모듈 매니페스트의 해시 테이블을 수동으로 만들 수 있습니다. 모듈과 동일한 이름으로 파일을 저장 하 고 파일 확장명을 사용 합니다 `.psd1` . 그런 다음 파일을 편집 하 고 적절 한 키 및 값을 추가할 수 있습니다.

1. 매니페스트 파일에 원하는 추가 요소를 추가 합니다.

   매니페스트 파일을 편집 하려면 원하는 텍스트 편집기를 사용 합니다. 그러나 매니페스트 파일은 코드를 포함 하는 스크립트 파일 이므로 스크립팅 또는 개발 환경 (예: Visual Studio Code)에서 편집할 수 있습니다. 매니페스트 파일의 모든 요소는 선택 사항이 며 **ModuleVersion** 번호를 제외 하 고는 선택 사항입니다.

   모듈 매니페스트에 포함할 수 있는 키와 값에 대 한 설명은 [모듈 매니페스트 요소](#module-manifest-elements) 표를 참조 하세요. 자세한 내용은 [new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet의 매개 변수 설명을 참조 하십시오.

1. 기본 모듈 매니페스트 요소에서 다루지 않을 수 있는 시나리오를 해결 하기 위해 모듈 매니페스트에 코드를 추가 하는 옵션이 있습니다.

   보안을 위해 PowerShell은 모듈 매니페스트 파일에서 사용 가능한 작업의 작은 하위 집합만 실행 합니다. 일반적으로 `if` 문, 산술 및 비교 연산자와 기본 PowerShell 데이터 형식을 사용할 수 있습니다.

1. 모듈 매니페스트를 만든 후에는이를 테스트 하 여 매니페스트에 설명 된 경로가 올바른지 확인할 수 있습니다. 모듈 매니페스트를 테스트 하려면 [new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest)를 사용 합니다.

   `Test-ModuleManifest myModuleName.psd1`

1. 모듈 매니페스트가 포함 된 디렉터리의 최상위 수준에 있어야 합니다.

   모듈을 시스템에 복사 하 고 가져오는 경우 PowerShell은 모듈 매니페스트를 사용 하 여 모듈을 가져옵니다.

1. 필요에 따라 매니페스트 자체를 점으로 [소싱 하 여 import-module을 호출](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 하 여 모듈 매니페스트를 직접 테스트할 수 있습니다.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>모듈 매니페스트 요소

다음 표에서는 모듈 매니페스트에 포함할 수 있는 요소에 대해 설명 합니다.

|요소|기본값|설명|
|-------------|-------------|-----------------|
|**RootModule**<br /> 형식: `String`|`<empty string>`|이 매니페스트와 연결 된 스크립트 모듈 또는 이진 모듈 파일입니다. 이전 버전의 PowerShell에서는이 요소를 **ModuleToProcess** 합니다.<br /> 루트 모듈에 사용할 수 있는 형식은 **매니페스트** 모듈, 스크립트 모듈 이름 ( `.psm1` ) 또는 이진 모듈 (또는)의 이름을 만드는 비어 있을 수 있습니다 `.exe` `.dll` . `.psd1`이 요소에 모듈 매니페스트 () 또는 스크립트 파일 ()의 이름을 배치 `.ps1` 하면 오류가 발생 합니다. <br /> 예: `RootModule = 'ScriptModule.psm1'`|
|**ModuleVersion**<br /> 형식: `Version`|`'0.0.1'`|이 모듈의 버전 번호입니다. 값을 지정 하지 않으면는 `New-ModuleManifest`   기본값을 사용 합니다. 문자열은 예를 들어 형식으로 변환할 수 있어야 합니다 `Version` `#.#.#.#.#` . `Import-Module` 이름에 일치 하는 **$PSModulePath** 에서 찾은 첫 번째 모듈을 로드 하 고, 적어도 **ModuleVersion** 을 **MinimumVersion** 매개 변수로 포함 합니다. 특정 버전을 가져오려면 `Import-Module` cmdlet의 **RequiredVersion** 매개 변수를 사용 합니다.<br /> 예: `ModuleVersion = '1.0'`|
|**GUID**<br /> 형식: `GUID`|`'<GUID>'`|이 모듈을 고유 하 게 식별 하는 데 사용 되는 ID입니다. 값을 지정 하지 않으면 `New-ModuleManifest` 경로도는 값을 지정 합니다. 현재는 **GUID** 로 모듈을 가져올 수 없습니다. <br /> 예: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|**작성자**<br /> 형식: `String`|`'<Current user>'`|이 모듈의 작성자입니다. 값을 지정 하지 않으면는 `New-ModuleManifest` 현재 사용자를 사용 합니다. <br /> 예: `Author = 'AuthorNameHere'`|
|**CompanyName**<br /> 형식: `String`|`'Unknown'`|이 모듈의 회사 또는 공급 업체입니다. 값을 지정 하지 않으면는 `New-ModuleManifest` 기본값을 사용 합니다.<br /> 예: `CompanyName = 'Fabrikam'`|
|**Copyright**<br /> 형식: `String`|`'(c) <Author>. All rights reserved.'`| 이 모듈에 대 한 Copyright 문입니다. 값을 지정 하지 않으면 `New-ModuleManifest` 는 현재 사용자를으로 사용 하 여 기본값을 사용 합니다 `<Author>` . 작성자를 지정 하려면 **author** 매개 변수를 사용 합니다. <br /> 예: `Copyright = '2019 AuthorName. All rights reserved.'`|
|**설명**<br /> 형식: `String`|`<empty string>`|이 모듈에서 제공 하는 기능에 대 한 설명입니다.<br /> 예: `Description = 'This is the module's description.'`|
|**PowerShellVersion**<br /> 형식: `Version`|`<empty string>`|이 모듈에 필요한 PowerShell 엔진의 최소 버전입니다. 유효한 값은 1.0, 2.0, 3.0, 4.0, 5.0, 5.1, 6 및 7입니다.<br /> 예: `PowerShellVersion = '5.0'`|
|**PowerShellHostName**<br /> 형식: `String`|`<empty string>`|이 모듈에 필요한 PowerShell 호스트의 이름입니다. 이 이름은 PowerShell에서 제공 됩니다. 프로그램에서 호스트 프로그램의 이름을 찾으려면를 입력 `$host.name` 합니다.<br /> 예: `PowerShellHostName = 'ConsoleHost'`|
|**PowerShellHostVersion**<br /> 형식: `Version`|`<empty string>`|이 모듈에 필요한 PowerShell 호스트의 최소 버전입니다.<br /> 예: `PowerShellHostVersion = '2.0'`|
|**DotNetFrameworkVersion**<br /> 형식: `Version`|`<empty string>`|이 모듈에 필요한 Microsoft .NET Framework의 최소 버전입니다. 이 필수 구성 요소는 powershell 데스크톱 버전에만 유효 합니다 (예: PowerShell 5.1).<br /> 예: `DotNetFrameworkVersion = '3.5'`|
|**CLRVersion**<br /> 형식: `Version`|`<empty string>`|이 모듈에 필요한 CLR (공용 언어 런타임)의 최소 버전입니다. 이 필수 구성 요소는 powershell 데스크톱 버전에만 유효 합니다 (예: PowerShell 5.1).<br /> 예: `CLRVersion = '3.5'`|
|**ProcessorArchitecture**<br /> 형식: `ProcessorArchitecture`|`<empty string>`|이 모듈에 필요한 프로세서 아키텍처 (없음, X86, Amd64)입니다. 유효한 값은 x86, AMD64, Arm, IA64, MSIL 및 None (알 수 없음 또는 지정 되지 않음)입니다.<br /> 예: `ProcessorArchitecture = 'x86'`|
|**RequiredModules**<br /> 형식: `Object[]`|`@()`|모듈을 가져오기 전에 전역 환경으로 가져와야 합니다. 이렇게 하면 아직 로드 되지 않은 경우 나열 된 모든 모듈이 로드 됩니다. 예를 들어 일부 모듈은 다른 모듈에 의해 이미 로드되어 있을 수 있습니다. 대신를 사용 하 여 로드할 특정 버전을 지정할 수 있습니다 `RequiredVersion` `ModuleVersion` . `ModuleVersion`을 사용 하는 경우 최소 버전의를 사용 하 여 사용 가능한 최신 버전을 로드 합니다. 매개 변수 값에서 문자열과 해시 테이블을 결합할 수 있습니다.<br /> 예: `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; ModuleVersion="2.0"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /> 예: `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; RequiredVersion="1.5"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|**RequiredAssemblies**<br /> 형식: `String[]`|`@()`|이 모듈을 가져오기 전에 로드 해야 하는 어셈블리입니다. `.dll`모듈에 필요한 어셈블리 () 파일 이름을 지정 합니다.<br /> PowerShell은 형식 또는 형식을 업데이트 하거나, 중첩 모듈을 가져오거나, RootModule 키 값에 지정 된 모듈 파일을 가져오기 전에 지정 된 어셈블리를 로드 합니다. 이 매개 변수를 사용 하 여 모듈에 필요한 모든 어셈블리를 나열 합니다.<br /> 예: `RequiredAssemblies = @("assembly1.dll", "assembly2.dll", "assembly3.dll")`|
|**매니페스트의 scriptstoprocess**<br /> 형식: `String[]`|`@()`|`.ps1`모듈을 가져올 때 호출자의 세션 상태에서 실행 되는 스크립트 () 파일입니다. 전역 세션 상태 이거나 중첩 된 모듈의 경우 다른 모듈의 세션 상태 일 수 있습니다. 스크립트에서 로그를 사용 하는 것 처럼 이러한 스크립트를 사용 하 여 환경을 준비할 수 있습니다.<br /> 이러한 스크립트는 매니페스트에 나열 된 모듈이 로드 되기 전에 실행 됩니다. <br /> 예: `ScriptsToProcess = @("script1.ps1", "script2.ps1", "script3.ps1")`|
|**TypesToProcess**<br /> 형식: `String[]`|`@()`|`.ps1xml`이 모듈을 가져올 때 로드할 파일 ()을 입력 합니다. <br /> 예: `TypesToProcess = @("type1.ps1xml", "type2.ps1xml", "type3.ps1xml")`|
|**FormatsToProcess**<br /> 형식: `String[]`|`@()`|`.ps1xml`이 모듈을 가져올 때 로드할 서식 파일 ()입니다. <br /> 예: `FormatsToProcess = @("format1.ps1xml", "format2.ps1xml", "format3.ps1xml")`|
|**NestedModules**<br /> 형식: `Object[]`|`@()`|**RootModule** 에 지정 된 모듈의 중첩 모듈로 가져올 모듈 (Alias:**ModuleToProcess**).<br /> 이 요소에 모듈 이름을 추가 하는 것은 `Import-Module` 스크립트나 어셈블리 코드 내에서를 호출 하는 것과 비슷합니다. 매니페스트 파일을 사용 하는 주요 차이점은 로드 하는 항목을 쉽게 확인할 수 있다는 것입니다. 그리고 모듈이 로드 되지 않으면 실제 모듈이 아직 로드 되지 않은 것입니다.<br /> 다른 모듈 외에도 여기에 스크립트 () 파일을 로드할 수 있습니다 `.ps1` . 이러한 파일은 루트 모듈의 컨텍스트에서 실행 됩니다. 이는 루트 모듈의 스크립트에 대 한 점을 소싱 하는 것과 같습니다. <br /> 예: `NestedModules = @("script.ps1", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FunctionsToExport**<br /> 형식: `String[]`|`@()`|이 모듈에서 내보낼 함수를 지정 합니다. 최상의 성능을 위해 와일드 카드를 사용 하지 않고 항목을 삭제 하지 않습니다. 내보낼 함수가 없는 경우 빈 배열을 사용 합니다. 기본적으로 함수는 내보내지 않습니다. 이 키를 사용 하 여 모듈에서 내보낸 함수를 나열할 수 있습니다.<br /> 모듈은 함수를 호출자의 세션 상태로 내보냅니다. 호출자의 세션 상태는 전역 세션 상태 이거나 중첩 된 모듈의 경우 다른 모듈의 세션 상태 일 수 있습니다. 중첩 모듈을 연결 하는 경우 체인의 모듈이 **Functionstoexport** 키를 사용 하 여 함수를 제한 하지 않는 한 중첩 된 모듈에서 내보낸 모든 함수를 전역 세션 상태로 내보냅니다.<br /> 매니페스트가 함수에 대 한 별칭을 내보내는 경우이 키는 별칭을 **AliasesToExport** 키에 나열 하는 함수를 제거할 수 있지만이 키는 함수 별칭을 목록에 추가할 수 없습니다. <br /> 예: `FunctionsToExport = @("function1", "function2", "function3")`|
|**CmdletsToExport**<br /> 형식: `String[]`|`@()`|이 모듈에서 내보낼 cmdlet을 지정 합니다. 최상의 성능을 위해 와일드 카드를 사용 하지 않고 항목을 삭제 하지 마세요. 내보낼 cmdlet이 없으면 빈 배열을 사용 합니다. 기본적으로 cmdlet은 내보내지지 않습니다. 이 키를 사용 하 여 모듈에서 내보낸 cmdlet을 나열할 수 있습니다.<br /> 호출자의 세션 상태는 전역 세션 상태 이거나 중첩 된 모듈의 경우 다른 모듈의 세션 상태 일 수 있습니다. 중첩 모듈을 연결 하는 경우 체인의 모듈에서 **Cmdletstoexport** 키를 사용 하 여 cmdlet을 제한 하지 않는 한 중첩 된 모듈에서 내보낸 모든 cmdlet을 전역 세션 상태로 내보냅니다.<br /> 매니페스트가 cmdlet에 대 한 별칭을 내보내는 경우이 키는 별칭을 **AliasesToExport** 키에 나열 하는 cmdlet을 제거할 수 있지만이 키가 목록에 cmdlet 별칭을 추가할 수는 없습니다. <br /> 예: `CmdletsToExport = @("Get-MyCmdlet", "Set-MyCmdlet", "Test-MyCmdlet")`|
|**VariablesToExport**<br /> 형식: `String[]`|`'*'`|모듈이 호출자의 세션 상태로 내보내는 변수를 지정 합니다. 와일드카드 문자를 사용할 수 있습니다. 기본적으로 모든 변수 ( `'*'` )를 내보냅니다. 이 키를 사용 하 여 모듈에서 내보내는 변수를 제한할 수 있습니다.<br /> 호출자의 세션 상태는 전역 세션 상태 이거나 중첩 된 모듈의 경우 다른 모듈의 세션 상태 일 수 있습니다. 중첩 모듈을 연결 하는 경우 체인의 모듈이 **VariablesToExport** 키를 사용 하 여 변수를 제한 하지 않는 한 중첩 된 모듈에서 내보낸 모든 변수는 전역 세션 상태로 내보내집니다.<br /> 매니페스트가 변수에 대 한 별칭을 내보내는 경우이 키는 별칭을 **AliasesToExport** 키에 나열 하는 변수를 제거할 수 있지만이 키는 변수 별칭을 목록에 추가할 수 없습니다. <br /> 예: `VariablesToExport = @('$MyVariable1', '$MyVariable2', '$MyVariable3')`|
|**AliasesToExport**<br /> 형식: `String[]`|`@()`|이 모듈에서 내보낼 별칭을 지정 합니다. 최상의 성능을 위해 와일드 카드를 사용 하지 않고 항목을 삭제 하지 마세요. 내보낼 별칭이 없으면 빈 배열을 사용 하십시오. 기본적으로 별칭은 내보내지지 않습니다. 이 키를 사용 하 여 모듈에서 내보내는 별칭을 나열할 수 있습니다.<br /> 모듈이 호출자의 세션 상태로 별칭을 내보냅니다. 호출자의 세션 상태는 전역 세션 상태 이거나 중첩 된 모듈의 경우 다른 모듈의 세션 상태 일 수 있습니다. 중첩 된 모듈을 연결 하는 경우 체인의 모듈이 **AliasesToExport** 키를 사용 하 여 별칭을 제한 하지 않는 한 중첩 된 모듈에서 내보낸 모든 별칭은 궁극적으로 전역 세션 상태로 내보내집니다. <br /> 예: `AliasesToExport = @("MyAlias1", "MyAlias2", "MyAlias3")`|
|**DscResourcesToExport**<br /> 형식: `String[]`|`@()`|이 모듈에서 내보낼 DSC 리소스를 지정 합니다. 와일드카드가 지원됩니다. <br /> 예: `DscResourcesToExport = @("DscResource1", "DscResource2", "DscResource3")`|
|**ModuleList**<br /> 형식: `Object[]`|`@()`|이 모듈을 사용 하 여 패키지 된 모든 모듈을 지정 합니다. 이러한 모듈은 이름으로 입력 하거나 쉼표로 구분 된 문자열을 사용 하 여 입력 하거나 **ModuleName** 및 **GUID** 키가 포함 된 해시 테이블로 입력할 수 있습니다. 해시 테이블에는 선택적 **ModuleVersion** 키도 있을 수 있습니다. **Modulelist** 키는 모듈 인벤토리 역할을 하도록 디자인 되었습니다. 이러한 모듈은 자동으로 처리 되지 않습니다. <br /> 예: `ModuleList = @("SampleModule", "MyModule", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FileList**<br /> 형식: `String[]`|`@()`|이 모듈과 함께 패키지 된 모든 파일의 목록입니다. **Modulelist** 와 마찬가지로 **FileList** 는 인벤토리 목록이 며 달리 처리 되지 않습니다. <br /> 예: `FileList = @("File1", "File2", "File3")`|
|**PrivateData**<br /> 형식: `Object`|`@{...}`|**RootModule** (Alias: **ModuleToProcess**) 키로 지정 된 루트 모듈에 전달 되어야 하는 개인 데이터를 지정 합니다. **PrivateData** 는 **Tags**, **LicenseUri**, **ProjectURI**, **IconUri**, **ReleaseNotes**, **시험판**, **RequireLicenseAcceptance** 및 **ExternalModuleDependencies** 등 여러 요소로 구성 된 해시 테이블입니다. |
|**태그** <br /> 형식: `String[]` |`@()`| 태그는 온라인 갤러리의 모듈 검색에 도움이 됩니다. <br /> 예: `Tags = "PackageManagement", "PowerShell", "Manifest"`|
|**LicenseUri**<br /> 형식: `Uri` |`<empty string>`| 이 모듈의 라이선스에 대 한 URL입니다. <br /> 예: `LicenseUri = 'https://www.contoso.com/license'`|
|**ProjectUri**<br /> 형식: `Uri` |`<empty string>`| 이 프로젝트의 기본 웹 사이트에 대 한 URL입니다. <br /> 예: `ProjectUri = 'https://www.contoso.com/project'`|
|**IconUri**<br /> 형식: `Uri` |`<empty string>`| 이 모듈을 나타내는 아이콘의 URL입니다. <br /> 예: `IconUri = 'https://www.contoso.com/icons/icon.png'`|
|**ReleaseNotes**<br /> 형식: `String` |`<empty string>`| 모듈의 릴리스 정보를 지정 합니다. <br /> 예: `ReleaseNotes = 'The release notes provide information about the module.`|
|**시험판**<br /> 형식: `String` |`<empty string>`| 이 매개 변수는 PowerShellGet 1.6.6에 추가 되었습니다. 온라인 갤러리에서 모듈을 시험판 버전으로 식별 하는 **시험판** 문자열입니다. <br /> 예: `PreRelease = 'This module is a prerelease version.`|
|**RequireLicenseAcceptance**<br /> 형식: `Boolean`|`$true`| 이 매개 변수는 PowerShellGet 1.5에 추가 되었습니다. 모듈에서 설치, 업데이트 또는 저장에 대 한 명시적 사용자 동의가 필요한 지 여부를 나타내는 플래그입니다. <br /> 예: `RequireLicenseAcceptance = $false`|
|**ExternalModuleDependencies**<br /> 형식: `String[]` |`@()`| 이 매개 변수는 PowerShellGet v2에서 추가 되었습니다. 이 모듈이 종속 된 외부 모듈의 목록입니다. <br /> 예: `ExternalModuleDependencies =  @("ExtModule1", "ExtModule2", "ExtModule3")`|
|**HelpInfoURI**<br /> 형식: `String`|`<empty string>`|이 모듈의 HelpInfo URI입니다. <br /> 예: `HelpInfoURI = 'https://www.contoso.com/help'`|
|**DefaultCommandPrefix**<br /> 형식: `String`|`<empty string>`|이 모듈에서 내보낸 명령의 기본 접두사입니다. 을 사용 하 여 기본 접두사를 재정의 `Import-Module -Prefix` 합니다. <br /> 예: `DefaultCommandPrefix = 'My'`|

## <a name="sample-module-manifest"></a>샘플 모듈 매니페스트

다음 샘플 모듈 매니페스트는 `New-ModuleManifest` PowerShell 7에서를 사용 하 여 만들어졌으며 기본 키 및 값을 포함 합니다.

```powershell
#
# Module manifest for module 'SampleModuleManifest'
#
# Generated by: User01
#
# Generated on: 10/15/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b632e90c-df3d-4340-9f6c-3b832646bf87'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{

    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # Prerelease string of this module
        # Prerelease = ''

        # Flag to indicate whether the module requires explicit user acceptance for install/update/save
        RequireLicenseAcceptance = $true

        # External dependent modules of this module
        # ExternalModuleDependencies = @()

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}
```

## <a name="see-also"></a>참고 항목

[about_Comparison_Operators](/powershell/module/microsoft.powershell.core/about/about_comparison_operators)

[about_If](/powershell/module/microsoft.powershell.core/about/about_if)

[전역 어셈블리 캐시](/dotnet/framework/app-domains/gac)

[모듈 가져오기](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest)

[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest)

[Update-ModuleManifest](/powershell/module/powershellget/update-modulemanifest)

[Windows PowerShell 모듈 작성](./writing-a-windows-powershell-module.md)

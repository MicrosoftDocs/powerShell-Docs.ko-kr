---
title: PowerShell 모듈 매니페스트를 작성 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 93a8c11099a9883127bca87422e1acaebfd2c093
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670290"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>PowerShell 모듈 매니페스트를 작성하는 방법

작성 한 후 Windows PowerShell 모듈, 모듈 매니페스트를 추가할 수도 있습니다. 모듈 매니페스트는 모듈에 대 한 정보를 포함 하 여 PowerShell 스크립트 파일. 예를 들어 작성자에 설명, 사용자의 환경에 맞게 스크립트를 실행 하는 모듈 (예: 중첩된 모듈의 경우)의 파일 형식 및 형식 지정 파일을 로드, 시스템 요구 사항 정의 및 모듈이 내보내는 멤버를 제한 지정 수 있습니다.

## <a name="creating-a-module-manifest"></a>모듈 매니페스트 만들기

A *모듈 매니페스트* 은 모듈의 내용을 설명 하 고 모듈 처리 방법을 결정 하는 Windows PowerShell 데이터 파일 (.psd1)입니다. 매니페스트 파일 자체는 키와 값의 해시 테이블을 포함 하는 텍스트 파일입니다. 모듈을 같은 이름 지정 및 모듈 디렉터리의 루트에 배치 하 여 매니페스트 파일을 모듈에 연결 합니다.

단일. psm1 또는 이진 어셈블리를 포함 하는 간단한 모듈, 모듈 매니페스트를 선택 사항입니다. 그러나 버전 관리 정보를 유지 관리 하 여 코드를 구성 하는 데 유용한 되므로 가능 하면 모듈 매니페스트를 사용 하는 것이 좋습니다. 또한 모듈 매니페스트를 전역 어셈블리 캐시에 설치 된 어셈블리를 내보냅니다 해야 합니다. 모듈 매니페스트를 업데이트할 수 있는 도움말 기능을 지 원하는 모듈에도 필요 합니다. 즉, 업데이트할 수 있는 도움말 사용 합니다 **HelpInfoUri** 모듈 매니페스트는 모듈에 대 한 업데이트 된 도움말 파일의 위치를 포함 하는 도움말 정보 (HelpInfo XML) 파일을 찾을 수에서 키입니다. 업데이트할 수 있는 도움말에 대 한 자세한 내용은 참조 하세요. [업데이트 가능한 도움말 지원](./supporting-updatable-help.md)합니다.

### <a name="to-create-and-use-a-module-manifest"></a>만들고 모듈 매니페스트를 사용 합니다.

1. 모듈 매니페스트를 만들려면 몇 가지 옵션이 있습니다.

   1. 직접 필요한 최소한의 정보를 사용 하 여 해시 테이블을 만들 고 모듈 이름이 동일한. psd1 파일에 저장 합니다. 이 작업을 수행한 후 파일을 열고 적절 한 값을 수동으로 추가할 수 있습니다.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. 또는 호출을 [New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) 하나 이상의 기본 값을 사용 하 여 cmdlet을 매개 변수로 전달 합니다. 그러나 (유의 합니다 매니페스트를 생성 하는 데 필요한 파일의 이름을 합니다.) 이 모든 매니페스트 값으로 사용자가 제공한 명시적으로 지정 및 적절 한 기본값을 포함 하는 rest를 사용 하 여 모듈 매니페스트를 만듭니다.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. 마지막으로, 있습니다 수도 빈. psd1 파일을이 항목의 맨 아래에 있는 템플릿 파일을 복사 만들고 관련 값을 입력 합니다. 이 경우 유일한 요구 사항은 모듈과 동일한 파일의 이름은 되도록 것입니다.

2. 매니페스트 파일에 원하는 모든 추가 요소에 추가 합니다.

   일반적으로 아마도 이렇게 메모장과 같은 원하는 어떤 텍스트 편집기에서. 그러나 기술적으로 이것이 실제 스크립팅 또는 개발 환경에서 PowerShell ISE 같은 편집 하려고 하므로 코드를 포함 하는 스크립트 파일입니다. 매니페스트 파일의 모든 요소는 선택 사항, ModuleVersion 번호를 제외 하 고 참고 다시 합니다.

   키 및 모듈 매니페스트의 있습니다 값의 설명에 대 한 참조를 **모듈 매니페스트 요소** 아래. 자세한 내용은 매개 변수 설명을 참조 합니다 [New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet.

3. 필요에 따라 추가 코드는 기본 모듈 매니페스트 요소에서 다룰 수 없는 모든 시나리오를 해결 하 여 모듈 매니페스트를 추가할 수 있습니다.

   보안 문제로 인해 PowerShell 모듈 매니페스트 파일에서 사용 가능한 작업의 작은 하위 집합만을 실행 됩니다. 일반적으로 사용할 수 있습니다 합니다 **경우** 문, 산술 및 비교 연산자 및 기본 PowerShell 데이터 형식입니다.

4. 프로그램 모듈 매니페스트를 만든 후 테스트할 수 있습니다 (매니페스트는에 설명 된 모든 경로가 올바른지 확인)를 호출 하 여 [Test-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest)합니다.

   `Test-ModuleManifest myModuleName.psd1`

5. 프로그램 모듈 매니페스트가 모듈을 포함 하는 디렉터리의 최상위 수준에 있는지 확인 해야 합니다.

   시스템에 모듈을 복사 하 고 가져올 때 PowerShell 모듈을 가져올 모듈 매니페스트를 사용 합니다.

6. 필요에 따라 프로그램 모듈 매니페스트를 호출 하 여 직접 테스트할 수 있습니다 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 도트 소싱 매니페스트 자체에서.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>모듈 매니페스트 요소

다음 표에서 모듈 매니페스트의 있습니다 요소를 설명 합니다.

|요소|Default|설명|
|-------------|-------------|-----------------|
|RootModule<br /><br /> 형식: 문자열|' '|스크립트 모듈 또는 이진 모듈 파일이이 매니페스트에 연결 된입니다. 이전 버전의 PowerShell이이 요소는 ModuleToProcess를 호출 합니다.<br /><br /> 루트 모듈에 대해 가능한 유형을 비워둘 수 (있는 이해를 돕기 위해를 **매니페스트** 모듈), 스크립트 모듈의 이름 (이 수 있습니다. psm1는 **스크립트** 모듈), 또는 이진 모듈 (.exe 또는.dll의 이름 그러면이 **이진** 모듈). 모듈 매니페스트 (.psd1) 또는 스크립트 파일 (.ps1) 이름을이 요소에 배치 하면 오류가 발생 합니다.|
|ModuleVersion<br /><br /> 형식: 문자열|1.0|이 모듈의 버전 번호입니다. 문자열 [System.Version]로 변환할 수 있어야 합니다. 즉, ' #. #. #. #. #'. `Import-Module` 찾은 첫 번째 모듈을 로드 합니다는 **$psModulePath** 는 이름과 일치 하는 및를 최소한으로 높은 ModuleVersion에는 `-MinimumVersion` 매개 변수입니다. 특정 버전을 가져오려면는`-RequiredVersion` 매개 변수를 대신 합니다.<br /><br /> 예: `ModuleVersion = '1.0'`|
|GUID<br /><br /> 형식: 문자열|자동 생성 된 GUID|이 모듈을 고유 하 게 식별 하는 데 사용 하는 ID입니다. 참고는 현재 GUID 기준으로 모듈을 가져올 수 없습니다.<br /><br /> 예: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Author<br /><br /> 형식: 문자열|없음|이 모듈의 작성자입니다.<br /><br /> 예: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> 형식: 문자열|Unknown|회사 또는이 모듈의 공급 업체입니다.<br /><br /> 예: `CompanyName = 'Fabrikam'`|
|저작권<br /><br /> 형식: 문자열|(c) [currentYear] [작성]. All rights reserved.|이 모듈에 대 한 저작권 정보입니다.<br /><br /> 예: `Copyright = '2016 AuthorName. All rights reserved.'`|
|설명<br /><br /> 형식: 문자열|' '|이 모듈에서 제공 하는 기능에 대 한 설명입니다.<br /><br /> 예: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> 형식: 문자열|' '|이 모듈에 필요한 Windows PowerShell 엔진의 최소 버전입니다. 현재 유효한 값 이며 1.0, 2.0, 3.0, 4.0 및 5.0<br /><br /> 예: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> 형식: 문자열|' '|모듈에 필요한 Windows PowerShell 호스트의 이름을 지정 합니다. 이 이름은 Windows PowerShell에서 제공 됩니다. 프로그램에서 호스트 프로그램의 이름을 찾으려면 입력: `$host.name` 합니다.<br /><br /> 예: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> 형식: 문자열|' '|이 모듈에 필요한 Windows PowerShell 호스트의 최소 버전입니다.<br /><br /> 예: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> 형식: 문자열|' '|이 모듈에 필요한 Microsoft.NET Framework의 최소 버전입니다.<br /><br /> 예: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> 형식: 문자열|' '|이 모듈에 필요한 공용 언어 런타임 (CLR)의 최소 버전입니다.<br /><br /> 예: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> 형식: 문자열|' '|프로세서 아키텍처 (None, X86, Amd64)이이 모듈에 필요한입니다. 유효한 값은 x86, AMD64, IA64 및 None(알 수 없음 또는 지정되지 않음)입니다.<br /><br /> 예: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> 형식: [string []]|@()|이 모듈을 가져오기 전에 전역 환경으로 가져와야 하는 모듈입니다. 가 이미 로드 되지 않은 나열 된 모든 모듈이 로드 됩니다. (예를 들어, 일부 모듈이 이미 로드 수 있습니다 다른 모듈에 의해.). 특정 버전을 사용 하 여 로드를 지정할 수 이기도 `RequiredVersion` 대신 `ModuleVersion`합니다. 사용 하는 경우 `ModuleVersion` 최소 지정 된 버전의 사용 가능한 최신 버전을 로드 됩니다.<br /><br /> 예: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> 예: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> 형식: [string []]|@()|이 모듈을 가져오기 전에 로드 해야 하는 어셈블리입니다.<br /><br /> RequiredModules 달리, 아직 로드 되지 않은 경우 PowerShell을 RequiredAssemblies 로드 됩니다.|
|ScriptsToProcess<br /><br /> 형식: [string []]|@()|모듈을 가져올 때 호출자의 세션 상태에서 실행 되는 스크립트 (.ps1) 파일입니다. 전역 세션 상태 또는 다른 모듈 세션 상태의 중첩된 모듈에 대 한 수 있습니다. 이러한 스크립트를 사용 하 여 로그인 스크립트를 사용할 수도 처럼 환경을 준비할 수 있습니다.<br /><br /> 이러한 스크립트는 매니페스트에 나열 된 모듈 로드 되기 전에 실행 됩니다.|
|TypesToProcess<br /><br /> 형식: [개체 []]|@()|이 모듈을 가져올 때 로드 되도록 파일 (.ps1xml)를 입력 합니다.|
|FormatsToProcess<br /><br /> 형식: [개체 []]|@()|이 모듈을 가져올 때 로드 되도록 파일 (.ps1xml) 서식을 지정 합니다.|
|NestedModules<br /><br /> 형식: [개체 []]|@()|모듈 가져오기 RootModule/ModuleToProcess에 지정 된 모듈의 중첩 된 모듈로입니다.<br /><br /> 모듈 이름을이 요소에 추가 하는 것은 호출 비슷합니다 `Import-Module` 에서 스크립트 또는 어셈블리 코드 내에서. 주요 차이점은 점 쉽게 새로운를 로드 하는 다음 매니페스트 파일에서 볼 수입니다. 또한 모듈을 로드 하지 못하는 여기 있습니다는 아직가 로드 되지 실제 모듈입니다.<br /><br /> 다른 모듈 외에 스크립트 (.ps1) 파일을 로드할 수 있습니다. 이러한 파일은 루트 모듈의 컨텍스트에서 실행 됩니다. (이 경우 도트 소싱 루트 모듈의 스크립트에 해당)|
|FunctionsToExport<br /><br /> 다음을 입력합니다. 문자열|'*'|호출자의 세션 상태로 모듈 (와일드 카드 문자는 허용)을 내보내는 함수를 지정 합니다. 기본적으로 모든 함수는 내보내집니다. 모듈에서 내보낸 함수를 제한 하려면이 키를 사용할 수 있습니다.<br /><br /> 호출자의 세션 상태는 전역 세션 상태 또는 중첩 모듈의 경우 다른 모듈의 세션 상태를 수 있습니다. 중첩된 모듈 체인 중첩된 모듈에서 내보낸 모든 함수는 체인의 모듈 FunctionsToExport 키를 사용 하 여 함수를 제한 하지 않으면 전역 세션 상태를 내보낼 수입니다.<br /><br /> 매니페스트는 또한 함수에 대 한 별칭을 내보냅니다, 경우에이 키 AliasesToExport 키에 해당 별칭은 나열 된 함수를 제거할 수 있지만이 키 목록에 함수 별칭을 추가할 수 없습니다.|
|CmdletsToExport<br /><br /> 다음을 입력합니다. 문자열|'*'|모듈이 내보내는 (와일드 카드 문자는 허용) 하는 cmdlet을 지정 합니다. 기본적으로 모든 cmdlet이 내보내집니다. 모듈에서 내보내는 cmdlet을 제한 하려면이 키를 사용할 수 있습니다.<br /><br /> 호출자의 세션 상태는 전역 세션 상태 또는 중첩 모듈의 경우 다른 모듈의 세션 상태를 수 있습니다. 중첩된 모듈을 연결 하는 경우 중첩된 모듈에서 내보낸 모든 cmdlet은 궁극적으로 내보낼 수 전역 세션 상태 체인에 있는 모듈 CmdletsToExport 키를 사용 하 여 cmdlet을 제한 하지 않으면.<br /><br /> 매니페스트는 또한 cmdlet에 대 한 별칭을 내보냅니다, 경우에이 키 AliasesToExport 키에 해당 별칭은 나열 된 cmdlet를 제거할 수 있지만이 키 목록에 cmdlet 별칭을 추가할 수 없습니다.|
|VariablesToExport<br /><br /> 다음을 입력합니다. 문자열|'*'|호출자의 세션 상태로 모듈이 내보내는 (와일드 카드 문자는 허용) 하는 변수를 지정 합니다. 기본적으로 모든 변수 내보내집니다. 모듈에서 내보내는 변수를 제한 하려면이 키를 사용할 수 있습니다.<br /><br /> 호출자의 세션 상태는 전역 세션 상태 또는 중첩 모듈의 경우 다른 모듈의 세션 상태를 수 있습니다. 중첩된 모듈을 연결 하는 경우 중첩 된 모듈에서 내보낸 모든 변수를 내보낼 전역 세션 상태 체인에 있는 모듈 VariablesToExport 키를 사용 하 여 변수를 제한 하지 않으면.<br /><br /> 매니페스트는 또한 변수에 대 한 별칭을 내보냅니다, 하는 경우이 키 AliasesToExport 키에 해당 별칭은 나열 된 변수를 제거할 수 있지만이 키 목록에 변수 별칭을 추가할 수 없습니다.|
|AliasesToExport<br /><br /> 다음을 입력합니다. 문자열|'*'|호출자의 세션 상태로 모듈 (와일드 카드 문자는 허용)을 내보내는 별칭을 지정 합니다. 기본적으로 모든 별칭 내보내집니다. 모듈에서 내보내는 별칭을 제한 하려면이 키를 사용할 수 있습니다.<br /><br /> 호출자의 세션 상태는 전역 세션 상태 또는 중첩 모듈의 경우 다른 모듈의 세션 상태를 수 있습니다. 중첩된 모듈을 연결 하는 경우 중첩된 모듈에서 내보낸 모든 별칭은 궁극적으로 내보낼 수 전역 세션 상태 체인에 있는 모듈 AliasesToExport 키를 사용 하 여 별칭을 제한 하지 않으면.|
|ModuleList<br /><br /> 형식: [string []]|@()|이 모듈을 사용 하 여 패키지 된 모든 모듈을 지정 합니다. 이러한 모듈 이름 및 GUID 키를 사용 하 여 이름 (쉼표로 구분 된 문자열) 또는 해시 테이블로 입력할 수 있습니다. 해시 테이블에서 선택적 ModuleVersion 키를 가질 수도 있습니다. ModuleList 키 모듈 인벤토리 역할 하도록 설계 되었습니다. 이러한 모듈은 자동으로 처리 되지 않습니다.|
|FileList<br /><br /> 형식: [string []]|@()|이 모듈을 사용 하 여 패키지 된 모든 파일의 목록입니다. ModuleList를 사용 하 여 FileList를 인벤토리 목록으로 도움이 되는 그렇지 않은 경우 처리 되지 않습니다.|
|PrivateData<br /><br /> 형식: [object]|' '|RootModule/ModuleToProcess 키에 지정 된 루트 모듈에 전달 되어야 하는 모든 개인 데이터를 지정 합니다.|
|HelpInfoURI<br /><br /> 형식: 문자열|' '|이 모듈의 HelpInfo URI입니다.|
|DefaultCommandPrefix<br /><br /> 형식: 문자열|' '|명령에 대 한 기본 접두사는이 모듈에서 내보냅니다. 사용 하 여 기본 접두사를 재정의 `Import-Module` -접두사입니다.|

## <a name="sample-module-manifest"></a>샘플 모듈 매니페스트

다음 샘플 모듈 매니페스트는 모듈 매니페스트에서 키와 기본 값을 보여 줍니다. 이 예제를 사용 하 여 만든는 `New-ModuleManifest` Windows PowerShell 3.0에서 cmdlet. 여러 모듈을 만들 때에 다른 모듈에 대 한 다음 수정할 수 있는 매니페스트 템플릿을 만들려면이 cmdlet을 사용할 수 있습니다.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 1/24/2012
#

@{

# Script module or binary module file associated with this manifest
#RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = 'd0a9150d-b6a4-4b17-a325-e3a24fed0aa9'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2012 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of the .NET Framework required by this module
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module
FunctionsToExport = '*'

# Cmdlets to export from this module
CmdletsToExport = '*'

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module
AliasesToExport = '*'

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess
# PrivateData = ''

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 작성](./writing-a-windows-powershell-module.md)

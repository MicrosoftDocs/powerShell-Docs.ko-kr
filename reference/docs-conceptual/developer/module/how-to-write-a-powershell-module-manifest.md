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
ms.openlocfilehash: 1265855b82b0bfaa7b2717c8eb348b822c19f561
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367102"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>PowerShell 모듈 매니페스트를 작성하는 방법

Windows PowerShell 모듈을 작성 한 후 필요에 따라 모듈 매니페스트를 추가할 수 있습니다. 모듈 매니페스트는 모듈에 대 한 정보를 포함 하는 데 사용할 수 있는 PowerShell 스크립트 파일입니다. 예를 들어 작성자를 설명 하 고 모듈의 파일 (예: 중첩 모듈)을 지정 하 고, 스크립트를 실행 하 여 사용자 환경을 사용자 지정 하 고, 형식 및 서식 파일을 로드 하 고, 시스템 요구 사항을 정의 하 고, 모듈이 내보내는 멤버를 제한할 수 있습니다.

## <a name="creating-a-module-manifest"></a>모듈 매니페스트 만들기

*모듈 매니페스트* 는 모듈의 내용을 설명 하 고 모듈이 처리 되는 방법을 결정 하는 Windows PowerShell 데이터 파일 (. psd1)입니다. 매니페스트 파일 자체는 키와 값의 해시 테이블을 포함 하는 텍스트 파일입니다. 매니페스트 파일을 모듈과 동일 하 게 명명 하 고 모듈 디렉터리의 루트에 배치 하 여 모듈에 연결 합니다.

단일 .psm1 또는 이진 어셈블리만 포함 하는 간단한 모듈의 경우 모듈 매니페스트는 선택 사항입니다. 그러나 가능 하면 항상 모듈 매니페스트를 사용 하는 것이 좋습니다 .이는 코드를 구성 하 고 버전 관리 정보를 유지 하는 데 유용 합니다. 또한 모듈 매니페스트는 전역 어셈블리 캐시에 설치 된 어셈블리를 내보내는 데 필요 합니다. 모듈 매니페스트는 업데이트할 수 있는 도움말 기능을 지 원하는 모듈에도 필요 합니다. 즉, 업데이트할 수 있는 도움말에서 모듈 매니페스트의 **HelpInfoUri** 키를 사용 하 여 모듈에 대 한 업데이트 된 도움말 파일의 위치를 포함 하는 도움말 정보 (HelpInfo XML) 파일을 찾습니다. 업데이트할 수 있는 도움말에 대 한 자세한 내용은 업데이트할 수 있는 [도움말 지원](./supporting-updatable-help.md)을 참조 하세요.

### <a name="to-create-and-use-a-module-manifest"></a>모듈 매니페스트를 만들고 사용 하려면

1. 모듈 매니페스트를 만들려면 다음과 같은 몇 가지 옵션을 사용할 수 있습니다.

   1. 필요한 최소한의 정보를 사용 하 여 해시 테이블을 직접 만들고 모듈과 이름이 같은 psd1 파일에 저장 합니다. 이 작업을 완료 한 후에는 파일을 열고 적절 한 값을 수동으로 추가할 수 있습니다.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. 또는 매개 변수로 전달 된 하나 이상의 기본값을 사용 하 여 [new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet을 호출 합니다. 그러나 매니페스트를 생성 하는 데 파일의 이름만 필요 합니다. 이렇게 하면 명시적으로 지정 된 모든 매니페스트 값과 적절 한 기본값을 포함 하는 rest를 사용 하 여 모듈 매니페스트를 만듭니다.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. 마지막으로, psd1 파일을 만들고이 항목의 맨 아래에 있는 템플릿을 파일에 복사 하 고 관련 값을 입력할 수도 있습니다. 이 경우에는 파일의 이름을 모듈과 동일 하 게 지정 해야 합니다.

2. 파일에 포함 하려는 매니페스트에 추가 요소를 추가 합니다.

   일반적으로 메모장과 같은 텍스트 편집기에서이 작업을 수행할 수 있습니다. 그러나이는 기술적으로 코드를 포함 하는 스크립트 파일 이므로 실제 스크립팅 또는 개발 환경 (예: Visual Studio Code)에서 편집할 수 있습니다. 매니페스트 파일의 모든 요소는 ModuleVersion 번호를 제외 하 고는 선택 사항입니다.

   모듈 매니페스트에 포함할 수 있는 키와 값에 대 한 설명은 아래의 **모듈 매니페스트 요소** 를 참조 하세요. 자세한 내용은 [new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet의 매개 변수 설명을 참조 하십시오.

3. 필요에 따라 모듈 매니페스트에 추가 코드를 추가 하 여 기본 모듈 매니페스트 요소에서 다루지 않는 시나리오를 처리할 수 있습니다.

   보안 문제로 인해 PowerShell은 모듈 매니페스트 파일에서 사용 가능한 작업의 작은 하위 집합만 실행 합니다. 일반적으로 **if** 문, 산술 연산자, 비교 연산자 및 기본 PowerShell 데이터 형식을 사용할 수 있습니다.

4. 모듈 매니페스트를 만들었으면 테스트 하 여 [new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest)에 대 한 호출을 통해 매니페스트에 설명 된 경로가 올바른지 확인할 수 있습니다.

   `Test-ModuleManifest myModuleName.psd1`

5. 모듈 매니페스트가 포함 된 디렉터리의 최상위 수준에 있어야 합니다.

   모듈을 시스템에 복사 하 고 가져오는 경우 PowerShell은 모듈 매니페스트를 사용 하 여 모듈을 가져옵니다.

6. 필요에 따라 매니페스트 자체를 점으로 [소싱 하 여 import-module을 호출](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 하 여 모듈 매니페스트를 직접 테스트할 수 있습니다.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>모듈 매니페스트 요소

다음 표에서는 모듈 매니페스트에 포함할 수 있는 요소에 대해 설명 합니다.

|요소|Default|설명|
|-------------|-------------|-----------------|
|RootModule<br /><br /> 형식: 문자열|' '|이 매니페스트와 연결 된 스크립트 모듈 또는 이진 모듈 파일입니다. 이전 버전의 PowerShell에서는이 요소를 ModuleToProcess 합니다.<br /><br /> 루트 모듈에 사용할 수 있는 형식은 비어 있거나 ( **매니페스트** 모듈을 만드는 경우) 스크립트 모듈 이름 (이 **스크립트** 모듈을 만드는 .psm1) 이거나 이진 모듈 (.exe 또는 .dll)의 이름을 사용 하 여 **이진** 모듈을 만들 수 있습니다. 이 요소에 모듈 매니페스트 (. psd1) 또는 스크립트 파일 (ps1)의 이름을 배치 하면 오류가 발생 합니다.|
|모듈<br /><br /> 형식: 문자열|1.0|이 모듈의 버전 번호입니다. 문자열은 [System.object]로 변환할 수 있어야 합니다. 즉, ' #. #. #. #. # '이 있습니다. `Import-Module`은 해당 이름과 일치 하는 **$psModulePath** 에서 검색 한 첫 번째 모듈을 로드 하 고, `-MinimumVersion` 매개 변수로 최소 ModuleVersion을 갖습니다. 특정 버전을 가져오려면 대신 @ no__t-0 매개 변수를 사용 합니다.<br /><br /> 예: `ModuleVersion = '1.0'`|
|GUID<br /><br /> 형식: 문자열|자동 생성 GUID|이 모듈을 고유 하 게 식별 하는 데 사용 되는 ID입니다. 현재는 GUID로 모듈을 가져올 수 없습니다.<br /><br /> 예: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Author<br /><br /> 형식: 문자열|없음|이 모듈의 작성자입니다.<br /><br /> 예: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> 형식: 문자열|Unknown|이 모듈의 회사 또는 공급 업체입니다.<br /><br /> 예: `CompanyName = 'Fabrikam'`|
|저작권<br /><br /> 형식: 문자열|(c) [currentYear] [Author]. All rights reserved.|이 모듈에 대 한 Copyright 문입니다.<br /><br /> 예: `Copyright = '2016 AuthorName. All rights reserved.'`|
|설명<br /><br /> 형식: 문자열|' '|이 모듈에서 제공 하는 기능에 대 한 설명입니다.<br /><br /> 예: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> 형식: 문자열|' '|이 모듈에 필요한 Windows PowerShell 엔진의 최소 버전입니다. 현재 유효한 값은 1.0, 2.0, 3.0, 4.0 및 5.0입니다.<br /><br /> 예: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> 형식: 문자열|' '|모듈에 필요한 Windows PowerShell 호스트의 이름을 지정 합니다. 이 이름은 Windows PowerShell에서 제공 됩니다. 프로그램에서 호스트 프로그램의 이름을 찾으려면 `$host.name`을 입력 합니다.<br /><br /> 예: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> 형식: 문자열|' '|이 모듈에 필요한 Windows PowerShell 호스트의 최소 버전입니다.<br /><br /> 예: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> 형식: 문자열|' '|이 모듈에 필요한 Microsoft .NET Framework의 최소 버전입니다.<br /><br /> 예: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> 형식: 문자열|' '|이 모듈에 필요한 CLR (공용 언어 런타임)의 최소 버전입니다.<br /><br /> 예: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> 형식: 문자열|' '|이 모듈에 필요한 프로세서 아키텍처 (없음, X86, Amd64)입니다. 유효한 값은 x86, AMD64, IA64 및 None(알 수 없음 또는 지정되지 않음)입니다.<br /><br /> 예: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> 유형: [string []]|@()|모듈을 가져오기 전에 전역 환경으로 가져와야 합니다. 이렇게 하면 아직 로드 되지 않은 경우 나열 된 모든 모듈이 로드 됩니다. (예를 들어 일부 모듈은 다른 모듈에 의해 이미 로드되어 있을 수 있음). @No__t-1이 아닌 `RequiredVersion`을 사용 하 여 로드할 특정 버전을 지정할 수도 있습니다. @No__t를 사용 하는 경우 최소 버전의를 사용 하 여 사용 가능한 최신 버전을 로드 합니다.<br /><br /> 예: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> 예: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> 유형: [string []]|@()|이 모듈을 가져오기 전에 로드 해야 하는 어셈블리입니다.<br /><br /> RequiredModules와 달리 PowerShell은 아직 로드 되지 않은 경우 RequiredAssemblies를 로드 합니다.|
|매니페스트의 scriptstoprocess<br /><br /> 유형: [string []]|@()|모듈을 가져올 때 호출자의 세션 상태에서 실행 되는 스크립트 (ps1) 파일입니다. 전역 세션 상태 이거나 중첩 된 모듈의 경우 다른 모듈의 세션 상태 일 수 있습니다. 로그인 스크립트를 사용 하는 것 처럼 이러한 스크립트를 사용 하 여 환경을 준비할 수 있습니다.<br /><br /> 이러한 스크립트는 매니페스트에 나열 된 모듈이 로드 되기 전에 실행 됩니다.|
|TypesToProcess<br /><br /> 유형: [string []]|@()|이 모듈을 가져올 때 로드할 파일 (. types.ps1xml)을 입력 합니다.|
|FormatsToProcess<br /><br /> 유형: [string []]|@()|이 모듈을 가져올 때 로드할 서식 파일 (types.ps1xml)입니다.|
|NestedModules<br /><br /> 유형: [string []]|@()|RootModule/ModuleToProcess에 지정 된 모듈의 중첩 모듈로 가져올 모듈입니다.<br /><br /> 이 요소에 모듈 이름을 추가 하는 것은 스크립트나 어셈블리 코드 내에서 `Import-Module`을 호출 하는 것과 비슷합니다. 주요 차이점은 매니페스트 파일에서 로드 하는 내용을 쉽게 확인할 수 있다는 것입니다. 또한 모듈을 여기에서 로드 하지 못하는 경우 실제 모듈을 아직 로드 하지 않은 것입니다.<br /><br /> 다른 모듈 외에도 여기에 스크립트 (ps1) 파일을 로드할 수 있습니다. 이러한 파일은 루트 모듈의 컨텍스트에서 실행 됩니다. 이는 루트 모듈의 스크립트를 점으로 소싱 하는 것과 같습니다.|
|FunctionsToExport<br /><br /> 유형: [string []]|@()|모듈에서 내보내는 함수 (와일드 카드 문자는 허용 되지만 권장 하지 않음)를 호출자의 세션 상태로 지정 합니다. 기본적으로 함수는 내보내지 않습니다. 이 키를 사용 하 여 모듈에서 내보낸 함수를 나열할 수 있습니다.<br /><br /> 호출자의 세션 상태는 전역 세션 상태 이거나 중첩 된 모듈의 경우 다른 모듈의 세션 상태 일 수 있습니다. 중첩 모듈을 연결 하는 경우 체인의 모듈이 FunctionsToExport 키를 사용 하 여 함수를 제한 하지 않는 한 중첩 된 모듈에서 내보낸 모든 함수를 전역 세션 상태로 내보냅니다.<br /><br /> 매니페스트가 함수에 대 한 별칭을 내보내는 경우이 키는 별칭을 AliasesToExport 키에 나열 하는 함수를 제거할 수 있지만이 키는 함수 별칭을 목록에 추가할 수 없습니다.|
|CmdletsToExport<br /><br /> 유형: [string []]|@()|모듈에서 내보내는 cmdlet을 지정 합니다 (와일드 카드 문자를 사용할 수 있지만 권장 하지 않음). 기본적으로 cmdlet은 내보내지지 않습니다. 이 키를 사용 하 여 모듈에서 내보낸 cmdlet을 나열할 수 있습니다.<br /><br /> 호출자의 세션 상태는 전역 세션 상태 이거나 중첩 된 모듈의 경우 다른 모듈의 세션 상태 일 수 있습니다. 중첩 모듈을 연결 하는 경우 체인의 모듈에서 CmdletsToExport 키를 사용 하 여 cmdlet을 제한 하지 않는 한 중첩 된 모듈에서 내보낸 모든 cmdlet은 궁극적으로 전역 세션 상태로 내보내집니다.<br /><br /> 매니페스트가 cmdlet에 대 한 별칭을 내보내는 경우이 키는 별칭을 AliasesToExport 키에 나열 하는 cmdlet을 제거할 수 있지만이 키가 목록에 cmdlet 별칭을 추가할 수는 없습니다.|
|VariablesToExport<br /><br /> 형식: 문자열|'*'|모듈에서 내보내는 변수 (와일드 카드 문자 허용)를 호출자의 세션 상태로 지정 합니다. 기본적으로 모든 변수를 내보냅니다. 이 키를 사용 하 여 모듈에서 내보내는 변수를 제한할 수 있습니다.<br /><br /> 호출자의 세션 상태는 전역 세션 상태 이거나 중첩 된 모듈의 경우 다른 모듈의 세션 상태 일 수 있습니다. 중첩 모듈을 연결 하는 경우 체인의 모듈이 VariablesToExport 키를 사용 하 여 변수를 제한 하지 않는 한 중첩 된 모듈에서 내보낸 모든 변수는 전역 세션 상태로 내보내집니다.<br /><br /> 매니페스트가 변수에 대 한 별칭을 내보내는 경우이 키는 별칭을 AliasesToExport 키에 나열 하는 변수를 제거할 수 있지만이 키는 변수 별칭을 목록에 추가할 수 없습니다.|
|AliasesToExport<br /><br /> 유형: [string []]|@()|모듈에서 내보내는 별칭 (와일드 카드 문자는 허용 되지만 권장 되지 않음)을 호출자의 세션 상태로 지정 합니다. 기본적으로 별칭은 내보내지지 않습니다. 이 키를 사용 하 여 모듈에서 내보내는 별칭을 나열할 수 있습니다.<br /><br /> 호출자의 세션 상태는 전역 세션 상태 이거나 중첩 된 모듈의 경우 다른 모듈의 세션 상태 일 수 있습니다. 중첩 된 모듈을 연결 하는 경우 체인의 모듈이 AliasesToExport 키를 사용 하 여 별칭을 제한 하지 않는 한 중첩 된 모듈에서 내보낸 모든 별칭은 궁극적으로 전역 세션 상태로 내보내집니다.|
|ModuleList<br /><br /> 유형: [string []]|@()|이 모듈을 사용 하 여 패키지 된 모든 모듈을 지정 합니다. 이러한 모듈은 이름 (쉼표로 구분 된 문자열) 또는 ModuleName 및 GUID 키를 사용 하는 해시 테이블로 입력할 수 있습니다. 해시 테이블에는 선택적 ModuleVersion 키도 있을 수 있습니다. ModuleList 키는 모듈 인벤토리 역할을 하도록 디자인 되었습니다. 이러한 모듈은 자동으로 처리 되지 않습니다.|
|FileList<br /><br /> 유형: [string []]|@()|이 모듈과 함께 패키지 된 모든 파일의 목록입니다. ModuleList와 마찬가지로 FileList는 인벤토리 목록으로 지원 하 고 달리 처리 되지 않습니다.|
|PrivateData<br /><br /> 유형: [object]|@{...}|RootModule/ModuleToProcess 키로 지정 된 루트 모듈에 전달 되어야 하는 개인 데이터를 지정 합니다.|
|HelpInfoURI<br /><br /> 형식: 문자열|' '|이 모듈의 HelpInfo URI입니다.|
|DefaultCommandPrefix<br /><br /> 형식: 문자열|' '|이 모듈에서 내보낸 명령의 기본 접두사입니다. @No__t-0-접두사를 사용 하 여 기본 접두사를 재정의 합니다.|

## <a name="sample-module-manifest"></a>샘플 모듈 매니페스트

다음 샘플 모듈 매니페스트는 모듈 매니페스트의 키와 기본값을 보여 줍니다. 이 예제는 Windows PowerShell 3.0에서 `New-ModuleManifest` cmdlet을 사용 하 여 만들었습니다. 여러 모듈을 만들 때이 cmdlet을 사용 하 여 다른 모듈에 대해 수정할 수 있는 매니페스트 템플릿을 만들 수 있습니다.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 2019-10-09
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b888e5a2-8578-4c0b-938d-0cd9b5b836ba'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2019 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
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

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 작성](./writing-a-windows-powershell-module.md)

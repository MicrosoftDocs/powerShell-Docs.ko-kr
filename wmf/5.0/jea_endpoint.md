---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3acd266a75bc61ffe4bce467cfb804ac7865c629
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682143"
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a>JEA 엔드포인트 만들기 및 연결

JEA 엔드포인트를 만들려면 특별히 구성된 PowerShell 세션 구성 파일을 만들어야 합니다. 이 파일은 **New-PSSessionConfigurationFile** cmdlet을 사용하여 생성할 수 있습니다.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

그러면 다음과 같은 세션 구성 파일이 만들어집니다.

```powershell
@{

    # Version number of the schema used for this document
    SchemaVersion = '2.0.0.0'

    # ID used to uniquely identify this document
    GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

    # Author of this document
    Author = 'Administrator'

    # Description of the functionality provided by these settings
    # Description = ''

    # Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
    SessionType = 'RestrictedRemoteServer'

    # Directory to place session transcripts for this session configuration
    TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

    # Whether to run this session configuration as the machine's (virtual) administrator account
    RunAsVirtualAccount = $true

    # Groups associated with machine's (virtual) administrator account
    # RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

    # Scripts to run when applied to a session
    # ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

    # User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
    RoleDefinitions = @{ 'CONTOSO\NonAdmin_Operators' = @{ 'RoleCapabilities' = 'Maintenance' } }
}
```

JEA 엔드포인트를 만들려면 다음과 같은 명령의 매개 변수(및 파일의 해당 키)를 설정해야 합니다.

1. SessionType을 RestrictedRemoteServer로 설정
2. RunAsVirtualAccount를 **$true**로 설정
3. TranscriptPath를 각 세션 후 “자격 증명 입력” 기록이 저장될 디렉터리로 설정
4. RoleDefinitions를 어떤 그룹이 어떤 “역할 기능”에 액세스할 수 있는지를 정의하는 해시 테이블로 설정. 이 필드는 이 엔드포인트에서 **누가** **무엇** 을 수행할 수 있는지를 정의합니다. 역할 기능은 특수 파일로 간단하게 설명합니다.

RoleDefinitions 필드는 어떤 그룹이 어떤 역할 기능에 액세스할 수 있는지를 정의합니다. 역할 기능은 연결하는 사용자에게 노출될 기능 집합을 정의하는 파일입니다.
역할 기능은 **New-PSRoleCapabilityFile** 명령을 사용하여 만들 수 있습니다.

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

그러면 다음과 같은 템플릿 역할 기능이 생성됩니다.

```powershell
@{
    # ID used to uniquely identify this document
    GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

    # Author of this document
    Author = 'Administrator'

    # Description of the functionality provided by these settings
    # Description = ''

    # Company associated with this document
    CompanyName = 'Unknown'

    # Copyright statement for this document
    Copyright = '(c) 2015 Administrator. All rights reserved.'

    # Modules to import when applied to a session
    # ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

    # Aliases to make visible when applied to a session
    # VisibleAliases = 'Item1', 'Item2'

    # Cmdlets to make visible when applied to a session
    # VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

    # Functions to make visible when applied to a session
    # VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

    # External commands (scripts and applications) to make visible when applied to a session
    # VisibleExternalCommands = 'Item1', 'Item2'

    # Providers to make visible when applied to a session
    # VisibleProviders = 'Item1', 'Item2'

    # Scripts to run when applied to a session
    # ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

    # Aliases to be defined when applied to a session
    # AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

    # Functions to define when applied to a session
    # FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

    # Variables to define when applied to a session
    # VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

    # Environment variables to define when applied to a session
    # EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

    # Type files (.ps1xml) to load when applied to a session
    # TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

    # Format files (.ps1xml) to load when applied to a session
    # FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

    # Assemblies to load when applied to a session
    # AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

}
```

JEA 세션 구성에서 사용하려면 역할 기능을 유효한 PowerShell 모듈로 “RoleCapabilities”라는 디렉터리에 저장해야 합니다. 원하는 경우 모듈에 역할 기능 파일이 여러 개 있을 수 있습니다.

JEA 세션에 연결할 때 사용자가 액세스할 수 있는 cmdlet, 함수, 별칭 및 스크립트를 구성하려면 고유한 규칙을 주석 처리된 템플릿 다음에 역할 기능 파일에 추가합니다. 역할 기능을 구성하는 방법을 자세히 살펴보려면 전체 [experience guide(환경 가이드)](http://aka.ms/JEA)를 확인하세요.

마지막으로 세션 구성 및 관련 역할 기능 사용자 지정을 마쳤으면 `Register-PSSessionConfiguration`을 실행하여 이 세션 구성을 등록하고 엔드포인트를 만듭니다.

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a>JEA 엔드포인트에 연결

JEA 엔드포인트에 연결은 다른 모든 PowerShell 엔드포인트에 연결하는 것과 동일한 방식으로 작동합니다.
**New-PSSession**, **Invoke-Command** 또는 **Enter-PSSession**에 대한 “ConfigurationName” 매개 변수처럼 JEA 엔드포인트에 이름만 지정하면 됩니다.

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```

JEA 세션에 연결한 후에는 액세스하는 역할 기능의 허용 목록에 있는 명령 실행으로 제한됩니다. 역할에 허용되지 않은 명령을 실행하려고 하면 오류가 발생합니다.
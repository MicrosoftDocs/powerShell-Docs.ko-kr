---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: 1f06d1e7114a84ea89097167b188ded605f81aa0
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564540"
---
# Get-Module

## 개요
현재 세션에서 가져온 모듈 또는 PSModulePath에서 가져올 수 있는 모듈을 나열 합니다.

## SYNTAX

### 로드 됨 (기본값)

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### 사용 가능

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] [<CommonParameters>]
```

### PsSession

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### CimSession

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-SkipEditionCheck] [-Refresh] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

## 설명

`Get-Module`Cmdlet은 powershell 세션으로 가져오거나 가져올 수 있는 powershell 모듈을 나열 합니다. 매개 변수가 없는 경우 `Get-Module` 현재 세션으로 가져온 모듈을 가져옵니다. **ListAvailable** 매개 변수는 PSModulePath 환경 변수 ()에 지정 된 경로에서 가져올 수 있는 모듈을 나열 하는 데 사용 됩니다 `$env:PSModulePath` .

을 반환 하는 module 개체는 `Get-Module` 모듈에 대 한 중요 한 정보를 포함 합니다. 모듈 개체를 및 cmdlet과 같은 다른 cmdlet으로 파이프 할 수도 있습니다 `Import-Module` `Remove-Module` .

`Get-Module` 모듈을 나열 하지만 가져오지는 않습니다. Windows PowerShell 3.0부터 모듈의 명령을 사용할 때 모듈을 자동으로 가져오지만, `Get-Module` 자동 가져오기를 트리거하지 않는 명령이 있습니다. Cmdlet을 사용 하 여 모듈을 세션으로 가져올 수도 있습니다 `Import-Module` .

Windows PowerShell 3.0 부터는 원격 세션에서 모듈을 가져온 다음 로컬 세션으로 가져올 수 있습니다. 이 전략은 PowerShell의 암시적 원격 기능을 사용 하며 cmdlet을 사용 하는 것과 같습니다 `Import-PSSession` . 다른 세션에서 가져온 모듈에서 명령을 사용 하면 명령이 원격 세션에서 암시적으로 실행 됩니다. 이 기능을 사용 하면 로컬 세션에서 원격 컴퓨터를 관리할 수 있습니다.

또한 Windows PowerShell 3.0부터 및를 사용 `Get-Module` `Import-Module` 하 여 CIM (CIM(Common Information Model)) 모듈을 가져오고 가져올 수 있습니다. CIM 모듈은 CDXML (Cmdlet 정의 XML) 파일에 cmdlet을 정의 합니다. 이 기능을 사용 하면 c + +로 작성 된 코드 어셈블리와 같이 관리 되지 않는 코드 어셈블리에 구현 된 cmdlet을 사용할 수 있습니다.

암시적 원격은 PowerShell 원격을 사용 하도록 설정 된 원격 컴퓨터를 관리 하는 데 사용할 수 있습니다.
원격 컴퓨터에 **pssession** 을 만든 다음의 **pssession** 매개 변수를 사용 `Get-Module` 하 여 원격 세션의 PowerShell 모듈을 가져옵니다. 원격 세션에서 모듈을 가져오면 가져온 명령이 원격 컴퓨터의 세션에서 실행 됩니다.

유사한 전략을 사용 하 여 PowerShell 원격을 사용 하지 않는 컴퓨터를 관리할 수 있습니다.
여기에는 Windows 운영 체제를 실행 하지 않는 컴퓨터와 PowerShell이 있지만 PowerShell 원격을 사용 하도록 설정 하지 않은 컴퓨터가 포함 됩니다.

원격 컴퓨터에서 CIM 세션을 만들어 시작 합니다. CIM 세션은 원격 컴퓨터의 WMI(Windows Management Instrumentation) (WMI)에 대 한 연결입니다. 그런 다음의 **CIMSession** 매개 변수를 사용 하 여 cim `Get-Module` 세션에서 cim 모듈을 가져옵니다. Cmdlet을 사용 하 여 CIM 모듈을 가져온 `Import-Module` 다음 가져온 명령을 실행 하면 명령이 원격 컴퓨터에서 암시적으로 실행 됩니다. 이 WMI 및 CIM 전략을 사용하여 원격 컴퓨터를 관리할 수 있습니다.

## 예제

### 예 1: 현재 세션으로 가져온 모듈 가져오기

```powershell
Get-Module
```

이 명령은 현재 세션으로 가져온 모듈을 검색합니다.

### 예 2: 설치 된 모듈 및 사용 가능한 모듈 가져오기

```powershell
Get-Module -ListAvailable
```

이 명령은 컴퓨터에 설치되어 있고 현재 세션으로 가져올 수 있는 모듈을 검색합니다.

`Get-Module`**$env:P SModulePath** 환경 변수로 지정 된 경로에서 사용 가능한 모듈을 찾습니다. **PSModulePath** 에 대한 자세한 내용은 [about_Modules](About/about_Modules.md) 및 [about_Environment_Variables](About/about_Environment_Variables.md)를 참조하세요.

### 예제 3: 내보낸 파일 모두 가져오기

```powershell
Get-Module -ListAvailable -All
```

이 명령은 사용 가능한 모든 모듈의 내보낸 파일을 모두 가져옵니다.

### 예제 4: 정규화 된 이름으로 모듈 가져오기

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

이 명령은 **FullyQualifiedName** 매개 변수를 사용 하 여 모듈의 정규화 된 이름을 지정 하 여 **Microsoft PowerShell 관리** 모듈을 가져옵니다. 그런 다음이 명령은 결과를 cmdlet으로 파이프 `Format-Table` 하 여 **이름** 및 **버전이** 열 머리글로 포함 된 테이블로 결과를 지정 합니다.

### 예 5: 모듈의 속성 가져오기

```powershell
Get-Module | Get-Member -MemberType Property | Format-Table Name
```

```Output
Name
----
AccessMode
Author
ClrVersion
CompanyName
Copyright
Definition
Description
DotNetFrameworkVersion
ExportedAliases
ExportedCmdlets
ExportedCommands
ExportedFormatFiles
ExportedFunctions
ExportedTypeFiles
ExportedVariables
ExportedWorkflows
FileList
Guid
HelpInfoUri
LogPipelineExecutionDetails
ModuleBase
ModuleList
ModuleType
Name
NestedModules
OnRemove
Path
PowerShellHostName
PowerShellHostVersion
PowerShellVersion
PrivateData
ProcessorArchitecture
RequiredAssemblies
RequiredModules
RootModule
Scripts
SessionState
Version
```

이 명령은를 반환 하는 **Psmoduleinfo** 개체의 속성을 가져옵니다 `Get-Module` . 모듈 파일마다 하나의 개체가 있습니다.

이러한 속성을 사용하여 모듈 개체의 형식을 지정하고 필터링할 수 있습니다. 속성에 대 한 자세한 내용은 [Psmoduleinfo 속성](/dotnet/api/system.management.automation.psmoduleinfo)을 참조 하세요.

출력에는 Windows PowerShell 3.0에 도입 된 새 속성 (예: Author 및 **CompanyName**) **이** 포함 됩니다.

### 예제 6: 이름별로 모든 모듈 그룹화

```powershell
Get-Module -ListAvailable -All | Format-Table -Property Name, Moduletype, Path -Groupby Name
```

```Output
Name: AppLocker

Name      ModuleType Path
----      ---------- ----
AppLocker   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\AppLocker\AppLocker.psd1


   Name: Appx

Name ModuleType Path
---- ---------- ----
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\en-US\Appx.psd1
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psd1
Appx     Script C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psm1


   Name: BestPractices

Name          ModuleType Path
----          ---------- ----
BestPractices   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BestPractices\BestPractices.psd1


   Name: BitsTransfer

Name         ModuleType Path
----         ---------- ----
BitsTransfer   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1
```

이 명령은 가져온 모듈과 사용 가능한 모듈 파일을 모두 가져온 다음 모듈 이름별로 그룹화 합니다. 이에 따라 각 스크립트에서 내보내는 모듈 파일을 확인할 수 있습니다.

### 예제 7: 모듈 매니페스트 내용 표시

이러한 명령은 Windows PowerShell **BitsTransfer** 모듈에 대 한 모듈 매니페스트의 내용을 표시 합니다.

모듈에는 매니페스트 파일이 필요 하지 않습니다. 매니페스트 파일이 있는 경우 매니페스트 파일에는 버전 번호를 포함 해야 합니다. 그러나 매니페스트 파일에서 모듈, 해당 모듈의 요구 사항 및 내용에 대한 유용한 정보를 제공하는 경우도 많습니다.

```powershell
# First command
$m = Get-Module -list -Name BitsTransfer

# Second command
Get-Content $m.Path
```

```Output
@ {
    GUID               = "{8FA5064B-8479-4c5c-86EA-0D311FE48875}"
    Author             = "Microsoft Corporation"
    CompanyName        = "Microsoft Corporation"
    Copyright          = "Microsoft Corporation. All rights reserved."
    ModuleVersion      = "1.0.0.0"
    Description        = "Windows PowerShell File Transfer Module"
    PowerShellVersion  = "2.0"
    CLRVersion         = "2.0"
    NestedModules      = "Microsoft.BackgroundIntelligentTransfer.Management"
    FormatsToProcess   = "FileTransfer.Format.ps1xml"
    RequiredAssemblies = Join-Path $psScriptRoot "Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll"
}
```

첫 번째 명령은 BitsTransfer 모듈을 나타내는 PSModuleInfo 개체를 검색합니다. 개체를 `$m` 변수에 저장 합니다.

두 번째 명령은 cmdlet을 사용 하 여 `Get-Content` 지정 된 경로에 있는 매니페스트 파일의 내용을 가져옵니다. 이 명령은 점 표기법을 사용하여 개체의 Path 속성에 저장되어 있는 매니페스트 파일의 경로를 검색합니다. 출력은 모듈 매니페스트의 내용을 보여 줍니다.

### 예 8: 모듈 디렉터리에 파일 나열

```powershell
dir (Get-Module -ListAvailable FileTransfer).ModuleBase
```

```Output
Directory: C:\Windows\system32\WindowsPowerShell\v1.0\Modules\FileTransfer
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/16/2008  12:36 PM            en-US
-a---        11/19/2008  11:30 PM      16184 FileTransfer.Format.ps1xml
-a---        11/20/2008  11:30 PM       1044 FileTransfer.psd1
-a---        12/16/2008  12:20 AM     108544 Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll
```

이 명령은 모듈의 디렉터리에 있는 파일을 나열 합니다. 이는 모듈을 가져오기 전에 모듈에 있는 항목을 확인하는 또 다른 방법입니다. 일부 모듈에는 모듈에 대해 설명하는 추가 정보 파일이나 도움말 파일이 있을 수 있습니다.

### 예 9: 컴퓨터에 설치 된 모듈 가져오기

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

이러한 명령은 Server01 컴퓨터에 설치된 모듈을 검색합니다.

첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` Server01 컴퓨터에 **PSSession** 을 만듭니다. 이 명령은 $s 변수에 **PSSession** 을 저장 합니다.

두 번째 명령은의 **pssession** 및 **ListAvailable** 매개 변수를 사용 하 여 `Get-Module` 변수의 **pssession** 에 있는 모듈을 가져옵니다 `$s` .

다른 세션에서 cmdlet으로 모듈을 파이프 하는 경우는 `Import-Module` `Import-Module` 암시적 원격 기능을 사용 하 여 모듈을 현재 세션으로 가져옵니다. Cmdlet을 사용 하는 것과 같습니다 `Import-PSSession` . 이 cmdlet은 현재 세션의 모듈에서 사용할 수 있지만 이러한 cmdlet을 사용하는 명령은 실제로 원격 세션을 실행합니다. 자세한 내용은 [`Import-Module`](Import-Module.md) 및 [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md)을 참조하세요.

### 예 10: Windows 운영 체제를 실행 하지 않는 컴퓨터 관리

이 예제의 명령을 사용 하면 Windows 운영 체제를 실행 하지 않는 원격 컴퓨터의 저장소 시스템을 관리할 수 있습니다.
이 예제에서는 컴퓨터의 관리자가 모듈 검색 WMI 공급자를 설치했으므로 CIM 명령은 공급자용으로 설계된 기본값을 사용할 수 있습니다.

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Get-Module -CimSession $cs -Name Storage | Import-Module
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
Get-Disk
```

```Output
Number Friendly Name              OperationalStatus          Total Size Partition Style
------ -------------              -----------------          ---------- ---------------
0      Virtual HD ATA Device      Online                          40 GB MBR
```

첫 번째 명령은 cmdlet을 사용 하 여 `New-CimSession` 여 rsdgf03 원격 컴퓨터에서 세션을 만듭니다. 이 세션은 원격 컴퓨터의 WMI에 연결됩니다. 이 명령은 CIM 세션을 변수에 저장 합니다 `$cs` .

두 번째 명령은 변수의 CIM 세션을 사용 하 여 `$cs` `Get-Module` 여 rsdgf03 컴퓨터에서 명령을 실행 합니다. 이 명령은 Name 매개 변수를 사용하여 스토리지 모듈을 지정합니다. 이 명령은 파이프라인 연산자 (|)를 사용 하 여 저장소 모듈을 cmdlet으로 보내고 `Import-Module` ,이 cmdlet은 로컬 세션으로 가져옵니다.

세 번째 명령은 `Get-Command` `Get-Disk` 저장소 모듈의 명령에서 cmdlet을 실행 합니다.
CIM 모듈을 로컬 세션으로 가져오면 PowerShell에서 CIM 모듈을 나타내는 CDXML 파일을 로컬 세션의 함수로 표시 되는 PowerShell 스크립트로 변환 합니다.

네 번째 명령은 명령을 실행 합니다 `Get-Disk` . 로컬 세션에서 이 명령을 입력하면 이 명령은 가져온 원격 컴퓨터에서 암시적으로 실행됩니다. 이 명령은 원격 컴퓨터에서 개체를 검색하여 로컬 세션에 반환합니다.

## PARAMETERS

### -All

이 cmdlet은 중첩 된 모듈, 매니페스트 (. psd1) 파일, 스크립트 모듈 (.psm1) 파일 및 이진 모듈 (.dll) 파일을 포함 하 여 각 모듈 폴더의 모든 모듈을 가져옵니다. 이 매개 변수를 사용 하지 않으면 `Get-Module` 각 모듈 폴더의 기본 모듈만 가져옵니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Loaded, Available
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimNamespace

CIM 모듈을 표시하는 대체 CIM 공급자의 네임스페이스를 지정합니다. 기본값은 모듈 검색 WMI 공급자의 네임스페이스입니다.

이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치에서 CIM 모듈을 가져옵니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimResourceUri

CIM 모듈의 대체 위치를 지정합니다. 기본값은 원격 컴퓨터의 모듈 검색 WMI 공급자에 대 한 리소스 URI입니다.

이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치에서 CIM 모듈을 가져옵니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

원격 컴퓨터에서 CIM 세션을 지정합니다. Cim 세션을 포함 하는 변수 또는 CIM 세션을 가져오는 명령 (예: [CimSession](/powershell/module/cimcmdlets/get-cimsession) 명령)을 입력 합니다.

`Get-Module` CIM 세션 연결을 사용 하 여 원격 컴퓨터에서 모듈을 가져옵니다. Cmdlet을 사용 하 여 모듈을 가져오고 `Import-Module` 현재 세션에서 가져온 모듈의 명령을 사용 하면 명령이 실제로 원격 컴퓨터에서 실행 됩니다.

이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치와 PowerShell이 있지만 PowerShell 원격을 사용 하도록 설정 하지 않은 컴퓨터에서 모듈을 가져올 수 있습니다.

**CimSession** 매개 변수는 **CIMSession** 에서 모든 모듈을 검색합니다. 그러나 CIM 기반 및 CDXML(Cmdlet 정의 XML) 기반 모듈만 가져올 수 있습니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedName

**ModuleSpecification** 개체 형식으로 지정 된 이름을 사용 하 여 모듈을 지정 합니다. [ModuleSpecification 생성자 (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)의 설명 섹션을 참조 하세요.

예를 들어 **변수인 fullyqualifiedmodule** 매개 변수는 다음 형식 중 하나로 지정 된 모듈 이름을 허용 합니다.

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다. **모듈** 매개 변수와 동일한 명령에 **변수인 fullyqualifiedmodule** 매개 변수를 지정할 수 없습니다. 두 매개 변수는 함께 사용할 수 없습니다.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ListAvailable

이 cmdlet은 설치 된 모든 모듈을 가져옵니다. `Get-Module`**PSModulePath** 환경 변수에 나열 된 경로에서 모듈을 가져옵니다. 이 매개 변수를 사용 하지 않으면 `Get-Module` **PSModulePath** 환경 변수에 나열 되어 있고 현재 세션에 로드 된 모듈만 가져옵니다. **ListAvailable** 은 해당 모듈이 현재 세션에 로드된 경우에도 **PSModulePath** 환경 변수에 없는 모듈에 대한 정보를 반환하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: True (Available), False (PsSession, CimSession)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

이 cmdlet이 가져오는 모듈의 이름 또는 이름 패턴을 지정 합니다. 와일드카드 문자를 사용할 수 있습니다. 이름을로 파이프 할 수도 있습니다 `Get-Module` . **Name** 매개 변수와 동일한 명령에 **FullyQualifiedName** 매개 변수를 지정할 수 없습니다.

**이름** 에서 모듈 GUID를 값으로 사용할 수 없습니다.
GUID를 지정 하 여 모듈을 반환 하려면 대신 **FullyQualifiedName** 를 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -PSEdition

지정 된 버전의 PowerShell을 지 원하는 모듈을 가져옵니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- 데스크톱
- 코어

Get-Module cmdlet은 지정 된 값에 대 한 **Psmoduleinfo** 개체의 **CompatiblePSEditions** 속성을 확인 하 고 해당 속성이 설정 된 모듈만 반환 합니다.

> [!NOTE]
>
> - **Desktop Edition:** .NET Framework를 기반으로 구축되며 Server Core 및 Windows Desktop과 같은 전체 버전의 Windows에서 실행되는 PowerShell 버전을 대상 지정하는 스크립트 및 모듈과 호환성을 제공합니다.
> - **Core Edition:** .NET Framework를 기반으로 구축되며 Nano 서버 및 Windows IoT와 같은 축소된 버전의 Windows에서 실행되는 PowerShell 버전을 대상 지정하는 스크립트 및 모듈과 호환성을 제공합니다.

```yaml
Type: System.String
Parameter Sets: PsSession, Available
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSSession

지정 된 사용자 관리 PowerShell 세션 (**PSSession**)에서 모듈을 가져옵니다. 세션을 포함 하는 변수, 세션을 가져오는 명령 (예: 명령) `Get-PSSession` 또는 세션을 만드는 명령 (예: 명령)을 입력 합니다 `New-PSSession` .

세션이 원격 컴퓨터에 연결 된 경우 **ListAvailable** 매개 변수를 지정 해야 합니다.

`Get-Module` **Pssession** 매개 변수를 사용 하는 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Get-Module -ListAvailable` **pssession** 에서 명령을 실행 하는 것과 같습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PsSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -새로 고침

이 cmdlet은 설치 된 명령의 캐시를 새로 고치도록 지정 합니다. 명령 캐시는 세션이 시작될 때 만들어집니다. Cmdlet을 사용 하 여 `Get-Command` 세션으로 가져오지 않은 모듈에서 명령을 가져올 수 있습니다.

이 매개 변수는 세션이 시작된 이후 모듈의 내용이 변경된 개발 및 테스트 시나리오에 사용하도록 설계되었습니다.

명령에서 **Refresh** 매개 변수를 지정 하는 경우 **ListAvailable** 을 지정 해야 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipEditionCheck

필드의 검사를 건너뜁니다 `CompatiblePSEditions` .

기본적으로 Get-Module는 디렉터리에서 필드에를 지정 하지 않은 모듈을 생략 `%windir%\System32\WindowsPowerShell\v1.0\Modules` `Core` `CompatiblePSEditions` 합니다. 이 스위치가 설정 되 면가 없는 모듈이 `Core` 포함 되므로 Powershell Core와 호환 되지 않는 Windows powershell 모듈 경로 아래의 모듈이 반환 됩니다.

MacOS 및 Linux에서이 매개 변수는 아무 작업도 수행 하지 않습니다.

자세한 내용은 [about_PowerShell_Editions](About/about_PowerShell_Editions.md) 를 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

모듈 이름을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### System.object..

이 cmdlet은 모듈을 나타내는 개체를 반환 합니다.
**ListAvailable** 매개 변수를 지정 하면는 `Get-Module` 동일한 속성 및 메서드를 포함 하는 **psmoduleinfo** 개체의 유형인 **moduleinfogrouping** 개체를 반환 합니다.

## 참고

- Windows PowerShell 3.0부터 PowerShell에 포함 된 핵심 명령이 모듈에 패키지 됩니다. **Add-pssnapin**(스냅인) 인 **Microsoft. PowerShell** 은 예외입니다. 기본적으로 **Microsoft.PowerShell.Core** 스냅인만 세션에 추가됩니다. 모듈은 처음 사용할 때 자동으로 가져오며 cmdlet을 사용 하 여 가져올 수 있습니다 `Import-Module` .

- Windows PowerShell 2.0 및 이후 버전의 PowerShell에서 이전 스타일의 세션을 만드는 호스트 프로그램에서 핵심 명령은 스냅인 (**PSSnapins**)으로 패키지 됩니다. 예외는 항상 스냅인 인 **Microsoft. PowerShell. Core** 입니다. 또한 cmdlet에서 시작한 것과 같은 원격 세션 `New-PSSession` 은 핵심 스냅인을 포함 하는 이전 스타일의 세션입니다.

  핵심 모듈과 함께 최신 스타일의 세션을 만드는 **initialsessionstate.createdefault2** 메서드에 대 한 자세한 내용은 [initialsessionstate.createdefault2 메서드](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)를 참조 하세요.

- `Get-Module`**PSModulePath** 환경 변수 ($Env:P SModulePath)의 값에 저장 된 위치의 모듈만 가져옵니다. `Import-Module`Cmdlet은 다른 위치의 모듈을 가져올 수 있지만 cmdlet을 사용 하 여 모듈을 가져올 수는 없습니다 `Get-Module` .

- 또한 PowerShell 3.0 부터는를 `Get-Module` 가져오기 전에 모듈을 더 쉽게 학습할 수 있도록를 반환 하는 개체에 새 속성이 추가 되었습니다. 가져오기 전에 모든 속성이 채워집니다. 여기에는 모듈에서 내보내는 명령을 나열 하는 **ExportedCommands**, **ExportedCmdlets** 및 **ExportedFunctions** 속성이 포함 됩니다.

- **ListAvailable** 매개 변수는 올바른 형식의 모듈만 가져옵니다. 즉, 기본 이름이 모듈 폴더의 이름과 동일한 파일이 하나 이상 포함 된 폴더입니다. 기본 이름은 파일 이름 확장명이 없는 이름입니다. 이름이 다른 파일을 포함 하는 폴더는 모듈이 아니라 컨테이너로 간주 됩니다.

  DLL 파일로 구현 되었지만 모듈 폴더에 포함 되지 않은 모듈을 가져오려면 **ListAvailable** 및 **All** 매개 변수를 모두 지정 합니다.

- CIM 세션 기능을 사용하려면 원격 컴퓨터에 WS-Management 원격 기능과 CIM(Common Information Model) 표준에 대한 Microsoft 구현인 WMI(Windows Management Instrumentation)가 설정되어 있어야 합니다. 또한 컴퓨터에 모듈 검색 WMI 공급자나 동일한 기본 기능을 갖춘 대체 WMI 공급자가 있어야 합니다.

  Windows 운영 체제를 실행 하지 않는 컴퓨터 및 PowerShell이 있지만 PowerShell 원격을 사용 하도록 설정 하지 않은 Windows 컴퓨터에서 CIM 세션 기능을 사용할 수 있습니다.

  또한 CIM 매개 변수를 사용 하 여 PowerShell 원격을 사용 하도록 설정한 컴퓨터에서 CIM 모듈을 가져올 수 있습니다. 여기에는 로컬 컴퓨터가 포함 됩니다. 로컬 컴퓨터에서 CIM 세션을 만드는 경우 PowerShell은 WMI 대신 DCOM을 사용 하 여 세션을 만듭니다.

## 관련 링크

[Get-CimSession](../CimCmdlets/Get-CimSession.md)

[New-CimSession](../CimCmdlets/New-CimSession.md)

[about_Modules](About/about_Modules.md)

[Get-PSSession](Get-PSSession.md)

[모듈 가져오기](Import-Module.md)

[Import-PSSession](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[New-PSSession](New-PSSession.md)

[Remove-Module](Remove-Module.md)

[about_PowerShell_Editions](About/about_PowerShell_Editions.md)

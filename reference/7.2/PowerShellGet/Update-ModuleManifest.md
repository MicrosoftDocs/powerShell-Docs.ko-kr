---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: 4f00450257178cac72d03303358150fd9f5cd26b
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99605214"
---
# Update-ModuleManifest

## 개요
모듈 매니페스트 파일을 업데이트합니다.

## SYNTAX

### 모두

```
Update-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-CompatiblePSEditions <String[]>] [-PowerShellVersion <Version>] [-ClrVersion <Version>]
 [-DotNetFrameworkVersion <Version>] [-PowerShellHostName <String>]
 [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>] [-RequiredAssemblies <String[]>]
 [-FileList <String[]>] [-ModuleList <Object[]>] [-FunctionsToExport <String[]>]
 [-AliasesToExport <String[]>] [-VariablesToExport <String[]>] [-CmdletsToExport <String[]>]
 [-DscResourcesToExport <String[]>] [-PrivateData <Hashtable>] [-Tags <String[]>]
 [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ReleaseNotes <String[]>]
 [-Prerelease <String>] [-HelpInfoUri <Uri>] [-PassThru] [-DefaultCommandPrefix <String>]
 [-ExternalModuleDependencies <String[]>] [-PackageManagementProviders <String[]>]
 [-RequireLicenseAcceptance] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Update-ModuleManifest`Cmdlet은 모듈 매니페스트 ( `.psd1` ) 파일을 업데이트 합니다.

## 예제

### 예제 1: 모듈 매니페스트 업데이트

이 예에서는 기존 모듈 매니페스트 파일을 업데이트 합니다. 스 플랫는 매개 변수 값을에 전달 하는 데 사용 됩니다 `Update-ModuleManifest` . 자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

`$Parms` 는 **Path**, **Author**, **CompanyName** 및 **저작권** 에 대 한 매개 변수 값을 저장 하는 스 플랫입니다. `Update-ModuleManifest` 에서 매개 변수 값을 가져오고 `@Parms` 모듈 매니페스트 ( **TestManifest.psd1)** 를 업데이트 합니다.

## PARAMETERS

### -AliasesToExport

모듈이 내보내는 별칭을 지정합니다. 와일드카드가 지원됩니다.

이 매개 변수를 사용 하 여 모듈에서 내보내는 별칭을 제한할 수 있습니다. **AliasesToExport** 는 내보낸 별칭 목록에서 별칭을 제거할 수 있지만 목록에 별칭을 추가할 수는 없습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -작성자

모듈 작성자를 지정합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClrVersion

모듈에 필요한 Microsoft .NET Framework의 CLR(공용 언어 런타임) 최소 버전을 지정합니다.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CmdletsToExport

모듈이 내보내는 cmdlet을 지정합니다. 와일드카드가 지원됩니다.

이 매개 변수를 사용 하 여 모듈에서 내보내는 cmdlet을 제한할 수 있습니다. **Cmdletstoexport** 는 내보낸 cmdlet 목록에서 cmdlet을 제거할 수 있지만 목록에 cmdlet을 추가할 수는 없습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -CompanyName

모듈을 만든 회사나 공급 업체를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CompatiblePSEditions

모듈의 호환 되는 **pseditions가** 를 지정 합니다. **PSEdition** 에 대 한 자세한 내용은 [호환 되는 PowerShell 버전이 있는 모듈](/powershell/scripting/gallery/concepts/module-psedition-support)을 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

실행 하기 전에 확인 메시지를 표시 `Update-ModuleManifest` 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -저작권

모듈의 저작권 정보를 지정합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultCommandPrefix

기본 명령 접두사를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

모듈에 대 한 설명을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DotNetFrameworkVersion

모듈에 필요한 Microsoft .NET Framework의 최소 버전을 지정합니다.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DscResourcesToExport

모듈에서 내보내는 DSC (Desired State Configuration) 리소스를 지정 합니다. 와일드카드가 지원됩니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExternalModuleDependencies

외부 모듈 종속성의 배열을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FileList

모듈에 포함된 모든 항목을 지정합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

`.ps1xml`모듈을 가져올 때 실행 되는 서식 파일 ()을 지정 합니다.

모듈을 가져올 때 PowerShell에서 지정 된 파일을 사용 하 여 cmdlet을 실행 합니다 `Update-FormatData` .
형식 지정 파일의 범위는 지정 되지 않기 때문에 세션의 모든 세션 상태에 영향을 줍니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FunctionsToExport

모듈이 내보내는 함수를 지정합니다. 와일드카드가 지원됩니다.

이 매개 변수를 사용 하 여 모듈에서 내보내는 함수를 제한할 수 있습니다. **Functionstoexport** 는 내보낸 별칭 목록에서 함수를 제거할 수 있지만 목록에 함수를 추가할 수 없습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Guid

모듈의 고유 식별자를 지정합니다. GUID를 사용하여 이름이 같은 모듈을 구별할 수 있습니다.

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HelpInfoUri

모듈의 **HELPINFO XML** 파일의 인터넷 주소를 지정 합니다. **Http** 또는 **https** 로 시작 하는 URI (Uniform resource Identifier)를 입력 합니다.

**HELPINFO XML** 파일은 PowerShell 버전 3.0에 도입 된 업데이트할 수 있는 도움말 기능을 지원 합니다. 모듈의 다운로드 가능한 도움말 파일의 위치 및 지원 되는 각 로캘에 대 한 최신 도움말 파일의 버전 번호에 대 한 정보가 포함 되어 있습니다.

업데이트할 수 있는 도움말에 대 한 자세한 내용은 [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md)를 참조 하세요.
**HELPINFO XML** 파일에 대 한 자세한 내용은 업데이트할 수 있는 [도움말 지원](/powershell/scripting/developer/module/supporting-updatable-help)을 참조 하세요.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IconUri

모듈에 대 한 아이콘의 URL을 지정 합니다. 지정 된 아이콘은 모듈에 대 한 갤러리 웹 페이지에 표시 됩니다.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LicenseUri

모듈에 대 한 라이선스 조건의 URL을 지정 합니다.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleList

모듈에 포함 된 모듈의 배열을 지정 합니다.

각 모듈 이름을 문자열이나 **ModuleName** 및 **ModuleVersion** 키가 포함된 해시 테이블로 입력합니다. 해시 테이블에 선택적 **GUID** 키가 포함될 수도 있습니다. 매개 변수 값에서 문자열과 해시 테이블을 결합할 수 있습니다.

이 키는 모듈 인벤토리 역할을 합니다. 이 키의 값에 나열 된 모듈은 자동으로 처리 되지 않습니다.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleVersion

모듈의 버전을 지정합니다.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NestedModules

`.psm1` `.dll` 모듈의 세션 상태로 가져올 스크립트 모듈 () 및 이진 모듈 ()을 지정 합니다. **NestedModules** 키의 파일은 값에 나열 된 순서 대로 실행 됩니다.

각 모듈 이름을 문자열이나 **ModuleName** 및 **ModuleVersion** 키가 포함된 해시 테이블로 입력합니다. 해시 테이블에 선택적 **GUID** 키가 포함될 수도 있습니다. 매개 변수 값에서 문자열과 해시 테이블을 결합할 수 있습니다.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProviders

패키지 관리 공급자의 배열을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

작업 중인 항목을 나타내는 개체를 반환 합니다. 기본적으로는 `Update-ModuleManifest` 출력을 생성 하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

모듈 매니페스트의 경로와 파일 이름을 지정 합니다. 파일 이름 확장명을 사용 하는 경로 및 파일 이름 (예:)을 입력 `.psd1` `$PSHOME\Modules\MyModule\MyModule.psd1` 합니다.

기존 파일에 대 한 경로를 지정 하는 경우 `Update-ModuleManifest` 파일에 읽기 전용 특성이 없는 경우는 경고 없이 파일을 바꿉니다.

매니페스트는 모듈 디렉터리에 있어야 하며 매니페스트 파일 이름은 모듈 디렉터리 이름과 동일 해야 하지만 확장명은 동일 해야 합니다 `.psd1` .

`$PSHOME` `$HOME` **경로** 매개 변수 값에 대 한 프롬프트에 응답 하 여 또는와 같은 변수를 사용할 수 없습니다. 변수를 사용하려면 명령에 **Path** 매개 변수를 포함합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PowerShellHostName

모듈에 필요한 PowerShell 호스트 프로그램의 이름을 지정 합니다. 호스트 프로그램의 이름 (예: PowerShell ISE Host 또는 ConsoleHost)을 입력 합니다. 와일드 카드는 허용 되지 않습니다.

호스트 프로그램의 이름을 찾으려면 프로그램에서을 입력 `$Host.Name` 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellHostVersion

모듈에서 작동 하는 PowerShell 호스트 프로그램의 최소 버전을 지정 합니다. 버전 번호를 입력하세요(예: 1.1).

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellVersion

이 모듈에서 작동 하는 PowerShell의 최소 버전을 지정 합니다. 예를 들어이 매개 변수의 값으로 3.0, 4.0 또는 5.0을 지정할 수 있습니다.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -시험판

모듈이 시험판 임을 나타냅니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PrivateData

모듈을 가져올 때 모듈에 전달 되는 데이터를 지정 합니다.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProcessorArchitecture

모듈에 필요한 프로세서 아키텍처를 지정합니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- Amd64
- Arm
- IA64
- MSIL
- 없음 (알 수 없음 또는 지정 되지 않음)
- X86

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProjectUri

이 프로젝트에 대 한 웹 페이지의 URL을 지정 합니다.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReleaseNotes

이 버전의 스크립트에 사용할 수 있는 릴리스 정보 또는 설명을 포함 하는 문자열 배열을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequireLicenseAcceptance

모듈에 대 한 라이선스 동의가 필요 하도록 지정 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredAssemblies

`.dll`모듈에 필요한 어셈블리 () 파일을 지정 합니다. 어셈블리 파일 이름을 입력합니다.
PowerShell은 형식 또는 형식을 업데이트 하거나, 중첩 모듈을 가져오거나, **RootModule** 키 값에 지정 된 모듈 파일을 가져오기 전에 지정 된 어셈블리를 로드 합니다.

이 매개 변수를 사용 하 여 모듈에 필요한 모든 어셈블리를 지정 합니다. 어셈블리를 포함 하 여 **Formatstoprocess** 또는 **TypesToProcess** keys에 나열 된 서식 파일 또는 형식 파일을 업데이트 하기 위해 로드 해야 하는 어셈블리를 포함 하 여 해당 어셈블리가 **NestedModules** 키에 이진 모듈로도 나열 되어 있는 경우에도 마찬가지입니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredModules

전역 세션 상태여야 하는 모듈을 지정합니다. 필수 모듈이 전역 세션 상태가 아닌 경우 PowerShell에서 해당 모듈을 가져옵니다. 필수 모듈을 사용할 수 없는 경우 `Import-Module` 명령이 실패 합니다.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RootModule

모듈의 기본 또는 루트 파일을 지정 합니다. 스크립트 ( `.ps1` ), 스크립트 모듈 ( `.psm1` ), 모듈 매니페스트 ( `.psd1` ), 어셈블리 ( `.dll` ), cmdlet 정의 XML 파일 ( `.cdxml` ) 또는 워크플로 ( `.xaml` )의 파일 이름을 입력 합니다. 모듈을 가져오는 경우 루트 모듈 파일에서 내보낸 멤버를 호출자의 세션 상태로 가져옵니다.

모듈에 매니페스트 파일이 있고 **RootModule** 키에 루트 파일이 지정 되지 않은 경우 매니페스트는 모듈의 주 파일이 됩니다. 그리고 모듈이 매니페스트 모듈이 됩니다 (ModuleType = Manifest).

`.psm1`매니페스트가 포함 된 모듈의 또는 파일에서 멤버를 내보내려면 `.dll` 해당 파일의 이름을 매니페스트의 **RootModule** 또는 **NestedModules** 키 값에 지정 해야 합니다. 그렇지 않으면 해당 멤버를 내보내지 않습니다.

PowerShell 2.0에서는이 키를 **ModuleToProcess** 라고 했습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

`.ps1`모듈을 가져올 때 호출자의 세션 상태에서 실행 되는 스크립트 () 파일을 지정 합니다.
로그인 스크립트를 사용하는 것처럼 이러한 스크립트를 사용하여 환경을 준비할 수 있습니다.

모듈의 세션 상태에서 실행되는 스크립트를 지정하려면 **NestedModules** 키를 사용합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -태그

태그의 배열을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypesToProcess

`.ps1xml`모듈을 가져올 때 실행 되는 형식 파일 ()을 지정 합니다.

모듈을 가져올 때 PowerShell에서 지정 된 파일을 사용 하 여 cmdlet을 실행 합니다 `Update-TypeData` .
형식 파일은 범위가 지정 되지 않기 때문에 세션의 모든 세션 상태에 영향을 줍니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VariablesToExport

모듈이 내보내는 변수를 지정합니다. 와일드카드가 지원됩니다.

이 매개 변수를 사용 하 여 모듈이 내보내는 변수를 제한할 수 있습니다. **VariablesToExport** 는 내보낸 변수 목록에서 변수를 제거할 수 있지만 목록에 변수를 추가할 수는 없습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -WhatIf

가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Update-ModuleManifest` . Cmdlet이 실행 되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

## 출력

### System.Object

## 참고

> [!IMPORTANT]
> 2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다. TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다. 다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.

## 관련 링크

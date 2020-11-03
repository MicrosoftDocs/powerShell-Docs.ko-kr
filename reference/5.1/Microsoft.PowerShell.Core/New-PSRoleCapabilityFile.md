---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 3dca5f922f31690bb78ccc610b4ed44b7423ca47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212857"
---
# New-PSRoleCapabilityFile

## 개요
세션 구성을 통해 노출할 기능 집합을 정의 하는 파일을 만듭니다.

## SYNTAX

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## 설명

`New-PSRoleCapabilityFile`Cmdlet은 세션 구성 파일을 통해 노출 될 수 있는 사용자 기능 집합을 정의 하는 파일을 만듭니다. 여기에는 사용자가 사용할 수 있는 cmdlet, 함수 및 스크립트를 결정 하는 작업이 포함 됩니다. 기능 파일은 세션 구성 속성 및 값의 해시 테이블을 포함 하는 사람이 읽을 수 있는 텍스트 파일입니다. 파일은 .psrc 파일 이름 확장명을 가지 며 둘 이상의 세션 구성에서 사용할 수 있습니다.

의 모든 매개 변수는 `New-PSRoleCapabilityFile` 파일의 파일 경로를 지정 하는 **Path** 매개 변수를 제외 하 고는 선택 사항입니다. Cmdlet을 실행할 때 매개 변수를 포함 하지 않는 경우에는 매개 변수 설명에 명시 된 경우를 제외 하 고 세션 구성 파일의 해당 키가 주석으로 처리 됩니다. 예를 들어 **AssembliesToLoad** 매개 변수를 포함 하지 않는 경우 세션 구성 파일의 해당 섹션은 주석으로 처리 됩니다.

세션 구성에서 역할 기능 파일을 사용 하려면 먼저 올바른 PowerShell 모듈 폴더의 **RoleCapabilities** 하위 폴더에 파일을 저장 합니다. 그런 다음 PowerShell 세션 구성 파일 (.psc)의 **Roledefinitions** 필드에서 이름을 기준으로 파일을 참조 합니다.

이 cmdlet은 Windows PowerShell 5.0에서 도입 되었습니다.

## 예제

### 예 1: 빈 역할 기능 파일 만들기

이 예제에서는 기본 (공백) 값을 사용 하는 새 역할 기능 파일을 만듭니다. 나중에 텍스트 편집기에서 파일을 편집 하 여 이러한 구성 설정을 변경할 수 있습니다.

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### 예제 2: 사용자가 서비스 및 VDI 컴퓨터를 다시 시작할 수 있도록 하는 역할 기능 파일 만들기

이 예제에서는 사용자가 특정 이름 패턴과 일치 하는 서비스 및 컴퓨터를 다시 시작할 수 있도록 하는 샘플 역할 기능 파일을 만듭니다. 이름 필터링은 **ValidatePattern** 매개 변수를 정규식으로 설정 하 여 정의 됩니다 `VDI\d+` .

```powershell
$roleParameters = @{
    Path = ".\Maintenance.psrc"
    Author = "User01"
    CompanyName = "Fabrikam Corporation"
    Description = "This role enables users to restart any service and restart any VDI computer."
    ModulesToImport = "Microsoft.PowerShell.Core"
    VisibleCmdlets = "Restart-Service", @{
                      Name = "Restart-Computer"
                      Parameters = @{ Name = "ComputerName"; ValidatePattern = "VDI\d+" }
    }
}
New-PSRoleCapabilityFile @roleParameters
```

## PARAMETERS

### -AliasDefinitions

역할 기능 파일을 사용 하는 세션에 지정 된 별칭을 추가 합니다. 다음 키를 사용하여 해시 테이블을 입력합니다.

- 이름. 별칭의 이름입니다. 이 키는 필수입니다.
- 값. 별칭이 나타내는 명령입니다. 이 키는 필수입니다.
- 설명 별칭을 설명하는 텍스트 문자열입니다. 이 키는 선택 사항입니다.
- 옵션입니다. 별칭 옵션입니다. 이 키는 선택 사항입니다. 기본값은 None입니다. 이 매개 변수에 허용 되는 값은 None, ReadOnly, Constant, Private 또는 AllScope입니다.

`@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssembliesToLoad

역할 기능 파일을 사용 하는 세션에 로드할 어셈블리를 지정 합니다.

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

### -작성자

역할 기능 파일을 만든 사용자를 지정 합니다.

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

### -CompanyName

역할 기능 파일을 만든 회사를 식별 합니다.
기본값은 알 수 없음입니다.

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

### -저작권

역할 기능 파일의 저작권을 지정 합니다. 이 매개 변수를 생략 하면은 `New-PSRoleCapabilityFile` **Author** 매개 변수 값을 사용 하 여 저작권 설명을 생성 합니다.

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

역할 기능 파일에 대 한 설명을 지정 합니다.

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

### -환경 변수

이 역할 기능 파일을 노출 하는 세션에 대 한 환경 변수를 지정 합니다. 키가 환경 변수 이름이고 값이 환경 변수 값인 해시 테이블을 입력합니다.

`EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

역할 기능 파일을 사용 하는 세션에서 실행 되는 형식 지정 파일 (. types.ps1xml)을 지정 합니다. 이 매개 변수 값은 형식 지정 파일의 전체 또는 절대 경로 여야 합니다.

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

### -FunctionDefinitions

역할 기능을 노출 하는 세션에 지정 된 함수를 추가 합니다. 다음 키를 사용하여 해시 테이블을 입력합니다.

- 이름. 함수의 이름입니다. 이 키는 필수입니다.
- ScriptBlock. 함수 본문입니다. 스크립트 블록을 입력합니다. 이 키는 필수입니다.
- 옵션입니다. 함수 옵션입니다. 이 키는 선택 사항입니다. 기본값은 None입니다. 이 매개 변수에 허용 되는 값은 None, ReadOnly, Constant, Private 또는 AllScope입니다.

다음은 그 예입니다. 

`@{Name="Get-PowerShellProcess";ScriptBlock={Get-Process PowerShell};Options="AllScope"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Guid

역할 기능 파일의 고유 식별자를 지정 합니다. 이 매개 변수를 생략 하면는 `New-PSRoleCapabilityFile` 파일에 대 한 GUID를 생성 합니다. PowerShell에서 새 GUID를 만들려면를 입력 `[guid]::NewGuid()` 합니다.

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

### -ModulesToImport

역할 기능 파일을 사용 하는 세션에 자동으로 가져오는 모듈을 지정 합니다. 기본적으로 나열 된 모듈의 모든 명령이 표시 됩니다. **VisibleCmdlets** 또는 **VisibleFunctions** 와 함께 사용 하는 경우 지정 된 모듈에서 표시 되는 명령을 제한할 수 있습니다.

이 매개 변수 값에 사용 되는 각 모듈은 문자열 또는 해시 테이블로 나타낼 수 있습니다. 모듈 문자열은 모듈의 이름 으로만 구성 됩니다. 모듈 해시 테이블에는 **ModuleName** , **ModuleVersion** 및 **GUID** 키가 포함 될 수 있습니다. **ModuleName** 키만 필수입니다.

예를 들어 다음 값은 문자열과 해시 테이블로 구성됩니다. 순서와 관계없이 문자열과 해시 테이블의 모든 조합이 유효합니다.

`"TroubleshootingPack", @{ModuleName="PSDiagnostics"; ModuleVersion="1.0.0.0";GUID="c61d6278-02a3-4618-ae37-a524d40a7f44"}`

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

### -Path

역할 기능 파일의 경로와 파일 이름을 지정 합니다. 파일에는 파일 `.psrc` 이름 확장명이 있어야 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

역할 기능 파일을 사용 하는 세션에 추가할 스크립트를 지정 합니다. 스크립트의 경로와 파일 이름을 입력합니다. 이 매개 변수 값은 스크립트 파일 이름의 전체 또는 절대 경로 여야 합니다.

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

역할 기능 파일을 사용 하는 세션에 추가할 형식 파일 (types.ps1xml)을 지정 합니다. 유형 파일 이름을 입력 합니다. 이 매개 변수 값은 형식 파일 이름의 전체 또는 절대 경로 여야 합니다.

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

### -VariableDefinitions

역할 기능 파일을 사용 하는 세션에 추가할 변수를 지정 합니다. 다음 키를 사용하여 해시 테이블을 입력합니다.

- 이름. 변수의 이름입니다. 이 키는 필수입니다.
- 값. 변수 값입니다. 이 키는 필수입니다.
- 옵션입니다. 변수 옵션입니다. 이 키는 선택 사항입니다. 기본값은 None입니다. 이 매개 변수에 허용 되는 값은 None, ReadOnly, Constant, Private 또는 AllScope입니다.

`@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleAliases

세션의 별칭을이 매개 변수 값에 지정 된 별칭 및 **AliasDefinition** 매개 변수에서 정의 하는 별칭으로 제한 합니다. 와일드카드 문자가 지원됩니다.
기본적으로 PowerShell 엔진에서 정의한 모든 별칭과 모듈에서 내보낸 모든 별칭이 세션에 표시 됩니다.

예를 들어, 사용 가능한 별칭을 gm 및 gcm으로 제한 하려면 다음 구문을 사용 합니다. `VisibleAliases="gcm", "gp"`

**표시** 되는 매개 변수가 역할 기능 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 별칭을 제거 합니다 `ipmo` .

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

### -VisibleCmdlets

세션의 cmdlet을 이 매개 변수 값에 지정된 cmdlet으로 제한합니다. 와일드 카드 문자 및 모듈 정규화 된 이름이 지원 됩니다.

기본적으로 세션 내보내기의 모듈이 세션에 표시 되는 모든 cmdlet입니다. **SessionType** 및 **ModulesToImport** 매개 변수를 사용하여 세션으로 가져올 모듈과 스냅인을 결정할 수 있습니다. **ModulesToImport** 에서 cmdlet을 노출 하는 모듈이 없으면에서 `New-PSRoleCapabilityFile` 적절 한 모듈을 로드 하려고 시도 합니다.

**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 별칭을 제거 합니다 `ipmo` .

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleExternalCommands

세션에서 실행할 수 있는 외부 이진 파일, 스크립트 및 명령을이 매개 변수 값에 지정 된 것으로 제한 합니다.

기본적으로이 세션에는 외부 명령이 표시 되지 않습니다.

**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 별칭을 제거 합니다 `ipmo` .

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

### -VisibleFunctions

세션의 함수를이 매개 변수 값에 지정 된 것으로 제한 하 고 **functiondefinitions** 매개 변수에서 정의한 함수를 제한 합니다. 와일드카드 문자가 지원됩니다.

기본적으로 세션의 모듈에서 내보낸 모든 함수는 해당 세션에서 볼 수 있습니다. **SessionType** 및 **ModulesToImport** 매개 변수를 사용 하 여 세션으로 가져올 모듈을 결정 합니다.

**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 별칭을 제거 합니다 `ipmo` .

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleProviders

세션의 PowerShell 공급자를이 매개 변수 값에 지정 된 공급자로 제한 합니다.
와일드카드 문자가 지원됩니다.

기본적으로 세션의 모듈에서 내보낸 모든 공급자가 세션에 표시 됩니다. **SessionType** 및 **ModulesToImport** 매개 변수를 사용 하 여 세션으로 가져올 모듈을 결정 합니다.

**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 별칭을 제거 합니다 `ipmo` .

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

## 참고

## 관련 링크

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Get-PSSessionCapability](Get-PSSessionCapability.md)

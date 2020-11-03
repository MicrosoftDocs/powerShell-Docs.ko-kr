---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: d7b75b9aec6cba352d72176de59af82155d1fa17
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212858"
---
# Publish-Module

## 개요
로컬 컴퓨터에서 지정된 모듈을 온라인 갤러리에 게시합니다.

## SYNTAX

### ModuleNameParameterSet (기본값)

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ModulePathParameterSet

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Publish-Module`Cmdlet은 갤러리에 사용자 프로필의 일부로 저장 된 API 키를 사용 하 여 온라인 NuGet 기반 갤러리에 모듈을 게시 합니다. 모듈의 이름 또는 모듈을 포함하는 폴더의 경로를 통해 게시할 모듈을 지정할 수 있습니다.

이름으로 모듈을 지정 하면에서를 `Publish-Module` 실행 하 여 발견 되는 첫 번째 모듈을 게시 합니다 `Get-Module -ListAvailable <Name>` . 게시할 모듈의 최소 버전을 지정 하는 경우는 `Publish-Module` 지정한 최소 버전 보다 크거나 같은 버전으로 첫 번째 모듈을 게시 합니다.

모듈을 게시하려면 모듈에 대한 갤러리 페이지에 표시되는 메타데이터가 필요합니다. 필수 메타데이터에는 모듈 이름, 버전, 설명, 만든 이 등이 포함됩니다. 대부분의 메타 데이터는 모듈 매니페스트에서 가져오므로 `Publish-Module` **Tag** , **ReleaseNote** , **IconUri** , **ProjectUri** 및 **LicenseUri** 와 같은 매개 변수는 NuGet 기반 갤러리의 필드와 일치 하므로 일부 메타 데이터는 매개 변수에서 지정 해야 합니다.

## 예제

### 예제 1: 모듈 게시

이 예제에서 MyDscModule는 모듈 소유자의 온라인 갤러리 계정을 나타내는 API 키를 사용 하 여 온라인 갤러리에 게시 됩니다. MyDscModule가 이름, 버전, 설명 및 작성자를 지정 하는 유효한 매니페스트 모듈이 아닌 경우 오류가 발생 합니다.

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### 예제 2: 갤러리 메타 데이터를 사용 하 여 모듈 게시

이 예제에서 MyDscModule는 모듈 소유자의 갤러리 계정을 나타내는 API 키를 사용 하 여 온라인 갤러리에 게시 됩니다. 제공 된 추가 메타 데이터는 갤러리의 모듈에 대 한 웹 페이지에 표시 됩니다. 소유자는 모듈에 대 한 두 개의 검색 태그를 추가 하 여 Active Directory와 관련 합니다. 간략 한 릴리스 정보를 추가 합니다. MyDscModule가 이름, 버전, 설명 및 작성자를 지정 하는 유효한 매니페스트 모듈이 아닌 경우 오류가 발생 합니다.

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## PARAMETERS

### -AllowPrerelease

시험판으로 표시 된 모듈을 게시할 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

을 실행 하기 전에 확인 메시지를 표시 `Publish-Module` 합니다.

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

### -Credential

지정 된 패키지 공급자나 원본에 대해 모듈을 게시할 수 있는 권한을 가진 사용자 계정을 지정 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -제외

게시 된 모듈에서 제외할 파일을 정의 합니다.

```yaml
Type: System.String[]
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatVersion

**ValidateSet** 특성에 지정 된 유효한 값만 허용 합니다.

자세한 내용은 [ValidateSet Attribute 선언](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) 및 [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute)을 참조 하세요.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:
Accepted values: 2.0

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

게시할 모듈에 대 한 라이선스 조건의 URL을 지정 합니다.

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

### -Name

게시할 모듈의 이름을 지정 합니다. `Publish-Module` 에서 지정 된 모듈 이름을 검색 `$Env:PSModulePath` 합니다.

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NuGetApiKey

온라인 갤러리에 모듈을 게시 하는 데 사용 하려는 API 키를 지정 합니다. API 키는 온라인 갤러리에 있는 프로필의 일부 이며 갤러리의 사용자 계정 페이지에서 찾을 수 있습니다. API 키는 NuGet 관련 기능입니다.

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

### -Path

게시할 모듈의 경로를 지정 합니다. 이 매개 변수는 모듈이 포함 된 폴더의 경로를 허용 합니다.

```yaml
Type: System.String
Parameter Sets: ModulePathParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

이 모듈 버전의 사용자가 사용할 수 있도록 하려는 릴리스 정보 또는 주석이 포함 된 문자열을 지정 합니다.

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

### -리포지토리

을 실행 하 여 등록 된 리포지토리의 이름을 지정 합니다 `Register-PSRepository` . 리포지토리에는 유효한 NuGet URI 인 **PublishLocation** 이 있어야 합니다.
**PublishLocation** 는를 실행 하 여 설정할 수 있습니다 `Set-PSRepository` .

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

### -RequiredVersion

게시할 단일 모듈의 정확한 버전을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipAutomaticTags

태그로 포함 되지 않도록 명령 및 리소스를 제거 합니다. 모듈에 태그를 자동으로 추가 하는 것을 건너뜁니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -태그

게시 하는 모듈에 하나 이상의 태그를 추가 합니다. 예제 태그에는 DesiredStateConfiguration, DSC, DSCResourceKit 또는 PSModule이 포함 됩니다. 여러 태그를 쉼표로 구분 합니다.

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

### -WhatIf

가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Publish-Module` . cmdlet은 실행되지 않습니다.

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

### System.object. PSCredential

## 출력

### System.Object

## 참고

`Publish-Module` powershell 3.0 이상 버전의 PowerShell, windows 7 또는 Windows 2008 R2 이상 버전에서 실행 됩니다.

모듈을 게시하려면 모듈에 대한 갤러리 페이지에 표시되는 메타데이터가 필요합니다. 필수 메타데이터에는 모듈 이름, 버전, 설명, 만든 이 등이 포함됩니다. 대부분의 메타 데이터는 모듈 매니페스트에서 가져오므로 `Publish-Module` **Tag** , **ReleaseNote** , **IconUri** , **ProjectUri** 및 **LicenseUri** 와 같은 매개 변수에 일부 메타 데이터를 지정할 수 있습니다. 자세한 내용은 [POWERSHELL 갤러리 UI에 영향을 주는 패키지 매니페스트 값](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui)을 참조 하세요.

## 관련 링크

[Find-Module](Find-Module.md)

[Install-Module](Install-Module.md)

[Register-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Uninstall-Module](Uninstall-Module.md)

[Update-Module](Update-Module.md)


---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 6ef89e9143fe8883bc98723d10775bf739fe72f9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599335"
---
# Unregister-PackageSource

## 개요
등록 된 패키지 소스를 제거 합니다.

## SYNTAX

### SourceBySearch

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### SourceByInputObject

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NuGet: SourceByInputObject

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### NuGet: SourceBySearch

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### PowerShellGet: SourceByInputObject

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### PowerShellGet: SourceBySearch

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## 설명

`Unregister-PackageSource`Cmdlet은 등록 된 패키지 원본을 제거 합니다. 패키지 원본은 항상 패키지 공급자에 의해 관리 됩니다. 패키지 원본을 찾으려면 cmdlet을 사용 `Get-PackageSource` 합니다.

## 예제

### 예제 1: Nuget 공급자에 대 한 패키지 소스 등록 취소

`Unregister-PackageSource`Cmdlet은 로컬 컴퓨터에서 패키지 원본의 등록을 취소 합니다. **위치** 및 **공급자** 매개 변수를 사용 하 여 제거할 소스를 추가로 지정할 수 있습니다.

```
PS> Unregister-PackageSource -Source MyNuGet
```

`Unregister-PackageSource`Cmdlet은 **source** 매개 변수를 사용 하 여 제거할 소스를 지정 합니다.

### 예제 2: Register-packagesource 개체를 사용 하 여 패키지 등록 취소

이 예제에서는 및를 사용 하 여 `Get-PackageSource` `Unregister-PackageSource` 패키지 원본의 등록을 취소 합니다. **Register-packagesource** 개체는 변수에 저장 됩니다.

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

`$pkgsource`변수는 cmdlet에서 만든 **register-packagesource** 를 저장 합니다 `Get-PackageSource` .
`Unregister-PackageSource` 를 `$pkgsource` **InputObject** 매개 변수에 대 한 입력으로 사용 합니다.

또는 `Unregister-PackageSource` cmdlet에서 **InputObject** 매개 변수에 대 한 값을 지정할 수 있습니다.

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## PARAMETERS

### -Smi-s

구성 파일을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

컴퓨터에 액세스할 수 있는 권한이 있는 사용자 계정을 지정 하 고 명령을 실행 합니다. **User01**, **Domain01\User01** 등의 사용자 이름을 입력 하거나, cmdlet에 의해 생성 되는 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

**Credential** 매개 변수를 지정 하지 않으면 현재 사용자 계정이 사용 됩니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다. 는 보안을 제외 하 고 다음이 발생 하지 않도록 하는 제한을 재정의 합니다 `Unregister-PackageSource` .

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

### -ForceBootstrap

PackageManagement가 `Unregister-PackageSource` 지정  된 패키지 원본에 대 한 패키지 공급자를 자동으로 제거 하도록 지정 합니다.

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

### -InputObject

Cmdlet에서 **register-packagesource** 개체를 지정 하는 파이프라인 입력을 허용 `Get-PackageSource` 합니다. **InputObject** 에서는 **register-packagesource** 개체를 `Get-PackageSource` 값 또는 개체를 포함 하는 변수로 받아들입니다.

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource[]
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Location

패키지 원본이 가리키는 위치를 지정 합니다. 이 매개 변수 값은 URI, 파일 경로 또는 패키지 공급자가 지 원하는 다른 모든 대상 형식일 수 있습니다.

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

**PackageManagement** 공급자를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

공급자 이름을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PublishLocation

게시 위치를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptPublishLocation

스크립트 게시 위치를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptSourceLocation

스크립트 원본 위치를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipValidate

패키지 원본에 대 한 자격 증명의 유효성 검사를 건너뛰는 스위치입니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

패키지 원본의 이름을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

을 실행 하기 전에 확인 메시지를 표시 `Unregister-PackageSource` 합니다.

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

### -WhatIf

Cmdlet이 실행 될 경우 발생 하는 상황을 보여 줍니다 `Unregister-PackageSource` . Cmdlet이 실행 되지 않습니다.

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

### `Unregister-PackageSource` 파이프라인의 **register-packagesource** 개체를 입력으로 받아들입니다.

## 출력

### `Unregister-PackageSource` 는 출력을 생성 하지 않습니다.

## 참고

명령에 패키지 공급자를 포함 하면 cmdlet에서 동적 매개 변수를 사용할 수 있습니다. 동적 매개 변수는 패키지 공급자에만 적용 됩니다. `Get-Help`Cmdlet은 cmdlet의 매개 변수 집합을 나열 하 고 공급자의 매개 변수 집합을 포함 합니다.

## 관련 링크

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-PackageSource](Get-PackageSource.md)

[Register-PackageSource](Register-PackageSource.md)

[Set-PackageSource](Set-PackageSource.md)


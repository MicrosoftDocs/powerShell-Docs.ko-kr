---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: f29c208805894634960085cd3816ce7780b7602f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99605500"
---
# Update-Module

## 개요
온라인 갤러리에서 지정된 모듈의 최신 버전을 로컬 컴퓨터에 다운로드하여 설치합니다.

## SYNTAX

### 모두

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Update-Module`Cmdlet은 온라인 갤러리에서 모듈의 최신 버전을 설치 합니다. 업데이트를 설치 하기 전에 확인 하 라는 메시지가 표시 됩니다. 업데이트는를 사용 하 여 로컬 컴퓨터에 설치 된 모듈에 대해서만 설치 됩니다 `Install-Module` . `Update-Module``$env:PSModulePath`설치 된 모듈을 검색 합니다.

`Update-Module` 매개 변수를 지정 하지 않으면 설치 된 모든 모듈을 업데이트 합니다. 업데이트할 모듈을 지정 하려면 **Name** 매개 변수를 사용 합니다. **RequiredVersion** 매개 변수를 사용 하 여 모듈의 특정 버전으로 업데이트할 수 있습니다.

설치 된 모듈이 이미 최신 버전인 경우 모듈은 업데이트 되지 않습니다. 에서 모듈을 찾을 수 없는 경우 `$env:PSModulePath` 오류가 표시 됩니다.

설치 된 모듈을 표시 하려면를 사용 `Get-InstalledModule` 합니다.

## 예제

### 예제 1: 모든 모듈 업데이트

이 예제에서는 설치 된 모든 모듈을 온라인 갤러리의 최신 버전으로 업데이트 합니다.

```powershell
Update-Module
```

### 예제 2: 이름별로 모듈 업데이트

이 예에서는 온라인 갤러리에서 특정 모듈을 최신 버전으로 업데이트 합니다.

```powershell
Update-Module -Name SpeculationControl
```

`Update-Module`**Name** 매개 변수를 사용 하 여 **SpeculationControl** 특정 모듈을 업데이트 합니다.

### 예 3: Update-Module 실행 보기

이 예에서는 가상 시나리오를 수행 하 여가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Update-Module` . 명령이 실행 되지 않습니다.

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

`Update-Module`**WhatIf** 매개 변수를 사용 하 여가 실행 된 경우 발생 하는 결과를 표시 `Update-Module` 합니다.

### 예제 4: 모듈을 지정 된 버전으로 업데이트

이 예제에서는 모듈이 특정 버전으로 업데이트 됩니다. 버전이 온라인 갤러리에 있어야 합니다. 그렇지 않으면 오류가 표시 됩니다.

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

`Update-Module`**Name** 매개 변수를 사용 하 여 **SpeculationControl** 모듈을 지정 합니다. **RequiredVersion** 매개 변수는 **1.0.14** 버전을 지정 합니다.

### 예 5: 확인 하지 않고 모듈 업데이트

이 예에서는 온라인 갤러리에서 모듈을 최신 버전으로 업데이트 하기 위한 확인을 요청 하지 않습니다. 모듈이 이미 설치 되어 있는 경우 **Force** 매개 변수는 모듈을 다시 설치 합니다.

```powershell
Update-Module -Name SpeculationControl -Force
```

`Update-Module`**Name** 매개 변수를 사용 하 여 **SpeculationControl** 모듈을 지정 합니다. **Force** 매개 변수는 사용자 확인을 요청 하지 않고 모듈을 업데이트 합니다.

## PARAMETERS

### -AcceptLicense

패키지에 필요한 경우 설치 하는 동안 사용권 계약에 자동으로 동의 합니다.

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

### -AllowPrerelease

시험판으로 표시 된 최신 모듈을 사용 하 여 모듈을 업데이트할 수 있습니다.

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

### -Confirm

실행 하기 전에 확인 메시지를 표시 `Update-Module` 합니다.

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

모듈을 업데이트할 수 있는 권한이 있는 사용자 계정을 지정 합니다.

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

### -Force

확인을 요청 하는 메시지가 표시 되지 않고 지정 된 각 모듈을 강제로 업데이트 합니다. 모듈이 이미 설치 되어 있는 경우에는에서 모듈을 **강제로** 다시 설치 합니다.

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

### -MaximumVersion

업데이트할 단일 모듈의 최대 버전을 지정 합니다. 여러 모듈을 업데이트 하려는 경우에는이 매개 변수를 추가할 수 없습니다. **MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

업데이트할 하나 이상의 모듈 이름을 지정 합니다. `Update-Module``$env:PSModulePath`업데이트할 모듈을 검색 합니다. 지정 된 모듈 이름에 대해 일치 하는 항목이 없는 경우 `$env:PSModulePath` 오류가 발생 합니다.

와일드 카드는 모듈 이름에 허용 됩니다. 지정 된 이름에 와일드 카드 문자를 추가 하 고 일치 항목을 찾을 수 없는 경우 오류가 발생 하지 않습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

작업 중인 항목을 나타내는 개체를 반환합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -프록시

인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

**프록시** 매개 변수로 지정 된 프록시 서버를 사용할 수 있는 권한을 가진 사용자 계정을 지정 합니다.

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

### -RequiredVersion

기존에 설치 된 모듈을 업데이트할 정확한 버전을 지정 합니다. **RequiredVersion** 에 지정 된 버전이 온라인 갤러리에 있어야 합니다. 그렇지 않으면 오류가 표시 됩니다. 단일 명령으로 둘 이상의 모듈이 업데이트 되는 경우 **RequiredVersion** 을 사용할 수 없습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -범위

모듈의 설치 범위를 지정합니다. 이 매개 변수에 허용 되는 값은 **AllUsers** 및 **CurrentUser** 입니다. **Scope** 가 지정 되지 않은 경우 업데이트는 **CurrentUser** 범위에 설치 됩니다.

**AllUsers** 범위에는 상승 된 권한이 필요 하 고 컴퓨터의 모든 사용자가 액세스할 수 있는 위치에 모듈을 설치 합니다.

`$env:ProgramFiles\PowerShell\Modules`

**CurrentUser** 는 높은 권한이 필요 하지 않으며 컴퓨터의 현재 사용자만 액세스할 수 있는 위치에 모듈을 설치 합니다.

`$home\Documents\PowerShell\Modules`

**범위** 를 정의 하지 않으면 PowerShellGet 버전에 따라 기본값이 설정 됩니다.

- PowerShellGet 버전 2.0.0 이상에서 기본값은 **CurrentUser** 이며, 설치 시 권한 상승이 필요 하지 않습니다.
- PowerShellGet 1. x 버전에서 기본값은 **AllUsers** 이며, 설치 시 권한 상승이 필요 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Update-Module` . Cmdlet이 실행 되지 않습니다.

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

### System.String[]

### System.String

### System.object. PSCredential

### System.Uri

## 출력

### System.Object

## 참고

PowerShell 버전 6.0 이상에서는 기본 설치 범위가 항상 **CurrentUser** 입니다.
**CurrentUser** 의 모듈 업데이트에 `$home\Documents\PowerShell\Modules` 는 상승 된 권한이 필요 하지 않습니다. **AllUsers**,에 대 한 모듈 업데이트에는 `$env:ProgramFiles\PowerShell\Modules` 상승 된 권한이 필요 합니다.

> [!IMPORTANT]
> 2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다. TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다. 다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.

`Update-Module` powershell 3.0 이상 버전의 PowerShell, windows 7 또는 Windows 2008 R2 이상 버전에서 실행 됩니다.

**Name** 매개 변수를 사용 하 여 지정한 모듈을를 사용 하 여 설치 하지 않은 경우 `Install-Module` 오류가 발생 합니다.

을 `Update-Module` 실행 하 여 온라인 갤러리에서 설치한 모듈 에서만 실행할 수 있습니다 `Install-Module` .

`Update-Module`에서 사용 중인 이진 파일을 업데이트 하려고 하면에서 `Update-Module` 문제 프로세스를 식별 하는 오류를 반환 합니다. 프로세스가 중지 된 후 사용자에 게 다시 시도 하는 알림이 사용자에 게 `Update-Module` 있습니다.

## 관련 링크

[Find-Module](Find-Module.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[Publish-Module](Publish-Module.md)

[제거 모듈](Uninstall-Module.md)

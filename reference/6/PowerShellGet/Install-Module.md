---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: 67d68427ba8e3c305b50ccbc19c6d48d574e3351
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2020
ms.locfileid: "93219105"
---
# Install-Module

## 개요
리포지토리에서 하나 이상의 모듈을 다운로드 하 고 로컬 컴퓨터에 설치 합니다.

## SYNTAX

### NameParameterSet (기본값)

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Install-Module`Cmdlet은 온라인 리포지토리에서 지정 된 조건을 충족 하는 하나 이상의 모듈을 가져옵니다. Cmdlet은 검색 결과가 유효한 모듈 인지 확인 하 고 모듈 폴더를 설치 위치로 복사 합니다. 설치 후 설치 된 모듈을 자동으로 가져오지 않습니다.
지정 된 모듈의 최소, 최대 및 정확한 버전에 따라 설치 되는 모듈을 필터링 할 수 있습니다.

설치 되는 모듈의 이름이 나 버전이 같거나 기존 모듈의 명령을 포함 하는 경우 경고 메시지가 표시 됩니다. 모듈을 설치 하 고 경고를 재정의할지를 확인 한 후에는 `-Force` 및 `-AllowClobber` 매개 변수를 사용 합니다. 리포지토리 설정에 따라 계속 하려면 모듈 설치에 대 한 프롬프트에 응답 해야 할 수도 있습니다.

이 예제에서는 [PowerShell 갤러리](https://www.powershellgallery.com/) 를 등록 된 유일한 리포지토리로 사용 합니다. `Get-PSRepository` 등록 된 리포지토리를 표시 합니다. 등록 된 리포지토리가 여러 개 있는 경우 `-Repository` 매개 변수를 사용 하 여 리포지토리의 이름을 지정 합니다.

## 예제

### 예제 1: 모듈 찾기 및 설치

이 예제에서는 리포지토리에서 모듈을 찾아 설치 합니다.

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

는 `Find-Module` **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다. 기본적으로 최신 버전의 모듈은 리포지토리에서 다운로드 됩니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Install-Module` . `Install-Module` 의 모든 사용자에 대 한 모듈을 설치 `$env:ProgramFiles\PowerShell\Modules` 합니다.

### 예제 2: 이름별로 모듈 설치

이 예제에서는 최신 버전의 **PowerShellGet** 모듈이 설치 되어 있습니다.

```powershell
Install-Module -Name PowerShellGet
```

는 `Install-Module` **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다. 기본적으로 최신 버전의 모듈은 리포지토리에서 다운로드 되어 설치 됩니다.

### 예제 3: 최소 버전을 사용 하 여 모듈 설치

이 예제에서는 **PowerShellGet** 모듈의 최소 버전을 설치 합니다. **MinimumVersion** 매개 변수는 설치 해야 하는 모듈의 가장 낮은 버전을 지정 합니다. 최신 버전의 모듈을 사용할 수 있는 경우 모든 사용자에 대해 해당 버전이 다운로드 되어 설치 됩니다.

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

는 `Install-Module` **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다. **MinimumVersion** 매개 변수는 버전 **2.0.1** 을 리포지토리에서 다운로드 하 여 설치 하도록 지정 합니다. 버전 **2.0.4 이상을** 를 사용할 수 있기 때문에 모든 사용자에 대해 해당 버전이 다운로드 되어 설치 됩니다.

### 예제 4: 모듈의 특정 버전 설치

이 예제에서는 특정 버전의 **PowerShellGet** 모듈이 설치 되어 있습니다.

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

는 `Install-Module` **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다. **RequiredVersion** 매개 변수는 버전 **2.0.0** 가 모든 사용자에 게 다운로드 및 설치 되도록 지정 합니다.

### 예 5: 현재 사용자에 대해서만 모듈 설치

이 예에서는 현재 사용자에 대해서만 최신 버전의 모듈을 다운로드 하 여 설치 합니다.

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

는 `Install-Module` **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.
`Install-Module` 최신 버전의 **PowerShellGet** 을 현재 사용자의 디렉터리에 다운로드 하 여 설치 `$home\Documents\PowerShell\Modules` 합니다.

## PARAMETERS

### -AcceptLicense

라이선스가 필요한 모듈의 경우에는 설치 중에 **Acceptlicense** 가 사용권 계약에 자동으로 동의 합니다. 자세한 내용은 [라이선스 동의가 필요한 모듈](/powershell/scripting/gallery/concepts/module-license-acceptance)을 참조 하세요.

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

### -AllowClobber

컴퓨터의 기존 명령과 관련 된 설치 충돌에 대 한 경고 메시지를 재정의 합니다.
모듈에 의해 설치 되는 명령과 이름이 같은 기존 명령을 덮어씁니다.
**AllowClobber** 및 **Force** 는 명령에 함께 사용할 수 있습니다 `Install-Module` .

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

시험판으로 표시 된 모듈을 설치할 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Cmdlet을 실행 하기 전에 확인 메시지를 표시 `Install-Module` 합니다.

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

지정 된 패키지 공급자 또는 원본에 대해 모듈을 설치할 수 있는 권한이 있는 사용자 계정을 지정 합니다.

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

모듈을 설치 하 고 모듈 설치 충돌에 대 한 경고 메시지를 재정의 합니다. 컴퓨터에 같은 이름의 모듈이 이미 있으면 **Force** 를 사용 하 여 여러 버전을 설치할 수 있습니다. 이름과 버전이 같은 기존 모듈이 있으면에서 해당 버전을 **강제로** 덮어씁니다. **Force** 및 **AllowClobber** 는 명령에 함께 사용할 수 있습니다 `Install-Module` .

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

파이프라인 입력에 사용 됩니다.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -MaximumVersion

설치할 단일 모듈의 최대 버전을 지정 합니다. 설치 된 버전은 **MaximumVersion** 보다 작거나 같아야 합니다. 여러 모듈을 설치 하려는 경우 **MaximumVersion** 을 사용할 수 없습니다. **MaximumVersion** 및 **RequiredVersion** 은 동일한 명령에서 사용할 수 없습니다 `Install-Module` .

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

설치할 단일 모듈의 최소 버전을 지정 합니다. 설치 된 버전은 **MinimumVersion** 보다 크거나 같아야 합니다. 최신 버전의 모듈을 사용할 수 있는 경우 최신 버전이 설치 됩니다. 여러 모듈을 설치 하려는 경우 **MinimumVersion** 을 사용할 수 없습니다.
**MinimumVersion** 및 **RequiredVersion** 은 동일한 명령에서 사용할 수 없습니다 `Install-Module` .

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

온라인 갤러리에서 설치할 모듈의 정확한 이름을 지정 합니다. 쉼표로 구분 된 모듈 이름 목록이 허용 됩니다. 모듈 이름은 리포지토리의 모듈 이름과 일치 해야 합니다. `Find-Module`를 사용 하 여 모듈 이름 목록을 가져옵니다.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

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

**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.

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

### -리포지토리

**리포지토리** 매개 변수를 사용 하 여 모듈을 다운로드 하 고 설치 하는 데 사용 되는 리포지토리를 지정 합니다. 여러 리포지토리를 등록할 때 사용 됩니다. 명령에 등록 된 리포지토리의 이름을 지정 합니다 `Install-Module` . 리포지토리를 등록 하려면를 사용 `Register-PSRepository` 합니다.
등록 된 리포지토리를 표시 하려면를 사용 `Get-PSRepository` 합니다.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

설치할 단일 모듈의 정확한 버전을 지정 합니다. 지정 된 버전에 대 한 리포지토리에 일치 하는 항목이 없는 경우 오류가 표시 됩니다. 여러 모듈을 설치 하려는 경우 **RequiredVersion** 을 사용할 수 없습니다. **RequiredVersion** 은 `Install-Module` **MinimumVersion** 또는 **MaximumVersion** 과 동일한 명령에서 사용할 수 없습니다.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -범위

모듈의 설치 범위를 지정합니다. 이 매개 변수에 허용 되는 값은 **AllUsers** 및 **CurrentUser** 입니다.

**AllUsers** 범위는 컴퓨터의 모든 사용자가 액세스할 수 있는 위치에 모듈을 설치 합니다.

`$env:ProgramFiles\PowerShell\Modules`

**CurrentUser** 는 컴퓨터의 현재 사용자만 액세스할 수 있는 위치에 모듈을 설치 합니다. 다음은 그 예입니다. 

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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipPublisherCheck

컴퓨터에 이미 존재 하는 모듈의 최신 버전을 설치할 수 있습니다. 예를 들어 신뢰할 수 있는 게시자가 기존 모듈을 디지털 서명 하지만 새 버전이 신뢰할 수 있는 게시자에 의해 디지털로 서명 되지 않은 경우를 예로 들 수 있습니다.

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

### -WhatIf

명령이 실행 된 경우 발생 하는 상황을 보여 줍니다 `Install-Module` . cmdlet은 실행되지 않습니다.

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

### PSRepositoryItemInfo

`Find-Module` 파이프라인에서로 전송할 수 있는 **PSRepositoryItemInfo** 개체를 만듭니다 `Install-Module` .

### System.String[]

### System.web. PSObject []

### System.String

### System.object. PSCredential

### System.Uri

## 출력

### PSRepositoryItemInfo.

**PassThru** 매개 변수를 사용 하는 경우 `Install-Module` 은 모듈에 대 한 **PSRepositoryItemInfo** 개체를 출력 합니다. 이는 cmdlet에서 가져오는 것과 동일한 정보입니다 `Find-Module` .

## 참고

`Install-Module` windows 7 또는 windows 2008 R2 이상 릴리스에서 PowerShell 5.0 이상 버전에서 실행 됩니다.

보안 모범 사례로, cmdlet 또는 함수를 처음 실행 하기 전에 모듈의 코드를 평가 합니다. 악성 코드가 포함 된 모듈 실행을 방지 하기 위해 설치 후 설치 된 모듈을 자동으로 가져오지 않습니다.

**이름** 매개 변수로 지정 된 모듈 이름이 리포지토리에 없으면에서 `Install-Module` 오류를 반환 합니다.

여러 모듈을 설치 하려면 **Name** 매개 변수를 사용 하 고 쉼표로 구분 된 모듈 이름 배열을 지정 합니다. 여러 모듈 이름을 지정 하는 경우 **MinimumVersion** , **MaximumVersion** 또는 **RequiredVersion** 을 사용할 수 없습니다. `Find-Module` 파이프라인에서로 전송할 수 있는 **PSRepositoryItemInfo** 개체를 만듭니다 `Install-Module` . 파이프라인은 단일 명령으로 설치할 여러 모듈을 지정 하는 또 다른 방법입니다.

기본적으로 **AllUsers** 의 범위에 대 한 모듈은에 설치 됩니다 `$env:ProgramFiles\PowerShell\Modules` . PowerShell DSC (필요한 상태 구성) 리소스를 설치할 때 기본적으로 혼동을 방지 합니다.

모듈 설치에 실패 하 고 `.psm1` `.psd1` 폴더 내에 같은 이름의, 또는가 없는 경우 가져올 수 없습니다 `.dll` . **Force** 매개 변수를 사용 하 여 모듈을 설치 합니다.

기존 모듈의 버전이 **name** 매개 변수에 지정 된 이름과 일치 하 고 **MinimumVersion** 또는 **RequiredVersion** 매개 변수를 사용 하지 않으면 `Install-Module` 자동으로 계속 되지만 모듈이 설치 되지 않습니다.

기존 모듈의 버전이 **MinimumVersion** 매개 변수 값 보다 크거나 **RequiredVersion** 매개 변수 값과 같으면가 `Install-Module` 자동으로 계속 되지만 모듈을 설치 하지 않습니다.

기존 모듈이 **MinimumVersion** 또는 **RequiredVersion** 매개 변수로 지정 된 값과 일치 하지 않으면 명령에서 오류가 발생 합니다 `Install-Module` . 예를 들어 기존에 설치 된 모듈의 버전이 **MinimumVersion** 값 보다 낮거나 **RequiredVersion** 값과 같지 않은 경우입니다.

모듈을 설치 하면 모듈 게시자에 필요한 대로 지정 된 모든 종속 모듈도 설치 됩니다.
게시자는 모듈 매니페스트에서 필요한 모듈 및 해당 버전을 지정 합니다.

## 관련 링크

[Find-Module](Find-Module.md)

[Get-PSRepository](Get-PSRepository.md)

[모듈 가져오기](../Microsoft.PowerShell.Core/Import-Module.md)

[Publish-Module](Publish-Module.md)

[Register-PSRepository](Register-PSRepository.md)

[Uninstall-Module](Uninstall-Module.md)

[Update-Module](Update-Module.md)

[about_Module](../Microsoft.PowerShell.Core/About/about_Modules.md)

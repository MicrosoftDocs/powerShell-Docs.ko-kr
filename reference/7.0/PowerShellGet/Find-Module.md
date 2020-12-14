---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: c6468d2f8226cb26ec5385c7d5a8a895155ad673
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892657"
---
# Find-Module

## 개요
리포지토리에서 지정 된 조건과 일치 하는 모듈을 찾습니다.

## SYNTAX

### 모두

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## 설명

`Find-Module`Cmdlet은 리포지토리에서 지정 된 조건과 일치 하는 모듈을 찾습니다.
`Find-Module` 찾은 각 모듈에 대해 **PSRepositoryItemInfo** 개체를 반환 합니다. 개체는와 같은 cmdlet에 파이프라인으로 전송 될 수 있습니다 `Install-Module` .

처음으로 `Find-Module` 리포지토리를 사용 하려고 시도 하면 업데이트를 설치 하 라는 메시지가 표시 될 수 있습니다.
리포지토리 원본이 cmdlet에 등록 되지 않은 경우 `Register-PSRepository` 오류가 반환 됩니다.

`Find-Module` 버전을 제한 하는 매개 변수를 사용 하지 않는 경우 최신 버전의 모듈을 반환 합니다. 리포지토리의 모듈 버전 목록을 가져오려면 **allversions)** 매개 변수를 사용 합니다.

**MinimumVersion** 매개 변수를 지정 하는 경우는 `Find-Module` 최소 보다 크거나 같은 모듈 버전을 반환 합니다. 리포지토리에 사용할 수 있는 최신 버전이 있으면 최신 버전이 반환 됩니다.

**MaximumVersion** 매개 변수가 지정 된 경우는 `Find-Module` 지정 된 버전을 초과 하지 않는 모듈의 최신 버전을 반환 합니다.

**RequiredVersion** 매개 변수를 지정 하면는 `Find-Module` 지정 된 버전과 정확히 일치 하는 모듈 버전만 반환 합니다. `Find-Module` 원본 간의 이름 충돌이 발생할 수 있으므로 사용 가능한 모든 모듈을 검색 합니다.

다음 예에서는 [PowerShell 갤러리](https://www.powershellgallery.com/) 를 등록 된 유일한 리포지토리로 사용 합니다. `Get-PSRepository` 등록 된 리포지토리를 표시 합니다. 등록 된 리포지토리가 여러 개 있는 경우 `-Repository` 매개 변수를 사용 하 여 리포지토리의 이름을 지정 합니다.

## 예제

### 예제 1: 이름별로 모듈 찾기

이 예에서는 기본 리포지토리에서 모듈을 찾습니다.

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

`Find-Module`Cmdlet은 **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.

### 예제 2: 비슷한 이름의 모듈 찾기

이 예제에서는 별표 ( `*` ) 와일드 카드를 사용 하 여 비슷한 이름의 모듈을 찾습니다.

```powershell
Find-Module -Name PowerShell*
```

```Output
Version   Name                            Repository    Description
-------   ----                            ----------    -----------
0.4.0     powershell-yaml                 PSGallery     Powershell module for serializing and...
2.1.0     PowerShellGet                   PSGallery     PowerShell module with commands for...
1.9       Powershell.Helper.Extension     PSGallery     # Powershell.Helper.Extension...
3.1       PowerShellHumanizer             PSGallery     PowerShell Humanizer wraps Humanizer...
4.0       PowerShellISEModule             PSGallery     a module that adds capability to the ISE
```

`Find-Module`Cmdlet은 **Name** 매개 변수를 별표 () 와일드 카드와 함께 사용 하 여 `*` **PowerShell** 이 포함 된 모든 모듈을 찾습니다.

### 예 3: 최소 버전 별로 모듈 찾기

이 예제에서는 모듈의 최소 버전을 검색 합니다. 리포지토리에 최신 버전의 모듈이 포함 되어 있으면 최신 버전이 반환 됩니다.

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

`Find-Module`Cmdlet은 **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다. **MinimumVersion** 은 **1.6.5** 버전을 지정 합니다. `Find-Module` PowerShellGet 버전 **2.1.0** 가 최소 버전을 초과 하 고 최신 버전 이므로 반환 합니다.

### 예제 4: 특정 버전 별로 모듈 찾기

이 예제에서는 모듈의 특정 버전을 나타내는 개체를 반환 합니다. 지정 된 버전을 찾을 수 없는 경우 오류가 반환 됩니다.

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

`Find-Module`Cmdlet은 **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다. **RequiredVersion** 매개 변수는 **1.6.5** 버전을 지정 합니다.

### 예 5: 특정 리포지토리에서 모듈 찾기

이 예에서는 **리포지토리** 매개 변수를 사용 하 여 특정 리포지토리의 모듈을 찾습니다.

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

`Find-Module`Cmdlet은 **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다. **리포지토리** 매개 변수는 **PSGallery** 리포지토리를 검색 하도록 지정 합니다.

### 예 6: 여러 리포지토리에서 모듈 찾기

이 예제에서는를 사용 하 여 `Register-PSRepository` 리포지토리를 지정 합니다. `Find-Module` 리포지토리를 사용 하 여 모듈을 검색 합니다.

```powershell
Register-PSRepository -Name MySource -SourceLocation https://www.myget.org/F/powershellgetdemo/
Find-Module -Name Contoso* -Repository PSGallery, MySource
```

```Output
Repository    Version   Name             Description
----------    -------   ----             -----------
PSGallery     2.0.0.0   ContosoServer    Cmdlets and DSC resources for managing Contoso Server...
MySource      1.2.0.0   ContosoClient    Cmdlets and DSC resources for managing Contoso Client...
```

`Register-PSRepository`Cmdlet은 새 리포지토리를 등록 합니다. **Name** 매개 변수는 **MySource** 이름을 할당 합니다. 위치 **매개 변수** 는 리포지토리의 주소를 지정 합니다.

`Find-Module`Cmdlet은 **Name** 매개 변수와 별표 ( `*` ) 와일드 카드를 사용 하 여 **Contoso** 모듈을 지정 합니다. **리포지토리** 매개 변수는 **PSGallery** 및 **MySource** 라는 두 리포지토리를 검색 하도록 지정 합니다.

### 예 7: DSC 리소스를 포함 하는 모듈 찾기

이 명령은 DSC 리소스를 포함 하는 모듈을 반환 합니다. **Include** 매개 변수에는 리포지토리를 검색 하는 데 사용 되는 4 가지 미리 정의 된 기능이 있습니다. 탭-전체를 사용 하 여 **include** 매개 변수에서 지 원하는 네 가지 기능을 표시 합니다.

```powershell
Find-Module -Repository PSGallery -Includes DscResource
```

```Output
Version     Name                            Repository    Description
-------     ----                            ----------    -----------
2.7.0       Carbon                          PSGallery     Carbon is a PowerShell module...
8.5.0.0     xPSDesiredStateConfiguration    PSGallery     The xPSDesiredStateConfiguration module...
1.3.1       PackageManagement               PSGallery     PackageManagement (a.k.a. OneGet) is...
2.7.0.0     xWindowsUpdate                  PSGallery     Module with DSC Resources...
3.2.0.0     xCertificate                    PSGallery     This module includes DSC resources...
3.1.0.0     xPowerShellExecutionPolicy      PSGallery     This DSC resource can change the user...
```

`Find-Module`이 cmdlet은 **리포지토리** 매개 변수를 사용 하 여 리포지토리 ( **PSGallery**)를 검색 합니다.
**Include** 매개 변수는 매개 변수가 리포지토리에서 검색할 수 있는 기능인 **get-dscresource** 를 지정 합니다.

### 예 8: 필터를 사용 하 여 모듈 찾기

이 예에서는 모듈을 찾기 위해 필터를 사용 하 여 리포지토리를 검색 합니다.

NuGet 기반 리포지토리의 경우 **필터** 매개 변수는 인수에 대 한 이름, 설명 및 태그를 검색 합니다.

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

`Find-Module`Cmdlet은 **필터** 매개 변수를 사용 하 여 저장소에서 **AppDomain** 을 검색 합니다.

## PARAMETERS

### -AllowPrerelease

시험판으로 표시 된 결과 모듈에를 포함 합니다.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Allversions)

모든 버전의 모듈을 결과에 포함 하도록 지정 합니다. **Allversions)** 매개 변수는 **MinimumVersion**, **MaximumVersion** 또는 **RequiredVersion** 매개 변수와 함께 사용할 수 없습니다.

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

### -Command

모듈에서 찾을 명령의 배열을 지정 합니다. 명령은 함수 또는 워크플로가 될 수 있습니다.

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

### -Get-dscresource

DSC 리소스를 포함 하는 모듈의 이름 또는 이름의 일부를 지정 합니다. PowerShell 규칙에 따라는 여러 인수를 제공 하는 경우 **또는** 검색을 수행 합니다.

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

### -Filter

**PackageManagement** 공급자별 검색 구문을 기반으로 하는 필터를 지정 합니다. NuGet 모듈의 경우이 매개 변수는 [PowerShell 갤러리](https://www.powershellgallery.com/) 웹 사이트의 검색 표시줄을 사용 하 여 검색 하는 것과 동일 합니다.

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

### -IncludeDependencies

이 작업에 **Name** 매개 변수에 지정 된 모듈에 종속 된 모든 모듈이 포함 됨을 나타냅니다.

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

### -포함

는 특정 종류의 PowerShell 기능을 포함 하는 모듈만 반환 합니다. 예를 들어 **get-dscresource** 를 포함 하는 모듈만 찾을 수 있습니다. 이 매개 변수에 허용 되는 값은 다음과 같습니다.

- Cmdlet
- DscResource
- 함수
- RoleCapability

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: DscResource, Cmdlet, Function, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

검색 결과에 포함할 모듈의 최대 또는 최신 버전을 지정 합니다.
**MaximumVersion** 및 **RequiredVersion** 은 동일한 명령에서 사용할 수 없습니다.

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

### -MinimumVersion

결과에 포함할 모듈의 최소 버전을 지정 합니다. **MinimumVersion** 및 **RequiredVersion** 은 동일한 명령에서 사용할 수 없습니다.

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

리포지토리에서 검색할 모듈의 이름을 지정 합니다. 쉼표로 구분 된 모듈 이름 목록이 허용 됩니다. 와일드 카드가 허용 됩니다.

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

**리포지토리** 매개 변수를 사용 하 여 모듈을 검색할 리포지토리를 지정 합니다. 여러 리포지토리를 등록할 때 사용 됩니다. 쉼표로 구분 된 저장소 목록을 허용 합니다. 리포지토리를 등록 하려면를 사용 `Register-PSRepository` 합니다. 등록 된 리포지토리를 표시 하려면를 사용 `Get-PSRepository` 합니다.

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

### -RequiredVersion

결과에 포함할 모듈의 정확한 버전 번호를 지정 합니다. **RequiredVersion** 은 **MinimumVersion** 또는 **MaximumVersion** 과 동일한 명령에서 사용할 수 없습니다.

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

### -Find-rolecapability

역할 기능의 배열을 지정 합니다.

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

### -Tag

태그의 배열을 지정 합니다. 예제 태그에는 **DesiredStateConfiguration**, **DSC**, **Dscresourcekit** 또는 **psmodule** 이 포함 됩니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String[]

### System.String

### System.Uri

### System.object. PSCredential

## 출력

### PSRepositoryItemInfo

`Find-Module` 와 같은 cmdlet에 파이프라인으로 전송할 수 있는 **PSRepositoryItemInfo** 개체를 만듭니다 `Install-Module` .

## 참고

> [!IMPORTANT]
> 2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다. TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다. 다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.

## 관련 링크

[Get-PSRepository](Get-PSRepository.md)

[Install-Module](Install-Module.md)

[Publish-Module](Publish-Module.md)

[Save-Module](Save-Module.md)

[Uninstall-Module](Uninstall-Module.md)

[Update-Module](Update-Module.md)

[Register-PSRepository](Register-PSRepository.md)

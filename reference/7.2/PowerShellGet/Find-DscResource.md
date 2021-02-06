---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/04/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-DscResource
ms.openlocfilehash: e1cb814d349d6b77885ebaaf176a7c3153d93eb5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99603070"
---
# Find-DscResource

## 개요
DSC (필요한 상태 구성) 리소스를 찾습니다.

## SYNTAX

### 모두

```
Find-DscResource [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## 설명

`Find-DscResource`Cmdlet은 모듈에 포함 된 DSC 리소스를 찾기 위해 등록 된 리포지토리를 검색 합니다. 기본적으로는 `Find-DscResource` 등록 된 모든 리포지토리를 검색 합니다.

에서 찾은 각 모듈에 대해 `Find-DscResource` **Psgetdscresourceinfo** 개체가 반환 됩니다.
**Psgetdscresourceinfo** 개체를 파이프라인에서 cmdlet으로 보낼 수 있습니다 `Install-Module` .
`Install-Module` 모듈을 설치 합니다.

## 예제

### 예 1: 모든 DSC 리소스 찾기

`Find-DscResource` 등록 된 리포지토리에서 DSC 리소스를 반환 합니다. 특정 리포지토리를 검색 하려면 **리포지토리** 매개 변수를 사용 합니다.

```powershell
Find-DscResource
```

```Output
Name                           Version    ModuleName                     Repository
----                           -------    ----------                     ----------
Carbon_Privilege               2.8.1      Carbon                         PSGallery
Carbon_ScheduledTask           2.8.1      Carbon                         PSGallery
Carbon_Service                 2.8.1      Carbon                         PSGallery
PackageManagement              1.4        PackageManagement              PSGallery
PackageManagementSource        1.4        PackageManagement              PSGallery
PSModule                       2.1.4      PowerShellGet                  PSGallery
PSRepository                   2.1.4      PowerShellGet                  PSGallery
xArchive                       8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xDSCWebService                 8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xEnvironment                   8.7.0.0    xPSDesiredStateConfiguration   PSGallery
```

### 예제 2: 이름별로 DSC 리소스 찾기

`Find-DscResource` 이름별로 DSC 리소스를 찾습니다. 리소스 이름 배열을 구분 하려면 쉼표를 사용 합니다.

```powershell
Find-DscResource -Name xWebsite, xWebApplication, xWebSiteDefaults
```

```Output
Name               Version    ModuleName            Repository
----               -------    ----------            ----------
xWebApplication    2.6.0.0    xWebAdministration    PSGallery
xWebsite           2.6.0.0    xWebAdministration    PSGallery
xWebSiteDefaults   2.6.0.0    xWebAdministration    PSGallery
```

`Find-DscResource`**Name** 매개 변수를 사용 하 여 DSC 리소스의 지정 된 배열을 찾습니다.

### 예 3: DSC 리소스 찾기 및 설치

`Find-DscResource` DSC 리소스를 찾아서 설치할 파이프라인에서 개체를 보냅니다.
설치 후 `Get-InstalledModule` 에는를 사용 하 여 결과를 확인 합니다.

동일한 모듈의 여러 리소스를 파이프라인에서로 보낼 수 있습니다 `Install-Module` .
`Install-Module` 모듈을 한 번만 설치 하려고 시도 합니다.

```powershell
Find-DscResource -Name xWebsite | Install-Module
```

`Find-DscResource`**Name** 매개 변수를 사용 하 여 **xwebsite** 라는 리소스를 찾습니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Install-Module` . `Install-Module` 리소스에 대 한 **Xwebadministration** 모듈을 설치 합니다.

### 예제 4: 모듈의 모든 DSC 리소스 찾기

`Find-DscResource` 지정 된 모듈에 포함 된 모든 DSC 리소스를 찾습니다. 기본적으로 현재 버전이 표시 됩니다. 다른 버전을 표시 하려면 **allversions)** 또는 **requiredversions** 매개 변수를 사용 합니다.

```powershell
Find-DscResource -ModuleName xWebAdministration
```

```Output
Name                                Version    ModuleName              Repository
----                                -------    ----------              ----------
WebApplicationHandler               2.6.0.0    xWebAdministration      PSGallery
xIisFeatureDelegation               2.6.0.0    xWebAdministration      PSGallery
xIisHandler                         2.6.0.0    xWebAdministration      PSGallery
xIisLogging                         2.6.0.0    xWebAdministration      PSGallery
```

`Find-DscResource`**ModuleName** 매개 변수를 사용 하 여 **xwebadministration** 를 지정 하 고 모듈에 포함 된 DSC 리소스를 찾습니다. 각 리소스의 현재 버전이 표시 됩니다.

### 예 5: 태그 및 필요한 버전으로 DSC 리소스 찾기

DSC 리소스는 parameters **태그** 및 **RequiredVersion** 을 사용 하 여 찾을 수 있습니다. **태그** 리포지토리에 지정 된 태그를 포함 하는 모든 리소스의 현재 버전을 표시 합니다.
**RequiredVersion** 은 **ModuleName** 매개 변수를 요구 하 고 **Name** 매개 변수는 선택 사항입니다. **Name** 및 **ModuleName** 매개 변수는 출력을 제한 합니다. **Allversions)** 매개 변수를 사용 하 여 DSC 리소스의 사용 가능한 버전을 표시 합니다.

```powershell
Find-DscResource -ModuleName xWebAdministration -Tag DSC -RequiredVersion 1.20
```

```output
Name                    Version    ModuleName             Repository
----                    -------    ----------             ----------
xIisFeatureDelegation   1.20.0.0   xWebAdministration     PSGallery
xIisHandler             1.20.0.0   xWebAdministration     PSGallery
xIisLogging             1.20.0.0   xWebAdministration     PSGallery
xIisMimeTypeMapping     1.20.0.0   xWebAdministration     PSGallery
```

### 예제 6: 필터를 사용 하 여 리소스 찾기

`Find-DscResource` 모든 리소스를 찾은 다음 **필터** 매개 변수를 사용 하 여 **도메인별** 결과를 지정 합니다. **Filter** 매개 변수는 개체의 설명 또는 모듈 이름에서 필터 값을 찾습니다. Cmdlet을 사용 `Select-Object` 하 여 개체의 속성을 볼 수 있습니다.

```powershell
Find-DscResource -Filter Domain
```

```output
Name                    Version    ModuleName                 Repository
----                    -------    ----------                 ---------
xComputer               4.1.0.0    xComputerManagement        PSGallery
Computer                6.4.0.0    ComputerManagementDsc      PSGallery
xDSCDomainjoin          1.1        xDSCDomainjoin             PSGallery
xDisk                   1.0        xDisk                      PSGallery
xDSCFirewall            1.6.21     xDSCFirewall               PSGallery
dmAwsTagInstance        1.0.1      domainAwsDSCResources      PSGallery
```

## PARAMETERS

### -AllowPrerelease

결과에서 시험판으로 표시 된 리소스를 포함 합니다.

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

### -Allversions)

**Allversions)** 매개 변수는 각 DSC 리소스의 사용 가능한 버전을 표시 합니다. **Allversions)** 매개 변수는 **MinimumVersion**, **MaximumVersion** 또는 **RequiredVersion** 매개 변수와 함께 사용할 수 없습니다.

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

### -Filter

**PackageManagement** 공급자의 검색 구문에 따라 리소스를 찾습니다. 예를 들어 **ModuleName** 및 **Description** 속성 내에서 검색할 단어를 지정 합니다.

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

### -MaximumVersion

결과에 포함할 리소스의 최대 버전을 지정 합니다. **MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.

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

### -MinimumVersion

결과에 포함할 리소스의 최소 버전을 지정 합니다. **MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.

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

### -ModuleName

DSC 리소스를 포함 하는 모듈을 지정 합니다.

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

### -Name

리소스의 이름을 지정합니다. 기본값은 모든 리소스입니다. 리소스 이름 배열을 구분 하려면 쉼표를 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
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

**Proxy** 매개 변수에 지정 된 프록시 서버를 사용할 수 있는 권한을 가진 사용자 계정을 지정 합니다.

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

리소스를 검색할 리포지토리를 지정 합니다. 저장소 이름 배열을 구분 하려면 쉼표를 사용 합니다.

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

결과에 포함할 모듈의 정확한 버전 번호를 지정 합니다. **RequiredVersion** 및 **MinimumVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.

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

### -Tag

리포지토리의 모듈을 범주화 하는 태그를 지정 합니다. 태그 배열을 구분 하려면 쉼표를 사용 합니다.

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

## 출력

### PSGetDscResourceInfo

`Find-DscResource`**Psgetdscresourceinfo** 개체를 반환 합니다.

## 참고

> [!IMPORTANT]
> 2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다. TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다. 다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.

## 관련 링크

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[Register-PSRepository](Register-PSRepository.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[제거 모듈](Uninstall-Module.md)

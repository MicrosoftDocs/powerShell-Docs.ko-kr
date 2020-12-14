---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: d3300e0f378139cc873ffef1e798326100644d94
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889813"
---
# Find-RoleCapability

## 개요
모듈에서 역할 기능을 찾습니다.

## SYNTAX

### 모두

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
[-Repository <String[]>] [<CommonParameters>]
```

## 설명

`Find-RoleCapability`Cmdlet은 등록 된 리포지토리를 검색 하 여 PowerShell 역할 기능 및 모듈을 찾습니다.

에서 찾은 각 역할 기능에 대해 `Find-RoleCapability` **PSGetRoleCapabilityInfo** 개체가 반환 됩니다. **PSGetRoleCapabilityInfo** 개체는 파이프라인에서 또는 cmdlet으로 보낼 수 `Install-Module` 있습니다 `Save-Module` .

PowerShell 역할 기능은 충분 한 관리 (JEA) 끝점에서 사용자가 사용할 수 있는 명령 및 응용 프로그램을 정의 합니다. 역할 기능은 확장명이 인 파일에 의해 정의 됩니다 `.psrc` .

## 예제

### 예 1: 역할 기능 찾기

`Find-RoleCapability` 등록 된 각 리포지토리에서 역할 기능을 찾습니다. 특정 리포지토리를 검색 하려면 **리포지토리** 매개 변수를 사용 합니다.

```powershell
Find-RoleCapability
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
General-Lev2     1.0        JeaExamples    PSGallery
IIS-Lev1         1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### 예 2: 이름으로 역할 기능 찾기

`Find-RoleCapability` 이름으로 역할 기능을 찾습니다. 이름 배열을 구분 하려면 쉼표를 사용 합니다.

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### 예 3: 역할 기능의 모듈 찾기 및 저장

`Find-RoleCapability`Cmdlet은 역할 기능을 찾고 파이프라인에서 개체를 보냅니다.
`Save-Module` 역할 기능의 모듈을 파일 시스템에 저장 합니다. `Get-ChildItem` 모듈 디렉터리의 내용을 표시 합니다.

```
PS> Find-RoleCapability -Name General-Lev1 | Save-Module -Path C:\Test\Modules

PS> Get-ChildItem -Path C:\Test\Modules\JeaExamples\1.0\

    Directory: C:\Test\Modules\JeaExamples\1.0

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----          6/4/2019    16:37                RoleCapabilities
-a----          2/5/2019    18:46           1702 CreateRegisterPSSC.ps1
-a----          2/5/2019    18:46           7656 JeaExamples.psd1
-a----         10/1/2018    08:16            595 JeaExamples.psm1
```

`Find-RoleCapability`**Name** 매개 변수를 사용 하 여 **일반-Lev1** 역할 기능을 지정 합니다.
개체가 파이프라인으로 전송 됩니다. `Save-Module` 는 파일 시스템 위치에 **Path** 매개 변수를 사용 하 여 모듈을 저장 합니다. 모듈을 저장 한 후에는 `Get-ChildItem` 모듈의 **경로** 를 지정 하 고 **JeaExamples** 모듈의 디렉터리 내용을 표시 합니다.

### 예제 4: 역할 기능의 모듈 찾기 및 설치

`Find-RoleCapability` 모듈을 찾고 개체를 파이프라인으로 보냅니다. `Install-Module` 모듈을 설치 합니다. 설치 후에는를 사용 `Get-InstalledModule` 하 여 결과를 확인 합니다.

```
PS> Find-RoleCapability -Name General-Lev1 | Install-Module -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'JeaExamples'.
VERBOSE: InstallPackageLocal' - name='JeaExamples', version='1.0',
VERBOSE: Validating the 'JeaExamples' module contents
VERBOSE: Test-ModuleManifest successfully validated the module manifest file
VERBOSE: Module 'JeaExamples' was installed successfully to path

PS> Get-InstalledModule

Version    Name            Repository     Description
-------    ----            ----------     -----------
1.0        JeaExamples     PSGallery      Some example Jea roles for general server maintenance...
```

`Find-RoleCapability`**Name** 매개 변수를 사용 하 여 **일반-Lev1** 역할 기능을 지정 합니다.
개체가 파이프라인으로 전송 됩니다. `Install-Module`**Verbose** 매개 변수를 사용 하 여 설치 중에 상태 메시지를 표시 합니다. 설치가 완료 되 면 `Get-InstalledModule` 출력은 **JeaExamples** 모듈이 설치 되었음을 확인 합니다.

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

이 cmdlet은 모듈의 모든 버전을 가져옵니다. **Allversions)** 매개 변수는 모듈의 사용 가능한 버전을 각각 표시 합니다.

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

결과에 포함할 모듈의 최대 버전을 지정 합니다. **MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.

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

결과에 포함할 모듈의 최소 버전을 지정 합니다. **MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.

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

역할 기능을 검색할 모듈의 이름을 지정 합니다. 기본값은 모든 모듈입니다.

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

역할 기능의 이름을 지정 합니다. 기본값은 모든 역할 기능입니다. 리소스 이름 배열을 구분 하려면 쉼표를 사용 합니다.

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

역할 기능을 검색할 리포지토리를 지정 합니다. 저장소 이름 배열을 구분 하려면 쉼표를 사용 합니다.

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

### PSGetRoleCapabilityInfo

`Find-RoleCapability`Cmdlet은 **PSGetRoleCapabilityInfo** 개체를 반환 합니다.

## 참고

> [!IMPORTANT]
> 2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다. TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다. 다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.

## 관련 링크

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[New-PSRoleCapabilityFile](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[Save-Module](Save-Module.md)

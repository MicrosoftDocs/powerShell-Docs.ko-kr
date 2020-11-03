---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: d872f53c504874f69f1e39c506a72bfefa072aa6
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210137"
---
# Find-Command

## 개요
모듈에서 PowerShell 명령을 찾습니다.

## SYNTAX

### 모두

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## 설명

`Find-Command`Cmdlet은 cmdlet, 별칭, 함수, 워크플로 등의 PowerShell 명령을 찾습니다. `Find-Command` 등록 된 리포지토리의 모듈을 검색 합니다.

에서 찾은 각 명령에 대해 `Find-Command` **Psgetcommandinfo** 개체가 반환 됩니다. **Psgetcommandinfo** 개체를 파이프라인에서 cmdlet으로 보낼 수 있습니다 `Install-Module` .
`Install-Module` 명령이 포함 된 모듈을 설치 합니다.

## 예제

### 예 1: 지정 된 리포지토리에서 모든 명령 찾기

`Find-Command`Cmdlet은 모듈에 대해 등록 된 리포지토리를 검색 합니다.

```powershell
Find-Command -Repository PSGallery | Select-Object -First 10
```

```output
Name                                Version    ModuleName          Repository
----                                -------    ----------          ----------
Disable-AzureRmDataCollection       5.8.3      AzureRM.profile     PSGallery
Disable-AzureRmContextAutosave      5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmDataCollection        5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmContextAutosave       5.8.3      AzureRM.profile     PSGallery
Remove-AzureRmEnvironment           5.8.3      AzureRM.profile     PSGallery
Get-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Set-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Add-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Get-AzureRmSubscription             5.8.3      AzureRM.profile     PSGallery
Connect-AzureRmAccount              5.8.3      AzureRM.profile     PSGallery
```

`Find-Command`**리포지토리** 매개 변수를 사용 하 여 등록 된 리포지토리의 이름을 지정 합니다. 개체는 파이프라인으로 전송 됩니다. `Select-Object` 개체를 수신 하 고 **첫** 번째 매개 변수를 사용 하 여 처음 10 개의 결과를 표시 합니다.

### 예 2: 이름별로 명령 찾기

`Find-Command` 는 명령 이름을 사용 하 여 리포지토리에서 모듈을 찾을 수 있습니다. 명령 이름이 여러 **ModuleNames** 에 있을 수 있습니다.

```powershell
Find-Command -Repository PSGallery -Name Get-TargetResource
```

```Output
Name                  Version    ModuleName                      Repository
----                  -------    ----------                      ----------
Get-TargetResource    3.1.0.0    xPowerShellExecutionPolicy      PSGallery
Get-TargetResource    1.0.0      xInternetExplorerHomePage       PSGallery
Get-TargetResource    1.2.0.0    SystemLocaleDsc                 PSGallery
```

`Find-Command`**리포지토리** 매개 변수를 사용 하 여 **PSGallery** 를 검색 합니다. **Name** 매개 변수는 **test-targetresource** 명령을 지정 합니다.

### 예제 3: 이름을 기준으로 명령 찾기 및 모듈 설치

`Find-Command` 는 명령 및 모듈을 찾은 다음 개체를로 보낼 수 있습니다 `Install-Module` . 명령이 여러 모듈에 포함 된 경우 `Find-Command` Cmdlet **모듈-Name** 매개 변수를 사용 합니다.
그렇지 않으면 설치 하지 않으려는 모듈이 설치 될 수 있습니다.

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

`Find-Command`**Name** 매개 변수를 사용 하 여 **test-targetresource** 명령을 지정 합니다. **리포지토리** 매개 변수는 **PSGallery** 를 검색 합니다. **ModuleName** 매개 변수는 설치 하려는 모듈을 **Systemlocaledsc** 로 지정 합니다. 개체가 파이프라인으로 전송 되 `Install-Module` 고 모듈이 설치 됩니다. 설치가 완료 되 면를 사용 하 여 `Get-InstalledModule` 결과를 표시할 수 있습니다.

### 예제 4: 명령 찾기 및 해당 모듈 저장

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

`Find-Command`**Name** 및 **리포지토리** 매개 변수를 사용 하 여 **PSGallery** 리포지토리에서 명령 **호출** 을 검색 합니다. 개체는 파이프라인에서로 전송 됩니다 `Save-Module` . **Path** 매개 변수는 모듈을 저장할 위치를 결정 합니다. **Verbose** 는 선택적 매개 변수 이지만 PowerShell 콘솔에 상태 출력을 표시 합니다. 자세한 정보 출력은 문제 해결에 유용 합니다.

## PARAMETERS

### -AllowPrerelease

결과에서 시험판으로 표시 된 모듈을 포함 합니다.

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

이 cmdlet은 모듈의 모든 버전을 가져옵니다.

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

**PackageManagement** 공급자의 검색 구문에 따라 모듈을 찾습니다. 예를 들어 **ModuleName** 및 **Description** 속성 내에서 검색할 단어를 지정 합니다.

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

명령을 검색할 모듈의 이름을 지정 합니다. 기본값은 모든 모듈입니다.

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

리포지토리에서 검색할 명령 이름을 지정 합니다. 명령 이름 배열을 구분 하려면 쉼표를 사용 합니다.

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

명령을 검색할 리포지토리를 지정 합니다. 저장소 이름 배열을 구분 하려면 쉼표를 사용 합니다. 기본값은 모든 리포지토리입니다.

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

결과에 포함할 모듈의 버전을 지정 합니다.

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

### PSGetCommandInfo

`Find-Command`**Psgetcommandinfo** 개체를 출력 합니다.

## 참고

## 관련 링크

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[Save-Module](Save-Module.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Uninstall-Module](Uninstall-Module.md)

---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: 1b5bba73a55f92b515113c8b895dcb8af3c52eb6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215225"
---
# Save-Module

## 개요
모듈 및 해당 종속성을 로컬 컴퓨터에 저장 하지만 모듈을 설치 하지는 않습니다.

## SYNTAX

### NameAndPathParameterSet (기본값)

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense]  [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameAndLiteralPathParameterSet

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense]  [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObjectAndLiteralPathParameterSet

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### InputObjectAndPathParameterSet

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## 설명

`Save-Module`Cmdlet은 모듈 및 등록 된 리포지토리에서 모든 종속성을 다운로드 합니다.
`Save-Module` 최신 버전의 모듈을 다운로드 하 여 저장 합니다. 파일은 로컬 컴퓨터의 지정 된 경로에 저장 됩니다. 모듈이 설치 되지 않았지만 관리자가 콘텐츠를 검사할 수 있습니다. 그런 다음 저장 된 모듈을 `$env:PSModulePath` 오프 라인 컴퓨터의 적절 한 위치에 복사할 수 있습니다.

`Get-PSRepository` 로컬 컴퓨터의 등록 된 리포지토리를 표시 합니다. Cmdlet을 사용 `Find-Module` 하 여 등록 된 리포지토리를 검색할 수 있습니다.

## 예제

### 예제 1: 모듈 저장

이 예제에서는 모듈 및 해당 종속성이 로컬 컴퓨터에 저장 됩니다.

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery
Get-ChildItem -Path C:\Test\Modules
```

```Output
    Directory: C:\Test\Modules

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:31                PackageManagement
d-----         7/1/2019     13:31                PowerShellGet
```

`Save-Module`**Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다. **Path** 매개 변수는 다운로드 한 모듈을 저장할 위치를 지정 합니다. **리포지토리** 매개 변수는 등록 된 리포지토리 **PSGallery** 를 지정 합니다. 다운로드가 완료 되 면는 `Get-ChildItem` 파일이 저장 된 **경로** 내용을 표시 합니다.

### 예제 2: 모듈의 특정 버전 저장

이 예에서는 **MaximumVersion** 또는 **RequiredVersion** 과 같은 매개 변수를 사용 하 여 모듈 버전을 지정 하는 방법을 보여 줍니다.

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery -MaximumVersion 2.1.0
Get-ChildItem -Path C:\Test\Modules\PowerShellGet\
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:40                2.1.0
```

`Save-Module`**Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다. **Path** 매개 변수는 다운로드 한 모듈을 저장할 위치를 지정 합니다. **리포지토리** 매개 변수는 등록 된 리포지토리 **PSGallery** 를 지정 합니다. **MaximumVersion** 은 버전 **2.1.0** 을 다운로드 하 여 저장 하도록 지정 합니다. 다운로드가 완료 되 면는 `Get-ChildItem` 파일이 저장 된 **경로** 내용을 표시 합니다.

### 예제 3: 모듈의 특정 버전 찾기 및 저장

이 예제에서는 필수 모듈 버전이 리포지토리에서 검색 되 고 로컬 컴퓨터에 저장 됩니다.

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery -RequiredVersion 1.6.5 |
  Save-Module -Path C:\Test\Modules
Get-ChildItem -Path C:\Test\Modules\PowerShellGet
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     14:04                1.6.5
```

`Find-Module`**Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다. **리포지토리** 매개 변수는 등록 된 리포지토리 **PSGallery** 를 지정 합니다. **RequiredVersion** 버전 **1.6.5** 를 지정 합니다.

개체는 파이프라인에서로 전송 됩니다 `Save-Module` . **Path** 매개 변수는 다운로드 한 모듈을 저장할 위치를 지정 합니다. 다운로드가 완료 되 면는 `Get-ChildItem` 파일이 저장 된 **경로** 내용을 표시 합니다.

## PARAMETERS

### -AcceptLicense

패키지에 필요한 경우 사용권 계약에 자동으로 동의 합니다.

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

시험판으로 표시 된 모듈을 저장할 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

을 실행 하기 전에 확인 메시지를 표시 `Save-Module` 합니다.

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

모듈을 저장할 수 있는 권한을 가진 사용자 계정을 지정 합니다.

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

`Save-Module`사용자 확인을 요청 하지 않고 강제로 실행 합니다.

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

**PSRepositoryItemInfo** 개체를 허용 합니다. 예를 들어 `Find-Module` 변수를 출력 하 고 해당 변수를 **InputObject** 인수로 사용 합니다.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

하나 이상의 위치에 대한 경로를 지정합니다. **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 경로에 이스케이프 문자가 포함 되어 있으면 작은따옴표로 묶습니다. PowerShell은 작은 따옴표로 묶인 문자를 이스케이프 시퀀스로 해석 하지 않습니다.

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaximumVersion

저장할 모듈의 최대 또는 최신 버전을 지정 합니다. **MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

저장할 단일 모듈의 최소 버전을 지정 합니다. 여러 모듈을 설치 하려는 경우에는이 매개 변수를 추가할 수 없습니다. **MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

저장할 모듈의 이름 배열을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

저장 된 모듈을 저장할 로컬 컴퓨터의 위치를 지정 합니다. 와일드 카드 문자를 허용 합니다.

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
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

을 실행 하 여 등록 된 리포지토리의 이름을 지정 합니다 `Register-PSRepository` . `Get-PSRepository`등록 된 리포지토리를 표시 하는 데 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

저장할 모듈의 정확한 버전 번호를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Save-Module` . Cmdlet이 실행 되지 않습니다.

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

## 출력

## 참고

## 관련 링크

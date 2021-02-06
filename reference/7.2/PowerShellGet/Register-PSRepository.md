---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/register-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSRepository
ms.openlocfilehash: 179e672a099cfb92275795a0dc6129581a0e0299
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99603075"
---
# Register-PSRepository

## 개요
PowerShell 리포지토리를 등록 합니다.

## SYNTAX

### NameParameterSet (기본값)

```
Register-PSRepository [-Name] <String> [-SourceLocation] <Uri> [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

### PSGalleryParameterSet

```
Register-PSRepository [-Default] [-InstallationPolicy <String>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [<CommonParameters>]
```

## 설명

`Register-PSRepository`Cmdlet은 PowerShell 모듈에 대 한 기본 리포지토리를 등록 합니다. 리포지토리를 등록 한 후에는, 및 cmdlet에서 리포지토리를 참조할 수 있습니다 `Find-Module` `Install-Module` `Publish-Module` . 등록 된 리포지토리는 및의 기본 리포지토리가 `Find-Module` 됩니다 `Install-Module` .

등록된 리포지토리는 사용자별 리포지토리입니다. 시스템 차원의 컨텍스트에는 등록되지 않습니다.

등록 된 각 리포지토리는 **PackageManagementProvider** 매개 변수로 지정 된 oneget 패키지 공급자와 연결 됩니다. 각 OneGet 공급자는 특정 리포지토리 형식과 상호 작용 하도록 설계 되었습니다. 예를 들어 nuget 공급자는 NuGet 기반 리포지토리와 상호 작용 하도록 설계 되었습니다. 등록 하는 동안 OneGet 공급자를 지정 하지 않으면 PowerShellGet에서 지정 된 원본 위치를 처리할 수 있는 OneGet 공급자를 찾으려고 시도 합니다.

## 예제

### 예제 1: 리포지토리 등록

```powershell
$parameters = @{
  Name = "myNuGetSource"
  SourceLocation = "https://www.myget.org/F/powershellgetdemo/api/v2"
  PublishLocation = "https://www.myget.org/F/powershellgetdemo/api/v2/Packages"
  InstallationPolicy = 'Trusted'
}
Register-PSRepository @parameters
Get-PSRepository
```

```Output
Name                SourceLocation          OneGetProvider       InstallationPolicy
----                --------------          --------------       ------------------
PSGallery           http://go.micro...      NuGet                Untrusted
myNuGetSource       https://myget.c...      NuGet                Trusted
```

첫 번째 명령은 `https://www.myget.org/F/powershellgetdemo/` 현재 사용자에 대 한 리포지토리로 등록 합니다. MyNuGetSource를 등록 한 후 모듈을 검색, 설치 및 게시할 때이를 명시적으로 참조할 수 있습니다. **PackageManagementProvider** 매개 변수가 지정 되지 않았기 때문에 리포지토리는 oneget 패키지 공급자와 명시적으로 연결 되지 않으므로 PowerShellGet에서 사용 가능한 패키지 공급자를 폴링하고 NuGet 공급자와 연결 합니다.

두 번째 명령은 등록 된 리포지토리를 가져오고 결과를 표시 합니다.

## PARAMETERS

### -Credential

리포지토리를 등록할 수 있는 권한이 있는 계정의 자격 증명을 지정 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Default

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PSGalleryParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstallationPolicy

설치 정책을 지정 합니다. 유효한 값은 신뢰할 수 있는 신뢰할 수 있는 값입니다. 기본값은 신뢰할 수 없습니다.

리포지토리의 설치 정책은 해당 리포지토리에서 설치할 때 PowerShell 동작을 지정 합니다. 신뢰할 수 없는 리포지토리의 모듈을 설치 하는 경우 사용자에 게 확인 메시지를 표시 합니다.

Cmdlet을 사용 하 여 **InstallationPolicy** 를 설정할 수 있습니다 `Set-PSRepository` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Trusted, Untrusted

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

등록할 리포지토리의 이름을 지정 합니다. 이 이름을 사용 하 여 및와 같은 cmdlet에 리포지토리를 지정할 수 있습니다 `Find-Module` `Install-Module` .

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

OneGet 패키지 공급자를 지정 합니다. 이 매개 변수에 대 한 값을 지정 하지 않으면 PowerShellGet은 사용 가능한 패키지 공급자를 폴링하고이 리포지토리를 리포지토리를 처리할 수 있음을 나타내는 첫 번째 패키지 공급자와 연결 합니다.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
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

### -PublishLocation

게시 위치의 URI를 지정 합니다. 예를 들어 NuGet 기반 리포지토리의 경우 게시 위치는와 유사 `https://someNuGetUrl.com/api/v2/Packages` 합니다.

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
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
Type: System.Uri
Parameter Sets: NameParameterSet
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
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -로의

이 리포지토리에서 모듈을 검색 하 고 설치 하기 위한 URI를 지정 합니다. URI는 NuGet 서버 피드 (가장 일반적인 상황), HTTP, HTTPS, FTP 또는 파일 위치가 될 수 있습니다.

예를 들어 NuGet 기반 리포지토리의 경우 원본 위치는와 유사 `https://someNuGetUrl.com/api/v2` 합니다.

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.object. PSCredential

### System.Uri

## 출력

### System.Object

## 참고

> [!IMPORTANT]
> 2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다. TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다. 다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.

## 관련 링크

[Get-PSRepository](Get-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Unregister-PSRepository](Unregister-PSRepository.md)

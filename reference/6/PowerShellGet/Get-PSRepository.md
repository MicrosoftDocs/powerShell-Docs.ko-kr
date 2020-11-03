---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: b4d786cdac183917428b0846ad3c88d41b083ac5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215986"
---
# Get-PSRepository

## 개요
PowerShell 리포지토리를 가져옵니다.

## SYNTAX

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## 설명

**Set-psrepository** cmdlet은 현재 사용자에 대해 등록 된 PowerShell 모듈 리포지토리를 가져옵니다.

## 예제

### 예제 1: 모든 모듈 리포지토리 가져오기

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

이 명령은 현재 사용자에 대해 등록 된 모든 모듈 리포지토리를 가져옵니다.

### 예 2: 이름별로 모듈 리포지토리 가져오기

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

이 명령은 이름에 NuGet이 포함 된 모든 모듈 리포지토리를 가져옵니다.

### 예 3: 모듈 리포지토리 가져오기 및 출력 형식 지정

```
PS C:\> Get-PSRepository -Name "Local01" | Format-List * -Force
Name                      : local01
SourceLocation            : http://manikb-dev:8765/api/v2/
Trusted                   : True
Registered                : True
InstallationPolicy        : Trusted
PackageManagementProvider : NuGet
PublishLocation           : http://pattif-dev:8765/api/v2/package/
ScriptSourceLocation      : http://pattif-dev:8765/api/v2/artifacts/psscript
ScriptPublishLocation     : http://pattif-dev:8765/api/v2/package/
ProviderOptions           : {}
```

이 명령은 Local01 이라는 리포지토리를 가져온 다음 파이프라인 연산자를 사용 하 여 해당 개체를 Format-List cmdlet에 전달 합니다.

## PARAMETERS

### -Name

가져올 리포지토리의 이름을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String[]

## 출력

### System.Object

## 참고

## 관련 링크

[Register-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Unregister-PSRepository](Unregister-PSRepository.md)

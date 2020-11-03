---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/test-scriptfileinfo?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ScriptFileInfo
ms.openlocfilehash: d7e70c9bff9e5c33edd1fd8eeb9d8fb7e15605da
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215185"
---
# Test-ScriptFileInfo

## 개요
스크립트에 대 한 주석 블록의 유효성을 검사 합니다.

## SYNTAX

### PathParameterSet (기본값)

```
Test-ScriptFileInfo [-Path] <String> [<CommonParameters>]
```

### LiteralPathParameterSet

```
Test-ScriptFileInfo -LiteralPath <String> [<CommonParameters>]
```

## 설명

**New-scriptfileinfo** cmdlet은 Publish-Script cmdlet을 사용 하 여 게시 될 스크립트의 시작 부분에 있는 주석 블록의 유효성을 검사 합니다.
주석 블록에 오류가 있는 경우이 cmdlet은 오류가 발생 한 위치 또는 수정 방법에 대 한 정보를 반환 합니다.

## 예제

### 예제 1: 스크립트 파일 테스트

```
PS C:\> Test-ScriptFileInfo -Path "C:\temp\temp_scripts\New-ScriptFile.ps1"
Version    Name                      Author               Description
-------    ----                      ------               -----------
1.0        New-ScriptFile            pattif               my new script file test
```

이 명령은 New-ScriptFile.ps1 스크립트 파일을 테스트 하 고 결과를 표시 합니다.
스크립트 파일에 유효한 메타 데이터가 포함 되어 있습니다.

### 예제 2: 모든 메타 데이터 속성에 대 한 값이 있는 스크립트 파일 테스트

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Test-Runbook.ps1" | Format-List *
Name                       : Test-Runbook
Path                       : D:\code\Test-Runbook.ps1
ScriptBase                 : D:\code
ReleaseNotes               : {contoso script now supports following features, Feature 1, Feature 2, Feature 3...}
Version                    : 1.0
Guid                       : eb246b19-17da-4392-8c89-7c280f69ad0e
Author                     : pattif
CompanyName                : Microsoft Corporation
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
Tags                       : {Tag1, Tag2, Tag3}
LicenseUri                 : https://contoso.com/License
ProjectUri                 : https://contoso.com/
IconUri                    : https://contoso.com/MyScriptIcon
ExternalModuleDependencies : ExternalModule1
RequiredScripts            : {Start-WFContosoServer, Stop-ContosoServerScript}
ExternalScriptDependencies : Stop-ContosoServerScript
Description                : Contoso Script example
RequiredModules            : {RequiredModule1, @{ ModuleName = 'RequiredModule2'; ModuleVersion = '1.0' }, @{ ModuleName = 'RequiredModule3'; RequiredVersion = '2.0' }, ExternalModule1}
ExportedCommands           : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-Workflow...}
ExportedFunctions          : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-AdvPSCmdlet}
ExportedWorkflows          : My-Workflow
```

이 명령은 Test-Runbook.ps1 스크립트 파일을 테스트 하 고 파이프라인 연산자를 사용 하 여 결과를 Format-List cmdlet에 전달 하 여 결과의 서식을 지정 합니다.

### 예제 3: 메타 데이터가 없는 스크립트 파일 테스트

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Hello-World.ps1"
Test-ScriptFileInfo : Script 'D:\code\Hello-World.ps1' is missing required metadata properties. Verify that the script file has Version, Description
and Author properties. You can use the Update-ScriptFileInfo or New-ScriptFileInfo cmdlet to add or update the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo D:\code\Hello-World.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidArgument: (D:\code\Hello-World.ps1:String) [Test-ScriptFileInfo], ArgumentException

+ FullyQualifiedErrorId : MissingRequiredPSScriptInfoProperties,Test-ScriptFile
```

이 명령은 연결 된 메타 데이터가 없는 Hello-World.ps1 스크립트 파일을 테스트 합니다.

## PARAMETERS

### -LiteralPath

하나 이상의 위치에 대한 경로를 지정합니다.
*Path* 매개 변수와 달리 *LiteralPath* 매개 변수 값은 입력 한 대로 사용 됩니다.
어떠한 문자도 와일드카드로 해석되지 않습니다.
경로에 이스케이프 문자가 포함 되어 있으면 작은따옴표로 묶습니다.
작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

하나 이상의 위치에 대한 경로를 지정합니다.
와일드카드가 지원됩니다.
기본 위치는 현재 디렉터리(.)입니다.

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

## 참고

## 관련 링크

[New-ScriptFileInfo](New-ScriptFileInfo.md)

[Publish-Script](Publish-Script.md)

[Update-ScriptFileInfo](Update-ScriptFileInfo.md)

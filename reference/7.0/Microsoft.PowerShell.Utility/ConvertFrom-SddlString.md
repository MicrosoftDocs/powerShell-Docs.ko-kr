---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: 9c864ec46af9584f36eef3f3ba879cf314e0ca1c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347315"
---
# ConvertFrom-SddlString

## 개요
SDDL 문자열을 사용자 지정 개체로 변환 합니다.

## SYNTAX

### 모두

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <AccessRightTypeNames>] [<CommonParameters>]
```

## 설명

`ConvertFrom-SddlString`Cmdlet은 Owner, Group, DiscretionaryAcl, SystemAcl 및 RawDescriptor 속성을 사용 하 여 보안 설명자 정의 언어 문자열을 사용자 지정 **PSCustomObject** 개체로 변환 합니다.

Owner, Group, DiscretionaryAcl 및 SystemAcl 속성은 SDDL 문자열에 지정 된 액세스 권한의 읽을 수 있는 텍스트 표현을 포함 합니다.

이 cmdlet은 PowerShell 5.0에서 도입 되었습니다.

## 예제

### 예제 1: 파일 시스템 액세스 권한 SDDL을 PSCustomObject로 변환

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` C:\Windows 폴더에 대 한 보안 설명자를 가져온 다음 변수에 저장 합니다.

두 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SddlString` 보안 설명자를 나타내는 개체의 sddl 속성에 포함 된 sddl 문자열의 텍스트 표현을 가져옵니다.

### 예제 2: 레지스트리 액세스 권한 SDDL을 PSCustomObject로 변환

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` HKLM: \ SOFTWARE\Microsoft\ 키에 대 한 보안 설명자를 가져온 다음 변수에 저장 합니다.

두 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SddlString` 보안 설명자를 나타내는 개체의 sddl 속성에 포함 된 sddl 문자열의 텍스트 표현을 가져옵니다.

매개 변수를 사용 하 여 `-Type` SDDL 문자열이 레지스트리 보안 설명자를 나타내도록 지정 합니다.

### 예제 3: 매개 변수를 사용 하거나 사용 하지 않고 ConvertFrom-SddlString를 사용 하 여 레지스트리 액세스 권한 SDDL을 PSCustomObject로 변환 `-Type`

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` HKLM: \ SOFTWARE\Microsoft\ 키에 대 한 보안 설명자를 가져온 다음 변수에 저장 합니다.

두 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SddlString` 보안 설명자를 나타내는 개체의 sddl 속성에 포함 된 sddl 문자열의 텍스트 표현을 가져옵니다.

`-Type`매개 변수를 사용 하지 않으므로 표시 되는 액세스 권한은 파일 시스템용입니다.

세 번째 명령은 `ConvertFrom-SddlString` 매개 변수와 함께 cmdlet을 사용 `-Type` 하므로 레지스트리에 대 한 액세스 권한이 반환 됩니다.

## PARAMETERS

### -Sddl

SDDL 구문에서 보안 설명자를 나타내는 문자열을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Type

SDDL 문자열이 나타내는 권한 유형을 지정 합니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- FileSystemRights
- RegistryRights
- ActiveDirectoryRights
- MutexRights
- SemaphoreRights
- CryptoKeyRights
- EventWaitHandleRights

기본적으로 cmdlet은 파일 시스템 권한을 사용 합니다.

CryptoKeyRights 및 ActiveDirectoryRights는 PowerShell Core에서 지원 되지 않습니다.

```yaml
Type: Microsoft.PowerShell.Commands.ConvertFromSddlStringCommand+AccessRightTypeNames
Parameter Sets: (All)
Aliases:
Accepted values: FileSystemRights, RegistryRights, ActiveDirectoryRights, MutexRights, SemaphoreRights, CryptoKeyRights, EventWaitHandleRights

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

SDDL 문자열을로 파이프 할 수 있습니다 `ConvertFrom-SddlString` .

## 출력

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

## 관련 링크

[보안 설명자 정의 언어](/windows/win32/secauthz/security-descriptor-definition-language)

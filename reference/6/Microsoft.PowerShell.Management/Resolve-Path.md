---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: 7e88e873c5c6aa0733869cdaaf1fba583468261d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212306"
---
# Resolve-Path

## 개요
경로에서 와일드카드 문자를 확인하고 경로 내용을 표시합니다.

## SYNTAX

### Path (기본값)

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

### LiteralPath

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

## 설명

`Resolve-Path`Cmdlet은 지정 된 위치에서 와일드 카드 패턴과 일치 하는 항목과 컨테이너를 표시 합니다. 일치 항목에는 파일, 폴더, 레지스트리 키 또는 PSDrive 공급자에서 액세스할 수 있는 기타 개체가 포함 될 수 있습니다.

## 예제

### 예 1: 홈 폴더 경로를 확인 합니다.

물결표 문자 (~)는 현재 사용자의 홈 폴더에 대 한 약식 표기법입니다. 이 예에서는 정규화 `Resolve-Path` 된 경로 값을 반환 하는 방법을 보여 줍니다.

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### 예 2: Windows 폴더의 경로 확인

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

이 명령은 C: 드라이브의 루트에서 실행 하면 C: 드라이브의 Windows 폴더 경로를 반환 합니다.

### 예제 3: Windows 폴더의 모든 경로 가져오기

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

이 명령은 C:\Windows 폴더의 모든 폴더를 반환 합니다. 이 명령은 파이프라인 연산자 (|)를 사용 하 여 경로 문자열을로 보냅니다 `Resolve-Path` .

### 예제 4: UNC 경로 확인

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

이 명령은 UNC(범용 명명 규칙) 경로를 확인하며 경로의 공유를 반환합니다.

### 예 5: 상대 경로 가져오기

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

이 명령은 C: 드라이브 루트에서 디렉터리에 대한 상대 경로를 반환합니다.

### 예제 6: 대괄호가 포함 된 경로 확인

이 예제에서는 **LiteralPath** 매개 변수를 사용 하 여 테스트 \[ xml 하위 폴더의 경로를 확인 합니다 \] .
**LiteralPath** 를 사용 하면 대괄호가 정규식이 아닌 일반 문자로 처리 됩니다.

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## PARAMETERS

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나 **PSCredential** 개체를 전달 합니다. Cmdlet을 사용 하 여 **PSCredential** 개체를 만들 수 있습니다 `Get-Credential` . 사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.

이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.

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

### -LiteralPath

확인할 경로를 지정합니다. **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드 문자로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

확인할 PowerShell 경로를 지정 합니다. 이 매개 변수는 필수적 요소입니다. 경로 문자열을로 파이프 할 수도 있습니다 `Resolve-Path` . 와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -상대

이 cmdlet이 상대 경로를 반환 함을 나타냅니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.

## 출력

### System.web. PathInfo, System.string

**Pathinfo** 개체를 반환 합니다. **상대** 매개 변수를 지정 하는 경우 확인 된 경로에 대 한 문자열 값을 반환 합니다.

## 참고

`*-Path`Cmdlet은 파일 시스템, 레지스트리 및 인증서 공급자와 함께 작동 합니다.

`Resolve-Path` 는 모든 공급자에서 사용할 수 있도록 설계 되었습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 [about_providers](../microsoft.powershell.core/about/about_providers.md)를 참조 하세요.

`Resolve-Path` 기존 경로만 확인 합니다. 아직 존재 하지 않는 위치를 확인 하는 데 사용할 수 없습니다.

## 관련 링크

[Convert-Path](Convert-Path.md)

[Join-Path](Join-Path.md)

[Split-Path](Split-Path.md)

[Test-Path](Test-Path.md)

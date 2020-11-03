---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: fa66e42e182a7dea830ab30373682e4d1e6601e3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210626"
---
# Convert-Path

## 개요
PowerShell 경로에서 PowerShell 공급자 경로로 경로를 변환 합니다.

## SYNTAX

### Path (기본값)

```
Convert-Path [-Path] <String[]> [<CommonParameters>]
```

### LiteralPath

```
Convert-Path -LiteralPath <String[]> [<CommonParameters>]
```

## 설명

`Convert-Path`Cmdlet은 powershell 경로에서 powershell 공급자 경로로 경로를 변환 합니다.

## 예제

### 예제 1: 작업 디렉터리를 표준 파일 시스템 경로로 변환

이 예에서는 점 ()으로 표시 되는 현재 작업 디렉터리를 `.` 표준 파일 시스템 경로로 변환 합니다.

```
PS C:\> Convert-Path .
C:\
```

### 예제 2: 공급자 경로를 표준 레지스트리 경로로 변환

이 예에서는 PowerShell 공급자 경로를 표준 레지스트리 경로로 변환 합니다.

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### 예제 3: 경로를 문자열로 변환

이 예에서는 FileSystem 공급자 인 현재 공급자의 홈 디렉터리에 대 한 경로를 문자열로 변환 합니다.

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## PARAMETERS

### -LiteralPath

변환할 경로를 문자열 배열로 지정 합니다. **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

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

변환할 PowerShell 경로를 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

리터럴 경로를 제외 하 고이 cmdlet에 경로를 파이프 할 수 있습니다.

## 출력

### System.String

이 cmdlet은 변환 된 경로를 포함 하는 문자열을 반환 합니다.

## 참고

경로 명사를 포함 하는 cmdlet은 경로 이름을 조작 하 고 모든 PowerShell 공급자가 해석할 수 있는 간결한 형식으로 이름을 반환 합니다. 이 cmdlet은 경로 이름의 전체 또는 일부를 특정 형식으로 표시하려는 프로그램 및 스크립트에 사용하도록 디자인되었습니다. 이를 사용 하 여 다른 **이름** , **Normpath** , **Realpath** , **Join** 또는 기타 경로 조작자를 사용 하는 것과 같습니다.

파일 시스템, 레지스트리 및 인증서 공급자를 포함하여 여러 공급자와 함께 Path cmdlet을 사용할 수 있습니다.

이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

`Convert-Path` 기존 경로만 변환 합니다. 아직 존재 하지 않는 위치를 변환 하는 데 사용할 수 없습니다.

## 관련 링크

[Join-Path](Join-Path.md)

[Resolve-Path](Resolve-Path.md)

[Split-Path](Split-Path.md)

[Test-Path](Test-Path.md)

[Get-PSProvider](Get-PSProvider.md)

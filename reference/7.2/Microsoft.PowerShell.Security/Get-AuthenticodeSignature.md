---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: de039877825a15f0ddf48ba7095b9cce710ec22b
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685563"
---
# Get-AuthenticodeSignature

## 개요
파일의 Authenticode 서명에 대 한 정보를 가져옵니다.

## SYNTAX

### ByPath (기본값)

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### ByLiteralPath

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### ByContent

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## 설명

`Get-AuthenticodeSignature`Cmdlet은 파일 또는 파일 콘텐츠의 Authenticode 서명에 대 한 정보를 바이트 배열로 가져옵니다.
서명 된 서명 및 Windows 카탈로그 파일이 모두 서명 된 경우 Windows 카탈로그 서명이 사용 됩니다.
파일이 서명되지 않은 경우 정보는 검색되지만 필드가 비어 있게 됩니다.

## 예제

### 예 1: 파일에 대 한 Authenticode 서명 가져오기

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

이 명령은 NewScript.ps1 파일에서 Authenticode 서명 정보를 가져옵니다. **FilePath** 매개 변수를 사용 하 여 파일을 지정 합니다.

### 예 2: 여러 파일에 대 한 Authenticode 서명 가져오기

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

이 명령은 명령줄에 나열 된 4 개 파일의 Authenticode 서명에 대 한 정보를 가져옵니다. 이 예제에서 옵션 인 **FilePath** 매개 변수의 이름은 생략 됩니다.

### 예 3: 여러 파일에 대해 유효한 Authenticode 서명만 가져오기

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

이 명령은 `$PSHOME` 디렉터리에서 유효한 Authenticode 서명이 있는 모든 파일을 나열 합니다. `$PSHOME`자동 변수는 PowerShell 설치 디렉터리에 대 한 경로를 포함 합니다.

이 명령은 cmdlet을 사용 하 여 `Get-ChildItem` 디렉터리의 파일을 `$PSHOME` 가져옵니다. 패턴을 사용 *합니다.* 디렉터리를 제외 하려면 (파일 이름에 점이 없는 파일도 제외)

이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 파일을 `$PSHOME` cmdlet으로 보냅니다 `ForEach-Object` `Get-AuthenticodeSignature` .이 cmdlet은 각 파일에 대해를 호출 합니다.

명령의 결과는 `Get-AuthenticodeSignature` `Where-Object` 유효한 상태로 서명 개체만 선택 하는 명령으로 전송 됩니다.

### 예제 4: 바이트 배열로 지정 된 파일 콘텐츠에 대 한 Authenticode 서명 가져오기

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

이 명령은 파일의 콘텐츠에 대 한 Authenticode 서명에 대 한 정보를 가져옵니다. 이 예에서는 파일 확장명이 파일의 내용과 함께 지정 됩니다.

## PARAMETERS

### -콘텐츠

Authenticode 서명이 검색 되는 바이트 배열인 파일의 콘텐츠입니다. 이 매개 변수는 **SourcePathOrExtension** 매개 변수와 함께 사용 해야 합니다. 파일의 내용은 유니코드 (UTF-16LE) 형식 이어야 합니다.

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FilePath

검사할 파일의 경로를 지정 합니다. 와일드카드를 사용할 수 있지만 단일 파일로 연결되어야 합니다. 이 매개 변수의 값을 지정 하는 경우 명령줄에서 **FilePath** 를 입력할 필요가 없습니다.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -LiteralPath

검사할 파일 경로를 지정합니다. **FilePath** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 경로에 이스케이프 문자가 포함 되어 있으면 작은따옴표로 묶습니다. 작은따옴표는 모든 문자를 이스케이프 문자로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourcePathOrExtension

Authenticode 서명이 검색 되는 콘텐츠의 파일 또는 파일 형식에 대 한 경로입니다. 이 매개 변수는 파일 콘텐츠가 바이트 배열로 전달 되는 **콘텐츠와** 함께 사용 됩니다.

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

파일 경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Get-AuthenticodeSignature` .

## 출력

### System.object..

`Get-AuthenticodeSignature` 가져오는 각 시그니처에 대 한 서명 개체를 반환 합니다.

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

PowerShell의 Authenticode 서명에 대 한 자세한 내용은 [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)를 참조 하세요.

## 관련 링크

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)

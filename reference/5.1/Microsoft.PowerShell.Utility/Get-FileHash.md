---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: ce0ecdfc216680f255718b1a03f78276364b1c50
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213985"
---
# Get-FileHash

## 개요
지정한 해시 알고리즘을 사용하여 파일에 대한 해시 값을 계산합니다.

## SYNTAX

### Path (기본값)

```
Get-FileHash [-Path] <String[]> [-Algorithm <String>] [<CommonParameters>]
```

### LiteralPath

```
Get-FileHash -LiteralPath <String[]> [-Algorithm <String>] [<CommonParameters>]
```

### STREAM

```
Get-FileHash -InputStream <Stream> [-Algorithm <String>] [<CommonParameters>]
```

## 설명

`Get-FileHash`Cmdlet은 지정 된 해시 알고리즘을 사용 하 여 파일에 대 한 해시 값을 계산 합니다.
해시 값은 파일 내용에 해당하는 고유한 값입니다. 파일 이름, 확장명 또는 기타 지정으로 파일 내용을 식별하는 대신 해시는 파일 내용에 고유한 값을 할당합니다. 파일 내용과 해시 값을 변경하지 않고 파일 이름과 확장명을 변경할 수 있습니다. 마찬가지로 이름 또는 확장명을 변경 하지 않고 파일의 콘텐츠를 변경할 수 있습니다. 그러나 파일 내용에서 한 문자라도 변경하면 파일의 해시 값이 변경됩니다.

해시 값은 파일 내용이 변경되지 않았음을 확인하는 암호화된 보안 방법을 제공합니다. MD5 및 SHA1을 비롯 한 일부 해시 알고리즘은 더 이상 공격 으로부터 안전 하 게 고려 되지 않지만, 보안 해시 알고리즘의 목표는 실수로 또는 악의적 또는 무단 시도로 파일의 콘텐츠를 변경할 수 없도록 렌더링 하 고 동일한 해시 값을 유지 하는 것입니다. 해시 값을 사용하여 두 개의 파일 내용이 같은지 확인할 수도 있습니다. 두 파일의 해시 값이 같으면 파일 내용도 같습니다.

기본적으로 cmdlet은 `Get-FileHash` SHA256 알고리즘을 사용 하지만 대상 운영 체제에서 지 원하는 모든 해시 알고리즘을 사용할 수 있습니다.

## 예제

### 예제 1: 파일에 대 한 해시 값 계산

이 예에서는 cmdlet을 사용 하 여 `Get-FileHash` 파일에 대 한 해시 값을 계산 합니다 `Powershell.exe` .
사용된 해시 알고리즘은 기본값인 SHA256입니다. 출력을 cmdlet으로 파이프 하 여 `Format-List` 출력을 목록 형식으로 지정 합니다.

```powershell
Get-FileHash $PSHOME\powershell.exe | Format-List
```

```Output
Algorithm : SHA256
Hash      : 908B64B1971A979C7E3E8CE4621945CBA84854CB98D76367B791A6E22B5F6D53
Path      : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
```

### 예제 2: ISO 파일에 대 한 해시 값 계산

이 예제에서는 `Get-FileHash` cmdlet 및 **SHA384** 알고리즘을 사용 하 여 관리자가 인터넷에서 다운로드 한 ISO 파일의 해시 값을 계산 합니다. 출력을 cmdlet으로 파이프 하 여 `Format-List` 출력을 목록 형식으로 지정 합니다.

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### 예제 3: 스트림의 해시 값 계산

이 예에서는 [Powershell 릴리스 페이지](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4)에서 패키지를 다운로드 하는 데 **시스템 .net. WebClient** 를 사용 합니다. 또한 릴리스 페이지는 각 패키지 파일의 SHA256 해시를 문서화 합니다. 게시 된 해시 값을 계산 하는 해시 값과 비교할 수 있습니다 `Get-FileHash` .

```powershell
$wc = [System.Net.WebClient]::new()
$pkgurl = 'https://github.com/PowerShell/PowerShell/releases/download/v6.2.4/powershell_6.2.4-1.debian.9_amd64.deb'
$publishedHash = '8E28E54D601F0751922DE24632C1E716B4684876255CF82304A9B19E89A9CCAC'
$FileHash = Get-FileHash -InputStream ($wc.OpenRead($pkgurl))
$FileHash.Hash -eq $publishedHash
```

```Output
True
```

### 예제 4: 문자열의 해시 계산

PowerShell은 문자열의 해시를 계산 하는 cmdlet을 제공 하지 않습니다. 그러나 문자열을 스트림에 쓰고의 **InputStream** 매개 변수를 사용 `Get-FileHash` 하 여 해시 값을 가져올 수 있습니다.

```powershell
$stringAsStream = [System.IO.MemoryStream]::new()
$writer = [System.IO.StreamWriter]::new($stringAsStream)
$writer.write("Hello world")
$writer.Flush()
$stringAsStream.Position = 0
Get-FileHash -InputStream $stringAsStream | Select-Object Hash
```

```Output
Hash
----
64EC88CA00B268E5BA1A35678A1B5316D212F4F366B2477232534A8AECA37F3C
```

## PARAMETERS

### -알고리즘

지정 된 파일 또는 스트림의 내용에 대 한 해시 값을 계산 하는 데 사용할 암호화 해시 함수를 지정 합니다. 암호화 해시 함수에는 동일한 해시 값을 가진 두 개의 다른 파일을 찾을 수 없는 속성이 있습니다. 해시 함수는 디지털 서명과 함께 데이터 무결성에 주로 사용됩니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- SHA1
- SHA256
- SHA384
- SHA512
- MACTripleDES
- MD5
- RIPEMD160

값을 지정하지 않거나 매개 변수를 생략할 경우 기본값은 SHA256입니다.

보안상, 더 이상 안전하지 않은 MD5 및 SHA1은 간단한 변경 유효성 검사에만 사용해야 하며 공격이나 조작으로부터 보호해야 하는 파일의 해시 값을 생성하는 데 사용하면 안 됩니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MACTripleDES, MD5, RIPEMD160

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputStream

입력 스트림을 지정 합니다.

```yaml
Type: System.IO.Stream
Parameter Sets: Stream
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

파일의 경로를 지정합니다. **Path** 매개 변수와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드 문자로 해석되지 않습니다. 경로에 이스케이프 문자가 포함되어 있으면 경로를 작은따옴표로 묶습니다. 작은따옴표는 PowerShell에서 문자를 이스케이프 시퀀스로 해석 하지 않도록 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

하나 이상의 파일에 대 한 경로를 배열로 지정 합니다. 와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

`Get-FileHash`하나 이상의 파일에 대 한 경로를 포함 하는 cmdlet에 문자열을 파이프 할 수 있습니다.

## 출력

### Microsoft. Powershell. FileHash

`Get-FileHash` 지정 된 파일에 대 한 경로, 계산 된 해시의 값 및 해시를 계산 하는 데 사용 되는 알고리즘을 나타내는 개체를 반환 합니다.

## 참고

## 관련 링크

[Format-List](Format-List.md)

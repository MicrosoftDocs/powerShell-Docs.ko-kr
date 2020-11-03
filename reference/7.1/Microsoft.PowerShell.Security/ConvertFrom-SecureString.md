---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 07/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: ed9ef1102c1e34670b3cb5664a227f86124812a0
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "93219001"
---
# ConvertFrom-SecureString

## 개요
보안 문자열을 암호화 된 표준 문자열로 변환 합니다.

## SYNTAX

### Secure (기본값)

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### AsPlainText

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-AsPlainText] [<CommonParameters>]
```

### 열기

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## 설명

**Convertfrom-csv** cmdlet은 보안 문자열 ( **system.web** )을 암호화 된 표준 문자열 ( **system.string** )로 변환 합니다. 보안 문자열과 달리 암호화된 기본 문자열은 나중에 사용할 수 있도록 파일에 저장할 수 있습니다. 암호화 된 표준 문자열은 cmdlet을 사용 하 여 보안 문자열 형식으로 다시 변환할 수 있습니다 `ConvertTo-SecureString` .

**Key** 또는 **SecureKey** 매개 변수를 사용하여 암호화 키를 지정한 경우 AES(Advanced Encryption) 암호화 알고리즘이 사용됩니다. 지정한 키 길이는 128, 192 및 256비트여야 합니다. AES 암호화 알고리즘에서 이러한 길이를 지원하기 때문입니다. 지정된 키가 없을 경우 Windows Data Protection API(DPAPI)가 기본 문자열 표현을 암호화하는 데 사용됩니다.

> [!NOTE]
> [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks)마다 SecureString의 콘텐츠는 비 Windows 시스템에서 암호화 되지 않습니다.

## 예제

### 예제 1: 보안 문자열 만들기

```powershell
$SecureString = Read-Host -AsSecureString
```

이 명령은 명령 프롬프트에 입력된 문자에서 보안 문자열을 만듭니다. 명령을 입력한 다음 보안 문자열로 저장할 문자열을 입력하세요. `*`입력 하는 각 문자를 나타내는 별표 ()가 표시 됩니다.

### 예제 2: 보안 문자열을 암호화 된 표준 문자열로 변환

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

이 명령은 변수의 보안 문자열 `$SecureString` 을 암호화 된 표준 문자열로 변환 합니다. 결과로 생성 되는 암호화 된 표준 문자열은 `$StandardString` 변수에 저장 됩니다.

### 예제 3:192 비트 키를 사용 하 여 보안 문자열을 암호화 된 표준 문자열로 변환

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

이러한 명령은 AES (AES(Advanced Encryption Standard)) 알고리즘을 사용 하 여 변수에 저장 된 보안 문자열을 `$SecureString` 192 비트 키를 사용 하는 암호화 된 표준 문자열로 변환 합니다. 결과로 생성 되는 암호화 된 표준 문자열은 `$StandardString` 변수에 저장 됩니다.

첫 번째 명령은 변수에 키를 저장 합니다 `$Key` . 키는 24 개의 10 진수 숫자로 이루어진 배열이 며, 각 숫자는 부호 없는 단일 바이트에 맞게 256 미만 이어야 합니다.

각 10 진수는 단일 바이트 (8 비트)를 나타내므로 키의 24 자리 숫자는 총 192 비트 (8 x 24)가 됩니다. 이것이 AES 알고리즘의 유효한 키 길이입니다.

두 번째 명령은 변수의 키를 사용 하 여 `$Key` 보안 문자열을 암호화 된 표준 문자열로 변환 합니다.

### 예제 4: 보안 문자열을 일반 텍스트 문자열로 직접 변환

```powershell
$secureString = ConvertTo-SecureString -String 'Example' -AsPlainText
$secureString # 'System.Security.SecureString'
ConvertFrom-SecureString -SecureString $secureString -AsPlainText # 'Example'
```

## PARAMETERS

### -AsPlainText

설정 하 `ConvertFrom-SecureString` 는 경우 보안 문자열을 해독 된 일반 텍스트 문자열의 출력으로 변환 합니다.

이 매개 변수는 PowerShell 7.0에 추가 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsPlainText
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -키

암호화 키를 바이트 배열로 지정합니다.

```yaml
Type: System.Byte[]
Parameter Sets: Open
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecureKey

암호화 키를 보안 문자열로 지정합니다. 보안 문자열 값은 키로 사용되기 전에 바이트 배열로 변환됩니다.

```yaml
Type: System.Security.SecureString
Parameter Sets: Secure
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecureString

암호화된 기본 문자열로 변환할 보안 문자열을 지정합니다.

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.
자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.Security.SecureString

**Securestring** 개체를 convertfrom-csv에 파이프 할 수 있습니다.

## 출력

### System.String

ConvertFrom-SecureString은 기본 문자열 개체를 반환합니다.

## 참고

- 명령 프롬프트에 입력 된 문자에서 보안 문자열을 만들려면 cmdlet의 **Assecurestring** 매개 변수를 사용 `Read-Host` 합니다.
- **키 또는** **securekey** 매개 변수를 사용 하 여 키를 지정 하는 경우 키 길이가 정확 해야 합니다. 예를 들어 128 비트의 키를 16 진수 숫자의 바이트 배열로 지정할 수 있습니다.
  마찬가지로 192 비트 및 256 비트 키는 각각 24 및 32 10 진수 숫자의 바이트 배열에 해당 합니다.
- 이모티콘 등의 일부 문자는 해당 문자를 포함 하는 문자열의 여러 코드 요소에 해당 합니다. 암호에 사용 되는 경우 문제 및 오해를 일으킬 수 있으므로 이러한 문자를 사용 하지 마십시오.

## 관련 링크

[ConvertTo-SecureString](ConvertTo-SecureString.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)

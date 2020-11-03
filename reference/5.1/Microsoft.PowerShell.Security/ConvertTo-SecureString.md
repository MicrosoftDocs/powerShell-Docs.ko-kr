---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-SecureString
ms.openlocfilehash: 6e536681f78a79660e80951d0dcc446fbba32553
ms.sourcegitcommit: df80c558e9a4b89c9798f084bd04012ece15155c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2020
ms.locfileid: "93225146"
---
# ConvertTo-SecureString

## 개요
일반 텍스트 또는 암호화 된 문자열을 보안 문자열로 변환 합니다.

## SYNTAX

### Secure (기본값)

```
ConvertTo-SecureString [-String] <String> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### 일반 텍스트

```
ConvertTo-SecureString [-String] <String> [-AsPlainText] [-Force] [<CommonParameters>]
```

### 열기

```
ConvertTo-SecureString [-String] <String> [-Key <Byte[]>] [<CommonParameters>]
```

## 설명

`ConvertTo-SecureString`Cmdlet은 암호화 된 표준 문자열을 보안 문자열로 변환 합니다. 또한 일반 텍스트를 보안 문자열로 변환할 수도 있습니다. 및와 함께 사용 `ConvertFrom-SecureString` 됩니다 `Read-Host` . Cmdlet에서 생성 된 보안 문자열은 **SecureString** 유형의 매개 변수가 필요한 cmdlet 또는 함수와 함께 사용할 수 있습니다. Cmdlet을 사용 하 여 보안 문자열을 암호화 된 표준 문자열로 다시 변환할 수 있습니다 `ConvertFrom-SecureString` . 이렇게 하면 나중에 사용할 수 있도록 문자열을 파일에 저장할 수 있습니다.

변환 되는 표준 문자열이 지정 된 키를 사용 하 여 암호화 된 경우 `ConvertFrom-SecureString` 동일한 키를 cmdlet의 **키** 또는 **securekey** 매개 변수 값으로 제공 해야 합니다 `ConvertTo-SecureString` .

## 예제

### 예제 1: 보안 문자열을 암호화 된 문자열로 변환

이 예제에서는 사용자 입력에서 보안 문자열을 만들고 보안 문자열을 암호화된 표준 문자열로 변환한 다음 암호화된 표준 문자열을 보안 문자열로 다시 변환하는 방법을 보여 줍니다.

```powershell
PS C:\> $Secure = Read-Host -AsSecureString
PS C:\> $Secure
System.Security.SecureString
PS C:\> $Encrypted = ConvertFrom-SecureString -SecureString $Secure
PS C:\> $Encrypted
01000000d08c9ddf0115d1118c7a00c04fc297eb010000001a114d45b8dd3f4aa11ad7c0abdae98000000000
02000000000003660000a8000000100000005df63cea84bfb7d70bd6842e7efa79820000000004800000a000
000010000000f10cd0f4a99a8d5814d94e0687d7430b100000008bf11f1960158405b2779613e9352c6d1400
0000e6b7bf46a9d485ff211b9b2a2df3bd6eb67aae41
PS C:\> $Secure2 = ConvertTo-SecureString -String $Encrypted
PS C:\> $Secure2
System.Security.SecureString
```

첫 번째 명령은 cmdlet의 **Assecurestring** 매개 변수를 사용 하 여 `Read-Host` 보안 문자열을 만듭니다. 명령을 입력 한 후 입력 하는 모든 문자는 보안 문자열로 변환 된 후 변수에 저장 됩니다 `$Secure` .

두 번째 명령은 변수의 내용을 표시 합니다 `$Secure` . `$Secure`변수에 보안 문자열이 포함 되어 있으므로 PowerShell은 **system.object** 형식만 표시 합니다.

세 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SecureString` 변수의 보안 문자열을 `$Secure` 암호화 된 표준 문자열로 변환 합니다. 결과를 `$Encrypted` 변수에 저장 합니다.

네 번째 명령은 변수 값에 암호화 된 문자열을 표시 합니다 `$Encrypted` .

다섯 번째 명령은 cmdlet을 사용 하 여 `ConvertTo-SecureString` 변수의 암호화 된 표준 문자열을 `$Encrypted` 다시 보안 문자열로 변환 합니다. 결과를 `$Secure2` 변수에 저장 합니다.
여섯 번째 명령은 변수의 값을 표시 합니다 `$Secure2` . SecureString 유형은 명령이 성공했음을 나타냅니다.

### 예제 2: 파일의 암호화 된 문자열에서 보안 문자열 만들기

이 예제에서는 파일에 저장된 암호화된 표준 문자열에서 보안 문자열을 만드는 방법을 보여 줍니다.

```powershell
$Secure = Read-Host -AsSecureString
$Encrypted = ConvertFrom-SecureString -SecureString $Secure -Key (1..16)
$Encrypted | Set-Content Encrypted.txt
$Secure2 = Get-Content Encrypted.txt | ConvertTo-SecureString -Key (1..16)
```

첫 번째 명령은 cmdlet의 **Assecurestring** 매개 변수를 사용 하 여 `Read-Host` 보안 문자열을 만듭니다. 명령을 입력 한 후 입력 하는 모든 문자는 보안 문자열로 변환 된 후 변수에 저장 됩니다 `$Secure` .

두 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SecureString` `$Secure` 지정 된 키를 사용 하 여 변수의 보안 문자열을 암호화 된 표준 문자열로 변환 합니다. 콘텐츠는 변수에 저장 됩니다 `$Encrypted` .

세 번째 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 변수 값을 `$Encrypted` cmdlet으로 보냅니다 `Set-Content` . 그러면이 cmdlet이 Encrypted.txt 파일에 값을 저장 합니다.

네 번째 명령은 cmdlet을 사용 하 여 `Get-Content` Encrypted.txt 파일에서 암호화 된 표준 문자열을 가져옵니다. 이 명령은 파이프라인 연산자를 사용 하 여 암호화 된 문자열을 cmdlet으로 보냅니다 `ConvertTo-SecureString` .이 cmdlet은 지정 된 키를 사용 하 여 보안 문자열로 변환 합니다.
결과는 변수에 저장 됩니다 `$Secure2` .

### 예제 3: 일반 텍스트 문자열을 보안 문자열로 변환

이 명령은 일반 텍스트 문자열을 `P@ssW0rD!` 보안 문자열로 변환 하 고 결과를 `$Secure_String_Pwd` 변수에 저장 합니다. **Asplaintext** 매개 변수를 사용 하려면 **Force** 매개 변수도 명령에 포함 되어야 합니다.

```powershell
$Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force
```

> [!CAUTION]
> 스크립트나 명령줄에서 일반 텍스트 문자열을 사용 하지 않는 것이 좋습니다. 일반 텍스트는 이벤트 로그 및 명령 기록 로그에 표시 될 수 있습니다.

## PARAMETERS

### -AsPlainText

보안 문자열로 변환할 일반 텍스트 문자열을 지정합니다. 보안 문자열 cmdlet을 사용하여 기밀 텍스트를 보호할 수 있습니다. 텍스트는 개인 정보 보호를 위해 암호화되며 사용한 후 컴퓨터 메모리에서 삭제됩니다. 이 매개 변수를 사용하여 일반 텍스트를 입력으로 제공할 경우 시스템에서 이러한 방식으로 해당 입력을 보호할 수 없습니다. 이 매개 변수를 사용 하려면 **Force** 매개 변수도 지정 해야 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

**Asplaintext** 매개 변수를 사용 하는 경우의 의미를 이해 하 고 있는지 확인 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -키

원래 보안 문자열을 암호화 된 표준 문자열로 변환 하는 데 사용 되는 암호화 키를 지정 합니다. 유효한 키 길이는 16, 24 및 32 바이트입니다.

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

원래 보안 문자열을 암호화 된 표준 문자열로 변환 하는 데 사용 되는 암호화 키를 지정 합니다. 제공하는 키는 보안 문자열 형식이어야 합니다. 보안 문자열은 키로 사용할 바이트 배열로 변환 됩니다. 유효한 보안 키 길이는 8, 12 및 16 코드 요소입니다.

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

### -문자열

보안 문자열로 변환할 문자열을 지정합니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

암호화 된 표준 문자열을로 파이프 할 수 있습니다 `ConvertTo-SecureString` .

## 출력

### System.Security.SecureString

`ConvertTo-SecureString`**SecureString** 개체를 반환 합니다.

## 참고

이모티콘 등의 일부 문자는 해당 문자를 포함 하는 문자열의 여러 코드 요소에 해당 합니다. 암호에 사용 되는 경우 문제 및 오해를 일으킬 수 있으므로 이러한 문자를 사용 하지 마십시오.

## 관련 링크

[ConvertFrom-SecureString](ConvertFrom-SecureString.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)

---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/protect-cmsmessage?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Protect-CmsMessage
ms.openlocfilehash: de72454f4c50746ca22853dd51e2ec0447bed101
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347638"
---
# Protect-CmsMessage

## 개요
암호화 메시지 구문 형식을 사용 하 여 콘텐츠를 암호화 합니다.

## SYNTAX

### ByContent (기본값)

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <PSObject> [[-OutFile] <String>]
 [<CommonParameters>]
```

### ByPath

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <String> [[-OutFile] <String>] [<CommonParameters>]
```

### ByLiteralPath

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <String> [[-OutFile] <String>]
 [<CommonParameters>]
```

## 설명

`Protect-CmsMessage`Cmdlet은 CMS (암호화 메시지 구문) 형식을 사용 하 여 콘텐츠를 암호화 합니다.

CMS cmdlet은 [RFC5652](https://tools.ietf.org/html/rfc5652.html)에 설명 된 대로 IETF 형식을 사용 하 여 콘텐츠의 암호화 및 암호 해독을 지원 합니다.

CMS 암호화 표준은 공개 키 암호화를 사용 합니다. 여기서는 콘텐츠를 암호화 하는 데 사용 되는 키 (공개 키)와 콘텐츠를 암호 해독 하는 데 사용 되는 키 (개인 키)가 구분 됩니다. 공개 키는 광범위하게 공유할 수 있으며 중요한 데이터가 아닙니다. 콘텐츠가 이 퍼블릭 키로 암호화된 경우 프라이빗 키로만 암호 해독할 수 있습니다. 자세한 내용은 [공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조하세요.

Cmdlet을 실행 하려면 먼저 `Protect-CmsMessage` 암호화 인증서를 설정 해야 합니다.
PowerShell에서 인식할 수 있도록 암호화 인증서에는 데이터 암호화 인증서 (예: 코드 서명 및 암호화 된 메일의 Id)로 식별 하는 고유[EKU](/windows/desktop/SecCrypto/eku)(확장 키 사용) ID가 필요 합니다. 문서 암호화에 사용할 수 있는 인증서의 예는이 항목의 예 1을 참조 하십시오.

> [!NOTE]
> 이 cmdlet은 Windows 에서만 사용할 수 있습니다.

## 예제

### 예제 1: 콘텐츠 암호화를 위한 인증서 만들기

Cmdlet을 실행 하려면 먼저 `Protect-CmsMessage` 암호화 인증서를 만들어야 합니다. 다음 텍스트를 사용 하 여 제목 줄의 이름을 이름, 전자 메일 또는 기타 식별자로 변경 하 고 인증서를 파일에 저장 합니다 (예: `DocumentEncryption.inf` 이 예제에 표시 된 것 처럼).

```powershell
# Create .INF file for certreq
{[Version]
Signature = "$Windows NT$"

[Strings]
szOID_ENHANCED_KEY_USAGE = "2.5.29.37"
szOID_DOCUMENT_ENCRYPTION = "1.3.6.1.4.1.311.80.1"

[NewRequest]
Subject = "cn=youralias@emailaddress.com"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT_KEY_ENCIPHERMENT_KEY_USAGE | CERT_DATA_ENCIPHERMENT_KEY_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"

[Extensions]
%szOID_ENHANCED_KEY_USAGE% = "{text}%szOID_DOCUMENT_ENCRYPTION%"
} | Out-File -FilePath DocumentEncryption.inf

# After you have created your certificate file, run the following command to add
# the certificate file to the certificate store. Now you are ready to encrypt and
# decrypt content with the next two examples.
certreq.exe -new DocumentEncryption.inf DocumentEncryption.cer
```

### 예 2: 전자 메일로 보낸 메시지 암호화

```powershell
$Protected = "Hello World" | Protect-CmsMessage -To "*youralias@emailaddress.com*"
```

다음 예에서는 "Hello World" 메시지를 cmdlet으로 파이프 하 여 암호화 한 `Protect-CmsMessage` 다음 암호화 된 메시지를 변수에 저장 합니다. **To** 매개 변수는 인증서의 제목 줄 값을 사용 합니다.

### 예제 3: 문서 암호화 인증서 보기

```
PS C:\> cd Cert:\CurrentUser\My
PS Cert:\CurrentUser\My> Get-ChildItem -DocumentEncryptionCert
```

인증서 공급자에서 문서 암호화 인증서를 보려면 인증서 공급자가 로드 된 경우에만 사용할 수 있는 [Get ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)의 **documentencryptioncert** 동적 매개 변수를 추가할 수 있습니다.

## PARAMETERS

### -콘텐츠

암호화 하려는 콘텐츠를 포함 하는 **PSObject** 를 지정 합니다. 예를 들어 이벤트 메시지의 내용을 암호화 한 다음, 메시지 (이 예제에서는)를 포함 하는 변수를 `$Event` **콘텐츠** 매개 변수의 값으로 사용할 수 있습니다 `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1` . Cmdlet을 사용 하 여 `Get-Content` Microsoft Word 문서와 같은 파일의 내용을 가져오고 **콘텐츠** 매개 변수 값으로 사용 하는 변수에 콘텐츠를 저장할 수도 있습니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByContent
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

암호화 하려는 콘텐츠의 경로를 지정 합니다. **Path** 와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -출력

암호화 된 콘텐츠를 전송 하려는 파일의 경로와 파일 이름을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

암호화 하려는 콘텐츠의 경로를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -To

다음 형식으로 식별 된 하나 이상의 CMS 메시지 받는 사람을 지정 합니다.

- 실제 인증서 (인증서 공급자에서 검색 됨)
- 인증서를 포함 하는 파일의 경로입니다.
- 인증서를 포함 하는 디렉터리의 경로입니다.
- 인증서의 지문 (인증서 저장소를 찾는 데 사용 됨)
- 인증서 저장소를 찾는 데 사용 되는 인증서의 주체 이름입니다.

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

## 출력

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

## 관련 링크

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-CmsMessage](Get-CmsMessage.md)

[Unprotect-CmsMessage](Unprotect-CmsMessage.md)

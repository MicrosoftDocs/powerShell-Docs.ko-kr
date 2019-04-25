---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: b8940ded189d822a5a2cd40773ef5146353611cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62059001"
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a>암호화 메시지 구문(CMS) cmdlet

암호화 메시지 구문 cmdlet은 [RFC5652](https://tools.ietf.org/html/rfc5652) 문서에 기록된 대로 메시지를 암호로 보호하기 위해 IETF 표준 형식을 사용하는 콘텐츠의 암호화 및 암호 해독을 지원합니다.

```powershell
Get-CmsMessage [-Content] <string>
Get-CmsMessage [-Path] <string>
Get-CmsMessage [-LiteralPath] <string>
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <string> [[-OutFile] <string>]
Unprotect-CmsMessage [-EventLogRecord] <EventLogRecord> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Content] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Path] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-LiteralPath] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
```

CMS 암호화 표준은 공개 키 암호화를 구현하는데, 여기서는 콘텐츠를 암호화하는 데 사용되는 키(*공개 키*)와 콘텐츠를 암호 해독하는 데 사용되는 키(*개인 키*)가 구분됩니다.

공개 키는 광범위하게 공유할 수 있으며 중요한 데이터가 아닙니다. 콘텐츠가 이 공개 키로 암호화된 경우 개인 키로만 암호 해독할 수 있습니다. 자세한 내용은 [공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조하세요.

PowerShell에서 인식할 수 있도록 암호화 인증서가 데이터 암호화 인증서로 식별되려면 고유 키 사용 식별자(EKU)(예: ‘코드 서명', ‘암호화된 메일’에 대한 식별자)가 필요합니다.

다음은 문서 암호화에 적합한 인증서를 만드는 예제입니다.

```powershell
(Change the text in **Subject** to your name, email, or other identifier), and put in a file (i.e.: DocumentEncryption.inf):
[Version]
Signature = "$Windows NT$"
[Strings]
szOID\_ENHANCED\_KEY\_USAGE = "2.5.29.37"
szOID\_DOCUMENT\_ENCRYPTION = "1.3.6.1.4.1.311.80.1"
[NewRequest]
Subject = "<cn=me@somewhere.com>"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT\_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT\_KEY\_ENCIPHERMENT\_KEY\_USAGE | CERT\_DATA\_ENCIPHERMENT\_KEY\_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"
[Extensions]
%szOID\_ENHANCED\_KEY\_USAGE% = "{text}%szOID\_DOCUMENT\_ENCRYPTION%"
```

다음을 실행합니다.
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

이제 콘텐츠를 암호화하고 암호 해독할 수 있습니다.

```powershell
$protected = "Hello World" | Protect-CmsMessage -To "\*me@somewhere.com\*[](mailto:*leeholm@microsoft.com*)"
$protected
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMMFWxlZWhv
bG1AbWljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYU5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNVmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPAwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84OHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1ZtDj7nSJc=
-----END CMS-----

$protected | Unprotect-CmsMessage
Hello World
```

**CMSMessageRecipient** 형식의 모든 매개 변수는 다음과 같은 형식의 식별자를 지원합니다.
- 실제 인증서(인증서 공급자에서 검색됨)
- 인증서를 포함하는 파일의 경로
- 인증서를 포함하는 디렉터리의 경로
- 인증서의 지문(인증서 저장소를 찾는 데 사용됨)
- 인증서의 주체 이름(인증서 저장소를 찾는 데 사용됨)

인증서 공급자에서 문서 암호화 인증서를 보려면 **-DocumentEncryptionCert** 동적 매개 변수를 사용할 수 있습니다.

```powershell
dir -DocumentEncryptionCert
```

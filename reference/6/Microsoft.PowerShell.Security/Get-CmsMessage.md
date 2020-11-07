---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-cmsmessage?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CmsMessage
ms.openlocfilehash: fcc4305ee5a7198f78eb7b6ce735cf45b90bbf6f
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344860"
---
# Get-CmsMessage

## 개요
암호화 메시지 구문 형식을 사용 하 여 암호화 된 콘텐츠를 가져옵니다.

## SYNTAX

### ByContent

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### ByPath

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### ByLiteralPath

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## 설명

`Get-CmsMessage`Cmdlet은 CMS (암호화 메시지 구문) 형식을 사용 하 여 암호화 된 콘텐츠를 가져옵니다.

CMS cmdlet은 [RFC5652](https://tools.ietf.org/html/rfc5652)에 설명 된 대로 암호화 된 메시지를 보호 하기 위해 IETF 형식을 사용 하 여 콘텐츠의 암호화 및 암호 해독을 지원 합니다.

CMS 암호화 표준은 공개 키 암호화를 사용 합니다. 여기서는 콘텐츠를 암호화 하는 데 사용 되는 키 (공개 키)와 콘텐츠를 암호 해독 하는 데 사용 되는 키 (개인 키)가 구분 됩니다. 공개 키는 광범위하게 공유할 수 있으며 중요한 데이터가 아닙니다. 콘텐츠가 이 퍼블릭 키로 암호화된 경우 프라이빗 키로만 암호 해독할 수 있습니다. 자세한 내용은 [공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조하세요.

`Get-CmsMessage` CMS 형식으로 암호화 된 콘텐츠를 가져옵니다. 콘텐츠를 해독 하거나 보호를 해제 하지 않습니다. 이 cmdlet을 실행 하 여 cmdlet을 실행 하 여 암호화 한 콘텐츠를 가져올 수 있습니다 `Protect-CmsMessage` . 암호화 된 내용에 대 한 경로를 통해 문자열로 해독 하려는 콘텐츠를 지정할 수 있습니다. `Get-CmsMessage` `Unprotect-CmsMessage` 콘텐츠를 암호화 하는 데 사용 된 문서 암호화 인증서에 대 한 정보가 있는 경우의 결과를로 파이프 하 여 콘텐츠의 암호를 해독할 수 있습니다.

> [!NOTE]
> 이 cmdlet은 Windows 에서만 사용할 수 있습니다.

## 예제

### 예제 1: 암호화 된 콘텐츠 가져오기

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg.Content
```

```Output
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMBFWxlZWhv
bG1AbGljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYP5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNXmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPRwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84AHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1AtDj7nSJc=
-----END CMS-----
```

이 명령은 C:\Users\Test\Documents\PowerShell\Future_Plans.txt에 있는 암호화 된 콘텐츠를 가져옵니다.

### 예제 2: Unprotect-CmsMessage로 암호화 된 콘텐츠 파이프

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

이 명령은 예제 1에서 cmdlet의 결과를 파이프 하 여 `Get-CmsMessage` `Unprotect-CmsMessage` 메시지의 암호를 해독 하 고 일반 텍스트로 읽습니다. 이 경우 **To** 매개 변수 값은 암호화 인증서의 제목 줄 값입니다. 해독 된 메시지 "새 중단 모두 실행 명령"이 결과에 해당 합니다.

## PARAMETERS

### -콘텐츠

암호화 된 문자열 또는 암호화 된 문자열을 포함 하는 변수를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

가져올 암호화 된 콘텐츠의 경로를 지정 합니다. **Path** 와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드 문자로 해석되지 않습니다. 경로에 이스케이프 문자가 포함 된 경우 각 항목을 작은따옴표로 묶습니다.
작은따옴표는 포함 된 문자를 이스케이프 문자로 해석 하지 않도록 PowerShell에 지시 합니다.

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

### -Path

해독 하려는 암호화 된 콘텐츠의 경로를 지정 합니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

## 관련 링크

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Protect-CmsMessage](Protect-CmsMessage.md)

[Unprotect-CmsMessage](Unprotect-CmsMessage.md)

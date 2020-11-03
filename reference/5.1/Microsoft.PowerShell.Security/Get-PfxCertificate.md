---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: 1be3034b1fb44b1dce1a592ea5a2c1622b54d28f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214225"
---
# Get-PfxCertificate

## 개요
컴퓨터의 PFX 인증서 파일에 대 한 정보를 가져옵니다.

## SYNTAX

### ByPath (기본값)

```
Get-PfxCertificate [-FilePath] <String[]> [<CommonParameters>]
```

### ByLiteralPath

```
Get-PfxCertificate -LiteralPath <String[]> [<CommonParameters>]
```

## 설명

`Get-PfxCertificate`Cmdlet은 지정 된 각 PFX 인증서 파일을 나타내는 개체를 가져옵니다.
PFX 파일에는 인증서와 개인 키가 모두 포함 됩니다.

## 예제

### 예제 1: PFX 인증서 가져오기

```powershell
Get-PfxCertificate -FilePath "C:\windows\system32\Test.pfx"
```

```output
Password: ******
Signer Certificate:      David Chew (Self Certificate)
Time Certificate:
Time Stamp:
Path:                    C:\windows\system32\zap.pfx
```

이 명령은 시스템의 테스트 .pfx 인증서 파일에 대 한 정보를 가져옵니다.

### 예 2: 원격 컴퓨터에서 PFX 인증서 가져오기

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

이 명령은 Server01 원격 컴퓨터에서 PFX 인증서 파일을 가져옵니다. 를 사용 `Invoke-Command` 하 여 `Get-PfxCertificate` 원격으로 명령을 실행 합니다.

PFX 인증서 파일이 암호로 보호 되지 않는 경우의 **Authentication** 매개 변수 값은 CredSSP 여야 합니다 `Invoke-Command` .

## PARAMETERS

### -FilePath

보안 파일의 PFX 파일에 대 한 전체 경로를 지정 합니다. 이 매개 변수에 대 한 값을 지정 하는 경우 명령줄에를 입력할 필요가 없습니다 `-FilePath` .

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

보안 파일의 PFX 파일에 대 한 전체 경로입니다. **FilePath** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

파일 경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Get-PfxCertificate` .

## 출력

### System.Security.Cryptography.X509Certificates.X509Certificate2

`Get-PfxCertificate` 가져오는 각 인증서에 대 한 개체를 반환 합니다.

## 참고

Cmdlet을 사용 하 여 `Invoke-Command` 원격으로 `Get-PfxCertificate` 명령을 실행 하 고 PFX 인증서 파일이 암호로 보호 되지 않는 경우의 **Authentication** 매개 변수 값은 CredSSP 여야 합니다 `Invoke-Command` .

## 관련 링크

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

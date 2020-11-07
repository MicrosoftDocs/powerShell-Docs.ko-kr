---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-authenticodesignature?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-AuthenticodeSignature
ms.openlocfilehash: 8c78366eacec964ced28aaed8ef17534df4abff4
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344816"
---
# Set-AuthenticodeSignature

## 개요
PowerShell 스크립트 또는 다른 파일에 [Authenticode](/windows-hardware/drivers/install/authenticode) 서명을 추가 합니다.

## SYNTAX

### ByPath (기본값)

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] [-FilePath] <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -LiteralPath <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByContent

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -SourcePathOrExtension <String[]>
 -Content <Byte[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Set-AuthenticodeSignature`Cmdlet은 SIP (Subject Interface Package)를 지 원하는 모든 파일에 Authenticode 서명을 추가 합니다.

PowerShell 스크립트 파일에서 서명은 스크립트에서 실행 되는 명령의 끝을 나타내는 텍스트 블록 형식을 사용 합니다. 이 cmdlet이 실행될 때 파일에 서명이 있는 경우 해당 서명은 제거됩니다.

## 예제

### 예 1-로컬 인증서 저장소의 인증서를 사용 하 여 스크립트 서명

이러한 명령은 PowerShell 인증서 공급자에서 코드 서명 인증서를 검색 하 여 PowerShell 스크립트에 서명 하는 데 사용 합니다.

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath PsTestInternet2.ps1 -Certificate $cert
```

첫 번째 명령은 `Get-ChildItem` cmdlet 및 PowerShell 인증서 공급자를 사용 하 여 `Cert:\CurrentUser\My` 인증서 저장소의 하위 디렉터리에 있는 인증서를 가져옵니다. `Cert:`드라이브는 인증서 공급자가 노출 하는 드라이브입니다. 인증서 공급자 에서만 지원 되는 **Codesigningcert** 매개 변수는 검색 된 인증서를 코드 서명 기관이 있는 인증서로 제한 합니다. 이 명령은 결과를 `$cert` 변수에 저장 합니다.

두 번째 명령은 cmdlet을 사용 하 여 `Set-AuthenticodeSignature` 스크립트에 서명 합니다 `PSTestInternet2.ps1` . **FilePath** 매개 변수를 사용 하 여 스크립트의 이름을 지정 하 고 **certificate** 매개 변수를 사용 하 여 인증서를 변수에 저장 하도록 지정 합니다 `$cert` .

> [!NOTE]
> 에서 **Codesigningcert** 매개 변수를 사용 하면 `Get-ChildItem` 코드 서명 기관이 있는 인증서만 반환 되 고 개인 키가 포함 됩니다. 개인 키가 없는 경우 서명에는 인증서를 사용할 수 없습니다.

### 예 2-PFX 파일의 인증서를 사용 하 여 스크립트 서명

이러한 명령은 cmdlet을 사용 `Get-PfxCertificate` 하 여 코드 서명 인증서를 로드 합니다. 그런 다음 PowerShell 스크립트에 서명 하는 데 사용 합니다.

```powershell
$cert = Get-PfxCertificate -FilePath C:\Test\Mysign.pfx
Set-AuthenticodeSignature -FilePath ServerProps.ps1 -Certificate $cert
```

첫 번째 명령은 cmdlet을 사용 하 여 `Get-PfxCertificate` C:\Test\MySign.pfx 인증서를 변수에 로드 합니다 `$cert` .

두 번째 명령은를 사용 하 여 `Set-AuthenticodeSignature` 스크립트에 서명 합니다. 의 **FilePath** 매개 변수는 `Set-AuthenticodeSignature` 서명 되는 스크립트 파일의 경로를 지정 하 고 **Cert** 매개 변수는 `$cert` 인증서를 포함 하는 변수를에 전달 `Set-AuthenticodeSignature` 합니다.

인증서 파일이 암호로 보호 된 경우 PowerShell에서 암호를 묻는 메시지를 표시 합니다.

### 예제 3-루트 인증 기관을 포함 하는 서명 추가

이 명령은 신뢰 체인에 루트 기관을 포함하는 디지털 서명을 추가하며 타사 타임스탬프 서버에서 서명됩니다.

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\Remodel.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

이 명령은 **FilePath** 매개 변수를 사용 하 여 서명할 스크립트를 지정 하 고 **certificate** 매개 변수를 사용 하 여 변수에 저장 된 인증서를 지정 합니다 `$cert` . **명령은 includechain** 매개 변수를 사용 하 여 루트 기관을 포함 하 여 신뢰 체인의 모든 서명을 포함 합니다. 또한 **이 명령은 timestampserver** 매개 변수를 사용 하 여 서명에 타임 스탬프를 추가 합니다.
그러면 인증서가 만료되어도 스크립트에 오류가 발생하지 않습니다.

## PARAMETERS

### -인증서

스크립트 또는 파일을 서명하는 데 사용할 인증서를 지정합니다. 인증서를 나타내는 개체 또는 인증서를 가져오는 식을 저장할 변수를 입력합니다.

인증서를 찾으려면를 사용 `Get-PfxCertificate` 하거나 `Get-ChildItem` 인증서 드라이브에서 cmdlet을 사용 `Cert:` 합니다. 인증서가 유효 하지 않거나 권한이 없는 경우 `code-signing` 명령이 실패 합니다.

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

서명할 파일 경로를 지정합니다.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Force

cmdlet이 읽기 전용 파일에 서명을 추가할 수 있도록 합니다. **Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HashAlgorithm

Windows에서 파일의 디지털 서명을 컴퓨팅하는 데 사용하는 해싱 알고리즘을 지정합니다.

PowerShell 3.0의 경우 기본값은 Windows 기본 해싱 알고리즘인 SHA256입니다. PowerShell 2.0의 경우 기본값은 SHA1입니다. 다른 해싱 알고리즘으로 서명된 파일은 다른 시스템에서 인식되지 않을 수도 있습니다. 지원 되는 알고리즘은 운영 체제의 버전에 따라 다릅니다.

가능한 값 목록은 [HashAlgorithmName 구조체](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SHA256
Accept pipeline input: False
Accept wildcard characters: False
```

### -명령은 includechain

인증서 신뢰 체인의 인증서가 디지털 서명에 포함되어 있는지 확인합니다.
**Notroot** 는 기본값입니다.

유효한 값은 다음과 같습니다.

- 서명자: 서명자의 인증서만 포함 합니다.
- NotRoot: 루트 인증 기관을 제외 하 고 인증서 체인의 모든 인증서를 포함 합니다.
- 모두: 인증서 체인의 모든 인증서를 포함 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: NotRoot
Accept pipeline input: False
Accept wildcard characters: False
```

### -이 명령은 timestampserver

지정된 타임스탬프 서버를 사용하여 서명에 타임스탬프를 추가합니다. 타임스탬프 서버의 URL을 문자열로 입력합니다.

타임스탬프는 인증서를 파일에 추가한 정확한 시간을 나타냅니다. 타임스탬프를 사용하면 사용자 및 프로그램에서 서명 당시 인증서가 유효했는지를 확인할 수 있으므로 인증서가 만료되어도 스크립트 오류를 방지할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

서명할 파일 경로를 지정합니다. **FilePath** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

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

디지털 서명이 추가 된 콘텐츠의 파일 또는 파일 형식에 대 한 경로입니다. 이 매개 변수는 파일 콘텐츠가 바이트 배열로 전달 되는 **콘텐츠와** 함께 사용 됩니다.

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

### -콘텐츠

디지털 서명을 추가 하는 바이트 배열인 파일의 내용입니다. 이 매개 변수는 **SourcePathOrExtension** 매개 변수와 함께 사용 해야 합니다. 파일의 내용은 유니코드 (UTF-16LE) 형식 이어야 합니다.

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

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

파일 경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Set-AuthenticodeSignature` .

## 출력

### System.object..

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

## 관련 링크

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Get-PfxCertificate](Get-PfxCertificate.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)

---
description: 인증서
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/about/about_certificate_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 인증서 공급자
ms.openlocfilehash: d1280d34429600e8c06e96a36921df3d04f9eda6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223641"
---
# <a name="certificate-provider"></a>인증서 공급자

## <a name="provider-name"></a>공급자 이름

인증서

## <a name="drives"></a>드라이브

`Cert:`

## <a name="capabilities"></a>기능

**ShouldProcess**

## <a name="short-description"></a>간단한 설명

PowerShell에서 x.509 인증서 저장소 및 인증서에 대 한 액세스를 제공 합니다.

## <a name="detailed-description"></a>자세한 설명

PowerShell **인증서** 공급자를 통해 powershell에서 인증서 및 인증서 저장소를 가져오고 추가, 변경 및 삭제할 수 있습니다.

**인증서** 드라이브는 컴퓨터의 인증서 저장소 및 인증서를 포함 하는 계층적 네임 스페이스입니다.

**인증서** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a>이 공급자가 노출 하는 형식

인증서 드라이브는 다음 형식을 노출 합니다.

- 저장소 위치 (Microsoft.powershell.commands.x509storelocation)-현재 사용자와 모든 사용자에 대 한 인증서를 그룹화 하는 상위 수준의 컨테이너입니다. 각 시스템에는 CurrentUser 및 LocalMachine(모든 사용자) 저장소 위치가 있습니다.

- 인증서 저장소 (System.security.cryptography.x509certificates.x509certificate2. X509Store)-인증서를 저장 하 고 관리 하는 물리적 저장소입니다.

- X.509 **system.security.cryptography.x509certificates.x509certificate2. X509Certificate2** 인증서 이며, 각 인증서는 컴퓨터의 x.509 인증서를 나타냅니다.
  인증서는 지문으로 식별됩니다.

## <a name="navigating-the-certificate-drive"></a>인증서 드라이브 탐색

**인증서** 공급자는 인증서 네임 스페이스를 `Cert:` PowerShell의 드라이브로 노출 합니다. 이 명령은 명령을 사용 하 여 `Set-Location` 현재 위치를 LocalMachine 저장소 위치의 루트 인증서 저장소로 변경 합니다. 백슬래시 ( \\ ) 또는 슬래시 (/)를 사용 하 여 드라이브의 수준을 표시 `Cert:` 합니다.

```powershell
Set-Location Cert:
```

다른 PowerShell 드라이브에서 인증서 공급자를 사용할 수도 있습니다. 다른 위치에서 별칭을 참조 하려면 `Cert:` 경로에 드라이브 이름을 사용 합니다.

```powershell
PS Cert:\> Set-Location -Path LocalMachine\Root
```

파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다. 예를 들어 다음과 같이 입력합니다.

```powershell
Set-Location C:
```

> [!NOTE]
> PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다. `dir`및 등의 명령은 `ls` 이제 [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭입니다 `cd` .는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭입니다.
> 및 `pwd` 은 [(는) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.

## <a name="displaying-the-contents-of-the-cert-drive"></a>Cert: 드라이브의 내용 표시

이 명령은 cmdlet을 사용 하 여 `Get-ChildItem` CurrentUser 인증서 저장소 위치에 인증서 저장소를 표시 합니다.

드라이브에 없으면 `Cert:` 절대 경로를 사용 합니다.

```powershell
PS Cert:\CurrentUser\> Get-ChildItem
```

### <a name="displaying-certificate-properties-within-the-cert-drive"></a>Cert: 드라이브 내 인증서 속성 표시

이 예제에서는를 사용 하 여 인증서를 가져온 `Get-Item` 다음 변수에 저장 합니다.
이 예에서는를 사용 하 여 새 인증서 스크립트 속성 ( **DnsNameList** , **EnhancedKeyUsageList** , **SendAsTrustedIssuer** )을 보여 줍니다 `Select-Object` .

```powershell
$c = Get-Item cert:\LocalMachine\My\52A149D0393CE8A8D4AF0B172ED667A9E3A1F44E
$c | Format-List DnsNameList, EnhancedKeyUsageList, SendAsTrustedIssuer
```

```output
DnsNameList          : {SERVER01.contoso.com}
EnhancedKeyUsageList : {WiFi-Machine (1.3.6.1.4.1.311.42.2.6),
                       Client Authentication (1.3.6.1.5.5.7.3.2)}
SendAsTrustedIssuer  : False
```

### <a name="find-all-codesigning-certificates"></a>모든 코드 서명 인증서 찾기

이 명령은 cmdlet의 **Codesigningcert** 및 **재귀** 매개 변수를 사용 하 여 `Get-ChildItem` 코드 서명 기관이 있는 컴퓨터의 모든 인증서를 가져옵니다.

```powershell
Get-ChildItem -Path cert: -CodeSigningCert -Recurse
```

### <a name="find-expired-certificates"></a>만료 된 인증서 찾기

이 명령은 cmdlet의 **ExpiringInDays** 매개 변수를 사용 하 여 `Get-ChildItem` 다음 30 일 내에 만료 되는 인증서를 가져옵니다.

```powershell
Get-ChildItem -Path cert:\LocalMachine\WebHosting -ExpiringInDays 30
```

### <a name="find-server-ssl-certificates"></a>서버 SSL 인증서 찾기

이 명령은 cmdlet의 **Sslserverauthentication** 매개 변수를 사용 하 여 `Get-ChildItem` My 및 webhosting 저장소에 있는 모든 서버 SSL 인증서를 가져옵니다.

```powershell
Get-ChildItem -Path cert:\LocalMachine\My, cert:\LocalMachine\WebHosting `
  -SSLServerAuthentication
```

### <a name="find-expired-certificates-on-remote-computers"></a>원격 컴퓨터에서 만료 된 인증서 찾기

이 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Get-ChildItem` Srv01 및 Srv02 컴퓨터에서 명령을 실행 합니다. **ExpiringInDays** 매개 변수의 값이 0 이면 Srv01 및 Srv02 컴퓨터에서 만료 된 인증서를 가져옵니다.

```powershell
Invoke-Command -ComputerName Srv01, Srv02 {Get-ChildItem -Path cert:\* `
  -Recurse -ExpiringInDays 0}
```

### <a name="combining-filters-to-find-a-specific-set-of-certificates"></a>필터를 결합 하 여 특정 인증서 집합 찾기

이 명령은 다음 특성이 있는 LocalMachine 저장소 위치의 모든 인증서를 가져옵니다.

- DNS 이름에 "fabrikam"이 있습니다.
- EKU의 "클라이언트 인증"
- `$true` **SendAsTrustedIssuer** 속성에 대 한 값
- 다음 30 일 이내에 만료 되지 않습니다.

**Notafter** 속성은 인증서 만료 날짜를 저장 합니다.

```powershell
[DateTime] $ValidThrough = (Get-Date) + (New-TimeSpan -Days 30)
Get-ChildItem -Path cert:\* -Recurse -DNSName "*fabrikam*" `
  -EKU "*Client Authentication*" | Where-Object {
                                     $_.SendAsTrustedIssuer -and `
                                     $_.NotAfter -gt $ValidThrough
                                   }
```

## <a name="opening-the-certificates-mmc-snap-in"></a>인증서 MMC 스냅인 열기

`Invoke-Item`이 cmdlet은 기본 응용 프로그램을 사용 하 여 지정한 경로를 엽니다. 인증서의 경우 기본 응용 프로그램은 인증서 MMC 스냅인입니다.

이 명령은 지정된 인증서를 관리할 인증서 MMC 스냅인을 엽니다.

```powershell
Invoke-Item cert:\CurrentUser\my\6B8223358119BB08840DEE50FD8AF9EA776CE66B
```

## <a name="copying-certificates"></a>인증서 복사

인증서를 복사 하는 기능은 **인증서** 공급자에서 지원 되지 않습니다. 인증서를 복사 하려고 하면이 오류가 표시 됩니다.

```
$path = "Cert:\LocalMachine\Root\E2C0F6662D3C569705B4B31FE2CBF3434094B254"
PS Cert:\LocalMachine\> Copy-Item -Path $path -Destination .\CA\
Copy-Item : Provider operation stopped because the provider does not support
this operation.
At line:1 char:1
+ Copy-Item -Path $path -Destination .\CA\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotImplemented: (:) [Copy-Item],
                              PSNotSupportedException
    + FullyQualifiedErrorId : NotSupported,
                              Microsoft.PowerShell.Commands.CopyItemCommand
```

## <a name="moving-certificates"></a>인증서 이동

### <a name="move-all-ssl-server-authentication-certs-to-the-webhosting-store"></a>모든 SSL 서버 인증 인증서를 WebHosting 저장소로 이동 합니다.

이 명령은 cmdlet을 사용 하 여 `Move-Item` 내 저장소에서 WebHosting 저장소로 인증서를 이동 합니다.

`Move-Item` 는 인증서 저장소를 이동 하지 않으며 인증서를 다른 저장소 위치로 이동 하지 않습니다 (예: 인증서를 LocalMachine에서 CurrentUser로 이동). `Move-Item`Cmdlet은 인증서를 이동 하지만 개인 키는 이동 하지 않습니다.

이 명령은 cmdlet의 **Sslserverauthentication** 매개 변수를 사용 하 여 `Get-ChildItem` 내 인증서 저장소에서 SSL 서버 인증 인증서를 가져옵니다.

반환 된 인증서는 cmdlet으로 파이프 되어 `Move-Item` 인증서를 WebHosting 저장소로 이동 합니다.

```powershell
Get-ChildItem cert:\LocalMachine\My -SSLServerAuthentication | Move-Item `
  -Destination cert:\LocalMachine\WebHosting
```

## <a name="deleting-certificates-and-private-keys"></a>인증서 및 개인 키 삭제

`Remove-Item`Cmdlet은 사용자가 지정 하는 인증서를 제거 합니다. `-DeleteKey`동적 매개 변수는 개인 키를 삭제 합니다.

### <a name="delete-a-certificate-from-the-ca-store"></a>CA 저장소에서 인증서를 삭제 합니다.

이 명령은 CA 인증서 저장소에서 인증서를 삭제하지만 연결된 개인 키는 그대로 둡니다.

드라이브에서 `Cert:` `Remove-Item` Cmdlet은 **deletekey** , **Path** , **WhatIf** 및 **Confirm** 매개 변수만 지원 합니다. 다른 모든 매개 변수는 무시됩니다.

```powershell
Remove-Item cert:\LocalMachine\CA\5DDC44652E62BF9AA1116DC41DE44AB47C87BDD0
```

### <a name="delete-a-certificate-using-a-wildcards-in-the-dns-name"></a>DNS 이름에 와일드 카드를 사용 하 여 인증서 삭제

이 명령은 DNS 이름에 "Fabrikam"이 포함된 모든 인증서를 삭제합니다. 이 cmdlet은 cmdlet의 **DNSName** 매개 변수를 사용 하 여 인증서를 가져오고 cmdlet을 사용 하 여 `Get-ChildItem` 인증서를 `Remove-Item` 삭제 합니다.

```powershell
Get-ChildItem -Path cert:\LocalMachine -DnsName *Fabrikam* | Remove-Item
```

### <a name="delete-private-keys-from-a-remote-computer"></a>원격 컴퓨터에서 개인 키 삭제

이 명령 시리즈는 원격 컴퓨터에서 위임을 사용하도록 설정하고, 인증서 및 연결된 개인 키를 삭제합니다. 원격 컴퓨터에서 개인 키를 삭제하려면 위임된 자격 증명을 사용해야 합니다.

Cmdlet을 사용 `Enable-WSManCredSSP` 하 여 S1 원격 컴퓨터의 클라이언트에서 CredSSP (Credential Security Service Provider) 인증을 사용 하도록 설정 합니다.
CredSSP는 대리 인증을 허용합니다.

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer S1
```

Cmdlet을 사용 `Connect-WSMan` 하 여 S1 컴퓨터를 로컬 컴퓨터의 WinRM 서비스에 연결 합니다. 이 명령이 완료 되 면 S1 컴퓨터가 PowerShell의 로컬 드라이브에 표시 됩니다 `WSMan:` .

```powershell
Connect-WSMan -ComputerName S1 -Credential Domain01\Admin01
```

이제 WSMan: 드라이브에서 Set-Item cmdlet을 사용 하 여 WinRM 서비스에 대 한 CredSSP 특성을 사용 하도록 설정할 수 있습니다.

```powershell
Set-Item -Path WSMan:\S1\Service\Auth\CredSSP -Value $true
```

Cmdlet을 사용 하 여 s1 컴퓨터에서 원격 세션을 시작 하 `New-PSSession` 고 CredSSP 인증을 지정 합니다. 세션을 `$s` 변수에 저장 합니다.

```powershell
$s  = New-PSSession S1 -Authentication CredSSP -Credential Domain01\Admin01
```

마지막으로, cmdlet을 사용 `Invoke-Command` 하 여 `Remove-Item` 변수의 세션에서 명령을 실행 `$s` 합니다. 이 `Remove-Item` 명령은 **deletekey** 매개 변수를 사용 하 여 지정 된 인증서와 함께 개인 키를 제거 합니다.

```powershell
Invoke-Command -Session $s { Remove-Item `
  -Path cert:\LocalMachine\My\D2D38EBA60CAA1C12055A2E1C83B15AD450110C2 `
  -DeleteKey
  }
```

### <a name="delete-expired-certificates"></a>만료 된 인증서 삭제

이 명령은 cmdlet의 **ExpiringInDays** 매개 변수 값을 0으로 사용 `Get-ChildItem` 하 여 만료 된 webhosting 저장소에서 인증서를 가져옵니다.

반환 된 인증서를 포함 하는 변수는 cmdlet으로 파이프 되어 해당 변수를 `Remove-Item` 삭제 합니다. 이 명령은 **deletekey** 매개 변수를 사용 하 여 인증서와 함께 개인 키를 삭제 합니다.

```powershell
$expired = Get-ChildItem cert:\LocalMachine\WebHosting -ExpiringInDays 0
$expired | Remove-Item -DeleteKey
```

## <a name="creating-certificates"></a>인증서 만들기

`New-Item`Cmdlet은 **인증서** 공급자에 새 인증서를 만들지 않습니다. [New-selfsignedcertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet을 사용 하 여 테스트용 인증서를 만듭니다.

## <a name="creating-certificate-stores"></a>인증서 저장소 만들기

Cert: 드라이브에서 `New-Item` cmdlet은 LocalMachine 저장소 위치에 인증서 저장소를 만듭니다. **Name** , **Path** , **WhatIf** 및 **Confirm** 매개 변수를 지원 합니다. 다른 모든 매개 변수는 무시됩니다. 이 명령은 새 인증서 저장소를 나타내는 **system.security.cryptography.x509certificates.x509certificate2** 를 반환 합니다.

이 명령은 LocalMachine 저장소 위치에서 이름이 "CustomStore"인 새 인증서 저장소를 만듭니다.

```powershell
New-Item -Path cert:\LocalMachine\CustomStore
```

### <a name="create-a-new-certificate-store-on-a-remote-computer"></a>원격 컴퓨터에 새 인증서 저장소 만들기

이 명령은 Server01 컴퓨터의 LocalMachine 저장소 위치에 이름이 "HostingStore"인 새 인증서 저장소를 만듭니다.

이 명령은 cmdlet을 사용 `Invoke-Command` 하 여 `New-Item` Server01 컴퓨터에서 명령을 실행 합니다. 이 명령은 새 인증서 저장소를 나타내는 **system.security.cryptography.x509certificates.x509certificate2** 를 반환 합니다.

```powershell
Invoke-Command { New-Item -Path cert:\LocalMachine\CustomStore } `
  -ComputerName Server01
```

## <a name="creating-client-certificates-for-ws-man"></a>WS-Man에 대 한 클라이언트 인증서 만들기

이 명령은 **ws-management** 클라이언트에서 사용할 수 있는 **ClientCertificate** 항목을 만듭니다. 새 **ClientCertificate** 가 **ClientCertificate** 디렉터리 아래에 "ClientCertificate_1234567890"로 표시 됩니다. 모든 매개 변수는 필수 사항입니다. **발급자** 는 발급자 인증서의 손 도장 (thumbprint) 이어야 합니다.

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* -Credential $cred
```

## <a name="deleting-certificate-stores"></a>인증서 저장소 삭제

### <a name="delete-a-certificate-store-from-a-remote-computer"></a>원격 컴퓨터에서 인증서 저장소를 삭제 합니다.

이 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Remove-Item` S1 및 S2 컴퓨터에서 명령을 실행 합니다. 이 명령에는 저장소를 `Remove-Item` 삭제 하기 전에 저장소에서 인증서를 삭제 하는 **재귀** 매개 변수가 포함 되어 있습니다.

```powershell
Invoke-Command { Remove-Item -Path cert:\LocalMachine\TestStore -Recurse } `
  -ComputerName S1, S2
```

## <a name="dynamic-parameters"></a>동적 매개 변수

동적 매개 변수는 PowerShell 공급자가 추가 하는 cmdlet 매개 변수 이며, 공급자 사용 드라이브에서 cmdlet을 사용 하는 경우에만 사용할 수 있습니다. 이러한 매개 변수는 인증서 공급자의 모든 하위 디렉터리에서 유효 하지만 인증서에만 적용 됩니다.

> [!NOTE]
> 속성에 대해 필터링을 수행 하는 매개 변수도 `EnhancedKeyUsageList` 빈 속성 값을 가진 항목을 반환 `EnhancedKeyUsageList` 합니다.
> 빈 **EnhancedKeyUsageList** 있는 인증서를 모든 용도로 사용할 수 있습니다.

다음 인증서 공급자 매개 변수가 PowerShell 6.0에서 제거 되었습니다.

- DNSName
- DocumentEncryptionCert
- EKU
- ExpiringInDays
- SSLServerAuthentication

### <a name="codesigningcert-systemmanagementautomationswitchparameter"></a>CodeSigningCert를 <>

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

이 매개 변수는 **EnhancedKeyUsageList** 속성 값에 "코드 서명"이 있는 인증서를 가져옵니다.

### <a name="deletekey-systemmanagementautomationswitchparameter"></a>DeleteKey를 <>

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)

이 매개 변수는 인증서를 삭제할 때 연결 된 개인 키를 삭제 합니다.

> [!IMPORTANT]
> 원격 컴퓨터의 저장소에 있는 사용자 인증서와 연결 된 개인 키를 삭제 하려면 `Cert:\CurrentUser` 위임 된 자격 증명을 사용 해야 합니다. `Invoke-Command`Cmdlet은 **CredSSP** 매개 변수를 사용 하 여 자격 증명 위임을 지원 합니다. `Remove-Item`및 자격 증명 위임을 사용 하기 전에 보안 위험을 고려해 야 합니다 `Invoke-Command` .

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

### <a name="itemtype-string"></a>ItemType \<String\>

이 매개 변수를 사용 하 여에서 만든 항목의 형식을 지정할 수 있습니다 `New-Item` .

드라이브에는 `Certificate` 다음 값을 사용할 수 있습니다.

- 인증서 공급자
- 인증서
- 스토어
- StoreLocation

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="script-properties"></a>스크립트 속성

인증서를 쉽게 검색 하 고 관리할 수 있도록 인증서를 나타내는 새 스크립트 속성이 **x509Certificate2** 개체에 추가 되었습니다.

- `DnsNameList`: 속성을 채우기 위해 `DnsNameList` 인증서 공급자는 SAN (SubjectAlternativeName) 확장의 DNSName 항목에서 콘텐츠를 복사 합니다. SAN 확장이 비어 있으면 속성은 인증서의 제목 필드에 있는 내용으로 채워집니다.

- `EnhancedKeyUsageList`: 속성을 채우기 위해 `EnhancedKeyUsageList` 인증서 공급자는 인증서에 있는 EKU (EnhancedKeyUsage) 필드의 OID 속성을 복사 하 여 친숙 한 이름을 만듭니다.

- `SendAsTrustedIssuer`: 속성을 채우기 위해 `SendAsTrustedIssuer` 인증서 공급자는 `SendAsTrustedIssuer` 인증서에서 속성을 복사 합니다.  자세한 내용은 [클라이언트 인증에 대 한 신뢰할 수 있는 발급자 관리](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers)를 참조 하세요.

이러한 새 기능을 통해 DNS 이름과 만료 날짜를 기준으로 인증서를 검색하고, EKU(확장된 키 사용) 속성의 값으로 클라이언트 및 서버 인증 인증서를 구분할 수 있습니다.

## <a name="using-the-pipeline"></a>파이프라인 사용

공급자 cmdlet은 파이프라인 입력을 허용 합니다. 파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.
공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.

## <a name="getting-help"></a>도움말 보기

Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.

파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` 의 매개 변수를 사용 `Get-Help` 하 여 파일 시스템 드라이브를 지정 합니다.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path cert:
```

## <a name="see-also"></a>참고 항목

[about_Providers](../../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Signing](../../Microsoft.PowerShell.Core/About/about_Signing.md)

[Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)

[Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[Get-PfxCertificate](xref:Microsoft.PowerShell.Security.Get-PfxCertificate)

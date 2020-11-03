---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsessionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSessionOption
ms.openlocfilehash: 6d926200ae923157c0b7d7556ef13400036b8437
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212418"
---
# New-CimSessionOption

## 개요
New-CimSession cmdlet에 대 한 고급 옵션을 지정 합니다.

## SYNTAX

### ProtocolTypeSet (기본값)

```
New-CimSessionOption [-Protocol] <ProtocolType> [-UICulture <CultureInfo>] [-Culture <CultureInfo>]
 [<CommonParameters>]
```

### WSManParameterSet

```
New-CimSessionOption [-NoEncryption] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-EncodePortInServicePrincipalName] [-Encoding <PacketEncoding>] [-HttpPrefix <Uri>]
 [-MaxEnvelopeSizeKB <UInt32>] [-ProxyAuthentication <PasswordAuthenticationMechanism>]
 [-ProxyCertificateThumbprint <String>] [-ProxyCredential <PSCredential>] [-ProxyType <ProxyType>]
 [-UseSsl] [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

### DcomParameterSet

```
New-CimSessionOption [-Impersonation <ImpersonationType>] [-PacketIntegrity] [-PacketPrivacy]
 [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

## 설명

`New-CimSessionOption`Cmdlet은 CIM 세션 옵션 개체의 인스턴스를 만듭니다. Cim 세션 옵션 개체를 cmdlet에 대 한 입력으로 사용 하 여 `New-CimSession` cim 세션의 옵션을 지정할 수 있습니다.

이 cmdlet에는 두 개의 매개 변수 집합, 즉 WsMan 옵션과 DCOM (Distributed Component Object Model) 옵션에 대 한 매개 변수 집합이 있습니다. 사용 하는 매개 변수에 따라 cmdlet은 DCOM 세션 옵션의 인스턴스를 반환 하거나 WsMan 세션 옵션을 반환 합니다.

## 예제

### 예제 1: DCOM에 대 한 CIM 세션 옵션 개체 만들기

이 예에서는 DCOM 프로토콜에 대 한 CIM 세션 옵션 개체를 만들고 라는 변수에 저장 `$so` 합니다. 그런 다음 변수의 내용이 cmdlet에 전달 됩니다 `New-CimSession` .
`New-CimSession` 그런 다음는 변수에 정의 된 옵션을 사용 하 여 Server01 라는 원격 서버를 사용 하 여 새 CIM 세션을 만듭니다.

```powershell
$so = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server01 -SessionOption $so
```

### 예제 2: WsMan에 대 한 CIM 세션 옵션 개체 만들기

이 예에서는 WsMan 프로토콜에 대 한 CIM 세션 옵션 개체를 만듭니다. 개체는 **proxyauthentication** 매개 변수로 지정 된 **Kerberos** 의 인증 모드에 대 한 구성, **ProxyCredential** 매개 변수로 지정 된 자격 증명을 포함 하 고, CA 검사를 건너뛰고 CN 검사를 건너뛰고 SSL을 사용 하도록 지정 합니다.

```powershell
New-CimSessionOption -ProxyAuthentication Kerberos -ProxyCredential $cred -SkipCACheck -SkipCNCheck -UseSsl
```

### 예제 3: 지정 된 문화권을 사용 하 여 CIM 세션 옵션 개체 만들기

```powershell
New-CimSessionOption -Culture Fr-Fr -Protocol Wsman
```

이 예에서는 CIM 세션에 사용 되는 문화권을 지정 합니다. 기본적으로 클라이언트의 문화권은 작업을 수행할 때 사용 됩니다. 그러나 **culture** 매개 변수를 사용 하 여 기본 문화권을 재정의할 수 있습니다.

## PARAMETERS

### -문화권

CIM 세션에 사용할 사용자 인터페이스 문화권을 지정 합니다. 다음 형식 중 하나를 사용 하 여이 매개 변수에 대 한 값을 지정 합니다.

- `<languagecode2>-<country/regioncode2>`"En-us"와 같은 형식의 문화권 이름입니다.
- **CultureInfo** 개체를 포함 하는 변수입니다.
- [-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md) 와 같은 **CultureInfo** 개체를 가져오는 명령입니다.

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EncodePortInServicePrincipalName

Kerberos 연결이 서비스 사용자 이름 (SPN)에 서비스 포트 번호를 포함 하는 서비스에 연결 하 고 있음을 나타냅니다. 이 유형의 연결은 일반적이 지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

WsMan 프로토콜에 사용 되는 인코딩을 지정 합니다. 이 매개 변수에 허용 되는 값은 **Default** , **Utf8** 또는 **Utf16** 입니다.

```yaml
Type: Microsoft.Management.Infrastructure.Options.PacketEncoding
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Utf8, Utf16

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -HttpPrefix

컴퓨터 이름과 포트 번호 뒤에 HTTP URL의 부분을 지정 합니다. 이를 변경 하는 것은 일반적이 지 않습니다. 기본적으로이 매개 변수의 값은 **/wsman** 입니다.

```yaml
Type: System.Uri
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -가장

가장을 사용 하 여 WMI (WMI(Windows Management Instrumentation))에 대 한 DCOM 세션을 만듭니다.

이 매개 변수에 유효한 값은 다음과 같습니다.

- 기본값: DCOM은 일반적인 보안 협상 알고리즘을 사용 하 여 가장 수준을 선택할 수 있습니다.
- 없음: 클라이언트가 서버에 대해 익명입니다. 서버 프로세스는 클라이언트를 가장할 수 있지만 가장 토큰에는 정보가 포함 되어 있지 않으며 사용할 수 없습니다.
- 식별: 개체가 호출자의 자격 증명을 쿼리할 수 있도록 허용 합니다.
- Impersonate: 개체가 호출자의 자격 증명을 사용할 수 있습니다.
- Delegate: 개체가 다른 개체가 호출자의 자격 증명을 사용할 수 있도록 허용 합니다.

**가장** 을 지정 하지 않으면 Cmdlet은 `New-CimSession` **Impersonate** 값을 사용 합니다.

```yaml
Type: Microsoft.Management.Infrastructure.Options.ImpersonationType
Parameter Sets: DcomParameterSet
Aliases:
Accepted values: Default, None, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxEnvelopeSizeKB

어느 방향에서 든 WsMan XML 메시지의 크기 제한을 지정 합니다.

```yaml
Type: System.UInt32
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoEncryption

데이터 암호화가 해제 되도록 지정 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PacketIntegrity

WMI에 생성 된 DCOM 세션이 COM (구성 요소 개체 모델) _PacketIntegrity_ 기능을 사용 하도록 지정 합니다. 기본적으로 DCOM을 사용 하 여 만든 모든 CIM 세션은 **PacketIntegrity** 매개 변수를 **True** 로 설정 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PacketPrivacy

COM _PacketPrivacy_ 를 사용 하 여 WMI에 대 한 DCOM 세션을 만듭니다. 기본적으로 DCOM을 사용 하 여 만든 모든 CIM 세션은 **PacketPrivacy** 매개 변수를 **true** 로 설정 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

사용할 프로토콜을 지정합니다. 이 매개 변수에 허용 되는 값은 **DCOM** , **Default** 또는 **Wsman** 입니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimCmdlets.ProtocolType
Parameter Sets: ProtocolTypeSet
Aliases:
Accepted values: Dcom, Default, Wsman

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyAuthentication

프록시 확인에 사용할 인증 방법을 지정 합니다. 이 매개 변수에 허용 되는 값은 **Default** , **Digest** , **Negotiate** , **Basic** , **Kerberos** , **NtlmDomain** 또는 **CredSsp** 입니다.

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCertificateThumbprint

프록시 인증용 사용자 계정의 (x.509) 디지털 공개 키 인증서를 지정 합니다.
인증서의 인증서 지문을 입력합니다. 인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.

인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell Cert: 드라이브에서 또는 cmdlet을 사용 합니다.

```yaml
Type: System.String
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

프록시 인증에 사용할 자격 증명을 지정합니다. 다음 중 하나를 입력합니다.

- PSCredential 개체를 포함 하는 변수입니다.
- 와 같은 PSCredential 개체를 가져오는 명령입니다. `Get-Credential`

이 옵션을 설정 하지 않으면 자격 증명을 지정할 수 없습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyType

사용할 호스트 이름 확인 메커니즘을 지정 합니다. 이 매개 변수에 허용 되는 값은 **None** , **WinHttp** , **Auto** 또는 **internetexplorer** 입니다.

이 매개 변수의 기본값은 **Internetexplorer** 입니다.

```yaml
Type: Microsoft.Management.Infrastructure.Options.ProxyType
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: None, WinHttp, Auto, InternetExplorer

Required: False
Position: Named
Default value: InternetExplorer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipCACheck

HTTPS를 통해 연결할 때 클라이언트가 서버 인증서가 신뢰할 수 있는 CA (인증 기관)에 의해 서명 되었는지 확인 하지 않음을 나타냅니다.

원격 컴퓨터가 물리적으로 안전 하 고 격리 된 네트워크에 속해 있거나 원격 컴퓨터가 WinRM 구성에서 신뢰할 수 있는 호스트로 나열 되어 있는 경우와 같이 원격 컴퓨터를 다른 메커니즘을 사용 하 여 신뢰할 수 있는 경우에만이 매개 변수를 사용 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipCNCheck

서버의 인증서 CN (일반 이름)이 서버의 호스트 이름과 일치 하지 않아도 됨을 나타냅니다. 이 매개 변수는 HTTPS 프로토콜을 사용 하는 신뢰할 수 있는 컴퓨터의 원격 작업에만 사용 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipRevocationCheck

서버 인증서에 대 한 해지 확인을 건너뛰도록 지정 합니다. 이 매개 변수는 신뢰할 수 있는 컴퓨터에만 사용 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UICulture

CIM 세션에 사용할 사용자 인터페이스 문화권을 지정 합니다. 다음 형식 중 하나를 사용 하 여이 매개 변수에 대 한 값을 지정 합니다.

- `<languagecode2>-<country/regioncode2>`"En-us"와 같은 형식의 문화권 이름입니다.
- CultureInfo 개체를 포함 하는 변수입니다.
- 와 같은 CultureInfo 개체를 가져오는 명령 `Get-Culture` 입니다.

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseSsl

원격 컴퓨터에 대 한 연결을 설정 하는 데 SSL을 사용 해야 함을 나타냅니다. 기본적으로 SSL은 사용되지 않습니다. WsMan은 HTTP를 사용 하는 경우에도 네트워크를 통해 전송 되는 모든 콘텐츠를 암호화 합니다.

이 매개 변수를 사용 하 여 HTTP 대신 HTTPS의 추가 보호를 지정할 수 있습니다. 연결에 사용 되는 포트에서 SSL을 사용할 수 없는 경우이 매개 변수를 지정 하면 명령이 실패 합니다.

이 매개 변수는 **PacketPrivacy** 매개 변수가 지정 되지 않은 경우에만 사용 하는 것이 좋습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet은 입력 개체를 허용 하지 않습니다.

## 출력

### CIMSessionOption

이 cmdlet은 CIM 세션 옵션 정보를 포함 하는 개체를 반환 합니다.

## 참고

## 관련 링크

[Get-ChildItem](../microsoft.powershell.management/get-childitem.md)

[Get-Credential](../microsoft.powershell.security/get-credential.md)

[Get-Culture](../microsoft.powershell.utility/get-culture.md)

[Get-Item](../microsoft.powershell.management/get-item.md)

[New-CimSession](New-CimSession.md)

---
description: WSMan
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_wsman_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: WSMan 공급자
ms.openlocfilehash: 52a36a9246c3d98650eaeed352aa46fb67ed9bc0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220954"
---
# <a name="wsman-provider"></a>WSMan 공급자

## <a name="provider-name"></a>공급자 이름

WSMan

## <a name="drives"></a>드라이브

`WSMan:`

## <a name="short-description"></a>간단한 설명

WS-Management(Web Services for Management) 구성 정보에 대한 액세스를 제공합니다.

## <a name="detailed-description"></a>자세한 설명

PowerShell 용 **WSMan** 공급자를 사용 하 여 로컬 또는 원격 컴퓨터에서 WS-Management 구성 데이터를 추가, 변경, 지우기 및 삭제할 수 있습니다.

**WSMan** 공급자는 WS-Management 구성 설정의 논리적 그룹에 해당 하는 디렉터리 구조를 사용 하 여 PowerShell 드라이브를 노출 합니다. 이러한 그룹을 컨테이너라고 합니다.

Windows PowerShell 3.0부터 **WSMan** 공급자가 **OutputBufferingMode** 와 같은 세션 구성에 대 한 새 속성을 지원 하도록 업데이트 되었습니다. 세션 구성은 드라이브의 플러그 인 디렉터리에 항목으로 표시 되 `WSMan:` 고 속성은 각 세션 구성에서 항목으로 표시 됩니다.

**WSMan** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)

> [!NOTE]
> 드라이브의 명령을 사용 하 여 `WSMan:` 새 속성의 값을 변경할 수 있습니다. 그러나 `WSMan:` powershell 2.0에서 드라이브를 사용 하 여 Windows powershell 3.0에 도입 된 속성을 변경할 수는 없습니다.
> 오류가 생성 되지 않지만 이러한 설정을 변경 하는 데는 명령을 사용할 수 없습니다. Windows PowerShell 3.0에서 **WSMan** 드라이브를 사용 합니다.

### <a name="organization-of-the-wsman-drive"></a>WSMan: 드라이브 구성

- **클라이언트** : WS-Management 클라이언트의 다양 한 측면을 구성할 수 있습니다. 구성 정보는 레지스트리에 저장됩니다.

- **서비스** : WS-Management 서비스의 다양 한 측면을 구성할 수 있습니다.
  구성 정보는 레지스트리에 저장됩니다.
  > [!NOTE]
  > 경우에 따라 서비스 구성을 서버 구성이라고 합니다.

- **Shell** : 원격 셸 액세스 허용 설정 ( **AllowRemoteShellAccess** ) 및 허용 되는 최대 동시 사용자 수 ( **MaxConcurrentUsers** )와 같은 WS-Management 셸의 다양 한 측면을 구성할 수 있습니다.

- **수신기** : 수신기를 만들고 구성할 수 있습니다. 수신기는 메시지를 보내고 받을 WS-Management 프로토콜을 구현하는 관리 서비스입니다.

- **플러그 인** : 플러그 인은 다양 한 기능을 제공 하기 위해 WS-Management 서비스에서 로드 되 고 사용 됩니다. 기본적으로 PowerShell은 세 가지 플러그 인을 제공 합니다.
  - 이벤트 전달 플러그 인입니다.
  - Microsoft PowerShell 플러그 인입니다.
  - WMI(Windows Management Instrumentation) (WMI) 공급자 플러그 인입니다.
  이 세 가지 플러그 인은 이벤트 전달, 구성 및 WMI 액세스를 지원 합니다.

- **ClientCertificate** : 클라이언트 인증서를 만들고 구성할 수 있습니다.
  클라이언트 인증서는 WS-Management 클라이언트가 인증서 인증을 사용하도록 구성된 경우에 사용됩니다.

### <a name="directory-hierarchy-of-the-wsman-provider"></a>WSMan 공급자의 디렉터리 계층 구조

로컬 컴퓨터용 WSMan 공급자의 디렉터리 계층 구조는 다음과 같습니다.

```
WSMan:\localhost
--- Client
--- Service
--- Shell
--- Listener
------ <Specific_Listener>
--- Plugin
------ Event Forwarding Plugin
--------- InitializationParameters
--------- Resources
------------ Security
------ Microsoft.Powershell
--------- InitializationParameters
--------- Resources
------------ Security
------ WMI Provider
--------- InitializationParameters
--------- Resources
------------ Security
--- ClientCertificate
```

로컬 컴퓨터와 원격 컴퓨터의 WSMan 공급자 디렉터리 계층 구조는 동일합니다. 그러나 원격 컴퓨터의 구성 설정에 액세스하려면 [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)을 사용하여 원격 컴퓨터에 연결해야 합니다. 원격 컴퓨터에 연결되면 원격 컴퓨터의 이름이 공급자에 표시됩니다.

```
WSMan:\<Remote_Computer_Name>
```

## <a name="navigating-the-wsman-drive"></a>WSMan: 드라이브 탐색

이 명령은 cmdlet을 사용 하 여 `Set-Location` 현재 위치를 드라이브로 변경 `WSMan:` 합니다.

```powershell
Set-Location WSMan:
```

파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다. 예를 들어을 입력 합니다.

```powershell
Set-Location C:
```

### <a name="navigating-to-a-remote-system-store-location"></a>원격 시스템 저장소 위치로 이동

이 명령은 명령을 사용 하 여 `Set-Location` 현재 위치를 원격 시스템 저장소 위치의 루트 위치로 변경 합니다. 백슬래시 `\` 또는 슬래시를 사용 `/` 하 여 드라이브의 수준을 표시 `WSMan:` 합니다.

```powershell
Set-Location -Path  WSMan:\SERVER01
```

> [!NOTE]
> 위의 명령은 원격 시스템에 대한 연결이 이미 있다고 가정합니다.

## <a name="displaying-the-contents-of-the-wsman-drive"></a>WSMan: 드라이브의 콘텐츠 표시

이 명령은 cmdlet을 사용 하 여 `Get-Childitem` Localhost 저장소 위치의 WS-Management 저장소를 표시 합니다.

```powershell
Get-ChildItem -path WSMan:\Localhost
```

드라이브에 있는 경우 `WSMan:` 드라이브 이름을 생략할 수 있습니다.

이 명령은 cmdlet을 사용 하 여 `Get-Childitem` 원격 컴퓨터 "SERVER01" 저장소 위치에 WS-Management 저장소를 표시 합니다.

```powershell
Get-ChildItem -path WSMan:\SERVER01
```

> [!NOTE]
> 위의 명령은 원격 시스템에 대한 연결이 이미 있다고 가정합니다.

## <a name="setting-the-value-of-items-in-the--wsman-drive"></a>WSMAN: 드라이브의 항목 값 설정

Cmdlet을 사용 `Set-Item` 하 여 드라이브의 구성 설정을 변경할 수 있습니다 `WSMAN` . 다음 예에서는 "contoso.com" 접미사를 사용 하 여 모든 호스트를 허용 하도록 **TrustedHosts** 값을 설정 합니다.

```powershell
# You do not need to specify the -Path parameter name when using Set-Item.
PS WSMAN:\localhost\Client> Set-Item .\TrustedHosts -Value "*.contoso.com"
```

`Set-Item`Cmdlet은 `-Concatenate` 값을 변경 하는 대신 추가 하는 추가 매개 변수를 지원 합니다. 다음 예에서는에 저장 된 이전 값에 새 값 "*. domain2.com"를 추가 합니다. `TrustedHost:`

```powershell
Set-Item WSMAN:\localhost\Client\TrustedHosts *.domain2.com -Concatenate
```

## <a name="creating-items-in-the-wsman-drive"></a>WSMAN: 드라이브에 항목 만들기

### <a name="creating-a-new-listener"></a>새 수신기 만들기

`New-Item`Cmdlet은 공급자 드라이브에 항목을 만듭니다. 각 공급자에는 만들 수 있는 다양 한 항목 유형이 있습니다. 드라이브에서 `WSMAN:` 원격 요청을 수신 하 고 응답 하도록 구성 하는 *수신기* 를 만들 수 있습니다. 다음 명령은 cmdlet을 사용 하 여 새 HTTP 수신기를 만듭니다 `New-Item` .

```powershell
New-Item -Path WSMan:\localhost\Listener -Address * -Transport HTTP -force
```

### <a name="creating-a-new-plug-in"></a>새 플러그 인 만들기

이 명령은 WS-Management 서비스용 플러그 인을 만듭니다(등록).

```powershell
New-Item -Path WSMan:\localhost\Plugin `
         -Plugin TestPlugin `
         -FileName %systemroot%\system32\WsmWmiPl.dll `
         -Resource http://schemas.dmtf.org/wbem/wscim/2/cim-schema `
         -SDKVersion 1 `
         -Capability "Get","Put","Invoke","Enumerate" `
         -XMLRenderingType text
```

### <a name="creating-a-new-resource-entry"></a>새 리소스 항목 만들기

이 명령은 TestPlugin의 Resources 디렉터리에 리소스 항목을 만듭니다. 이 명령은 TestPlugin이 별도의 명령을 사용 하 여 생성 된 것으로 가정 합니다.

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\Resources `
         -ResourceUri http://schemas.dmtf.org/wbem/wscim/3/cim-schema `
         -Capability "Enumerate"

```

### <a name="creating-a-new-security-entry-for-a-resource"></a>리소스에 대 한 새 보안 항목 만들기

이 명령은 Resource_5967683(특정 리소스)의 Security 디렉터리에 보안 항목을 만듭니다. 이 명령은 리소스 항목이 별도의 명령을 사용 하 여 생성 된 것으로 가정 합니다.

```powershell
$path = "WSMan:\localhost\Plugin\TestPlugin\Resources\Resource_5967683"
New-Item -Path $path\Security `
         -Sddl "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GWGX;;;WD)"
```

### <a name="creating-a-new-client-certificate"></a>새 클라이언트 인증서 만들기

이 명령은 WS-Management 클라이언트에서 사용할 수 있는 **ClientCertificate** 항목을 만듭니다. 새 **ClientCertificate** 가 **ClientCertificate** 디렉터리 아래에 "ClientCertificate_1234567890"로 표시 됩니다. 모든 매개 변수는 필수 사항입니다. **발급자** 는 발급자 인증서의 손 도장 (thumbprint) 이어야 합니다.

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* `
         -Credential $cred;
```

### <a name="creating-a-new-initialization-parameter"></a>새 초기화 매개 변수 만들기

이 명령은 "InitializationParameters" 디렉터리에 "testparametername" 이라는 초기화 매개 변수를 만듭니다. 이 명령은 "TestPlugin"이 별도의 명령을 사용 하 여 생성 된 것으로 가정 합니다.

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\InitializationParameters `
         -ParamName testparametername `
         -ParamValue testparametervalue
```

## <a name="dynamic-parameters"></a>동적 매개 변수

동적 매개 변수는 PowerShell 공급자가 추가 하는 cmdlet 매개 변수 이며, 공급자 사용 드라이브에서 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.

### <a name="address-string"></a>Address \<String\>

이 수신기가 만들어진 주소를 지정합니다. 값은 다음 중 하나일 수 있습니다.

- 리터럴 문자열 "*"입니다. 와일드 카드 문자 ( `*` )를 사용 하면 명령이 모든 네트워크 어댑터에서 모든 IP 주소를 바인딩합니다.
- 리터럴 문자열 "IP:"와 IPv4 점으로 구분 된 IPv4 형식의 유효한 IP 주소, 즉 IPv6 복제 된 16 진수 형식입니다.
- 리터럴 문자열 "MAC:" 뒤에 어댑터의 MAC 주소가 옵니다.
  예: MAC: 32-a3-58 -90-cc.

> [!NOTE]
> Address 값은 수신기를 만들 때 설정됩니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="capability-enumeration"></a>Capability \<Enumeration\>

*플러그* 인을 사용 하는 경우이 매개 변수는이 URI (Uniform resource Identifier)에서 지원 되는 작업을 지정 합니다. URI가 지원하는 각 작업 유형에 대해 하나의 항목을 만들어야 합니다. 작업에서 지 원하는 경우 지정 된 작업에 유효한 특성을 지정할 수 있습니다.

이러한 특성에는 **Supportsfiltering** And **supportsfiltering** 가 포함 됩니다.

- **만들기** : URI에서 만들기 작업이 지원 됩니다.
  - **Supportfragment** 특성은 만들기 작업에서 개념을 지 원하는 경우에 사용 됩니다.
  - **Supportfiltering** 특성은 만들기 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.
  > [!NOTE]
  > Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.
- **삭제** : URI에서 삭제 작업이 지원 됩니다.
  - **Supportfragment** 특성은 Delete 작업에서 개념을 지 원하는 경우에 사용 됩니다.
  - **Supportfiltering** 특성은 삭제 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.
  > [!NOTE]
  > Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.
- **열거** : URI에 대해 열거 작업이 지원 됩니다.
  - **Supportfragment** 특성은 열거 작업에 지원 되지 않으므로 False로 설정 해야 합니다.
  - **Supportfiltering** 특성이 유효 하 고 플러그 인에서 필터링을 지 원하는 경우이 특성을 "True"로 설정 해야 합니다.
  > [!NOTE]
  > Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.
- **Get** : get 작업은 URI에서 지원 됩니다.
  - **Supportfragment** 특성은 Get 작업에서 개념을 지 원하는 경우에 사용 됩니다.
  - **Supportfiltering** 특성은 Get 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.
  > [!NOTE]
  > Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.
- **Invoke** : 호출 작업은 URI에서 지원 됩니다.
  - **Supportfragment** 특성은 호출 작업에 지원 되지 않으므로 False로 설정 해야 합니다.
  - **Supportfiltering** 특성이 잘못 되었으며 "False"로 설정 되어야 합니다.
  > [!NOTE]
  > Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.
- **Put** : URI에서 put 작업이 지원 됩니다.
  - **Supportfragment** 특성은 Put 작업에서 개념을 지 원하는 경우에 사용 됩니다.
  - **Supportfiltering** 특성은 Put 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.
  > [!NOTE]
  > Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.
- **구독** : URI에서 구독 작업이 지원 됩니다.
  - **Supportfragment** 특성은 구독 작업에 대해 지원 되지 않으므로 False로 설정 해야 합니다.
  - **Supportfiltering** 특성은 구독 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.
  > [!NOTE]
  > Shell 작업도 지원되는 경우 이 작업은 URI에 대해 유효하지 않습니다.
- **셸** : URI에서 셸 작업이 지원 됩니다.
  - **Supportfragment** 특성은 셸 작업에 대해 지원 되지 않으므로 "False"로 설정 해야 합니다.
  - **Supportfiltering** 특성은 셸 작업에 유효 하지 않으므로 "False"로 설정 해야 합니다.
  > [!NOTE]
  > 다른 작업도 지원 되는 경우이 작업은 URI에 대해 유효 하지 않습니다.
  > [!NOTE]
  > URI에 대해 Shell 작업이 구성된 경우 Get, Put, Create, Delete, Invoke 및 Enumerate 작업은 셸을 관리하기 위해 WS-Management(WinRM) 서비스에서 내부적으로 처리됩니다. 따라서 플러그 인에서 작업을 처리할 수 없습니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="certificatethumbprint-string"></a>CertificateThumbprint \<String\>

서비스 인증서의 지문을 지정합니다.

이 값은 인증서의 Thumbprint 필드에 있는 2자리 16진수 값의 문자열을 나타냅니다. 이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다. 인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 인증서는 로컬 사용자 계정으로만 매핑될 수 있고 도메인 계정에는 사용할 수 없습니다. 인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell 드라이브에서 또는 cmdlet을 사용 `Cert:` 합니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="enabled-boolean"></a>Enabled \<Boolean\>

수신기를 사용하도록 설정할지 또는 사용하지 않도록 설정할지를 지정합니다. 기본값은 true입니다.

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="filename-plugin-string"></a>FileName (Plugin) \<String\>

작업 플러그 인의 파일 이름을 지정 합니다. 이 항목에 포함 된 모든 환경 변수는 요청이 수신 될 때 사용자의 컨텍스트에서 확장 됩니다. 각 사용자는 동일한 환경 변수의 서로 다른 버전을 가질 수 있기 때문에 각 사용자는 다른 플러그 인을 가질 수 있습니다. 이 항목은 비워 둘 수 없으며 올바른 플러그 인을 가리켜야 합니다.

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="hostname-string"></a>HostName \<String\>

WS-Management(WinRM) 서비스가 실행되는 컴퓨터의 호스트 이름을 지정합니다.

값은 정규화된 도메인 이름, IPv4 또는 IPv6 리터럴 문자열 또는 와일드카드 문자여야 합니다.

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="issuer-string"></a>Issuer \<String\>

인증서를 발급한 인증 기관의 이름을 지정합니다.

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="plugin--ws-management-plug-ins-are-native-dynamic-link-libraries-dlls"></a>플러그 인 \<\> WS-Management 플러그 인은 네이티브 dll (동적 연결 라이브러리)입니다.

WS-Management의 기능을 연결 하 고 확장 합니다. WSW-Management 플러그 인 API는 지원 되는 리소스 Uri 및 작업에 대 한 특정 Api를 구현 하 여 사용자가 플러그 인을 작성할 수 있도록 하는 기능을 제공 합니다. 플러그 인이 WS-Management(WinRM) 서비스 또는 IIS(인터넷 정보 서비스)에 대해 구성된 경우 각각 WS-Management 호스트 또는 IIS 호스트에 로드됩니다. 원격 요청은 작업을 수행하기 위해 이러한 플러그 인 진입점에 라우팅됩니다.

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="port-unsigned-short-integer"></a>Port \<Unsigned Short Integer\>

이 수신기가 만들어지는 TCP 포트를 지정합니다. 1에서 65535 사이의 값을 지정할 수 있습니다.

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a>Resource \<String\>

고유한 유형의 관리 작업 또는 값을 나타내는 엔드포인트를 지정합니다. 서비스는 하나 이상의 리소스를 표시하고, 일부 리소스는 둘 이상의 인스턴스를 가질 수 있습니다. 관리 리소스는 WMI 클래스 또는 데이터베이스 테이블과 유사하며, 인스턴스는 클래스 인스턴스나 테이블의 행과 유사합니다. 예를 들어 **Win32_LogicalDisk** 클래스는 리소스를 나타냅니다. `Win32_LogicalDisk="C:\\"` 는 리소스의 특정 인스턴스입니다.

URI(Uniform Resource Identifier)에는 접두사와 리소스 경로가 포함됩니다.
다음은 그 예입니다. 

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a>Resource \<String\>

디스크 또는 프로세스와 같은 컴퓨터의 특정 리소스 유형을 식별하는 URI(Uniform Resource Identifier)를 지정합니다.

URI는 접두사와 리소스 경로로 구성됩니다. 다음은 그 예입니다. 

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sdkversion-string"></a>SDKVersion \<String\>

WS-Management 플러그 인 SDK의 버전을 지정합니다. 유일 하 게 유효한 값은
1.

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="subject-string"></a>Subject \<String\>

인증서로 식별되는 엔티티를 지정합니다.

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="transport-string"></a>Transport \<String\>

WS-Management 프로토콜 요청 및 응답을 보내고 받는 데 사용할 전송을 지정합니다. 값은 HTTP 또는 HTTPS여야 합니다.

참고: 전송 값은 수신기를 만들 때 설정 됩니다.

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="uri-string"></a>URI \<String\>

Sddl 매개 변수의 값을 기준으로 액세스 권한이 부여되는 URI를 식별합니다.

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="urlprefix-string"></a>URLPrefix \<String\>

HTTP 또는 HTTPS 요청을 수락할 URL 접두사입니다. 이는 문자 `[a-z]` , `[A-Z]` , `[9-0]` , 밑줄 ( `_` ) 및 백슬래시 ( `/` )만 포함 하는 문자열입니다. 문자열은 백슬래시 ()로 시작 하거나 끝나지 않아야 합니다 `/` . 예를 들어 컴퓨터 이름이 "SampleComputer" 인 경우 WS-Management 클라이언트는 `http://SampleMachine/URLPrefix` 대상 주소에를 지정 합니다.

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="value-string"></a>Value \<String\>

구성 옵션을 지정하는 데 사용되는 플러그 인 관련 값인 초기화 매개 변수 값을 지정합니다.

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="xmlrenderingtype-string"></a>XMLRenderingType \<String\>

**WSMAN_DATA** 개체를 통해 XML이 플러그 인에 전달 되는 형식을 지정 합니다. 다음은 유효한 값입니다.

- Text: 들어오는 XML 데이터는 XML을 **Pcwstr** 메모리 버퍼로 나타내는 **WSMAN_DATA_TYPE_TEXT** 구조에 포함 됩니다.
- XMLReader: 들어오는 XML 데이터는 XML을 "WebServices" 헤더 파일에 정의 된 **XmlReader** 개체로 나타내는 **WSMAN_DATA_TYPE_WS_XML_READER** 구조에 포함 되어 있습니다.

#### <a name="cmdlets-supported"></a>지원되는 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a>파이프라인 사용

공급자 cmdlet은 파이프라인 입력을 허용 합니다. 파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.
공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.

## <a name="getting-help"></a>도움말 보기

Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.

파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 의 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path wsman:
```

## <a name="see-also"></a>참고 항목

[about_Providers](../../Microsoft.PowerShell.Core/About/about_Providers.md)

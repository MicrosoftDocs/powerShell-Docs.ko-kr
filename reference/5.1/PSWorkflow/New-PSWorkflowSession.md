---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowSession
ms.openlocfilehash: 995dd8a6df3ac8ebd7a204d2aefef3fa6aa71e14
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213362"
---
# New-PSWorkflowSession

## 개요
워크플로 세션을 만듭니다.

## SYNTAX

```
New-PSWorkflowSession [[-ComputerName] <String[]>] [-Credential <Object>] [-Name <String[]>] [-Port <Int32>]
 [-UseSSL] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-EnableNetworkAccess]
 [<CommonParameters>]
```

## 설명

`New-PSWorkflowSession`Cmdlet은 Windows PowerShell 워크플로를 실행 하기 위해 특별히 설계 된 **PSSession** (사용자 관리 세션)을 만듭니다. 이 cmdlet은 워크플로에 필요한 스크립트, 형식 및 서식 지정 파일과 옵션이 포함된 Microsoft.PowerShell.Workflow 세션 구성을 사용합니다.

`New-PSWorkflowSession`또는 해당 별칭 ()을 사용할 수 있습니다 `nwsn` .

또한 이 명령에 워크플로 일반 매개 변수를 추가할 수 있습니다. 워크플로 일반 매개 변수에 대 한 자세한 내용은을 참조 하십시오 [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md)

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 원격 컴퓨터에서 워크플로 세션 만들기

이 예제에서는 ServerNode01 원격 컴퓨터에 **Workflowtests** 세션을 만듭니다.

```powershell
$params = @{
    ComputerName = "ServerNode01"
    Name = "WorkflowTests"
    SessionOption = (New-PSSessionOption -OutputBufferingMode Drop)
}
New-PSWorkflowSession @params
```

**Sessionoption** 매개 변수 값은 `New-PSSessionOption` 세션에서 **Drop** 으로 출력 버퍼링 모드를 설정 하는 명령입니다.

### 예 2: 여러 원격 컴퓨터에 워크플로 세션 만들기

이 예제에서는 ServerNode01 및 Server12 컴퓨터에 워크플로 세션을 만듭니다. 이 명령은 **Credential** 매개 변수를 사용하여 도메인 관리자 권한으로 실행합니다.

```powershell
"ServerNode01", "Server12" |
    New-PSWorkflowSession -Name WorkflowSession -Credential Domain01\Admin01 -ThrottleLimit 150
```

이 명령은 **ThrottleLimit** 매개 변수를 사용하여 명령당 제한 한도를 150으로 늘립니다.
이 값은 **Microsoft. PowerShell 워크플로** 세션 구성에 설정 된 기본 제한 제한인 100 보다 우선 합니다.

## PARAMETERS

### -ApplicationName

연결 URI의 애플리케이션 이름 세그먼트를 지정합니다.

기본값은 `$PSSessionApplicationName` 로컬 컴퓨터의 기본 설정 변수 값입니다. 이 기본 설정 변수를 정의하지 않으면 WSMAN이 기본값으로 사용됩니다. 이 값은 대부분의 사용에 적합합니다. 자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.

WinRM 서비스는 애플리케이션 이름을 사용하여 연결 요청을 제공하는 수신기를 선택합니다.
이 매개 변수 값은 원격 컴퓨터에 있는 수신기의 **URLPrefix** 속성 값과 일치해야 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -인증

사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본값
- Basic
- Credssp
- 다이제스트
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

기본값은 Default입니다.

CredSSP 인증은 windows Vista, Windows Server 2008 이상 버전의 Windows 운영 체제 에서만 사용할 수 있습니다.

이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)를 참조 하세요.

> [!CAUTION]
> 사용자 자격 증명을 인증을 위해 원격 컴퓨터에 전달 하는 CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다. 인증서의 인증서 지문을 입력합니다.

인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.

인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` Windows PowerShell Cert: 드라이브에서 cmdlet 또는 cmdlet을 사용 합니다.

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

### -ComputerName

지정 된 컴퓨터에 대 한 영구 연결 ( **PSSession** )을 만듭니다. 여러 컴퓨터 이름을 입력 하면 Windows PowerShell에서 각 컴퓨터에 대해 **하나씩 여러 개의 pssession을 만듭니다** . 기본값은 로컬 컴퓨터입니다.

하나 이상의 원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요. 로컬 컴퓨터를 지정 하려면 컴퓨터 이름, localhost 또는 점 (.)을 입력 합니다. 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름이 필요합니다. 컴퓨터 이름을 따옴표로 묶을 수도 있습니다 `New-PSWorkflowSession` .

**ComputerName** 매개 변수 값에 IP 주소를 사용 하려면 명령에 **Credential** 매개 변수를 포함 해야 합니다. 또한 HTTPS 전송을 사용하도록 컴퓨터를 구성하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 WinRM TrustedHosts 목록에 포함해야 합니다. TrustedHosts 목록에 컴퓨터 이름을 추가 하는 방법에 대 한 지침은 [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)의 "신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법"을 참조 하십시오.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다. User01, Domain01\User01 또는와 같은 사용자 이름을 입력 User@Domain.com 하거나, cmdlet에서 반환 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .

사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

이 cmdlet이 루프백 세션에 대화형 보안 토큰을 추가 함을 나타냅니다. 대화형 토큰을 사용하면 다른 컴퓨터에서 데이터를 가져오는 명령을 루프백 세션에서 실행할 수 있습니다. 예를 들어 원격 컴퓨터에서 로컬 컴퓨터로 XML 파일을 복사하는 세션에서 명령을 실행할 수 있습니다.

루프백 세션은 동일한 컴퓨터에서 시작 하 여 종료 되는 **PSSession** 입니다. 루프백 세션을 만들려면 **ComputerName** 매개 변수를 지정 하거나 해당 값을 dot, localhost 또는 로컬 컴퓨터 이름으로 설정 하지 마세요.

기본적으로 루프백 세션은 원격 컴퓨터를 인증 하는 데 충분 한 권한을 제공 하지 않을 수 있는 네트워크 토큰을 포함 하는 생성 됩니다.

**EnableNetworkAccess** 매개 변수는 루프백 세션에서만 유효합니다. 원격 컴퓨터에서 세션을 만들 때 **EnableNetworkAccess** 매개 변수를 지정 하면 명령이 성공 하지만 매개 변수는 무시 됩니다.

또한 세션 자격 증명을 다른 컴퓨터에 위임하는 **CredSSP** 매개 변수의 **Authentication** 값을 사용하여 루프백 세션에서 원격 액세스를 허용할 수도 있습니다.

악의적인 액세스 로부터 컴퓨터를 보호 하기 위해 **EnableNetworkAccess** 매개 변수를 사용 하 여 만든 대화형 토큰을 포함 하는 분리 된 루프백 세션은 세션을 만든 컴퓨터 에서만 다시 연결할 수 있습니다. CredSSP 인증을 사용하는 연결이 끊어진 세션은 다른 컴퓨터에서 다시 연결할 수 있습니다. 자세한 내용은 `Disconnect-PSSession` cmdlet을 참조하세요.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

워크플로 세션의 이름을 지정합니다. 다른 cmdlet (예: 및)에서이 이름을 사용할 수 있습니다 `Get-PSSession` `Enter-PSSession` . 이 이름은 컴퓨터나 현재 세션에서 고유하지 않아도 됩니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Session#
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

이 명령에 사용되는 원격 컴퓨터의 네트워크 포트를 지정합니다. 원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다. 기본 포트는 5985 (HTTP의 경우 WinRM 포트) 및 5986 (HTTPS의 경우 WinRM 포트)입니다.

다른 포트를 사용 하기 전에 해당 포트에서 수신 대기 하도록 원격 컴퓨터의 WinRM 수신기를 구성 해야 합니다. 다음 명령을 사용하여 수신기를 구성합니다.

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

필요한 경우가 아니면 **Port** 매개 변수를 사용하지 마세요. 명령의 포트 설정은 이 명령이 실행되는 모든 컴퓨터나 세션에 적용됩니다. 대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

세션에 대 한 고급 옵션을 지정 합니다. Cmdlet을 사용 하 여 만든 것과 같은 **Sessionoption** 개체를 입력 합니다 `New-PSSessionOption` .

옵션의 기본값은 기본 설정 `$PSSessionOption` 변수의 값 (설정 된 경우)에 따라 결정 됩니다. 그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.

세션 옵션 값은 기본 설정 변수 및 세션 구성에 설정 된 세션의 기본값 보다 우선 적용 `$PSSessionOption` 됩니다. 그러나 이러한 값은 세션 구성에 설정된 최대값, 할당량 또는 제한보다 우선하지 않습니다. 세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)를 참조 하세요.

기본값을 포함 하 여 세션 옵션에 대 한 자세한 내용은을 참조 하십시오 `New-PSSessionOption` .
기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.
이 매개 변수를 생략 하거나 값 0을 입력 하면 **Microsoft. PowerShellWorkflow** 세션 구성 100에 대 한 기본값이 사용 됩니다.

제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

이 cmdlet이 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 함을 나타냅니다. 기본적으로 SSL은 사용되지 않습니다.

WS-Management는 네트워크를 통해 전송되는 모든 Windows PowerShell 내용을 암호화합니다. **UseSSL** 매개 변수는 HTTP 연결 대신 HTTPS 연결을 통해 데이터를 전송 하는 추가 보호 기능입니다.

이 매개 변수를 지정 하지만 명령에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### Runspace [], System.string이 있습니다.

이 cmdlet에 세션 또는 컴퓨터 이름을 파이프 하 여 지정할 수 있습니다.

## 출력

### Runspace입니다.

## 참고

`New-PSWorkflowSession`명령은 다음 명령과 동일 합니다.

`New-PSSession -ConfigurationName Microsoft.PowerShell.Workflow`

## 관련 링크

[Disconnect-PSSession](../Microsoft.PowerShell.Core/Disconnect-PSSession.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-PSTransportOption](../Microsoft.PowerShell.Core/New-PSTransportOption.md)

[Register-PSSessionConfiguration](../Microsoft.PowerShell.Core/Register-PSSessionConfiguration.md)

[about_PSSessions](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)

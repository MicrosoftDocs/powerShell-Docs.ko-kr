---
description: 이 항목에서는 모든 Windows PowerShell 워크플로 명령에 유효한 매개 변수에 대해 설명 합니다. Windows PowerShell 엔진은 워크플로에 추가 하므로 워크플로를 통해 이러한 매개 변수를 사용할 수 있으며 작성자가 만든 워크플로에서 자동으로 사용 하도록 설정 됩니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflowcommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WorkflowCommonParameters
ms.openlocfilehash: c371666d4f58386848e7ef715b7c804dc1e8f28e
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387790"
---
# <a name="about-workflowcommonparameters"></a>WorkflowCommonParameters 정보

## <a name="short-description"></a>간단한 설명

이 항목에서는 모든 Windows PowerShell 워크플로 명령에 유효한 매개 변수에 대해 설명 합니다. Windows PowerShell 엔진은 워크플로에 추가 하므로 워크플로를 통해 이러한 매개 변수를 사용할 수 있으며 작성자가 만든 워크플로에서 자동으로 사용 하도록 설정 됩니다.

## <a name="long-description"></a>자세한 설명

Windows PowerShell 워크플로 일반 매개 변수는 모든 Windows PowerShell 워크플로 및 작업에 사용할 수 있는 cmdlet 매개 변수 집합입니다. 이러한 워크플로는 워크플로 작성자가 아닌 Windows PowerShell 워크플로 엔진에 의해 추가 되며 워크플로 및 활동에서 자동으로 사용할 수 있습니다. 그러나 세 수준 깊이 중첩 된 워크플로는 워크플로 일반 매개 변수를 포함 하 여 일반 매개 변수를 지원 하지 않습니다.

모든 워크플로 매개 변수는 선택 사항이 며 위치는 지정 되지 않습니다. 파이프라인에서 입력을 사용 하지 않습니다.

대부분의 워크플로 일반 매개 변수에는 PS 접두사 (예: 및)가 있습니다 `PSComputerName` `PSCredential` . PS 접두사가 있는 매개 변수는 대상 컴퓨터에 대 한 연결 및 실행 환경을 구성 합니다 ("원격 노드" 라고도 함).

및와 같은 대부분의 워크플로 일반 매개 변수에 `PSAllowRedirection` 는 `AsJob` Windows PowerShell 원격 작업 및 백그라운드 작업에서 사용 되는 매개 변수와 비슷한 이름이 있습니다. 이러한 매개 변수는 비슷한 이름의 remoting 및 작업 매개 변수와 동일한 방식으로 작동 하므로 원격 작업에서 개발한 정보를 사용 하 여 워크플로를 관리할 수 있습니다.

워크플로는 Windows PowerShell 3.0에서 도입 되었습니다.

### <a name="parameter-descriptions"></a>매개 변수 설명

이 섹션에서는 워크플로 일반 매개 변수에 대해 설명 합니다.

#### <a name="-asjob-switchparameter"></a>-AsJob \<SwitchParameter\>

워크플로 작업으로 워크플로를 실행 합니다. 워크플로 명령은 부모 작업을 나타내는 개체를 즉시 반환 합니다. 부모 작업에는 각 대상 컴퓨터에서 실행 되는 자식 작업이 포함 됩니다. 작업을 관리하려면 Job cmdlet을 사용합니다. 작업 결과를 가져오려면 [Receive-Job](xref:Microsoft.PowerShell.Core.Receive-Job)을 사용합니다.

#### <a name="-jobname-string"></a>-JobName \<String\>

워크플로 작업에 대 한 친숙 한 이름을 지정 합니다. 기본적으로 작업 이름은 "작업\<n\>"이며, \<n\>은 서수 번호입니다.

워크플로 명령에 JobName 매개 변수를 사용 하는 경우 `AsJob` 명령에 매개 변수를 포함 하지 않더라도 워크플로는 작업으로 실행 되 고 워크플로 명령은 작업 개체를 반환 합니다.

Windows PowerShell 백그라운드 작업에 대한 자세한 내용은 [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)를 참조하세요.

#### <a name="-psallowredirection-switchparameter"></a>-PSAllowRedirection \<SwitchParameter\>

대상 컴퓨터에 대 한 연결 리디렉션을 허용 합니다.

매개 변수를 사용 하는 경우 `PSConnectionURI` 원격 대상이 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다. 기본적으로 Windows PowerShell은 연결을 리디렉션하지 않지만 매개 변수를 사용 하 여 `PSAllowRedirection` 대상 컴퓨터에 대 한 연결 리디렉션을 허용할 수 있습니다.

`MaximumConnectionRedirectionCount` `$PSSessionOption` 기본 설정 변수의 속성을 설정 하거나 `MaximumConnectionRedirectionCount` 값의 속성을 설정 하 여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다 `PSSessionOption parameter` . 기본값은 5입니다. 자세한 내용은 `PSSessionOption` 매개 변수 및 [새-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)에 대 한 설명을 참조 하세요.

#### <a name="-psapplicationname-string"></a>-PSApplicationName \<String\>

대상 컴퓨터에 연결 하는 데 사용 되는 연결 URI의 응용 프로그램 이름 세그먼트를 지정 합니다. 명령에 매개 변수를 사용 하지 않는 경우이 매개 변수를 사용 하 여 응용 프로그램 이름을 지정 합니다 `ConnectionURI` .

기본값은 `$PSSessionApplicationName` 로컬 컴퓨터의 기본 설정 변수 값입니다. 이 기본 설정 변수를 정의하지 않으면 WSMAN이 기본값으로 사용됩니다. 이 값은 대부분의 사용에 적합합니다. 자세한 내용은 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.

WinRM 서비스는 애플리케이션 이름을 사용하여 연결 요청을 제공하는 수신기를 선택합니다. 이 매개 변수 값은 `URLPrefix` 원격 컴퓨터에 있는 수신기의 속성 값과 일치 해야 합니다.

#### <a name="-psauthentication-authenticationmechanism"></a>-PSAuthentication \<AuthenticationMechanism\>

대상 컴퓨터에 연결할 때 사용자의 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.

유효한 값은 다음과 같습니다.

- **기본값**
- **기본**
- **Credssp**
- **다이제스트**
- **Kerberos**
- **결정할**
- **NegotiateWithImplicitCredential**

기본값은 **Default** 입니다.

이 매개 변수 값에 대 한 자세한 내용은 PowerShell SDK의 열거에 대 한 설명을 참조 하세요 `System.Management.Automation.Runspaces.AuthenticationMechanism` .

> [!WARNING]
> 사용자 자격 증명이 인증할 원격 컴퓨터로 전달되는 CredSSP(Credential Security Service Provider) 인증은 원격 네트워크 공유 액세스 등 두 개 이상의 리소스에서 인증이 필요한 명령에 사용됩니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

#### <a name="-psauthenticationlevel-authenticationlevel"></a>-PSAuthenticationLevel \<AuthenticationLevel\>

대상 컴퓨터에 대 한 연결의 인증 수준을 지정 합니다.
기본값은 **Default** 입니다.

유효한 값은 다음과 같습니다.

|속성 |Description |
|---------|---------|
|**변경 안 됨** | 인증 수준이 이전 명령과 동일합니다. |
|**기본값** | Windows 인증. |
|**없음** | COM 인증이 없습니다.   |
|**연결** | 연결 수준 COM 인증입니다.|
|**호출** | 호출 수준 COM 인증입니다.   |
|**패킷** | 패킷 수준 COM 인증입니다.|
|**PacketIntegrity** | 패킷 무결성 수준 COM 인증입니다.  |
|**PacketPrivacy** | 패킷 전용 수준 COM 인증입니다. |

#### <a name="-pscertificatethumbprint-string"></a>-PSCertificateThumbprint \<String\>

이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다. 인증서의 인증서 지문을 입력합니다.

인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 인증서 손 도장(Thumbprint)은 로컬 사용자 계정으로만 매핑될 수 있고 도메인 계정에는 사용할 수 없습니다.

인증서를 가져오려면 [Get Item](xref:Microsoft.PowerShell.Management.Get-Item) 또는 [Get-childitem] (.)을 사용 합니다. /.. Windows PowerShell Cert: 드라이브의 cmdlet을/Microsoft.PowerShell.Management/Get-Childitem.md 합니다.

#### <a name="-pscomputername-string"></a>-PSComputerName \<String[]\>

워크플로의 대상 노드인 컴퓨터 목록을 지정 합니다.
워크플로의 명령 또는 활동은이 매개 변수를 사용 하 여 지정 된 컴퓨터에서 실행 됩니다. 기본값은 로컬 컴퓨터입니다.

하나 이상의 컴퓨터의 NETBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 쉼표로 구분된 목록으로 입력합니다. 로컬 컴퓨터를 지정하려면 컴퓨터 이름, "localhost" 또는 점(.)을 입력하세요.

매개 변수 값에 로컬 컴퓨터를 포함 하려면 `PSComputerName` "관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell을 엽니다.

명령에서이 매개 변수를 생략 하거나 값이 `$null` 또는 빈 문자열인 경우 워크플로 대상은 로컬 컴퓨터이 고 Windows PowerShell 원격을 사용 하 여 명령을 실행 하지 않습니다.

매개 변수 값에 IP 주소를 사용 하려면 `ComputerName` 명령에 매개 변수를 포함 해야 합니다 `PSCredential` . 또한 HTTPS 전송을 사용하도록 컴퓨터를 구성하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 WinRM TrustedHosts 목록에 포함해야 합니다. TrustedHosts 목록에 컴퓨터 이름을 추가 하는 방법에 대 한 지침은 [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)의 *"신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법"* 을 참조 하십시오.

#### <a name="-psconfigurationname-string"></a>-PSConfigurationName \<String\>

대상 컴퓨터에서 세션을 구성 하는 데 사용 되는 세션 구성을 지정 합니다. 대상 컴퓨터에 세션 구성을 입력 합니다 (워크플로 서버 컴퓨터가 아님). 기본값은 `Microsoft.PowerShell.Workflow`입니다.

#### <a name="-psconnectionretrycount-uint"></a>-PSConnectionRetryCount \<UInt\>

첫 번째 연결 시도가 실패 한 경우 각 대상 컴퓨터에 대 한 최대 연결 시도 횟수를 지정 합니다. 1에서 4294967295 사이의 숫자 (Int32.maxvalue)를 입력 합니다. 기본값 영 (0)은 재시도 횟수를 나타냅니다.

#### <a name="-psconnectionretryintervalsec-uint"></a>-PSConnectionRetryIntervalSec \<UInt\>

연결 다시 시도 사이의 지연 시간 (초)을 지정 합니다. 기본값은 영(0)입니다. 이 매개 변수는 PSConnectionRetryCount의 값이 1 이상인 경우에만 유효 합니다.

#### <a name="-psconnectionuri-systemuri"></a>-PSConnectionURI \<System.Uri\>

대상 컴퓨터에서 워크플로의 연결 끝점을 정의 하는 URI (Uniform Resource Identifier)를 지정 합니다. URI는 정규화된 URI여야 합니다.

이 문자열의 형식은 다음과 같습니다.

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

기본값은 `http://localhost:5985/WSMAN`입니다.

을 지정 하지 않으면,, `PSConnectionURI` `PSUseSSL` `PSComputerName` `PSPort` 및 매개 변수를 사용 하 여 값을 `PSApplicationName` 지정할 수 있습니다 `PSConnectionURI` .

URI의 전송 세그먼트에 유효한 값은 **HTTP** 및 **HTTPS** 입니다.
전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다. Windows PowerShell 원격을 위한 기본 포트를 사용하려면 HTTP의 경우 포트 5985 또는 HTTPS의 경우 5986을 지정합니다.

#### <a name="-pscredential-pscredential"></a>-PSCredential \<PSCredential\>

대상 컴퓨터에서 워크플로를 실행할 수 있는 권한을 가진 사용자 계정을 지정 합니다. 기본값은 현재 사용자입니다. 이 매개 변수는 PSComputerName 매개 변수가 명령에 포함 된 경우에만 유효 합니다.

"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나 `PSCredential` cmdlet이 반환 하는 개체와 같은 개체를 포함 하는 변수를 입력 `Get-Credential` 합니다. 사용자 이름만 입력하면 암호를 묻는 메시지가 표시됩니다.

#### <a name="-pselapsedtimeoutsec-uint32"></a>-PSElapsedTimeoutSec \<UInt32\>

시스템에서 워크플로 및 모든 관련 리소스를 유지 관리 하는 기간을 결정 합니다. 제한 시간이 만료 되 면 워크플로는 아직 처리 중인 경우에도 삭제 됩니다. 10에서 4294967295 사이의 값을 입력 합니다. 기본값 0은 경과 된 시간 제한이 없음을 의미 합니다.

#### <a name="-psparametercollection-hashtable"></a>-PSParameterCollection \<Hashtable[]\>

서로 다른 대상 컴퓨터에 대해 서로 다른 워크플로 일반 매개 변수 값을 지정 합니다.

각 대상 컴퓨터에 대해 하나의 해시 테이블을 사용 하 여 쉼표로 구분 된 해시 테이블 목록을 입력 합니다. 각 해시 테이블에서 첫 번째 키는이 `PSComputerName` 고 해당 값은 대상 컴퓨터의 이름입니다. 컴퓨터 이름에 와일드 카드 문자를 사용할 수 있습니다. 해시 테이블의 나머지 키에 대 한 키는 매개 변수 이름이 고 값은 매개 변수 값입니다.

예를 들어:

```powershell
-PSParameterCollection @{PSComputerName="*"; PSElapsedTimeoutSec=20},
@{PSComputerName="Server02"},
@{PSComputerName="Server03"},
@{PSComputerName="Server01"; PSElapsedTimeoutSec=10}
```

위의 예제에서 모든 연결의 기본 PSElapsedTimeoutSec은 20 초의 기본 Server01를 제외 하 고, 기본 값을 10 초로 지정 하 여 기본값을 재정의 하는 경우를 제외 하 고,

#### <a name="-pspersist-boolean"></a>-PSPersist \<Boolean\>

워크플로에 지정 된 검사점 외에도 워크플로에 검사점을 추가 합니다.

이 매개 변수는 `PSPersist` 활동 일반 매개 변수, `Checkpoint-Workflow` 활동 또는 변수를 사용 하 여 지정 된 검사점 등 워크플로의 검사점을 표시 하지 않습니다 `$PSPersistPreference` .

"검사점" 또는 "지 속성 지점"은 워크플로가 실행 되는 동안 캡처되고 디스크 또는 SQL 데이터베이스의 지 속성 저장소에 저장 되는 데이터와 워크플로 상태에 대 한 스냅숏입니다. Windows PowerShell 워크플로는 저장 된 데이터를 사용 하 여 워크플로를 다시 시작 하지 않고 마지막 지 속성 지점에서 일시 중단 또는 중단 된 워크플로를 다시 시작 합니다.

유효한 값은

- ( *기본값* ) 이 매개 변수를 생략 하면 워크플로에 지정 된 검사점 외에도 워크플로의 시작과 끝에 검사점이 추가 됩니다.

- `$True`. 워크플로에 지정 된 검사점 외에도 워크플로의 시작과 끝에 검사점을 추가 하 고 각 활동 뒤에 검사점을 추가 합니다.

- `$False`. 검사점이 추가 되지 않습니다. 검사점은 워크플로에 지정 된 경우에만 수행 됩니다.

#### <a name="-psport-int32"></a>-PSPort \<Int32\>

대상 컴퓨터의 네트워크 포트를 지정 합니다. 기본 포트는 5985(HTTP용 WinRM 포트) 및 5986(HTTPS용 WinRM 포트)입니다.

반드시 필요한 경우가 아니면 PSPort 매개 변수를 사용 하지 마세요. 명령에 설정 된 포트는 명령이 실행 되는 모든 컴퓨터 또는 세션에 적용 됩니다. 대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다. 대체 포트를 사용하려면 먼저 원격 컴퓨터에 해당 포트에서 수신 대기할 WinRM 수신기를 구성해야 합니다.

#### <a name="-psprivatemetadata-hashtable"></a>-PSPrivateMetadata \<Hashtable\>

워크플로 작업에 사용자 지정 된 정보를 제공 합니다. 해시 테이블을 입력 합니다. 각 워크플로에 대 한 키 및 값이 사용자 지정 됩니다. 워크플로의 개인 메타 데이터에 대 한 자세한 내용은 워크플로에 대 한 도움말 항목을 참조 하세요.

이 매개 변수는 Windows PowerShell 워크플로 엔진에서 처리 되지 않습니다.
대신, 엔진은 해시 테이블을 워크플로로 직접 전달 합니다.

#### <a name="-psrunningtimeoutsec-uint32"></a>-PSRunningTimeoutSec \<UInt32\>

워크플로가 일시 중단 된 시간을 제외 하 고 워크플로의 실행 시간 (초)을 지정 합니다. 시간이 만료 될 때 워크플로 실행이 완료 되지 않으면 Windows PowerShell 워크플로 엔진은 워크플로 실행을 강제로 중지 합니다.

#### <a name="-pssessionoption-pssessionoption"></a>-PSSessionOption \<PSSessionOption\>

대상 컴퓨터에 대 한 세션의 고급 옵션을 설정 합니다. Cmdlet을 `PSSessionOption` 사용 하 여 만든 개체와 같은 개체를 입력 합니다 `New-PSSessionOption` .

세션 옵션의 기본값은 기본 설정 `$PSSessionOption` 변수의 값 (설정 된 경우)에 따라 결정 됩니다. 그렇지 않으면 세션 구성에 지정 된 값을 사용 합니다.

기본값을 포함 하 여 세션 옵션에 대 한 자세한 내용은 cmdlet의 도움말 항목 `New-PSSessionOption` (.. /.. /Microsoft.PowerShell.Core/New-PSSessionOption.md). 기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.

#### <a name="-psusessl-switchparameter"></a>-PSUseSSL \<SwitchParameter\>

는 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 대상 컴퓨터에 대 한 연결을 설정 합니다. 기본적으로 SSL은 사용되지 않습니다.

WS-Management는 네트워크를 통해 전송되는 모든 Windows PowerShell 내용을 암호화합니다. UseSSL은 HTTP 대신 HTTPS를 통해 데이터를 보내는 추가적인 보호 기능입니다. 이 매개 변수를 사용하지만 명령에 사용되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패합니다.

## <a name="see-also"></a>참고 항목

- [about_ActivityCommonParameters](about_ActivityCommonParameters.md)
- [about_Workflows](about_Workflows.md)
- [Invoke-AsWorkflow](xref:PSWorkflowUtility.Invoke-AsWorkflow)
- [New-PSWorkflowExecutionOption](xref:PSWorkflow.New-PSWorkflowExecutionOption)
- [New-PSWorkflowSession](xref:PSWorkflow.New-PSWorkflowSession)

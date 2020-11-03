---
description: Windows PowerShell 워크플로에서 활동에 추가 하는 매개 변수를 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_activitycommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_ActivityCommonParameters
ms.openlocfilehash: b745bf17e4ae26156042ecdc25211830177bc692
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221914"
---
# <a name="about-activitycommonparameters"></a>ActivityCommonParameters 정보

## <a name="short-description"></a>간단한 설명

Windows PowerShell 워크플로에서 활동에 추가 하는 매개 변수를 설명 합니다.

## <a name="long-description"></a>자세한 설명

Windows PowerShell 워크플로는 PSActivity 기본 클래스에서 파생 된 활동에 활동 일반 매개 변수를 추가 합니다. 이 범주에는 Get-Process 및 WinEvent와 같이 활동으로 구현 되는 InlineScript 활동 및 Windows PowerShell cmdlet이 포함 됩니다.

활동 일반 매개 변수는 Suspend-Workflow 및 Checkpoint-Workflow 활동에서 유효 하지 않으며 Windows PowerShell 워크플로가 InlineScript 스크립트 블록이 나 유사한 활동에서 자동으로 실행 하는 cmdlet 또는 식에는 추가 되지 않습니다. InlineScript 활동에서는 활동 일반 매개 변수를 사용할 수 있지만 InlineScript 스크립트 블록의 명령에서는 사용할 수 없습니다.

활동 일반 매개 변수 중 일부는 워크플로 일반 매개 변수 또는 Windows PowerShell 일반 매개 변수 이기도 합니다. 다른 활동 일반 매개 변수는 활동에 대해 고유 합니다.

워크플로 일반 매개 변수에 대한 자세한 내용은 about_WorkflowCommonParameters를 참조하세요. Windows PowerShell 일반 매개 변수에 대 한 자세한 내용은 about_CommonParameters를 참조 하세요.

### <a name="list-of-activity-common-parameters"></a>활동 일반 매개 변수 목록

```
AppendOutput                      PSDebug
Debug                             PSDisableSerialization
DisplayName                       PSDisableSerializationPreference
ErrorAction                       PSError
Input                             PSPersist
MergeErrorToOutput                PSPort
PSActionRetryCount                PSProgress
PSActionRetryIntervalSec          PSProgressMessage
PSActionRunningTimeoutSec         PSRemotingBehavior
PSApplicationName                 PSRequiredModules
PSAuthentication                  PSSessionOption
PSCertificateThumbprint           PSUseSSL
PSComputerName                    PSVerbose
PSConfigurationName               PSWarning
PSConnectionRetryCount            Result
PSConnectionRetryIntervalSec      UseDefaultInput
PSConnectionURI                   Verbose
PSCredential                      WarningAction
```

### <a name="parameter-descriptions"></a>매개 변수 설명

이 섹션에서는 활동 일반 매개 변수에 대해 설명 합니다.

#### <a name="appendoutput-boolean"></a>AppendOutput \<Boolean\>

값은 `$True` 변수의 값에 활동의 출력을 추가 합니다.
값은 아무런 `$False` 영향을 주지 않습니다. 기본적으로 값을 변수에 할당하면 변수 값이 대체됩니다.

예를 들어 다음 명령은 변수에서 service 개체에 process 개체를 추가 `$x` 합니다.

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x = Get-Process -AppendOutput $true
}
```

이 매개 변수는 XAML 기반 워크플로 용으로 설계 되었습니다. 스크립트 워크플로에서 다음 예와 같이 + = 대입 연산자를 사용 하 여 출력을 변수 값에 추가할 수도 있습니다.

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x += Get-Process
}
```

#### <a name="debug-switchparameter"></a>디버그 \<SwitchParameter\>

명령에 의해 수행 된 작업에 대 한 프로그래머 수준의 세부 정보를 표시 합니다.
Debug 매개 변수는 현재 명령에 대 한 $DebugPreference 변수의 값을 재정의 합니다. 이 매개 변수는 명령에서 디버깅 메시지를 생성 하는 경우에만 작동 합니다. 이 매개 변수는 Windows PowerShell 일반 매개 변수 이기도 합니다.

#### <a name="displayname-string"></a>DisplayName \<String\>

활동에 식별 이름을 지정합니다. 워크플로를 실행 하는 동안 및 워크플로 작업의 Progress 속성 값에서 DisplayName 값이 진행률 표시줄에 표시 됩니다. PSProgressMessage 매개 변수가 명령에도 포함 된 경우 진행률 표시줄 콘텐츠가: 형식으로 표시 됩니다 \<DisplayName\> \<PSProgressMessage\> .

#### <a name="erroraction-actionpreference"></a>ErrorAction \<ActionPreference\>

작업이 명령에서 종료 되지 않는 오류에 응답 하는 방법을 결정 합니다. 종료 오류에는 영향을 주지 않습니다. 이 매개 변수는 Write-Error cmdlet의 경우와 같이 명령이 종료 되지 않는 오류를 생성 하는 경우에만 작동 합니다. ErrorAction 매개 변수는 현재 명령에 대 한 $ErrorActionPreference 변수의 값을 재정의 합니다. 이 매개 변수는 Windows PowerShell 일반 매개 변수 이기도 합니다.

유효한 값은

- 하기. 오류 메시지를 표시 하 고 명령을 계속 실행 합니다. "Continue"가 기본값입니다.

- 무시. 오류 메시지를 표시 하지 않고 명령을 계속 실행 합니다.
  SilentlyContinue와 달리 Ignore는 $Error 자동 변수에 오류 메시지를 추가 하지 않습니다. Ignore 값은 Windows PowerShell 3.0에서 도입 되었습니다.

- Inquire. 오류 메시지를 표시 하 고 실행을 계속 하기 전에 확인 메시지를 표시 합니다. 이 값은 거의 사용 되지 않습니다.

- 일시 중단. 추가 조사를 허용 하도록 워크플로 작업을 자동으로 일시 중단 합니다. 조사 후 워크플로를 다시 시작할 수 있습니다.

- SilentlyContinue. 오류 메시지를 표시 하지 않고 명령을 계속 실행 합니다.

- 중지 오류 메시지를 표시 하 고 명령 실행을 중지 합니다.

#### <a name="input-object"></a>입력 \<Object[]\>

개체의 컬렉션을 활동에 제출합니다. 이는 한 번에 하나씩 개체를 활동에 파이프하는 것에 대한 대안입니다.

#### <a name="mergeerrortooutput-boolean"></a>MergeErrorToOutput \<Boolean\>

값이 이면 `$True` 출력 스트림에 오류가 추가 됩니다. 값은 `$False` 적용 되지 않습니다. 병렬 및 키워드와 함께이 매개 변수를 사용 `ForEach -Parallel` 하 여 단일 컬렉션의 여러 병렬 명령에서 발생 하는 오류 및 출력을 수집 합니다.

#### <a name="psactionretrycount-int32"></a>PSActionRetryCount \<Int32\>

첫 번째 시도가 실패하면 반복해서 활동을 실행하려고 시도합니다. 기본값 0은 다시 시도하지 않습니다.

#### <a name="psactionretryintervalsec-int32"></a>PSActionRetryIntervalSec \<Int32\>

동작 다시 시도 사이의 간격을 초 단위로 결정합니다. 기본값 0은 동작을 즉시 다시 시도합니다. 이 매개 변수는 PSActionRetryCount 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다.

#### <a name="psactionrunningtimeoutsec-int32"></a>PSActionRunningTimeoutSec \<Int32\>

각 대상 컴퓨터에서 활동이 실행될 수 있는 기간을 결정합니다. 제한 시간이 만료 되기 전에 작업이 완료 되지 않으면 Windows PowerShell 워크플로에서 종료 오류를 생성 하 고 영향을 받는 대상 컴퓨터에서 워크플로 처리를 중지 합니다.

#### <a name="psallowredirection-boolean"></a>PSAllowRedirection \<Boolean\>

$True 값은 대상 컴퓨터에 대 한 연결 리디렉션을 허용 합니다.
$False 값은 영향을 주지 않습니다. 이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

PSConnectionURI 매개 변수를 사용 하는 경우 원격 대상이 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다. 기본적으로 Windows PowerShell은 연결을 리디렉션하지 않지만, PSAllowRedirection 매개 변수를 $True 값과 함께 사용 하 여 대상 컴퓨터에 대 한 연결 리디렉션을 허용할 수 있습니다.

`$PSSessionOption`기본 설정 변수의 MaximumConnectionRedirectionCount 속성을 설정 하거나 세션을 만드는 cmdlet의 SSessionOption 매개 변수 값의 MaximumConnectionRedirectionCount 속성을 설정 하 여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다. 기본값은 5입니다.

#### <a name="psapplicationname-string"></a>PSApplicationName \<String\>

대상 컴퓨터에 연결 하는 데 사용 되는 연결 URI의 응용 프로그램 이름 세그먼트를 지정 합니다. 이 매개 변수를 사용하여 명령에 ConnectionURI 매개 변수를 사용하지 않는 경우 애플리케이션 이름을 지정할 수 있습니다. 이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

기본값은 `$PSSessionApplicationName` 대상 컴퓨터의 기본 설정 변수 값입니다. 이 기본 설정 변수를 정의하지 않으면 WSMAN이 기본값으로 사용됩니다. 이 값은 대부분의 사용에 적합합니다. 자세한 내용은 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.

WinRM 서비스는 애플리케이션 이름을 사용하여 연결 요청을 제공하는 수신기를 선택합니다. 이 매개 변수 값은 원격 컴퓨터에 있는 수신기의 URLPrefix 속성 값과 일치해야 합니다.

#### <a name="psauthentication-authenticationmechanism"></a>PSAuthentication \<AuthenticationMechanism\>

대상 컴퓨터에 연결할 때 사용자의 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다. 유효한 값은 Default, Basic, Credssp, Digest, Kerberos, Negotiate 및 NegotiateWithImplicitCredential입니다. 기본값은 Default입니다. 이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

이 매개 변수 값에 대한 자세한 내용은 MSDN의 **System.Management.Automation.Runspaces.AuthenticationMechanism** 열거형 설명을 참조하세요.

> [!WARNING]
> 사용자 자격 증명이 인증할 원격 컴퓨터로 전달되는 CredSSP(Credential Security Service Provider) 인증은 원격 네트워크 공유 액세스 등 두 개 이상의 리소스에서 인증이 필요한 명령에 사용됩니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

#### <a name="pscertificatethumbprint-string"></a>PSCertificateThumbprint \<String\>

이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다. 인증서의 인증서 지문을 입력합니다. 이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 인증서 손 도장(Thumbprint)은 로컬 사용자 계정으로만 매핑될 수 있고 도메인 계정에는 사용할 수 없습니다.

인증서를 가져오려면 Windows PowerShell Cert: 드라이브의 [Get Item](xref:Microsoft.PowerShell.Management.Get-Item) 또는 [Get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) cmdlet을 사용 합니다.

#### <a name="pscomputername-string"></a>PSComputerName \<String[]\>

작업이 실행 되는 대상 컴퓨터를 지정 합니다. 기본값은 로컬 컴퓨터입니다. 이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

하나 이상의 컴퓨터의 NETBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 쉼표로 구분된 목록으로 입력합니다. 로컬 컴퓨터를 지정하려면 컴퓨터 이름, "localhost" 또는 점(.)을 입력하세요.

PSComputerName 매개 변수 값에 로컬 컴퓨터를 포함 하려면 "관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell을 엽니다.

명령에서이 매개 변수를 생략 하거나 값이 $null 또는 빈 문자열인 경우 워크플로 대상은 로컬 컴퓨터이 고 Windows PowerShell 원격을 사용 하 여 명령을 실행 하지 않습니다.

ComputerName 매개 변수 값에 IP 주소를 사용 하려면 명령에 PSCredential 매개 변수를 포함 해야 합니다. 또한 HTTPS 전송을 사용하도록 컴퓨터를 구성하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 WinRM TrustedHosts 목록에 포함해야 합니다. TrustedHosts 목록에 컴퓨터 이름을 추가 하는 방법에 대 한 지침은 [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)의 "신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법"을 참조 하십시오.

#### <a name="psconfigurationname-string"></a>PSConfigurationName \<String\>

대상 컴퓨터에서 세션을 만드는 데 사용 되는 세션 구성을 지정 합니다. 워크플로를 실행 하는 컴퓨터가 아니라 대상 컴퓨터에 세션 구성의 이름을 입력 합니다. 기본값은 Microsoft. PowerShell입니다. 이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

#### <a name="psconnectionretrycount-uint"></a>PSConnectionRetryCount \<UInt\>

첫 번째 연결 시도가 실패 한 경우 각 대상 컴퓨터에 대 한 최대 연결 시도 횟수를 지정 합니다. 1에서 4294967295 사이의 숫자 (Int32.maxvalue)를 입력 합니다. 기본값 영 (0)은 재시도 횟수를 나타냅니다.
이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

#### <a name="psconnectionretryintervalsec-uint"></a>PSConnectionRetryIntervalSec \<UInt\>

연결 다시 시도 사이의 지연 시간 (초)을 지정 합니다. 기본값은 영(0)입니다. 이 매개 변수는 PSConnectionRetryCount의 값이 1 이상인 경우에만 유효 합니다. 이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

#### <a name="psconnectionuri-systemuri"></a>PSConnectionURI \<System.Uri\>

대상 컴퓨터에서 작업에 대 한 연결 끝점을 정의 하는 URI (Uniform Resource Identifier)를 지정 합니다. URI는 정규화된 URI여야 합니다. 이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

이 문자열의 형식은 다음과 같습니다.

```
<Transport>://<ComputerName>:<Port>/<ApplicationName>
```

기본값은 `http://localhost:5985/WSMAN`입니다.

PSConnectionURI를 지정 하지 않으면 PSUseSSL, PSComputerName, PSPort 및 PSApplicationName 매개 변수를 사용 하 여 PSConnectionURI 값을 지정할 수 있습니다.

URI의 전송 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다. 전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다. Windows PowerShell 원격을 위한 기본 포트를 사용하려면 HTTP의 경우 포트 5985 또는 HTTPS의 경우 5986을 지정합니다.

#### <a name="pscredential-pscredential"></a>유형이 \<PSCredential\>

대상 컴퓨터에서 작업을 실행할 수 있는 권한을 가진 사용자 계정을 지정 합니다. 기본값은 현재 사용자입니다. 이 매개 변수는 PSComputerName 매개 변수가 명령에 포함 된 경우에만 유효 합니다. 이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

사용자 이름 (예: "User01" 또는 "Domain01\User01")을 입력 하거나 PSCredential 개체 (예: Get-Credential cmdlet이 반환 하는 변수)를 포함 하는 변수를 입력 합니다. 사용자 이름만 입력하면 암호를 묻는 메시지가 표시됩니다.

#### <a name="psdebug-psdatacollectiondebugrecord"></a>Set-psdebug \<PSDataCollection[DebugRecord]\>

디버그 메시지를 콘솔에 기록 하거나 워크플로 작업의 Debug 속성 값에 쓰지 않고 활동의 디버그 메시지를 지정 된 디버그 레코드 컬렉션에 추가 합니다. 여러 활동의 디버그 메시지를 동일한 디버그 레코드 컬렉션 개체에 추가할 수 있습니다.

이 활동 일반 매개 변수를 사용 하려면 New-Object cmdlet을 사용 하 여 DebugRecord 형식의 P s d 개체를 만들고 개체를 변수에 저장 합니다. 그런 다음, 다음 예제와 같이 변수를 하나 이상의 활동에 대 한 PSDebug 매개 변수 값으로 사용 합니다.

```powershell
Workflow Test-Workflow
{
    $debugCollection = New-Object -Type `
    System.Management.Automation.PSDataCollection[System.Management.Automation.DebugRecord]
    InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    if ($debugCollection -like "Missing") { ...}
}
```

#### <a name="psdisableserialization-boolean"></a>PSDisableSerialization \<Boolean\>

활동이 워크플로에 "라이브"(직렬화하지 않음) 개체를 반환하도록 지시합니다.
결과 개체는 방법 및 속성이 있지만 검사점을 사용하는 경우 저장할 수 없습니다.

#### <a name="psdisableserializationpreference-boolean"></a>PSDisableSerializationPreference \<Boolean\>

활동 뿐만 아니라 전체 워크플로에 PSDisableSerialization 매개 변수에 해당 하는 것을 적용 합니다. 개체를 직렬화 하지 않는 워크플로는 다시 시작 하거나 지속할 수 없으므로 일반적으로이 매개 변수를 추가 하지 않는 것이 좋습니다.

유효한 값은

- 기본 생략 하는 경우 PSDisableSerialization 매개 변수를 작업에 추가 하지 않은 경우에도 개체가 serialize 됩니다.

- `$True`. 워크플로 내의 모든 활동이 "라이브" (직렬화 되지 않음) 개체를 반환 하도록 지시 합니다. 결과 개체는 방법 및 속성이 있지만 검사점을 사용하는 경우 저장할 수 없습니다.
- `$False`. 워크플로 개체는 serialize 됩니다.

#### <a name="pserror-psdatacollectionerrorrecord"></a>PSError \<PSDataCollection[ErrorRecord]\>

워크플로 작업의 오류 속성 값 또는 콘솔에 오류 메시지를 쓰지 않고 활동의 오류 메시지를 지정 된 오류 레코드 컬렉션에 추가 합니다. 여러 활동의 오류 메시지를 동일한 오류 레코드 컬렉션 개체에 추가할 수 있습니다.

이 활동 일반 매개 변수를 사용 하려면 cmdlet을 사용 하 여 `New-Object` ErrorRecord 유형의 p s d 개체를 만들고 해당 개체를 변수에 저장 합니다. 그런 다음, 다음 예제와 같이 변수를 하나 이상의 활동에 대 한 PSError 매개 변수 값으로 사용 합니다.

```powershell
Workflow Test-Workflow
{
   $typeName = "System.Management.Automation.PSDataCollection"
   $typeName += '[System.Management.Automation.ErrorRecord]'
   $ec = New-Object $typeName
   InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSError $ec
   InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSError $ec
   if ($ec.Count -gt 2)
   {
      # Do Some Work.
   }
}
```

#### <a name="pspersist-boolean"></a>PSPersist \<Boolean\>

작업 후 검사점을 만듭니다. 이 검사점은 워크플로에 지정 된 검사점에 추가 됩니다. 이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

"검사점" 또는 "지 속성 지점"은 워크플로 상태와 워크플로를 실행 하는 동안 캡처되고 디스크의 지 속성 저장소에 저장 되는 데이터의 스냅숏입니다. Windows PowerShell 워크플로는 저장 된 데이터를 사용 하 여 워크플로를 다시 시작 하지 않고 마지막 지 속성 지점에서 일시 중단 또는 중단 된 워크플로를 다시 시작 합니다.

유효한 값은

- 기본 이 매개 변수를 생략 하면 검사점이 추가 되지 않습니다. 검사점은 워크플로의 설정에 따라 수행 됩니다.

- `$True`. 활동이 완료된 후 검사점을 작성합니다.
  이 검사점은 워크플로에 지정 된 검사점에 추가 됩니다.

- `$False`. 검사점이 추가 되지 않습니다. 검사점은 워크플로에 지정 된 경우에만 수행 됩니다.

#### <a name="psport-int32"></a>PSPort \<Int32\>

대상 컴퓨터의 네트워크 포트를 지정 합니다. 기본 포트는 5985(HTTP용 WinRM 포트) 및 5986(HTTPS용 WinRM 포트)입니다. 이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

반드시 필요한 경우가 아니면 PSPort 매개 변수를 사용 하지 마세요. 명령에 설정 된 포트는 명령이 실행 되는 모든 컴퓨터 또는 세션에 적용 됩니다. 대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다. 대체 포트를 사용하려면 먼저 원격 컴퓨터에 해당 포트에서 수신 대기할 WinRM 수신기를 구성해야 합니다.

#### <a name="psprogress-psdatacollectionprogressrecord"></a>PSProgress \<PSDataCollection[ProgressRecord]\>

워크플로 작업의 progress 속성 값 또는 콘솔에 진행률 메시지를 쓰지 않고 활동의 진행률 메시지를 지정 된 진행률 레코드 컬렉션에 추가 합니다. 여러 활동의 진행률 메시지를 동일한 진행률 레코드 컬렉션 개체에 추가할 수 있습니다.

#### <a name="psprogressmessage-string"></a>PSProgressMessage \<String\>

활동에 대한 간단한 설명을 지정합니다. PSProgressMessage 값은 워크플로가 실행 되는 동안 진행률 표시줄에 표시 됩니다. DisplayName이 명령에도 포함 된 경우 진행률 표시줄 콘텐츠가: 형식으로 표시 됩니다 \<DisplayName\> \<PSProgressMessage\> .

이 매개 변수는 ForEach-Parallel 스크립트 블록에서 활동을 식별 하는 데 특히 유용 합니다. 이 메시지가 없으면 모든 병렬 분기의 활동이 같은 이름으로 식별됩니다.

#### <a name="psremotingbehavior-remotingbehavior"></a>Psremo의 동작 \<RemotingBehavior\>

활동이 대상 컴퓨터에서 실행될 때 원격이 어떻게 관리되는지 지정합니다.
PowerShell이 기본값입니다.

유효한 값은 다음과 같습니다.

- 없음: 작업이 원격 컴퓨터에서 실행 되지 않습니다.

- PowerShell: 대상 컴퓨터에서 작업을 실행 하는 데 Windows PowerShell 원격 기능을 사용 합니다.

- 사용자 지정: 활동은 고유한 유형의 원격을 지원 합니다. 이 값은 활동으로 구현 되는 cmdlet이 Remorerecommand 특성의 값을 SupportedByCommand로 설정 하 고 명령에 ComputerName 매개 변수를 포함 하는 경우에 유효 합니다.

#### <a name="psrequiredmodules-string"></a>PSRequiredModules \<String[]\>

명령을 실행하기 전에 지정된 모듈을 가져옵니다. 모듈 이름을 입력합니다. 모듈은 대상 컴퓨터에 설치 해야 합니다.

PSModulePath 환경 변수에 지정 된 경로에 설치 된 모듈은 모듈의 명령을 처음 사용할 때 자동으로 가져옵니다.
PSModulePath 위치에 없는 모듈을 가져오려면이 매개 변수를 사용 합니다.

워크플로의 각 활동은 자체 세션에서 실행되기 때문에 Import-Module 명령은 해당 활동이 실행되는 세션으로만 모듈을 가져옵니다. 다른 활동이 실행되는 세션으로 모듈을 가져오지 않습니다.

#### <a name="pssessionoption-pssessionoption"></a>PSSessionOption \<PSSessionOption\>

대상 컴퓨터에 대 한 세션의 고급 옵션을 설정 합니다. New-PSSessionOption cmdlet을 사용 하 여 만든 것과 같은 PSSessionOption 개체를 입력 합니다. 이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

세션 옵션의 기본값은 기본 설정 `$PSSessionOption` 변수의 값 (설정 된 경우)에 따라 결정 됩니다. 그렇지 않으면 세션 구성에 지정 된 값을 사용 합니다.

기본값을 비롯 한 세션 옵션에 대 한 자세한 내용은 New-PSSessionOption cmdlet [새-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)에 대 한 도움말 항목을 참조 하세요.

$PSSessionOption 기본 설정 변수에 대 한 자세한 내용은 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)을 참조 하세요.

#### <a name="psusessl-boolean"></a>PSUseSSL \<Boolean\>

$True 값은 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 대상 컴퓨터에 대 한 연결을 설정 합니다. 기본적으로 SSL은 사용되지 않습니다. $False 값은 영향을 주지 않습니다. 이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.

WS-Management는 네트워크를 통해 전송되는 모든 Windows PowerShell 내용을 암호화합니다. UseSSL은 HTTP 대신 HTTPS를 통해 데이터를 보내는 추가적인 보호 기능입니다. 이 매개 변수를 사용하지만 명령에 사용되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패합니다.

#### <a name="psverbose-psdatacollectionverboserecord"></a>PSVerbose \<PSDataCollection[VerboseRecord]\>

워크플로 작업의 verbose 속성 값 또는 콘솔에 자세한 정보 표시 메시지를 쓰지 않고 활동의 자세한 정보 표시 메시지를 지정 된 자세한 정보 표시 레코드 컬렉션에 추가 합니다. 여러 활동의 자세한 정보 표시 메시지를 동일한 자세한 정보 표시 레코드 컬렉션 개체에 추가할 수 있습니다.

#### <a name="pswarning-psdatacollectionwarningrecord"></a>PSWarning \<PSDataCollection[WarningRecord]\>

워크플로 작업의 경고 속성 값 또는 콘솔에 경고 메시지를 쓰지 않고 활동의 경고 메시지를 지정 된 경고 레코드 컬렉션에 추가 합니다. 여러 활동의 경고 메시지를 동일한 경고 레코드 컬렉션 개체에 추가할 수 있습니다.

#### <a name="result"></a>결과

이 매개 변수는 XAML 워크플로에서만 유효합니다.

#### <a name="usedefaultinput-boolean"></a>UseDefaultInput \<Boolean\>

모든 워크플로 입력을 활동에 대한 입력 값으로 허용합니다.

예를 들어 다음 샘플 워크플로의 Get-Process 활동은 UseDefaultInput 활동 일반 매개 변수를 사용하여 워크플로에 전달된 입력을 가져옵니다. 입력을 사용하여 워크플로를 실행하는 경우 해당 입력이 활동에 의해 사용됩니다.

```powershell
workflow Test-Workflow
{
    Get-Service -UseDefaultInput $True
}

PS C:> Test-Workflow -InputObject WinRm
```

```output
Status   Name        DisplayName                            PSComputerName
------   ----        -----------                            --------------
Running  winrm       Windows Remote Management (WS-Manag... localhost
```

#### <a name="verbose-switchparameter"></a>구문 \<SwitchParameter\>

명령에 의해 수행 된 작업에 대 한 자세한 정보를 표시 합니다.
이 정보는 추적 또는 트랜잭션 로그의 정보와 유사 합니다.
Verbose 매개 변수는 현재 명령에 대 한 $VerbosePreference 변수의 값을 재정의 합니다. 이 매개 변수는 명령이 자세한 정보 메시지를 생성 하는 경우에만 작동 합니다. 이 매개 변수는 Windows PowerShell 일반 매개 변수 이기도 합니다.

#### <a name="warningaction-actionpreference"></a>WarningAction \<ActionPreference\>

활동에서 경고에 응답 하는 방법을 결정 합니다. "Continue"가 기본값입니다. WarningAction 매개 변수는 현재 명령에 대 한 $WarningPreference 변수의 값을 재정의 합니다. 이 매개 변수는 명령에서 경고 메시지를 생성 하는 경우에만 작동 합니다. 이 매개 변수는 Windows PowerShell 일반 매개 변수 이기도 합니다.

유효한 값은

- SilentlyContinue. 경고 메시지를 표시 하지 않고 명령을 계속 실행 합니다.

- 하기. 경고 메시지를 표시 하 고 명령을 계속 실행 합니다.
  "Continue"가 기본값입니다.

- Inquire. 경고 메시지를 표시 하 고 실행을 계속 하기 전에 확인 메시지를 표시 합니다. 이 값은 거의 사용 되지 않습니다.

- 중지 경고 메시지를 표시 하 고 명령 실행을 중지 합니다.

> [!NOTE]
> WarningAction 매개 변수는 스크립트 또는 함수를 실행 하는 명령에 매개 변수가 사용 되는 경우 $WarningAction 기본 설정 변수의 값을 재정의 하지 않습니다.

### <a name="examples"></a>예제

활동 일반 매개 변수는 매우 유용합니다. 예를 들어, PSComputerName 매개 변수를 사용 하 여 대상 컴퓨터의 하위 집합에 대해서만 특정 작업을 실행할 수 있습니다.

또는 PSConnectionRetryCount 및 PSConnectionRetryIntervalSec 매개 변수를 사용 하 여 특정 작업에 대 한 재시도 값을 조정할 수 있습니다.

다음 예제에서는 PSComputerName 활동 일반 매개 변수를 사용 하 여 특정 도메인에 있는 컴퓨터 에서만 Get-EventLog 작업을 실행 하는 방법을 보여 줍니다.

```powershell
Workflow Test-Workflow
{
    $UserDomain = Get-Content -Path '.\UserComputers.txt'
    $Log = (Get-EventLog -LogName "Windows PowerShell" `
      -PSComputerName $UserDomain)

    if ($Log)
    {
        # Do Work Here.
    }
}
```

<!--
# KEYWORDS
[about_Activity_Common_Parameters](about_Activity_Common_Parameters.md)
[about_Activity_Parameters](about_Activity_Parameters.md)
[about_ActivityParameters]()about_ActivityParameters.md) -->

## <a name="see-also"></a>참고 항목

[about_Workflows](about_workflows.md) 
 [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)

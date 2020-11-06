---
description: PowerShell은 엔진, 공급자 및 cmdlet의 내부 작업을 Windows 이벤트 로그에 기록 합니다.
keywords: PowerShell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging-Windows
ms.openlocfilehash: 08b2ad8ecd3451f7cb24600b37fad19cd7fc8161
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354817"
---
# <a name="about-logging-windows"></a>Windows 로깅 정보

## <a name="short-description"></a>간단한 설명
PowerShell은 엔진, 공급자 및 cmdlet의 내부 작업을 Windows 이벤트 로그에 기록 합니다.

## <a name="long-description"></a>자세한 설명입니다.

Powershell은 엔진 및 공급자 시작 및 중지, PowerShell 명령 실행과 같은 PowerShell 작업에 대 한 세부 정보를 기록 합니다.

> [!NOTE]
> Windows PowerShell 버전 3.0, 4.0, 5.0 및 5.1에는 Windows 이벤트 로그에 대 한 **EventLog** cmdlet이 포함 되어 있습니다. 이러한 버전에서 **EventLog** cmdlet의 목록을 표시 하려면:를 입력 `Get-Command -Noun EventLog` 합니다. 자세한 내용은 Windows PowerShell 버전에 대 한 cmdlet 설명서 및 about_EventLogs을 참조 하세요.

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a>Windows에서 PowerShell 이벤트 로그 항목 보기

PowerShell 로그는 Windows 이벤트 뷰어를 사용 하 여 볼 수 있습니다. 이벤트 로그는 응용 프로그램 및 서비스 로그 그룹에 있으며 이름이로 지정 됩니다 `PowerShellCore` . 연결 된 ETW 공급자 `GUID` 는 `{f90714a8-5509-434a-bf6d-b1624c8a19a2}` 입니다.

스크립트 블록 로깅을 사용 하는 경우 PowerShell은 다음 이벤트를 로그에 기록 합니다 `PowerShellCore/Operational` .

|  필드  |       값       |
| ------- | ----------------- |
| EventId | `4104` / `0x1008` |
| 채널 | `Operational`     |
| Level   | `Verbose`         |
| Opcode  | `Create`          |
| Task    | `CommandStart`    |
| 키워드 | `Runspace`        |

### <a name="registering-the-powershell-event-provider-on-windows"></a>Windows에서 PowerShell 이벤트 공급자 등록

Linux 또는 macOS와 달리 Windows에서는 이벤트 로그에 이벤트를 기록 하기 전에 이벤트 공급자를 등록 해야 합니다. PowerShell 이벤트 공급자를 사용 하도록 설정 하려면 관리자 권한 PowerShell 프롬프트에서 다음 명령을 실행 합니다.

```powershell
$PSHOME\RegisterManifest.ps1
```

### <a name="unregistering-the-powershell-event-provider-on-windows"></a>Windows에서 PowerShell 이벤트 공급자 등록 취소

이벤트 공급자를 등록 하면 이벤트를 디코딩하는 데 사용 되는 이진 라이브러리에 잠금이 배치 됩니다. 이 라이브러리를 업데이트 하려면이 잠금을 해제 하기 위해 공급자를 등록 취소 해야 합니다.

PowerShell 공급자의 등록을 취소 하려면 관리자 권한 PowerShell 프롬프트에서 다음 명령을 실행 합니다.

```powershell
$PSHOME\RegisterManifest.ps1 -Unregister
```

PowerShell을 업데이트 한 후를 실행 `$PSHOME\RegisterManifest.ps1` 하 여 업데이트 된 이벤트 공급자를 등록 합니다.

## <a name="enabling-script-block-logging"></a>스크립트 블록 로깅 사용

스크립트 블록 로깅을 사용 하는 경우 PowerShell은 처리 하는 모든 스크립트 블록의 콘텐츠를 기록 합니다. 사용 하도록 설정 되 면 모든 새 PowerShell 세션에서이 정보를 기록 합니다.

> [!NOTE]
> 진단이 아닌 다른 항목에 대해 스크립트 블록 로깅을 사용 하는 경우 아래에 설명 된 대로 보호 된 이벤트 로깅을 사용 하는 것이 좋습니다.

스크립트 블록 로깅은 그룹 정책 또는 레지스트리 설정을 통해 사용 하도록 설정할 수 있습니다.

### <a name="using-group-policy"></a>그룹 정책을 사용 하 여

자동 기록을 사용 하도록 설정 하려면 그룹 정책에서 기능을 사용 하도록 설정 `Turn on PowerShell Script Block
Logging` `Administrative Templates -> Windows
Components -> Windows PowerShell` 합니다.

### <a name="using-the-registry"></a>레지스트리 사용

다음 함수를 실행 합니다.

```powershell
function Enable-PSScriptBlockLogging
{
    $basePath = 'HKLM:\Software\Policies\Microsoft\Windows' +
      '\PowerShell\ScriptBlockLogging'

    if(-not (Test-Path $basePath))
    {
        $null = New-Item $basePath -Force
    }

    Set-ItemProperty $basePath -Name EnableScriptBlockLogging -Value "1"
}
```

## <a name="protected-event-logging"></a>보호 된 이벤트 로깅

시스템에 대 한 로깅 수준을 높이면 기록 된 콘텐츠에 중요 한 데이터가 포함 될 가능성이 높아집니다. 예를 들어 스크립트 로깅을 사용 하는 경우 스크립트에서 사용 하는 자격 증명 또는 기타 중요 한 데이터를 이벤트 로그에 쓸 수 있습니다. 중요 한 데이터를 기록 하는 컴퓨터가 손상 된 경우 로그는 해당 연결을 확장 하는 데 필요한 정보를 공격자에 게 제공할 수 있습니다.

이 정보를 보호 하기 위해 Windows 10에서는 보호 된 이벤트 로깅을 소개 합니다.
보호 된 이벤트 로깅을 사용 하면 참여 응용 프로그램에서 이벤트 로그에 기록 된 중요 한 데이터를 암호화할 수 있습니다. 나중에 보다 안전 하 고 중앙 집중식 로그 수집기에서 이러한 로그를 해독 하 고 처리할 수 있습니다.

이벤트 로그 내용은 IETF CMS (암호화 메시지 구문) 표준을 사용 하 여 보호 됩니다. CMS는 공개 키 암호화를 사용 합니다. 콘텐츠를 암호화 하 고 암호를 해독 하는 데 사용 되는 키는 분리 된 상태로 유지 됩니다.

공개 키는 광범위 하 게 공유할 수 있으며 중요 한 데이터가 아닙니다. 이 공개 키로 암호화 된 콘텐츠는 개인 키로만 해독할 수 있습니다. 공개 키 암호화에 대 한 자세한 내용은 [위키백과-공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조 하세요.

보호 된 이벤트 로깅 정책을 사용 하도록 설정 하려면 보호할 이벤트 로그 데이터가 있는 모든 컴퓨터에 공개 키를 배포 합니다. 해당 개인 키는 중앙 이벤트 로그 수집기 또는 [Siem][] 집계와 같은 보다 안전한 위치에서 이벤트 로그를 사후 처리 하는 데 사용 됩니다. Azure에서 SIEM을 설정할 수 있습니다. 자세한 내용은 [일반 SIEM 통합](/cloud-app-security/siem)을 참조 하세요.

### <a name="enabling-protected-event-logging-via-group-policy"></a>그룹 정책를 통해 보호 된 이벤트 로깅 사용

보호 된 이벤트 로깅을 사용 하도록 설정 하려면 `Enable Protected Event Logging` 그룹 정책에서로 기능을 사용 하도록 설정 `Administrative Templates -> Windows Components
-> Event Logging` 합니다. 이 설정에는 암호화 인증서가 필요 하며,이 인증서는 다음과 같은 여러 형식 중 하나로 제공할 수 있습니다.

- Base-64로 인코딩된 x.509 인증서 (예: `Export` 인증서 관리자의 옵션에서 제공 하는)의 콘텐츠입니다.
- 로컬 컴퓨터 인증서 저장소에서 찾을 수 있는 인증서의 지문입니다 (PKI 인프라로 배포할 수 있음).
- 인증서에 대 한 전체 경로입니다 (로컬 또는 원격 공유 일 수 있음).
- 인증서 또는 인증서를 포함 하는 디렉터리의 경로 (로컬 또는 원격 공유 일 수 있음)입니다.
- 로컬 컴퓨터 인증서 저장소에서 찾을 수 있는 인증서의 주체 이름입니다 (PKI 인프라로 배포할 수 있음).

결과 인증서에 확장 된 `Document Encryption` 키 사용 ( `1.3.6.1.4.1.311.80.1` )이 있어야 하 고 `Data Encipherment` 또는 키 사용이 `Key
Encipherment` 사용 하도록 설정 되어 있어야 합니다.

> [!WARNING]
> 개인 키는 컴퓨터 로깅 이벤트에 배포할 수 없습니다. 메시지를 암호 해독 하는 안전한 위치에 보관 해야 합니다.

### <a name="decrypting-protected-event-logging-messages"></a>보호 된 이벤트 로깅 메시지 암호 해독

다음 스크립트는 개인 키가 있는 것으로 가정 하 여를 검색 하 고 암호를 해독 합니다.

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a>참고 항목

[about_Logging_Non-Windows](about_Logging_Non-Windows.md)

[PowerShell 블루 팀](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[일반 SIEM 통합](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management

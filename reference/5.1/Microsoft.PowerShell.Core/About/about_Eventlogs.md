---
description: Windows powershell은 windows powershell 이벤트를 기록 하는 "Windows PowerShell" 이라는 Windows 이벤트 로그를 만듭니다. 이 로그는 이벤트 뷰어에서 볼 수도 있고 cmdlet과 같이 이벤트를 가져오는 cmdlet을 사용 하 여 볼 수도 있습니다 `Get-EventLog` . 기본적으로 Windows PowerShell 엔진 및 공급자 이벤트는 이벤트 로그에 기록 되지만 이벤트 로그 기본 설정 변수를 사용 하 여 이벤트 로그를 사용자 지정할 수 있습니다. 예를 들어 Windows PowerShell 명령에 대 한 이벤트를 추가할 수 있습니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_eventlogs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Eventlogs
ms.openlocfilehash: eb92333c6a6e220e287dcbec1441d2d05aa9275b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223506"
---
# <a name="about-eventlogs"></a>Eventlogs 정보

## <a name="short-description"></a>간단한 설명

Windows powershell은 windows powershell 이벤트를 기록 하는 "Windows PowerShell" 이라는 Windows 이벤트 로그를 만듭니다. 이 로그는 이벤트 뷰어에서 볼 수도 있고 cmdlet과 같이 이벤트를 가져오는 cmdlet을 사용 하 여 볼 수도 있습니다 `Get-EventLog` . 기본적으로 Windows PowerShell 엔진 및 공급자 이벤트는 이벤트 로그에 기록 되지만 이벤트 로그 기본 설정 변수를 사용 하 여 이벤트 로그를 사용자 지정할 수 있습니다. 예를 들어 Windows PowerShell 명령에 대 한 이벤트를 추가할 수 있습니다.

## <a name="long-description"></a>자세한 설명

Windows PowerShell 이벤트 로그는 프로그램 엔진 시작 및 중지, Windows PowerShell 공급자 시작 및 중지와 같은 Windows PowerShell 작업에 대 한 세부 정보를 기록 합니다. Windows PowerShell 명령에 대 한 세부 정보를 기록할 수도 있습니다.

Windows PowerShell 이벤트 로그는 응용 프로그램 및 서비스 로그 그룹에 있습니다. Windows PowerShell 로그는 Windows 이벤트 기술을 사용 하지 않는 클래식 이벤트 로그입니다. 로그를 보려면와 같은 클래식 이벤트 로그에 대해 디자인 된 cmdlet을 사용 `Get-EventLog` 합니다.

## <a name="viewing-the-windows-powershell-event-log"></a>Windows PowerShell 이벤트 로그 보기

이벤트 뷰어에서 또는 및 cmdlet을 사용 하 여 Windows PowerShell 이벤트 로그를 볼 수 있습니다 `Get-EventLog` `Get-WmiObject` . Windows PowerShell 로그의 내용을 보려면 다음을 입력 합니다.

```powershell
Get-EventLog -LogName "Windows PowerShell"
```

이벤트 및 해당 속성을 검사 하려면 cmdlet, cmdlet `Sort-Object` `Group-Object` 및 `Format` 동사 (cmdlet)를 포함 하는 cmdlet을 사용 `Format` 합니다.

예를 들어 이벤트 ID 별로 그룹화 된 로그의 이벤트를 보려면 다음과 같이 입력 합니다.

```powershell
Get-EventLog "Windows PowerShell" | Format-Table -GroupBy EventID
```

또는 다음과 같이 입력 합니다.

```powershell
Get-EventLog "Windows PowerShell" |
  Sort-Object EventID |
  Group-Object EventID
```

모든 클래식 이벤트 로그를 보려면 다음과 같이 입력 합니다.

```powershell
Get-EventLog -List
```

Cmdlet을 사용 하 여 이벤트 `Get-WmiObject` 관련 WMI(Windows Management Instrumentation) (WMI) 클래스를 사용 하 여 이벤트 로그를 검사할 수도 있습니다. 예를 들어 이벤트 로그 파일의 모든 속성을 보려면 다음을 입력 합니다.

```powershell
Get-WmiObject Win32_NTEventlogFile |
  where LogFileName -EQ "Windows PowerShell" |
  Format-List -Property *
```

Win32 이벤트 관련 WMI 클래스를 찾으려면 다음을 입력 합니다.

```powershell
Get-WmiObject -List | where Name -Like "win32*event*"
```

자세한 내용을 보려면 "Get-help get-EventLog" 및 "Get-help Get-wmiobject"를 입력 하십시오.

## <a name="selecting-events-for-the-windows-powershell-event-log"></a>Windows PowerShell 이벤트 로그에 대 한 이벤트 선택

이벤트 로그 기본 설정 변수를 사용 하 여 Windows PowerShell 이벤트 로그에 기록 되는 이벤트를 확인할 수 있습니다.

6 개의 이벤트 로그 기본 설정 변수가 있습니다. 세 가지 로깅 구성 요소 각각에 대 한 두 가지 변수: 엔진 (Windows PowerShell 프로그램), 공급자 및 명령입니다. LifeCycleEvent 변수는 정상적으로 시작 하 고 중지 하는 이벤트를 기록 합니다. 상태 변수는 오류 이벤트를 기록 합니다.

다음 표에서는 이벤트 로그 기본 설정 변수를 보여 줍니다.

|변수                  |Description                                    |
|--------------------------|-----------------------------------------------|
|$LogEngineLifeCycleEvent  |PowerShell의 시작 및 중지를 로깅합니다.          |
|$LogEngineHealthEvent     |PowerShell 프로그램 오류를 기록 합니다.                 |
|$LogProviderLifeCycleEvent|PowerShell 공급자의 시작 및 중지를 로깅합니다.|
|$LogProviderHealthEvent   |로그 PowerShell 공급자 오류                |
|$LogCommandLifeCycleEvent |명령의 시작 및 완료를 로깅합니다.   |
|$LogCommandHealthEvent    |명령 오류 기록                            |

Windows PowerShell 공급자에 대 한 자세한 내용은 [about_Providers](about_Providers.md)를 참조 하세요.

기본적으로 다음 이벤트 유형만 사용 됩니다.

* $LogEngineLifeCycleEvent
* $LogEngineHealthEvent
* $LogProviderLifeCycleEvent
* $LogProviderHealthEvent

이벤트 유형을 사용 하도록 설정 하려면 해당 이벤트 유형에 대 한 기본 설정 변수를 $true 설정 합니다. 예를 들어, 명령 수명 주기 이벤트를 사용 하려면 다음을 입력 합니다.

```powershell
$LogCommandLifeCycleEvent
```

또는 다음과 같이 입력 합니다.

```powershell
$LogCommandLifeCycleEvent = $true
```

이벤트 유형을 사용 하지 않도록 설정 하려면 해당 이벤트 유형에 대 한 기본 설정 변수를 $false 설정 합니다. 예를 들어, 명령 수명 주기 이벤트를 사용 하지 않도록 설정 하려면 다음을 입력 합니다.

```powershell
$LogProviderLifeCycleEvent = $false
```

Windows PowerShell 엔진과 핵심 공급자가 시작 되었음을 나타내는 이벤트를 제외 하 고 모든 이벤트를 사용 하지 않도록 설정할 수 있습니다. 이러한 이벤트는 Windows PowerShell 프로필이 실행 되기 전에 호스트 프로그램에서 명령을 수락할 준비가 되기 전에 생성 됩니다.

변수 설정은 현재 Windows PowerShell 세션에만 적용 됩니다.
모든 Windows PowerShell 세션에 적용 하려면 Windows PowerShell 프로필에 추가 합니다.

## <a name="logging-module-events"></a>모듈 이벤트 로깅

Windows PowerShell 3.0부터 모듈 및 스냅인의 LogPipelineExecutionDetails 속성을 TRUE로 설정 하 여 Windows PowerShell 모듈 및 스냅인의 cmdlet 및 함수에 대 한 실행 이벤트를 기록할 수 있습니다. Windows PowerShell 2.0에서이 기능은 스냅인에 대해서만 사용할 수 있습니다.

LogPipelineExecutionDetails 속성 값이 TRUE () 인 경우 `$true` Windows powershell은 세션의 cmdlet 및 함수 실행 이벤트를 Windows powershell 로그인 이벤트 뷰어에 기록 합니다. 설정은 현재 세션 에서만 적용 됩니다.

모듈의 cmdlet 및 함수에 대 한 실행 이벤트 로깅을 사용 하도록 설정 하려면 다음 명령 시퀀스를 사용 합니다.

```powershell
Import-Module <ModuleName>
$m = Get-Module <ModuleName>
$m.LogPipelineExecutionDetails = $true
```

스냅인에서 cmdlet의 실행 이벤트 로깅을 사용 하도록 설정 하려면 다음 명령 시퀀스를 사용 합니다.

```powershell
$m = Get-PSSnapin <SnapInName> [-Registered]
$m.LogPipelineExecutionDetails = $True
```

로깅을 사용 하지 않도록 설정 하려면 동일한 명령 시퀀스를 사용 하 여 속성 값을 FALSE ()로 설정 `$false` 합니다.

"모듈 로깅 켜기" 그룹 정책 설정을 사용 하 여 모듈 및 스냅인 로깅을 사용 하거나 사용 하지 않도록 설정할 수도 있습니다. 정책 값에는 모듈 및 스냅인 이름 목록이 포함 됩니다. 와일드카드가 지원됩니다.

모듈에 대해 "모듈 로깅 켜기"가 설정 된 경우 모듈의 LogPipelineExecutionDetails 속성 값은 모든 세션에서 TRUE 이며 변경할 수 없습니다.

모듈 로깅 켜기 그룹 정책 설정은 다음 그룹 정책 경로에 있습니다.

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
     Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

사용자 구성 정책이 컴퓨터 구성 정책 보다 우선적으로 적용 되 고 두 정책은 모두 모듈 및 스냅인의 LogPipelineExecutionDetails 속성 값에 우선 합니다.

이 그룹 정책 설정에 대 한 자세한 내용은 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)을 참조 하세요.

## <a name="security-and-auditing"></a>보안 및 감사

Windows PowerShell 이벤트 로그는 활동을 표시 하 고 문제 해결을 위한 작업 세부 정보를 제공 하도록 설계 되었습니다.

그러나 대부분의 Windows 기반 응용 프로그램 이벤트 로그와 마찬가지로 Windows PowerShell 이벤트 로그는 안전 하지 않도록 설계 되었습니다. 보안을 감사 하거나 기밀 정보나 독점 정보를 기록 하는 데 사용 하면 안 됩니다.

이벤트 로그는 사용자가 읽고 이해할 수 있도록 설계 되었습니다. 사용자는 로그에서 읽고 로그에 쓸 수 있습니다. 악의적인 사용자가 로컬 또는 원격 컴퓨터에서 이벤트 로그를 읽고 false 데이터를 기록한 다음 해당 작업의 로깅을 방지할 수 있습니다.

## <a name="notes"></a>메모

모듈 작성자의 작성자는 해당 모듈에 로깅 기능을 추가할 수 있습니다. 자세한 내용은 [Windows PowerShell 모듈 작성](/powershell/scripting/developer/module/writing-a-windows-powershell-module)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[Get-EventLog](xref:Microsoft.PowerShell.Management.Get-EventLog)

[Get-WmiObject](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Preference_Variables](about_Preference_Variables.md)

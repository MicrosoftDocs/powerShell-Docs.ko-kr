---
description: PowerShell은 엔진, 공급자 및 cmdlet에서 내부 작업을 기록 합니다.
keywords: PowerShell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_non-windows?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging_Non-Windows
ms.openlocfilehash: 5face386a479a0264f5ff2ba3f6665cb1e218a4a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220458"
---
# <a name="about-logging-non-windows"></a>비 Windows 로깅 정보

## <a name="short-description"></a>간단한 설명

PowerShell은 엔진, 공급자 및 cmdlet에서 내부 작업을 기록 합니다.

## <a name="long-description"></a>자세한 설명입니다.

Powershell 작업에 대 한 세부 정보를 기록 합니다. 예를 들어 PowerShell은 엔진을 시작 및 중지 하 고 공급자를 시작 및 중지 하는 등의 작업을 기록 합니다. PowerShell 명령에 대 한 세부 정보도 기록 합니다.

PowerShell 로그의 위치는 대상 플랫폼에 따라 달라 집니다. **Linux** 에서는 **syslog** 및 **rsyslog** 에 PowerShell 로그를 사용할 수 있습니다. 자세한 내용은 Linux 컴퓨터의 로컬 페이지를 참조 `man` 하세요. **Macos** 에서 **os_log** 로깅 시스템이 사용 됩니다. 자세한 내용은 [os_log 개발자 설명서](https://developer.apple.com/documentation/os/os_log)를 참조 하세요.

## <a name="viewing-powershell-log-output-on-linux"></a>Linux에서 PowerShell 로그 출력 보기

Linux의 **syslog** 에 대 한 PowerShell 로그 및 **syslog** 콘텐츠를 보는 데 일반적으로 사용 되는 모든 도구를 사용할 수 있습니다.

로그 항목의 형식은 다음 템플릿을 사용 합니다.

```
TIMESTAMP MACHINENAME powershell[PID]: (COMMITID:TID:CID)
  [EVENTID:TASK.OPCODE.LEVEL] MESSAGE
```

|필드        |Description                                             |
|-------------|--------------------------------------------------------|
|`TIMESTAMP`  |로그 항목이 생성 된 날짜/시간입니다.            |
|`MACHINENAME`|로그가 생성 된 시스템의 이름입니다.      |
|`PID`        |로그 항목을 작성 한 프로세스의 프로세스 ID입니다. |
|`COMMITID`   |`git commit`빌드를 생성 하는 데 사용 되는 ID 또는 태그입니다.   |
|`TID`        |로그 항목을 쓴 스레드의 스레드 ID입니다.   |
|`CID`        |로그 항목의 16 진수 채널 식별자입니다.            |
|             |10 = 작동, 11 = 분석                         |
|`EVENTID`    |로그 항목의 이벤트 식별자입니다.                  |
|`TASK`       |이벤트 항목에 대 한 작업 식별자입니다.                 |
|`OPCODE`     |이벤트 엔트리의 opcode입니다.                          |
|`LEVEL`      |이벤트 항목의 로그 수준입니다.                       |
|`MESSAGE`    |이벤트 항목과 연결 된 메시지입니다.             |

> [!NOTE]
> `EVENTID`, `TASK` , `OPCODE` 및는 `LEVEL` Windows 이벤트 로그에 로깅할 때 사용 되는 것과 동일한 값입니다.

### <a name="filtering-powershell-log-entries-using-rsyslog"></a>Rsyslog를 사용 하 여 PowerShell 로그 항목 필터링

일반적으로 PowerShell 로그 항목은 syslog의 기본값에 기록 됩니다 `location/file` . **syslog** 그러나 항목을 사용자 지정 파일로 리디렉션할 수 있습니다.

1. PowerShell 로그 구성에 대 한 회의를 만들고와 같이 50 보다 작은 숫자를 제공 `50-default.conf` `40-powershell.conf` 합니다. 파일은 아래에 배치 해야 합니다 `/etc/rsyslog.d` .

1. 파일에 다음 항목을 추가 합니다.

   ```
   :syslogtag, contains, "powershell[" /var/log/powershell.log
   & stop
   ```

1. `/etc/rsyslog.conf`새 파일이 포함 되어 있는지 확인 합니다. 종종 다음과 같은 구성 처럼 일반 include 문을 사용할 수 있습니다.

   `$IncludeConfig /etc/rsyslog.d/*.conf`

   그렇지 않은 경우 include 문을 수동으로 추가 해야 합니다.

1. 특성 및 사용 권한이 적절 하 게 설정 되었는지 확인 합니다.

   ```
   -rw-r--r-- 1 root root   67 Nov 28 12:51 40-powershell.conf
   ```

1. 소유권을 **root** 로 설정 합니다.

   ```
   chown root:root /etc/rsyslog.d/40-powershell.conf
   ```

1. 액세스 권한 설정: **루트** 에 읽기/쓰기 권한이 있으며 **사용자** 는 읽기 권한이 있습니다.

   ```
   chmod 644 /etc/rsyslog.d/40-powershell.conf
   ```

## <a name="viewing-powershell-log-output-on-macos"></a>MacOS에서 PowerShell 로그 출력 보기

MacOS에서 PowerShell 로그 출력을 보는 가장 쉬운 방법은 **콘솔** 응용 프로그램을 사용 하는 것입니다.

1. **콘솔** 응용 프로그램을 검색 하 여 시작 합니다.
1. **장치** 에서 컴퓨터 이름을 선택 합니다.
1. **Search** `pwsh` PowerShell 주 이진에 대해 검색 필드에를 입력 합니다.
1. 검색 필터를에서로 변경 합니다 `Any` `Process` .
1. 작업을 수행 합니다.
1. 필요에 따라 나중에 사용 하기 위해 검색을 저장 합니다.

**콘솔** 에서 PowerShell의 특정 프로세스 인스턴스를 필터링 하기 위해 변수는 `$pid` 프로세스 ID를 포함 합니다.

1. **검색** 필드에 **PID** (프로세스 ID)를 입력 합니다.
1. 검색 필터를로 변경 `PID` 합니다.
1. 작업을 수행 합니다.

### <a name="viewing-powershell-log-output-from-a-command-line"></a>명령줄에서 PowerShell 로그 출력 보기

명령을 `log` 사용 하 여 명령줄에서 PowerShell 로그 항목을 볼 수 있습니다.

```
sudo log stream --predicate 'process == "pwsh"' --info
```

### <a name="persisting-powershell-log-output"></a>PowerShell 로그 출력 유지

기본적으로 PowerShell은 macOS에서 기본 메모리 전용 로깅을 사용 합니다. 명령을 사용 하 여 지 속성을 사용 하도록 설정 하면이 동작을 변경할 수 있습니다 `log config` .

다음 스크립트는 정보 수준 로깅 및 지 속성을 사용 하도록 설정 합니다.

```
log config --subsystem com.microsoft.powershell --mode=persist:info,level:info
```

다음 명령은 PowerShell 로깅을 기본 상태로 되돌립니다.

```
log config --subsystem com.microsoft.powershell --mode=persist:default,level:default
```

지 속성을 사용 하도록 설정한 후에는 `log show` 명령을 사용 하 여 로그 항목을 내보낼 수 있습니다. 명령은 마지막 N 개 항목, 지정 된 시간 이후의 항목 또는 지정 된 시간 범위 내의 항목을 내보내기 위한 옵션을 제공 합니다.

예를 들어 다음 명령은 이후 항목을 내보냅니다 `9am on April 5 of 2018` .

```
log show --info --start "2018-04-05 09:00:00" --predicate "process = 'pwsh'"
```

`log`추가 정보는를 실행 하 여에 대 한 도움말을 볼 수 있습니다 `log show --help` .

> [!TIP]
> PowerShell 프롬프트 또는 스크립트에서 로그 명령을 실행할 때 전체 조건자 문자열과 작은따옴표를 큰따옴표로 묶습니다. 이렇게 하면 조건자 문자열 내에서 큰따옴표 문자를 이스케이프 하지 않아도 됩니다.

또한 이벤트 로그를 중앙 이벤트 로그 수집기 또는 [Siem][] 집계와 같은 보다 안전한 위치에 저장 하는 것을 고려할 수 있습니다. Azure에서 SIEM을 설정할 수 있습니다. 자세한 내용은 [일반 SIEM 통합](/cloud-app-security/siem)을 참조 하세요.

## <a name="configuring-logging-on-a-non-windows-system"></a>비 Windows 시스템에 대 한 로깅 구성

Windows에서는 ETW 추적 수신기를 만들거나 이벤트 뷰어를 사용 하 여 분석 로깅을 사용 하도록 설정 하 여 로깅을 구성 합니다. Linux 및 macOS에서 로깅은 파일을 사용 하 여 구성 됩니다 `powershell.config.json` . 이 섹션의 나머지 부분에서는 비 Windows 시스템에 대 한 PowerShell 로깅을 구성 하는 방법을 설명 합니다.

기본적으로 PowerShell은 작업 채널에 대 한 정보 로깅을 사용 하도록 설정 합니다. 즉, 작업으로 표시 되 고 정보 보다 더 높은 로그 (추적) 수준을 기록 하는 PowerShell에서 생성 되는 로그 출력을 의미 합니다. 때로는 진단에 자세한 로그 출력과 같은 추가 로그 출력이 필요 하거나 분석 로그 출력을 사용 하도록 설정할 수 있습니다.

이 파일은 `powershell.config.json` PowerShell 디렉터리에 상주 하는 **JSON** 형식의 파일입니다 `$PSHOME` . PowerShell을 설치할 때마다이 파일의 복사본을 사용 합니다. 일반 작업의 경우이 파일은 변경 되지 않고 그대로 유지 됩니다. 파일의 일부 설정을 변경 하는 것이 유용할 수 있지만, 동일한 시스템 또는 동일한 버전의 여러 복사본 (아래 표 참조)에 대 한 여러 PowerShell 버전을 진단 하거나 구분 하기 위해 파일의 일부 설정을 변경 하는 것이 유용할 수 있습니다 `LogIdentity` .

다음 코드는 구성의 예입니다.

```json
{
  "Microsoft.PowerShell:ExecutionPolicy": "RemoteSigned",
  "PowerShellPolicies": {
    "ScriptExecution": {
      "ExecutionPolicy": "RemoteSigned",
      "EnableScripts": true
    },
    "ScriptBlockLogging": {
      "EnableScriptBlockInvocationLogging": true,
      "EnableScriptBlockLogging": true
    },
    "ModuleLogging": {
      "EnableModuleLogging": false,
      "ModuleNames": [
        "PSReadline",
        "PowerShellGet"
      ]
    },
    "ProtectedEventLogging": {
      "EnableProtectedEventLogging": false,
      "EncryptionCertificate": [
        "Joe"
      ]
    },
    "Transcription": {
      "EnableTranscripting": true,
      "EnableInvocationHeader": true,
      "OutputDirectory": "F:\\tmp\\new"
    },
    "UpdatableHelp": {
      "DefaultSourcePath": "f:\\temp"
    },
    "ConsoleSessionConfiguration": {
      "EnableConsoleSessionConfiguration": false,
      "ConsoleSessionConfigurationName": "name"
    }
  },
  "LogLevel": "verbose"
}
```

PowerShell 로깅 구성에 대 한 속성은 다음 표에 나와 있습니다. 와 같이 별표가 표시 된 값 `Operational*` 은 파일에 값이 제공 되지 않은 경우 기본값을 표시 합니다.

|속성   |값        |Description                                  |
|-----------|--------------|---------------------------------------------|
|`LogIdentity`|(문자열 이름) |로깅할 때 사용할 이름입니다. 기본적으로  |
|           |슬래시   |powershell은 id입니다. 이 값은 일 수 있습니다.|
|           |              |두의 차이를 알리는 데 사용 됩니다.      |
|           |              |PowerShell 설치 인스턴스 (예:) |
|           |              |릴리스 및 베타 버전으로 이 값은 |
|           |              |로그 출력을로 리디렉션하는 데도 사용 됩니다.        |
|           |              |Linux에서 파일을 분리 합니다. 다음에 대 한 설명을 참조 하세요.|
|           |              |위의 **rsyslog**                           |
|`LogChannels`|주기와  |사용할 채널입니다. 값 구분|
|           |Analytic      |하나 이상의을 지정할 때 쉼표를 사용 합니다.  |
|`LogLevel`   |Always        |단일 값을 지정 합니다. 이 값을 사용 하면  |
|           |중요      |그리고 그 위에 있는 모든 값은        |
|           |오류         |왼쪽에 나열 됩니다.                            |
|           |경고       |                                             |
|           |위해서|                                             |
|           |자세히       |                                             |
|           |디버그         |                                             |
|`LogKeywords`|Runspace      |키워드는 로깅을 제한 하는 기능을 제공 합니다.|
|           |파이프라인      |PowerShell 내의 특정 구성 요소에 적용 됩니다. 기준 |
|           |프로토콜      |기본값, 모든 키워드를 사용 하도록 설정 및 변경 |
|           |전송     |이 값은 매우 유용 합니다.           |
|           |호스트          |특수 한 문제 해결.                |
|           |Cmdlet       |                                             |
|           |serializer    |                                             |
|           |세션       |                                             |
|           |ManagedPlugin |                                             |

## <a name="see-also"></a>참고 항목

Linux **syslog** 및 **Rsyslog** 의 경우 linux 컴퓨터의 로컬 페이지를 참조 하세요 `man` .

MacOS **os_log** 내용은 [os_log 개발자 설명서](https://developer.apple.com/documentation/os/os_log)를 참조 하세요.

[about_Logging_Windows](about_Logging_Windows.md)

[일반 SIEM 통합](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management


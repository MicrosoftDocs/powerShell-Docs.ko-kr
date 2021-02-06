---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: 6e7fd1c6eb3551906b4dd9d947b5e551cd05d30a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603306"
---
# Set-TraceSource

## 개요
PowerShell 구성 요소의 추적을 구성, 시작 및 중지 합니다.

## SYNTAX

### 기본 설정 (기본값)

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### removeAllListenersSet

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### removeFileListenersSet

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## 설명

**TraceSource** Cmdlet은 PowerShell 구성 요소의 추적을 구성, 시작 및 중지 합니다.
이 cmdlet을 사용하면 추적할 구성 요소 및 추적한 출력을 보낼 위치를 지정할 수 있습니다.

## 예제

### 예제 1: ParameterBinding 구성 요소 추적

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

이 명령은 PowerShell의 ParameterBinding 구성 요소에 대 한 추적을 시작 합니다.
*Name* 매개 변수를 사용 하 여 추적 원본을 지정 하 고 *Option* 매개 변수를 사용 하 여 executionflow 추적 이벤트를 선택 하 고 *PSHost* 매개 변수를 사용 하 여 출력을 콘솔로 보내는 PowerShell 호스트 수신기를 선택 합니다.
*ListenerOption* 매개 변수는 추적 메시지 접두사에 ProcessID 및 TimeStamp 값을 추가 합니다.

### 예 2: 추적 중지

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

이 명령은 PowerShell의 ParameterBinding 구성 요소에 대 한 추적을 중지 합니다.
*Name* 매개 변수를 사용 하 여 추적 중인 구성 요소를 식별 하 고 *RemoveListener* 매개 변수를 사용 하 여 추적 수신기를 식별 합니다.

## PARAMETERS

### -디버거

Cmdlet이 추적 출력을 디버거로 보낼지 여부를 나타냅니다.
사용자 모드 또는 커널 모드 디버거나 Microsoft Visual Studio에서 출력을 볼 수 있습니다.
이 매개 변수는 기본 추적 수신기도 선택합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

이 cmdlet이 추적 출력을 전송 하는 파일을 지정 합니다.
이 매개 변수는 파일 추적 수신기도 선택합니다.
이 매개 변수를 사용 하 여 추적을 시작 하는 경우 *Removefilelistener* 매개 변수를 사용 하 여 추적을 중지 합니다.

```yaml
Type: System.String
Parameter Sets: optionsSet
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Cmdlet이 읽기 전용 파일을 덮어쓰도록 지정 합니다.
*FilePath* 매개 변수와 함께 사용 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ListenerOption

출력에서 각 추적 메시지의 접두사에 대 한 선택적 데이터를 지정 합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 없음
- LogicalOperationStack
- DateTime
- 타임스탬프
- ProcessId
- 스레드 Id
- 호출 스택

없음이 기본값입니다.

여러 옵션을 지정하려면 "ProcessID,ThreadID"와 같이 공백 없이 쉼표로 구분하고 따옴표로 묶습니다.

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

추적할 구성 요소를 지정 합니다.
각 구성 요소의 추적 원본 이름을 입력합니다.
와일드카드가 지원됩니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -옵션

추적 되는 이벤트의 유형을 지정 합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 없음
- 생성자
- Dispose
- Finalizer
- 메서드
- 속성
- 대리자
- 이벤트
- 예외
- 잠금
- Error
- 오류
- 경고
- 자세히
- WriteLine
- 데이터
- Scope
- ExecutionFlow
- Assert
- 모두

All이 기본값입니다.

다음 값은 다른 값의 조합입니다.

- ExecutionFlow: (Constructor, Dispose, Finalizer, Method, 대리자, 이벤트 및 범위)
- 데이터: (Constructor, Dispose, Finalizer, Property, Verbose 및 WriteLine)
- 오류: (오류 및 예외).

여러 옵션을 지정하려면 "Constructor,Dispose"와 같이 공백 없이 쉼표로 구분하고 따옴표로 묶습니다.

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

작업 중인 항목을 나타내는 개체를 반환합니다.
기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSHost

이 cmdlet은 PowerShell 호스트로 추적 출력을 ndicates 합니다.
이 매개 변수는 PSHost 추적 수신기도 선택합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveFileListener

지정된 파일과 연결된 파일 추적 수신기를 제거하여 추적을 중지합니다.
추적 출력 파일의 경로와 파일 이름을 입력하세요.

```yaml
Type: System.String[]
Parameter Sets: removeFileListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveListener

추적 수신기를 제거하여 추적을 중지합니다.

*RemoveListener* 에 다음 값을 사용 합니다.

- PSHost (콘솔)를 제거 하려면을 입력 `Host` 합니다.
- 디버거를 제거 하려면을 입력 `Debug` 합니다.
- 모든 추적 수신기를 제거 하려면을 입력 `*` 합니다.

파일 추적 수신기를 제거 하려면 *Removefilelistener* 매개 변수를 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: removeAllListenersSet
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

### System.String

이름이 포함 된 문자열을 **TraceSource** 로 파이프 할 수 있습니다.

## 출력

### None 또는 System.object입니다.

*PassThru* 매개 변수를 사용 하는 경우 **TraceSource** 는 추적 세션을 나타내는 **system.object** 를 생성 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

* 추적은 개발자가 디버깅하고 프로그램을 다듬는 데 사용하는 방법입니다. 추적하면 프로그램에서 내부 프로세스의 각 단계에 대한 세부 메시지를 생성합니다.

  Powershell 추적 cmdlet은 PowerShell 개발자를 돕기 위해 설계 되었지만 모든 사용자가 사용할 수 있습니다.
이를 통해 PowerShell 기능의 거의 모든 측면을 모니터링할 수 있습니다.

  추적 소스는 추적을 관리 하 고 구성 요소에 대 한 추적 메시지를 생성 하는 각 PowerShell 구성 요소의 일부입니다.
구성 요소를 추적하려면 추적 원본을 확인하세요.

  추적 수신기는 추적의 출력을 받아 사용자에 게 표시 합니다.
사용자 모드 또는 커널 모드 디버거, 콘솔, 파일 또는 **TraceListener** 클래스에서 파생 된 사용자 지정 수신기로 추적 데이터를 보내도록 선택할 수 있습니다.

* 추적을 시작 하려면 *Name* 매개 변수를 사용 하 여 추적 소스를 지정 하 고 *FilePath*, *Debugger* 또는 *PSHost* 매개 변수를 사용 하 여 수신기 (출력의 대상)를 지정 합니다. *Options* 매개 변수를 사용 하 여 추적 되는 이벤트 유형을 확인 하 고 *ListenerOption* 매개 변수를 사용 하 여 추적 출력을 구성 합니다.
* 추적의 구성을 변경 하려면 **TraceSource** 명령을 입력 하 여 추적을 시작 합니다. PowerShell에서 추적 원본이 이미 추적 되 고 있음을 인식 합니다. 그다음 추적을 중지하고 새 구성을 추가한 다음 추적을 시작하거나 다시 시작합니다.
* 추적을 중지 하려면 *RemoveListener* 매개 변수를 사용 합니다. 파일 수신기를 사용 하는 추적 ( *FilePath* 매개 변수를 사용 하 여 시작 된 추적)을 중지 하려면 *removefilelistener* 매개 변수를 사용 합니다. 수신기를 제거하면 추적이 중지됩니다.
* 추적할 수 있는 구성 요소를 확인하려면 Get-TraceSource를 사용합니다. 각 모듈에 대 한 추적 소스는 구성 요소가 사용 중일 때 자동으로 로드 되며 **TraceSource** 의 출력에 표시 됩니다.

## 관련 링크

[Get-TraceSource](Get-TraceSource.md)

[Trace-Command](Trace-Command.md)


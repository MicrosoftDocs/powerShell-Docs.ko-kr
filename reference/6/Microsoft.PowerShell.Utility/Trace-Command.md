---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/trace-command?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Trace-Command
ms.openlocfilehash: 9147be62c881e81a4ff1352a1b9fe7a34d2610cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216209"
---
# Trace-Command

## 개요
지정된 식 또는 명령의 추적을 구성하고 시작합니다.

## SYNTAX

### expressionSet (기본값)

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Expression] <ScriptBlock> [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force] [-Debugger]
 [-PSHost] [<CommonParameters>]
```

### commandSet

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Command] <String> [-ArgumentList <Object[]>] [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force]
 [-Debugger] [-PSHost] [<CommonParameters>]
```

## 설명
`Trace-Command`Cmdlet은 지정 된 식 또는 명령의 추적을 구성 하 고 시작 합니다.
지정한 명령에만 적용된다는 점을 제외하고 Set-TraceSource와 동일하게 작동합니다.

## 예제

### 예제 1: 추적 메타 데이터 처리, 매개 변수 바인딩 및 식

이 예에서는 메타 데이터 처리, 매개 변수 바인딩 및 식의 생성 및 소멸에 대 한 추적을 시작 `Get-Process Notepad` 합니다.

```powershell
Trace-Command -Name metadata,parameterbinding,cmdlet -Expression {Get-Process Notepad} -PSHost
```

**Name** 매개 변수를 사용 하 여 추적 원본을 지정 하 고, **Expression** 매개 변수를 사용 하 여 명령을 지정 하 고, **PSHost** 매개 변수를 사용 하 여 출력을 콘솔로 보냅니다. 이 명령은 추적 옵션이 나 수신기 옵션을 지정 하지 않으므로 기본값을 사용 합니다.

- 모든 추적 옵션
- 수신기 옵션의 경우 없음

### 예제 2: ParameterBinding 작업의 동작 추적

이 예제에서는 파이프라인의 입력을 사용 하는 식을 처리 하는 동안 PowerShell의 **Parameterbinding** 작업 동작을 추적 합니다 `Get-Alias` .

```powershell
$A = "i*"
Trace-Command ParameterBinding {Get-Alias $Input} -PSHost -InputObject $A
```

에서 `Trace-Command` **InputObject** 매개 변수는 추적 하는 동안 처리 되는 식에 개체를 전달 합니다.

첫 번째 명령은 문자열을 `i*` 변수에 저장 합니다 `$A` . 두 번째 명령은 `Trace-Command` ParameterBinding 추적 원본과 함께 cmdlet을 사용 합니다. **PSHost** 매개 변수는 출력을 콘솔로 보냅니다.

처리 되는 식은 이며 `Get-Alias $Input` , 여기서 `$Input` 변수는 **InputObject** 매개 변수와 연결 됩니다. **InputObject** 매개 변수는 변수를 `$A` 식으로 전달 합니다. 실제로 추적 하는 동안 처리 되는 명령은 `Get-Alias -InputObject $A" or "$A | Get-Alias` 입니다.

## PARAMETERS

### -ArgumentList

추적되는 명령의 매개 변수 및 매개 변수 값을 지정합니다. **ArgumentList** 의 별칭은 **Args** 입니다. 이 기능은 동적 매개 변수를 디버그하는 데 특히 유용합니다.

**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: commandSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command

추적하는 동안 처리되는 명령을 지정합니다.

```yaml
Type: System.String
Parameter Sets: commandSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -디버거

Cmdlet이 추적 출력을 디버거로 보낼지 여부를 나타냅니다. 사용자 모드 또는 커널 모드 디버거나 Visual Studio에서 출력을 볼 수 있습니다. 이 매개 변수는 기본 추적 수신기도 선택합니다.

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

### -식

추적하는 동안 처리되는 식을 지정합니다. 식을 중괄호 ()로 묶습니다 `{}` .

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: expressionSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Cmdlet이 추적 출력을 전송 하는 파일을 지정 합니다. 이 매개 변수는 파일 추적 수신기도 선택합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다. **FilePath** 매개 변수와 함께 사용 됩니다. **Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.

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

### -InputObject

추적 하는 동안 처리 되는 식에 대 한 입력을 지정 합니다. 식에서 허용하는 입력을 나타내는 변수를 입력하거나 파이프라인을 통해 개체를 전달할 수 있습니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ListenerOption

출력에서 각 추적 메시지의 접두사에 대 한 선택적 데이터를 지정 합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 없음
- LogicalOperationStack
- DateTime
- 타임스탬프
- ProcessId
- 스레드 Id
- 호출 스택

기본값은 **없음** 입니다.

여러 옵션을 지정하려면 "ProcessID,ThreadID"와 같이 공백 없이 쉼표로 구분하고 따옴표로 묶습니다.

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

추적할 PowerShell 구성 요소의 배열을 지정 합니다. 각 구성 요소의 추적 원본 이름을 입력합니다. 와일드카드가 지원됩니다. 컴퓨터에서 추적 소스를 찾으려면를 입력 `Get-TraceSource` 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -옵션

추적할 이벤트 유형을 결정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

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
- 오류
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
Parameter Sets: (All)
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSHost

Cmdlet이 추적 출력을 PowerShell 호스트로 보내도록 지정 합니다. 이 매개 변수는 PSHost 추적 수신기도 선택합니다.

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

### System.web. PSObject

식에 대 한 입력을 나타내는 개체를로 파이프 할 수 있습니다 `Trace-Command` .

## 출력

### System.web. PSObject

명령 추적을 디버그 스트림으로 반환합니다.

## 참고

- 추적은 개발자가 디버깅하고 프로그램을 다듬는 데 사용하는 방법입니다. 추적하면 프로그램에서 내부 프로세스의 각 단계에 대한 세부 메시지를 생성합니다.

- Powershell 추적 cmdlet은 PowerShell 개발자를 돕기 위해 설계 되었지만 모든 사용자가 사용할 수 있습니다. 이 cmdlet을 사용하면 셸 기능의 거의 모든 측면을 모니터링할 수 있습니다.

- 추적할 수 있는 PowerShell 구성 요소를 찾으려면를 입력 `Get-Help Get-TraceSource` 합니다.

  추적 소스는 추적을 관리 하 고 구성 요소에 대 한 추적 메시지를 생성 하는 각 PowerShell 구성 요소의 일부입니다. 구성 요소를 추적하려면 추적 원본을 확인하세요.

  추적 수신기는 추적의 출력을 받아 사용자에 게 표시 합니다. 사용자 모드 또는 커널 모드 디버거, 호스트 또는 콘솔, 파일 또는 **TraceListener** 클래스에서 파생 된 사용자 지정 수신기로 추적 데이터를 보내도록 선택할 수 있습니다.

- CommandSet 매개 변수 집합을 사용 하는 경우 PowerShell은 파이프라인에서 처리 되는 것과 동일한 방식으로 명령을 처리 합니다. 예를 들어 들어오는 개체마다 명령 검색을 반복하지 않습니다.

- **Name** , **Expression** , **Option** 및 **Command** 매개 변수의 이름은 선택 사항입니다. 매개 변수 이름을 생략 하는 경우 명명 되지 않은 매개 변수 값은 **Name** , **Expression** , **option** 또는 **name** , **Command** , **option** 순서로 표시 되어야 합니다. 매개 변수 이름을 포함할 경우 원하는 순서대로 매개 변수를 표시할 수 있습니다.

## 관련 링크

[Get-TraceSource](Get-TraceSource.md)

[Measure-Command](Measure-Command.md)

[Set-TraceSource](Set-TraceSource.md)

---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: d5f7002eea35924117753d0f73b40e9d9243c64e
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224233"
---
# Write-Error

## 개요
오류 스트림에 개체를 기록합니다.

## SYNTAX

### NoException (기본값)

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### WithException

```
Write-Error -Exception <Exception> [-Message <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### ErrorRecord

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## 설명

`Write-Error`Cmdlet는 종료 되지 않는 오류를 선언 합니다. 기본적으로 오류는 출력과 함께 표시되도록 오류 스트림을 통해 호스트 프로그램에 전송됩니다.

종료되지 않는 오류를 쓰려면 오류 메시지 문자열, **ErrorRecord** 개체 또는 **Exception** 개체를 입력합니다. 의 다른 매개 변수 `Write-Error` 를 사용 하 여 오류 레코드를 채웁니다.

종료되지 않는 오류는 오류 스트림에 오류를 쓰지만 명령 처리를 중지하지는 않습니다.
입력 항목 컬렉션에 있는 하나의 항목에서 종료되지 않는 오류가 선언될 경우 명령이 컬렉션의 다른 항목을 계속 처리합니다.

종료 오류를 선언 하려면 키워드를 사용 `Throw` 합니다.
자세한 내용은 [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md)를 참조 하세요.

## 예제

### 예 1: RegistryKey 개체에 대 한 오류 쓰기

```powershell
Get-ChildItem | ForEach-Object {
    if ($_.GetType().ToString() -eq "Microsoft.Win32.RegistryKey")
    {
        Write-Error "Invalid object" -ErrorId B1 -TargetObject $_
    }
    else
    {
        $_
    }
}
```

이 명령은 `Get-ChildItem` cmdlet이 `Microsoft.Win32.RegistryKey` `HKLM:` PowerShell 레지스트리 공급자의 또는 드라이브에 있는 개체와 같은 개체를 반환할 때 종료 되지 않는 오류를 선언 `HKCU:` 합니다.

### 예제 2: 콘솔에 오류 메시지 쓰기

```powershell
Write-Error "Access denied."
```

이 명령은 종료되지 않는 오류를 선언하고 "액세스 거부됨" 오류를 씁니다. **Message** 매개 변수를 사용하여 메시지를 지정하지만 선택적 매개 변수 이름 **Message** 는 생략합니다.

### 예 3: 콘솔에 오류를 기록 하 고 범주 지정

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

이 명령은 종료되지 않는 오류를 선언하고 오류 범주를 지정합니다.

### 예제 4: 예외 개체를 사용 하 여 오류 쓰기

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

이 명령은 **Exception** 개체를 사용하여 종료되지 않는 오류를 선언합니다.

첫 번째 명령은 해시 테이블을 사용하여 **System.Exception** 개체를 만들고 이 메서드는 예외 개체를 `$E` 변수에 저장 합니다. 해시 테이블을 사용하여 null 생성자가 있는 유형의 개체를 만들 수 있습니다.

두 번째 명령은 cmdlet을 사용 하 여 `Write-Error` 종료 되지 않는 오류를 선언 합니다. **Exception** 매개 변수 값은 변수의 **예외** 개체입니다 `$E` .

## PARAMETERS

### -범주

오류의 범주를 지정합니다. 기본값은 **NotSpecified** 입니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- NotSpecified
- OpenError
- CloseError
- DeviceError
- DeadlockDetected
- InvalidArgument
- InvalidData
- InvalidOperation
- InvalidResult
- InvalidType
- MetadataError
- NotImplemented
- NotInstalled
- ObjectNotFound
- OperationStopped 됨
- OperationTimeout
- SyntaxError
- ParserError
- 이상 거부 됨
- ResourceBusy
- ResourceExists
- ResourceUnavailable 수 없음
- ReadError
- WriteError
- FromStdErr
- SecurityError
- ProtocolError
- ConnectionError
- AuthenticationError
- LimitsExceeded
- QuotaExceeded
- NotEnabled

오류 범주에 대 한 자세한 내용은 [ErrorCategory 열거형](https://go.microsoft.com/fwlink/?LinkId=143600)을 참조 하세요.

```yaml
Type: System.Management.Automation.ErrorCategory
Parameter Sets: NoException, WithException
Aliases:
Accepted values: NotSpecified, OpenError, CloseError, DeviceError, DeadlockDetected, InvalidArgument, InvalidData, InvalidOperation, InvalidResult, InvalidType, MetadataError, NotImplemented, NotInstalled, ObjectNotFound, OperationStopped, OperationTimeout, SyntaxError, ParserError, PermissionDenied, ResourceBusy, ResourceExists, ResourceUnavailable, ReadError, WriteError, FromStdErr, SecurityError, ProtocolError, ConnectionError, AuthenticationError, LimitsExceeded, QuotaExceeded, NotEnabled

Required: False
Position: Named
Default value: NotSpecified
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryActivity

오류를 발생 시킨 동작을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Activity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryReason

활동에서 오류의 원인이 되는 방법 또는 이유를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Reason

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryTargetName

오류가 발생했을 때 처리 중이던 개체의 이름을 지정합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryTargetType

오류가 발생했을 때 처리 중이던 개체의 유형을 지정합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetType

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ErrorId

오류를 식별하는 ID 문자열을 지정합니다. 오류에 대해 고유한 문자열이어야 합니다.

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ErrorRecord

오류를 나타내는 오류 레코드 개체를 지정합니다. 개체의 속성을 사용하여 오류를 설명할 수 있습니다.

오류 레코드 개체를 만들려면 cmdlet을 사용 `New-Object` 하거나 자동 변수의 배열에서 오류 레코드 개체를 가져옵니다 `$Error` .

```yaml
Type: System.Management.Automation.ErrorRecord
Parameter Sets: ErrorRecord
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -예외

오류를 나타내는 예외 개체를 지정합니다. 개체의 속성을 사용하여 오류를 설명할 수 있습니다.

예외 개체를 만들려면 해시 테이블을 사용 하거나 cmdlet을 사용 `New-Object` 합니다.

```yaml
Type: System.Exception
Parameter Sets: WithException
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -메시지

오류 메시지 텍스트를 지정합니다. 텍스트에 공백이나 특수 문자가 포함되어 있으면 따옴표로 묶습니다. 메시지 문자열을로 파이프 할 수도 있습니다 `Write-Error` .

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases: Msg

Required: True (NoException), False (WithException)
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -RecommendedAction

오류를 해결 하거나 방지 하기 위해 사용자가 수행 해야 하는 동작을 지정 합니다.

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

### -TargetObject

오류가 발생했을 때 처리 중이던 개체를 지정합니다. 개체, 개체가 포함 된 변수 또는 개체를 가져오는 명령을 입력 합니다.

```yaml
Type: System.Object
Parameter Sets: NoException, WithException
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

오류 메시지를 포함 하는 문자열을로 파이프 할 수 있습니다 `Write-Error` .

## 출력

### Error 개체

`Write-Error` 오류 스트림에만 씁니다. 개체를 반환하지 않습니다.

## 참고

`Write-Error` 는 자동 변수 값을 변경 하지 않으므로 `$?` 종료 오류 조건을 신호 하지 않습니다. 종료 오류를 알리려면 [$PSCmdlet WriteError ()](/dotnet/api/system.management.automation.cmdlet.writeerror) 메서드를 사용 합니다.

## 관련 링크

[about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md)

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Write-Host](Write-Host.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)

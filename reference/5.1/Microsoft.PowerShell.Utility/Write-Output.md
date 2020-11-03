---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: ccc72ac961adbcba542a7b8be55ad49df68a5ef6
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224297"
---
# Write-Output

## 개요
지정된 개체를 파이프라인의 다음 명령으로 보냅니다. 명령이 파이프라인에서 마지막 명령인 경우 개체가 콘솔에 표시됩니다.

## SYNTAX

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## 설명

`Write-Output`Cmdlet은 지정 된 개체를 파이프라인의 다음 명령으로 보냅니다.
명령이 파이프라인에서 마지막 명령인 경우 개체가 콘솔에 표시됩니다.

`Write-Output` "출력 스트림" 또는 "성공 파이프라인"이 라고도 하는 개체를 기본 파이프라인으로 보냅니다. 오류 개체를 오류 파이프라인으로 보내려면 Write-Error를 사용하세요.

이 cmdlet은 대개 콘솔에 문자열 및 다른 개체를 표시하기 위해 스크립트에 사용됩니다. 에 대 한 기본 제공 별칭 중 하나 `Write-Output` 는를 `echo` 사용 하는 다른 셸과 유사 하며 `echo` , 기본 동작은 파이프라인 끝에 출력을 표시 하는 것입니다. PowerShell에서는 일반적으로 출력이 기본적으로 표시 되는 인스턴스에서 cmdlet을 사용할 필요가 없습니다. 예를 들어 `Get-Process | Write-Output`는 `Get-Process`와 같습니다. 또는를 `echo "Home directory: $HOME"` 작성할 수 있습니다 `"Home directory: $HOME"` .

기본적으로는 `Write-Output` cmdlet에 제공 된 컬렉션을 통해 열거 합니다. 그러나 `Write-Output` 는 **noenumerate** 매개 변수를 사용 하 여 파이프라인에서 단일 개체로 컬렉션을 전달 하는 데 사용할 수도 있습니다.

## 예제

### 예 1: 개체를 가져와 콘솔에 기록

```powershell
$P = Get-Process
Write-Output $P
```

첫 번째 명령은 컴퓨터에서 실행 중인 프로세스를 가져와서 변수에 저장 합니다 `$P` .

두 번째 및 세 번째 명령은 콘솔에의 프로세스 개체를 표시 합니다 `$P` .

### 예 2: 다른 cmdlet에 출력 전달

```powershell
Write-Output "test output" | Get-Member
```

이 명령은 "테스트 출력" 문자열을 cmdlet에 파이프 합니다 .이 cmdlet은 system.string `Get-Member` 클래스의 **System.String** 멤버를 표시 하 여 해당 문자열이 파이프라인을 따라 전달 되었음을 보여 줍니다.

### 예제 3: 출력에 열거 표시 안 함

```powershell
Write-Output 1,2,3 | Measure-Object
```

```Output
Count    : 3
...
```

```powershell
Write-Output 1,2,3 -NoEnumerate | Measure-Object
```

```Output
Count    : 1
...
```

이 명령은 **Noenumerate** 매개 변수를 추가 하 여 파이프라인을 통해 컬렉션이 나 배열을 단일 개체로 처리 합니다.

## PARAMETERS

### -InputObject

파이프라인으로 보낼 개체를 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoEnumerate

기본적으로 cmdlet은 `Write-Output` 항상 해당 출력을 열거 합니다. **Noenumerate** 매개 변수는 기본 동작을 억제 하 고 출력을 열거 하지 못하도록 합니다 `Write-Output` . 괄호를 강제로 열거 하므로 명령이 괄호 안에 래핑된 경우 **Noenumerate** 매개 변수는 영향을 주지 않습니다. 예를 들어 `(Write-Output 1,2,3)` 는 배열을 여전히 열거 합니다.

> [!IMPORTANT]
> Windows PowerShell에서 PowerShell 6.2 이상에서 수정 된이 스위치에 문제가 있습니다. **Noenumerate** 를 사용 하 고 **InputObject** 매개 변수를 명시적으로 사용 하는 경우 명령은 여전히를 열거 합니다. 이 문제를 해결 하려면 **InputObject** 인수 메서드에 액세스할를 전달 합니다.

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

개체를로 파이프 할 수 있습니다 `Write-Output` .

## 출력

### System.web. PSObject

`Write-Output` 입력으로 전송 되는 개체를 반환 합니다.

## 참고

## 관련 링크

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Tee-Object](Tee-Object.md)

[Write-Debug](Write-Debug.md)

[쓰기 오류](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)

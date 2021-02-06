---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Host
ms.openlocfilehash: 4fefb133416b3db6c19c71a916d73fe00f86f3a4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600141"
---
# Out-Host

## 개요
출력을 명령줄로 보냅니다.

## SYNTAX

### 모두

```
Out-Host [-Paging] [-InputObject <PSObject>] [<CommonParameters>]
```

## 설명

`Out-Host`Cmdlet은 표시를 위해 출력을 PowerShell 호스트로 보냅니다. 이 호스트는 명령줄에 출력을 표시합니다. 는 기본값 이기 때문에 `Out-Host` 매개 변수를 사용 하지 않을 경우에는 지정 하지 않아도 됩니다.

`Out-Host` 는 실행 되는 모든 명령에 자동으로 추가 됩니다. 명령을 실행 하는 호스트에 파이프라인 출력을 전달 합니다. `Out-Host` ANSI 이스케이프 시퀀스를 무시 합니다. 이스케이프 시퀀스는 호스트에 의해 처리 됩니다. `Out-Host` 해석 하거나 변경 하지 않고 ANSI 이스케이프 시퀀스를 호스트에 전달 합니다.

## 예제

### 예제 1: 한 번에 한 페이지씩 출력 표시

이 예에서는 시스템 프로세스를 한 번에 한 페이지씩 표시 합니다.

```powershell
Get-Process | Out-Host -Paging
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     30    24.12      36.95      15.86   21004  14 ApplicationFrameHost
     55    24.33      60.48      10.80   12904  14 BCompare
<SPACE> next page; <CR> next line; Q quit
      9     4.71       8.94       0.00   16864  14 explorer
<SPACE> next page; <CR> next line; Q quit
```

`Get-Process` 시스템 프로세스를 가져오고 개체를 파이프라인으로 보냅니다. `Out-Host`**페이징** 매개 변수를 사용 하 여 한 번에 하나의 데이터 페이지를 표시 합니다.

### 예제 2: 변수를 입력으로 사용

이 예에서는 변수에 저장 된 개체를에 대 한 입력으로 사용 `Out-Host` 합니다.

```powershell
$io = Get-History
Out-Host -InputObject $io
```

`Get-History` PowerShell 세션의 기록을 가져오고 개체를 `$io` 변수에 저장 합니다.
`Out-Host`**InputObject** 매개 변수를 사용 하 여 변수를 지정 하 `$io` 고 기록을 표시 합니다.

## PARAMETERS

### -InputObject

콘솔에 기록할 개체를 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

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

### -페이징

에서 한 번 `Out-Host` 에 한 페이지씩 출력을 표시 하 고 나머지 페이지를 표시 하기 전에 사용자 입력을 대기 함을 나타냅니다. 기본적으로 모든 출력은 단일 페이지에 표시 됩니다. 호스트의 특성에 따라 페이지 크기가 결정됩니다.

다음 출력 페이지를 표시 하려면 <kbd>스페이스바</kbd> 를 누르고 출력의 다음 줄을 보려면 <kbd>enter</kbd> 키를 누릅니다. <kbd>Q</kbd> 키를 눌러 종료 합니다.

**페이징은** **추가** 명령과 유사 합니다.

> [!NOTE]
> **페이징** 매개 변수는 PowerShell ISE 호스트에서 지원 되지 않습니다.

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

파이프라인에서로 개체를 보낼 수 있습니다 `Out-Host` .

## 출력

### 없음

`Out-Host` 는 출력을 생성 하지 않습니다. 표시 하기 위해 호스트에 개체를 보냅니다.

## 참고

모든 PowerShell 호스트에서 **페이징** 매개 변수를 지원 하지 않습니다. 예를 들어 PowerShell ISE에서 **Paging** 매개 변수를 사용 하는 경우 다음과 같은 오류가 표시 됩니다. `out-lineoutput : The method or operation is not implemented.`

**Out** 동사를 포함 하는 cmdlet은 `Out-` 개체의 형식을 지정 하지 않습니다. 개체를 렌더링 하 고 지정 된 표시 대상으로 보냅니다. 포맷 되지 않은 개체를 cmdlet에 보내면 `Out-` cmdlet이 해당 개체를 렌더링 하기 전에 형식 지정 cmdlet으로 보냅니다.

Cmdlet에는 `Out-` 이름 또는 파일 경로에 대 한 매개 변수가 없습니다. Cmdlet을 사용 하 여 cmdlet에 데이터를 보내려면 파이프라인을 사용 하 여 `Out-` PowerShell 명령의 출력을 cmdlet으로 보냅니다. 또는 변수에 데이터를 저장 하 고 **InputObject** 매개 변수를 사용 하 여 cmdlet에 데이터를 전달할 수 있습니다.

`Out-Host` 는 데이터를 보내지만 출력 개체를 생성 하지 않습니다. 의 출력을 cmdlet으로 파이프라인 하는 경우는 `Out-Host` `Get-Member` 지정 된 `Get-Member` 개체가 없음을 보고 합니다.

## 관련 링크

[Clear-Host](Clear-Host.md)

[Out-Default](Out-Default.md)

[Out-File](../Microsoft.PowerShell.Utility/Out-File.md)

[Out-Null](Out-Null.md)

[Out-Printer](../Microsoft.PowerShell.Utility/Out-Printer.md)

[Out-String](../Microsoft.PowerShell.Utility/Out-String.md)

[Write-Host](../Microsoft.PowerShell.Utility/Write-Host.md)


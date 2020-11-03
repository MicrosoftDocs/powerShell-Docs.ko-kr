---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-printer?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Printer
ms.openlocfilehash: 69d78550d68457c92deb3e4d690483bf742544b0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217369"
---
# Out-Printer

## 개요
출력을 프린터로 보냅니다.

## SYNTAX

```
Out-Printer [[-Name] <String>] [-InputObject <PSObject>] [<CommonParameters>]
```

## 설명

`Out-Printer`이 cmdlet은 출력을 기본 프린터로 보내거나 다른 프린터 (지정 된 경우)로 보냅니다.

> [!NOTE]
> 이 cmdlet은 PowerShell 7에서 다시 도입 되었습니다. 이 cmdlet은 Windows 데스크톱을 지 원하는 Windows 시스템 에서만 사용할 수 있습니다.

## 예제

### 예 1-기본 프린터에 인쇄할 파일 보내기

이 예제에서는 `Out-Printer` 에 **경로** 매개 변수가 없는 경우에도 파일을 인쇄 하는 방법을 보여 줍니다.

```powershell
Get-Content -Path ./readme.txt | Out-Printer
```

`Get-Content``readme.txt`현재 디렉터리에 있는 파일의 내용을 가져오고로 파이프 하 여 `Out-Printer` 기본 프린터로 보냅니다.

### 예제 2: 원격 프린터에 문자열 인쇄

이 예제에서는 `Hello, World` Server01의 **Prt 6B 컬러** 프린터에 인쇄 합니다.

```powershell
"Hello, World" | Out-Printer -Name "\\Server01\Prt-6B Color"
```

**Name** 매개 변수는 기본값이 아닌 특정 프린터를 선택 합니다.

### 예제 3-기본 프린터에 도움말 항목 인쇄

이 예에서는에 대 한 도움말 항목의 전체 버전을 인쇄 합니다 `Get-CimInstance` .

```powershell
$H = Get-Help -Full Get-CimInstance
Out-Printer -InputObject $H
```

`Get-Help` 에 대 한 도움말 항목의 전체 버전을 가져와서 `Get-CimInstance` 변수에 저장 합니다 `$H` . **InputObject** 매개 변수는의 값을 `$H` 에 전달 `Out-Printer` 합니다.

## PARAMETERS

### -InputObject

프린터로 보낼 개체를 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

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

### -Name

지정 된 프린터로 출력을 보냅니다. 매개 변수 이름 **이름은** 선택 사항입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PrinterName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

모든 개체를로 파이프 할 수 있습니다 `Out-Printer` .

## 출력

### 없음

`Out-Printer` 는 개체를 반환 하지 않습니다.

## 참고

동사를 포함 하는 cmdlet은 `Out` 개체의 형식을 지정 하지 않습니다. 단지 렌더링 하 여 지정 된 표시 대상으로 보냅니다. 포맷 되지 않은 개체를 cmdlet에 보내면 `Out` cmdlet이 해당 개체를 렌더링 하기 전에 형식 지정 cmdlet으로 보냅니다.

`Out-Printer` 데이터를 프린터로 보내지만 출력 개체를 파이프라인으로 내보내지 않습니다. 의 출력을로 파이프 하는 경우는 `Out-Printer` `Get-Member` 지정 된 개체가 없다는 `Get-Member` 것을 보고 합니다.

## 관련 링크

[Out-File](Out-File.md)

[Out-String](Out-String.md)


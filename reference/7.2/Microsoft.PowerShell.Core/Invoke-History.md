---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: 7fb4341a84706f7d31d463bb527a1a31f387c2ae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605006"
---
# Invoke-History

## 개요
세션 기록에서 명령을 실행합니다.

## SYNTAX

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Invoke-History`Cmdlet은 세션 기록에서 명령을 실행 합니다. Get-History에서 명령을 나타내는 개체를 전달 `Invoke-History` 하거나 해당 **Id** 번호를 사용 하 여 현재 기록의 명령을 식별할 수 있습니다. 명령의 id 번호를 확인 하려면 cmdlet을 사용 합니다 `Get-History` .

세션 기록은 **Psreadline** 모듈에 의해 유지 관리 되는 기록과 별도로 관리 됩니다.
**Psreadline** 이 로드 된 세션에서 두 기록을 모두 사용할 수 있습니다. 이 cmdlet은 세션 기록 에서만 작동 합니다. 자세한 내용은 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.

## 예제

### 예제 1: 기록에서 최신 명령 실행

이 예에서는 세션 기록에서 마지막 또는 가장 최근 명령을 실행 합니다. 이 명령을 `r` 에 대 한 별칭으로 약어로 사용할 수 있습니다 `Invoke-History` .

```powershell
Invoke-History
```

### 예 2: 지정 된 ID를 가진 명령 실행

이 예제에서는 **Id가** 132 인 세션 기록에서 명령을 실행 합니다. **Id** 매개 변수의 이름은 선택 사항 이므로이 명령의 약어는, 또는로 지정할 수 있습니다 `Invoke-History 132` `ihy 132` `r 132` .

```powershell
Invoke-History -Id 132
```

### 예제 3: 명령 텍스트를 사용 하 여 가장 최근 명령 실행

이 예에서는 `Get-Process` 세션 기록에서 가장 최근의 명령을 실행 합니다. **Id** 매개 변수에 대 한 문자를 입력 하는 경우 `Invoke-History` 가장 최근 명령부터 시작 하 여 패턴에 일치 하는 첫 번째 명령을 실행 합니다.

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> 패턴 일치는 대/소문자를 구분 하지 않지만 패턴은 줄의 시작 부분을 찾습니다.

### 예제 4: 기록에서 일련의 명령 실행

이 예제에서는 16-24 명령을 실행 합니다. 하나의 **id** 값만 나열할 수 있으므로 명령은 cmdlet을 사용 하 여 `ForEach-Object` `Invoke-History` 각 **id** 값에 대해 명령을 한 번 실행 합니다.

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### 예제 5

이 예제에서는 기록에서 명령 255 (249 ~ 255)로 끝나는 명령 7 개를 실행 합니다. Cmdlet을 사용 하 여 `Get-History` 명령을 검색 합니다. 하나의 **id** 값만 나열할 수 있으므로 명령은 cmdlet을 사용 하 여 `ForEach-Object` `Invoke-History` 각 **id** 값에 대해 명령을 한 번 실행 합니다.

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## PARAMETERS

### -Id

기록의 명령 **Id** 를 지정 합니다. 명령의 **Id** 번호 또는 명령의 처음 몇 문자를 입력할 수 있습니다.

문자를 입력 하 `Invoke-History` 는 경우 가장 최근 명령과 가장 먼저 일치 합니다. 이 매개 변수를 생략 하면는 `Invoke-History` 마지막 또는 가장 최근 명령을 실행 합니다. 명령의 **Id** 번호를 찾으려면 cmdlet을 사용 합니다 `Get-History` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

기록 **Id** 를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음

이 cmdlet은 출력을 생성 하지 않지만를 실행 하는 명령에 의해 출력이 생성 될 수 있습니다 `Invoke-History` .

## 참고

세션 기록은 세션 중에 입력된 명령 목록입니다. 세션 기록은 명령의 실행 순서, 상태, 시작 시간 및 종료 시간을 나타냅니다. 각 명령을 입력 하면 PowerShell에서 해당 명령을 다시 사용할 수 있도록 기록에 추가 합니다. 세션 기록에 대 한 자세한 내용은 [about_History](About/about_History.md)를 참조 하세요.

`Invoke-History`기본 제공 별칭인 및를 참조할 수도 있습니다 `r` `ihy` . 자세한 내용은 [about_Aliases](About/about_Aliases.md)를 참조 하세요.

## 관련 링크

[Add-History](Add-History.md)

[Clear-History](Clear-History.md)

[Get-History](Get-History.md)


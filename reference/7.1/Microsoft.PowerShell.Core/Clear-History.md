---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: c159262b21e39965f32db4a0fa736aa70de8e916
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211657"
---
# Clear-History

## 개요
PowerShell 세션 명령 기록에서 항목을 삭제 합니다.

## SYNTAX

### IDParameter (기본값)

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CommandLineParameter

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## 설명

`Clear-History` PowerShell 세션에서 명령 기록을 삭제 합니다. 각 PowerShell 세션에는 자체 명령 기록이 있습니다. 명령 기록을 표시 하려면 cmdlet을 사용 `Get-History` 합니다.

기본적으로는 `Clear-History` PowerShell 세션에서 전체 명령 기록을 삭제 합니다. 매개 변수를 사용 `Clear-History` 하 여 선택한 명령을 삭제할 수 있습니다.

`Clear-History``PSReadLine`명령 기록 파일을 지우지 않습니다. `PSReadLine`모듈은 모든 powershell 세션의 모든 powershell 명령을 포함 하는 기록 파일을 저장 합니다. PowerShell 프롬프트에서 키보드의 위쪽 및 아래쪽 화살표를 사용 하 여 명령 기록을 스크롤합니다. `PSReadLine`명령 기록에 대 한 구성을 표시 하려면를 사용 `Get-PSReadLineOption` 합니다.
`PSReadLine` PowerShell 5.0 이상에서 제공 됩니다. 자세한 내용은 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.

## 예제

### 예제 1: PowerShell 세션에서 명령 기록 삭제

이 명령은 PowerShell 세션의 기록에서 모든 명령을 삭제 합니다.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location .\Test
   2 Update-Help
   3 Set-Location C:\Test\Logs
   4 Get-Location
```

```powershell
Clear-History
Get-History
```

```Output
  Id CommandLine
  -- -----------
   5 Clear-History
```

`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다. `Clear-History` 전체 명령 기록을 삭제 합니다. `Get-History` 업데이트 된 명령 기록을 표시 하 고 이전 기록을 삭제 했는지 확인 합니다.

### 예 2: 최신 명령 삭제

이 명령은 **Count** 및 **최신** 매개 변수를 사용 하 여 PowerShell 세션의 기록에서 최신 명령을 삭제 합니다.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Count 5 -Newest
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
  11 Clear-History -Count 5 -Newest
```

`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다. `Clear-History` 는 명령 기록을 삭제 하는 데 사용 됩니다. **Count** 매개 변수는 지정 된 **Id** 를 포함 하 여 삭제할 명령의 수를 지정 합니다. **최신** 매개 변수는 최근 명령이 기록에서 삭제 되도록 지정 합니다. `Get-History`업데이트 된 명령 기록을 표시 하 고 5 개의 최신 명령이 삭제 되었는지 확인 합니다 ( **id 6**  -  **id 10** ).

### 예 3: 특정 조건과 일치 하는 명령 삭제

이 명령은 **CommandLine** 매개 변수로 정의 된 특정 조건과 일치 하는 명령을 삭제 합니다.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
```

```powershell
Clear-History -CommandLine *Help*, *Syntax
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   4 Get-Command Clear-History -ShowCommandInfo
   8 Clear-History -CommandLine *Help*, *Syntax
```

`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다. `Clear-History` 명령 기록을 삭제 합니다. **CommandLine** 매개 변수는 **도움말과** end **구문을** 포함 하는 명령을 지정 합니다. `Get-History` 업데이트 된 명령 기록을 표시 하 고, id **3** , **id 5** , id **6** 및 **id 7** 명령이 삭제 되었는지 확인 합니다.

### 예 4: Id 번호로 명령 삭제

이 명령은 **Id** 를 사용 하 여 특정 기록 항목을 삭제 합니다. 여러 명령을 삭제 하려면 쉼표로 구분 된 **Id** 번호 목록을 제출 합니다.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   3 Get-Help Get-Alias
   4 Get-Command Clear-History
   5 Get-Command Clear-History -Syntax
   6 Get-Command Clear-History -ShowCommandInfo
```

```powershell
Clear-History -Id 3, 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   4 Get-Command Clear-History
   6 Get-Command Clear-History -ShowCommandInfo
   7 Get-History
   8 Clear-History -Id 3, 5
```

`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다. `Clear-History` 명령 기록을 삭제 합니다. **Id** 매개 변수는 삭제할 명령을 지정 합니다. `Get-History` 업데이트 된 명령 기록을 표시 하 고 **id 3** 및 **id 5** 가 삭제 되었는지 확인 합니다.

### 예 5: Id 번호 및 개수로 명령 삭제

이 명령은 **Id** 및 **Count** 매개 변수를 사용 하 여 명령 기록을 삭제 합니다. 명령이 지정 된 **Id** 에서 역순으로 (최신에서 가장 오래 된 순서로) 삭제 됩니다.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Id 7 -Count 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
  11 Clear-History -Id 7 -Count 5
```

`Get-History`Cmdlet은 PowerShell 세션의 기록을 표시 합니다. `Clear-History` 명령 기록을 삭제 합니다. **Id** 매개 변수는 **id 7** 로 시작 하도록 지정 합니다. **Count** 매개 변수는 지정 된 **Id** 를 포함 하 여 다섯 개의 명령을 삭제 하도록 지정 합니다. `Get-History`업데이트 된 명령 기록을 표시 하 고 5 개의 명령이 삭제 되었는지 확인 합니다 ( **id 3**  -  **id 7** ).

## PARAMETERS

### -CommandLine

PowerShell 세션에서 명령 기록을 삭제 합니다. 문자열은 정확히 일치 해야 합니다. 또는 와일드 카드를 사용 하 여에 표시 된 PowerShell 세션 기록의 명령과 일치 해야 합니다 `Get-History` . 둘 이상의 문자열을 입력 하는 경우는 `Clear-History` 문자열과 일치 하는 명령을 삭제 합니다. **CommandLine** 매개 변수는 **Count** 와 함께 사용할 수 있습니다.

공백이 있는 문자열의 경우 단일 따옴표를 사용 합니다. 자세한 내용은 [about_Quoting_Rules](About/about_Quoting_Rules.md)를 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: CommandLineParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -개수

삭제할 기록 항목의 수를 지정 합니다 `Clear-History` . 명령은 기록에서 가장 오래 된 항목부터 시작 하 여 순서 대로 삭제 됩니다.

**Count** 및 **Id** 매개 변수를 함께 사용할 수 있습니다. **Count** 매개 변수는 지정 된 **Id** 를 포함 하 여 삭제할 명령의 수를 지정 합니다. 지정 된 **Id** 부터 명령이 순차적으로 역순으로 삭제 됩니다. 예를 들어 **Id** 가 30이 고 **개수가** 10 이면에서 `Clear-History` 21 ~ 30 개 항목을 삭제 합니다.

**Count** 및 **CommandLine** 매개 변수를 함께 사용할 수 있습니다. **Count** 는 해당 일치 하는 **명령줄** 매개 변수 값을 삭제 하는 명령 수를 지정 합니다. 명령이 순서 대로 삭제 됩니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

에서 삭제 하는 명령 기록 **Id** 를 지정 합니다 `Clear-History` . **Id** 번호를 표시 하려면 cmdlet을 사용 `Get-History` 합니다. **Id** 번호는 순차적 이며 명령은 PowerShell 세션 전체에서 **id** 번호를 유지 합니다. **Id** 매개 변수는 **Count** 와 **최신** 에서 사용할 수 있습니다.

```yaml
Type: System.Int32[]
Parameter Sets: IDParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -최신

**최신** 매개 변수가 사용 되 면는 `Clear-History` 기록에서 최신 항목을 삭제 합니다. 기본적으로는 `Clear-History` 기록에서 가장 오래 된 항목을 삭제 합니다.

**최신** 매개 변수는 **Id** 및 **개수** 와 함께 사용할 수 있습니다. **Count** 매개 변수는 지정 된 **Id** 를 포함 하 여 삭제할 명령의 수를 지정 합니다. 지정 된 **Id** 부터 명령이 순서 대로 삭제 됩니다. 예를 들어 **Id** 가 30이 고 **개수가** 10 인 경우는 `Clear-History` 30 ~ 39 항목을 삭제 합니다.

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

### -Confirm

Cmdlet을 실행 하기 전에 확인 메시지를 표시 `Clear-History` 합니다.

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

Cmdlet이 실행 될 경우 발생 하는 상황을 보여 줍니다 `Clear-History` . cmdlet은 실행되지 않습니다.

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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### 없음

개체를에 연결할 수 없습니다 `Clear-History` .

## 출력

### 없음

`Clear-History` 는 출력을 생성 하지 않습니다.

## 참고

Powershell 세션 기록은 PowerShell 세션 중에 입력 된 명령 목록입니다. 기록을 보고, 명령을 추가 및 삭제하고, 기록에서 명령을 실행할 수 있습니다. 자세한 내용은 [about_History](About/about_History.md)를 참조 하세요.

세션 기록은 **Psreadline** 모듈에 의해 유지 관리 되는 기록과 별도로 관리 됩니다.
**Psreadline** 이 로드 된 세션에서 두 기록을 모두 사용할 수 있습니다. 이 cmdlet은 세션 기록 에서만 작동 합니다. 자세한 내용은 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)를 참조 하세요.

## 관련 링크

[about_History](About/about_History.md)

[about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)

[about_Quoting_Rules](About/about_Quoting_Rules.md)

[Add-History](Add-History.md)

[Get-History](Get-History.md)

[Invoke-History](Invoke-History.md)

[Get-PSReadLineOption](/powershell/module/psreadline/get-psreadlineoption)

[Set-PSReadLineOption](/powershell/module/psreadline/set-psreadlineoption)


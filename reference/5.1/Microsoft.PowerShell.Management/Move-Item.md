---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: d3637825e7570e5fb0f3ff77efbc89e9d93974a3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214626"
---
# Move-Item

## 개요
항목의 위치를 이동합니다.

## SYNTAX

### Path (기본값)

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction]
 [<CommonParameters>]
```

### LiteralPath

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction]
 [<CommonParameters>]
```

## 설명

`Move-Item`Cmdlet은 속성, 내용 및 자식 항목을 포함 하 여 항목을 한 위치에서 다른 위치로 이동 합니다.
이동하기 전과 후의 위치가 동일한 공급자에서 지원되어야 합니다.
예를 들어 디렉터리 간에 파일 또는 하위 디렉터리를 이동하거나 레지스트리 키 간에 레지스트리 하위 키를 이동할 수 있습니다.
항목을 이동하면 원래 위치에서 해당 항목이 삭제되고 새 위치에 추가됩니다.

## 예제

### 예제 1: 파일을 다른 디렉터리로 이동 하 고 이름을 바꿉니다.

이 명령은 드라이브의 "Test.txt" 파일 `C:` 을 "e:\temp 디렉터리로" 디렉터리로 이동 하 고 "test.txt"에서 "tst.txt"로 이름을 바꿉니다.

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### 예제 2: 디렉터리 및 해당 콘텐츠를 다른 디렉터리로 이동

이 명령은 "C:\Temp" 디렉터리와 해당 내용을 "C:\Logs" 디렉터리로 이동 합니다.
"Temp" 디렉터리와 모든 하위 디렉터리 및 파일이 "Logs" 디렉터리에 표시 됩니다.

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### 예제 3: 지정 된 확장의 모든 파일을 현재 디렉터리에서 다른 디렉터리로 이동 합니다.

이 명령은 현재 디렉터리 (점 ('. ')로 표시)에 있는 모든 텍스트 파일 ("* .txt")을 "C:\Logs" 디렉터리로 이동 합니다.

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### 예제 4: 지정 된 확장의 모든 파일을 현재 디렉터리에서 다른 디렉터리로 재귀적으로 이동

이 명령은 현재 디렉터리와 모든 하위 디렉터리의 모든 텍스트 파일을 "C:\TextFiles" 디렉터리로 재귀적으로 이동 합니다.

이 명령은 cmdlet을 사용 하 여 `Get-ChildItem` 현재 디렉터리에 있는 모든 자식 항목 (점으로 표시 \[ \] )과 " *.txt" 파일 이름 확장명을 가진 하위 디렉터리를 가져옵니다. 재귀 매개 변수 **를** 사용 하 여 검색 재귀를 수행 하 고 Include 매개 변수를 사용* 하 여 ".txt" 파일로 검색을 제한 합니다.

파이프라인 연산자 ( `|` )는이 명령의 결과를에 전송 하 여 `Move-Item` 텍스트 파일을 "textfiles" 디렉터리로 이동 합니다.

"C:\Textfiles"로 이동 하는 파일의 이름이 같은 경우에는에서 `Move-Item` 오류를 표시 하 고 계속 되지만 각 이름을 가진 하나의 파일만 "C:\Textfiles"로 이동 합니다.
나머지 파일은 원래 디렉터리에 그대로 유지됩니다.

"Textfiles" 디렉터리 (또는 대상 경로의 다른 요소)가 없을 경우 명령이 실패 합니다.
**Force** 매개 변수를 사용 하더라도 누락 된 디렉터리는 생성 되지 않습니다.
`Move-Item` 첫 번째 항목을 "Textfiles" 라는 파일로 이동한 다음 파일이 이미 있음을 설명 하는 오류를 표시 합니다.

또한 기본적으로는 `Get-ChildItem` 숨겨진 파일을 이동 하지 않습니다.
숨겨진 파일을 이동 하려면에 **Force** 매개 변수를 사용 `Get-ChildItem` 합니다.

참고: Windows PowerShell 2.0에서 cmdlet의 **재귀** 매개 변수를 사용 하는 경우 `Get-ChildItem` **Path** 매개 변수 값은 컨테이너 여야 합니다.
**Include** 매개 변수를 사용 하 여 .txt 파일 이름 확장명 필터 ()를 지정 합니다 `Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles` .

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

### 예 5: 레지스트리 키 및 값을 다른 키로 이동

이 명령은 "HKLM\Software"의 "MyCompany" 레지스트리 키에 있는 레지스트리 키와 값을 "MyNewCompany" 키로 이동 합니다.
와일드 카드 문자 (' * ')는 키 자체가 아니라 "MyCompany" 키의 내용을 이동 해야 함을 나타냅니다.
이 명령에서 선택적 **경로** 및 **대상** 매개 변수 이름은 생략 됩니다.

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### 예제 6: 디렉터리 및 해당 콘텐츠를 지정 된 디렉터리의 하위 디렉터리로 이동 합니다.

이 명령은 "로그 \[ 9 월 \` 06 \] " 디렉터리와 해당 내용을 "logs \[ 2006 \] " 디렉터리로 이동 합니다.

원본 디렉터리 이름에 왼쪽 대괄호와 **Path** 오른쪽 대괄호 문자 (" **LiteralPath** \[ " 및 "")가 포함 되어 있기 때문에 LiteralPath 매개 변수가 경로 대신 사용 됩니다 \] .
또한 경로는 작은따옴표 (' ')로 묶여 있으므로 억음 기호 ( \` )는 잘못 해석 되지 않습니다.

대상 변수는 잘못 해석 될 수 있는 대괄호가 포함 되어 있으므로 작은따옴표 안에 포함 해야 하기 때문에 **destination** 매개 변수에는 리터럴 경로가 필요 하지 않습니다.

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

## PARAMETERS

### -Credential

> [!NOTE]
> 이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.
> 이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Destination

항목을 이동할 위치의 경로를 지정합니다.
기본값은 현재 디렉터리입니다.
와일드카드를 사용할 수 있지만 결과는 하나의 위치를 지정해야 합니다.

이동할 항목의 이름을 바꾸려면 **Destination** 매개 변수 값에 새 이름을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -제외

이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.
경로 요소 또는 패턴(예: "*.txt")을 입력합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

공급자의 형식 또는 언어로 필터를 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.

와일드 카드 문자를 포함 한 필터 구문은 공급자에 따라 달라 집니다.
필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.
구현은 공급자에 따라 다릅니다.
자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -포함

작업에서이 cmdlet이 이동 하는 항목을 문자열 배열로 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.
경로 요소 또는 패턴(예: "*.txt")을 입력합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LiteralPath

항목의 현재 위치 경로를 지정합니다.
**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.
어떠한 문자도 와일드카드로 해석되지 않습니다.
이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.
작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

작업 중인 항목을 나타내는 개체를 반환합니다.
기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

항목의 현재 위치 경로를 지정합니다.
기본값은 현재 디렉터리입니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -UseTransaction

활성 트랜잭션에 명령을 포함합니다.
이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.
자세한 내용은 about_Transactions를 참조하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
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

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

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

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.

## 출력

### 없음 또는 이동 된 항목을 나타내는 개체입니다.

*PassThru* 매개 변수를 사용 하는 경우이 cmdlet은 이동 된 항목을 나타내는 개체를 생성 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

이 cmdlet은 동일한 공급자가 지 원하는 드라이브 간에 파일을 이동 하지만 디렉터리는 동일한 드라이브 내 에서만 이동 합니다.

명령에서 `Move-Item` 항목의 속성, 내용 및 자식 항목을 이동 하기 때문에 기본적으로 모든 이동이 재귀적으로 진행 됩니다.

이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.
세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.
자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

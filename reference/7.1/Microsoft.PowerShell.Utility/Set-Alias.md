---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 2/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Alias
ms.openlocfilehash: 2a84c08022689d53c3273f1b6f802cfeae67953d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211825"
---
# Set-Alias

## 개요
현재 PowerShell 세션의 cmdlet 또는 다른 명령에 대 한 별칭을 만들거나 변경 합니다.

## SYNTAX

### Default (기본값)

```
Set-Alias [-Name] <string> [-Value] <string> [-Description <string>] [-Option <ScopedItemOptions>]
 [-PassThru] [-Scope <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Set-Alias`Cmdlet은 cmdlet 또는 명령 (예: 함수, 스크립트, 파일 또는 기타 실행 파일)에 대 한 별칭을 만들거나 변경 합니다. 별칭은 cmdlet 또는 명령을 참조 하는 대체 이름입니다.
예를 들어 `sal` 는 cmdlet에 대 한 별칭입니다 `Set-Alias` . 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.

Cmdlet은 여러 별칭을 포함할 수 있지만 별칭은 하나의 cmdlet에만 연결 될 수 있습니다. `Set-Alias`를 사용 하 여 기존 별칭을 다른 cmdlet에 재할당 하거나 설명 등의 별칭 속성을 변경할 수 있습니다.

에 의해 만들어지거나 변경 된 별칭 `Set-Alias` 은 영구적이 지 않으며 현재 PowerShell 세션 에서만 사용할 수 있습니다. PowerShell 세션이 닫히면 별칭이 제거 됩니다.

## 예제

### 예제 1: cmdlet에 대 한 별칭 만들기

이 명령은 현재 PowerShell 세션에서 cmdlet에 대 한 별칭을 만듭니다.

```
PS> Set-Alias -Name list -Value Get-ChildItem

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem
```

`Set-Alias`Cmdlet은 현재 PowerShell 세션에서 별칭을 만듭니다. **Name** 매개 변수는 별칭의 이름을 지정 합니다 `list` . **Value** 매개 변수는 별칭이 실행 되는 cmdlet을 지정 합니다.

별칭을 실행 하려면 `list` PowerShell 명령줄에를 입력 합니다.

### 예 2: 다른 cmdlet에 기존 별칭 재할당

이 명령은 기존 별칭을 다시 할당 하 여 다른 cmdlet을 실행 합니다.

```
PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem

PS> Set-Alias -Name list -Value Get-Location

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-Location
```

`Get-Alias`Cmdlet은 **Name** 매개 변수를 사용 하 여 별칭을 표시 합니다 `list` . `list`별칭은 cmdlet과 연결 됩니다 `Get-ChildItem` . `list`별칭을 실행 하면 현재 디렉터리의 항목이 표시 됩니다.

`Set-Alias`Cmdlet은 **Name** 매개 변수를 사용 하 여 별칭을 지정 합니다 `list` . **값** 매개 변수는 별칭을 cmdlet에 연결 합니다 `Get-Location` .

`Get-Alias`Cmdlet은 **Name** 매개 변수를 사용 하 여 별칭을 표시 합니다 `list` . `list`별칭은 cmdlet과 연결 됩니다 `Get-Location` . `list`별칭을 실행 하면 현재 디렉터리의 위치가 표시 됩니다.

### 예제 3: 읽기 전용 별칭 만들기 및 변경

이 명령은 읽기 전용 별칭을 만듭니다. 읽기 전용 옵션을 선택 하면 별칭에 대 한 의도 하지 않은 변경을 방지할 수 있습니다. 읽기 전용 별칭을 변경 하거나 삭제 하려면 **Force** 매개 변수를 사용 합니다.

```
PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         :
Name                : loc
CommandType         : Alias

PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -Description 'Displays the current directory' -Force -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         : Displays the current directory
Name                : loc
CommandType         : Alias
```

`Set-Alias`Cmdlet은 현재 PowerShell 세션에서 별칭을 만듭니다. **Name** 매개 변수는 별칭의 이름을 지정 합니다 `loc` . **Value** 매개 변수는 `Get-Location` 별칭이 실행 되는 cmdlet을 지정 합니다. **Option** 매개 변수는 **ReadOnly** 값을 지정 합니다. **PassThru** 매개 변수는 별칭 개체를 나타내며 파이프라인에서 개체를 cmdlet으로 보냅니다 `Format-List` . `Format-List`**속성** 매개 변수를 별표 ()와 함께 사용 하 여 `*` 모든 속성을 표시 합니다. 예제 출력에서는 이러한 속성의 일부 목록을 보여 줍니다.

`loc`두 매개 변수를 추가 하 여 별칭을 변경 합니다. **설명** 별칭의 용도를 설명 하는 텍스트를 추가 합니다. 별칭은 읽기 전용 이므로 **Force** 매개 변수가 필요 합니다 `loc` . **Force** 매개 변수를 사용 하지 않으면 변경이 실패 합니다.

### 예제 4: 실행 파일에 대 한 별칭 만들기

이 예제에서는 로컬 컴퓨터의 실행 파일에 대 한 별칭을 만듭니다.

```
PS> Set-Alias -Name np -Value C:\Windows\notepad.exe

PS> Get-Alias -Name np

CommandType     Name
-----------     ----
Alias           np -> notepad.exe
```

`Set-Alias`Cmdlet은 현재 PowerShell 세션에서 별칭을 만듭니다. **Name** 매개 변수는 별칭의 이름을 지정 합니다 `np` . **값** 매개 변수는 **C:\Windows\notepad.exe** 경로 및 응용 프로그램 이름을 지정 합니다. `Get-Alias`이 cmdlet은 **Name** 매개 변수를 사용 하 여 `np` 별칭이 **notepad.exe** 와 연결 되어 있음을 보여 줍니다.

별칭을 실행 하려면 `np` PowerShell 명령줄에를 입력 하 여 **notepad.exe** 를 엽니다.

### 예 5: 매개 변수를 사용 하 여 명령에 대 한 별칭 만들기

이 예제에서는 매개 변수를 사용 하 여 명령에 별칭을 할당 하는 방법을 보여 줍니다.

Cmdlet에 대 한 별칭을 만들 수 있습니다 (예:) `Set-Location` . 매개 변수 및 값 (예:)을 사용 하 여 명령에 대 한 별칭을 만들 수 없습니다 `Set-Location -Path C:\Windows\System32` . 명령의 별칭을 만들려면 명령이 포함된 함수를 만든 다음 함수의 별칭을 만듭니다. 자세한 내용은 [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)를 참조 하세요.

```
PS> Function CD32 {Set-Location -Path C:\Windows\System32}

PS> Set-Alias -Name Go -Value CD32
```

이라는 함수를 `CD32` 만듭니다. 함수는 `Set-Location` **Path** 매개 변수와 함께 cmdlet을 사용 하 여 디렉터리를 지정 합니다 ( **c:\system32** ).

`Set-Alias`Cmdlet은 현재 PowerShell 세션에서 함수에 대 한 별칭을 만듭니다. **Name** 매개 변수는 별칭의 이름을 지정 합니다 `Go` . **값** 매개 변수는 함수의 이름를 지정 합니다 `CD32` .

별칭을 실행 하려면 `Go` PowerShell 명령줄에를 입력 합니다. 함수는를 `CD32` 실행 하 고 디렉터리를 **C:\Windows\System32** 변경 합니다.

## PARAMETERS

### -Description

별칭에 대한 설명을 지정합니다. 아무 문자열이나 입력할 수 있습니다. 설명에 공백이 포함 되어 있으면 작은따옴표로 묶습니다.

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

### -Force

**Force** 매개 변수를 사용 하 여 **Option** 매개 변수가 **ReadOnly** 로 설정 된 별칭을 변경 하거나 삭제할 수 있습니다.

**Force** 매개 변수는 **상수** 로 설정 된 **Option** 매개 변수를 사용 하 여 별칭을 변경 하거나 삭제할 수 없습니다.

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

### -Name

새 별칭의 이름을 지정 합니다. 별칭 이름에는 영숫자 문자와 하이픈이 포함 될 수 있습니다. 별칭 이름은 숫자 (예: 123) 일 수 없습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -옵션

별칭의 **Option** 속성 값을 설정 합니다. **ReadOnly** 및 **Constant** 와 같은 값은 의도 하지 않은 변경 으로부터 별칭을 보호 합니다. 세션에 있는 모든 별칭의 **Option** 속성을 보려면를 입력 `Get-Alias | Format-Table -Property Name, Options -Autosize` 합니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- **AllScope** 별칭은 새로 생성 된 범위에 복사 됩니다.
- **상수** 을 변경 하거나 삭제할 수 없습니다.
- **없음** 는 옵션을 설정 하지 않으며 기본값입니다.
- **개인** 별칭은 현재 범위 에서만 사용할 수 있습니다.
- **읽기 전용** **Force** 매개 변수를 사용 하지 않으면를 변경 하거나 삭제할 수 없습니다.
- **Unspecified**

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: AllScope, Constant, None, Private, ReadOnly, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

별칭을 나타내는 개체를 반환합니다. 와 같은 형식 cmdlet을 사용 `Format-List` 하 여 개체를 표시 합니다. 기본적으로는 `Set-Alias` 출력을 생성 하지 않습니다.

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

### -범위

이 별칭이 유효한 범위를 지정합니다. 기본값은 **Local** 입니다. 자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.

허용 되는 값은 다음과 같습니다.

- 전역
- 로컬
- Private
- 번호가 매겨진 범위
- 스크립트

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Global, Local, Private, Numbered scopes, Script

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

별칭이 실행 되는 cmdlet 또는 명령의 이름을 지정 합니다. **값** 매개 변수는 별칭의 **정의** 속성입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
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

### 없음

`Set-Alias` 파이프라인의 입력을 허용 하지 않습니다.

## 출력

### 없음 또는 System.management.automation.aliasinfo

**PassThru** 매개 변수를 사용 하는 경우는 `Set-Alias` 별칭을 나타내는 **system.management.automation.aliasinfo** 개체를 생성 합니다. 그렇지 않으면에서 `Set-Alias` 출력을 생성 하지 않습니다.

## 참고

PowerShell은 각 PowerShell 세션에서 사용할 수 있는 기본 제공 별칭을 포함 합니다. `Get-Alias`Cmdlet은 PowerShell 세션에서 사용할 수 있는 별칭을 표시 합니다.

별칭을 만들려면 cmdlet 또는를 사용 `Set-Alias` `New-Alias` 합니다. PowerShell 6에서 별칭을 삭제 하려면 cmdlet을 사용 `Remove-Alias` 합니다. `Remove-Item` 이전 버전의 PowerShell을 사용 하 여 만든 스크립트와 같은 이전 버전과의 호환성을 위해이 허용 됩니다. 와 같은 명령을 사용 `Remove-Item -Path Alias:aliasname` 합니다.

각 PowerShell 세션에서 사용할 수 있는 별칭을 만들려면 PowerShell 프로필에 추가 합니다.
자세한 내용은 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)를 참조 하세요.

내보내기 및 가져오기를 수행 하 여 다른 PowerShell 세션에서 별칭을 저장 하 고 다시 사용할 수 있습니다. 별칭을 파일에 저장 하려면를 사용 `Export-Alias` 합니다. 새 PowerShell 세션에 저장 된 별칭을 추가 하려면를 사용 `Import-Alias` 합니다.

## 관련 링크

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)

[about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)

[about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Remove-Alias](Remove-Alias.md)

[Remove-Item](../Microsoft.PowerShell.Management/Remove-Item.md)


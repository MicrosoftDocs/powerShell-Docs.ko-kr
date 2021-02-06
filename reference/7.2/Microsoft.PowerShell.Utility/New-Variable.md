---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: c77eb9c64022d028c3c4b2de6bf4551886b940e1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599566"
---
# New-Variable

## 개요
새 변수를 만듭니다.

## SYNTAX

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명
**새 변수** Cmdlet은 PowerShell에 새 변수를 만듭니다.
변수를 만드는 동안 값을 할당할 수도 있고 만든 후에 값을 할당하거나 변경할 수도 있습니다.

**새 변수** 매개 변수를 사용 하 여 변수의 속성을 설정 하 고, 변수의 범위를 설정 하 고, 변수가 공용 변수 인지 아니면 개인 변수 인지를 결정할 수 있습니다.

일반적으로 변수 이름과 해당 값 (예:)을 입력 하 여 새 변수를 `$Var = 3` 만들지만, **새** 변수 cmdlet을 사용 하 여 해당 매개 변수를 사용할 수 있습니다.

## 예제

### 예제 1: 변수 만들기

```
PS C:\> New-Variable days
```

이 명령은 days 라는 새 변수를 만듭니다.
*Name* 매개 변수를 입력할 필요는 없습니다.

### 예 2: 변수를 만들고 값을 할당 합니다.

```
PS C:\> New-Variable -Name "zipcode" -Value 98033
```

이 명령은 zipcode 라는 변수를 만들고 값 98033을 할당 합니다.

### 예제 3: ReadOnly 옵션을 사용 하 여 변수 만들기

```
PS C:\> New-Variable -Name Max -Value 256 -Option ReadOnly
PS C:\> New-Variable -Name max -Value 1024

New-Variable : A variable with name 'max' already exists.
At line:1 char:1
+ New-Variable -Name max -Value 1024
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ResourceExists: (max:String) [New-Variable], SessionStateException
    + FullyQualifiedErrorId : VariableAlreadyExists,Microsoft.PowerShell.Commands.NewVariableCommand

PS C:\> New-Variable -Name max -Value 1024 -Force
```

이 예에서는 **New 변수의** ReadOnly 옵션을 사용 하 여 변수를 덮어쓰지 않도록 보호 하는 방법을 보여 줍니다.

첫 번째 명령은 Max 라는 새 변수를 만들고 해당 값을 256로 설정 합니다.
*Option* 매개 변수를 ReadOnly 값과 함께 사용 합니다.

두 번째 명령은 이름이 같은 두 번째 변수를 만들려고 시도합니다.
그러나 변수에 대해 읽기 전용 옵션이 설정되어 있으므로 이 명령을 실행하면 오류가 반환됩니다.

세 번째 명령은 *Force* 매개 변수를 사용 하 여 변수에 대 한 읽기 전용 보호를 재정의 합니다.
이 경우에는 이름이 같은 새 변수를 만드는 명령이 제대로 실행됩니다.

### 예제 4: 전용 변수 만들기

```
PS C:\> New-Variable -Name counter -Visibility Private

#Effect of private variable in a module.

PS C:\> Get-Variable c*

Name                           Value
----                           -----
Culture                        en-US
ConsoleFileName
ConfirmPreference              High
CommandLineParameters          {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"
At line:1 char:1
+ $counter
+ ~~~~~~~~
    + CategoryInfo          : PermissionDenied: (counter:String) [], SessionStateException
    + FullyQualifiedErrorId : VariableIsPrivate

PS C:\> Get-Counter
Name         Value
----         -----
Counter1     3.1415
...
```

이 명령은 모듈의 개인 변수 동작을 보여 줍니다.
이 모듈에는 Counter 라는 전용 변수가 있는 Get-Counter cmdlet이 포함 되어 있습니다.
이 명령은 값이 Private 인 *Visibility* 매개 변수를 사용 하 여 변수를 만듭니다.

샘플 출력은 개인 변수의 동작을 보여 줍니다.
모듈을 로드한 사용자는 Counter 변수 값을 보거나 변경할 수 없지만, 모듈의 명령을 통해 Counter 변수를 읽고 변경할 수 있습니다.

### 예 5: 공백으로 변수 만들기

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

이 명령은 공백이 있는 변수를 만들 수 있음을 보여 줍니다.
변수는 **Get 변수** cmdlet을 사용 하 여 액세스 하거나 중괄호를 사용 하 여 변수를 구분 하 여 직접 액세스할 수 있습니다.

## PARAMETERS

### -Description
변수의 설명을 지정합니다.

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
Cmdlet이 기존 읽기 전용 변수와 이름이 같은 변수를 생성 함을 나타냅니다.

기본적으로 ReadOnly 또는 Constant 옵션 값이 없는 변수는 덮어쓸 수 있습니다.
자세한 내용은 *Option* 매개 변수를 참조 하세요.

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

### -Name
새 변수의 이름을 지정합니다.

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
변수의 **Options** 속성 값을 지정 합니다. 이 매개 변수에 허용 되는 값은 다음과 같습니다.

- 없음
옵션을 설정하지 않습니다.
기본값은 없음입니다.
- ReadOnly.
삭제할 수 있습니다.
*Force* 매개 변수를 사용 하는 경우를 제외 하 고는 변경할 수 없습니다.
- 비공개.
변수는 현재 범위에서만 사용할 수 있습니다.
- AllScope.
변수는 새로 만든 범위로 복사됩니다.
- 상수입니다.
삭제하거나 변경할 수 없습니다.
상수는 변수를 만드는 경우에만 유효 합니다.
기존 변수의 옵션을 Constant로 변경할 수 없습니다.

세션에 있는 모든 변수의 **Options** 속성을 보려면를 입력 `Get-Variable | Format-Table -Property name, options -autosize` 합니다.

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -범위
새 변수의 범위를 지정 합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 전역적.
전역 범위에서 만든 변수는 PowerShell 프로세스의 모든 위치에서 액세스할 수 있습니다.
- 로컬.
로컬 범위는 현재 범위를 참조 하며, 컨텍스트에 따라 모든 범위가 될 수 있습니다.
- 스크립트.
스크립트 범위에서 만든 변수는 스크립트 파일이 나 생성 된 모듈 내 에서만 액세스할 수 있습니다.
- 비공개.
전용 범위에서 만든 변수는에 존재 하는 범위 밖에 서 액세스할 수 없습니다.
전용 범위를 사용 하 여 다른 범위에 있는 동일한 이름의 개인 버전을 만들 수 있습니다.
- 현재 범위 (0부터 범위 수까지, 여기서 0은 현재 범위, 1은 부모, 2는 부모 범위의 부모)에 상대적인 숫자입니다.
음수를 사용할 수 없습니다.

범위 매개 변수가 지정 되지 않은 경우 Local은 기본 범위입니다.

자세한 내용은 about_Scopes를 참조하세요.

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

### -Value
변수의 초기 값을 지정합니다.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -표시 유형
변수를 만든 세션 외부에서도 변수가 표시되는지를 결정합니다.
이 매개 변수는 다른 사용자에게 전달할 스크립트 및 명령에 사용할 수 있습니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 공개.
변수가 표시됩니다.
기본값은 Public입니다.
- 비공개.
변수가 표시되지 않습니다.

개인 변수는 Get-Variable에서 반환하는 목록과 같은 변수 목록이나 Variable: 드라이브의 표시에 나타나지 않습니다.
개인 변수의 값을 읽거나 변경하는 명령을 실행하면 오류가 반환됩니다.
그러나 변수를 정의한 세션에서 명령을 작성한 경우에는 개인 변수를 사용하는 명령을 실행할 수 있습니다.

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: None
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
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.Object
**새 변수에** 값을 파이프 할 수 있습니다.

## 출력

### None 또는 System.object입니다.
*PassThru* 매개 변수를 사용 하는 경우 **새** 변수는 새 변수를 나타내는 **system.object** 를 생성 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

## 관련 링크

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[Remove-Variable](Remove-Variable.md)

[Set-Variable](Set-Variable.md)


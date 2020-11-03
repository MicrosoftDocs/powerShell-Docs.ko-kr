---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 2041d40803aac1afafad2a0855aa39ebba9ad814
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239864"
---
# Set-Variable

## 개요
변수 값을 설정합니다. 요청한 이름이 있는 변수가 없으면 새로 만듭니다.

## SYNTAX

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Set-Variable`Cmdlet은 지정 된 변수에 값을 할당 하거나 현재 값을 변경 합니다. 변수가 없는 경우 cmdlet이 만듭니다.

## 예제

### 예 1: 변수를 설정 하 고 해당 값 가져오기

이러한 명령은 변수의 값을로 설정 하 `$desc` `A description` 고 변수 값을 가져옵니다.

```powershell
Set-Variable -Name "desc" -Value "A description"
Get-Variable -Name "desc"
```

```Output
Name                           Value
----                           -----
desc                           A description
```

### 예 2: 읽기 전용 전역 변수 설정

이 예에서는 시스템의 모든 프로세스가 포함 된 읽기 전용의 전역 변수를 만든 다음 변수의 모든 속성을 표시 합니다.

```powershell
Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru |
    Format-List -Property *
```

이 명령은 cmdlet을 사용 하 여 `Set-Variable` 변수를 만듭니다. **PassThru** 매개 변수를 사용 하 여 새 변수를 나타내는 개체를 만든 다음 파이프라인 연산자 ()를 사용 하 여 `|` 개체를 cmdlet으로 전달 `Format-List` 합니다. 의 **Property** 매개 변수를 `Format-List` all () 값과 함께 사용 `*` 하 여 새로 만든 변수의 모든 속성을 표시 합니다.

값은 `(Get-Process)` 변수에 저장 하기 전에 실행 되도록 괄호로 묶여 있습니다. 그렇지 않으면 변수는 " **Get Process** " 라는 단어를 포함 합니다.

### 예제 3: public 및 private 변수 이해

이 예에서는 변수의 표시 유형을로 변경 하는 방법을 보여 줍니다 `Private` . 이 변수는 필요한 권한을 가진 스크립트를 통해 읽거나 변경할 수 있지만 사용자에게 표시되지는 않습니다.

```
PS C:\> New-Variable -Name "counter" -Visibility Public -Value 26
PS C:\> $Counter
26

PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}
Counter               26

PS C:\> Set-Variable -Name "counter" -Visibility Private
PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"

PS C:\> .\use-counter.ps1
#Commands completed successfully.
```

이 명령은 변수의 표시 유형을 Private으로 변경 하는 방법을 보여 줍니다. 이 변수는 필요한 권한을 가진 스크립트를 통해 읽거나 변경할 수 있지만 사용자에게 표시되지는 않습니다.

## PARAMETERS

### -Description

변수에 대한 설명을 지정합니다.

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

### -제외

이 cmdlet이 작업에서 제외 하는 항목의 배열을 지정 합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.
와일드카드가 지원됩니다.

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

### -Force

기존 읽기 전용 변수와 이름이 같은 변수를 만들거나 읽기 전용 변수의 값을 변경할 수 있도록 허용합니다.

기본적으로 변수에 또는의 옵션 값이 없는 경우 변수를 덮어쓸 수 있습니다 `ReadOnly` `Constant` . 자세한 내용은 **Option** 매개 변수를 참조 하세요.

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

이 cmdlet이 작업에 포함 하는 항목의 배열을 지정 합니다. 이 매개 변수 값은 **Name** 매개 변수를 한정 합니다. 이름 또는 이름 패턴 (예:)을 입력 `c*` 합니다. 와일드카드가 지원됩니다.

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

### -Name

변수 이름을 지정합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -옵션

변수의 **Options** 속성 값을 지정 합니다.

유효한 값은 다음과 같습니다.

- `None`: 옵션을 설정 하지 않습니다. "None"이 기본값입니다.
- `ReadOnly`: 삭제할 수 있습니다. Force 매개 변수를 사용 하는 경우를 제외 하 고는 변경할 수 없습니다.
- `Constant`: 삭제 하거나 변경할 수 없습니다. `Constant` 는 변수를 만드는 경우에만 유효 합니다. 기존 변수의 옵션을로 변경할 수 없습니다 `Constant` .
- `Private`: 변수는 현재 범위 에서만 사용할 수 있습니다.
- `AllScope`: 변수가 만들어진 모든 새 범위로 복사 됩니다.

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

새 변수를 나타내는 개체를 반환합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -범위

변수의 범위를 지정 합니다. 이 매개 변수에 허용 되는 값은 다음과 같습니다.

- 전역
- 로컬
- 스크립트
- Private
- 현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)입니다.

Local이 기본값입니다.

자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

변수의 값을 지정합니다.

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

변수를 만든 세션 외부에서도 변수가 표시되는지를 결정합니다. 이 매개 변수는 다른 사용자에 게 전달 되는 스크립트 및 명령에 사용 하도록 설계 되었습니다.

유효한 값은 다음과 같습니다.

- Public: 변수가 표시 됩니다. "Public"이 기본값입니다.
- Private: 변수가 표시 되지 않습니다.

변수가 private 이면 변수가에서 반환 하는 변수 `Get-Variable` 또는 **변수:** 드라이브의 표시와 같은 변수 목록에 나타나지 않습니다. 개인 변수의 값을 읽거나 변경하는 명령을 실행하면 오류가 반환됩니다. 그러나 변수를 정의한 세션에서 명령을 작성한 경우에는 개인 변수를 사용하는 명령을 실행할 수 있습니다.

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: Public
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

### System.Object

변수의 값을 나타내는 개체를로 파이프 할 수 있습니다 `Set-Variable` .

## 출력

### None 또는 System.object입니다.

**PassThru** 매개 변수를 사용 하는 경우는 `Set-Variable` 새 변수 또는 변경 된 변수를 나타내는 **system.object** 를 생성 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

## 관련 링크

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[New-Variable](New-Variable.md)

[Remove-Variable](Remove-Variable.md)

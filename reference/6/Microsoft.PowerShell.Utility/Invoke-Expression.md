---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-expression?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Expression
ms.openlocfilehash: 575f696d74e6a7aa7cf864cbb559f15a25ac1a66
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214962"
---
# Invoke-Expression

## 개요
로컬 컴퓨터에서 명령 또는 식을 실행합니다.

## SYNTAX

```
Invoke-Expression [-Command] <String> [<CommonParameters>]
```

## 설명

`Invoke-Expression`Cmdlet은 지정 된 문자열을 명령으로 평가 하거나 실행 하 여 식 또는 명령의 결과를 반환 합니다. `Invoke-Expression`를 사용 하지 않으면 명령줄에서 전송 된 문자열이 변경 되지 않고 반환 됩니다.

식이 평가 되 고 현재 범위에서 실행 됩니다. 자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.

> [!CAUTION]
> 스크립트에서 cmdlet을 사용할 때 적절 한 예방 조치 `Invoke-Expression` 를 취합니다. 를 사용 하 여 `Invoke-Expression` 사용자가 입력 하는 명령을 실행 하는 경우 명령을 실행 하기 전에 명령을 실행 해도 안전한 지 확인 합니다. 일반적으로는 자유 형태 입력을 허용하는 것보다 미리 정의된 입력 옵션을 사용하여 스크립트를 디자인하는 것이 가장 좋습니다.

## 예제

### 예제 1: 식 계산

```powershell
$Command = "Get-Process"
$Command
```

```Output
Get-Process
```

```powershell
Invoke-Expression $Command
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
296       4       1572       1956    20       0.53     1348   AdtAgent
270       6       1328       800     34       0.06     2396   alg
67        2       620        484     20       0.22     716    ati2evxx
1060      15      12904      11840   74       11.48    892    CcmExec
1400      33      25280      37544   223      38.44    2564   communicator
...
```

이 예에서는를 사용 `Invoke-Expression` 하 여 식을 계산 하는 방법을 보여 줍니다. 가 없으면 `Invoke-Expression` 식이 출력 되지만 계산 되지 않습니다.

첫 번째 명령은 `Get-Process` 변수에 (문자열) 값을 할당 `$Command` 합니다.

두 번째 명령은 명령줄에 변수 이름을 입력하는 경우의 효과를 보여 줍니다. PowerShell에서 문자열을 에코 합니다.

세 번째 명령은 `Invoke-Expression` 를 사용 하 여 문자열을 평가 합니다.

### 예제 2: 로컬 컴퓨터에서 스크립트 실행

```powershell
Invoke-Expression -Command "C:\ps-test\testscript.ps1"
"C:\ps-test\testscript.ps1" | Invoke-Expression
```

이러한 명령은를 사용 `Invoke-Expression` 하 여 로컬 컴퓨터에서 TestScript.ps1 스크립트를 실행 합니다. 두 명령은 서로 동일합니다. 첫 번째는 **command** 매개 변수를 사용 하 여 실행할 명령을 지정 합니다.
두 번째는 파이프라인 연산자 ()를 사용 하 여 `|` 명령 문자열을로 보냅니다 `Invoke-Expression` .

### 예제 3: 변수에서 명령 실행

```powershell
$Command = 'Get-Process | where {$_.cpu -gt 1000}'
Invoke-Expression $Command
```

이 예에서는 변수에 저장 되는 명령 문자열을 실행 `$Command` 합니다.

명령 문자열은 현재 개체를 나타내는 변수를 포함 하기 때문에 작은따옴표로 묶여 있습니다 `$_` . 큰따옴표로 묶여 있으면 변수에 변수를 `$_` 저장 하기 전에 해당 값으로 대체 됩니다 `$Command` .

### 예제 4: cmdlet 도움말 예제 가져오기 및 실행

```powershell
$Cmdlet_name = "Get-EventLog"
$Example_number = 1
$Example_code = (Get-Help $Cmdlet_name).examples.example[($Example_number-1)].code
Invoke-Expression $Example_code
```

이 명령은 cmdlet 도움말 항목에서 첫 번째 예제를 검색 하 고 실행 합니다 `Get-EventLog` .

다른 cmdlet의 예를 실행 하려면 변수 값을 `$Cmdlet_name` cmdlet의 이름으로 변경 합니다. 그리고 `$Example_number` 변수를 실행 하려는 예제 번호로 변경 합니다. 예 번호가 잘못 된 경우 명령이 실패 합니다.

## PARAMETERS

### -Command

실행할 명령 또는 식을 지정합니다. 명령 또는 식을 입력하거나 명령 또는 식이 포함된 변수를 입력합니다. **명령** 매개 변수는 필수입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.string 또는 PSObject

명령을 나타내는 개체를로 파이프 할 수 있습니다 `Invoke-Expression` .
`$Input`자동 변수를 사용 하 여 명령에서 입력 개체를 나타냅니다.

## 출력

### PSObject

호출 된 명령 ( **command** 매개 변수 값)에 의해 생성 된 출력을 반환 합니다.

## 참고

대부분의 경우 PowerShell의 call 연산자를 사용 하 여 식을 호출 하 고 동일한 결과를 얻습니다.
Call 연산자는 안전한 방법입니다. 자세한 내용은 [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-)를 참조 하세요.

## 관련 링크

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)

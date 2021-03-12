---
description: PowerShell에서 사용 되는 구문 다이어그램에 대해 설명 합니다.
Locale: en-US
ms.date: 06/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_syntax?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Syntax
ms.openlocfilehash: 05677d5633c56efd4b7c44c16f9c4e34a222e8b0
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195191"
---
# <a name="about-command-syntax"></a>명령 구문 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 사용 되는 구문 다이어그램에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

[Get-help](xref:Microsoft.PowerShell.Core.Get-Help) 및 [get Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlet은 명령을 올바르게 생성 하는 데 도움이 되는 구문 다이어그램을 표시 합니다. 이 항목에서는 구문 다이어그램을 해석 하는 방법에 대해 설명 합니다.

## <a name="syntax-diagrams"></a>구문 다이어그램

명령 구문 다이어그램의 각 단락은 명령의 올바른 형태를 나타냅니다.

명령을 생성 하려면 구문 다이어그램의 왼쪽에서 오른쪽으로 이동 합니다. 선택적 매개 변수 중에서 하나를 선택 하 고 자리 표시자에 대 한 값을 제공 합니다.

PowerShell에서는 구문 다이어그램에 다음 표기법을 사용 합니다.

```powershell
<command-name> -<Required Parameter Name> <Required Parameter Value>
[-<Optional Parameter Name> <Optional Parameter Value>]
[-<Optional Switch Parameters>]
[-<Optional Parameter Name>] <Required Parameter Value>
```

다음은 [새 별칭](xref:Microsoft.PowerShell.Utility.New-Alias) cmdlet에 대 한 구문입니다.

```powershell
New-Alias [-Name] <string> [-Value] <string> [-Description <string>]
[-Force] [-Option {None | ReadOnly | Constant | Private | AllScope}]
[-PassThru] [-Scope <string>] [-Confirm] [-WhatIf] [<CommonParameters>]
```

구문은 가독성을 위해 대문자로 표기 되지만 PowerShell은 대/소문자를 구분 하지 않습니다.

구문 다이어그램에는 다음과 같은 요소가 있습니다.

## <a name="command-name"></a>명령 이름

명령은 항상 명령 이름 (예:)으로 시작 `New-Alias` 합니다. 명령 이름 또는 해당 별칭 (예:의 "gcm")을 입력 합니다 `Get-Command` .

## <a name="parameters"></a>매개 변수

명령의 매개 변수는 명령이 수행 하는 작업을 결정 하는 옵션입니다.
일부 매개 변수는 명령에 대 한 사용자 입력 인 "값"을 사용 합니다.

예를 들어 명령에는 `Get-Help` 도움말이 표시 되는 항목의 이름을 지정할 수 있는 **name** 매개 변수가 있습니다. 토픽 이름은 **name** 매개 변수의 값입니다.

PowerShell 명령에서 매개 변수 이름은 항상 하이픈으로 시작 합니다.
하이픈은 명령의 항목이 매개 변수 이름 임을 PowerShell에 알려 줍니다.

예를 들어의 Name 매개 변수를 사용 하려면 `New-Alias` 다음을 입력 합니다.

```powershell
-Name
```

매개 변수는 필수 또는 선택적 일 수 있습니다. 구문 다이어그램에서 선택적 항목은 대괄호로 묶여 `[ ]` 있습니다.

매개 변수에 대 한 자세한 내용은 [about_Parameters](about_Parameters.md)를 참조 하세요.

## <a name="parameter-values"></a>매개 변수 값

매개 변수 값은 매개 변수가 사용 하는 입력입니다. Windows PowerShell은 Microsoft .NET 프레임 워크를 기반으로 하기 때문에 매개 변수 값은 구문 다이어그램에서 .NET 형식으로 표시 됩니다.

예를 들어의 Name 매개 변수는 `Get-Help` "string" 값을 사용 합니다 .이 값은 단일 단어 또는 따옴표로 묶인 여러 단어와 같은 텍스트 문자열입니다.

```powershell
[-Name] <string>
```

매개 변수 값의 .NET 형식은 꺾쇠 괄호로 묶어 `< >` 명령에 입력 하는 리터럴이 아니라 값에 대 한 자리 표시자 임을 나타낼 수 있습니다.

매개 변수를 사용 하려면 .NET 형식 자리 표시자를 지정 된 .NET 형식의 개체로 바꿉니다.

예를 들어 **name** 매개 변수를 사용 하려면 다음과 같이 "-name"을 입력 한 다음 문자열을 입력 합니다.

```powershell
-Name MyAlias
```

## <a name="parameters-with-no-values"></a>값이 없는 매개 변수

일부 매개 변수는 입력을 허용 하지 않으므로 매개 변수 값이 없습니다.
값이 없는 매개 변수는 설정/해제 스위치 처럼 작동 하므로 "스위치 매개 변수" 라고 합니다. 이러한 항목을 포함 하거나 명령에서 생략할 수 있습니다 (꺼짐).

스위치 매개 변수를 사용 하려면 매개 변수 이름을 하이픈 앞에 입력 하면 됩니다.

예를 들어 cmdlet의 **WhatIf** 매개 변수를 사용 하려면 `New-Alias` 다음을 입력 합니다.

```powershell
-WhatIf
```

## <a name="parameter-sets"></a>매개 변수 집합

명령의 매개 변수는 매개 변수 집합에 나열 됩니다. 매개 변수 집합은 구문 다이어그램의 단락과 같습니다.

Cmdlet에는 `New-Alias` 하나의 매개 변수 집합이 있지만 많은 cmdlet에는 여러 매개 변수 집합이 있습니다. 일부 cmdlet 매개 변수는 매개 변수 집합에 대해 고유 하며, 다른 매개 변수는 여러 매개 변수 집합에 표시 됩니다. 각 매개 변수 집합은 유효한 명령의 형식을 나타냅니다. 매개 변수 집합에는 명령에 함께 사용할 수 있는 매개 변수만 포함 됩니다. 동일한 명령에서 매개 변수를 사용할 수 없는 경우 별도의 매개 변수 집합에 표시 됩니다.

예를 들어, [Get Random](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet에는 다음과 같은 매개 변수 집합이 있습니다.

```powershell
Get-Random [[-Maximum] <Object>] [-Minimum <Object>] [-SetSeed <int>]
[<CommonParameters>]

Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>]
[<CommonParameters>]
```

난수를 반환 하는 첫 번째 매개 변수 집합에는 **최소** 및 **최대** 매개 변수가 있습니다. 개체 집합에서 무작위로 선택 된 개체를 반환 하는 두 번째 매개 변수 집합에는 **InputObject** 및 **Count** 매개 변수가 포함 됩니다. 두 매개 변수 집합 모두에는 **Setseed** 매개 변수와 일반 매개 변수가 있습니다.

이러한 매개 변수 집합은 동일한 명령에서 **InputObject** 및 **count** 매개 변수를 사용할 수 있지만 동일한 명령에서 **Maximum** 및 **count** 매개 변수를 사용할 수 없음을 의미 합니다.

해당 매개 변수 집합에서 매개 변수를 사용 하 여 사용 하려는 매개 변수 집합을 지정 합니다.

그러나 모든 cmdlet에는 기본 매개 변수 집합이 있습니다. 기본 매개 변수 집합은 매개 변수 집합에 고유한 매개 변수를 지정 하지 않을 때 사용 됩니다. 예를 들어 `Get-Random` 매개 변수 없이를 사용 하는 경우 Windows PowerShell은 사용자가 **number** 매개 변수 집합을 사용 하 고 있으며 난수를 반환 한다고 가정 합니다.

각 매개 변수 집합에서 매개 변수는 위치 순서 대로 표시 됩니다. 명령의 매개 변수 순서는 선택적 매개 변수 이름을 생략 하는 경우에만 중요 합니다. 매개 변수 이름을 생략 하면 PowerShell은 위치 및 유형별로 매개 변수에 값을 할당 합니다. 매개 변수 위치에 대 한 자세한 내용은을 참조 하십시오 `about_Parameters` .

## <a name="symbols-in-syntax-diagrams"></a>구문 다이어그램의 기호

구문 다이어그램은 명령 이름, 명령 매개 변수 및 매개 변수 값을 나열 합니다. 또한 기호를 사용 하 여 유효한 명령을 생성 하는 방법을 보여 줍니다.

구문 다이어그램은 다음 기호를 사용 합니다.

- 하이픈은 `-` 매개 변수 이름을 나타냅니다. 구문 다이어그램에 표시 된 것 처럼 명령에 공백을 사용 하지 않고 매개 변수 이름 바로 앞에 하이픈을 입력 합니다.

  예를 들어의 **Name** 매개 변수를 사용 하려면 `New-Alias` 다음을 입력 합니다.

  ```powershell
  -Name
  ```

- 꺾쇠 괄호는 `<>` 자리 표시자 텍스트를 표시 합니다. 명령에 꺾쇠 괄호 또는 자리 표시자 텍스트를 입력 하지 않습니다. 대신이 항목을 설명 하는 항목으로 바꿉니다.

  꺾쇠 괄호는 매개 변수에서 사용 하는 값의 .NET 유형을 식별 하는 데 사용 됩니다. 예를 들어 cmdlet의 **Name** 매개 변수를 사용 하려면 `New-Alias` 를 `<string>` 문자열로 바꿉니다 .이 문자열은 단일 단어나 따옴표로 묶인 단어 그룹입니다.

- 대괄호는 `[ ]` 선택적 항목을 표시 합니다. 매개 변수 및 해당 값은 선택 사항이 될 수 있으며, 필수 매개 변수의 이름은 선택 사항 일 수 있습니다.

  예를 들어의 **Description** 매개 변수 `New-Alias` 및 해당 값은 모두 선택 사항 이므로 대괄호로 묶여 있습니다.

  ```powershell
  [-Description <string>]
  ```

  대괄호는 또한 Name 매개 변수 값이 필요 하다는 것 `<string>` 을 나타내지만 매개 변수 이름 "name"은 선택적입니다.

  ```powershell
  [-Name] <string>
  ```

- .NET 형식에 오른쪽 및 왼쪽 대괄호가 추가 된 경우 `[]` 매개 변수가 해당 형식의 값을 하나 또는 여러 개 사용할 수 있음을 나타냅니다. 쉼표로 구분된 목록으로 값을 입력합니다.

  예를 들어 cmdlet의 **name** 매개 변수는 `New-Alias` 하나의 문자열만 사용 하지만, [Get-Process](xref:Microsoft.PowerShell.Management.Get-Process) 의 **name** 매개 변수는 하나 이상의 문자열을 사용할 수 있습니다.

  ```powershell
  New-Alias [-Name] <string>

  New-Alias -Name MyAlias
  ```

  ```powershell
  Get-Process [-Name] <string[]>

  Get-Process -Name Explorer, Winlogon, Services
  ```

- 중괄호는 `{}` 매개 변수의 유효한 값 집합인 "열거형"을 의미 합니다.

  중괄호의 값은 세로 막대로 구분 됩니다 `|` . 이러한 막대는 "배타적 OR" 선택을 나타냅니다. 즉, 중괄호 안에 나열 된 값 집합에서 값을 하나만 선택할 수 있습니다.

  예를 들어 cmdlet에 대 한 구문에는 `New-Alias` **Option** 매개 변수에 대 한 다음 값 열거형이 포함 됩니다.

  ```powershell
  -Option {None | ReadOnly | Constant | Private | AllScope}
  ```

  중괄호 및 세로 막대는 **Option** 매개 변수에 대해 나열 된 값 중 하나 (예: "ReadOnly" 또는 "AllScope")를 선택할 수 있음을 의미 합니다.

  ```powershell
  -Option ReadOnly
  ```

## <a name="optional-items"></a>선택적 항목

대괄호는 `[]` 선택적 항목을 둘러쌉니다. 예를 들어 `New-Alias` cmdlet 구문 설명에서 **Scope** 매개 변수는 선택 사항입니다. 이는 매개 변수 이름 및 유형을 괄호로 묶어 구문에 표시 합니다.

```powershell
[-Scope <string>]
```

다음은 cmdlet의 올바른 사용 예입니다 `New-Alias` .

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd -Value Update-TypeData -Scope Global
```

매개 변수 이름은 해당 매개 변수의 값이 필요한 경우에도 선택할 수 있습니다. 이는 cmdlet의이 예제와 같이 매개 변수 이름 주위의 대괄호에 의해 구문에서 표시 됩니다 `New-Alias` .

```powershell
[-Name] <string> [-Value] <string>
```

다음 명령은 cmdlet을 올바르게 사용 합니다 `New-Alias` . 명령은 동일한 결과를 생성 합니다.

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd Update-TypeData
New-Alias utd -Value Update-TypeData
New-Alias utd Update-TypeData
```

매개 변수 이름이 문에 형식으로 포함 되지 않은 경우 Windows PowerShell은 인수 위치를 사용 하 여 매개 변수에 값을 할당 하려고 합니다.

다음 예제는 완전 하지 않습니다.

```powershell
New-Alias utd
```

이 cmdlet에는 **Name** 및 **Value** 매개 변수 모두에 대 한 값이 필요 합니다.

구문 예제에서는 괄호를 사용 하 여 .NET Framework 형식에 대 한 이름 지정 및 캐스팅에도 사용 됩니다. 이 컨텍스트에서 대괄호는 요소가 선택 사항임을 나타내지 않습니다.

## <a name="see-also"></a>참고 항목

- [about_Parameters](about_Parameters.md)
- [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)
- [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)


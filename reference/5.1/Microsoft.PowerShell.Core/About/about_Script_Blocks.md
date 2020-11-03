---
description: 스크립트 블록이 무엇 인지 정의 하 고 PowerShell 프로그래밍 언어에서 스크립트 블록을 사용 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: f842701d83c525e4695debf99c4725580661b1de
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222545"
---
# <a name="about-script-blocks"></a>스크립트 블록 정보

## <a name="short-description"></a>간단한 설명

스크립트 블록이 무엇 인지 정의 하 고 PowerShell 프로그래밍 언어에서 스크립트 블록을 사용 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell 프로그래밍 언어에서 스크립트 블록은 단일 단위로 사용할 수 있는 문 또는 식의 컬렉션입니다.
스크립트 블록은 인수를 받아서 값을 반환할 수 있습니다.

구문적으로 스크립트 블록은 다음 구문에 표시 된 것 처럼 중괄호의 문 목록입니다.

```
{<statement list>}
```

스크립트 블록은 스크립트 블록의 모든 명령에 대 한 출력을 단일 개체 또는 배열로 반환 합니다.

키워드를 사용 하 여 반환 값을 지정할 수도 있습니다 `return` . `return`키워드는 스크립트 블록에서 반환 된 다른 출력에 영향을 주거나 표시 하지 않습니다. 그러나 키워드는 `return` 해당 줄에서 스크립트 블록을 종료 합니다. 자세한 내용은 [about_Return](about_Return.md)를 참조 하세요.

함수와 마찬가지로 스크립트 블록에는 매개 변수가 포함 될 수 있습니다. 다음 구문과 같이 Param 키워드를 사용 하 여 명명 된 매개 변수를 할당 합니다.

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> 스크립트 블록에서 함수와 달리 중괄호 외부에 매개 변수를 지정할 수 없습니다.

함수와 마찬가지로 스크립트 블록에는,, `DynamicParam` `Begin` `Process` 및 키워드가 포함 될 수 있습니다 `End` . 자세한 내용은 [about_Functions](about_Functions.md) 및 [about_Functions_Advanced](about_Functions_Advanced.md)를 참조 하세요.

## <a name="using-script-blocks"></a>스크립트 블록 사용

스크립트 블록은 Microsoft .NET Framework 형식의 인스턴스입니다 `System.Management.Automation.ScriptBlock` . 명령에는 스크립트 블록 매개 변수 값이 있을 수 있습니다. 예를 들어 cmdlet에는 `Invoke-Command` `ScriptBlock` 다음 예제와 같이 스크립트 블록 값을 사용 하는 매개 변수가 있습니다.

```powershell
Invoke-Command -ScriptBlock { Get-Process }
```

```Output
Handles  NPM(K)    PM(K)     WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----     ----- -----   ------     -- -----------
999          28    39100     45020   262    15.88   1844 communicator
721          28    32696     36536   222    20.84   4028 explorer
...
```

`Invoke-Command` 는 매개 변수 블록을 포함 하는 스크립트 블록을 실행할 수도 있습니다.
매개 변수는 **Argumentlist** 매개 변수를 사용 하 여 위치에 의해 할당 됩니다.

```powershell
Invoke-Command -ScriptBlock { param($p1, $p2)
"p1: $p1"
"p2: $p2"
} -ArgumentList "First", "Second"
```

```Output
p1: First
p2: Second
```

이전 예제의 스크립트 블록은 키워드를 사용 하 여 `param` 및 매개 변수를 `$p1` 만듭니다 `$p2` . "First" 문자열은 첫 번째 매개 변수 ()에 바인딩되고 `$p1` "Second"는 ()에 바인딩됩니다 `$p2` .

**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about_Splatting.md#splatting-with-arrays)를 참조 하세요.

변수를 사용 하 여 스크립트 블록을 저장 하 고 실행할 수 있습니다. 아래 예제에서는 스크립트 블록을 변수에 저장 하 고에 전달 `Invoke-Command` 합니다.

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

Call 연산자는 변수에 저장 된 스크립트 블록을 실행 하는 또 다른 방법입니다.
Like `Invoke-Command` 연산자는 자식 범위에서 스크립트 블록을 실행 합니다. Call 연산자를 사용 하면 스크립트 블록에서 매개 변수를 더 쉽게 사용할 수 있습니다.

```powershell
$a ={ param($p1, $p2)
"p1: $p1"
"p2: $p2"
}
&$a -p2 "First" -p1 "Second"
```

```Output
p1: Second
p2: First
```

할당을 사용 하 여 스크립트 블록의 출력을 변수에 저장할 수 있습니다.

```
PS>  $a = { 1 + 1}
PS>  $b = &$a
PS>  $b
2
```

```
PS>  $a = { 1 + 1}
PS>  $b = Invoke-Command $a
PS>  $b
2
```

호출 연산자에 대 한 자세한 내용은 [about_Operators](about_Operators.md)를 참조 하세요.

## <a name="using-delay-bind-script-blocks-with-parameters"></a>매개 변수가 포함 된 지연 바인딩 스크립트 블록 사용

파이프라인 입력 () 또는 ()를 허용 하는 형식화 된 매개 변수는 `by Value` `by PropertyName` 매개 변수에 대해 **지연 바인딩** 스크립트 블록을 사용할 수 있도록 합니다.
**지연 바인딩** 스크립트 블록 내에서 파이프라인 변수를 사용 하 여 파이프에서 파이프 된를 참조할 수 있습니다 `$_` .

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

더 복잡 한 cmdlet에서는 지연 바인딩 스크립트 블록을 사용 하 여 개체에서 파이프 된를 다시 사용 하 여 다른 매개 변수를 채울 수 있습니다.

**지연-** 스크립트 블록을 매개 변수로 바인딩하는 방법에 대 한 참고 사항:

- **지연 바인드** 스크립트 블록에서 사용 하는 매개 변수 이름을 명시적으로 지정 해야 합니다.
- 매개 변수는 형식화 되지 않아야 하 고 매개 변수의 형식은 또는 일 수 `[scriptblock]` 없습니다 `[object]` .
- 파이프라인 입력을 제공 하지 않고 **지연 바인드** 스크립트 블록을 사용 하는 경우 오류가 표시 됩니다.

  ```powershell
  Rename-Item -NewName {$_.Name + ".old"}
  ```

  ```Output
  Rename-Item : Cannot evaluate parameter 'NewName' because its argument is
  specified as a script block and there is no input. A script block cannot
  be evaluated without input.
  At line:1 char:23
  +  Rename-Item -NewName {$_.Name + ".old"}
  +                       ~~~~~~~~~~~~~~~~~~
      + CategoryInfo          : MetadataError: (:) [Rename-Item],
        ParameterBindingException
      + FullyQualifiedErrorId : ScriptBlockArgumentNoInput,
        Microsoft.PowerShell.Commands.RenameItemCommand
  ```

## <a name="see-also"></a>참고 항목

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Operators](about_Operators.md)

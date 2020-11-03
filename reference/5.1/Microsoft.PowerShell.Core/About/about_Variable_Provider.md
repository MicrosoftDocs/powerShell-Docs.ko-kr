---
description: 변수
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 변수 공급자
ms.openlocfilehash: ff3d457e8d057329544cf1265720fc041a804973
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223225"
---
# <a name="variable-provider"></a>변수 공급자

## <a name="provider-name"></a>공급자 이름

변수

## <a name="drives"></a>드라이브

`Variable:`

## <a name="capabilities"></a>기능

**ShouldProcess**

## <a name="short-description"></a>간단한 설명

PowerShell 변수 및 해당 값에 대 한 액세스를 제공 합니다.

## <a name="detailed-description"></a>자세한 설명

PowerShell **변수** 공급자를 통해 현재 콘솔에서 powershell 변수를 가져오고 추가, 변경 및 삭제할 수 있습니다.

PowerShell **변수** 공급자는 자동 변수, 기본 설정 변수 및 사용자가 만드는 변수를 포함 하 여 powershell이 만드는 변수를 지원 합니다.

**변수** 드라이브는 변수 개체만 포함 하는 플랫 네임 스페이스입니다. 변수에는 하위 항목이 없습니다.

**변수** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

또한 PowerShell에는 변수를 보고 변경할 수 있도록 특별히 설계 된 cmdlet 집합이 포함 되어 있습니다. **변수** cmdlet을 사용 하는 경우 이름에 드라이브를 지정할 필요가 없습니다 `Variable:` . 이 문서에서는 **변수** cmdlet 작업에 대해 다루지 않습니다.

- [Get-Variable](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [New-Variable](xref:Microsoft.PowerShell.Utility.New-Variable)
- [Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> Cmdlet을 사용 하지 않고 PowerShell 식 파서를 사용 하 여 변수 값을 만들고 확인 하 고 변경할 수도 있습니다. 변수를 직접 사용 하는 경우 달러 기호 ()를 사용 `$` 하 여 이름을 변수로 식별 하 고 대입 연산자 ()를 사용 하 여 `=` 해당 값을 설정 하 고 변경할 수 있습니다. 예를 들어 `$p = Get-Process` 은 변수를 만들고 `p` 명령의 결과를 저장 `Get-Process` 합니다.

## <a name="types-exposed-by-this-provider"></a>이 공급자가 노출 하는 형식

변수는 여러 가지 형식 중 하나일 수 있습니다. 대부분의 변수는 클래스의 인스턴스입니다 `PSVariable` . 다른 변수 및 해당 형식은 아래에 나열 되어 있습니다.

- `?`변수는 클래스의 인스턴스입니다 `QuestionMarkVariable` .
- `null`변수는 클래스의 인스턴스입니다 `NullVariable` .
- 최대 개수 변수는 클래스의 인스턴스입니다 `SessionStateCapacityVariable` .
- `LocalVariable` 인스턴스에는 다음과 같은 현재 실행에 대 한 정보가 포함 됩니다.
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a>변수 드라이브 탐색

**변수** 공급자는 드라이브에 해당 데이터 저장소를 노출 합니다 `Variable:` . 변수를 사용 하려면 위치를 `Variable:` drive ()로 변경 `Set-Location Variable:` 하거나 다른 PowerShell 드라이브에서 작업할 수 있습니다. 다른 위치에서 변수를 참조 하려면 경로에 드라이브 이름 ()을 사용 `Variable:` 합니다.

```powershell
Set-Location Variable:
```

파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다. 예를 들어 다음과 같이 입력합니다.

```powershell
Set-Location C:
```

다른 PowerShell 드라이브에서 **변수** 공급자를 사용할 수도 있습니다. 다른 위치에서 변수를 참조 하려면 경로에 드라이브 이름을 사용 `Variable:` 합니다.

> [!NOTE]
> PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다. `dir`및 등의 명령은 `ls` 이제 [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭입니다 `cd` .는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭입니다. 및 `pwd` 은 [(는) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.

## <a name="displaying-the-value-of-variables"></a>변수의 값 표시

### <a name="get-all-variables-in-the-current-session"></a>현재 세션의 모든 변수 가져오기

이 명령은 현재 세션의 모든 변수 및 변수 값 목록을 가져옵니다. 모든 PowerShell 드라이브에서이 명령을 사용할 수 있습니다.

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a>공급자 경로를 사용 하 여 변수 가져오기

이 명령은 달러 기호 ()로 시작 하는 공급자 경로를 사용 하 여 변수 값을 검색 `$` 합니다. 이는 변수 이름 앞에 달러 기호 ()를 접두사로 사용 하는 것과 동일한 효과를 가집니다 `$` .

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a>와일드 카드를 사용 하 여 변수 가져오기

이 명령은 이름이 "max"로 시작하는 변수를 가져옵니다. 모든 PowerShell 드라이브에서이 명령을 사용할 수 있습니다.

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a>의 값을 가져옵니다. 변수

이 명령은 `-LiteralPath` [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 의 매개 변수를 사용 하 여 `?` 드라이브 내에서 변수 값을 가져옵니다 `Variable:` . 는 `?` 경로에서 와일드 카드 이지만 `Get-ChildItem` 매개 변수 값에서 와일드 카드를 확인 하려고 시도 하지 않습니다 `-LiteralPath` .

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a>ReadOnly 및 상수 변수 가져오기

이 명령은 Options 속성 값이 또는 인 변수를 `ReadOnly` 가져옵니다 `Constant` . **Options**

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a>변수 만들기

### <a name="create-a-new-variable"></a>새 변수 만들기

이 명령은 변수를 만들고 `services` 명령 결과를 저장 `Get-Service` 합니다. 현재 위치가 드라이브에 있기 때문에 `Variable:` `-Path` 매개 변수 값은 `.` 현재 위치를 나타내는 점 ()입니다.

명령을 둘러싼 괄호는 `Get-Service` 변수가 만들어지기 전에 명령이 실행 되는지 확인 합니다. 괄호가 없으면 새 변수 값이 "Get-Service" 문자열이 됩니다.

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a>절대 경로를 사용 하 여 변수 만들기

이 명령은 변수를 만들고 `services` 명령 결과를 저장 `Get-Service` 합니다.

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 값 없는 변수를 만들려면 대입 연산자를 생략합니다.

## <a name="changing-variables"></a>변수 변경

### <a name="rename-a-variable"></a>변수 이름 바꾸기

이 명령은 cmdlet을 사용 하 여 `Rename-Item` 변수 이름을로 변경 `a` `processes` 합니다.

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a>변수 값 변경

이 명령은 cmdlet을 사용 하 여 `Set-Item` 변수 값을 `ErrorActionPreference` "Stop"으로 변경 합니다.

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a>변수 복사

이 명령은 cmdlet을 사용 하 여 `Copy-Item` `processes` 변수를로 복사 `old_processes` 합니다. 그러면 변수와 동일한 값을 가진 라는 새 변수가 만들어집니다 `old_processes` `processes` .

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a>변수 삭제

이 명령은 `serv` 현재 세션에서 변수를 삭제 합니다. PowerShell 드라이브에서이 명령을 사용할 수 있습니다.

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a>-Force 매개 변수를 사용 하 여 변수 삭제

이 명령은 **Options** 속성 값이 인 변수를 제외 하 고 현재 세션에서 모든 변수를 삭제 `Constant` 합니다. `-Force`매개 변수가 없으면 **Options** 속성의 값이 인 변수는 삭제 되지 않습니다 `ReadOnly` .

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a>변수 값을 NULL로 설정

이 명령은 cmdlet을 사용 하 여 `Clear-Item` 변수 값을 `processes` NULL로 변경 합니다.

```powershell
Clear-Item -Path Variable:processes
```

## <a name="using-the-pipeline"></a>파이프라인 사용

공급자 cmdlet은 파이프라인 입력을 허용 합니다. 파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.
공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.

## <a name="getting-help"></a>도움말 보기

Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.

파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 의 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a>참고 항목

[about_Variables](../About/about_Variables.md)

[about_Automatic_Variables](../About/about_Automatic_Variables.md)

[about_Providers](../About/about_Providers.md)

---
description: 원격 명령에서 로컬 및 원격 변수를 사용하는 방법을 설명합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Variables
ms.openlocfilehash: 8546e7860dd6d9770328c2d749de1ba433413fdf
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222601"
---
# <a name="about-remote-variables"></a>원격 변수 정보

## <a name="short-description"></a>간단한 설명

원격 명령에서 로컬 및 원격 변수를 사용하는 방법을 설명합니다.

## <a name="long-description"></a>자세한 설명입니다.

원격 컴퓨터에서 실행 하는 명령에서 변수를 사용할 수 있습니다. 변수에 값을 할당 한 다음 값 대신 변수를 사용 합니다.

기본적으로 원격 명령의 변수는 명령을 실행 하는 세션에서 정의 된 것으로 간주 됩니다. 로컬 세션에 정의 된 변수는 명령에서 지역 변수로 식별 되어야 합니다.

## <a name="using-remote-variables"></a>원격 변수 사용

PowerShell에서는 명령이 실행 되는 세션에서 원격 명령에 사용 된 변수가 정의 되어 있다고 가정 합니다.

이 예제에서 변수는 `$ps` 명령이 실행 되는 임시 세션에서 정의 됩니다 `Get-WinEvent` .

```powershell
Invoke-Command -ComputerName S1 -ScriptBlock {
  $ps = "*PowerShell*"; Get-WinEvent -LogName $ps
}
```

명령이 영구 세션 **PSSession** 에서 실행 되는 경우 해당 세션에서 원격 변수를 정의 해야 합니다.

```powershell
$s = New-PSSession -ComputerName S1
Invoke-Command -Session $s -ScriptBlock {$ps = "*PowerShell*"}
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $ps}
```

## <a name="using-local-variables"></a>지역 변수 사용

원격 명령의 지역 변수를 사용할 수 있지만 변수는 로컬 세션에서 정의 해야 합니다.

PowerShell 3.0부터 범위 한정자를 사용 하 여 `Using` 원격 명령에서 지역 변수를 식별할 수 있습니다.

의 구문은 다음과 같습니다 `Using` .

```
$Using:<VariableName>
```

다음 예에서는 `$ps` 변수가 로컬 세션에서 만들어지지만 명령이 실행 되는 세션에 사용 됩니다. `Using`범위 한정자는를 `$ps` 지역 변수로 식별 합니다.

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  Get-WinEvent -LogName $Using:ps
}
```

`Using`범위 한정자는 **PSSession** 에서 사용할 수 있습니다.

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $Using:ps}
```

와 같은 변수 참조는 `$using:var` 호출자의 컨텍스트에서 변수 값으로 확장 `$var` 됩니다. 호출자의 변수 개체에 대 한 액세스 권한을 얻을 수 없습니다.
`Using`범위 한정자는 **PSSession** 내에서 지역 변수를 수정 하는 데 사용할 수 없습니다. 예를 들어 다음 코드는 작동 하지 않습니다.

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {$Using:ps = 'Cannot assign new value'}
```

에 대 한 자세한 내용은 `Using` 을 참조 하십시오 [about_Scopes](./about_Scopes.md)

### <a name="using-splatting"></a>스 플랫 사용

PowerShell 스 플랫는 매개 변수 이름 및 값의 컬렉션을 명령에 전달 합니다. 자세한 내용은 [about_Splatting](about_Splatting.md)를 참조 하세요.

이 예에서 스 플랫 변수는 `$Splat` 로컬 컴퓨터에 설정 된 해시 테이블입니다. 는 `Invoke-Command` 원격 컴퓨터 세션에 연결 합니다. **ScriptBlock** 은 `Using` Scope 한정자와 At () 기호를 사용 하 여 `@` splatted 변수를 나타냅니다.

```powershell
$Splat = @{ Name = "Win*"; Include = "WinRM" }
Invoke-Command -Session $s -ScriptBlock { Get-Service @Using:Splat }
```

### <a name="other-situations-where-the-using-scope-modifier-is-needed"></a>' Using ' 범위 한정자가 필요한 다른 상황

세션에서 실행 되지 않는 스크립트나 명령의 경우 범위 한정자를 사용 하 여 `Using` 호출 세션 범위의 변수 값을 포함 해야 합니다. 이렇게 하면 세션 외부 코드에서 해당 값에 액세스할 수 있습니다. `Using`범위 한정자는 다음 컨텍스트에서 지원 됩니다.

- 원격으로 실행 되는 명령, `Invoke-Command` **ComputerName** 또는 **Session** 매개 변수를 사용 하 여 시작 (원격 세션)
- 백그라운드 작업, 시작 `Start-Job` (out-of-process 세션)
- 를 통해 시작 되는 스레드 작업 `Start-ThreadJob` (별도 스레드 세션)

컨텍스트에 따라 포함 된 변수 값은 호출자의 범위에 있는 데이터의 독립적인 복사본 이거나이에 대 한 참조입니다. 원격 및 out-of-process 세션에서 항상 독립적인 복사본입니다. 스레드 세션에서는 참조로 전달 됩니다.

## <a name="serialization-of-variable-values"></a>변수 값의 Serialization

원격으로 실행 되는 명령 및 백그라운드 작업은 out-of-process로 실행 됩니다.
Out-of-process 세션은 XML 기반 serialization 및 deserialization을 사용 하 여 프로세스 경계를 넘어 변수 값을 사용할 수 있도록 합니다. Serialization 프로세스는 개체를 원래 개체 속성이 있지만 메서드는 포함 하지 않는 **PSObject** 로 변환 합니다.

제한 된 형식 집합의 경우 deserialization 리하이드레이션 할 개체를 원래 형식으로 다시 설정 합니다. 원래 개체 인스턴스의 복사본입니다.
형식 속성 및 메서드를 포함 합니다. **System.object** 와 같은 단순 형식의 경우 복사본은 정확 합니다. 복합 형식의 경우 복사본은 아직까지 완벽입니다. 예를 들어, 공개 된 인증서 개체에는 개인 키가 포함 되지 않습니다.

다른 모든 형식의 인스턴스는 **PSObject** 인스턴스입니다. **PSTypeNames** 속성에는 **deserialize** (예:Deserialized.System) 접두사가 붙은 원래 형식 이름이 포함 **됩니다. 데이터 DataTable**

## <a name="using-local-variables-with-argumentlist-parameter"></a>**Argumentlist** 매개 변수를 사용 하 여 지역 변수 사용

원격 명령에 대 한 매개 변수를 정의 하 고 cmdlet의 **Argumentlist** 매개 변수를 사용 하 여 지역 변수를 `Invoke-Command` 매개 변수 값으로 지정 하 여 원격 명령에서 로컬 변수를 사용할 수 있습니다.

- 키워드를 사용 `param` 하 여 원격 명령에 대 한 매개 변수를 정의 합니다. 매개 변수 이름은 지역 변수의 이름과 일치 하지 않아도 되는 자리 표시자입니다.

- 명령에서 키워드로 정의 된 매개 변수를 사용 `param` 합니다.

- Cmdlet의 **Argumentlist** 매개 변수를 사용 `Invoke-Command` 하 여 지역 변수를 매개 변수 값으로 지정 합니다.

예를 들어 다음 명령은 `$ps` 로컬 세션에서 변수를 정의한 다음 원격 명령에 사용 합니다. `$log`이 명령은 매개 변수 이름과 지역 변수를 `$ps` 해당 값으로 사용 합니다.

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  param($log)
  Get-WinEvent -LogName $log
} -ArgumentList $ps
```

## <a name="see-also"></a>참고 항목

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[about_Splatting](about_Splatting.md)

[about_Variables](about_Variables.md)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Start-ThreadJob](/powershell/module/ThreadJob/Start-ThreadJob)

---
description: 모든 cmdlet에 사용할 수 있는 매개 변수에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CommonParameters
ms.openlocfilehash: 3c1a26754baf9bdfa2a9d6d3cf5a68ddb657c3bf
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222130"
---
# <a name="about-commonparameters"></a>CommonParameters 정보

## <a name="short-description"></a>간단한 설명

모든 cmdlet에 사용할 수 있는 매개 변수에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

일반 매개 변수는 cmdlet에서 사용할 수 있는 cmdlet 매개 변수 집합입니다. 이러한 cmdlet은 cmdlet 개발자가 아닌 PowerShell에서 구현 되며 cmdlet에서 자동으로 사용할 수 있습니다.

모든 cmdlet에는 일반 매개 변수를 사용할 수 있지만 모든 cmdlet에는 영향을 주지 않을 수 있습니다. 예를 들어 cmdlet이 자세한 정보 표시 출력을 생성 하지 않는 경우 **verbose** 일반 매개 변수를 사용 해도 아무런 효과가 없습니다.

Common 매개 변수는 **Cmdletbinding** 특성 또는 **Parameter** 특성을 사용 하는 고급 함수 에서도 사용할 수 있습니다.

여러 일반 매개 변수가 시스템 기본값 또는 PowerShell 기본 설정 변수를 사용 하 여 설정 하는 기본 설정을 재정의 합니다. 기본 설정 변수와 달리 일반 매개 변수는 해당 매개 변수가 사용 되는 명령에만 영향을 줍니다.

자세한 내용은 [about_Preference_Variables](./about_Preference_Variables.md)를 참조 하세요.

다음 목록에는 일반 매개 변수가 표시 됩니다. 해당 별칭은 괄호 안에 나열 됩니다.

- **Debug** (db)
- **Erroraction** (ea)
- **Errorvariable** (ev)
- **Informationaction** (infa)
- **Informationvariable** (iv)
- **OutVariable** (ov-es)
- **OutBuffer** (ob)
- **PipelineVariable** (pv)
- **자세한 정보** 표시 (vb)
- **WarningAction** (wa)
- **WarningVariable** (wv)

**동작** 매개 변수는 **actionpreference** 형식 값입니다.
**Actionpreference** 는 다음 값이 포함 된 열거형입니다.

| 속성             | 값 |
|------------------|-------|
| 일시 중지됨          | 5     |
| 무시           | 4     |
| 문의          | 3     |
| 계속         | 2     |
| 중지             | 1     |
| SilentlyContinue | 0     |

매개 변수를 사용 하 여 이름이 나 값을 사용할 수 있습니다.

일반 매개 변수 외에도 많은 cmdlet은 위험 완화 매개 변수를 제공 합니다. 시스템이 나 사용자 데이터에 대 한 위험을 포함 하는 cmdlet은 일반적으로 이러한 매개 변수를 제공 합니다.

위험 완화 매개 변수는 다음과 같습니다.

- **WhatIf** (wi)
- **확인** (cf)

### <a name="common-parameter-descriptions"></a>일반 매개 변수 설명

#### <a name="debug"></a>디버그

명령에 의해 수행 된 작업에 대 한 프로그래머 수준의 세부 정보를 표시 합니다. 이 매개 변수는 명령에서 디버깅 메시지를 생성 하는 경우에만 작동 합니다. 예를 들어이 매개 변수는 명령에 cmdlet이 포함 되어 있을 때 작동 `Write-Debug` 합니다.

```yaml
Type: SwitchParameter
Aliases: db

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

기본적으로 `$DebugPreference` 변수 값이 **SilentlyContinue** 이므로 디버깅 메시지가 표시 되지 않습니다.

대화형 모드에서 **Debug** 매개 변수는 `$DebugPreference` 현재 명령의 변수 값을 재정의 하 여의 값을 `$DebugPreference` **Inquire** 로 설정 합니다.

비 대화형 모드에서 **Debug** 매개 변수는 현재 명령의 변수 값을 재정의 `$DebugPreference` 하 고의 값을 `$DebugPreference` **계속** 로 설정 합니다.

`-Debug:$true` 와 동일한 효과가 `-Debug` 있습니다. `-Debug:$false`SilentlyContinue가 아닌 경우 (기본값) 디버깅 메시지를 표시 하지 않으려면를 사용 합니다 `$DebugPreference` . **SilentlyContinue**

#### <a name="erroraction"></a>ErrorAction

Cmdlet이 명령에서 종료 되지 않는 오류에 응답 하는 방법을 결정 합니다.
이 매개 변수는 cmdlet의 경우와 같이 명령이 종료 되지 않는 오류를 생성 하는 경우에만 작동 합니다 `Write-Error` .

```yaml
Type: ActionPreference
Aliases: ea
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

**Erroraction** 매개 변수는 `$ErrorActionPreference` 현재 명령에 대 한 변수 값을 재정의 합니다. 변수의 기본값은 `$ErrorActionPreference` **계속** 되므로 **erroraction** 매개 변수를 사용 하지 않으면 오류 메시지가 표시 되 고 실행이 계속 됩니다.

**Erroraction** 매개 변수는 명령이 성공적으로 완료 되지 않도록 하는 종료 오류 (예: 누락 된 데이터, 유효 하지 않은 매개 변수 또는 권한 부족)에 영향을 주지 않습니다.

`-ErrorAction:Continue` 오류 메시지를 표시 하 고 명령을 계속 실행 합니다. 기본값은 `Continue`입니다.

`-ErrorAction:Ignore` 오류 메시지를 표시 하지 않고 명령을 계속 실행 합니다. **SilentlyContinue** 와 달리 **Ignore** 는 자동 변수에 오류 메시지를 추가 하지 않습니다 `$Error` . **Ignore** 값은 PowerShell 3.0에서 도입 되었습니다.

`-ErrorAction:Inquire` 오류 메시지를 표시 하 고 실행을 계속 하기 전에 확인 메시지를 표시 합니다. 이 값은 거의 사용 되지 않습니다.

`-ErrorAction:SilentlyContinue` 오류 메시지를 표시 하지 않고 명령을 계속 실행 합니다.

`-ErrorAction:Stop` 오류 메시지를 표시 하 고 명령 실행을 중지 합니다.

`-ErrorAction:Suspend` 는 PowerShell 6 이상에서 지원 되지 않는 워크플로에 대해서만 사용할 수 있습니다.

> [!NOTE]
> **Erroraction** 매개 변수는를 재정의 하지만 `$ErrorAction` 매개 변수를 명령에서 사용 하 여 스크립트나 함수를 실행할 때 기본 설정 변수의 값을 대체 하지 않습니다.

#### <a name="errorvariable"></a>ErrorVariable

**Errorvariable** 은 명령에 대 한 오류 메시지를 지정 된 변수와 `$Error` 자동 변수에 저장 합니다. 자세한 내용은 [about_Automatic_Variables](about_Automatic_Variables.md) 를 참조 하세요.

```yaml
Type: String
Aliases: ev

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

기본적으로 새 오류 메시지는 변수에 이미 저장 된 오류 메시지를 덮어씁니다. 변수 내용에 오류 메시지를 추가 하려면 변수 이름 앞에 더하기 기호 ( `+` )를 입력 합니다.

예를 들어 다음 명령은 변수를 만든 `$a` 다음 오류를 저장 합니다.

```powershell
Get-Process -Id 6 -ErrorVariable a
```

다음 명령은 모든 오류 메시지를 변수에 추가 합니다 `$a` .

```powershell
Get-Process -Id 2 -ErrorVariable +a
```

다음 명령은의 내용을 표시 합니다 `$a` .

```powershell
$a
```

이 매개 변수를 사용 하 여 특정 명령의 오류 메시지만 포함 하는 변수를 만들 수 있으며 자동 변수의 동작에는 영향을 주지 않습니다 `$Error` . `$Error`자동 변수에는 세션의 모든 명령에 포함 된 오류 메시지가 포함 됩니다. 또는와 같은 배열 표기법을 사용 `$a[0]` 하 여 `$error[1,2]` 변수에 저장 된 특정 오류를 참조할 수 있습니다.

> [!NOTE]
> 사용자 지정 오류 변수에는 중첩 된 함수 또는 스크립트에 대 한 호출의 오류를 포함 하 여 명령에 의해 생성 된 모든 오류가 포함 됩니다.

#### <a name="informationaction"></a>InformationAction

PowerShell 5.0에서 도입 되었습니다. 사용 되는 명령 또는 스크립트 내에서 **Informationaction** 일반 매개 변수는 `$InformationPreference` 기본적으로 **SilentlyContinue** 로 설정 되는 기본 설정 변수의 값을 재정의 합니다. `Write-Information` **Informationaction** 이 포함 된 스크립트에서를 사용 하는 경우 `Write-Information` **informationaction** 매개 변수의 값에 따라 값이 표시 됩니다. 에 대 한 자세한 내용은 `$InformationPreference` [about_Preference_Variables](./about_Preference_Variables.md)를 참조 하세요.

```yaml
Type: ActionPreference
Aliases: ia
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

`-InformationAction:Stop` 명령이 발생 한 경우 명령이 나 스크립트를 중지 `Write-Information` 합니다.

`-InformationAction:Ignore` 정보 메시지를 표시 하지 않고 명령을 계속 실행 합니다. **SilentlyContinue** 와 달리 **무시** 는 정보 메시지를 완전히 무시 합니다. 정보 스트림에 정보 메시지를 추가 하지 않습니다.

`-InformationAction:Inquire` 명령에 지정한 정보 메시지를 표시 `Write-Information` 한 다음 계속할지 여부를 묻는 메시지를 표시 합니다.

`-InformationAction:Continue` 정보 메시지를 표시 하 고 계속 실행 합니다.

`-InformationAction:Suspend` 는 워크플로에서만 사용할 수 있으므로 PowerShell Core에서 지원 되지 않습니다.

`-InformationAction:SilentlyContinue` 정보 메시지 (기본값)는 표시 되지 않으며 스크립트는 중단 없이 계속 됩니다.

> [!NOTE]
> **Informationaction** 매개 변수는를 재정의 하지만 `$InformationAction` 매개 변수를 명령에서 사용 하 여 스크립트나 함수를 실행할 때 기본 설정 변수의 값을 대체 하지는 않습니다.

#### <a name="informationvariable"></a>InformationVariable

PowerShell 5.0에서 도입 되었습니다. 사용 되는 명령 또는 스크립트 내에서 **informationvariable** 일반 매개 변수는 명령을 추가 하 여 지정한 문자열을 변수에 저장 합니다 `Write-Information` . `Write-Information` 값은 **Informationaction** 일반 매개 변수의 값에 따라 표시 됩니다. **Informationaction** 일반 매개 변수를 추가 하지 않으면 `Write-Information` 기본 설정 변수의 값에 따라 문자열이 표시 됩니다 `$InformationPreference` . 에 대 한 자세한 내용은 `$InformationPreference` [about_Preference_Variables](./about_Preference_Variables.md)를 참조 하세요.

> [!NOTE]
> 정보 변수에는 중첩 된 함수 또는 스크립트에 대 한 호출의 정보 메시지를 포함 하 여 명령에 의해 생성 된 모든 정보 메시지가 포함 됩니다.

```yaml
Type: String
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

#### <a name="outbuffer"></a>OutBuffer

파이프라인을 통해 개체가 전송 되기 전에 버퍼에 누적 되는 개체 수를 결정 합니다. 이 매개 변수를 생략 하면 개체가 생성 될 때 전송 됩니다.

```yaml
Type: Int32
Aliases: ob

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

이 리소스 관리 매개 변수는 고급 사용자를 위해 설계 되었습니다. 이 매개 변수를 사용 하는 경우 PowerShell은의 일괄 처리로 데이터를 다음 cmdlet으로 보냅니다 `OutBuffer + 1` .

다음 예에서는 cmdlet을 사용 하 `ForEach-Object` 는 프로세스 블록 사이에를 표시 합니다 `Write-Host` . 표시는 2 또는의 일괄 처리로 대체 `OutBuffer + 1` 됩니다.

```powershell
1..4 | ForEach-Object {
        Write-Host "$($_): First"; $_
      } -OutBuffer 1 | ForEach-Object {
                        Write-Host "$($_): Second" }
```

```Output
1: First
2: First
1: Second
2: Second
3: First
4: First
3: Second
4: Second
```

#### <a name="outvariable"></a>OutVariable

파이프라인을 따라 출력을 전송 하는 것 외에도 지정 된 변수에 명령의 출력 개체를 저장 합니다.

```yaml
Type: String
Aliases: ov

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

출력을 변수에 추가 하려면 이미 저장 되어 있을 수 있는 출력을 바꾸지 않고 변수 이름 앞에 더하기 기호 ()를 입력 `+` 합니다.

예를 들어 다음 명령은 변수를 만들고 `$out` 여기에 프로세스 개체를 저장 합니다.

```powershell
Get-Process PowerShell -OutVariable out
```

다음 명령은 변수에 process 개체를 추가 합니다 `$out` .

```powershell
Get-Process iexplore -OutVariable +out
```

다음 명령은 변수의 내용을 표시 합니다 `$out` .

```powershell
$out
```

> [!NOTE]
> **OutVariable** 매개 변수에서 만든 변수는 `[System.Collections.ArrayList]` 입니다.

#### <a name="pipelinevariable"></a>PipelineVariable

**PipelineVariable** 은 파이프라인을 통해 흐르는 모든 명명 된 명령에 대해 현재 파이프라인 요소의 값을 변수로 저장 합니다.

```yaml
Type: String
Aliases: pv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

유효한 값은 모든 변수 이름과 동일한 문자열입니다.

다음은 **PipelineVariable** 의 작동 방식에 대 한 예입니다. 이 예에서는 명령에 명령 결과를 저장 하는 **PipelineVariable** 매개 변수가 명령에 추가 됩니다 `Foreach-Object` . 숫자 범위 (1 ~ 10)는 첫 번째 명령으로 파이프 되며, `Foreach-Object` 결과는 **Left** 라는 변수에 저장 됩니다.

첫 번째 명령의 결과는 `Foreach-Object` 첫 번째 명령 `Foreach-Object` 에서 반환 된 개체를 필터링 하는 두 번째 명령으로 파이프 됩니다 `Foreach-Object` . 두 번째 명령의 결과는 **Right** 라는 변수에 저장 됩니다.

세 번째 `Foreach-Object` 명령에서 `Foreach-Object` **왼쪽** 및 **오른쪽** 변수로 표시 되는 처음 두 개의 파이프 된 명령의 결과는 곱하기 연산자를 사용 하 여 처리 됩니다. 이 명령은 **왼쪽** 변수와 **오른쪽** 변수에 저장 된 개체에 곱할 수 있도록 지시 하 고 결과를 "왼쪽 범위 멤버 * 오른쪽 범위 member = product"로 표시 하도록 지정 합니다.

```powershell
1..10 | Foreach-Object -PipelineVariable Left -Process { $_ } |
  Foreach-Object -PV Right -Process { 1..10 } |
  Foreach-Object -Process { "$Left * $Right = " + ($Left*$Right) }
```

```output
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
1 * 4 = 4
1 * 5 = 5
...
```

#### <a name="verbose"></a>자세히

명령에서 수행한 작업에 대 한 자세한 정보를 표시 합니다. 이 정보는 추적 또는 트랜잭션 로그의 정보와 유사 합니다. 이 매개 변수는 명령이 자세한 정보 메시지를 생성 하는 경우에만 작동 합니다. 예를 들어이 매개 변수는 명령에 cmdlet이 포함 되어 있을 때 작동 `Write-Verbose` 합니다.

```yaml
Type: SwitchParameter
Aliases: vb

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

**Verbose** 매개 변수는 `$VerbosePreference` 현재 명령에 대 한 변수 값을 재정의 합니다. 변수의 기본값은 `$VerbosePreference` **SilentlyContinue** 이므로 자세한 정보 표시 메시지는 기본적으로 표시 되지 않습니다.

`-Verbose:$true` 는와 동일한 효과가 있습니다. `-Verbose`

`-Verbose:$false` 자세한 정보 표시 메시지를 표시 하지 않습니다. 의 값이 `$VerbosePreference` **SilentlyContinue** (기본값)가 아닌 경우이 매개 변수를 사용 합니다.

#### <a name="warningaction"></a>WarningAction

Cmdlet이 명령의 경고에 응답 하는 방법을 결정 합니다. 기본값은 **Continue** 입니다. 이 매개 변수는 명령에서 경고 메시지를 생성 하는 경우에만 작동 합니다. 예를 들어이 매개 변수는 명령에 cmdlet이 포함 되어 있을 때 작동 `Write-Warning` 합니다.

```yaml
Type: ActionPreference
Aliases: wa
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

**WarningAction** 매개 변수는 `$WarningPreference` 현재 명령에 대 한 변수 값을 재정의 합니다. 변수의 기본값은 `$WarningPreference` **Continue** 이므로 **WarningAction** 매개 변수를 사용 하지 않으면 경고가 표시 되 고 실행이 계속 됩니다.

`-WarningAction:Continue` 경고 메시지를 표시 하 고 명령을 계속 실행 합니다. 기본값은 `Continue`입니다.

`-WarningAction:Inquire` 경고 메시지를 표시 하 고 실행을 계속 하기 전에 확인 메시지를 표시 합니다. 이 값은 거의 사용 되지 않습니다.

`-WarningAction:SilentlyContinue` 경고 메시지를 표시 하지 않고 명령을 계속 실행 합니다.

`-WarningAction:Stop` 경고 메시지를 표시 하 고 명령 실행을 중지 합니다.

> [!NOTE]
> **WarningAction** 매개 변수는를 재정의 하지만 `$WarningAction` 명령이 스크립트나 함수를 실행 하는 명령에 사용 되는 경우 기본 설정 변수의 값을 대체 하지 않습니다.

#### <a name="warningvariable"></a>WarningVariable

지정 된 변수에서 명령에 대 한 경고를 저장 합니다.

```yaml
Type: String
Aliases: wv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

생성 된 모든 경고는 사용자에 게 경고가 표시 되지 않는 경우에도 변수에 저장 됩니다.

변수에 이미 저장 되어 있을 수 있는 경고를 대체 하는 대신 변수 내용에 경고를 추가 하려면 변수 이름 앞에 더하기 기호 ()를 입력 `+` 합니다.

예를 들어 다음 명령은 변수를 만든 `$a` 다음 경고를 저장 합니다.

```powershell
Get-Process -Id 6 -WarningVariable a
```

다음 명령은 경고를 변수에 추가 합니다 `$a` .

```powershell
Get-Process -Id 2 -WarningVariable +a
```

다음 명령은의 내용을 표시 합니다 `$a` .

```powershell
$a
```

이 매개 변수를 사용 하 여 특정 명령의 경고만 포함 하는 변수를 만들 수 있습니다. 또는와 같은 배열 표기법을 사용 `$a[0]` 하 여 `$warning[1,2]` 변수에 저장 된 특정 경고를 참조할 수 있습니다.

> [!NOTE]
> 경고 변수에는 중첩 된 함수 또는 스크립트에 대 한 호출의 경고를 포함 하 여 명령에 의해 생성 된 모든 경고가 포함 됩니다.

### <a name="risk-management-parameter-descriptions"></a>위험 관리 매개 변수 설명

#### <a name="whatif"></a>WhatIf

명령을 실행 하는 대신 명령의 효과를 설명 하는 메시지를 표시 합니다.

```yaml
Type: SwitchParameter
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

**WhatIf** 매개 변수는 `$WhatIfPreference` 현재 명령에 대 한 변수 값을 재정의 합니다. 변수의 기본값은 `$WhatIfPreference` 0 (사용 안 함) **이므로 Whatif** 동작은 **whatif** 매개 변수 없이 수행 되지 않습니다. 자세한 내용은 [about_Preference_Variables](about_Preference_Variables.md) 를 참조 하세요.

`-WhatIf:$true` 와 동일한 효과가 `-WhatIf` 있습니다.

`-WhatIf:$false` 변수의 값이 1 인 경우 발생 하는 자동 WhatIf 동작을 표시 하지 않습니다 `$WhatIfPreference` .

예를 들어 다음 명령은 `-WhatIf` 명령에 매개 변수를 사용 합니다 `Remove-Item` .

```powershell
Remove-Item Date.csv -WhatIf
```

항목을 제거 하는 대신 PowerShell에서 수행 하는 작업과 영향을 받는 항목을 나열 합니다. 이 명령은 다음과 같은 출력을 생성 합니다.

```output
What if: Performing operation "Remove File" on
Target "C:\ps-test\date.csv".
```

#### <a name="confirm"></a>확인

명령을 실행하기 전 확인 메시지를 표시합니다.

```yaml
Type: SwitchParameter
Aliases: cf

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

**Confirm** 매개 변수는 `$ConfirmPreference` 현재 명령에 대 한 변수 값을 재정의 합니다. 기본값은 true입니다. 자세한 내용은 [about_Preference_Variables](about_Preference_Variables.md) 를 참조 하세요.

`-Confirm:$true` 와 동일한 효과가 `-Confirm` 있습니다.

`-Confirm:$false` 의 값 `$ConfirmPreference` 이 cmdlet의 예상 위험 보다 작거나 같을 때 발생 하는 자동 확인을 표시 하지 않습니다.

예를 들어 다음 명령은 명령에 **Confirm** 매개 변수를 사용 합니다 `Remove-Item` . 항목을 제거 하기 전에 PowerShell에서 수행 하는 작업과 영향을 받는 항목을 나열 하 고 승인을 요청 합니다.

```
PS C:\ps-test> Remove-Item tmp*.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target " C:\ps-test\tmp1.txt
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

확인 응답 옵션은 다음과 같습니다.

|응답       |결과                                                     |
|---------------|-----------------------------------------------------------|
|예 (Y)        |작업을 수행 합니다.                                        |
|모두 예 (A) |모든 작업을 수행 하 고 후속 확인 쿼리를 표시 하지 않습니다.|
|               |이 명령에 대 한입니다.                                          |
|아니요 (N):        |작업을 수행 하지 마십시오.                                 |
|모두 아니요 (L): |작업을 수행 하지 않고 후속 확인을 표시 하지 않습니다. |
|               |이 명령에 대 한 쿼리입니다.                                  |
|일시 중단:   |명령을 일시 중지 하 고 임시 세션을 만듭니다.          |
|도움말 (?)       |이러한 옵션에 대 한 도움말을 표시 합니다.                            |

**일시 중단** 옵션은 명령을 보류 중으로 설정 하 고 **확인** 옵션을 선택할 준비가 될 때까지 작업을 수행할 수 있는 임시 중첩 세션을 만듭니다. 중첩 된 세션에 대 한 명령 프롬프트에는 원래의 부모 명령의 자식 작업 임을 나타내는 두 개의 추가 캐럿 (>>)가 있습니다. 중첩 된 세션에서 명령 및 스크립트를 실행할 수 있습니다. 중첩 된 세션을 종료 하 고 원래 명령의 확인 옵션으로 돌아가려면 "exit"를 입력 합니다.

다음 예에서는 사용자가 명령 매개 변수에 대 한 도움말을 확인 하는 동안 **일시 중단** 옵션을 사용 하 여 명령을 일시적으로 중지 합니다. 필요한 정보를 구한 후 "끝내기"를 입력 하 여 중첩 된 프롬프트를 종료 한 다음 확인 쿼리에 대 한 예 (y) 응답을 선택 합니다.

```
PS C:\ps-test> New-Item -ItemType File -Name Test.txt -Confirm

Confirm
Are you sure you want to perform this action?

Performing operation "Create File" on Target "Destination:
C:\ps-test\test.txt".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default
is "Y"): s

PS C:\ps-test> Get-Help New-Item -Parameter ItemType

-ItemType <string>
Specifies the provider-specified type of the new item.

Required?                    false
Position?                    named
Default value
Accept pipeline input?       true (ByPropertyName)
Accept wildcard characters?  false

PS C:\ps-test> exit

Confirm
Are you sure you want to perform this action?
Performing operation "Create File" on Target "Destination: C:\ps-test\test
.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (defau
lt is "Y"): y

Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         8/27/2010   2:41 PM          0 test.txt
```

## <a name="keywords"></a>어

about_Common_Parameters

## <a name="see-also"></a>참고 항목

[about_Preference_Variables](about_Preference_Variables.md)

[Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)

[Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning)

[쓰기 오류](xref:Microsoft.PowerShell.Utility.Write-Error)

[Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)


---
description: 특성을 지정 하는 함수가 `CmdletBinding` 컴파일된 cmdlet에 사용할 수 있는 메서드 및 속성을 사용할 수 있는 방법에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Methods
ms.openlocfilehash: 260dab1937715da34b9191ff2765dee7d2ac3ec5
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223498"
---
# <a name="about-functions-advanced-methods"></a>함수 고급 메서드 정보

## <a name="short-description"></a>간단한 설명

특성을 지정 하는 함수가 `CmdletBinding` 컴파일된 cmdlet에 사용할 수 있는 메서드 및 속성을 사용할 수 있는 방법에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

특성을 지정 하는 함수는 `CmdletBinding` 변수를 통해 여러 메서드와 속성에 액세스할 수 있습니다 `$PSCmdlet` . 이러한 메서드에는 다음과 같은 메서드가 포함 됩니다.

- 컴파일된 cmdlet이 작업을 수행 하는 데 사용 하는 입력 처리 방법입니다.
- `ShouldProcess`작업을 `ShouldContinue` 수행 하기 전에 사용자 의견을 가져오는 데 사용 되는 및 메서드.
- `ThrowTerminatingError`오류 레코드를 생성 하는 방법입니다.
- 여러 가지 `Write` 형식의 출력을 반환 하는 메서드

**PSCmdlet** 클래스의 모든 메서드 및 속성은 고급 함수에서 사용할 수 있습니다. 자세한 내용은 [PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)를 참조 하세요.

특성에 대 한 자세한 내용은 `CmdletBinding` [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)를 참조 하세요.
**Cmdletbindingattribute** 클래스의 경우에는 [system.object](/dotnet/api/system.management.automation.cmdletbindingattribute)를 참조 하십시오.

### <a name="input-processing-methods"></a>입력 처리 방법

이 섹션에서 설명 하는 메서드를 입력 처리 메서드 라고 합니다. 함수의 경우이 세 가지 메서드는 `Begin` `Process` 함수의, 및 블록으로 표현 됩니다 `End` . 함수에서 이러한 블록을 사용할 필요는 없습니다.

> [!NOTE]
> 이러한 블록은 특성을 사용 하지 않는 함수에도 사용할 수 있습니다 `CmdletBinding` .

#### <a name="begin"></a>시작

이 블록은 함수에 대 한 선택적 일회성 전처리를 제공 하는 데 사용 됩니다.
PowerShell 런타임은 파이프라인에서 함수의 각 인스턴스에 대해 한 번씩이 블록의 코드를 사용 합니다.

#### <a name="process"></a>프로세스

이 블록은 함수에 대 한 레코드 레코드 처리를 제공 하는 데 사용 됩니다. `Process`다른 블록을 정의 하지 않고 블록을 사용할 수 있습니다. `Process`블록 실행 수는 함수를 사용 하는 방법 및 함수가 수신 하는 입력에 따라 달라 집니다.

자동 변수 `$_` 이거나 `$PSItem` 블록에서 사용할 파이프라인의 현재 개체를 포함 합니다 `Process` . `$input`자동 변수에는 함수와 스크립트 블록에만 사용할 수 있는 열거자가 포함 되어 있습니다.
자세한 내용은 [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.

- 함수를 시작 부분 또는 파이프라인 외부에서 호출 하면 `Process` 블록을 한 번 실행 합니다.
- 파이프라인 내에서 블록은 `Process` 함수에 도달 하는 각 입력 개체에 대해 한 번씩 실행 됩니다.
- 함수에 도달 하는 파이프라인 입력이 비어 있으면 `Process` 블록이 실행 **되지 않습니다** .
  - `Begin`및 `End` 블록은 계속 실행 됩니다.

> [!IMPORTANT]
> 파이프라인 입력을 허용 하도록 함수 매개 변수를 설정 하 고 `Process` 블록이 정의 되지 않은 경우 레코드에의 한 레코드 처리가 실패 합니다. 이 경우 함수는 입력에 관계 없이 한 번만 실행 됩니다.

#### <a name="end"></a>끝

이 블록은 함수에 대 한 선택적인 일회성 사후 처리를 제공 하는 데 사용 됩니다.

다음 예에서는 일회성 `Begin` 전처리를 위한 블록, `Process` 다중 레코드 처리를 위한 블록 및 `End` 일회성 사후 처리를 위한 블록을 포함 하는 함수의 개요를 보여 줍니다.

```powershell
Function Test-ScriptCmdlet
{
[CmdletBinding(SupportsShouldProcess=$True)]
    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

> [!NOTE]
> 또는 블록 중 하나를 사용 `Begin` `End` 하려면 세 개의 블록을 모두 정의 해야 합니다. 세 블록을 모두 사용 하는 경우 모든 PowerShell 코드는 블록 중 하나에 있어야 합니다.

### <a name="confirmation-methods"></a>확인 방법

#### <a name="shouldprocess"></a>ShouldProcess

이 메서드는 함수에서 시스템을 변경 하는 작업을 수행 하기 전에 사용자의 확인을 요청 하기 위해 호출 됩니다. 함수는 메서드에서 반환 된 부울 값을 기반으로 계속할 수 있습니다. 이 메서드는 함수 블록 내 에서만 호출할 수 있습니다 `Process{}` . `CmdletBinding`또한 특성은 `ShouldProcess` 앞의 예제와 같이 함수에서 지원 되는를 선언 해야 합니다.

이 메서드에 대 한 자세한 내용은 [system.object](/dotnet/api/system.management.automation.cmdlet.shouldprocess)를 참조 하십시오.

확인을 요청 하는 방법에 대 한 자세한 내용은 [확인 요청](/powershell/scripting/developer/cmdlet/requesting-confirmation)을 참조 하세요.

#### <a name="shouldcontinue"></a>ShouldContinue

이 메서드는 두 번째 확인 메시지를 요청 하기 위해 호출 됩니다. 메서드가 반환 될 때 호출 되어야 합니다 `ShouldProcess` `$true` . 이 메서드에 대 한 자세한 내용은 [system.object](/dotnet/api/system.management.automation.cmdlet.shouldcontinue)를 참조 하십시오.

### <a name="error-methods"></a>오류 메서드

오류가 발생 하는 경우 함수는 두 가지 메서드를 호출할 수 있습니다. 종료 되지 않는 오류가 발생 하면 함수는 `WriteError` 메서드 섹션에서 설명 하는 메서드를 호출 해야 합니다 `Write` . 종료 오류가 발생 하 고 함수를 계속할 수 없는 경우 메서드를 호출 해야 합니다 `ThrowTerminatingError` . 종료 오류에 대 한 문을 사용 하 여 오류 `Throw` 를 종료 하 고 [오류를 기록할](xref:Microsoft.PowerShell.Utility.Write-Error) 수도 있습니다.

자세한 내용은 [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror)을 (를) 참조 하세요.

### <a name="write-methods"></a>Write 메서드

함수는 다음 메서드를 호출 하 여 다른 유형의 출력을 반환할 수 있습니다.
모든 출력이 파이프라인의 다음 명령으로 이동 하는 것은 아닙니다. 과 같은 다양 한 cmdlet을 사용할 수도 있습니다 `Write` `Write-Error` .

#### <a name="writecommanddetail"></a>WriteCommandDetail

메서드에 대 한 자세한 내용은 `WriteCommandDetails` [WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail)를 참조 하세요.

#### <a name="writedebug"></a>WriteDebug

함수 문제를 해결 하는 데 사용할 수 있는 정보를 제공 하려면 함수에서 메서드를 호출 하도록 합니다 `WriteDebug` . `WriteDebug`메서드는 디버그 메시지를 사용자에 게 표시 합니다. 자세한 내용은 System.web. n a m a [debug](/dotnet/api/system.management.automation.cmdlet.writedebug)를 참조 하십시오.

#### <a name="writeerror"></a>WriteError

종료 되지 않는 오류가 발생 하 고 함수가 레코드를 계속 처리 하도록 디자인 된 경우 함수는이 메서드를 호출 해야 합니다. 자세한 내용은 [WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror)을 (를) 참조 하세요.

> [!NOTE]
> 종료 오류가 발생 하는 경우 함수는 [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) 메서드를 호출 해야 합니다.

#### <a name="writeobject"></a>WriteObject

`WriteObject`메서드를 사용 하 여 함수는 파이프라인의 다음 명령으로 개체를 보낼 수 있습니다. 대부분의 경우 `WriteObject` 는 함수가 데이터를 반환할 때 사용 하는 메서드입니다. 자세한 내용은 [PSCmdlet. WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject)를 참조 하세요.

#### <a name="writeprogress"></a>WriteProgress

작업을 완료 하는 데 오랜 시간이 걸리는 함수에서이 메서드를 사용 하면 `WriteProgress` 진행률 정보가 표시 되도록 함수에서 메서드를 호출할 수 있습니다. 예를 들어 완료 된 비율을 표시할 수 있습니다.
자세한 내용은 [PSCmdlet 진행률](/dotnet/api/system.management.automation.cmdlet.writeprogress)을 참조 하세요.

#### <a name="writeverbose"></a>WriteVerbose

함수에서 수행 하는 작업에 대 한 자세한 정보를 제공 하려면 함수에서 메서드를 호출 하 여 `WriteVerbose` 사용자에 게 자세한 정보 메시지를 표시 하도록 합니다. 기본적으로 자세한 정보 표시 메시지는 표시 되지 않습니다. 자세한 내용은 [PSCmdlet](/dotnet/api/system.management.automation.cmdlet.writeverbose)을 (를) 참조 하세요.

#### <a name="writewarning"></a>WriteWarning

예기치 않은 결과를 발생 시킬 수 있는 조건에 대 한 정보를 제공 하기 위해 함수가 WriteWarning 메서드를 호출 하 여 사용자에 게 경고 메시지를 표시 하도록 합니다. 기본적으로 경고 메시지가 표시 됩니다. 자세한 내용은 [PSCmdlet 경고](/dotnet/api/system.management.automation.cmdlet.writewarning)를 참조 하세요.

> [!NOTE]
> `$WarningPreference` `Verbose` 및 명령줄 옵션을 사용 하 여 또는 변수를 구성 하 여 경고 메시지를 표시할 수도 있습니다 `Debug` . 변수에 대 한 자세한 내용은 `$WarningPreference` [about_Preference_Variables](about_Preference_Variables.md)를 참조 하세요.

### <a name="other-methods-and-properties"></a>기타 메서드 및 속성

변수를 통해 액세스할 수 있는 다른 메서드 및 속성에 대 한 자세한 내용은 `$PSCmdlet` [PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)를 참조 하세요.

예를 들어 [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) 속성을 사용 하 여 사용 중인 매개 변수 집합을 볼 수 있습니다. 매개 변수 집합을 사용 하면 함수를 실행할 때 지정 된 매개 변수를 기반으로 다양 한 작업을 수행 하는 함수를 만들 수 있습니다.

## <a name="see-also"></a>참고 항목

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Preference_Variables](about_Preference_Variables.md)

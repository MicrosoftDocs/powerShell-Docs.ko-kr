---
description: PowerShell의 실험적 기능 지원에서는 PowerShell 또는 PowerShell 모듈에서 기존의 안정적인 기능과 함께 실험적 기능을 사용할 수 있는 메커니즘을 제공합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 실험적 기능 정보
ms.openlocfilehash: e53af155c2a8691e2e4d4cc6f47bfd5932801db9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223865"
---
# <a name="experimental-features"></a>실험적 기능

PowerShell의 실험적 기능 지원에서는 PowerShell 또는 PowerShell 모듈에서 기존의 안정적인 기능과 함께 실험적 기능을 사용할 수 있는 메커니즘을 제공합니다.

실험적 기능은 디자인이 완성되지 않은 기능입니다. 사용자는 이 기능을 테스트하고 피드백을 제공할 수 있습니다. 실험적 기능이 완성되면 해당 디자인 변경 내용은 호환성이 손상되는 변경이 됩니다. 이로 인해 중단이 발생할 수 있으므로 실험적 기능은 프로덕션에서 사용하기에 적합하지 않습니다.

실험적 기능은 기본적으로 사용 하지 않도록 설정 되며 시스템의 사용자 또는 관리자가 명시적으로 사용 하도록 설정 해야 합니다.

사용 하도록 설정 된 실험적 기능은 `powershell.config.json` `$PSHOME` 모든 사용자에 대 한의 파일 또는 특정 사용자에 대 한 사용자별 구성 파일에 나열 됩니다.

> [!NOTE]
> 사용자 구성 파일에서 사용 하도록 설정 된 실험적 기능은 시스템 구성 파일에 나열 된 실험적 기능 보다 우선적으로 적용 됩니다.

## <a name="the-experimental-attribute"></a>실험적 특성

특성을 사용 `Experimental` 하 여 일부 코드를 실험적으로 선언 합니다.

다음 구문을 사용 하 여 실험적 기능의 `Experimental` 이름을 제공 하는 특성과 실험적 기능을 사용 하도록 설정한 경우 수행할 작업을 선언 합니다.

```csharp
[Experimental(NameOfExperimentalFeature, ExperimentAction)]
```

모듈의 경우는 `NameOfExperimentalFeature` 의 형식을 따라야 합니다 `<modulename>.<experimentname>` . `ExperimentAction`매개 변수를 지정 해야 하며 유효한 값은 다음과 같습니다.

- `Show` 기능이 사용 되는 경우이 실험적 기능을 표시 하는 것을 의미 합니다.
- `Hide` 기능이 사용 되는 경우이 실험적 기능을 숨기는 것을 의미 합니다.

### <a name="declaring-experimental-features-in-modules-written-in-c"></a>C로 작성 된 모듈에서 실험적 기능 선언\#

실험적 기능 플래그를 사용 하려는 모듈 작성자는 특성을 사용 하 여 cmdlet을 실험적으로 선언할 수 있습니다 `Experimental` .

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }
```

### <a name="declaring-experimental-features-in-modules-written-in-powershell"></a>PowerShell로 작성 된 모듈에서 실험적 기능 선언

PowerShell로 작성 된 모듈은 특성을 사용 `Experimental` 하 여 실험적 cmdlet을 선언할 수도 있습니다.

```powershell
function Enable-SSHRemoting {
    [Experimental("MyRemoting.PSSSHRemoting", "Show")]
    [CmdletBinding()]
    param()
    ...
}
```

### <a name="mutually-exclusive-experimental-features"></a>상호 배타적인 실험적 기능

실험적 기능이 기존 기능 또는 다른 실험적 기능과 함께 공존할 수 없는 경우가 있습니다.

예를 들어 기존 cmdlet을 재정의 하는 실험적 cmdlet을 사용할 수 있습니다. 두 버전은 나란히 공존할 수 없습니다. 설정에는 `ExperimentAction.Hide` 한 번에 두 cmdlet 중 하나만 사용할 수 있습니다.

이 예에서는 새 실험적 cmdlet을 만듭니다 `Invoke-WebRequest` .
`InvokeWebRequestCommand` 실험적이 아닌 구현을 포함 합니다.
`InvokeWebRequestCommandV2` 에는 cmdlet의 실험적 버전이 포함 되어 있습니다.

를 사용 하면 `ExperimentAction.Hide` 한 번에 두 기능 중 하나만 사용할 수 있습니다.

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }

[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Hide)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommand : WebCmdletBase { ... }
```

`MyWebCmdlets.PSWebCmdletV2`실험적 기능을 사용 하도록 설정 하면 기존 `InvokeWebRequestCommand` 구현이 숨겨지고에서 `InvokeWebRequestCommandV2` 의 구현을 제공 합니다 `Invoke-WebRequest` .

이렇게 하면 사용자가 새 cmdlet을 사용 하 여 피드백을 제공 하 고 필요한 경우 실험적이 아닌 버전으로 되돌릴 수 있습니다.

### <a name="experimental-parameters-in-cmdlets"></a>Cmdlet의 실험적 매개 변수

`Experimental`특성은 개별 매개 변수에도 적용할 수 있습니다. 이를 통해 완전히 새로운 cmdlet이 아닌 기존 cmdlet에 대 한 실험 매개 변수 집합을 만들 수 있습니다.

C #의 예제는 다음과 같습니다.

```csharp
[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Show)]
[Parameter(ParameterSet = "NewCompilation")]
public CompilationParameters CompileParameters { ... }

[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Hide)]
[Parameter()]
public CodeDom CodeDom { ... }
```

PowerShell 스크립트의 다른 예는 다음과 같습니다.

```powershell
param(
    [Experimental("MyModule.PSNewFeature", "Show")]
    [string] $NewName,

    [Experimental("MyModule.PSNewFeature", "Hide")]
    [string] $OldName
)
```

## <a name="checking-if-an-experimental-feature-is-enabled"></a>실험적 기능이 활성화 되어 있는지 확인 하는 중

코드에서 적절 한 작업을 수행 하기 전에 실험적 기능을 사용할 수 있는지 확인 해야 합니다. 클래스의 정적 메서드를 사용 하 여 실험적 기능을 사용할 수 있는지 확인할 수 있습니다 `IsEnabled()` `System.Management.Automation.ExperimentalFeature` .

C #의 예제는 다음과 같습니다.

```csharp
if (ExperimentalFeature.IsEnabled("MyModule.MyExperimentalFeature"))
{
   // code specific to the experimental feature
}
```

PowerShell 스크립트의 예제는 다음과 같습니다.

```powershell
if ([ExperimentalFeature]::IsEnabled("MyModule.MyExperimentalFeature"))
{
  # code specific to the experimental feature
}
```

## <a name="see-also"></a>참고 항목

[Enable-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Enable-ExperimentalFeature)

[Disable-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Disable-ExperimentalFeature)

[Get-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Get-ExperimentalFeature)

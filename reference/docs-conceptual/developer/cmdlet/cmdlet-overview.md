---
title: Cmdlet 개요
ms.date: 06/11/2020
ms.topic: article
ms.openlocfilehash: e179bf371c26781cf1c8db641c46c0329036c8ea
ms.sourcegitcommit: 56463fb628a7d83dec4364e89417d83316c3e53b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2020
ms.locfileid: "84722833"
---
# <a name="cmdlet-overview"></a>Cmdlet 개요

Cmdlet은 PowerShell 환경에서 사용 되는 간단한 명령입니다. PowerShell 런타임은 명령줄에서 제공 되는 자동화 스크립트의 컨텍스트 내에서 이러한 cmdlet을 호출 합니다. 또한 powershell 런타임은 PowerShell Api를 통해 프로그래밍 방식으로 호출 합니다.

## <a name="cmdlets"></a>Cmdlet

Cmdlet은 작업을 수행 하 고 일반적으로 파이프라인의 다음 명령에 Microsoft .NET 개체를 반환 합니다. Cmdlet은 PowerShell의 파이프라인 의미 체계에 참여 하는 단일 명령입니다.
여기에는 이진 (c #) cmdlet, 고급 스크립트 함수, CDXML 및 워크플로가 포함 됩니다.

이 SDK 설명서에서는 c #으로 작성 된 이진 cmdlet을 만드는 방법을 설명 합니다. 스크립트 기반 cmdlet에 대 한 자세한 내용은 다음을 참조 하세요.

- [about_Functions_Advanced](/powershell/module/microsoft.powershell.core/about/about_functions_advanced)
- [about_Functions_CmdletBindingAttribute](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)
- [about_Functions_Advanced_Methods](/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods)

이진 cmdlet을 만들려면 두 가지 특수화 된 cmdlet 기본 클래스 중 하나에서 파생 되는 cmdlet 클래스를 구현 해야 합니다. 파생 클래스는 다음을 수행 해야 합니다.

- 파생 클래스를 식별 하는 특성을 cmdlet으로 선언 합니다.
- 공용 속성을 cmdlet 매개 변수로 식별 하는 특성으로 데코레이팅된 공용 속성을 정의 합니다.
- 하나 이상의 입력 처리 메서드를 재정의 하 여 레코드를 처리 합니다.

[Import-module](/powershell/module/microsoft.powershell.core/import-module) cmdlet을 사용 하 여 클래스를 포함 하는 어셈블리를 직접 로드 하거나 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API를 사용 하 여 어셈블리를 로드 하는 호스트 응용 프로그램을 만들 수 있습니다. 두 메서드는 cmdlet의 기능에 프로그래밍 방식으로 액세스 하 고 명령줄 액세스를 제공 합니다.

## <a name="cmdlet-terms"></a>Cmdlet 용어

PowerShell cmdlet 설명서에서 자주 사용 되는 용어는 다음과 같습니다.

### <a name="cmdlet-attribute"></a>Cmdlet 특성

Cmdlet 클래스를 cmdlet으로 선언 하는 데 사용 되는 .NET 특성입니다. PowerShell에서 선택적으로 사용 되는 여러 특성을 사용 하지만 Cmdlet 특성이 필요 합니다. 이 특성에 대 한 자세한 내용은 [Cmdlet 특성 선언](cmdlet-attribute-declaration.md)을 참조 하세요.

### <a name="cmdlet-parameter"></a>Cmdlet 매개 변수

Cmdlet을 실행 하는 응용 프로그램 또는 사용자에 게 제공 되는 매개 변수를 정의 하는 공용 속성입니다. Cmdlet은 필수, 명명 된 위치, 위치 및 *스위치* 매개 변수를 사용할 수 있습니다. 스위치 매개 변수를 사용 하면 호출에 매개 변수가 지정 된 경우에만 평가 되는 매개 변수를 정의할 수 있습니다. 다양 한 형식의 매개 변수에 대 한 자세한 내용은 [Cmdlet 매개 변수](cmdlet-parameters.md)를 참조 하세요.

### <a name="parameter-set"></a>매개 변수 집합

특정 작업을 수행하기 위해 동일한 명령에 사용할 수 있는 매개 변수 그룹입니다. Cmdlet에는 여러 매개 변수 집합이 있을 수 있지만 각 매개 변수 집합에는 고유한 매개 변수가 하나 이상 있어야 합니다. 올바른 cmdlet 디자인은 unique 매개 변수도 필수 매개 변수 라고 권장 합니다.
매개 변수 집합에 대 한 자세한 내용은 [Cmdlet 매개 변수 집합](cmdlet-parameter-sets.md)을 참조 하세요.

### <a name="dynamic-parameter"></a>동적 매개 변수

런타임에 cmdlet에 추가 되는 매개 변수입니다. 일반적으로 다른 매개 변수가 특정 값으로 설정 된 경우 동적 매개 변수가 cmdlet에 추가 됩니다. 동적 매개 변수에 대 한 자세한 내용은 [Cmdlet 동적 매개 변수](cmdlet-dynamic-parameters.md)를 참조 하세요.

### <a name="input-processing-methods"></a>입력 처리 방법

[System.object](/dotnet/api/System.Management.Automation.Cmdlet) 클래스는 레코드를 처리 하는 데 사용 되는 다음과 같은 가상 메서드를 제공 합니다. 모든 파생 된 cmdlet 클래스는 처음 세 가지 메서드 중 하나 이상을 재정의 해야 합니다.

- [System.object](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): cmdlet에 대 한 선택적인 일회성 전처리 기능을 제공 하는 데 사용 됩니다.
- [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Cmdlet에 대 한 레코드 레코드 처리 기능을 제공 하는 데 사용 됩니다. [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드는 Cmdlet의 입력에 따라 여러 번 호출 되거나 전혀 호출 되지 않을 수 있습니다 (예를 들어,
- [System.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): cmdlet에 대 한 선택적 일회성 사후 처리 기능을 제공 하는 데 사용 됩니다.
- [System.object](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): 사용자가 Cmdlet을 비동기적으로 중지할 때 (예: <kbd>CTRL</kbd> + <kbd>C</kbd>를 눌러) 처리를 중지 하는 데 사용 됩니다.

이러한 메서드에 대 한 자세한 내용은 [Cmdlet 입력 처리 메서드](./cmdlet-input-processing-methods.md)를 참조 하세요.

Cmdlet을 구현 하는 경우 이러한 입력 처리 방법 중 하나 이상을 재정의 해야 합니다.
일반적으로 **ProcessRecord ()** 는 cmdlet이 처리 하는 모든 레코드에 대해 호출 되기 때문에 재정의 하는 메서드입니다. 반면, **beginprocessing ()** 메서드와 **EndProcessing ()** 메서드는 레코드의 전처리 또는 사후 처리를 수행 하기 위해 한 번 호출 됩니다. 이러한 메서드에 대 한 자세한 내용은 [입력 처리 메서드](cmdlet-input-processing-methods.md)를 참조 하세요.

### <a name="shouldprocess-feature"></a>ShouldProcess 기능

PowerShell을 사용 하면 cmdlet이 시스템을 변경 하기 전에 사용자에 게 피드백을 요청 하는 cmdlet을 만들 수 있습니다. 이 기능을 사용 하려면 cmdlet에서 `ShouldProcess` cmdlet 특성을 선언할 때이 기능을 지원 하도록 선언 해야 하며, cmdlet은 입력 처리 메서드 내에서 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 해야 합니다 .이 경우에는 cmdlet을 [실행](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 해야 합니다. 기능을 지 원하는 방법에 대 한 자세한 내용은 `ShouldProcess` [확인 요청](requesting-confirmation-from-cmdlets.md)을 참조 하세요.

### <a name="transaction"></a>트랜잭션

단일 작업으로 처리 되는 명령에 대 한 논리적 그룹입니다. 그룹의 명령이 실패 하 고 사용자가 트랜잭션 내에서 수행 된 작업을 수락 하거나 거부 하도록 선택할 수 있으면 태스크가 자동으로 실패 합니다. 트랜잭션에 참여 하려면 cmdlet은 Cmdlet 특성이 선언 될 때 트랜잭션을 지원 하도록 선언 해야 합니다. 트랜잭션은 Windows PowerShell 2.0에서 도입 되었습니다. 트랜잭션에 대 한 자세한 내용은 [트랜잭션을 지 원하는 방법](how-to-support-transactions.md)을 참조 하세요.

## <a name="how-cmdlets-differ-from-commands"></a>Cmdlet과 명령의 차이점

Cmdlet은 다음과 같은 방법으로 다른 명령 셸 환경의 명령과 다릅니다.

- Cmdlet은 .NET 클래스의 인스턴스입니다. 독립 실행형 실행 파일은 아닙니다.
- 몇 줄의 코드에서 cmdlet을 만들 수 있습니다.
- Cmdlet은 일반적으로 자체 구문 분석, 오류 표시 또는 출력 서식 지정을 수행 하지 않습니다. 구문 분석, 오류 프레젠테이션 및 출력 형식은 PowerShell 런타임에 의해 처리 됩니다.
- Cmdlet은 텍스트 스트림이 아니라 파이프라인에서 입력 개체를 처리 하 고, 일반적으로 cmdlet은 개체를 파이프라인에 출력으로 전달 합니다.
- Cmdlet은 한 번에 하나의 개체를 처리 하기 때문에 레코드 지향적입니다.

## <a name="cmdlet-base-classes"></a>Cmdlet 기본 클래스

Windows PowerShell은 다음 두 가지 기본 클래스에서 파생 된 cmdlet을 지원 합니다.

- 대부분의 cmdlet은 [system.object](/dotnet/api/System.Management.Automation.Cmdlet) 기본 클래스에서 파생 되는 .net 클래스를 기반으로 합니다.
  이 클래스에서 파생 하면 cmdlet이 Windows PowerShell 런타임에 최소 종속성 집합을 사용할 수 있습니다. 두 가지 이점이 있습니다. 첫 번째 방법은 cmdlet 개체가 작으며 PowerShell 런타임에 대 한 변경의 영향을 받을 가능성이 낮은 것입니다. 두 번째 혜택은 필요할 경우 cmdlet 개체의 인스턴스를 직접 만든 다음 PowerShell 런타임을 통해 호출 하는 대신 직접 호출할 수 있다는 것입니다.

- 더 복잡 한 cmdlet은 [PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 기본 클래스에서 파생 되는 .net 클래스를 기반으로 합니다. 이 클래스에서 파생 하면 PowerShell 런타임에 훨씬 더 많은 액세스 권한을 제공 합니다. 이 액세스를 통해 cmdlet은 스크립트를 호출 하 고, 공급자에 액세스 하 고, 현재 세션 상태에 액세스할 수 있습니다.
  현재 세션 상태에 액세스 하려면 세션 변수 및 기본 설정을 가져오고 설정 합니다. 그러나이 클래스에서 파생 하면 cmdlet 개체의 크기가 늘어나지만 cmdlet이 현재 버전의 PowerShell 런타임과 더 긴밀 하 게 결합 됩니다.

일반적으로 PowerShell 런타임에 대 한 확장 액세스 권한이 필요 하지 않은 경우에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet) 클래스에서 파생 해야 합니다.
그러나 PowerShell 런타임에는 cmdlet 실행을 위한 광범위 한 로깅 기능이 있습니다. 감사 모델이이 로깅에 종속 되는 경우 [PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스에서 파생 하 여 다른 cmdlet 내에서 cmdlet을 실행 하지 못하게 할 수 있습니다.

## <a name="cmdlet-attributes"></a>Cmdlet 특성

PowerShell은 cmdlet을 관리 하 고 PowerShell에서 제공 하는 공통 기능을 지정 하 고 cmdlet에 필요할 수 있는 여러 .NET 특성을 정의 합니다. 예를 들어 특성을 사용 하 여 클래스를 cmdlet으로 지정 하 고, cmdlet의 매개 변수를 지정 하 고, cmdlet 개발자가 cmdlet 코드에서 해당 기능을 구현할 필요가 없도록 입력 유효성 검사를 요청 합니다. 특성에 대 한 자세한 내용은 [PowerShell 특성](./cmdlet-attributes.md)을 참조 하세요.

## <a name="cmdlet-names"></a>cmdlet 이름

PowerShell은 동사-명사 이름 쌍을 사용 하 여 cmdlet의 이름을 만듭니다. 예를 들어 `Get-Command` PowerShell에 포함 된 cmdlet은 명령 셸에 등록 된 모든 cmdlet을 가져오는 데 사용 됩니다. 동사는 cmdlet이 수행 하는 작업을 식별 하 고, 명사는 cmdlet이 해당 동작을 수행 하는 리소스를 식별 합니다.

이러한 이름은 .NET 클래스가 cmdlet으로 선언 될 때 지정 됩니다. .NET 클래스를 cmdlet으로 선언 하는 방법에 대 한 자세한 내용은 [Cmdlet 특성 선언](./cmdlet-class-declaration.md)을 참조 하세요.

## <a name="writing-cmdlet-code"></a>Cmdlet 코드 작성

이 문서에서는 cmdlet 코드를 작성 하는 방법을 검색 하는 두 가지 방법을 제공 합니다. 많은 설명 없이 코드를 보려면 [Cmdlet 코드의 예제](./examples-of-cmdlet-code.md)를 참조 하세요. 코드에 대 한 자세한 설명을 선호 하는 경우 [Getproc 자습서](./getproc-tutorial.md), [stopproc 자습서](./stopproc-tutorial.md)또는 [selectstr 자습서](./selectstr-tutorial.md) 항목을 참조 하세요.

Cmdlet을 작성 하는 방법에 대 한 자세한 내용은 [Cmdlet 개발 지침](./cmdlet-development-guidelines.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[PowerShell Cmdlet 개념](./windows-powershell-cmdlet-concepts.md)

[PowerShell Cmdlet 작성](./writing-a-windows-powershell-cmdlet.md)

[PowerShell SDK](../windows-powershell-reference.md)

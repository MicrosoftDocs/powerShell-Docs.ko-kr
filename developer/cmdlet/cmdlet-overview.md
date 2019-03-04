---
title: Cmdlet 개요 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: a53b1ada46ad614af3522e6cc11e187afb76e7b1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855319"
---
# <a name="cmdlet-overview"></a>Cmdlet 개요

Cmdlet는 Windows PowerShell 환경에서 사용 되는 간단한 명령입니다. Windows PowerShell 런타임에 명령줄에서 제공 되는 자동화 스크립트의 컨텍스트 내에서 이러한 cmdlet을 호출 합니다. Windows PowerShell 런타임에 호출을 프로그래밍 방식으로 Windows PowerShell Api를 통해.

## <a name="cmdlets"></a>Cmdlet

Cmdlet는 작업을 수행 하 고 일반적으로 파이프라인에서 다음 명령에는 Microsoft.NET Framework 개체를 반환 합니다. Cmdlet를 작성 하려면 두 가지 특수화 된 cmdlet은 기본 클래스 중 하나에서 파생 되는 cmdlet 클래스를 구현 해야 합니다. 파생된 클래스는 다음 작업을 수행 해야합니다.

- 파생된 클래스를 cmdlet으로 식별 하는 특성을 선언 합니다.

- Cmdlet 매개 변수로 공용 속성을 식별 하는 특성으로 데코레이팅된 공용 속성을 정의 합니다.

- 하나 이상의 입력 처리 레코드를 처리 하는 메서드를 재정의 합니다.

사용 하 여 직접 클래스를 포함 하는 어셈블리를 로드할 수 있습니다는 [Import-module](/powershell/module/microsoft.powershell.core/import-module) cmdlet을 만들 수 있습니다 사용 하 여 어셈블리를 로드 하는 호스트 응용 프로그램을 [ System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API. 두 메서드는 cmdlet의 기능에 대 한 명령줄 및 프로그래밍 방식 액세스를 제공합니다.

## <a name="cmdlet-terms"></a>Cmdlet 사용 약관

다음 용어는 Windows PowerShell cmdlet 설명서에서 자주 사용 됩니다.

- **Cmdlet 특성**: Cmdlet으로는 cmdlet 클래스를 선언 하는 데 사용 되는.NET Framework 특성입니다. Windows PowerShell은 선택적 요소는 다른 여러 특성을 사용 하지만 Cmdlet 특성이 필요 합니다. 이 특성에 대 한 자세한 내용은 참조 하세요. [Cmdlet 특성 선언을](./cmdlet-attribute-declaration.md)합니다.

- **Cmdlet 매개 변수**: 사용자에 게 또는 cmdlet을 실행 하는 응용 프로그램에 사용할 수 있는 매개 변수를 정의 하는 공용 속성입니다. Cmdlet 필수, 명명 된, 위치 및 *전환* 매개 변수입니다. 스위치 매개 변수를 사용 하면 호출 된 매개 변수를 지정 하는 경우에 평가 되는 매개 변수를 정의할 수 있습니다. 다양 한 유형의 매개 변수에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수](./cmdlet-parameters.md)합니다.

- **매개 변수 집합**: 특정 작업을 수행하기 위해 동일한 명령에 사용할 수 있는 매개 변수 그룹입니다. Cmdlet는 여러 매개 변수 집합이 있을 수 있습니다 하지만 각 매개 변수 집합에는 고유한 매개 변수가 하나 이상 있어야 합니다. 좋은 cmdlet 설계 unique 매개 변수는 필수 매개 변수를 될 하는 것이 가장 좋습니다. 매개 변수 집합에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수 설정](./cmdlet-parameter-sets.md)합니다.

- **동적 매개 변수**: 런타임 시 cmdlet에 추가 되는 매개 변수입니다. 일반적으로 다른 매개 변수가 특정 값으로 설정 된 경우 동적 매개 변수를 cmdlet에 추가 됩니다. 동적 매개 변수에 대 한 자세한 내용은 참조 하십시오 [cmdlet은 동적 매개 변수](./cmdlet-dynamic-parameters.md)합니다.

- **입력 처리 메서드**: cmdlet이 입력으로 받은 레코드를 처리하는 데 사용할 수 있는 메서드입니다. 입력된 처리 메서드로 합니다 [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드는 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드, 합니다 [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드, 및 [System.Management.Automation.Cmdlet.Stopprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) 메서드. 하나 이상의 재정의 해야 cmdlet을 구현 하는 경우는 [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)를 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), 및 [ System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드. 일반적으로 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드는 해당 cmdlet이 처리 하는 모든 레코드에 대 한 호출 되므로 재정의 하는 메서드입니다. 반면에 [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드는 [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드 수행 하기 위해 한 번 호출 됩니다 전처리 또는 후 레코드를 처리 합니다. 이러한 방법에 대 한 자세한 내용은 참조 하세요. [입력 처리 메서드](./cmdlet-input-processing-methods.md)합니다.

- **ShouldProcess 기능**: Windows PowerShell을 사용 하면 cmdlet은 시스템에 변경의 작업을 수행 하기 전에 사용자에 게 피드백을 요청 하는 cmdlet를 만들 수 있습니다. 이 기능을 사용 하려면 cmdlet은 Cmdlet 특성을 선언 하 고 cmdlet을 호출 해야 하는 경우 ShouldProcess 기능을 지원 하 선언 해야 합니다 [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 고 [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 는 입력 처리 메서드 내에서 메서드. ShouldProcess 기능을 지 원하는 방법에 대 한 자세한 내용은 참조 하세요. [요청 확인](./requesting-confirmation-from-cmdlets.md)합니다.

- **트랜잭션**: 단일 작업으로 처리 되는 명령의 논리적 그룹입니다. 작업 그룹의 모든 명령이 실패 하면 사용자에 게 적용 하거나 트랜잭션 내에서 수행 되는 작업을 취소 하도록 선택할 경우에 자동으로 실패 합니다. 트랜잭션에 참여 cmdlet은 Cmdlet 특성 선언 되 면 트랜잭션을 지원 하는지 선언 해야 합니다. 트랜잭션에 대 한 지원이 Windows PowerShell 2.0에서 도입 되었습니다. 트랜잭션에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 트랜잭션](http://msdn.microsoft.com/en-us/74d7bac7-bc53-49f1-a47a-272e8da84710)합니다.

## <a name="how-cmdlets-differ-from-commands"></a>명령에서 Cmdlet을 다 하는 방법

Cmdlet는 다음과 같은 방법으로 다른 명령 셸 환경의 명령에서 다릅니다.

- Cmdlet은.NET Framework 클래스의 인스턴스 독립 실행형 실행 하지 않습니다.

- Cmdlet에서 여러 줄의 코드 만큼 만들 수 있습니다.

- Cmdlet은 일반적으로 하지 자체 구문 분석 오류 프레젠테이션 또는 출력의 형식을 지정 합니다. 구문 분석, 오류 표시 및 출력 서식 지정은 Windows PowerShell 런타임에 의해 처리 됩니다.

- 텍스트 스트림 대신 파이프라인에서 개체를 입력 하는 Cmdlet 처리 하 고 cmdlet는 일반적으로 개체를 파이프라인으로 출력으로 전달 합니다.

- Cmdlet은 한 번에 단일 개체를 처리 하므로 레코드 지향입니다.

## <a name="cmdlet-base-classes"></a>Cmdlet은 기본 클래스

Windows PowerShell cmdlet에는 다음 두 가지 기본 클래스에서 파생 되는 지원 합니다.

- 파생 되는.NET Framework 클래스를 기반으로 하는 대부분의 cmdlet을 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 기본 클래스입니다. 이 클래스에서 파생 Windows PowerShell 런타임에 종속성의 최소 집합을 사용 하는 cmdlet이 있습니다. 이 두 가지 이점이 있습니다. 첫 번째 장점은 cmdlet 개체는 작게 하는 Windows PowerShell 런타임에 대 한 변경 내용에 영향을 받을 가능성이 적습니다. 두 번째 장점은 해야 할 경우 cmdlet은 개체의 인스턴스는 직접 만들 하 수 Windows PowerShell 런타임을 통해 호출 하는 대신 직접 호출 합니다.

- 파생 되는.NET Framework 클래스를 기반으로 하는 보다 복잡 한 cmdlet의 [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 기본 클래스입니다. 이 클래스에서 파생 액세스할 수 있습니다 훨씬 더 많은 Windows PowerShell 런타임에 있습니다. 이 액세스 cmdlet 공급자에 액세스 하 고 현재 세션 상태에 액세스 하는 데 스크립트를 호출할 수 있습니다. (현재 세션 상태에 액세스 하려면 얻고 세션 변수 및 기본 설정을 설정 합니다.) 그러나이 클래스에서 파생 cmdlet은 개체의 크기가 늘어나고 의미 cmdlet은 현재 버전의 Windows PowerShell 런타임에 더 밀접 하 게 결합 됩니다.

일반적으로 Windows PowerShell 런타임에 확장된 액세스에 필요한 경우가 아니면에서 파생 시켜야 합니다 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 클래스입니다. 그러나 Windows PowerShell 런타임에 cmdlet 실행에 대 한 광범위 한 로깅 기능이 있습니다. 감사 모델이이 로깅에 의존 하는 경우에서 파생 하 여 다른 cmdlet 내에서 cmdlet의 실행을 방지할 수 있습니다 합니다 [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스입니다.

## <a name="input-processing-methods"></a>입력 처리 메서드

합니다 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 클래스는 레코드를 처리 하는 데 사용 되는 가상 메서드를 제공 합니다. 모든 파생 된 cmdlet 클래스로 처음 세 방법 중 하나 이상을 재정의 해야 합니다.

- [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Cmdlet에 대해 선택적인 일회성 사전 처리 기능을 제공 하는 데 사용 합니다.

- [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Cmdlet에 대 한 레코드에서 처리 기능을 제공 하는 데 사용 합니다. 합니다 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 횟수 또는 전혀 cmdlet의 입력에 따라 여러 메서드를 호출할 수 있습니다.

- [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Cmdlet에 대해 선택적인 일회성 사후 처리 기능을 제공 하는 데 사용 합니다.

- [System.Management.Automation.Cmdlet.Stopprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): 사용자가 cmdlet을 비동기적으로 (예를 들어, CTRL + C를 눌러) 하는 경우 처리를 중지 하는 데 사용 합니다.

이러한 방법에 대 한 자세한 내용은 참조 하세요. [cmdlet은 입력 처리 메서드](./cmdlet-input-processing-methods.md)합니다.

## <a name="cmdlet-attributes"></a>Cmdlet 특성

Windows PowerShell cmdlet을 관리 하 고 Windows PowerShell에서 제공 하는 cmdlet에서 해야 할 수 있습니다 하는 일반적인 기능을 지정 하는 여러.NET Framework 특성을 정의 합니다. 예를 들어, cmdlet, cmdlet의 매개 변수를 지정 하 고 cmdlet 개발자는 해당 cmdlet 코드에서 해당 기능을 구현 하지 않아도 되도록 입력의 유효성 검사 요청으로 클래스를 지정 하려면 특성이 사용 됩니다. 특성에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 특성](./cmdlet-attributes.md)합니다.

## <a name="cmdlet-names"></a>cmdlet 이름

Windows PowerShell cmdlet의 이름이 동사-명사 이름 쌍을 사용합니다. 예를 들어를 `Get-Command` cmdlet은 Windows PowerShell에 포함 된 명령 셸에서 등록 된 모든 cmdlet을 가져오는 데 사용 됩니다. Cmdlet은 수행 하는 작업을 식별 하는 동사 및 명사는 cmdlet이 해당 작업을 수행 하는 리소스를 식별 합니다.

이러한 이름은 cmdlet으로.NET Framework 클래스를 선언할 때 지정 됩니다. Cmdlet으로.NET Framework 클래스를 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [Cmdlet 특성 선언을](./cmdlet-class-declaration.md)합니다.

## <a name="writing-cmdlet-code"></a>Cmdlet 코드 작성

이 문서에서는 cmdlet 코드를 작성 하는 방법을 검색 하는 두 가지를 제공 합니다. 장황한 설명 없이 코드를 참조 하려는 경우 참조 [예의 Cmdlet 코드](./examples-of-cmdlet-code.md)합니다. 코드에 대 한 자세한 설명을 원하는 경우 참조를 [GetProc 자습서](./getproc-tutorial.md)를 [StopProc 자습서](./stopproc-tutorial.md), 또는 [SelectStr 자습서](./selectstr-tutorial.md) 항목입니다.

쓰기 cmdlet에 대 한 지침에 대 한 자세한 내용은 참조 하세요. [Cmdlet 개발 지침](./cmdlet-development-guidelines.md)합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell Cmdlet 개념](./windows-powershell-cmdlet-concepts.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell SDK](../windows-powershell-reference.md)

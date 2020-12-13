---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 특성 선언
description: Cmdlet 특성 선언
ms.openlocfilehash: 6bdfe39a4ab9ef4d4cc98daa592f69f7fab95e84
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653545"
---
# <a name="cmdlet-attribute-declaration"></a>Cmdlet 특성 선언

Cmdlet 특성은 Microsoft .NET Framework 클래스를 cmdlet으로 식별 하 고 cmdlet을 호출 하는 데 사용 되는 동사와 명사를 지정 합니다.

## <a name="syntax"></a>구문

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>매개 변수

`VerbName` ([System.string](/dotnet/api/System.String))이 필요 합니다. Cmdlet 동사를 지정 합니다. 이 동사는 cmdlet이 수행 하는 동작을 지정 합니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md) 및 [필수 개발 지침](./required-development-guidelines.md)을 참조 하세요.

`NounName` ([System.string](/dotnet/api/System.String))이 필요 합니다. Cmdlet 명사를 지정 합니다. 이 명사는 cmdlet이 작동 하는 리소스를 지정 합니다. Cmdlet 명사에 대 한 자세한 내용은 [Cmdlet 선언](./cmdlet-class-declaration.md) 및 강력 하 게 권장 되는 [개발 지침](./strongly-encouraged-development-guidelines.md)을 참조 하세요.

`SupportsShouldProcess` ([System.string) 선택적](/dotnet/api/System.Boolean)명명 된 매개 변수입니다. `True` cmdlet에서 [시스템](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 을 변경 하는 작업을 수행 하기 전에 사용자에 게 메시지를 표시 하는 방법을 제공 하는, cmdlet에 대 한 호출을 지원함을 나타냅니다. `False`기본값은 cmdlet이 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하는 것을 지원 하지 않음을 나타냅니다. 확인 요청에 대 한 자세한 내용은 [확인 요청](./requesting-confirmation-from-cmdlets.md)을 참조 하세요.

`ConfirmImpact` ([System.web](/dotnet/api/System.Management.Automation.ConfirmImpact)... n a m a) 선택적 명명 된 매개 변수입니다. Cmdlet에 대 한 호출을 통해 cmdlet의 동작을 확인 하는 시기를 지정 [합니다.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Cmdlet (기본적으로 Medium)의 기능 값이 변수의 값 보다 크거나 같은 경우에만 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하는 것이 좋습니다. `$ConfirmPreference` 이 매개 변수는 매개 변수가 지정 된 경우에만 지정 해야 합니다 `SupportsShouldProcess` .

`DefaultParameterSetName` ([System.string](/dotnet/api/System.String)) 선택적 명명 된 매개 변수입니다. 사용할 매개 변수 집합을 확인할 수 없는 경우 Windows PowerShell 런타임에서 사용 하려는 기본 매개 변수 집합을 지정 합니다. 각 매개 변수의 고유한 매개 변수를 필수 매개 변수로 설정 하 여이 상황을 제거할 수 있습니다.

기본 매개 변수 집합 이름이 지정 된 경우에도 Windows PowerShell에서 기본 매개 변수 집합을 사용할 수 없는 경우가 있습니다. Windows PowerShell 런타임에서는 단순히 개체 유형을 기반으로 하는 매개 변수 집합을 구분할 수 없습니다. 예를 들어 문자열을 파일 경로로 사용 하는 하나의 매개 변수 집합을 사용 하 고 **FileInfo** 개체를 직접 사용 하는 다른 집합을 사용 하는 경우 Windows PowerShell은 cmdlet에 전달 된 값에 따라 사용할 매개 변수 집합을 확인할 수 없으며 기본 매개 변수 집합을 사용 하지도 않습니다. 이 경우 기본 매개 변수 설정 이름을 지정 하는 경우에도 Windows PowerShell에서 모호한 매개 변수 설정 오류 메시지를 throw 합니다.

`SupportsTransactions` ([System.string) 선택적](/dotnet/api/System.Boolean)명명 된 매개 변수입니다. `True` cmdlet을 트랜잭션 내에서 사용할 수 있음을 나타냅니다. 을 `True` 지정 하면 Windows PowerShell 런타임에서 매개 변수를 `UseTransaction` cmdlet의 매개 변수 목록에 추가 합니다. `False`기본값은 트랜잭션 내에서 cmdlet을 사용할 수 없음을 나타냅니다.

## <a name="remarks"></a>설명

- 동사와 명사는 함께 등록 된 cmdlet을 식별 하 고 스크립트 내에서 cmdlet을 호출 하는 데 사용 됩니다.

- Windows PowerShell 콘솔에서이 cmdlet을 호출 하는 경우 명령은 다음 명령과 유사 합니다.

**VerbName-NounName**

- Cmdlet 특성이 선언 될 때 Windows PowerShell 외부에서 리소스를 변경 하는 모든 cmdlet에는 키워드를 포함 해야 합니다. 이렇게 하면 cmdlet에서 `SupportsShouldProcess` 해당 작업을 수행 하기 전에 cmdlet이 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출할 수 있습니다. [System.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 가를 반환 하는 경우에는 작업을 수행 하면 안 `false` 됩니다. [System.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하 여 생성 된 확인 요청에 대 한 자세한 내용은 [요청 확인](./requesting-confirmation-from-cmdlets.md)을 참조 하세요.

`Confirm`및 `WhatIf` cmdlet 매개 변수는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 지 원하는 cmdlet에 대해서만 사용할 수 있습니다.

## <a name="example"></a>예제

다음 클래스 정의에서는 Cmdlet 특성을 사용 하 여 로컬 컴퓨터에서 실행 중인 프로세스에 대 한 정보를 검색 **하는 node.js cmdlet에** 대 한 .NET Framework 클래스를 식별 합니다.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

**Get-help** cmdlet에 대 한 자세한 내용은 [getproc 자습서](./getproc-tutorial.md)를 참조 하십시오.

## <a name="see-also"></a>관련 항목

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)

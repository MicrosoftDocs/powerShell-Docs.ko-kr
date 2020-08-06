---
title: Cmdlet 코드의 예 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2d2597d3d3f64cae1c1494eb2f05873f6feae5e0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784336"
---
# <a name="examples-of-cmdlet-code"></a>Cmdlet 코드 예제

이 섹션에는 사용자 고유의 cmdlet 작성을 시작 하는 데 사용할 수 있는 cmdlet 코드 예제가 포함 되어 있습니다.

> [!IMPORTANT]
> Cmdlet을 작성 하는 방법에 대 한 단계별 지침은 [Cmdlet 작성을 위한 자습서](./tutorials-for-writing-cmdlets.md)를 참조 하세요.

## <a name="in-this-section"></a>섹션 내용

[간단한 Cmdlet을 작성 하는 방법](./how-to-write-a-simple-cmdlet.md) 이 예제에서는 cmdlet 코드의 기본 구조를 보여 줍니다.

[Cmdlet 매개 변수를 선언 하는 방법](./how-to-declare-cmdlet-parameters.md) 이 예제에서는 다양 한 형식의 매개 변수를 선언 하는 방법을 보여 줍니다.

[매개 변수 집합을 선언 하는 방법](./how-to-declare-parameter-sets.md) 이 예제에서는 cmdlet이 수행 하는 동작을 변경할 수 있는 매개 변수 집합을 선언 하는 방법을 보여 줍니다.

[매개 변수 입력의 유효성을 검사 하는 방법](./how-to-validate-parameter-input.md) 다음 예제에서는 매개 변수 입력의 유효성을 검사 하는 방법을 보여 줍니다.

[동적 매개 변수를 선언 하는 방법](./how-to-declare-dynamic-parameters.md) 이 예제에서는 런타임에 추가 되는 매개 변수를 선언 하는 방법을 보여 줍니다.

[Cmdlet 내에서 스크립트를 호출 하는 방법](./how-to-invoke-scripts-within-a-cmdlet.md) 이 예제에서는 cmdlet에 제공 된 스크립트를 호출 하는 방법을 보여 줍니다.

[입력 처리 메서드를 재정의 하는 방법](./how-to-override-input-processing-methods.md) 다음 예제에서는 BeginProcessing, ProcessRecord 및 EndProcessing 메서드를 재정의 하는 데 사용 되는 기본 구조를 보여 줍니다.

[ShouldProcess 호출을 지 원하는 방법](./how-to-request-confirmations.md) 이 예제에서는 cmdlet 내에서 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) [를 호출](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 하는 방법에 대해 설명 하는 방법에 대해 설명 합니다.

[트랜잭션을 지 원하는 방법](./how-to-support-transactions.md) 이 예에서는 cmdlet이 트랜잭션을 지원 함을 나타내는 방법과 트랜잭션 내에서 cmdlet을 사용할 때 수행 되는 동작을 구현 하는 방법을 보여 줍니다.

[작업 지원 방법](./how-to-support-jobs.md) 이 예제에서는 cmdlet을 작성할 때 작업을 지 원하는 방법을 보여 줍니다.

[Cmdlet에서 cmdlet을 호출 하는 방법](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) 이 예에서는 다른 cmdlet 내에서 cmdlet을 호출 하는 방법을 보여 줍니다 .이 cmdlet을 사용 하면 호출 되는 cmdlet의 기능을 개발 중인 cmdlet에 추가할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)

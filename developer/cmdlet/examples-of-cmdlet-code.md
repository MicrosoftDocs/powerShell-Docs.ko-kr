---
title: Cmdlet 코드의 예 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068201"
---
# <a name="examples-of-cmdlet-code"></a>Cmdlet 코드 예제

이 섹션에서는 사용자 고유의 cmdlet을 작성 하려면 사용할 수 있는 cmdlet 코드의 예제를 포함 합니다.

> [!IMPORTANT]
> Cmdlet을 작성 하기 위한 단계별 지침을 참조 하세요 [작성 하는 Cmdlet에 대 한 자습서](./tutorials-for-writing-cmdlets.md)합니다.

## <a name="in-this-section"></a>이 섹션의 내용

[간단한 Cmdlet을 작성 하는 방법을](./how-to-write-a-simple-cmdlet.md) 이 예제에서는 cmdlet 코드의 기본 구조를 보여 줍니다.

[Cmdlet 매개 변수를 선언 하는 방법을](./how-to-declare-cmdlet-parameters.md) 이 예제에서는 다양 한 유형의 매개 변수를 선언 하는 방법을 보여 줍니다.

[선언 매개 변수를 설정 하는 방법을](./how-to-declare-parameter-sets.md) 이 예제 cmdlet에서 수행 하는 동작을 변경할 수 있는 매개 변수 집합을 선언 하는 방법을 보여 줍니다.

[매개 변수 입력 유효성 검사 방법](./how-to-validate-parameter-input.md) 이러한 예제 매개 변수 입력의 유효성을 검사 하는 방법을 보여 줍니다.

[동적 매개 변수를 선언 하는 방법을](./how-to-declare-dynamic-parameters.md) 이 예제에서는 런타임에 추가 되는 매개 변수를 선언 하는 방법을 보여 줍니다.

[Cmdlet 내에서 스크립트를 호출 하는 방법을](./how-to-invoke-scripts-within-a-cmdlet.md) 이 예제 cmdlet에 제공 된 스크립트를 호출 하는 방법을 보여 줍니다.

[입력 처리 메서드를 재정의 하는 방법을](./how-to-override-input-processing-methods.md) 이러한 예제에서는 BeginProcessing 고 ProcessRecord, EndProcessing 메서드를 재정의 하는 데 기본 구조를 보여 줍니다.

[지원 ShouldProcess 호출 하는 방법](./how-to-request-confirmations.md) 보여 주는이 예제는 방법을 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 하 고 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) cmdlet 내에서 메서드를 호출 해야 합니다.

[트랜잭션 지원 방법](./how-to-support-transactions.md) 이 예제에서는 cmdlet에서 트랜잭션을 지원 하도록 지정 하는 방법 및 cmdlet은 트랜잭션 내에서 사용 되는 경우 수행 되는 작업을 구현 하는 방법을 보여 줍니다.

[지원 작업 방법](./how-to-support-jobs.md) 이 예제에서는 cmdlet을 작성 하는 경우 작업을 지 원하는 방법을 보여 줍니다.

[Cmdlet에서 내는 Cmdlet을 호출 하는 방법을](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) 호출된 cmdlet의 기능을 개발 하는 cmdlet에 추가할 수 있는 다른 cmdlet 내에서 cmdlet을 호출 하는 방법을 보여 주는이 예제입니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

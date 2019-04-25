---
title: Cmdlet 매개 변수 설정 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068523"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet 매개 변수 집합

Windows PowerShell 매개 변수 집합을 사용 하 여 다양 한 시나리오에 대 한 다양 한 작업을 수행할 수 있는 단일 cmdlet를 작성할 수 있도록 합니다. 매개 변수 집합을 사용 하면 사용자가 지정한 매개 변수를 기반으로 하는 다양 한 정보를 반환 하 고 사용자에 게 서로 다른 매개 변수를 노출할 수 있습니다.

## <a name="examples-of-parameter-sets"></a>매개 변수 집합의 예

예를 들어 합니다 `Get-EventLog` 사용자 지정 여부에 따라 다른 정보를 반환 하는 cmdlet (Windows PowerShell에서 제공)를 `List` 또는 `LogName` 매개 변수입니다. 경우는 `List` 매개 변수를 지정, 자체 하지만 포함 된 이벤트 정보가 아니라 로그 파일에 대 한 정보를 반환 합니다. 경우는 `LogName` 특정 이벤트 로그에서 이벤트에 대 한 정보를 반환 하는 cmdlet, 매개 변수를 지정 합니다. 합니다 `List` 고 `LogName` 매개 변수 두 개의 별도 매개 변수 집합을 식별 합니다.

## <a name="unique-parameter"></a>고유한 매개 변수

각 매개 변수 집합에는 Windows PowerShell 런타임에 적절 한 매개 변수 집합을 노출 하는 데 사용할 수 있는 고유한 매개 변수가 있어야 합니다. 가능 하면 unique 매개 변수는 필수 매개 변수 이어야 합니다. 매개 변수가 필수 이면 매개 변수를 지정 하는 사용자가 강제 적용 및 Windows PowerShell 런타임을 사용 하도록 설정 하는 매개 변수를 식별 하는 매개 변수를 사용할 수 있습니다. Unique 매개 변수는 cmdlet 매개 변수를 지정 하지 않아도 실행 되도록 설계 된 경우 필수 일 수 없습니다.

## <a name="multiple-parameter-sets"></a>여러 매개 변수 집합

다음 그림에서 왼쪽된 열 세 가지 유효한 매개 변수 집합을 표시합니다. 매개 변수는 첫 번째 매개 변수 집합에 고유한, B 매개 변수는 두 번째 매개 변수를 설정 하려면 고유한 이며 매개 변수 C 세 번째 매개 변수 집합에 고유 합니다. 그러나 오른쪽 열에서 매개 변수 집합이 없는 고유한 매개 변수입니다.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>매개 변수 요구 사항을 설정

다음 요구 사항을 모든 매개 변수 집합에 적용 됩니다.

- 각 매개 변수 집합에는 고유한 매개 변수가 하나 이상 있어야 합니다. 가능 하면이 매개 변수는 필수 매개 변수입니다.

- 여러 위치 매개 변수를 포함 하는 매개 변수 집합을 각 매개 변수에 대해 고유한 위치를 정의 해야 합니다. 두 위치 매개 변수 없이 동일한 위치를 지정할 수 있습니다.

- 집합에서 하나의 매개 변수를 선언할 수는 `ValueFromPipeline` 키워드의 값을 사용 하 여 `true`입니다. 여러 매개 변수를 정의할 수는 `ValueFromPipelineByPropertyName` 키워드의 값을 사용 하 여 `true`입니다.

- 없는 매개 변수 집합이 매개 변수에 대해 지정 된, 매개 변수는 모든 매개 변수 집합에 속합니다.

## <a name="default-parameter-sets"></a>기본 매개 변수 집합

여러 매개 변수 집합이 정의 되어 있는 경우 사용할 수는 `DefaultParameterSetName` 기본 매개 변수 집합을 지정 하는 Cmdlet 특성의 키워드입니다. Windows PowerShell 명령에서 제공 정보를 기반으로 사용 하도록 설정 하는 매개 변수를 확인할 수 없을 때를 설정 합니다. 기본 매개 변수를 사용 합니다. Cmdlet 특성에 대 한 자세한 내용은 참조 하세요. [Cmdlet 특성 선언을](./cmdlet-attribute-declaration.md)합니다.

## <a name="declaring-parameter-sets"></a>선언 매개 변수 집합

매개 변수 집합을 만들려면 지정 해야 합니다는 `ParameterSetName` 키워드 매개 변수 집합의 모든 매개 변수에 대해 매개 변수 특성을 선언 하는 경우. 여러 매개 변수 집합에 속하는 매개 변수를 각 매개 변수 집합에 대 한 매개 변수 특성을 추가 합니다. 이 옵션을 사용 하면 각 매개 변수 집합에 대해 다르게 매개 변수를 정의할 수 있습니다. 예를 들어, 하나의 집합에 필수 및 다른 선택적으로 매개 변수를 정의할 수 있습니다. 그러나 각 매개 변수 집합에 고유한 매개 변수가 하나 포함 해야 합니다.

다음 예제에서는 `UserName` 매개 변수는 Test01 매개 변수 집합의 고유한 매개 변수 및 `ComputerName` 매개 변수는 Test02 매개 변수 집합의 unique 매개 변수입니다. `SharedParam` 매개 변수 집합 모두에 속하며 Test02 매개 변수 집합에 대 한 선택 사항 이지만 설정 Test01 매개 변수에 대 한 필수입니다.

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```
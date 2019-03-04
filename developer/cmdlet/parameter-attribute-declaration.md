---
title: 매개 변수 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "56863619"
---
# <a name="parameter-attribute-declaration"></a>Parameter 특성 선언

매개 변수 특성을 cmdlet 매개 변수로 cmdlet 클래스의 공용 속성을 식별합니다.

## <a name="syntax"></a>구문

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>매개 변수

`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) 명명 된 매개 변수는 선택 사항입니다. `True` 필요한 cmdlet 매개 변수를 나타냅니다. Cmdlet을 호출 하면 필수 매개 변수를 제공 하지 않으면, Windows PowerShell 매개 변수 값에 대 한 사용자를 묻습니다. 기본값은 `false`입니다.

`ParameterSetName` ([System.String](/dotnet/api/System.String)) 명명 된 매개 변수는 선택 사항입니다. 이 cmdlet은 매개 변수가 속한 매개 변수 집합을 지정 합니다. 없는 매개 변수 집합을 지정 하는 경우 매개 변수는 모든 매개 변수 집합에 속합니다.

`Position` ([System.Integer](/dotnet/api/System.Integer)) 명명 된 매개 변수는 선택 사항입니다. Windows PowerShell 명령 내에서 매개 변수의 위치를 지정합니다.

`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) 명명 된 매개 변수는 선택 사항입니다. `True` cmdlet 매개 변수는 파이프라인 개체에서 해당 값을 나타냅니다. Cmdlet은 전체 액세스 하는 경우이 키워드를 지정 합니다. 개체의 속성 뿐 아니라 개체입니다. 기본값은 `false`입니다.

`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) 명명 된 매개 변수는 선택 사항입니다. `True` cmdlet 매개 변수는 동일한 이름 또는이 매개 변수는 동일한 별칭이 있는 파이프라인 개체의 속성에서 해당 값을 나타냅니다. 예를 들어 cmdlet에는 `Name` 매개 변수 및 파이프라인 개체도 있습니다.을 `Name` 속성, 값을 `Name` 속성에 할당 된는 `Name` cmdlet의 매개 변수. 기본값은 `false`입니다.

`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) 명명 된 매개 변수는 선택 사항입니다. `True` cmdlet 매개 변수를 cmdlet으로 전달 되는 모든 나머지 인수를 허용 하는지 나타냅니다. 기본값은 `false`입니다.

`HelpMessage` 명명 된 매개 변수는 선택 사항입니다. 매개 변수에 대 한 간단한 설명을 지정합니다. Windows PowerShell cmdlet이 실행 되 고 필수 매개 변수를 지정 하지 않으면 하는 경우이 메시지를 표시 합니다.

`HelpMessageBaseName` 명명 된 매개 변수는 선택 사항입니다. 리소스 식별자가 있는 위치를 지정 합니다. 예를 들어이 매개 변수 지역화 하려는 도움말 메시지를 포함 하는 리소스 어셈블리를 지정할 수 있습니다.

`HelpMessageResourceId` 명명 된 매개 변수는 선택 사항입니다. 도움말 메시지를의 리소스 식별자를 지정합니다.

## <a name="remarks"></a>설명

- 이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수를 선언 하는 방법을](./how-to-declare-cmdlet-parameters.md)합니다.

- Cmdlet 매개 변수 수가 있습니다. 그러나 사용자 경험 개선을 위해 매개 변수 개수를 제한 합니다.

- 매개 변수는 공용 비정적 필드 또는 속성에 선언 되어야 합니다. 매개 변수 속성에 선언 되어야 합니다. 속성에 public set 접근자에 있어야 합니다. 경우에 `ValueFromPipeline` 또는 `ValueFromPipelineByPropertyName` 키워드를 지정한 경우 속성 공용 get 접근자가 있어야 합니다.

- 위치 매개 변수를 지정 하는 경우 매개 변수를 5 보다 작게 설정에서 위치 매개 변수 수를 제한 합니다. 및 위치 매개 변수를 연속일 필요가 없습니다. 5, 100 및 250 위치 0, 1 및 2 위치와 동일 하 게 작동 합니다.

- 경우는 `Position` 키워드를 지정 하지 않으면 cmdlet 매개 변수 이름별으로 참조 해야 합니다.

- 매개 변수 집합을 사용 하면 다음 note:

    - 각 매개 변수 집합에는 고유한 매개 변수가 하나 이상 있어야 합니다. 좋은 cmdlet 설계가 고유한 매개 변수 역시 필수 가능한 경우를 나타냅니다. Cmdlet 매개 변수 없이 실행 되도록 디자인 된, 경우 unique 매개 변수는 필수 일 수 없습니다.

    - 매개 변수 집합에 없는 동일한 위치를 사용 하 여 둘 이상의 위치 매개 변수를 포함 해야 합니다.

    - 매개 변수 집합에 하나의 매개 변수를 선언 해야 합니다 `ValueFromPipeline = true`합니다. 여러 매개 변수를 정의할 수 `ValueFromPipelineByPropertyName = true`입니다.

    - 여러 매개 변수를 정의할 수 `ValueFromPipelineByPropertyName = true`입니다.

- 매개 변수 이름에 대 한 지침에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수 이름은](standard-cmdlet-parameter-names-and-types.md)합니다.

- 매개 변수 특성은 정의한 합니다 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 클래스입니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Cmdlet 매개 변수 이름](standard-cmdlet-parameter-names-and-types.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

---
ms.date: 09/13/2016
ms.topic: reference
title: Parameter 특성 선언
description: Parameter 특성 선언
ms.openlocfilehash: 24a49406b1493a7f8c23bca798ddb3e73a901111
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500232"
---
# <a name="parameter-attribute-declaration"></a>Parameter 특성 선언

Parameter 특성은 cmdlet 클래스의 공용 속성을 cmdlet 매개 변수로 식별 합니다.

## <a name="syntax"></a>구문

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>매개 변수

`Mandatory` ([System.string) 선택적](/dotnet/api/System.Boolean)명명 된 매개 변수입니다. `True` cmdlet 매개 변수가 필요 함을 나타냅니다. Cmdlet을 호출할 때 필수 매개 변수를 제공 하지 않으면 Windows PowerShell에서 사용자에 게 매개 변수 값을 묻는 메시지를 표시 합니다. 기본값은 `false`입니다.

`ParameterSetName` ([System.string](/dotnet/api/System.String)) 선택적 명명 된 매개 변수입니다. 이 cmdlet 매개 변수가 속하는 매개 변수 집합을 지정 합니다. 매개 변수 집합이 지정 되지 않은 경우 매개 변수는 모든 매개 변수 집합에 속합니다.

`Position` ([System.web](/dotnet/api/System.Int32)) 선택적 명명 된 매개 변수입니다. Windows PowerShell 명령 내에서 매개 변수의 위치를 지정 합니다.

`ValueFromPipeline` ([System.string) 선택적](/dotnet/api/System.Boolean)명명 된 매개 변수입니다. `True` cmdlet 매개 변수가 파이프라인 개체에서 해당 값을 사용 함을 나타냅니다. Cmdlet이 개체의 속성 뿐만 아니라 전체 개체에 액세스 하는 경우이 키워드를 지정 합니다. 기본값은 `false`입니다.

`ValueFromPipelineByPropertyName` ([System.string) 선택적](/dotnet/api/System.Boolean)명명 된 매개 변수입니다. `True` cmdlet 매개 변수가이 매개 변수와 이름이 같거나 동일한 별칭을 가진 파이프라인 개체의 속성에서 해당 값을 사용 함을 나타냅니다. 예를 들어 cmdlet에 `Name` 매개 변수가 있고 파이프라인 개체에 `Name` 속성도 있으면 속성의 값 `Name` 이 `Name` cmdlet의 매개 변수에 할당 됩니다. 기본값은 `false`입니다.

`ValueFromRemainingArguments` ([System.string) 선택적](/dotnet/api/System.Boolean)명명 된 매개 변수입니다. `True` cmdlet 매개 변수가 cmdlet에 전달 되는 나머지 인수를 모두 허용 함을 나타냅니다. 기본값은 `false`입니다.

`HelpMessage` 선택적 명명 된 매개 변수입니다. 매개 변수에 대 한 간단한 설명을 지정 합니다. Windows PowerShell은 cmdlet을 실행할 때 필수 매개 변수를 지정 하지 않은 경우이 메시지를 표시 합니다.

`HelpMessageBaseName` 선택적 명명 된 매개 변수입니다. 리소스 식별자가 있는 위치를 지정 합니다. 예를 들어이 매개 변수는 지역화할 도움말 메시지를 포함 하는 리소스 어셈블리를 지정할 수 있습니다.

`HelpMessageResourceId` 선택적 명명 된 매개 변수입니다. 도움말 메시지의 리소스 식별자를 지정 합니다.

## <a name="remarks"></a>설명

- 이 특성을 선언 하는 방법에 대 한 자세한 내용은 [Cmdlet 매개 변수를 선언 하는 방법](./how-to-declare-cmdlet-parameters.md)을 참조 하세요.

- Cmdlet에는 원하는 수의 매개 변수가 있을 수 있습니다. 그러나 사용자 환경을 개선 하려면 매개 변수 수를 제한 합니다.

- 매개 변수는 public 비정적 필드 또는 속성에서 선언 해야 합니다. 매개 변수는 속성에서 선언 해야 합니다. 속성에는 public set 접근자가 있어야 하 고 `ValueFromPipeline` 또는 키워드가 지정 된 경우에 `ValueFromPipelineByPropertyName` 는 속성에 public get 접근자가 있어야 합니다.

- 위치 매개 변수를 지정 하는 경우 매개 변수 집합의 위치 매개 변수 수를 5 개 미만으로 제한 합니다. 위치 매개 변수는 연속적 일 필요가 없습니다. 5, 100 및 250 위치는 0, 1, 2 위치와 동일 하 게 작동 합니다.

- 키워드를 `Position` 지정 하지 않은 경우에는 cmdlet 매개 변수를 이름으로 참조 해야 합니다.

- 매개 변수 집합을 사용 하는 경우 다음에 유의 하십시오.

  - 각 매개 변수 집합에는 하나 이상의 고유 매개 변수가 있어야 합니다. 바람직한 cmdlet 디자인은 가능 하면이 unique 매개 변수도 필수 매개 변수 여야 함을 나타냅니다. Cmdlet이 매개 변수 없이 실행 되도록 디자인 된 경우 unique 매개 변수는 필수 매개 변수가 될 수 없습니다.

  - 위치 매개 변수를 두 개 이상 포함 하는 매개 변수 집합은 동일 하지 않습니다.

  - 매개 변수 집합에서 하나의 매개 변수만 선언 해야 `ValueFromPipeline = true` 합니다.

  - 여러 매개 변수에서를 정의할 수 있습니다 `ValueFromPipelineByPropertyName = true` .

- 매개 변수 이름에 대 한 지침에 대 한 자세한 내용은 [Cmdlet 매개 변수 이름](standard-cmdlet-parameter-names-and-types.md)을 참조 하세요.

- Parameter 특성은 [system.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 클래스에서 정의 합니다.

## <a name="see-also"></a>참고 항목

[System.object. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Cmdlet 매개 변수 이름](standard-cmdlet-parameter-names-and-types.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

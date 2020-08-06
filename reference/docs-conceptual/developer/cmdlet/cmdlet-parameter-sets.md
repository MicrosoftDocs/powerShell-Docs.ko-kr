---
title: Cmdlet 매개 변수 집합
ms.date: 09/13/2016
ms.openlocfilehash: 202cdd354693b9b7edaca5c127ae1f7d88ff4a28
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784421"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet 매개 변수 집합

PowerShell은 매개 변수 집합을 사용 하 여 다양 한 시나리오에 대해 다른 작업을 수행할 수 있는 단일 cmdlet을 작성할 수 있도록 합니다. 매개 변수 집합을 사용 하면 사용자에 게 서로 다른 매개 변수를 노출할 수 있습니다. 사용자가 지정한 매개 변수를 기반으로 다른 정보를 반환 하는 데 사용 됩니다.

## <a name="examples-of-parameter-sets"></a>매개 변수 집합의 예

예를 들어 PowerShell `Get-EventLog` cmdlet은 사용자가 **List** 또는 **LogName** 매개 변수를 지정 하는지에 따라 다른 정보를 반환 합니다. **List** 매개 변수가 지정 된 경우 cmdlet은 로그 파일 자체에 대 한 정보를 반환 하지만 여기에 포함 된 이벤트 정보는 반환 하지 않습니다. **LogName** 매개 변수가 지정 된 경우 cmdlet은 특정 이벤트 로그의 이벤트에 대 한 정보를 반환 합니다. **List** 및 **LogName** 매개 변수는 두 개의 개별 매개 변수 집합을 식별 합니다.

## <a name="unique-parameter"></a>Unique 매개 변수

각 매개 변수 집합에는 PowerShell 런타임에서 적절 한 매개 변수 집합을 노출 하는 데 사용 하는 고유한 매개 변수가 있어야 합니다. 가능 하면 unique 매개 변수는 필수 매개 변수 여야 합니다. 매개 변수가 필수 이면 사용자는 매개 변수를 지정 해야 하 고 PowerShell 런타임에서는 매개 변수 집합을 식별 하는 데 해당 매개 변수를 사용 합니다. 매개 변수를 지정 하지 않고 cmdlet을 실행 하도록 디자인 된 경우 unique 매개 변수는 필수 매개 변수 일 수 없습니다.

## <a name="multiple-parameter-sets"></a>여러 매개 변수 집합

다음 그림에서 왼쪽 열에는 세 개의 유효한 매개 변수 집합이 표시 됩니다. **A 매개 변수는** 첫 번째 매개 변수 집합에 대해 고유 하며, **매개 변수 B** 는 두 번째 매개 변수 집합에 고유 하며, **C 매개 변수** 는 세 번째 매개 변수 집합에 대해 고유 합니다. 오른쪽 열에서 매개 변수 집합에는 고유한 매개 변수가 없습니다.

![매개 변수 집합의 그림](media/cmdlet-parameter-sets/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>매개 변수 집합 요구 사항

모든 매개 변수 집합에는 다음 요구 사항이 적용 됩니다.

- 각 매개 변수 집합에는 하나 이상의 고유 매개 변수가 있어야 합니다. 가능 하면이 매개 변수를 필수 매개 변수로 설정 합니다.

- 여러 위치 매개 변수를 포함 하는 매개 변수 집합은 각 매개 변수에 대해 고유한 위치를 정의 해야 합니다. 두 위치 매개 변수는 같은 위치를 지정할 수 없습니다.

- 집합에 있는 하나의 매개 변수만 `ValueFromPipeline` 값을 사용 하 여 키워드를 선언할 수 있습니다 `true` .
  여러 매개 변수는 `ValueFromPipelineByPropertyName` 값을 사용 하 여 키워드를 정의할 수 있습니다 `true` .

- 매개 변수에 대 한 매개 변수 집합이 지정 되지 않은 경우 매개 변수는 모든 매개 변수 집합에 속합니다.

> [!NOTE]
> Cmdlet 또는 함수의 경우 매개 변수 집합은 32 개로 제한 됩니다.

## <a name="default-parameter-sets"></a>기본 매개 변수 집합

여러 매개 변수 집합을 정의 하는 경우 `DefaultParameterSetName` **Cmdlet** 특성의 키워드를 사용 하 여 기본 매개 변수 집합을 지정할 수 있습니다. 명령에서 제공 하는 정보에 따라 사용할 매개 변수 집합을 확인할 수 없는 경우 PowerShell은 기본 매개 변수 집합을 사용 합니다. **Cmdlet** 특성에 대 한 자세한 내용은 [cmdlet 특성 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.

## <a name="declaring-parameter-sets"></a>매개 변수 집합 선언

매개 변수 집합을 만들려면 매개 변수 `ParameterSetName` 집합의 모든 매개 변수에 대 한 **매개 변수** 특성을 선언할 때 키워드를 지정 해야 합니다. 여러 매개 변수 집합에 속하는 매개 변수의 경우 각 매개 변수 집합에 대 한 **매개 변수** 특성을 추가 합니다. 이 특성을 사용 하면 매개 변수 집합 마다 매개 변수를 다르게 정의할 수 있습니다. 예를 들어 매개 변수를 한 집합에서 필수로 정의 하 고 다른 집합에서는 선택적으로 정의할 수 있습니다. 그러나 각 매개 변수 집합에는 하나의 고유 매개 변수가 포함 되어야 합니다. 자세한 내용은 [매개 변수 특성 선언](parameter-attribute-declaration.md)을 참조 하세요.

다음 예제에서 **UserName** 매개 변수는 매개 변수 집합의 고유한 매개 변수이 `Test01` 고 **ComputerName** 매개 변수는 `Test02` 매개 변수 집합의 고유한 매개 변수입니다. **Sharedparam** 매개 변수는 두 집합에 속하며 매개 변수 집합에는 필수 `Test01` 이지만 `Test02` 매개 변수 집합의 경우 선택 사항입니다.

```csharp
[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test02")]
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
private string sharedParam;
```

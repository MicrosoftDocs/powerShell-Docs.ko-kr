---
ms.date: 07/16/2020
ms.topic: reference
title: DSC 환경 리소스
description: DSC 환경 리소스
ms.openlocfilehash: c7995fc5e7efdfb9a1dbae3da9f824d33c67085c
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142585"
---
# <a name="dsc-environment-resource"></a>DSC 환경 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x

PowerShell DSC(필요한 상태 구성)의 **Environment** 리소스에서는 시스템 환경 변수를 관리하는 메커니즘을 제공합니다.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>구문

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>속성

|속성 |Description |
|---|---|
|속성 |특정 상태를 확인하려는 환경 변수의 이름을 나타냅니다. |
|경로 |구성 중인 환경 변수를 정의합니다. 변수가 **Path** 변수이면 이 속성을 `$true`로 설정하고, 그렇지 않으면 `$false`로 설정합니다. 기본값은 `$false`입니다. 구성되고 있는 변수가 **Path** 변수라면, **Value** 속성을 통해 제공된 값은 기존 값에 추가됩니다. |
|값 |환경 변수에 할당할 값입니다. |

## <a name="common-properties"></a>공용 속성

|속성 |Description |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|Ensure |변수가 있는지 여부를 나타냅니다. 변수가 없는 경우 환경 변수를 만들거나 변수가 이미 있는 경우 그 값이 **Value** 속성을 통해 제공된 값과 일치하는지 확인하려면 이 속성을 **있음** 으로 설정합니다. 변수가 존재하는 경우 변수를 삭제하려면 이 속성을 **없음** 으로 설정합니다. |
|PsDscRunAsCredential |전체 리소스를 실행하기 위한 자격 증명을 설정합니다. |

> [!NOTE]
> **PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다. 자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.

## <a name="example"></a>예제

다음 예제에서는 TestEnvironmentVariable이 있고 그 값이 _TestValue_ 인지 확인합니다. 없을 경우 만듭니다.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```

---
ms.date: 01/06/2021
ms.topic: reference
title: DSC 서비스 리소스
description: DSC 서비스 리소스
ms.openlocfilehash: bb151e11475c6e67f1fcb2d73336ff2e34b749b8
ms.sourcegitcommit: afefb3636362857036648c2fe80215bc4e81f5ac
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97957039"
---
# <a name="dsc-service-resource"></a>DSC 서비스 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x

Windows PowerShell DSC(필요한 상태 구성)의 **서비스** 리소스에서는 대상 노드에 있는 서비스를 관리하는 메커니즘을 제공합니다.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>구문

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Dependencies = [string[]] ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>속성

|속성 |Description |
|---|---|
|속성 |서비스 이름을 나타냅니다. 이 속성은 경우에 따라 표시 이름과 다릅니다. `Get-Service` cmdlet으로 서비스 목록과 현재 상태를 가져올 수 있습니다. |
|BuiltInAccount |서비스에 사용할 로그인 계정을 나타냅니다. 이 속성에 허용된 값은 **LocalService**, **LocalSystem** 및 **NetworkService** 입니다. |
|자격 증명 |서비스가 실행되는 계정에 대한 자격 증명을 나타냅니다. 이 속성과 **BuiltinAccount** 속성은 함께 사용할 수 없습니다. |
|StartupType |서비스의 시작 유형을 나타냅니다. 이 속성에 허용된 값은 **Automatic**, **Disabled** 및 **Manual** 입니다. |
|시스템 상태 |서비스에 대해 확인하려는 상태를 나타냅니다. 값은 다음과 같습니다. **실행 중** 또는 **중지됨**. |
|종속성 | 서비스에 포함되어야 하는 종속성 이름의 배열입니다. |
|설명 |대상 서비스에 대한 설명을 나타냅니다. |
|DisplayName |대상 서비스에 대한 표시 이름을 나타냅니다. |
|경로 |새 서비스에 대한 이진 파일의 경로를 나타냅니다. |

## <a name="common-properties"></a>공용 속성

|속성 |Description |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|Ensure |대상 서비스가 시스템에 있는지 여부를 지정합니다. 대상 서비스가 존재하지 않도록 하려면 이 속성을 **Absent** 로 설정합니다. 서비스가 존재하도록 하려면 이 속성을 **Present** 로 설정합니다. 기본값은 **Present** 입니다. |
|PsDscRunAsCredential |전체 리소스를 실행하기 위한 자격 증명을 설정합니다. |

> [!NOTE]
> **PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다. 자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.

## <a name="example"></a>예제

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```

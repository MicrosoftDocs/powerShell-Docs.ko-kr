---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Linux용 DSC nxService 리소스
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047555"
---
# <a name="dsc-for-linux-nxservice-resource"></a>Linux용 DSC nxService 리소스

PowerShell DSC(필요한 상태 구성)의 **nxService** 리소스에서는 Linux 노드에 있는 서비스를 관리하는 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>속성

| 속성 | 설명 |
|---|---|
| 이름| 구성할 서비스/데몬의 이름입니다.|
| 컨트롤러| 서비스를 구성할 때 사용할 서비스 컨트롤러의 형식입니다.|
| 사용| 부팅 시 서비스가 시작되는지 여부를 나타냅니다.|
| State| 서비스가 실행되고 있는지를 나타냅니다. 서비스가 실행 중이 아니도록 하려면 이 속성을 "Stopped"로 설정합니다. 서비스가 실행 중이도록 하려면 이 속성을 "Running"으로 설정합니다.|
| DependsOn | 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 **ID**가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.|

## <a name="additional-information"></a>추가 정보

**nxService** 리소스는 서비스 정의나 서비스에 대한 스크립트가 존재하지 않는 경우 만들지 않습니다. PowerShell 필요한 상태 구성 **nxFile** 리소스를 사용하여 서비스 정의 파일 또는 스크립트의 존재 또는 내용을 관리할 수 있습니다.

## <a name="example"></a>예제

다음 예에서는 **SystemD** 서비스 컨트롤러로 등록된 ‘httpd’ 서비스(Apache HTTP Server용)의 구성을 보여 줍니다.

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```
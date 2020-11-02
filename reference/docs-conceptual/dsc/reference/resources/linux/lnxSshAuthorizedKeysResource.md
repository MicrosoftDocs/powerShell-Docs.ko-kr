---
ms.date: 07/17/2020
ms.topic: reference
title: Linux용 DSC nxSshAuthorizedKeys 리소스
description: Linux용 DSC nxSshAuthorizedKeys 리소스
ms.openlocfilehash: 881e94aa583a745cdac7f01b6e445352ef4ca937
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662767"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>Linux용 DSC nxSshAuthorizedKeys 리소스

PowerShell DSC(필요한 상태 구성)의 **nxAuthorizedKeys** 리소스에서는 지정된된 사용자에 대한 권한 있는 ssh 키를 관리하는 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```Syntax
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>속성

|속성 |Description |
|---|---|
|KeyComment |키에 대한 고유 설명입니다. 이 속성은 키를 고유하게 식별하는 데 사용됩니다. |
|사용자 이름 |ssh 권한 있는 키 파일을 관리할 사용자 이름입니다. 정의되지 않은 경우, 기본 사용자는 **root** 입니다. |
|키 |키의 내용입니다. **Ensure** 가 **Present** 로 설정되어 있을 경우 필수입니다.|

## <a name="common-properties"></a>공용 속성

|속성 |Description |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|Ensure |키가 정의되어 있는지 여부를 지정합니다. 키가 사용자의 권한 있는 키 파일에 존재하지 않도록 하려면 이 속성을 **Absent** 로 설정합니다. 키가 사용자의 권한 있는 키 파일에 정의되어 있도록 하려면 이 속성을 **Present** 로 설정합니다. |

## <a name="example"></a>예제

다음 예제에서는 사용자 "monuser"에 대한 공개 ssh 권한이 있는 키를 정의합니다.

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxSshAuthorizedKeys myKey
    {
        KeyComment = "myKey"
        Ensure = "Present"
        Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
        UserName = "monuser"
    }
}
```

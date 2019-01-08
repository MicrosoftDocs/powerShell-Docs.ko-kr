---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Linux용 DSC nxScript 리소스
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047589"
---
# <a name="dsc-for-linux-nxscript-resource"></a>Linux용 DSC nxScript 리소스

PowerShell DSC(필요한 상태 구성)의 **nxScript** 리소스에서는 Linux 노드에 있는 Linux 스크립트를 실행하는 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>속성

|  속성 |  설명 |
|---|---|
| GetScript| [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet을 호출할 때 실행되는 스크립트를 제공합니다. 스크립트는 #!/bin/bash와 같은 구조로 시작해야 합니다.|
| SetScript| 스크립트를 제공합니다. [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet을 호출하면 **TestScript**가 가장 먼저 실행됩니다. **TestScript** 블록에서 0이 아닌 종료 코드를 반환한다면, **SetScript** 블록이 실행됩니다. **TestScript**에서 0이라는 종료 코드를 반환한다면, **SetScript**가 실행되지 않습니다. 스크립트는 `#!/bin/bash`와 같은 구조로 시작해야 합니다.|
| TestScript| 스크립트를 제공합니다. [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet을 호출하면 이 스크립트가 실행됩니다. 이 스크립트에서 0이 아닌 종료 코드를 반환한다면, SetScript가 실행됩니다. 이 스크립트에서 0이라는 종료 코드를 반환한다면, **SetScript**가 실행되지 않습니다. [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet을 호출하면 **TestScript**도 실행됩니다. 그러나 이 경우에서는 **TestScript**에서 어떤 종료 코드가 반환되는지 관계없이 **SetScript**가 실행되지 않습니다. 실제 구성이 현재 필요한 상태 구성과 일치하는 경우 **TestScript**는 종료 코드 0을 반환해야 하고, 일치하지 않는 경우에는 0이 아닌 종료 코드를 반환해야 합니다. (현재 필요한 상태 구성은 DSC를 사용하는 노드에서 시행된 마지막 구성입니다.) 스크립트는 1#!/bin/bash.1과 같은 구조로 시작해야 합니다.|
| 사용자| 스크립트를 실행할 권한이 있는 사용자입니다.|
| 그룹| 스크립트를 실행할 권한이 있는 그룹입니다.|
| DependsOn | 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 **ID**가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.|

## <a name="example"></a>예제

다음 예제에서는 추가적인 구성 관리를 수행하는 **nxScript** 리소스 사용을 보여 줍니다.

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
}
}
```
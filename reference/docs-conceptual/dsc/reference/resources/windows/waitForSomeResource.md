---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC WaitForSome 리소스
ms.openlocfilehash: 91589c84518a2bd0f4816d11aa011dec1d5305e1
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71952980"
---
# <a name="dsc-waitforsome-resource"></a>DSC WaitForSome 리소스

> 적용 대상: Windows PowerShell 5.x

**WaitForSome** DSC(Desired State Configuration) 리소스를 [DSC 구성](../../../configurations/configurations.md)의 노드 블록 내에서 사용하면 다른 노드의 구성에 대한 종속성을 지정할 수 있습니다.

**ResourceName** 속성으로 지정된 리소스가 **NodeName** 속성으로 정의된 최소 노드 수(**NodeCount**를 통해 지정함)에서 필요한 상태이면 이 리소스가 정상적으로 적용됩니다.

> [!NOTE]
> **WaitForSome** 리소스는 Windows 원격 관리를 사용하여 다른 노드의 상태를 확인합니다. WinRM에 대한 포트 및 보안 요구 사항에 대한 자세한 내용은 [PowerShell Remoting 보안 고려 사항](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)을 참조하세요.

## <a name="syntax"></a>구문

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>속성

|속성 |Description |
|---|---|
|NodeCount |이 리소스를 정상적으로 적용하려면 필요한 상태여야 하는 최소 노드 수입니다. |
|NodeName |사용할 리소스의 대상 노드입니다. |
|ResourceName |사용할 리소스 이름입니다. 이 리소스가 다른 구성에 속하면 `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`으로 이름을 지정합니다. |
|RetryIntervalSec |다시 시도할 때까지의 시간(초)입니다. 최소값은 1입니다. |
|RetryCount |최대 다시 시도 횟수입니다. |
|ThrottleLimit |동시에 연결하는 컴퓨터의 수입니다. 기본값은 `New-CimSession` 기본값입니다. |

## <a name="common-properties"></a>공용 속성

|속성 |Description |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|PsDscRunAsCredential |전체 리소스를 실행하기 위한 자격 증명을 설정합니다. |

> [!NOTE]
> **PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다. 자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.

## <a name="example"></a>예제

이 리소스를 사용하는 방법의 예제를 보려면 [노드 간 종속성 지정](../../../configurations/crossNodeDependencies.md)을 참조하세요.
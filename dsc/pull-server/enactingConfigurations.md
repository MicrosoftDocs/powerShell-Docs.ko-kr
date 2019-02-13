---
ms.date: 10/16/2017
keywords: dsc,powershell,configuration,setup
title: 구성 시행
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679846"
---
# <a name="enacting-configurations"></a>구성 시행

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

PowerShell DSC(필요한 상태 구성) 구성을 시행하는 방법에는 밀어넣기 모드와 끌어오기 모드, 이렇게 두 가지가 있습니다.

## <a name="push-mode"></a>밀어넣기 모드

![밀어넣기 모드](../images/pushModel.png "밀어넣기 모드 작동 방식")

밀어넣기 모드는 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 호출하여 대상 노드에 구성을 적극적으로 적용하는 사용자를 참조합니다.

구성을 만들고 컴파일한 후에는 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 호출하고 cmdlet의 -Path 매개 변수를 구성 MOF가 있는 경로로 설정하여 밀어넣기 모드에서 구성을 시행할 수 있습니다.
예를 들어 구성 MOF가 `C:\DSC\Configurations\localhost.mof`에 있으면, 다음 명령을 사용하여 로컬 컴퓨터에 적용합니다.`Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __참고__: 기본적으로 DSC는 구성을 백그라운드 작업으로 실행 됩니다. 구성을 대화형으로 실행하려면 __-Wait__ 매개 변수로 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)을 호출합니다.

## <a name="pull-mode"></a>끌어오기 모드

![끌어오기 모드](../images/pullModel.png "끌어오기 모드 작동 방식")

풀 모드에서는 풀 클라이언트가 해당 클라이언트의 필요한 상태 구성을 원격 풀 서비스에서 가져오도록 구성됩니다.
마찬가지로, 풀 서비스는 DSC 서비스를 호스트하도록 설정되었으며 풀 클라이언트에 필요한 구성과 리소스로 프로비전되었습니다.
각 풀 클라이언트에는 노드의 구성에 대해 주기적인 준수 확인을 수행하는 예약된 이벤트가 있습니다.
이벤트가 처음으로 트리거되면 풀 클라이언트의 LCM(로컬 구성 관리자)이 LCM에 지정된 구성을 가져오기 위해 풀 서비스에 요청합니다.
해당 구성이 풀 서비스에 존재하고 초기 유효성 검사를 통과하면 이 구성은 풀 클라이언트로 다운로드된 후 여기에서 LCM에 의해 실행됩니다.

LCM은 LCM의 **ConfigurationModeFrequencyMins** 속성으로 지정된 정기적인 간격에 따라 클라이언트가 구성을 준수하는지 확인합니다.
LCM은 LCM의 **RefreshModeFrequency** 속성으로 지정된 정기적인 간격에 따라 풀 서비스의 업데이트된 구성을 확인합니다.
LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md)을 참조하세요.

풀 서비스 호스팅에 권장되는 솔루션은 DSC 클라우드 서비스인 [Azure Automation](https://azure.microsoft.com/services/automation/)입니다.
Azure Automation은 그래픽 관리, 보고 및 중앙 집중식 관리를 제공하는 호스트된 솔루션입니다.

Windows Server에서 풀 서비스 설정에 대한 자세한 내용은 [DSC 웹 풀 서버 설정](pullServer.md)을 참조하세요.
그러나 이 구현에는 기능이 제한되어 있으며 일부 “직접” 통합이 필요합니다.

다음 항목에서는 풀 서비스 및 클라이언트를 설명합니다.

- [Azure Automation DSC 개요](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Setting up an SMB pull server(SMB 끌어오기 서버 설정)](pullServerSMB.md)
- [Configuring a pull client(끌어오기 클라이언트 구성)](pullClientConfigID.md)

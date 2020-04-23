---
ms.date: 10/13/2017
keywords: dsc,powershell,configuration,setup
title: 엔지니어를 위한 필요한 상태 구성 개요
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953800"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>엔지니어를 위한 필요한 상태 구성 개요

이 문서는 개발자 및 운영 팀에게 PowerShell DSC(필요한 상태 구성)의 혜택을 설명하기 위해 작성되었습니다.
DSC가 제공하는 가치에 대해 개략적으로 살펴보려면 [의사 결정자를 위한 필요한 상태 구성 개요](decisionMaker.md)를 참조하세요.

## <a name="benefits-of-desired-state-configuration"></a>필요한 상태 구성의 이점

DSC의 가치는 다음과 같습니다.

- Windows에서 스크립팅의 복잡성 줄이기
- 반복 속도 향상

"연속 배포"라는 개념이 점점 더 중요해지고 있습니다.
연속 배포란 하루에도 여러 번 자주 배포할 수 있음을 의미합니다.
이러한 배포는 문제를 해결하기 위해서가 아니라 게시를 신속하게 하기 위한 것입니다.
새 기능의 개발에서 운영까지의 과정을 최대한 원활하고 안정적으로 진행하여 새 비즈니스 논리의 실현을 단축할 수 있습니다.

클라우드 컴퓨팅으로 전환은 종료 상태 환경이 텍스트로 선언되고 배포 엔진에 게시되는 “선언적” 템플릿 모델을 활용하는 배포 솔루션을 의미합니다.
이 배포 기술을 사용하면 언제든지 배포를 일관되게 반복하여 종료 상태를 보장할 수 있으므로 실패 위협에 대한 복원력을 가지고 대규모로 빠르게 변경할 수 있습니다.
이러한 변경에 대한 응답으로 자동화를 통해 이 작업 스타일을 지원하는 도구 및 서비스가 만들어집니다.

DSC는 선언적 및 idempotent(반복 가능한) 배포, 구성 및 규칙을 제공하는 플랫폼입니다.
DSC 플랫폼을 사용하면 데이터 센터 구성 요소를 올바로 구성하여 오류를 방지하고 비용이 많이 드는 배포 오류를 막을 수 있습니다.
DSC에서는 애플리케이션 코드의 일부로 DSC 구성을 처리하여 연속 배포를 지원합니다.
DSC 구성은 애플리케이션의 일부로 업데이트되므로, 애플리케이션을 배포하는 데 필요한 정보가 항상 사용할 준비가 된 최신 상태입니다.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>"PowerShell이 있는데, 필요한 상태 구성이 필요한 이유는 무엇인가요"?

DSC 구성에서는 의도 또는 "하려는 작업"과 실행 또는 "이 작업을 수행할 방법"을 구분합니다.
즉, 실행 논리가 리소스 내에 포함되어 있습니다.
사용자는 기능에 대한 DSC 리소스를 사용할 수 있는 경우 기능을 구현하거나 배포하는 방법을 몰라도 됩니다.
따라서 사용자는 배포의 구조에 집중할 수 있습니다.

예를 들어 PowerShell 스크립트는 다음과 같습니다.
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
이 스크립트는 단순하고 포괄적이며 간단합니다.
그러나 해당 스크립트를 프로덕션으로 전환하면 여러 문제가 발생합니다.
해당 스크립트가 연속으로 두 번 실행되면 어떻게 될까요?
기존에 Bob이 공유에 대한 모든 권한을 갖고 있었으면 어떻게 되나요?

이러한 문제를 보완하기 위해 스크립트의 "실제" 버전은 다음과 유사합니다.
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

이 스크립트는 많은 논리 및 오류 처리가 포함되어 더 복잡합니다.
이 스크립트는 수행하려는 작업은 더 이상 지정하지 않지만 *수행하는 방법*을 지정하므로 더 복잡합니다.

DSC를 사용하면 수행할 작업을 지정할 수 있고 기본 논리는 일반화됩니다.

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

이 스크립트는 서식이 깔끔하고 읽기 간단합니다.
논리 경로 및 오류 처리는 여전히 [리소스](../resources/resources.md)에 있지만 스크립트 작성자에게 표시되지 않지만 합니다.

## <a name="separating-environment-from-structure"></a>환경과 구조 분리

DevOps의 일반적인 패턴은 배포용 환경이 여러 개입니다.
예를 들어 새 코드의 프로토타입을 신속하게 생성하는 데 사용되는 "dev" 환경이 있을 수 있습니다.
"dev" 환경의 코드는 다른 사용자가 새 기능을 확인하는 "test" 환경으로 이동됩니다.
마지막으로 코드는 "prod" 또는 라이브 사이트 프로덕션 환경으로 이동됩니다.

DSC 구성에서는 [구성 데이터](../configurations/configData.md)를 사용하여 이 dev-test-prod 파이프라인을 수용합니다.
따라서 구성의 구조와 관리되는 노드 간의 차이가 더욱 추상화됩니다.
예를 들어 SQL 서버, IIS 서버 및 중간 계층 서버가 필요한 구성을 정의할 수 있습니다.
이 구성의 다른 부분을 수신하는 노드가 무엇인지에 관계없이 이러한 세 가지 요소는 항상 있습니다.
구성 데이터를 사용하여 dev 환경에서는 모든 세 개 요소가 동일한 컴퓨터를 가리키도록 하고, test 환경에서는 세 요소를 세 개의 다른 컴퓨터로 분리하고, 마지막으로 prod 환경에서는 모든 프로덕션 서버를 가리키도록 할 수 있습니다.
다른 환경으로 배포하려면 대상으로 할 환경에 대한 올바른 구성 데이터를 사용하여 **Start-DscConfiguration**을 호출하면 됩니다.

## <a name="see-also"></a>참고 항목

[구성](../configurations/configurations.md)

[구성 데이터](../configurations/configData.md)

[리소스](../resources/resources.md)

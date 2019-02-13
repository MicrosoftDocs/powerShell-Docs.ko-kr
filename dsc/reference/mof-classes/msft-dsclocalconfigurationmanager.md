---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스
ms.openlocfilehash: 7f6aaf209601e99b0120407eb301d32fcfda9eb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680542"
---
# <a name="msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 클래스

구성 파일의 상태를 제어하고 구성 에이전트를 사용해 구성을 적용하는 LCM(로컬 구성 관리자)입니다.

다음 구문은 MOF(Managed Object Format) 코드를 단순화한 것으로 상속된 속성이 모두 포함되어 있습니다.

## <a name="syntax"></a>구문

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>구성원

**MSFT_DSCLocalConfigurationManager** 클래스에 다음 멤버가 있습니다.

- [메서드][]

### <a name="methods"></a>메서드

**MSFT_DSCLocalConfigurationManager** 클래스에 다음 메서드가 있습니다.

|방법 |설명 |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| 구성 에이전트를 사용해 보류 중인 구성을 적용합니다.|
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| DSC 리소스 디버깅을 사용하지 않도록 설정합니다.|
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| DSC 리소스 디버깅을 사용하도록 설정합니다.|
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| 구성 문서를 관리 노드로 보내고, 구성 에이전트의 **Get** 메서드를 사용해 구성을 적용합니다.|
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| 특정 작업과 관련된 구성 에이전트 출력을 가져옵니다.|
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| 구성 상태 기록을 가져옵니다.|
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| 구성 에이전트를 제어하는 데 사용되는 LCM 설정을 가져옵니다.|
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| 일관성 확인을 시작합니다.|
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| 구성 파일을 제거합니다.|
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| DSC 리소스의 **Get** 메서드를 직접 호출합니다.|
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| DSC 리소스의 **Set** 메서드를 직접 호출합니다.|
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| DSC 리소스의 **Test** 메서드를 직접 호출합니다.|
| [RollBack](msft-dsclocalconfigurationmanager-rollback.md)| 이전 구성으로 롤백합니다.|
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| 구성 문서를 관리 노드로 보내고 보류 중인 변경으로 저장합니다.|
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| 구성 문서를 관리 노드로 보내고, 구성 에이전트를 사용해 구성을 적용합니다.|
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| 구성 문서를 관리 노드로 보내고, 구성 에이전트를 사용해 구성을 적용합니다. GetConfigurationResultOutput을 사용해 결과 출력을 검색합니다.|
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| 구성 에이전트를 제어하는 데 사용되는 LCM 설정을 구성합니다.|
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| 진행 중인 구성을 중지합니다.|
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| 구성 문서를 관리 노드로 보내고, 문서에 대해 현재 구성을 확인합니다.|

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration
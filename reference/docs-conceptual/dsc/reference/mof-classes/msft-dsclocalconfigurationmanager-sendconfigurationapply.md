---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApply 메서드
ms.openlocfilehash: 9b684790e5a7d6c7bdf074caca6040e13807f1ca
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464318"
---
# <a name="sendconfigurationapply-method"></a>SendConfigurationApply 메서드

구성 문서를 관리 노드로 보내고, 구성 에이전트를 사용해 구성을 적용합니다.

## <a name="syntax"></a>구문

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>매개 변수

**ConfigurationData** \[in\] 구성에 대한 환경 데이터입니다.

**force** \[in\] **true**이면 구성을 강제로 중지합니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참고 항목

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

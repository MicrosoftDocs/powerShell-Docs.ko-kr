---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: SendMetaConfigurationApply 메서드
ms.openlocfilehash: 896afe2f3370e108b48583aafb33ee7b0eb1301b
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463723"
---
# <a name="sendmetaconfigurationapply-method"></a>SendMetaConfigurationApply 메서드

구성 에이전트를 제어하는 데 사용되는 로컬 구성 관리자 설정을 구성합니다.

## <a name="syntax"></a>구문

```mof
uint32 SendMetaConfigurationApply(
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

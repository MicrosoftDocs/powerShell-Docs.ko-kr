---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ApplyConfiguration 메서드
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727187"
---
# <a name="applyconfiguration-method"></a>ApplyConfiguration 메서드

구성 에이전트를 사용해 보류 중인 구성을 적용합니다.

보류 중인 구성이 없으면 이 메서드는 현재 구성을 다시 적용합니다.

## <a name="syntax"></a>구문

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>매개 변수

*force* \[in\] **true**인 경우 현재 구성이 다시 적용됩니다. 보류 중인 구성이 있더라도 마찬가지입니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참고 항목

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

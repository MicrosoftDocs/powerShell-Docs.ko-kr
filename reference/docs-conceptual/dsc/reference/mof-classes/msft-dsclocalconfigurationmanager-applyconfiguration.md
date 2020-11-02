---
ms.date: 07/14/2020
ms.topic: reference
title: ApplyConfiguration 메서드
description: ApplyConfiguration 메서드
ms.openlocfilehash: aa99221b33d39c3ecc70156a11eaee10b540e2dc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664278"
---
# <a name="applyconfiguration-method"></a>ApplyConfiguration 메서드

구성 에이전트를 사용해 보류 중인 구성을 적용합니다.

보류 중인 구성이 없으면 이 메서드는 현재 구성을 다시 적용합니다.

## <a name="syntax"></a>구문

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>매개 변수

### <a name="force"></a>force

**true** 인 경우 현재 구성이 다시 적용됩니다. 보류 중인 구성이 있더라도 마찬가지입니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참조

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

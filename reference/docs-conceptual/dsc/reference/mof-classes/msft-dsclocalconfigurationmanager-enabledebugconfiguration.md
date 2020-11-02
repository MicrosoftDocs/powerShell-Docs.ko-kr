---
ms.date: 07/17/2020
ms.topic: reference
title: EnableDebugConfiguration 메서드
description: EnableDebugConfiguration 메서드
ms.openlocfilehash: 536366e6e1627a249f3bc2dc19bfd8ff3de42117
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644784"
---
# <a name="enabledebugconfiguration-method"></a>EnableDebugConfiguration 메서드

DSC 리소스 디버깅을 사용하도록 설정합니다.

## <a name="syntax"></a>구문

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a>매개 변수

**BreakAll** \[in\] 리소스 스크립트의 모든 줄에 중단점을 설정합니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참고 항목

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

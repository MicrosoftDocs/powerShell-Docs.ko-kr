---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfiguration 메서드
description: SendConfiguration 메서드
ms.openlocfilehash: 3939a76ab6672b49559847b0ef1408f1c7be6d0c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650554"
---
# <a name="sendconfiguration-method"></a>SendConfiguration 메서드

구성 문서를 관리 노드로 보내고 보류 중인 변경으로 저장합니다.

## <a name="syntax"></a>구문

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>매개 변수

**ConfigurationData** \[in\] 구성에 대한 환경 데이터입니다.

**force** \[in\] **true** 이면 구성을 강제로 중지합니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참고 항목

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

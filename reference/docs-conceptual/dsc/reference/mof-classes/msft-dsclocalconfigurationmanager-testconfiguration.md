---
ms.date: 07/17/2020
ms.topic: reference
title: TestConfiguration 메서드
description: TestConfiguration 메서드
ms.openlocfilehash: ed26fcad2286ca753fb4b1845b8c6ad0741d491b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648919"
---
# <a name="testconfiguration-method"></a>TestConfiguration 메서드

구성 문서를 관리 노드로 보내고, 문서에 대해 현재 구성을 확인합니다.

## <a name="syntax"></a>구문

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a>매개 변수

**configurationData** \[in\] 구성에 대한 환경 데이터입니다.

**InDesiredState** \[out\] 반환 시, 관리 노드가 구성 문서에서 지정한 상태인지 여부를 지정합니다.

**ResourcesInDesiredState** \[out\] 반환 시, 원하는 상태인 리소스를 지정하는 **MSFT_ResourceInDesiredState** 클래스의 포함 인스턴스가 들어 있습니다.

**ResourcesNotInDesiredState** \[out\] 반환 시, 원하는 상태가 아닌 리소스를 지정하는 **MSFT_ResourceNotInDesiredState** 클래스의 포함 인스턴스가 들어 있습니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참고 항목

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

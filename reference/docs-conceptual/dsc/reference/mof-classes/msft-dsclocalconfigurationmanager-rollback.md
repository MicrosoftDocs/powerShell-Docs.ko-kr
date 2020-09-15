---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: RollBack 메서드
ms.openlocfilehash: 301b8926d2ebf1ebe524f52a67928d34e26d860e
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464335"
---
# <a name="rollback-method"></a>RollBack 메서드

이전 버전으로 구성을 롤백합니다.

## <a name="syntax"></a>구문

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a>매개 변수

**configurationNumber** \[in\] 요청된 구성을 지정합니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참고 항목

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

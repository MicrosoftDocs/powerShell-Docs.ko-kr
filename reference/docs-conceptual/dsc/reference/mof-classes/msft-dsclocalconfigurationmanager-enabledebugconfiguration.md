---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: EnableDebugConfiguration 메서드
ms.openlocfilehash: be75b1012f49db79eb75a68c6912ffd5772bf16f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464097"
---
# <a name="enabledebugconfiguration-method"></a>EnableDebugConfiguration 메서드

DSC 리소스 디버깅을 사용하도록 설정합니다.

## <a name="syntax"></a>구문

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
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

**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참고 항목

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

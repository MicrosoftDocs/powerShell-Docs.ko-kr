---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: StopConfiguration 메서드
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953360"
---
# <a name="stopconfiguration-method"></a>StopConfiguration 메서드

진행 중인 구성 변경을 중지합니다.

## <a name="syntax"></a>구문

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>매개 변수

*force* \[in\] **true**이면 구성을 강제로 중지합니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참고 항목

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

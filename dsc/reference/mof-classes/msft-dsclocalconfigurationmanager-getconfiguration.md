---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetConfiguration 메서드
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734533"
---
# <a name="getconfiguration-method"></a>GetConfiguration 메서드

구성 문서를 관리 노드로 보내고, 구성 에이전트의 **Get** 메서드를 사용해 구성을 적용합니다.

## <a name="syntax"></a>구문

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a>매개 변수

*configurationData* \[in\] 보낼 구성 데이터를 지정합니다.

*configurations* \[out\] 반환 시, 구성의 포함 인스턴스가 들어 있습니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참고 항목

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

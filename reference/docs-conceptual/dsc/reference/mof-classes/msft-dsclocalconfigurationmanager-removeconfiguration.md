---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RemoveConfiguration 메서드
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953400"
---
# <a name="removeconfiguration-method"></a>RemoveConfiguration 메서드

구성 파일을 제거합니다.

## <a name="syntax"></a>구문

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>매개 변수

*Stage* \[in\] 제거할 구성 문서를 지정합니다. 유효한 값은

|값 |Description |
|:--- |:---|
|**1** | **현재** 구성 문서(current.mof)입니다. |
|**2** | **보류 중인** 구성 문서(pending.mof)입니다.  |
|**4** | **이전** 구성 문서(previous.mof)입니다. |

*Force* \[in\] **true**이면 구성을 강제로 제거합니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참고 항목

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

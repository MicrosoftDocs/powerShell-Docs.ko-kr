---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 PerformRequiredConfigurationChecks 메서드
ms.openlocfilehash: b92eefb7fbea6d96afa31f6b802ba10fe20d4103
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682033"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 클래스의 PerformRequiredConfigurationChecks 메서드

작업 스케줄러를 사용해 일관성 확인을 시작합니다.

## <a name="syntax"></a>구문

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>매개 변수

*Flags* \[in\] 실행할 일관성 확인 유형을 지정하는 비트 마스크입니다. 다음 값은 올바르며, 비트 **OR** 작업을 사용해 조합할 수 있습니다.

|Value |설명 |
|:--- |:---|
|**1** | 일반 일관성 확인입니다. |
|**2** | 다시 부팅한 후 일관성 확인의 연속입니다. 이 값은 다른 값과 결합하면 안 됩니다. |
|**4** | 구성은 노드의 메타 구성에 지정된 끌어오기 서버에서 끌어와야 합니다. **5** 값인 경우 이 값은 항상 **1**과 결합되어야 합니다. |
|**8** | 보고서 서버에 상태를 보냅니다. |

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참고 항목

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
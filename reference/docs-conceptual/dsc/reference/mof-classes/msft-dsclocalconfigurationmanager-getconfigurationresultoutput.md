---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,setup
title: GetConfigurationResultOutput 메서드
ms.openlocfilehash: 9c81082c28b2ffcc329264d29784782deaa9779d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464080"
---
# <a name="getconfigurationresultoutput-method"></a>GetConfigurationResultOutput 메서드

특정 작업에 연결된 구성 에이전트 출력을 검색합니다.

## <a name="syntax"></a>구문

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a>매개 변수

**jobId** \[in\] 출력 데이터를 가져올 작업의 ID입니다.

**resumeOutputBookmark** \[in\] 출력이 이전 책갈피의 연속이어야 함을 지정합니다.

**output** \[out\] 지정된 작업의 출력입니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참고 항목

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceSet 메서드
description: ResourceSet 메서드
ms.openlocfilehash: 2554ff5805d7ed9518bd283565dc879a0fdfdfd0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650690"
---
# <a name="resourceset-method"></a>ResourceSet 메서드

DSC 리소스의 **Set** 메서드를 직접 호출합니다.

## <a name="syntax"></a>구문

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a>매개 변수

**ResourceType** \[in\] 호출할 리소스의 이름입니다.

**ModuleName** \[in\] 호출할 리소스를 포함하는 모듈의 이름입니다.

**resourceProperty** \[in\] 해시 테이블의 리소스 속성 이름과 해당 값을 각각 키와 값으로 지정합니다. [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet을 사용하여 리소스 속성 및 해당 종류를 검색합니다.

**RebootRequired** \[out\] 반환 시, 대상 노드를 다시 부팅해야 하면 이 속성이 **true** 로 설정됩니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항

**MOF:** DscCore.mof

**네임스페이스** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>참고 항목

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

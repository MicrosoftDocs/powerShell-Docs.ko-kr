---
title: 일반 매개 변수 이름 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: a421d151ac3fdbb763668dd6fbf775f5b91a833f
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56863649"
---
# <a name="common-parameter-names"></a>일반 매개 변수 이름

이 항목에서 설명 하는 매개 변수를 이라고 *일반 매개 변수*합니다. Windows PowerShell 런타임에 의해 cmdlet에 추가 되 고 cmdlet에서 선언할 수 없습니다.

> [!NOTE]
> 이러한 매개 변수는 공급자 cmdlet을 사용 하 여 데코레이팅된 함수에도 추가 됩니다는 `CmdletBinding` 특성입니다.

## <a name="general-common-parameters"></a>일반 공통 매개 변수

다음 매개 변수는 모든 cmdlet에 추가 되 고 cmdlet이 실행 될 때마다 액세스할 수 있습니다. 이러한 매개 변수에서 정의 되는 [System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) 클래스입니다.

### <a name="debug-alias-db"></a>디버그 (별칭: db)

데이터 형식: SwitchParameter

이 매개 변수 지정 하는지 여부를 프로그래머 수준의 디버깅 메시지를 명령줄에 표시 될 수 있습니다. 이러한 메시지는 cmdlet의 작동 문제를 해결 하는 것에 대 한 고 호출 하 여 생성 되는 [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 메서드. 디버그 메시지를 지역화할 필요가 없습니다.

### <a name="erroraction-alias-ea"></a>ErrorAction (별칭: ea)

데이터 형식: 열거

이 매개 변수는 어떤 조치를 오류가 발생 하면를 지정 합니다. 이 매개 변수에 가능한 값은가 정의한 합니다 [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) 열거형입니다.

### <a name="errorvariable-alias-ev"></a>ErrorVariable (별칭: ev)

데이터 형식: 문자열

이 매개 변수에서 오류가 발생 하는 경우 개체를 배치 하는 변수를 지정 합니다. 사용할에이 변수를 추가 하려면 +*varname* 선택을 취소 하 고 변수를 설정 하는 대신 합니다.

### <a name="outvariable-alias-ov"></a>OutVariable (별칭: ov)

데이터 형식: 문자열

이 매개 변수를 배치할 모든 cmdlet에서 생성 한 개체 출력 변수를 지정 합니다. 사용할에이 변수를 추가 하려면 +*varname* 선택을 취소 하 고 변수를 설정 하는 대신 합니다.

### <a name="outbuffer-alias-ob"></a>OutBuffer (별칭: ob)

데이터 형식: Int32

이 매개 변수는 모든 개체를 파이프라인으로 전달 하기 전에 출력 버퍼에 저장 하는 개체의 수를 정의 합니다. 기본적으로 개체를 파이프라인 아래쪽 즉시 전달 됩니다.

### <a name="verbose-alias-vb"></a>자세한 정보 (별칭: vb)

데이터 형식: SwitchParameter

이 매개 변수는 cmdlet은 명령줄에 표시 될 수 있는 설명 메시지를 기록 하는지 여부를 지정 합니다. 이러한 메시지는 사용자에 게 추가 도움을 제공 하 고를 호출 하 여 생성 되는 [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 메서드.

### <a name="warningaction-alias-wa"></a>WarningAction (별칭: 워싱턴)

데이터 형식: 열거

이 매개 변수는 어떤 조치를 cmdlet 경고 메시지를 기록 하는 경우를 지정 합니다. 이 매개 변수에 가능한 값은가 정의한 합니다 [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) 열거형입니다.

### <a name="warningvariable-alias-wv"></a>WarningVariable (별칭: wv)

데이터 형식: 문자열

이 매개 변수는 경고 메시지를 저장할 수 있습니다 하는 변수를 지정 합니다. 사용할에이 변수를 추가 하려면 +*varname* 선택을 취소 하 고 변수를 설정 하는 대신 합니다.

## <a name="risk-mitigation-parameters"></a>위험 완화 매개 변수

다음 매개 변수는 해당 동작을 수행 하기 전에 확인을 요청 하는 cmdlet에 추가 됩니다. 확인 요청에 대 한 자세한 내용은 참조 하십시오 [요청 확인](./requesting-confirmation-from-cmdlets.md)합니다. 이러한 매개 변수에서 정의 되는 [System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) 클래스입니다.

### <a name="confirm-alias-cf"></a>확인 (별칭: cf)

데이터 형식: SwitchParameter

이 매개 변수는 cmdlet은 사용자가 계속할 것인지를 묻는 메시지가 표시 되는지 여부를 지정 합니다.

### <a name="whatif-alias-wi"></a>WhatIf (별칭: 마법사)

데이터 형식: SwitchParameter

이 매개 변수는 cmdlet은 실제로 아무 작업도 수행 하지 않고 cmdlet를 실행 하는 효과 설명 하는 메시지를 기록 하는지 여부를 지정 합니다.

## <a name="transaction-parameters"></a>트랜잭션 매개 변수

다음 매개 변수는 트랜잭션을 지 원하는 cmdlet에 추가 됩니다. 이러한 매개 변수에서 정의 되는 [System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) 클래스입니다.

### <a name="usetransaction-alias-usetx"></a>UseTransaction (별칭: usetx)

데이터 형식: SwitchParameter

이 매개 변수는 cmdlet에서 해당 작업을 수행 하려면 현재 트랜잭션을 사용할지 여부를 지정 합니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell SDK](../windows-powershell-reference.md)

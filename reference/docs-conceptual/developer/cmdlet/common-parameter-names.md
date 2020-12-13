---
ms.date: 09/13/2016
ms.topic: reference
title: 일반 매개 변수 이름
description: 일반 매개 변수 이름
ms.openlocfilehash: cf39dd3b04660076718336857d79d55c3784ccd1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668221"
---
# <a name="common-parameter-names"></a>일반 매개 변수 이름

이 항목에서 설명 하는 매개 변수는 *일반 매개 변수* 라고 합니다. 이러한 cmdlet은 Windows PowerShell 런타임에 의해 cmdlet에 추가 되며 cmdlet으로 선언할 수 없습니다.

> [!NOTE]
> 이러한 매개 변수는 공급자 cmdlet에 추가 되 고 특성을 사용 하 여 데코레이팅된 함수에도 추가 됩니다 `CmdletBinding` .

## <a name="general-common-parameters"></a>일반 일반 매개 변수

다음 매개 변수는 모든 cmdlet에 추가 되며 cmdlet이 실행 될 때마다 액세스할 수 있습니다. 이러한 매개 변수는 [Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) 클래스에 의해 정의 됩니다.

### <a name="debug-alias-db"></a>디버그 (별칭: db)

데이터 형식: SwitchParameter

이 매개 변수는 명령줄에 표시 될 수 있는 프로그래머 수준의 디버깅 메시지를 지정 합니다. 이러한 메시지는 cmdlet의 작업 문제를 해결 하기 위한 것 이며,이는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 를 호출 하 여 생성 됩니다. 디버그 메시지는 지역화할 필요가 없습니다.

### <a name="erroraction-alias-ea"></a>ErrorAction (별칭: ea)

데이터 형식: Enumeration

이 매개 변수는 오류가 발생할 때 수행할 동작을 지정 합니다. 이 매개 변수에 사용할 수 있는 값은 System.web. [Actionpreference 설정](/dotnet/api/System.Management.Automation.ActionPreference) 열거형에 의해 정의 됩니다.

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias: ev)

데이터 형식: 문자열

이 매개 변수는 오류가 발생 하는 경우 개체를 저장할 변수를 지정 합니다. 이 변수에 추가 하려면 변수를 지우고 설정 하는 대신 +*varname* 을 사용 합니다.

### <a name="outvariable-alias-ov"></a>OutVariable (별칭: ov-es)

데이터 형식: 문자열

이 매개 변수는 cmdlet에 의해 생성 된 모든 출력 개체를 저장할 변수를 지정 합니다. 이 변수에 추가 하려면 변수를 지우고 설정 하는 대신 +*varname* 을 사용 합니다.

### <a name="outbuffer-alias-ob"></a>OutBuffer (별칭: ob)

데이터 형식: Int32

이 매개 변수는 개체를 파이프라인으로 전달 하기 전에 출력 버퍼에 저장할 개체의 수를 정의 합니다. 기본적으로 개체는 즉시 파이프라인으로 전달 됩니다.

### <a name="verbose-alias-vb"></a>Verbose (별칭: vb)

데이터 형식: SwitchParameter

이 매개 변수는 cmdlet이 명령줄에 표시 될 수 있는 설명 메시지를 기록할지 여부를 지정 합니다. 이러한 메시지는 사용자에 게 추가 도움말을 제공 하기 위한 것 이며,이는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 를 호출 하 여 생성 됩니다.

### <a name="warningaction-alias-wa"></a>WarningAction (별칭: wa)

데이터 형식: Enumeration

이 매개 변수는 cmdlet이 경고 메시지를 쓸 때 발생 하는 동작을 지정 합니다. 이 매개 변수에 사용할 수 있는 값은 System.web. [Actionpreference 설정](/dotnet/api/System.Management.Automation.ActionPreference) 열거형에 의해 정의 됩니다.

### <a name="warningvariable-alias-wv"></a>WarningVariable (별칭: wv)

데이터 형식: 문자열

이 매개 변수는 경고 메시지를 저장할 수 있는 변수를 지정 합니다. 이 변수에 추가 하려면 변수를 지우고 설정 하는 대신 +*varname* 을 사용 합니다.

## <a name="risk-mitigation-parameters"></a>Risk-Mitigation 매개 변수

다음 매개 변수는 작업을 수행 하기 전에 확인을 요청 하는 cmdlet에 추가 됩니다. 확인 요청에 대 한 자세한 내용은 [확인 요청](./requesting-confirmation-from-cmdlets.md)을 참조 하세요. 이러한 매개 변수는 [Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) 클래스에 의해 정의 됩니다.

### <a name="confirm-alias-cf"></a>확인 (별칭: cf)

데이터 형식: SwitchParameter

이 매개 변수는 cmdlet에서 사용자에 게 계속할지 묻는 메시지를 표시할지 여부를 지정 합니다.

### <a name="whatif-alias-wi"></a>WhatIf (별칭: wi)

데이터 형식: SwitchParameter

이 매개 변수는 cmdlet이 실제로 아무 동작도 수행 하지 않고 cmdlet을 실행 한 결과를 설명 하는 메시지를 기록할지 여부를 지정 합니다.

## <a name="transaction-parameters"></a>트랜잭션 매개 변수

다음 매개 변수는 트랜잭션을 지 원하는 cmdlet에 추가 됩니다. 이러한 매개 변수는 [system.object](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) 를 통해 정의 됩니다.

### <a name="usetransaction-alias-usetx"></a>UseTransaction (별칭: usetx)

데이터 형식: SwitchParameter

이 매개 변수는 cmdlet이 현재 트랜잭션을 사용 하 여 해당 작업을 수행할지 여부를 지정 합니다.

## <a name="see-also"></a>참고 항목

[Commonparameters입니다.](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[Shouldprocessparameters입니다.](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.object 매개 변수를](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell SDK](../windows-powershell-reference.md)

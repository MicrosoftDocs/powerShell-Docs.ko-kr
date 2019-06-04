---
title: Windows PowerShell 세션 상태 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066977"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell 세션 상태

세션 상태는 Windows PowerShell 세션 또는 모듈의 현재 구성을 참조합니다. Windows PowerShell 세션에는 명령줄 사용자 또는 프로그래밍 방식으로 호스트 응용 프로그램에서 대화형으로 사용 되는 운영 환경입니다. 세션에 세션 상태를 전역 세션 상태 라고 합니다.

개발자 관점에서 Windows PowerShell 세션을 호스트 응용 프로그램을 Windows PowerShell runspace를 열 때 runspace을 닫을 때 사이의 시간을 나타냅니다. 다른 방법을 살펴보고, 세션 수명은 runspace 존재 하는 동안 호출 되는 Windows PowerShell 엔진의 인스턴스.

## <a name="module-session-state"></a>모듈 세션 상태

모듈 세션 상태는 세션으로 가져온 모듈 또는 해당 중첩된 모듈 중 하나가 될 때마다 생성 됩니다. 모듈이 내보내는 cmdlet, 함수 또는 스크립트와 같은 요소를 세션의 전역 세션 상태에 해당 요소에 대 한 참조가 추가 됩니다. 그러나 요소를 실행 하는 경우 모듈의 세션 상태 내에서 실행 됩니다.

## <a name="session-state-data"></a>세션 상태 데이터

세션 상태 데이터는 공용 또는 개인 수 있습니다. 공용 데이터가 개인 데이터를 세션 상태 내에서 호출에만 사용할 수 있는 세션 상태 외부에서 호출을 사용할 수 있습니다. 예를 들어, 모듈을 모듈에 의해만 또는 내부 에서만 호출할 수 있는 전용 함수 있습니다 내보낸 공개 요소입니다. 이.NET Framework 형식의 private 및 public 멤버와 비슷합니다.

세션 상태 데이터는 현재 Windows PowerShell 세션의 컨텍스트 내에서 실행 엔진의 현재 인스턴스에 의해 저장 됩니다. 세션 상태 데이터는 다음 항목으로 구성 됩니다.

- 경로 정보

- 드라이브 정보

- Windows PowerShell 공급자 정보

- 모듈에서 내보내는 모듈 요소 (예: cmdlet, 함수 및 스크립트)에 대 한 참조 및 가져온된 모듈에 대 한 정보입니다. 이 정보 및 이러한 참조는 전역 세션 상태만 합니다.

- 세션 상태 변수 정보

## <a name="accessing-session-state-data-within-cmdlets"></a>Cmdlet 내에서 세션 상태 데이터에 액세스

Cmdlet은 세션 상태 데이터를 하거나 액세스할 수 있습니다 통해 간접적으로 [System.Management.Automation.PSCmdlet.Sessionstate*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) 는 cmdlet 클래스 또는 통해 직접 속성을 [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) 클래스입니다. 합니다 [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) 클래스는 다양 한 유형의 세션 상태 데이터를 조사 하는 속성을 제공 합니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.PSCmdlet.Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System.Management.Automation.Sessionstate?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Windows PowerShell Cmdlet](./cmdlet-overview.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)

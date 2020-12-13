---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 세션 상태
description: Windows PowerShell 세션 상태
ms.openlocfilehash: 51de92f1f392f708cf49c7ccb4a6808fd628076c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668136"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell 세션 상태

세션 상태는 Windows PowerShell 세션 또는 모듈의 현재 구성을 나타냅니다. Windows PowerShell 세션은 명령줄 사용자가 대화형으로 사용 하거나 호스트 응용 프로그램에서 프로그래밍 방식으로 사용 하는 작업 환경입니다. 세션에 대 한 세션 상태를 전역 세션 상태 라고 합니다.

개발자 관점에서 Windows PowerShell 세션은 호스트 응용 프로그램이 Windows PowerShell runspace를 열고 runspace를 닫을 때 까지의 시간을 나타냅니다. 다른 방법으로는 runspace가 존재 하는 동안 호출 되는 Windows PowerShell 엔진 인스턴스의 수명 세션이 있습니다.

## <a name="module-session-state"></a>모듈 세션 상태

모듈 세션 상태는 모듈 또는 중첩 된 모듈 중 하나를 세션으로 가져올 때마다 생성 됩니다. 모듈에서 cmdlet, 함수 또는 스크립트와 같은 요소를 내보내는 경우 해당 요소에 대 한 참조가 세션의 전역 세션 상태에 추가 됩니다. 그러나 요소를 실행 하면 모듈의 세션 상태 내에서 실행 됩니다.

## <a name="session-state-data"></a>Session-State 데이터

세션 상태 데이터는 공개 또는 비공개 일 수 있습니다. 공용 데이터는 세션 상태 외부에서 호출 하는 데 사용할 수 있지만, 전용 데이터는 세션 상태 내의 호출에만 사용할 수 있습니다. 예를 들어 모듈은 모듈에 의해서만 호출 되거나 내보낸 public 요소에 의해서만 내부적으로 호출 될 수 있는 전용 함수를 포함할 수 있습니다. 이는 .NET Framework 형식의 private 및 public 멤버와 비슷합니다.

세션 상태 데이터는 현재 Windows PowerShell 세션 컨텍스트 내에서 실행 엔진의 현재 인스턴스에 의해 저장 됩니다. 세션 상태 데이터는 다음 항목으로 구성 됩니다.

- 경로 정보

- 드라이브 정보

- Windows PowerShell 공급자 정보

- 모듈에서 내보낸 모듈 요소 (예: cmdlet, 함수 및 스크립트)에 대 한 참조 및 가져온 모듈에 대 한 정보입니다. 이 정보와 이러한 참조는 전역 세션 상태 전용입니다.

- 세션 상태 변수 정보

## <a name="accessing-session-state-data-within-cmdlets"></a>Cmdlet 내의 Session-State 데이터에 액세스

Cmdlet은 cmdlet 클래스의 [PSCmdlet. Sessionstate *](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) 속성을 통해 간접적으로 또는 [Sessionstate](/dotnet/api/System.Management.Automation.SessionState) 클래스를 통해 직접 세션 상태 데이터에 액세스할 수 있습니다. [Sessionstate](/dotnet/api/System.Management.Automation.SessionState) 클래스는 여러 유형의 세션 상태 데이터를 조사 하는 데 사용할 수 있는 속성을 제공 합니다.

## <a name="see-also"></a>참고 항목

[PSCmdlet. Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[. Sessionstate? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Windows PowerShell cmdlet](./cmdlet-overview.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)

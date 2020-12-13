---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 참조-새로운 기능
description: Windows PowerShell 참조-새로운 기능
ms.openlocfilehash: b6fa97eacd476f055dd0c69eed2e547c450b85e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647115"
---
# <a name="whats-new"></a>What's New

Windows PowerShell 2.0에는 cmdlet, 공급자 및 호스트 응용 프로그램을 작성할 때 사용할 새 기능이 다음과 같이 제공 됩니다.

## <a name="modules"></a>모듈

이제 모듈을 사용 하 여 Windows PowerShell 솔루션을 패키지 하 고 배포할 수 있습니다. 모듈을 사용 하 여 Windows PowerShell 코드를 독립적이 고 재사용 가능한 단위로 분할, 구성 및 추상화할 수 있습니다. 모듈에 대 한 자세한 내용은 Windows PowerShell 모듈 작성을 참조 하세요.

## <a name="the-powershell-class"></a>PowerShell 클래스

PowerShell 클래스는 프로그래밍 방식으로 명령을 실행 하는 응용 프로그램을 만들기 위한 간단한 솔루션 (호스트 응용 프로그램 이라고 함)을 제공 합니다. 이 클래스를 사용 하 여 명령 파이프라인을 만들고, 명령을 실행 하는 데 사용 되는 runspace를 지정 하 고, 동기적 또는 비동기적으로 명령 호출을 지정할 수 있습니다.

## <a name="the-runspacepool-class"></a>RunspacePool 클래스

Runspace 풀을 사용 하면 단일 호출을 사용 하 여 여러 runspace를 만들 수 있습니다. CreateRunspacePool 메서드는 동일한 호스트, 초기 세션 상태, 연결 정보 등 동일한 기능이 있는 runspace를 만드는 데 사용할 수 있는 여러 오버 로드를 제공 합니다.

## <a name="the-initialsessionstate-class"></a>InitialSessionState 클래스

InitialSessionState 클래스를 사용 하 여 runspace를 열 때 사용 되는 세션 상태 구성을 만들 수 있습니다. 사용자 지정 구성, mshshort에서 제공 하는 명령을 포함 하는 기본 구성 및 세션의 기능에 따라 명령이 제한 되는 구성을 만들 수 있습니다.

## <a name="remote-runspaces"></a>원격 runspace

이제 원격 컴퓨터에서 열 수 있는 runspace을 만들어 원격 컴퓨터에서 명령을 실행 하 고 결과를 로컬로 수집할 수 있습니다. 원격 runspace를 만들려면 runspace를 만들 때 원격 연결에 대 한 정보를 지정 해야 합니다. 예제는 CreateRunspace 및 CreateRunspacePool 메서드를 참조 하세요. 연결 정보는 RunspaceConnectionInfo 클래스에 의해 정의 됩니다.

## <a name="private-runspace-elements"></a>Private runspace 요소

이제 해당 요소가 public 또는 private 인 runspace을 만들 수 있습니다. 그러면 해당 요소를 runspace에 사용할 수 있지만 사용자가 사용할 수 없는 runspace을 만들 수 있습니다. ConstrainedSessionStateEntry 클래스를 참조 하 여 전용으로 만들 수 있는 runspace 요소를 확인 합니다.

## <a name="runspace-threading-modes-and-apartment-state"></a>Runspace 스레딩 모드 및 아파트 상태

이제 runspace에서 명령을 실행할 때 스레드를 만들고 사용 하는 방법을 지정할 수 있습니다. Runspace 및 Runspace 및 RunspacePool 속성을 참조 하는 방법에 대해 자세한 내용을 확인 합니다.

이제 runspace에서 명령을 실행 하는 데 사용 되는 스레드의 아파트 상태를 가져올 수 있습니다. System.threading.thread.apartmentstate 및 Runspace 속성을 참조 하세요. Runspace. System.threading.thread.apartmentstate 속성을 참조 하세요.

## <a name="transaction-cmdlets"></a>트랜잭션 cmdlet

이제 트랜잭션 내에서 사용할 수 있는 cmdlet을 만들 수 있습니다. 트랜잭션에서 cmdlet을 사용 하는 경우 해당 작업은 일시적 이며 Windows PowerShell에서 제공 하는 트랜잭션 cmdlet에 의해 허용 되거나 거부 될 수 있습니다.

트랜잭션에 대 한 자세한 내용은 트랜잭션을 지 원하는 방법을 참조 하세요.

## <a name="transaction-provider"></a>트랜잭션 공급자

이제 트랜잭션 내에서 사용할 수 있는 공급자를 만들 수 있습니다. Cmdlet과 마찬가지로 트랜잭션에서 공급자를 사용 하는 경우 해당 작업은 일시적 이며 Windows PowerShell에서 제공 하는 트랜잭션 cmdlet에 의해 허용 되거나 거부 될 수 있습니다.

공급자 클래스 내에서 트랜잭션 지원을 지정 하는 방법에 대 한 자세한 내용은 CmdletProviderAttribute 속성을 참조 하세요.

## <a name="job-cmdlets"></a>작업 cmdlet

이제 작업으로 작업을 수행할 수 있는 cmdlet을 작성할 수 있습니다. 이러한 작업은 현재 세션과 상호 작용 하지 않고 백그라운드에서 실행 됩니다. Windows PowerShell에서 작업을 지 원하는 방법에 대 한 자세한 내용은 백그라운드 작업을 참조 하세요.

## <a name="cmdlet-output-types"></a>Cmdlet 출력 형식

이제 cmdlet을 작성할 때 OutputType 특성을 선언 하 여 cmdlet에서 반환 되는 .NET Framework 형식을 지정할 수 있습니다. 이렇게 하면 cmdlet에서 반환 되는 개체 유형을 확인할 수 있습니다. cmdlet의 OutputType 속성을 살펴보면 cmdlet에서 반환 되는 개체 유형을 확인할 수 있습니다.

## <a name="event-support"></a>이벤트 지원

이제 이벤트를 추가 하 고 사용 하는 cmdlet을 작성할 수 있습니다. PSEvent 클래스를 참조 하세요.

## <a name="proxy-commands"></a>프록시 명령

이제 다른 명령을 실행 하는 데 사용할 수 있는 프록시 명령을 작성할 수 있습니다. 프록시 명령을 사용 하면 사용자가 사용할 수 있는 원본 cmdlet의 기능을 제어할 수 있습니다. 예를 들어 소스 명령에서 제공 하는 매개 변수를 제거 하는 프록시 명령을 만들 수 있습니다. ProxyCommand 클래스를 참조 하세요.

## <a name="multiple-choice-prompts"></a>여러 선택 프롬프트

이제 사용자가 여러 선택 항목을 선택할 수 있는 프롬프트를 제공할 수 있는 응용 프로그램을 작성할 수 있습니다. IHostUISupportsMultipleChoiceSelection 인터페이스를 참조 하세요.

## <a name="interactive-sessions"></a>대화형 세션

이제 원격 컴퓨터에서 대화형 세션을 시작 하 고 중지할 수 있는 응용 프로그램을 작성할 수 있습니다.
IHostSupportsInteractiveSession 인터페이스를 참조 하세요.

## <a name="custom-cmdlet-help-for-providers"></a>공급자에 대 한 사용자 지정 Cmdlet 도움말

이제 공급자 cmdlet에 대 한 사용자 지정 도움말 항목을 만들 수 있습니다. 사용자 지정 cmdlet 도움말 항목에서는 공급자 경로에서 cmdlet이 작동 하는 방법 및 공급자가 cmdlet에 추가 하는 동적 매개 변수를 비롯 한 특수 기능을 문서화 하는 방법을 설명할 수 있습니다.

---
title: Windows PowerShell 참조-새로운 기능
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080529"
---
# <a name="whats-new"></a>새로운 기능

Windows PowerShell 2.0 cmdlet, 공급자 및 호스트 응용 프로그램을 작성할 때 사용 하기 위해 다음과 같은 새로운 기능을 제공 합니다.

## <a name="modules"></a>모듈

이제 패키지 하 고 모듈을 사용 하 여 Windows PowerShell 솔루션을 배포할 수 있습니다. 모듈에 파티션 수, 구성 및 다시 사용할 수 있는 자체 포함된 단위를 Windows PowerShell 코드를 추상화 합니다. 모듈에 대 한 자세한 내용은 Windows PowerShell 모듈 작성을 참조 하세요.

## <a name="the-powershell-class"></a>PowerShell 클래스

PowerShell 클래스를 프로그래밍 방식으로 명령을 실행 하는 호스트 응용 프로그램 이라고 하는 응용 프로그램을 만들기 위한 간단한 솔루션을 제공 합니다. 이 클래스를 사용 하면 명령의 파이프라인을 만듭니다, 명령을 실행 하는 데 사용 되는 runspace를 지정 하 고, 명령을 호출 하 여 동기적 또는 비동기적으로 지정할 수 있습니다.

## <a name="the-runspacepool-class"></a>RunspacePool 클래스

Runspace 풀을 사용 하 여 단일 호출을 사용 하 여 여러 runspace를 만들 수 있습니다. CreateRunspacePool 메서드를 동일한 호스트, 초기 세션 상태 및 연결 정보 등의 동일한 기능에 있는 runspace를 만드는 데 사용할 수 있는 여러 오버 로드가 있습니다.

## <a name="the-initialsessionstate-class"></a>InitialSessionState 클래스

InitialSessionState 클래스를 사용 하는 runspace를 열 때 사용 되는 세션 상태 구성을 만들 수 있습니다. 사용자 지정 구성을, mshshort를 제공한 명령을 포함 하는 기본 구성 및 명령 세션의 기능에 따라 제한 됩니다 구성을 만들 수 있습니다.

## <a name="remote-runspaces"></a>원격 runspace

이제 만들면 runspace를 열 수 있는 원격 컴퓨터에서 원격 컴퓨터에서 명령을 실행 하 고 결과 로컬로 수집할 수 있습니다. 원격 runspace를 만들려면 runspace를 만들 때 원격 연결에 대 한 정보를 지정 해야 합니다. 예제 CreateRunspace 및 CreateRunspacePool 메서드를 참조 하세요. 연결 정보를 RunspaceConnectionInfo 클래스에 의해 정의 됩니다.

## <a name="private-runspace-elements"></a>개인 runspace 요소

이제 해당 요소는 공용 또는 개인 runspace를 만들 수 있습니다. 이 옵션을 사용 하면 요소가 runspace를 사용할 수 있지만 사용자에 게 사용할 수 없는 runspace를 만들 수 있습니다. Runspace의 요소 수 개인 알아보려면 ConstrainedSessionStateEntry 클래스를 참조 하세요.

## <a name="runspace-threading-modes-and-apartment-state"></a>Runspace 스레딩 모드 및 아파트 상태

스레드 생성 되 고 runspace에서 명령을 실행할 때 사용 되는 방식을 지정할 수 있습니다. System.Management.Automation.Runspaces.Runspace.ThreadOptions 및 System.Management.Automation.Runspaces.RunspacePool.ThreadOptions 속성을 참조 하세요.

이제 runspace에서 명령을 실행 하는 데 사용 되는 스레드의 아파트 상태를 가져올 수 있습니다. System.Management.Automation.Runspaces.Runspace.ApartmentState 및 System.Management.Automation.Runspaces.RunspacePool.ApartmentState 속성을 참조 하세요.

## <a name="transaction-cmdlets"></a>트랜잭션 cmdlet

이제 트랜잭션 내에서 사용할 수 있는 cmdlet를 만들 수 있습니다. 트랜잭션에서 cmdlet를 사용 하면 해당 작업은 임시 하며 수락 하거나 Windows PowerShell에서 제공 하는 트랜잭션 cmdlet에 의해 거부 수 있습니다.

트랜잭션에 대 한 자세한 내용은 참조 하세요. 트랜잭션을 지원 하는 방법입니다.

## <a name="transaction-provider"></a>트랜잭션 공급자

이제 트랜잭션 내에서 사용할 수 있는 공급자를 만들 수 있습니다. Cmdlet, 공급자는 트랜잭션에 사용 되는 경우와 마찬가지로, 해당 작업은 임시 하며 수락 하거나 Windows PowerShell에서 제공 하는 트랜잭션 cmdlet에 의해 거부 수 있습니다.

공급자 클래스 내에서 트랜잭션에 대 한 지원을 지정 하는 방법에 대 한 자세한 내용은 System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities 속성을 참조 하세요.

## <a name="job-cmdlets"></a>Job cmdlet

이제 작업으로 해당 작업을 수행할 수 있는 cmdlet을 작성할 수 있습니다. 이러한 작업은 현재 세션과 상호 작용 없이 백그라운드에서 실행 됩니다. Windows PowerShell 작업에서 지 원하는 방법에 대 한 자세한 내용은 백그라운드 작업을 참조 하세요.

## <a name="cmdlet-output-types"></a>Cmdlet 출력 형식

이제 cmdlet을 작성 하는 경우 OutputType 특성을 선언 하 여 cmdlet에서 반환 되는.NET Framework 형식을 지정할 수 있습니다. 이렇게 하면 다른 cmdlet의 OutputType 속성을 확인 하 여 cmdlet에서 반환 된 개체의 종류를 확인 합니다.

## <a name="event-support"></a>이벤트 지원

이제 추가 및 이벤트를 사용 하는 cmdlet를 작성할 수 있습니다. PSEvent 클래스를 참조 하세요.

## <a name="proxy-commands"></a>프록시 명령

이제 다른 명령을 실행 하는 프록시 명령을 작성할 수 있습니다. Proxy 명령을 사용 하면 원본 cmdlet의 어떤 기능을 사용자에 게 사용할 수를 제어할 수 있습니다. 예를 들어, 원본 명령에 의해 제공 되는 매개 변수를 제거 하는 프록시 명령을 만들 수 있습니다. ProxyCommand 클래스를 참조 하세요.

## <a name="multiple-choice-prompts"></a>여러 개의 선택 프롬프트가

이제 사용자가 여러 선택 항목을 선택할 수 있는 프롬프트를 제공할 수 있는 응용 프로그램을 작성할 수 있습니다. IHostUISupportsMultipleChoiceSelection 인터페이스를 참조 하세요.

## <a name="interactive-sessions"></a>대화형 세션

이제 시작 하 고 원격 컴퓨터에서 대화형 세션을 중지 하는 응용 프로그램을 작성할 수 있습니다.
IHostSupportsInteractiveSession 인터페이스를 참조 하세요.

## <a name="custom-cmdlet-help-for-providers"></a>공급자에 대 한 사용자 지정 Cmdlet 도움말

이제 공급자 cmdlet에 대 한 사용자 지정된 도움말 항목을 만들 수 있습니다. 사용자 지정 cmdlet 도움말 항목의 공급자 경로 및 문서 특수 기능 공급자 cmdlet에 추가 하는 동적 매개 변수를 포함 하 여에서 cmdlet이 작동 하는 방법을 설명 합니다.

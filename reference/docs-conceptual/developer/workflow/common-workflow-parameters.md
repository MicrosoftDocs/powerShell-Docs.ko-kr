---
title: 공통 워크플로 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: b2e8f272a82ee03de306fd8eac45e109142f6284
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366052"
---
# <a name="common-workflow-parameters"></a>일반 워크플로 매개 변수

Windows PowerShell cmdlet에서 생성 된 워크플로 작업은 모든 작업에 공통적인 여러 매개 변수를 정의 합니다. 워크플로 작성자가 활동을 사용자 지정할 수 있도록 이러한 매개 변수의 하위 집합을 제작 시 지정할 수 있습니다. 사용자가 작업을 호출할 때 이러한 매개 변수의 다른 하위 집합을 지정할 수 있습니다.

일반적인 워크플로 매개 변수는 다음과 같이 여러 범주로 그룹화 됩니다.

## <a name="connectivity-parameters"></a>연결 매개 변수

|Name|유형|설명|실행 시간에 최종 사용자가 지정할 수 있나요?|제작 시 워크플로 작성자가 지정할 수 있나요?|인스턴스화할 때 워크플로 작성자가 지정할 수 있나요?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|작업을 시작할 컴퓨터 이름 목록입니다.|예|예|예|
|PSCredential|[System.object. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|PSComputerName 매개 변수로 지정 된 컴퓨터에 로그인 하는 데 사용할 인증 자격 증명입니다. 이 매개 변수는 PSComputerName가 지정 된 경우에만 유효 합니다.|예|예|예|
|PSPort|UInt32|워크플로를 실행 하는 데 사용할 포트입니다.|예|예|예|
|PSUseSSL|부울|SSL (SSL(Secure Sockets Layer)) 프로토콜을 사용 하 여 원격 컴퓨터에 대 한 보안 연결을 설정 하 여 워크플로를 실행 합니다.|예|예|예|
|PSConfigurationName|문자열|워크플로를 실행 하는 데 사용 되는 세션 구성입니다.|예|예|예|
|PSApplicationName|문자열|워크플로 실행에 대 한 연결 URI의 응용 프로그램 이름 부분입니다. ConnectionURI 매개 변수를 사용 하지 않는 경우에만이 매개 변수를 사용 합니다.|예|예|예|
|PSThrottleLimit|UInt32|워크플로를 실행 하기 위해 설정할 수 있는 최대 동시 연결 수입니다.|예|TBD|예|
|PSConnectionURI|String[]|워크플로를 실행 하는 데 사용 되는 대화형 세션의 끝점을 지정 하는 정규화 된 Uri의 배열입니다.|예|예|예|
|PSAllowRedirection|부울|워크플로를 실행 하기 위해이 연결을 대체 URI로 리디렉션할 수 있는지 여부를 지정 합니다.|예|예|예|
|PSSessionOption|[System.object. a p.](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|워크플로를 실행 하는 데 사용 되는 세션에 대 한 고급 옵션입니다.|예|예|예|
|PSAuthentication|[Runspace. Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|사용자의 자격 증명을 인증 하는 데 사용 되는 인증 메커니즘을 지정 하는 [runspace](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) 열거형의 값입니다.|예|예|예|
|PSCertificateThumbprint|문자열|워크플로를 실행할 수 있는 권한이 있는 사용자 계정의 디지털 공개 키 인증서 (X509)입니다.|예|예|예|

### <a name="behavior-parameters"></a>동작 매개 변수
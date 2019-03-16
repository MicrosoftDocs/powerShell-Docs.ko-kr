---
title: 일반적인 워크플로 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: b2e8f272a82ee03de306fd8eac45e109142f6284
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054801"
---
# <a name="common-workflow-parameters"></a>일반 워크플로 매개 변수

Windows PowerShell cmdlet에서 생성 된 워크플로 작업을 모든 작업에는 일반적인 매개 변수 개수를 정의 합니다. 워크플로 작성자가 활동을 사용자 지정할 수 있도록 작성 시 이러한 매개 변수의 하위 집합을 지정할 수 있습니다. 작업을 호출 하는 경우 사용자가 이러한 매개 변수는 다른 하위 집합을 지정할 수 있습니다.

일반적인 워크플로 매개 변수를 다음과 같이 여러 범주로 그룹화 됩니다.

## <a name="connectivity-parameters"></a>연결 매개 변수

|이름|형식|설명|실행 시 최종 사용자가 지정할 수 있습니다.|작성 시 워크플로 작성자가 지정할 수 있습니다.|인스턴스화할 때 워크플로 작성자가 지정할 수 있습니다.|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|목록 작업을 시작 하는 컴퓨터 이름입니다.|예|예|예|
|PSCredential|[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|사용할 인증 자격 증명 PSComputerName 매개 변수로 지정한 컴퓨터에 로그인 합니다. 이 매개 변수는 PSComputerName 지정 하는 경우에 유효 합니다.|예|예|예|
|PSPort|UInt32|워크플로 실행 하는 데 사용할 포트입니다.|예|예|예|
|PSUseSSL|부울|워크플로 실행 하 여 원격 컴퓨터에 보안 연결을 설정할 Secure Sockets Layer (SSL) 프로토콜을 사용 합니다.|예|예|예|
|PSConfigurationName|문자열|워크플로 실행 하는 데 세션 구성을 가져옵니다.|예|예|예|
|PSApplicationName|문자열|워크플로 실행을 위한 연결 URI의 응용 프로그램 이름 부분입니다. ConnectionURI 매개 변수를 사용 하지 않는 경우에이 매개 변수를 사용 합니다.|예|예|예|
|PSThrottleLimit|UInt32|워크플로 실행 하도록 설정할 수 있는 동시 연결의 최대 수입니다.|예|TBD|예|
|PSConnectionURI|String[]|배열 워크플로 실행 하는 데 사용 하는 대화형 세션에 대 한 끝점을 지정 하는 정규화 된 Uri입니다.|예|예|예|
|PSAllowRedirection|부울|이 연결 워크플로 실행 하는 대체 URI로 리디렉션할 수 있도록 할지 여부를 지정 합니다.|예|예|예|
|PSSessionOption|[System.Management.Automation.Remoting.Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|워크플로 실행 하는 데 사용 하는 세션에 대 한 고급 옵션입니다.|예|예|예|
|PSAuthentication|[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|값을 [System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) 사용자의 자격 증명을 인증 하는 데 사용 되는 인증 메커니즘을 지정 하는 열거형입니다.|예|예|예|
|PSCertificateThumbprint|문자열|디지털 공개 키 인증서 (X509) 워크플로 실행할 수 있는 권한을 가진 사용자 계정.|예|예|예|

### <a name="behavior-parameters"></a>동작 매개 변수
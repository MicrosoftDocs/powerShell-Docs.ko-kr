---
title: 보안 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: 9b4d83aeaf45eab1365dec5fbf48c3c796ed5bde
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067436"
---
# <a name="security-parameters"></a>보안 매개 변수

다음 표에서 권장 되는 이름 및 인증서 키 및 권한 정보를 지정 하는 매개 변수와 같은 작업에 대 한 보안 정보를 제공 하는 데 사용 되는 매개 변수에 대 한 기능을 나열 합니다.

|매개 변수|기능|
|---|---|
|**ACL**<br>데이터 형식: 문자열|보호 또는 Uniform 리소스 식별자 (URI)에 대 한 카탈로그에 대 한 액세스 제어 수준을 지정 하려면이 매개 변수를 구현 합니다.|
|**CertFile**<br>데이터 형식: 문자열|사용자는 다음 중 하나를 포함 하는 파일의 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.<br>-규칙 DER (Distinguished Encoding) 또는 Base64로 인코딩된 x.509 인증서<br>하나 이상의 인증서 및 키를 포함 하는 공개 키 암호화 표준 (PKCS) #12 파일-|
|**CertIssuerName**<br>데이터 형식: 문자열|사용자 인증서의 발급자 이름을 지정할 수 있도록 또는 사용자 부분 문자열을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**CertRequestFile**<br>데이터 형식: 문자열|Base64 또는 DER로 인코딩된 pkcs#10 인증서 요청을 포함 하는 파일의 이름을 지정 하려면이 매개 변수를 구현 합니다.|
|**CertSerialNumber**<br>데이터 형식: 문자열|인증 기관에서 발급 하는 일련 번호를 지정 하려면이 매개 변수를 구현 합니다.|
|**CertStoreLocation**<br>데이터 형식: 문자열|사용자 인증서 저장소의 위치를 지정할 수 있도록이 매개 변수를 구현 합니다. 위치는 일반적으로 파일 경로.|
|**CertSubjectName**<br>데이터 형식: 문자열|사용자는 인증서의 발급자를 지정할 수 있도록 또는 사용자 부분 문자열을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**CertUsage**<br>데이터 형식: 문자열|키 사용 또는 확장 된 키 사용을 지정 하려면이 매개 변수를 구현 합니다. 비트 마스크를 약간 개체 식별자 (OID), 또는 문자열 키를 나타낼 수 있습니다.|
|**자격 증명**<br>데이터 형식: [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Cmdlet은 사용자에 게 사용자 이름 또는 암호를 묻는 자동으로이 매개 변수를 구현 합니다. 전체 자격 증명을 직접 제공 하지 않으면 둘 다에 대 한 프롬프트가 표시 됩니다.|
|**CSPName**<br>데이터 형식: 문자열|사용자는 인증서 서비스 공급자 (CSP)의 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**CSPType**<br>데이터 형식: 정수|사용자는 CSP의 유형을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**그룹**<br>데이터 형식: 문자열|사용자 액세스에 대 한 주체의 컬렉션을 지정할 수 있도록이 매개 변수를 구현 합니다. 자세한 내용은 참조에 대 한 설명을 합니다 **주** 매개 변수입니다.|
|**KeyAlgorithm**<br>데이터 형식: 문자열|사용자 보안에 사용할 키 생성 알고리즘을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**KeyContainerName**<br>데이터 형식: 문자열|사용자는 키 컨테이너의 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**KeyLength**<br>데이터 형식: 정수|사용자 비트에서 키의 길이 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**연산**<br>데이터 형식: 문자열|사용자는 보호 된 개체에서 수행할 수 있는 작업을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**보안 주체**<br>데이터 형식: 문자열|사용자 액세스에 대 한 고유 식별이 가능한 엔터티를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**권한**<br>데이터 형식: 문자열|사용자는 cmdlet은 특정 엔터티에 대 한 작업을 수행 해야 오른쪽을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**권한**<br>데이터 형식: 권한의 배열|사용자는 cmdlet에서 특정 항목에 대 한 해당 작업을 수행 해야 하는 권한을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**역할**<br>데이터 형식: 문자열|사용자는 엔터티에서 수행할 수 있는 작업 집합을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**SaveCred**<br>데이터 형식: SwitchParameter|이 매개 변수를 구현 하는 매개 변수를 지정 하는 경우 사용자가 이전에 저장 된 자격 증명은 사용 합니다.|
|**범위**<br>데이터 형식: 문자열|사용자는 cmdlet에 대 한 보호 되는 개체의 그룹을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**SID**<br>데이터 형식: 문자열|사용자 보안 주체를 나타내는 고유 식별자를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**신뢰할 수 있는**<br>데이터 형식: SwitchParameter|매개 변수를 지정 하는 경우 지원 되는 신뢰 수준을 있도록이 매개 변수를 구현 합니다.|
|**TrustLevel**<br>데이터 형식: 키워드|사용자는 지원 되는 신뢰 수준을 지정할 수 있도록이 매개 변수를 구현 합니다. 예를 들어 가능한 값에는 인터넷, 인트라넷 및 fulltrust 포함 됩니다.|

## <a name="see-also"></a>참고 항목

[Cmdlet 매개 변수](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell SDK](../windows-powershell-reference.md)

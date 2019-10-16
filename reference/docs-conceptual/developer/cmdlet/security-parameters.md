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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369502"
---
# <a name="security-parameters"></a>보안 매개 변수

다음 표에서는 인증서 키 및 권한 정보를 지정 하는 매개 변수와 같이 작업에 대 한 보안 정보를 제공 하는 데 사용 되는 매개 변수에 대해 권장 되는 이름 및 기능을 보여 줍니다.

|매개 변수|기능|
|---|---|
|**ACL**<br>데이터 형식: 문자열|카탈로그 또는 URI (Uniform Resource Identifier)에 대 한 액세스 제어 수준을 지정 하려면이 매개 변수를 구현 합니다.|
|**CertFile**<br>데이터 형식: 문자열|사용자가 다음 중 하나를 포함 하는 파일의 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.<br>-Base64 또는 Distinguished Encoding Rules (DER) 인코딩된 x.509 certificate<br>-하나 이상의 인증서와 키를 포함 하는 PKCS (공개 키 암호화 표준) #12 파일|
|**CertIssuerName**<br>데이터 형식: 문자열|사용자가 인증서 발급자의 이름을 지정 하거나 사용자가 하위 문자열을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**CertRequestFile**<br>데이터 형식: 문자열|이 매개 변수를 구현 하 여 Base64 또는 DER로 인코딩된 PKCS #10 인증서 요청을 포함 하는 파일의 이름을 지정 합니다.|
|**CertSerialNumber**<br>데이터 형식: 문자열|이 매개 변수를 구현 하 여 인증 기관에서 발급 한 일련 번호를 지정 합니다.|
|**찾아보십시오**<br>데이터 형식: 문자열|사용자가 인증서 저장소의 위치를 지정할 수 있도록이 매개 변수를 구현 합니다. 위치는 일반적으로 파일 경로입니다.|
|**CertSubjectName**<br>데이터 형식: 문자열|사용자가 인증서 발급자를 지정 하거나 사용자가 부분 문자열을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**CertUsage**<br>데이터 형식: 문자열|키 사용 또는 확장 된 키 사용을 지정 하려면이 매개 변수를 구현 합니다. 키를 비트 마스크, 비트, OID (개체 식별자) 또는 문자열로 나타낼 수 있습니다.|
|**증명서**<br>데이터 형식: [system.web. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Cmdlet이 사용자에 게 사용자 이름 또는 암호를 묻는 메시지를 자동으로 표시 하도록이 매개 변수를 구현 합니다. 전체 자격 증명을 직접 제공 하지 않으면 둘 다에 대 한 프롬프트가 표시 됩니다.|
|**CSPName**<br>데이터 형식: 문자열|사용자가 CSP (인증서 서비스 공급자)의 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**CSPType**<br>데이터 형식: Integer|사용자가 CSP 형식을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**그룹**<br>데이터 형식: 문자열|사용자가 액세스에 대 한 보안 주체 컬렉션을 지정할 수 있도록이 매개 변수를 구현 합니다. 자세한 내용은 **Principal** 매개 변수에 대 한 설명을 참조 하세요.|
|**KeyAlgorithm**<br>데이터 형식: 문자열|사용자가 보안에 사용할 키 생성 알고리즘을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**Cspparameters.keycontainername**<br>데이터 형식: 문자열|이 매개 변수를 구현 하 여 사용자가 키 컨테이너의 이름을 지정할 수 있도록 합니다.|
|**KeyLength**<br>데이터 형식: Integer|사용자가 키의 길이 (비트)를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**연산의**<br>데이터 형식: 문자열|사용자가 보호 된 개체에 대해 수행할 수 있는 작업을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**원칙**<br>데이터 형식: 문자열|사용자가 액세스를 위해 고유 하 게 식별할 수 있는 엔터티를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**권한과**<br>데이터 형식: 문자열|사용자가 특정 엔터티에 대 한 작업을 수행 하는 데 필요한 권한을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**권한**<br>데이터 형식: 권한 배열|사용자가 특정 항목에 대 한 작업을 수행 하는 데 필요한 권한을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**역할**<br>데이터 형식: 문자열|사용자가 엔터티에서 수행할 수 있는 작업 집합을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**SaveCred**<br>데이터 형식: SwitchParameter|매개 변수가 지정 될 때 사용자가 이전에 저장 한 자격 증명을 사용 하도록이 매개 변수를 구현 합니다.|
|**범위**<br>데이터 형식: 문자열|이 매개 변수를 구현 하 여 사용자가 cmdlet에 대 한 보호 된 개체의 그룹을 지정할 수 있도록 합니다.|
|**S**<br>데이터 형식: 문자열|사용자가 보안 주체를 나타내는 고유 식별자를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**신뢰할 수 있는**<br>데이터 형식: SwitchParameter|매개 변수가 지정 된 경우 신뢰 수준이 지원 되도록이 매개 변수를 구현 합니다.|
|**TrustLevel**<br>데이터 형식: 키워드|사용자가 지원 되는 신뢰 수준을 지정할 수 있도록이 매개 변수를 구현 합니다. 예를 들어 가능한 값에는 인터넷, 인트라넷 및 fulltrust가 있습니다.|

## <a name="see-also"></a>참고 항목

[Cmdlet 매개 변수](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell SDK](../windows-powershell-reference.md)

---
title: 속성 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067572"
---
# <a name="property-parameters"></a>속성 매개 변수

다음 표에서 권장 되는 이름 및 속성 매개 변수에 대 한 기능을 나열합니다.

|매개 변수|기능|
|---|---|
|**개수**<br>데이터 형식: Int32|사용자는 처리할 개체 수를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**설명**<br>데이터 형식: 문자열|사용자 리소스에 대 한 설명을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**보낸 사람**<br>데이터 형식: 문자열|사용자의 정보를 가져올 참조 개체를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**Id**<br>데이터 형식: 종속 리소스|사용자 리소스의 식별자를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**입력**<br>데이터 형식: 문자열|사용자 입력된 파일 사양을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**위치**<br>데이터 형식: 문자열|사용자 리소스의 위치를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**LogName**<br>데이터 형식: 문자열|사용자를 처리 하거나 사용 하 여 로그 파일의 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**이름**<br>데이터 형식: 문자열|사용자 리소스의 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**출력**<br>데이터 형식: 문자열|사용자는 출력 파일을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**소유자**<br>데이터 형식: 문자열|사용자는 리소스 소유자의 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**속성**<br>데이터 형식: 문자열|사용자 이름 또는 사용할 속성의 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**이유**<br>데이터 형식: 문자열|이 cmdlet가 호출 되는 이유를 사용자 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**Regex**<br>데이터 형식: SwitchParameter|매개 변수를 지정 하는 경우 정규식을 사용할 수 있도록이 매개 변수를 구현 합니다. 이 매개 변수를 지정 하는 경우 와일드 카드 문자는 확인 되지 않습니다.|
|**속도**<br>데이터 형식: Int32|사용자는 전송 속도 지정할 수 있도록이 매개 변수를 구현 합니다. 사용자는 리소스의 속도를이 매개 변수를 설정합니다.|
|**State**<br>데이터 형식: 키워드 배열|사용자 상태의 KEYDOWN 같은 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**Value**<br>데이터 형식: 개체|사용자는 cmdlet을 제공 하도록 값을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**버전**<br>데이터 형식: 문자열|사용자 속성의 버전을 지정할 수 있도록이 매개 변수를 구현 합니다.|

## <a name="see-also"></a>참고 항목

[Cmdlet 매개 변수](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell SDK](../windows-powershell-reference.md)

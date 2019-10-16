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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369582"
---
# <a name="property-parameters"></a>속성 매개 변수

다음 표에서는 속성 매개 변수의 권장 이름 및 기능을 보여 줍니다.

|매개 변수|기능|
|---|---|
|**수**<br>데이터 형식: Int32|사용자가 처리할 개체의 수를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**설명**<br>데이터 형식: 문자열|이 매개 변수를 구현 하 여 사용자가 리소스에 대 한 설명을 지정할 수 있습니다.|
|**보낸 사람**<br>데이터 형식: 문자열|사용자가 정보를 가져올 참조 개체를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**A-id**<br>데이터 형식: 리소스 종속|사용자가 리소스의 식별자를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**입력**<br>데이터 형식: 문자열|사용자가 입력 파일 사양을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**위치**<br>데이터 형식: 문자열|사용자가 리소스의 위치를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**LogName**<br>데이터 형식: 문자열|이 매개 변수를 구현 하 여 사용자가 처리 하거나 사용할 로그 파일의 이름을 지정할 수 있도록 합니다.|
|**이름의**<br>데이터 형식: 문자열|사용자가 리소스의 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**출력**<br>데이터 형식: 문자열|이 매개 변수를 구현 하 여 사용자가 출력 파일을 지정할 수 있도록 합니다.|
|**소유자도**<br>데이터 형식: 문자열|사용자가 리소스 소유자의 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**속성**<br>데이터 형식: 문자열|사용자가 사용할 속성의 이름 또는 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**문서화**<br>데이터 형식: 문자열|이 매개 변수를 구현 하 여 사용자가이 cmdlet이 호출 되는 이유를 지정할 수 있도록 합니다.|
|**Regex**<br>데이터 형식: SwitchParameter|매개 변수를 지정할 때 정규식을 사용 하도록이 매개 변수를 구현 합니다. 이 매개 변수를 지정 하면 와일드 카드 문자를 확인할 수 없습니다.|
|**빨라집니다**<br>데이터 형식: Int32|이 매개 변수를 구현 하 여 사용자가 전송 속도를 지정할 수 있도록 합니다. 사용자는이 매개 변수를 리소스의 속도로 설정 합니다.|
|**상태일**<br>데이터 형식: 키워드 배열|사용자가 KEYDOWN과 같은 상태 이름을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**기본값**<br>데이터 형식: Object|사용자가 cmdlet에 제공할 값을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**버전**<br>데이터 형식: 문자열|이 매개 변수를 구현 하 여 사용자가 속성의 버전을 지정할 수 있도록 합니다.|

## <a name="see-also"></a>참고 항목

[Cmdlet 매개 변수](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell SDK](../windows-powershell-reference.md)

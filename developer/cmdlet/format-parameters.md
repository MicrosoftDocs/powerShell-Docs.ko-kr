---
title: 매개 변수 형식 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251186"
---
# <a name="format-parameters"></a>형식 매개 변수

다음 표에서 권장 되는 이름 및 형식을 지정 하거나 데이터를 생성 하는 매개 변수에 대 한 기능을 나열 합니다.

|매개 변수|기능|
|---|---|
|**As**<br>데이터 형식: 키워드|Cmdlet 출력 형식을 지정 하려면이 매개 변수를 구현 합니다. 예를 들어 가능한 값은 텍스트 또는 스크립트 수 있습니다.|
|**이진**<br>데이터 형식: SwitchParameter|Cmdlet에서 이진 값을 처리 하는 것을 나타내려면이 매개 변수를 구현 합니다.|
|**인코딩**<br>데이터 형식: 키워드|지원 되는 인코딩 유형을 지정 하려면이 매개 변수를 구현 합니다. 예를 들어 가능한 값은 ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, 바이트 및 문자열 수 있습니다.|
|**NewLine**<br>데이터 형식: SwitchParameter|매개 변수를 지정 하는 줄 바꿈 문자를 사용할 수 있도록이 매개 변수를 구현 합니다.|
|**ShortName**<br>데이터 형식: SwitchParameter|매개 변수를 지정 하는 경우 짧은 이름을 사용할 수 있도록이 매개 변수를 구현 합니다.|
|**너비**<br>데이터 형식: Int32|사용자는 출력 장치의 너비를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**Wrap**<br>데이터 형식: SwitchParameter|매개 변수를 지정 하는 경우 텍스트 줄 바꿈을 사용할 수 있도록이 매개 변수를 구현 합니다.|
## <a name="see-also"></a>참고 항목

[Cmdlet 매개 변수](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell SDK](../windows-powershell-reference.md)

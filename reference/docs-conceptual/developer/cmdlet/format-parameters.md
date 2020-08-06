---
title: Format 매개 변수 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8e031f62aa8bcb0e9d5b900b2eace7187b1f3dd
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784285"
---
# <a name="format-parameters"></a>형식 매개 변수

다음 표에서는 데이터를 포맷 하거나 생성 하는 데 사용 되는 매개 변수의 권장 이름 및 기능을 보여 줍니다.

|매개 변수|기능|
|---|---|
|**는**<br>데이터 형식: 키워드|Cmdlet 출력 형식을 지정 하려면이 매개 변수를 구현 합니다. 예를 들어 가능한 값은 텍스트 또는 스크립트 일 수 있습니다.|
|**이진**<br>데이터 형식: SwitchParameter|Cmdlet이 이진 값을 처리 함을 나타내려면이 매개 변수를 구현 합니다.|
|**인코딩**<br>데이터 형식: 키워드|이 매개 변수를 구현 하 여 지원 되는 인코딩 유형을 지정 합니다. 예를 들어 가능한 값은 ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte 및 String 일 수 있습니다.|
|**줄**<br>데이터 형식: SwitchParameter|매개 변수를 지정할 때 줄 바꿈 문자가 지원 되도록이 매개 변수를 구현 합니다.|
|**ShortName**<br>데이터 형식: SwitchParameter|매개 변수를 지정할 때 짧은 이름이 지원 되도록이 매개 변수를 구현 합니다.|
|**Width**<br>데이터 형식: Int32|사용자가 출력 장치의 너비를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**래핑**<br>데이터 형식: SwitchParameter|매개 변수를 지정할 때 텍스트 줄 바꿈이 지원 되도록 하려면이 매개 변수를 구현 합니다.|
## <a name="see-also"></a>참고 항목

[Cmdlet 매개 변수](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)

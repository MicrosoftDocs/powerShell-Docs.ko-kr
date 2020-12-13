---
ms.date: 09/13/2016
ms.topic: reference
title: 날짜 및 시간 매개 변수
description: 날짜 및 시간 매개 변수
ms.openlocfilehash: 2f73d16ca8261ebc4ca8d2c18aff4176d7d7314c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653186"
---
# <a name="date-and-time-parameters"></a>날짜 및 시간 매개 변수

다음 표에서는 날짜 및 시간 정보를 처리 하는 매개 변수의 권장 이름 및 기능을 보여 줍니다. 날짜 및 시간 매개 변수는 일반적으로 무언가를 만들거나 액세스할 때 기록 하는 데 사용 됩니다.

|매개 변수|기능|
|---|---|
|**날짜**<br>데이터 형식: SwitchParameter|지정 된 경우 cmdlet은 **Before** 및 **After** 매개 변수로 지정 된 날짜 및 시간을 기반으로 액세스 된 리소스에 대해 작동 하도록이 매개 변수를 구현 합니다. 이 매개 변수를 지정 하는 경우 **생성** 된 매개 변수 및 **수정** 된 매개 변수를 지정 하지 않아야 합니다.|
|**업데이트 후**<br>데이터 형식: DateTime|이 매개 변수를 구현 하 여 cmdlet이 사용 된 날짜와 시간을 지정 합니다. **After** 매개 변수가 작동 하려면 cmdlet에도 **액세스**, **생성** 또는 **수정** 된 매개 변수가 있어야 합니다. Cmdlet을 호출 하는 경우이 매개 변수를 **true** 로 설정 해야 합니다.|
|**업데이트 전**<br>데이터 형식: DateTime|이 매개 변수를 구현 하 여 cmdlet이 사용 된 날짜와 시간을 지정 합니다. **Before** 매개 변수가 작동 하려면 Cmdlet에 **액세스**, **생성** 또는 **수정** 된 매개 변수도 있어야 합니다. Cmdlet을 호출 하는 경우이 매개 변수를 **true** 로 설정 해야 합니다.|
|**만든 날짜**<br>데이터 형식: SwitchParameter|지정 된 경우 cmdlet은 **Before** 및 **After** 매개 변수로 지정 된 날짜 및 시간을 기준으로 만들어진 리소스에 대해 작동 하도록이 매개 변수를 구현 합니다. 이 매개 변수를 지정 하면 **액세스** 및 **수정** 된 매개 변수를 지정 하지 않아야 합니다.|
|**Exact**<br>데이터 형식: SwitchParameter|지정 된 경우 리소스 용어와 리소스 이름이 정확히 일치 해야 하도록이 매개 변수를 구현 합니다. 매개 변수를 지정 하지 않으면 리소스 용어와 이름이 정확히 일치 하지 않아도 됩니다.|
|**수정한 날짜**<br>데이터 형식: DateTime|지정 된 경우 cmdlet은 **Before** 및 **After** 매개 변수로 지정 된 날짜 및 시간을 기반으로 변경 된 리소스에서 작동 하도록이 매개 변수를 구현 합니다. 이 매개 변수를 지정 하면 **액세스** 및 **만든** 매개 변수를 지정 하지 않아야 합니다.|
## <a name="see-also"></a>참고 항목

[Cmdlet 매개 변수](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell SDK](../windows-powershell-reference.md)

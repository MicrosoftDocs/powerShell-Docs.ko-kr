---
title: 날짜 및 시간 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251356"
---
# <a name="date-and-time-parameters"></a>날짜 및 시간 매개 변수

다음 표에서 권장 되는 이름 및 날짜와 시간 정보를 처리 하는 매개 변수에 대 한 기능을 나열 합니다. 날짜 및 시간 매개 변수는 일반적으로 무언가 만들거나 액세스할 때를 기록 하기 위해 사용 됩니다.

|매개 변수|기능|
|---|---|
|**Accessed**<br>데이터 형식: SwitchParameter|날짜 및 지정 된 시간에 따라 cmdlet에 액세스 하는 리소스에 작동 합니다. 지정 된 경우이 매개 변수를 구현 합니다 **하기 전에** 하 고 **후** 매개 변수입니다. 이 매개 변수를 지정 하는 경우는 **Created** 및 **Modified** 매개 변수 여야 합니다 지정할 수 없습니다.|
|**After**<br>데이터 형식: DateTime|날짜 및 되기까지의 cmdlet 사용 된 시간을 지정 하려면이 매개 변수를 구현 합니다. 에 대 한 합니다 **후** 하려면 매개 변수 cmdlet도 있어야는 **액세스**, **생성**, 또는 **Modified** 매개 변수입니다. 및 해당 매개 변수를 설정 해야 합니다 **true** cmdlet를 호출할 때.|
|**전에**<br>데이터 형식: DateTime|날짜 및 되기까지의 cmdlet 사용 된 시간을 지정 하려면이 매개 변수를 구현 합니다. 에 대 한 합니다 **하기 전에** 하려면 매개 변수 cmdlet도 있어야를 **액세스**, **생성**, 또는 **수정** 매개 변수입니다. 및 해당 매개 변수를 설정 해야 합니다 **true** cmdlet를 호출할 때.|
|**생성**<br>데이터 형식: SwitchParameter|날짜 및 지정 된 시간에 따라 cmdlet은 생성 된 리소스에 작동 합니다. 지정 된 경우이 매개 변수를 구현 합니다 **하기 전에** 하 고 **후** 매개 변수입니다. 이 매개 변수를 지정 합니다 **액세스** 및 **Modified** 매개 변수는 지정 하지 않아야 합니다.|
|**정확한**<br>데이터 형식: SwitchParameter|리소스 라는 용어가 지정 된 경우 리소스 이름의 정확 하 게 일치 해야이 매개 변수를 구현 합니다. 매개 변수를 지정 하지 않으면 리소스 용어와 이름이 필요가 없습니다 정확 하 게 일치 합니다.|
|**수정**<br>데이터 형식: DateTime|날짜 및 지정 된 시간에 따라 cmdlet 변경 된 리소스에 작동 합니다. 지정 된 경우이 매개 변수를 구현 합니다 **하기 전에** 하 고 **후** 매개 변수입니다. 이 매개 변수를 지정 하는 경우는 **액세스** 하 고 **생성** 매개 변수는 지정 하지 않아야 합니다.|
## <a name="see-also"></a>참고 항목

[Cmdlet 매개 변수](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell SDK](../windows-powershell-reference.md)

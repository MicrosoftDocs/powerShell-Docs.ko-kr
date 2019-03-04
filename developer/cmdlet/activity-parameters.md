---
title: 활동 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251220"
---
# <a name="activity-parameters"></a>활동 매개 변수

다음 표에서 권장 되는 이름 및 작업 매개 변수에 대 한 기능을 나열합니다.

|매개 변수|기능|
|---|---|
|**추가**<br>데이터 형식: SwitchParameter|매개 변수를 지정 하는 경우 사용자는 리소스의 끝에 내용을 추가할 수 있도록이 매개 변수를 구현 합니다.|
|**CaseSensitive**<br>데이터 형식: SwitchParameter|이 매개 변수를 구현 하는 매개 변수를 지정 하는 경우 사용자가 대/소문자 구분을 요구할 수 있습니다.|
|**Command**<br>데이터 형식: 문자열|이 매개 변수를 구현 하 여 실행 하려면 명령 문자열을 지정할 수 있습니다.|
|**CompatibleVersion**<br>데이터 형식: System.Version 개체|사용자는 cmdlet은 이전 버전과 호환성에 대 한 호환 되어야 하는 의미 체계를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**압축**<br>데이터 형식: SwitchParameter|이 매개 변수를 구현 하는 매개 변수를 지정 하는 경우 데이터 압축을 사용 합니다.|
|**압축**<br>데이터 형식: 키워드|사용자는 데이터 압축에 사용할 알고리즘을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**연속**<br>데이터 형식: SwitchParameter|사용자는 매개 변수를 지정 하는 경우 cmdlet은 종료 될 때까지 데이터를 처리 하므로이 매개 변수를 구현 합니다. 매개 변수를 지정 하지 않으면 cmdlet 미리 정의 된 양의 데이터를 처리 하 고 작업을 종료 합니다.|
|**만들기**<br>데이터 형식: SwitchParameter|이미 없는 매개 변수를 지정 하는 경우 리소스를 만든 것을 나타내려면이 매개 변수를 구현 합니다.|
|**Delete**<br>데이터 형식: SwitchParameter|Cmdlet 매개 변수를 지정 하는 경우 해당 작업이 완료 될 때 리소스가 삭제 됩니다 있도록이 매개 변수를 구현 합니다.|
|**드레이닝**<br>데이터 형식: SwitchParameter|이 매개 변수는 매개 변수를 지정 하는 경우 cmdlet은 새 데이터를 처리 하기 전에 처리 중인 작업 항목은 처리를 구현 합니다. 매개 변수를 지정 하지 않으면 작업 항목을 즉시 처리 됩니다.|
|**지우기**<br>데이터 형식: Int32|사용자 리소스는 삭제 되기 전에 지워집니다 횟수를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**ErrorLevel**<br>데이터 형식: Int32|사용자는 보고서에는 오류 수준을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**제외**<br>데이터 형식: String[]|사용자 활동에서 무언가 제외할 수 있도록이 매개 변수를 구현 합니다. 입력된 필터를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [필터 매개 변수 입력](input-filter-parameters.md)합니다.|
|**Assert**<br>데이터 형식: 키워드|사용자는 cmdlet은 작업을 수행 하는 리소스를 선택 하는 필터를 지정할 수 있도록이 매개 변수를 구현 합니다. 입력된 필터를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [필터 매개 변수 입력](./input-filter-parameters.md)합니다.|
|**에 따라**<br>데이터 형식: SwitchParameter|매개 변수를 지정 하는 경우 진행률 추적 됩니다 있도록이 매개 변수를 구현 합니다.|
|**Force**<br>데이터 형식: SwitchParameter|이 매개 변수는 매개 변수를 지정 하는 경우 제한이 발생 하는 경우에 사용자 작업을 수행할 수 있는지를 구현 합니다. 매개 변수는 손상 된 것으로 보안을 허용 하지 않습니다. 예를 들어이 매개 변수는 읽기 전용 파일을 덮어쓸지 사용자 수 있습니다.|
|**포함**<br>데이터 형식: String[]|사용자 활동에 무언가 포함할 수 있도록이 매개 변수를 구현 합니다. 입력된 필터를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [필터 매개 변수 입력](input-filter-parameters.md)합니다.|
|**증분**<br>데이터 형식: SwitchParameter|이 매개 변수는 매개 변수를 지정 하는 경우 처리는 증분 방식으로 수행 했음을 나타내면를 구현 합니다. 예를 들어이 매개 변수는 사용자를 마지막 백업 이후에 파일을 백업 하는 증분 백업을 수행할 수 있습니다.|
|**InputObject**<br>데이터 형식: 개체|Cmdlet는 다른 cmdlet에서 입력을 사용 하는 경우이 매개 변수를 구현 합니다. 정의 하는 경우는 **InputObject** 매개 변수를 항상 지정 합니다 **ValueFromPipeline** 키워드를 선언 하는 경우는 **매개 변수** 특성입니다. 입력된 필터를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [필터 매개 변수 입력](./input-filter-parameters.md)합니다.|
|**삽입**<br>데이터 형식: SwitchParameter|Cmdlet 매개 변수를 지정 하는 경우 항목을 삽입 되도록이 매개 변수를 구현 합니다.|
|**대화형**<br>데이터 형식: SwitchParameter|매개 변수는 지정 된 사용자를 사용 하 여 cmdlet을 대화형으로 작동할 수 있도록이 매개 변수를 구현 합니다.|
|**간격**<br>데이터 형식: HashTable|사용자는 값이 포함 된 키워드의 해시 테이블을 지정할 수 있도록이 매개 변수를 구현 합니다. 다음 예제에서는 샘플 값을 **간격** 매개 변수: `-interval @{ResumeScan=15; Retry=3}`합니다.|
|**Log**<br>데이터 형식: SwitchParameter|매개 변수를 지정 하는 경우이 매개 변수 감사 cmdlet의 작업을 구현 합니다.|
|**NoClobber**<br>데이터 형식: SwitchParameter|매개 변수를 지정 하는 경우 리소스를 덮어쓸 수는이 매개 변수를 구현 합니다. 이 매개 변수는 일반적으로 동일한 이름을 가진 기존 개체를 덮어쓰지 방지할 수 있도록 새 개체를 만드는 cmdlet에 적용 됩니다.|
|**Notify**<br>데이터 형식: SwitchParameter|사용자는 매개 변수를 지정 하는 경우 작업이 완료 된 알림을 받을 수 있도록이 매개 변수를 구현 합니다.|
|**NotifyAddress**<br>데이터 형식: 메일 주소|사용자를 사용 하는 알림을 보내는 전자 메일 주소를 지정할 수 있도록이 매개 변수를 구현할 때를 **알림** 매개 변수를 지정 합니다.|
|**덮어쓰기**<br>데이터 형식: SwitchParameter|Cmdlet 매개 변수를 지정 하는 경우 모든 기존 데이터를 덮어쓰는 있도록이 매개 변수를 구현 합니다.|
|**Prompt**<br>데이터 형식: 문자열|사용자는 cmdlet에 대 한 프롬프트를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**자동**<br>데이터 형식: SwitchParameter|Cmdlet 매개 변수를 지정 하는 경우 해당 작업 하는 동안 사용자 피드백을 억제 있도록이 매개 변수를 구현 합니다.|
|**Recurse**<br>데이터 형식: SwitchParameter|이 매개 변수를 구현 하는 cmdlet을 재귀적으로 매개 변수를 지정 하는 경우 리소스에 해당 작업을 수행 합니다.|
|**복구**<br>데이터 형식: SwitchParameter|Cmdlet 매개 변수를 지정 하는 경우 손상 된 상태에서 항목을 수정 하려고 합니다.이 매개 변수를 구현 합니다.|
|**RepairString**<br>데이터 형식: 문자열|사용 하는 문자열을 지정할 수 있도록이 매개 변수를 구현 합니다 **복구** 매개 변수를 지정 합니다.|
|**Retry**<br>데이터 형식: Int32|사용자는 cmdlet에서 작업을 시도 하는 횟수를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**Select**<br>데이터 형식: 키워드 배열|사용자는 항목의 형식 배열을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**Stream**<br>데이터 형식: SwitchParameter|사용자는 매개 변수를 지정 하는 경우 파이프라인을 통해 여러 출력 개체를 스트리밍할 수 있도록이 매개 변수를 구현 합니다.|
|**Strict**<br>데이터 형식: SwitchParameter|매개 변수를 지정 하는 경우 모든 오류 종료 오류로 처리할 수 있도록이 매개 변수를 구현 합니다.|
|**TempLocation**<br>데이터 형식: 문자열|사용자는 cmdlet의 작업 중 사용 되는 임시 데이터의 위치를 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**Timeout**<br>데이터 형식: Int32|사용자는 제한 시간 간격 (밀리초)을 지정할 수 있도록이 매개 변수를 구현 합니다.|
|**Truncate**<br>데이터 형식: SwitchParameter|Cmdlet 매개 변수를 지정 하는 경우 해당 작업 잘립니다 있도록이 매개 변수를 구현 합니다. 매개 변수를 지정 하지 않으면 cmdlet은 다른 작업을 수행 합니다.|
|**Verify**<br>데이터 형식: SwitchParameter|Cmdlet은 작업 매개 변수를 지정 하는 경우에 발생 했는지 여부를 확인 하려면 테스트 되도록이 매개 변수를 구현 합니다.|
|**대기**<br>데이터 형식: SwitchParameter|Cmdlet 매개 변수를 지정 하는 경우 계속 하기 전에 사용자 입력에 대해 대기할 수 있도록이 매개 변수를 구현 합니다.
|**WaitTime**<br>데이터 형식: Int32|사용자 기간 (초)을 지정할 수 있도록이 매개 변수를 구현할 때 입력 cmdlet은 사용자에 대 한 대기 함을 합니다 **대기** 매개 변수를 지정 합니다.|

## <a name="see-also"></a>참고 항목

[Cmdlet 매개 변수](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell SDK](../windows-powershell-reference.md)

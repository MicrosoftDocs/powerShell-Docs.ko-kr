---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085799"
---
# <a name="detailed-information-about-lcm-state"></a>LCM 상태에 대한 자세한 정보

LCM 상태에 대한 세부 정보를 노출하는 기능이 향상되었습니다. 이제 Get-DscLocalConfigurationManager에서 반환되는 LCMState에 다음과 같은 값이 포함될 수 있습니다.

* **유휴 상태**
* **사용 중**
* **PendingReboot**
* **PendingConfiguration**

또한 상태에 대한 자세한 정보를 포함하는 LCMStateDetail 속성이 추가되었습니다.

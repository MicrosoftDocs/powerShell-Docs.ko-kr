---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682538"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>RefreshMode 및 ConfigurationMode의 빈도가 서로의 배수일 필요가 없음

이전 버전의 DSC에서 LCM은 `RefreshFrequencyMins` 및 `ConfigurationModeFrequencyMins`를 서로의 배수로 처리합니다. WMF 5.0 RTM에서 이러한 속성은 서로 독립적으로 처리됩니다.

자세한 내용은 [로컬 구성 관리자 구성](https://msdn.microsoft.com/powershell/dsc/metaconfig)을 참조하세요.

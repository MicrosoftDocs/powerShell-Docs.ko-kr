---
description: Powershell을 시작할 때 새 버전의 PowerShell이 출시 되었음을 사용자에 게 알립니다.
Locale: en-US
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Update_Notifications
ms.openlocfilehash: 1a9f8cfec15f83566fdb77175dcc1aed6d9e8c34
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602239"
---
# <a name="about-update-notifications"></a>업데이트 알림 정보

## <a name="short-description"></a>간단한 설명

Powershell을 시작할 때 새 버전의 PowerShell이 출시 되었음을 사용자에 게 알립니다.

## <a name="long-description"></a>자세한 설명

Powershell 7.0부터 powershell은 업데이트 알림을 사용 하 여 PowerShell에 대 한 업데이트가 있음을 사용자에 게 알립니다. PowerShell은 하루 한 번 온라인 서비스를 쿼리하여 최신 버전을 사용할 수 있는지 확인합니다.

> [!NOTE]
> 업데이트 확인은 지정 된 24 시간 동안 첫 번째 세션 중에 발생 하지만 성능상의 이유로 알림은 후속 세션의 시작 부분에만 표시 됩니다. 또한 성능상의 이유로 세션이 시작 될 때까지 3 초 이상이 지나면 검사가 시작 되지 않습니다.

기본적으로 PowerShell은 버전/분기에 따라 두 가지 알림 채널 중 하나를 구독합니다. 지원되는 GA(일반 공급) 버전의 PowerShell은 업데이트된 GA 릴리스에 대한 알림만 반환합니다. 미리 보기 및 RC(릴리스 후보) 릴리스는 미리 보기, RC 및 GA 릴리스에 대한 업데이트 알림을 제공합니다.

업데이트 알림 동작은 `POWERSHELL_UPDATECHECK` 환경 변수를 사용하여 변경할 수 있습니다. 지원되는 값은 다음과 같습니다.

- `Off` 업데이트 알림 기능을 끕니다.
- `Default` 는 정의와 동일 합니다 `POWERSHELL_UPDATECHECK` .
  - GA 릴리스는 GA 릴리스 업데이트를 알림
  - 미리 보기/RC 릴리스는 GA 및 미리 보기 릴리스 업데이트를 알림
- `LTS` LTS (장기 서비스) GA 릴리스에 대 한 업데이트 알림

다음 끝점은 현재 각 채널의 최신 버전을 확인 하는 데 사용 됩니다.

- `LTS`: https://aka.ms/pwsh-buildinfo-lts
- `Stable`: https://aka.ms/pwsh-buildinfo-stable
- `Preview`: https://aka.ms/pwsh-buildinfo-preview

업데이트 알림은 PowerShell을 자동으로 업데이트 하는 방법을 제공 하지 않습니다. 나중에 PowerShell 내에서 업데이트할 추가 지침이 나 기능이 있을 수 있지만, 현재는 PowerShell을 설치 하는 데 사용한 것과 동일한 설치 메커니즘을 사용 하 여 업데이트 해야 합니다.


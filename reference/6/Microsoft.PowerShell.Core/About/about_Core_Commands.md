---
description: PowerShell 공급자와 함께 사용 하도록 디자인 된 cmdlet을 나열 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: d02067bca8f66c61a66ff121521a49668f32d839
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221714"
---
# <a name="about-core-commands"></a>핵심 명령 정보

## <a name="short-description"></a>간단한 설명
PowerShell 공급자와 함께 사용 하도록 디자인 된 cmdlet을 나열 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell에는 PowerShell 공급자가 제공 하는 데이터 저장소의 항목을 관리 하도록 특별히 설계 된 cmdlet 집합이 포함 되어 있습니다.
이러한 cmdlet을 동일한 방법으로 사용 하 여 공급자가 제공 하는 다양 한 유형의 데이터를 관리할 수 있습니다. 공급자에 대 한 자세한 내용을 보려면 "get-help about_providers"를 입력 하십시오.

예를 들어 Get-ChildItem cmdlet을 사용 하 여 파일 시스템 디렉터리, 레지스트리 키 아래의 키 또는 사용자가 쓰거나 다운로드 하는 공급자가 노출 하는 항목을 나열할 수 있습니다.

다음은 공급자와 함께 사용 하도록 디자인 된 PowerShell cmdlet의 목록입니다.

ChildItem cmdlet

- Get-ChildItem

콘텐츠 cmdlet

- Add-Content
- Clear-Content
- Get-Content
- Set-Content

항목 cmdlet

- Clear-Item
- Copy-Item
- Get-Item
- Invoke-Item
- Move-Item
- New-Item
- Remove-Item
- Rename-Item
- Set-Item

Get-itemproperty cmdlet

- Clear-ItemProperty
- Copy-ItemProperty
- Get-ItemProperty
- Move-ItemProperty
- New-ItemProperty
- Remove-ItemProperty
- Rename-ItemProperty
- Set-ItemProperty

위치 cmdlet

- Get-Location
- Pop-Location
- Push-Location
- Set-Location

경로 cmdlet

- Join-Path
- Convert-Path
- Split-Path
- Resolve-Path
- Test-Path

PSDrive cmdlet

- Get-PSDrive
- New-PSDrive
- Remove-PSDrive

PSProvider cmdlet

- Get-PSProvider

Cmdlet에 대 한 자세한 내용을 보려면를 입력 하십시오 `get-help <cmdlet-name>` .

## <a name="see-also"></a>참고 항목

[about_Providers](about_Providers.md)

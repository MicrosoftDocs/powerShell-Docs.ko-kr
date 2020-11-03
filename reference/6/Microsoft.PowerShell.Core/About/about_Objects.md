---
description: PowerShell의 개체에 대 한 필수 정보를 제공 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_objects?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Objects
ms.openlocfilehash: 152234de5e4f55f63b70ee9775bba0c5c9977f84
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221466"
---
# <a name="about-objects"></a>개체 정보

## <a name="short-description"></a>간단한 설명
PowerShell의 개체에 대 한 필수 정보를 제공 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell에서 수행 하는 모든 작업은 개체의 컨텍스트 내에서 발생 합니다. 데이터를 한 명령에서 다음 명령으로 이동 하면 하나 이상의 식별 가능한 개체로 이동 합니다. 그런 다음 개체는 항목을 나타내는 데이터의 컬렉션입니다. 개체는 세 가지 유형의 데이터 즉, 개체 형식, 해당 메서드 및 속성으로 구성 됩니다.

## <a name="types-methods-and-properties"></a>형식, 메서드 및 속성

개체 형식은 개체의 종류를 알려 줍니다. 예를 들어 파일을 나타내는 개체는 FileInfo 개체입니다.

개체 메서드는 개체에 대해 수행할 수 있는 작업입니다.
예를 들어, FileInfo 개체에는 파일을 복사 하는 데 사용할 수 있는 CopyTo 메서드가 있습니다.

개체 속성은 개체에 대 한 정보를 저장 합니다. 예를 들어, FileInfo 개체에는 파일에 가장 최근에 액세스 한 날짜와 시간을 저장 하는 LastWriteTime 속성이 있습니다.

개체를 사용 하는 경우 명령에서 해당 메서드 및 속성을 사용 하 여 작업을 수행 하 고 데이터를 관리할 수 있습니다.

## <a name="objects-in-pipelines"></a>파이프라인의 개체

파이프라인에서 명령을 결합 하면 서로 정보를 개체로 전달 합니다. 첫 번째 명령이 실행 될 때 파이프라인에서 하나 이상의 개체를 두 번째 명령으로 보냅니다. 두 번째 명령은 첫 번째 명령에서 개체를 받아서 처리 한 다음 새 개체 또는 수정 된 개체를 파이프라인의 다음 명령에 전달 합니다.
파이프라인의 모든 명령이 실행 될 때까지 계속 됩니다.

다음 예제에서는 개체가 한 명령에서 다음 명령으로 전달 되는 방법을 보여 줍니다.

```powershell
Get-ChildItem C: | where { $_.PsIsContainer -eq $false } | Format-List
```

첫 번째 명령은 `Get-ChildItem C:` 파일 시스템의 루트 디렉터리에 있는 각 항목에 대 한 파일 또는 디렉터리 개체를 반환 합니다. 파일 및 디렉터리 개체는 파이프라인에서 두 번째 명령으로 전달 됩니다.

두 번째 명령은 `where { $_.PsIsContainer -eq $false }` 모든 파일 시스템 개체의 PsIsContainer 속성을 사용 하 여 PsIsContainer 속성에 false (false) 값이 있는 파일만 선택 합니다 \$ . 컨테이너 이며, 따라서 PsIsContainer 속성에 True (true) 값이 있는 폴더는 \$ 선택 되지 않습니다.

두 번째 명령은 파일 개체만 목록의 파일 개체를 표시 하는 세 번째 명령에 전달 합니다 `Format-List` .

## <a name="see-also"></a>참고 항목

[about_Methods](about_Methods.md)

[about_Object_Creation](about_Object_Creation.md)

[about_Properties](about_Properties.md)

[about_Pipelines](about_Pipelines.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)

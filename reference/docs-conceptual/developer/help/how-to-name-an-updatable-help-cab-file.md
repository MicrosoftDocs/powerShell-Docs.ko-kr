---
title: 업데이트할 수 있는 도움말 CAB 파일의 이름을로 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: a253f98d213f797a659affb1560907bb99a045d3
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811702"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>업데이트 가능한 도움말 CAB 파일 이름을 지정하는 방법

이 항목에서는 업데이트할 수 있는 도움말 캐비닛 ()의 필수 이름 형식에 대해 설명 합니다. CAB) 파일.

## <a name="how-to-name-an-updatable-help-cab-file"></a>업데이트 가능한 도움말 CAB 파일 이름을 지정하는 방법

업데이트 가능한 캐비닛 (. CAB) 파일의 이름은 다음과 같은 형식 이어야 합니다.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

이름의 요소는 다음과 같습니다.

ModuleName [import-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet이 반환 하는 **Moduleinfo** 개체의 **Name** 속성 값입니다.

ModuleGUID 모듈 매니페스트의 **guid** 키 값입니다.

UICulture는 CAB 파일의 도움말 파일에 대 한 UI 문화권을 유지 합니다. 이 값은 모듈에 대 한 HelpInfo XML 파일의 **UICulture** 요소 중 하나의 값과 일치 해야 합니다.

예를 들어 모듈 이름이 "TestModule"이 고 모듈 GUID가 9cabb9ad-4914-a46b-bfc1bebf07f9이 고 UI 문화권이 "en-us" 이면 CAB 파일의 이름은 다음과 같습니다.

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`

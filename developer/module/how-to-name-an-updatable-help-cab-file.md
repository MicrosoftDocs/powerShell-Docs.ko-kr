---
title: 업데이트할 수 있는 도움말 CAB 파일 이름을 지정 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794760"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>업데이트 가능한 도움말 CAB 파일 이름을 지정하는 방법

이 항목에서는 필수 이름 형식을 업데이트할 수 있는 도움말 캐비닛에 대 한 설명 (합니다. CAB) 파일입니다.

## <a name="how-to-name-an-updatable-help-cab-file"></a>업데이트 가능한 도움말 CAB 파일 이름을 지정하는 방법

업데이트할 수 있는 캐비닛 (합니다. CAB) 파일에는 다음 형식으로 이름이 있어야 합니다.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

이름의 요소는 다음과 같습니다.

ModuleName 값의를 **이름** 의 속성을 **ModuleInfo** 개체를 [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet이 반환.

ModuleGUID 값의 합니다 **GUID** 모듈 매니페스트 키입니다.

CAB 파일에 있는 도움말 파일의 UICulture UI culture입니다. 이 값 중 하나의 값과 일치 해야 합니다 **UICulture** 모듈에 대 한 HelpInfo XML 파일의 요소입니다.

예를 들어 모듈 이름을 "TestModule" 인 경우 모듈 GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, 하며 UI 문화권이 "EN-US", CAB 파일의 이름이 표시 됩니다.

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
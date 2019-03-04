---
title: HelpInfo XML 파일의 이름을 지정 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: a3e8ae664d5c0e29d0f84174950bebe6a1da6a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857829"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>HelpInfo XML 파일 이름을 지정하는 방법

이 항목에서는 HelpInfo XML 파일 이라는 일반적으로 업데이트할 수 있는 도움말 정보 파일에 대 한 필수 이름 형식에 설명 합니다.

## <a name="how-to-name-a-helpinfo-xml-file"></a>HelpInfo XML 파일 이름을 지정하는 방법

HelpInfo XML 파일을 다음 형식으로 이름이 있어야 합니다.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

이름의 요소는 다음과 같습니다.

ModuleName 값의를 **이름** 의 속성을 **ModuleInfo** 개체를 [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet이 반환.
값을 **이름** 의 속성을 **ModuleInfo** 개체를 [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet을 반환 합니다.

ModuleGUID 값의 합니다 **GUID** 모듈 매니페스트 키입니다.

예를 들어, 모듈 이름 "TestModule" 이며 모듈 GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, 하는 경우 모듈에 대 한 HelpInfo XML 파일의 이름을 다음과 같습니다.

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
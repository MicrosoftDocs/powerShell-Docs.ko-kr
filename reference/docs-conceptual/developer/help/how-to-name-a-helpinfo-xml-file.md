---
ms.date: 09/12/2016
ms.topic: reference
title: HelpInfo XML 파일 이름을 지정하는 방법
description: HelpInfo XML 파일 이름을 지정하는 방법
ms.openlocfilehash: 55bc2ef9530fc457e4d9ddf18e79e7226c991663
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659039"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>HelpInfo XML 파일 이름을 지정하는 방법

이 항목에서는 일반적으로 HelpInfo XML 파일 이라고 하는 업데이트할 수 있는 도움말 정보 파일의 필수 이름 형식에 대해 설명 합니다.

## <a name="how-to-name-a-helpinfo-xml-file"></a>HelpInfo XML 파일 이름을 지정하는 방법

HelpInfo XML 파일의 이름은 다음과 같은 형식 이어야 합니다.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

이름의 요소는 다음과 같습니다.

- `<ModuleName>`- [Import-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet이 반환 하는 **Moduleinfo** 개체의 **Name** 속성 값입니다.

- `<ModuleGUID>` -모듈 매니페스트의 **GUID** 키 값입니다.

예를 들어 모듈 이름이 "TestModule"이 고 모듈 GUID가 9cabb9ad-4914-a46b-bfc1bebf07f9 인 경우 모듈의 HelpInfo XML 파일 이름은 다음과 같습니다.

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`

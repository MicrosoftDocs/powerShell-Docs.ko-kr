---
ms.date: 08/25/2017
keywords: powershell,cmdlet
title: ObjectModelRoot 개체
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086785"
---
# <a name="the-objectmodelroot-object"></a>ObjectModelRoot 개체

Windows PowerShell® ISE(통합 스크립팅 환경)의 주 루트 개체인 **$psISE** 개체는 Microsoft.PowerShell.Host.ISE.ObjectModelRoot 클래스의 인스턴스입니다.
이 항목에서는 **ObjectModelRoot** 개체의 속성을 설명합니다.

## <a name="properties"></a>속성

### <a name="currentfile"></a>CurrentFile

> Windows PowerShell ISE 2.0 이상에서 지원됩니다.

현재 포커스가 있는 이 호스트 개체와 연결된 파일을 가져오는 읽기 전용 속성입니다.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Windows PowerShell ISE 2.0 이상에서 지원됩니다.

포커스가 있는 PowerShell 탭을 가져오는 읽기 전용 속성입니다.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Windows PowerShell ISE 2.0 이상에서 지원됩니다.

편집기의 맨 아래에 있는 수평 도구 창에 위치한 현재 표시되는 Windows PowerShell ISE 추가 기능 도구를 가져오는 읽기 전용 속성입니다.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Windows PowerShell ISE 2.0 이상에서 지원됩니다.

편집기의 오른쪽에 있는 수직 도구 창에 위치한 현재 표시되는 Windows PowerShell ISE 추가 기능 도구를 가져오는 읽기 전용 속성입니다.

### <a name="options"></a>옵션

> Windows PowerShell ISE 2.0 이상에서 지원됩니다.

Windows PowerShell ISE에서 설정을 변경할 수 있는 다양한 옵션을 가져오는 읽기 전용 속성입니다.

### <a name="powershelltabs"></a>PowerShellTabs

> Windows PowerShell ISE 2.0 이상에서 지원됩니다.

Windows PowerShell ISE에서 열려 있는 PowerShell 탭의 컬렉션을 가져오는 읽기 전용 속성입니다. 기본적으로 이 개체는 하나의 PowerShell 탭을 포함합니다. 그러나 스크립트를 사용하거나 Windows PowerShell ISE의 메뉴를 사용하여 이 개체에 더 많은 PowerShell 탭을 추가할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [Windows PowerShell ISE 스크립팅 개체 모델의 용도](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 개체 모델 계층 구조](The-ISE-Object-Model-Hierarchy.md)
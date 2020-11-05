---
ms.date: 07/08/2020
keywords: dsc,powershell,configuration,setup
title: 사용자 지정 Windows PowerShell 필요한 상태 구성 리소스 빌드
description: 이 문서에서는 리소스 개발의 개요와 특정 정보 및 예제가 있는 문서에 대한 링크를 제공합니다.
ms.openlocfilehash: ff9a0c8ae10583155217fbeccc62e6e1c94f9a11
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656404"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>사용자 지정 Windows PowerShell 필요한 상태 구성 리소스 빌드

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC(필요한 상태 구성)은 환경을 구성하는 데 사용할 수 있는 기본 제공 리소스를 포함합니다. 이 문서에서는 리소스 개발의 개요와 특정 정보 및 예제가 있는 문서에 대한 링크를 제공합니다.

## <a name="dsc-resource-components"></a>DSC 리소스 구성 요소

DSC 리소스는 Windows PowerShell 모듈입니다. 모듈에는 리소스에 대한 스키마(구성 가능한 속성 정의)와 구현(구성으로 지정한 실제 작업을 수행하는 코드)이 모두 들어 있습니다. DSC 리소스 스키마는 MOF 파일에 정의할 수 있으며, 구현은 스크립트 모듈에 의해 수행됩니다. 버전 5에 있는 PowerShell 클래스의 지원으로 시작하여, 스키마와 구현은 클래스에서 모두 정의할 수 있습니다. 다음 문서에서는 DSC 리소스를 만드는 방법을 자세히 설명합니다.

- [Writing a custom DSC resource with MOF(MOF를 사용하여 사용자 지정 DSC 리소스 작성)](authoringResourceMOF.md)
- [Implementing a DSC resource in C#(C#에서 DSC 리소스 구현)](authoringResourceMofCS.md)
- [PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성](authoringResourceClass.md)
- [복합 리소스: DSC 구성을 자원으로 사용](authoringResourceComposite.md)
- [Using the Resource Designer tool(리소스 디자이너 도구 사용)](authoringResourceMofDesigner.md)

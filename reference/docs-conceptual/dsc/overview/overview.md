---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Windows PowerShell 필요한 상태 구성 개요
ms.openlocfilehash: 5c4853cb059ca0cf063a9450f97230732bc56b10
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953640"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Windows PowerShell 필요한 상태 구성 개요

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC는 PowerShell에서 코드로 된 구성을 사용하여 IT 및 개발 인프라를 관리할 수 있게 해 주는 관리 플랫폼입니다.

- DSC를 사용하여 비즈니스에서 얻을 수 있는 이점은 [의사 결정자를 위한 필요한 상태 구성 개요](decisionMaker.md)를 참조하세요.
- DSC를 사용하여 엔지니어링에서 얻을 수 있는 이점은 [엔지니어를 위한 필요한 상태 구성 개요](DscForEngineers.md)를 참조하세요.
- 빨리 DSC를 사용하기 시작하려면 [DSC 빠른 시작](../quickstarts/website-quickstart.md)을 참조하세요.

## <a name="key-concepts"></a>주요 개념

DSC는 시스템의 구성, 배포 및 관리에 사용되는 선언적 플랫폼입니다. 이것은 세 가지 기본 요소로 구성됩니다.

- [구성](../configurations/configurations.md)은 리소스의 인스턴스를 정의 및 구성하는 선언적 PowerShell 스크립트입니다.
    구성 실행 시, DSC(및 구성에 의해 호출되는 리소스)는 시스템이 구성에 의해 배치된 상태로 존재하도록 단순히 "그대로 수행"하게 됩니다.
    또한 DSC 구성은 idempotent입니다. LCM(로컬 구성 관리자)은 구성에서 선언하는 상태가 무엇이든 계속 컴퓨터가 해당 상태로 구성되어 있도록 합니다.
- [리소스](../resources/resources.md)는 DSC에서 "실행을 맡는" 부분입니다. 구성의 대상을 지정된 상태에 놓고 유지하는 코드가 여기에 포함되어 있습니다.
    리소스는 PowerShell 모듈 내에 상주하며, 파일이나 Windows 프로세스만큼 일반적이거나 Azure에서 실행되는 IIS 서버 또는 VM만큼 특별한 것을 모델링하도록 작성할 수 있습니다.
- [LCM(로컬 구성 관리자)](../managing-nodes/metaConfig.md)은 DSC에서 리소스와 구성 간 상호 작용을 이용할 때 사용하는 엔진입니다.
    LCM은 리소스가 구현한 제어 흐름을 사용하여 구성으로 정의된 상태를 유지하도록 시스템을 정기적으로 폴링합니다.
    시스템이 상태를 벗어나면 LCM은 리소스에 있는 코드를 호출하여 구성에 따라 “그대로 수행”하게 됩니다.

## <a name="see-also"></a>참고 항목

- [DSC 구성](../configurations/configurations.md)
- [DSC 리소스](../resources/resources.md)
- [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md)

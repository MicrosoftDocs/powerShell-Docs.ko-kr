---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 의사 결정자를 위한 필요한 상태 구성 개요
ms.openlocfilehash: ce554d4bb994d4b1816d9d9c24599e4ef0e1c593
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402447"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>의사 결정자를 위한 필요한 상태 구성 개요

이 문서에서는 Windows PowerShell DSC(필요한 상태 구성)를 사용하는 비즈니스 혜택에 대해 설명합니다. 기술 가이드가 아닙니다.

## <a name="what-is-desired-state-configuration"></a>필요한 상태 구성이란?

PowerShell DSC(필요한 상태 구성)는 개방형 표준에 따라 Windows에 기본 제공되는 구성 관리 플랫폼입니다. DSC는 확장 중은 물론, 배포 수명 주기의 각 단계(개발, 테스트, 사전 프로덕션, 프로덕션)에서 안정적이고 일관되게 작동할 수 있을 만큼 유연합니다.

DSC의 중심은 [구성](../configurations/configurations.md)입니다.
구성은 특정한 특징을 가진 컴퓨터("노드")로 구성된 환경을 읽기 쉽게 설명한 문서입니다.
이 특성은 특정 Windows 기능을 사용할 수 있도록 할 만큼 간단하거나 SharePoint를 배포할 만큼 복잡할 수 있습니다.

DSC에서는 모니터링 및 보고 기능도 기본적으로 제공합니다.
시스템이 더 이상 호환하지 않는 경우 DSC에서는 경고를 발생시키고 시스템을 수정하는 작업을 수행합니다.

## <a name="benefits-of-using-desired-state-configuration"></a>필요한 상태 구성을 사용할 때의 이점

구성은 쉽게 읽고 저장하고 업데이트하도록 설계되었습니다.
구성에서는 대상 디바이스를 해당 상태에 배치하는 방법에 대한 지침을 작성하는 대신 대상 디바이스가 있어야 하는 상태를 선언합니다.
따라서 DSC를 통해 구성에 대해 배우고, 구성을 채택하고, 구현하고 유지 관리하는 데에 훨씬 적은 비용이 듭니다.

구성을 만드는 것은 복잡한 배포 단계를 단일 위치에서 "단일 데이터 소스(single source of truth)"로 캡처함을 의미합니다.
이렇게 하면 특정 컴퓨터 집합의 반복된 배포의 오류 발생률이 훨씬 낮아지고,
결국 더 빠르고 안정적으로 배포할 수 있어 복잡한 배포의 소요 시간이 짧아집니다.

[PowerShell 갤러리](https://powershellgallery.com)를 통해 구성을 공유할 수도 있습니다. 즉, 완료해야 하는 작업에 대한 일반적인 시나리오 및 모범 사례가 이미 있을 수 있습니다.


## <a name="desired-state-configuration-and-devops"></a>필요한 상태 구성 및 DevOps

DSC는 내부 사용자든 외부 사용자든 최종 사용자에게 가치를 제공하는 데 중점을 둔 빠른 배포와 반복이 가능한 사용자, 프로세스 및 도구의 조합인 [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx)를 사용하여 디자인되었습니다.
단일 구성으로 환경을 정의하면 개발자가 해당 요구 사항을 구성으로 인코딩하고, 해당 구성을 소스 제어에 대해 검사할 수 있습니다. 운영 팀은 오류가 발생하기 쉬운 수동 프로세스를 거치지 않고 쉽게 코드를 배포할 수 있습니다.

구성은 [데이터 기반](../configurations/configData.md)이기도 해서 운영 팀이 개발자의 개입 없이 환경을 쉽게 식별하고 변경할 수 있도록 합니다.

## <a name="desired-state-configuration-on-premises-and-off-premises"></a>Desired State Configuration 온-프레미스 및 오프-프레미스
DSC는 온-프레미스 배포와 오프-프레미스 배포를 모두 관리하는 데 사용할 수 있습니다.
온-프레미스 솔루션의 경우 DSC에는 컴퓨터 관리를 중앙에 집중하고 그 상태에 대해 보고하는 데 사용할 수 있는 [끌어오기 서버](../pull-server/pullServer.md)가 있습니다.
클라우드 솔루션의 경우 DSC는 Windows를 사용할 수 있는 곳이라면 어디서든 사용할 수 있습니다.
DSC의 보고를 중앙에 집중하는 [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/)와 같은 필요한 상태 구성을 기반으로 하는 Azure의 특정 제공 기능도 있습니다.

## <a name="dsc-and-compatibility"></a>DSC 및 호환성

DSC는 Windows Server 2012 R2에서 도입되었지만 WMF(Windows Management Framework) 패키지를 통해 이전 운영 체제에 사용할 수 있습니다.
WMF에 대한 자세한 정보는 [PowerShell homepage(PowerShell 홈페이지)](/powershell/)에서 찾을 수 있습니다.

DSC는 Linux를 관리하는 데에도 사용할 수 있습니다. 자세한 내용은 [Linux용 DSC 시작](../getting-started/lnxGettingStarted.md)을 참조하세요.

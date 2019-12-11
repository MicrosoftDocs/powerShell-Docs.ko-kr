---
ms.date: 10/11/2019
keywords: dsc,powershell,configuration,setup
title: 의사 결정자를 위한 필요한 상태 구성 개요
ms.openlocfilehash: 271ec04035feb17e932acd0ac80f32213a4e018b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352130"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>의사 결정자를 위한 필요한 상태 구성 개요

이 문서에서는 PowerShell DSC(Desired State Configuration) 사용의 비즈니스 혜택에 대해 설명하며, 기술 가이드가 아닙니다.

## <a name="what-is-dsc"></a>DSC란 무엇인가요?

PowerShell DSC는 개방형 표준에 따라 Windows에 기본 제공되는 구성 관리 플랫폼입니다. DSC는 배포 수명 주기의 각 단계(개발, 테스트, 사전 프로덕션, 프로덕션)와 스케일 아웃 과정에서 안정적이고 일관되게 작동할 수 있을 만큼 유연합니다.

DSC의 중심은 [구성](../configurations/configurations.md)입니다. 구성은 특정한 특징을 가진 컴퓨터(또는 노드)로 구성된 환경을 설명하는 PowerShell 스크립트입니다. 이 특성은 특정 Windows 기능을 사용할 수 있도록 할 만큼 간단하거나 SharePoint를 배포할 만큼 복잡할 수 있습니다.

DSC에서는 모니터링 및 보고 기능을 기본적으로 제공합니다. 시스템이 더 이상 호환하지 않는 경우 DSC에서는 경고를 발생시키고 시스템을 수정하는 작업을 수행합니다.

## <a name="benefits-of-using-dsc"></a>DSC 사용의 장점

구성의 디자인에 따라 읽기, 저장, 업데이트 방법이 간소화됩니다. 구성에서는 디바이스를 특정 상태에 배치하는 방법에 대한 지침을 작성하는 대신 대상 디바이스의 해당 상태를 선언합니다. 이러한 요인으로 DSC를 통해 구성에 대해 배우고, 구성을 채택하고, 구현하고 유지 관리하는 비용이 절감됩니다.

구성을 만드는 것은 복잡한 배포 단계를 단일 위치에서 **단일 데이터 소스(single source of truth)** 로 캡처함을 의미합니다. 구성은 특정 컴퓨터 집합의 반복된 배포의 오류 발생률을 낮추고, 더 빠르고 안정적으로 배포할 수 있어 복잡한 배포의 소요 시간이 짧아집니다.

구성은 [PowerShell Gallery(PowerShell 갤러리)](https://powershellgallery.com)를 통해 공유할 수 있습니다. 수행해야 하는 작업에 대한 일반적인 시나리오와 모범 사례는 이미 있을 수 있습니다.

## <a name="dsc-and-devops"></a>DSC 및 DevOps

DSC는 [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx)를 염두에 두고 설계되었습니다. 내부 사용자든 외부 사용자든 최종 사용자에게 가치를 제공하는 데 중점을 둔 빠른 배포와 반복이 가능한 사용자, 프로세스 및 도구의 조합입니다. 환경을 정의하는 단일 구성이란 개발자가 본인의 요구 사항을 구성 내에 인코딩하고 해당 구성을 원본 코드 제어로 체크인할 수 있음을 의미합니다. 그러면 운영 팀은 오류가 발생하기 쉬운 수동 프로세스를 거치지 않고 코드를 배포할 수 있습니다.

구성은 [데이터 기반](../configurations/configData.md)입니다. 운영 팀은 정의된 데이터를 통해 개발자의 개입 없이 환경을 쉽게 식별하고 변경할 수 있습니다.

## <a name="dsc-on-premises-and-off-premises"></a>DSC 온-프레미스 및 오프-프레미스

DSC는 온-프레미스 배포와 오프-프레미스 배포 모두의 관리가 가능합니다. 온-프레미스 솔루션의 경우 DSC에는 컴퓨터를 중앙 집중식으로 관리하고 컴퓨터 상태를 보고하는 데 사용되는 [끌어오기 서버](../pull-server/pullServer.md)가 있습니다. 오프-프레미스 클라우드 솔루션의 경우 DSC는 Windows 사용이 가능한 어디서든 사용할 수 있습니다.
DSC 기반 Azure에서는 DSC 보고를 중앙 집중화하는 [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/) 같은 특정 서비스가 제공됩니다.

## <a name="dsc-and-compatibility"></a>DSC 및 호환성

DSC는 Windows Server 2012 R2에 도입되었지만 Windows Management Framework(WMF)를 통해 하위 수준의 운영 체제에서도 사용할 수 있습니다. WMF에 대한 자세한 내용은 [Windows Management Framework](/powershell/scripting/wmf/overview)를 참조하십시오.

DSC는 Linux 관리에 사용할 수 있습니다. 자세한 내용은 [Linux용 DSC 시작](../getting-started/lnxGettingStarted.md)을 참조하세요.

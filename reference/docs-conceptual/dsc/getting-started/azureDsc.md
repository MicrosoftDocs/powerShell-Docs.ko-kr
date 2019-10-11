---
ms.date: 03/15/2018
keywords: dsc,powershell,configuration,setup
title: Microsoft Azure에서 DSC 사용
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953960"
---
# <a name="using-dsc-on-microsoft-azure"></a>Microsoft Azure에서 DSC 사용

DSC(필요한 상태 구성)는 Microsoft Azure에서 [Azure 필요한 상태 구성 확장 처리기](/azure/virtual-machines/extensions/dsc-overview) 및 [Azure Automation DSC](/azure/automation/automation-dsc-overview)를 통해 지원됩니다.

## <a name="azure-desired-state-configuration-extension-handler"></a>Azure 필요한 상태 구성 확장 처리기

Azure DSC 확장을 사용하면 Microsoft Azure에서 호스트된 VM을 DSC로 관리할 수 있습니다.
자세한 내용은 아래 항목을 참조하세요.

- [Azure 필요한 상태 구성 확장 처리기](/azure/virtual-machines/extensions/dsc-overview)
- [Azure Resource Manager 템플릿을 사용하는 Windows VMSS 및 필요한 상태 구성](/azure/virtual-machines/extensions/dsc-template)
- [Azure DSC 확장 처리기에 자격 증명 전달](/azure/virtual-machines/extensions/dsc-credentials)
- [Azure 필요한 상태 구성 확장 기록](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>Azure Automation DSC

[Azure Automation 서비스](https://azure.microsoft.com/en-us/services/automation/)를 사용하면 Azure 내에서 DSC 구성, 리소스 및 관리되는 노드를 관리할 수 있습니다. 자세한 내용은 아래 항목을 참조하세요.

- [Azure Automation DSC](/azure/automation/automation-dsc-overview)
- [Azure Automation DSC 시작하기](/azure/automation/automation-dsc-getting-started)
- [Azure Automation DSC를 통한 관리를 위한 컴퓨터 온보드](/azure/automation/automation-dsc-onboarding)
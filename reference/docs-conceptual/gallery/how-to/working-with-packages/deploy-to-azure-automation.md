---
ms.date: 06/12/2017
title: Azure 자동화에 배포
description: 이 문서에서는 PowerShell 갤러리를 사용하여 Azure Automation에 패키지를 배포하는 방법을 설명합니다.
ms.openlocfilehash: e9de079ee6cc950c8a268423b9eabd515959b718
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662373"
---
# <a name="deploy-to-azure-automation"></a>Azure 자동화에 배포

패키지 세부 정보 페이지의 Azure Automation에 배포 단추를 클릭하면 PowerShell 갤러리의 패키지가 Azure Automation에 배포됩니다.

![Azure Automation에 배포](media/deploy-to-azure-automation/DeployToAzureAutomationButton.png)

클릭하면 Azure 관리 포털로 리디렉션되며, 여기서 Azure 계정 자격 증명을 사용하여 로그인합니다. 패키지에 종속성이 포함된 경우 모든 종속성도 Azure Automation에 배포됩니다.

> [!WARNING]
> Automation 계정에 동일한 패키지와 버전이 이미 있는 경우 PowerShell 갤러리에서 다시 배포하면 Automation 계정의 패키지를 덮어씁니다.

모듈을 배포하는 경우 Azure Automation의 Modules 섹션에 표시됩니다. 스크립트를 배포하는 경우 Azure Automation의 Runbook 섹션에 표시됩니다.

패키지 메타데이터에 AzureAutomationNotSupported 태그를 추가하면 Azure Automation에 배포 단추를 해제할 수 있습니다.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Azure Automation에 배포에 대한 라이선스 동의 필요

Azure Automation에 배포되는 모듈에 라이선스 동의가 필요한 경우 포털 UI에 ‘This module requires license acceptance. By clicking OK, you are accepting license terms.’(이 모듈은 라이선스 동의가 필요합니다. [확인]을 클릭하면 라이선스 조건에 동의하게 됩니다.)가 표시됩니다.

![Azure Automation에 배포하려면 라이선스 동의 필요](media/deploy-to-azure-automation/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>자세한 내용

- [PowerShellGet에서 라이선스 동의 필요](../../concepts/module-license-acceptance.md)
- [PowerShell 갤러리에서 라이선스 동의 필요](packages-that-require-license-acceptance.md)
- [Azure Automation 웹 사이트](https://azure.microsoft.com/services/automation/)

---
ms.date: 06/12/2017
title: 라이선스 동의 필요
description: 항목 세부 정보 페이지에서 패키지 라이선스를 확인하는 방법
ms.openlocfilehash: 0d8a9ed671f7993726bc3fa41d11159b366e5a28
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662309"
---
# <a name="require-license-acceptance"></a>라이선스 동의 필요

라이선스 동의가 필요한 모듈에 대해 항목 세부 정보 페이지에 라이선스 동의 필요 텍스트가 표시됩니다. 모듈의 라이선스는 **License.txt 보기** 링크를 클릭하여 볼 수 있습니다.

![라이선스 동의 필요](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

PowerShellGet을 통해 모듈을 설치, 저장 또는 업데이트하거나 Azure Automation에 배포할 때 라이선스에 동의하라는 메시지가 사용자에게 표시됩니다.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Azure Automation에 배포에 대한 라이선스 동의 필요

Azure Automation에 배포되는 모듈에 라이선스 동의가 필요한 경우 포털 UI에 ‘This module requires license acceptance. By clicking OK, you are accepting license terms.’(이 모듈은 라이선스 동의가 필요합니다. [확인]을 클릭하면 라이선스 조건에 동의하게 됩니다.)가 표시됩니다.

![Azure Automation에 배포하려면 라이선스 동의 필요](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>자세한 내용

[PowerShellGet에서 라이선스 동의 필요](../../concepts/module-license-acceptance.md)
[Azure Automation 웹 사이트](/azure/automation)

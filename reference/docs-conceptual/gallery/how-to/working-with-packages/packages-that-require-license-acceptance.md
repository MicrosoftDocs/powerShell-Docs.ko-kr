---
ms.date: 06/12/2017
contributor: Farehar
keywords: gallery,powershell,psgallery
title: 라이선스 동의 필요
ms.openlocfilehash: 4b293ea693062cf9717fa4ca913c3eb9abaf7014
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278659"
---
# <a name="require-license-acceptance"></a>라이선스 동의 필요

라이선스 동의가 필요한 모듈에 대해 항목 세부 정보 페이지에 라이선스 동의 필요 텍스트가 표시됩니다. 모듈에 대한 라이선스는 ‘License.txt 보기’ 링크를 클릭하여 볼 수 있습니다.

![라이선스 동의 필요](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

PowerShellGet을 통해 모듈을 설치, 저장 또는 업데이트하거나 Azure Automation에 배포할 때 라이선스에 동의하라는 메시지가 사용자에게 표시됩니다.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Azure Automation에 배포에 대한 라이선스 동의 필요

Azure Automation에 배포되는 모듈에 라이선스 동의가 필요한 경우 포털 UI에 ‘This module requires license acceptance. By clicking OK, you are accepting license terms.’(이 모듈은 라이선스 동의가 필요합니다. [확인]을 클릭하면 라이선스 조건에 동의하게 됩니다.)가 표시됩니다.

![Azure Automation에 배포하려면 라이선스 동의 필요](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>자세한 내용

[PowerShellGet에서 라이선스 동의 필요](../../concepts/module-license-acceptance.md)
[Azure Automation 웹 사이트](/azure/automation)

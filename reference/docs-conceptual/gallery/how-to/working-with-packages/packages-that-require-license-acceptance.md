---
ms.date: 06/12/2017
contributor: Farehar
keywords: gallery,powershell,psgallery
title: 라이선스 동의 필요
ms.openlocfilehash: 4b293ea693062cf9717fa4ca913c3eb9abaf7014
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278659"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="0809f-103">라이선스 동의 필요</span><span class="sxs-lookup"><span data-stu-id="0809f-103">Require license acceptance</span></span>

<span data-ttu-id="0809f-104">라이선스 동의가 필요한 모듈에 대해 항목 세부 정보 페이지에 라이선스 동의 필요 텍스트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0809f-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="0809f-105">모듈에 대한 라이선스는 ‘License.txt 보기’ 링크를 클릭하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0809f-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![라이선스 동의 필요](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

<span data-ttu-id="0809f-107">PowerShellGet을 통해 모듈을 설치, 저장 또는 업데이트하거나 Azure Automation에 배포할 때 라이선스에 동의하라는 메시지가 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0809f-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="0809f-108">Azure Automation에 배포에 대한 라이선스 동의 필요</span><span class="sxs-lookup"><span data-stu-id="0809f-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="0809f-109">Azure Automation에 배포되는 모듈에 라이선스 동의가 필요한 경우 포털 UI에 ‘This module requires license acceptance.</span><span class="sxs-lookup"><span data-stu-id="0809f-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="0809f-110">By clicking OK, you are accepting license terms.’(이 모듈은 라이선스 동의가 필요합니다. [확인]을 클릭하면 라이선스 조건에 동의하게 됩니다.)가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0809f-110">By clicking OK, you are accepting license terms.'</span></span>

![Azure Automation에 배포하려면 라이선스 동의 필요](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="0809f-112">자세한 내용</span><span class="sxs-lookup"><span data-stu-id="0809f-112">More details</span></span>

<span data-ttu-id="0809f-113">[PowerShellGet에서 라이선스 동의 필요](../../concepts/module-license-acceptance.md)
[Azure Automation 웹 사이트](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="0809f-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>

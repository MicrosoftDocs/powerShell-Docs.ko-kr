---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Azure 자동화에 배포
ms.openlocfilehash: dc382b1cf3ceaa787f54c555d01e6bd9ba70e680
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084897"
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="bec31-103">Azure 자동화에 배포</span><span class="sxs-lookup"><span data-stu-id="bec31-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="bec31-104">패키지 세부 정보 페이지의 Azure Automation에 배포 단추를 클릭하면 PowerShell 갤러리의 패키지가 Azure Automation에 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="bec31-104">The Deploy to Azure Automation button on the package details page will deploy the package from the PowerShell Gallery to Azure Automation.</span></span>

![Azure Automation에 배포](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="bec31-106">클릭하면 Azure 관리 포털로 리디렉션되며, 여기서 Azure 계정 자격 증명을 사용하여 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="bec31-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="bec31-107">패키지에 종속성이 포함된 경우 모든 종속성도 Azure Automation에 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="bec31-107">If the package includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="bec31-108">Automation 계정에 동일한 패키지와 버전이 이미 있는 경우 PowerShell 갤러리에서 다시 배포하면 Automation 계정의 패키지를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="bec31-108">If the same package and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the package in your Automation account.</span></span>

<span data-ttu-id="bec31-109">모듈을 배포하는 경우 Azure Automation의 Modules 섹션에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bec31-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="bec31-110">스크립트를 배포하는 경우 Azure Automation의 Runbook 섹션에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bec31-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="bec31-111">패키지 메타데이터에 AzureAutomationNotSupported 태그를 추가하면 Azure Automation에 배포 단추를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bec31-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the package metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="bec31-112">Azure Automation에 배포에 대한 라이선스 동의 필요</span><span class="sxs-lookup"><span data-stu-id="bec31-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="bec31-113">Azure Automation에 배포되는 모듈에 라이선스 동의가 필요한 경우 포털 UI에 ‘This module requires license acceptance.</span><span class="sxs-lookup"><span data-stu-id="bec31-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="bec31-114">By clicking OK, you are accepting license terms.’(이 모듈은 라이선스 동의가 필요합니다. [확인]을 클릭하면 라이선스 조건에 동의하게 됩니다.)가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bec31-114">By clicking OK, you are accepting license terms.'</span></span>

![Azure Automation에 배포하려면 라이선스 동의 필요](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="bec31-116">자세한 내용</span><span class="sxs-lookup"><span data-stu-id="bec31-116">More details</span></span>

- [<span data-ttu-id="bec31-117">PowerShellGet에서 라이선스 동의 필요</span><span class="sxs-lookup"><span data-stu-id="bec31-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="bec31-118">PowerShell 갤러리에서 라이선스 동의 필요</span><span class="sxs-lookup"><span data-stu-id="bec31-118">Require License Acceptance in PowerShell Gallery</span></span>](packages-that-require-license-acceptance.md)
- [<span data-ttu-id="bec31-119">Azure Automation 웹 사이트</span><span class="sxs-lookup"><span data-stu-id="bec31-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)

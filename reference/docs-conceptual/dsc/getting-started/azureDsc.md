---
ms.date: 03/15/2018
keywords: dsc,powershell,configuration,setup
title: Microsoft Azure에서 DSC 사용
ms.openlocfilehash: 6d71b69eea78e775a3e5aaac64bccfa10092b8e6
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870832"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="c2dd7-103">Microsoft Azure에서 DSC 사용</span><span class="sxs-lookup"><span data-stu-id="c2dd7-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="c2dd7-104">DSC(필요한 상태 구성)는 Microsoft Azure에서 [Azure 필요한 상태 구성 확장 처리기](/azure/virtual-machines/extensions/dsc-overview) 및 [Azure Automation DSC](/azure/automation/automation-dsc-overview)를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2dd7-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="c2dd7-105">Azure 필요한 상태 구성 확장 처리기</span><span class="sxs-lookup"><span data-stu-id="c2dd7-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="c2dd7-106">Azure DSC 확장을 사용하면 Microsoft Azure에서 호스트된 VM을 DSC로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dd7-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span> <span data-ttu-id="c2dd7-107">자세한 내용은 아래 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2dd7-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="c2dd7-108">Azure 필요한 상태 구성 확장 처리기</span><span class="sxs-lookup"><span data-stu-id="c2dd7-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="c2dd7-109">Azure Resource Manager 템플릿을 사용하는 Windows VMSS 및 필요한 상태 구성</span><span class="sxs-lookup"><span data-stu-id="c2dd7-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="c2dd7-110">Azure DSC 확장 처리기에 자격 증명 전달</span><span class="sxs-lookup"><span data-stu-id="c2dd7-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="c2dd7-111">Azure 필요한 상태 구성 확장 기록</span><span class="sxs-lookup"><span data-stu-id="c2dd7-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="c2dd7-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="c2dd7-112">Azure Automation DSC</span></span>

<span data-ttu-id="c2dd7-113">[Azure Automation 서비스](https://azure.microsoft.com/services/automation/)를 사용하면 Azure 내에서 DSC 구성, 리소스 및 관리되는 노드를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dd7-113">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="c2dd7-114">자세한 내용은 아래 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2dd7-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="c2dd7-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="c2dd7-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="c2dd7-116">Azure Automation DSC 시작하기</span><span class="sxs-lookup"><span data-stu-id="c2dd7-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="c2dd7-117">Azure Automation DSC를 통한 관리를 위한 컴퓨터 온보드</span><span class="sxs-lookup"><span data-stu-id="c2dd7-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)
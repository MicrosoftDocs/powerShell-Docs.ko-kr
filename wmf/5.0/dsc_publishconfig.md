---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db4543b788ad0a5c7aa32706246446533b901d09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085816"
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="01312-102">구성 문서를 적용하지 않고 제공</span><span class="sxs-lookup"><span data-stu-id="01312-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="01312-103">[Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet은 구성 MOF 파일을 대상 노드에 복사하지만 구성을 적용하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01312-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span>
<span data-ttu-id="01312-104">이 구성은 다음 일관성 검사 중이나 [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet을 실행할 때 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01312-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>

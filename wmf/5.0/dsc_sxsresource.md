---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057930"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="0bdcd-102">DSC 리소스의 Side-By-Side 모듈 버전 관리 지원</span><span class="sxs-lookup"><span data-stu-id="0bdcd-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="0bdcd-103">DSC 리소스를 포함하는 모듈은 병렬로 설치할 수 있으며, DSC 구성에서는 시스템에 설치되어 있는 특정 버전의 리소스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bdcd-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="0bdcd-104">자세한 내용은 [여러 버전의 리소스 사용](https://msdn.microsoft.com/powershell/dsc/sxsresource)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0bdcd-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="0bdcd-105">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="0bdcd-105">Known issues</span></span>

<span data-ttu-id="0bdcd-106">이번 릴리스에서 병렬 설치에는 다음과 같은 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bdcd-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="0bdcd-107">동일한 구성 내에서 두 가지 다른 버전의 DSC 리소스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0bdcd-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>

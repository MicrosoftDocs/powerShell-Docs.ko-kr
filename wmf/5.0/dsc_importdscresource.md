---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680118"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="7e6b4-102">Import-DscResource 키워드에서 -ModuleVersion 매개 변수 지원</span><span class="sxs-lookup"><span data-stu-id="7e6b4-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="7e6b4-103">DSC 구성을 작성할 때 사용할 수 있는 `Import-DscResource` 동적 키워드에 새로운 매개 변수를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="7e6b4-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="7e6b4-104">이제 구성 작성자는 DSC 리소스를 로드할 모듈 버전을 정확하게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e6b4-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="7e6b4-105">새 키워드의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7e6b4-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="7e6b4-106">**Name**: 가져오려는 리소스 하나 이상의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7e6b4-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="7e6b4-107">**ModuleName**: 가져오려는 모듈 하나 이상의 모듈 이름 또는 ModuleSpecification 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7e6b4-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="7e6b4-108">**ModuleVersion**: 가져오려는 모듈의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="7e6b4-108">**ModuleVersion**: Version of module to import.</span></span> <span data-ttu-id="7e6b4-109">사용될 경우 ModuleName은 이름으로 하나의 모듈만 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6b4-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="7e6b4-110">Windows PowerShell ISE에서는 IntelliSense로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e6b4-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="7e6b4-111">**참고**: `–ModuleVersion` 매개 변수는 `–ModuleName` 매개 변수와 함께만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e6b4-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="7e6b4-112">`–Name` 매개 변수만 사용하여 리소스 이름과 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e6b4-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="7e6b4-113">이전에는 DSC 리소스를 로드할 때 모듈 버전을 지정하려면 모듈 사양 개체(예: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`)만 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="7e6b4-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>

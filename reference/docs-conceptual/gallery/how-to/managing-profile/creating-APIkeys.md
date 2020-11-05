---
ms.date: 09/10/2018
title: API 키 관리
description: PowerShell 갤러리는 API 키를 사용하여 콘텐츠 게시자의 갤러리 액세스를 인증합니다.
ms.openlocfilehash: 4b70ac7d56fc1d63719c2acf93da3dd4ac22abed
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661125"
---
# <a name="managing-api-keys"></a><span data-ttu-id="32c46-103">API 키 관리</span><span class="sxs-lookup"><span data-stu-id="32c46-103">Managing API keys</span></span>

<span data-ttu-id="32c46-104">PowerShell 갤러리는 다양한 API 요구 사항을 지원하기 위해 여러 API 키를 만들 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="32c46-105">API 키는 하나 이상의 패키지에 적용할 수 있으며, 특정 권한을 부여하고, 만료 날짜가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="32c46-106">범위가 지정된 API 키를 도입하기 전에 PowerShell 갤러리에 게시된 사용자에게는 "전체 액세스 API 키"가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="32c46-107">전체 액세스 키에는 범위가 지정된 API 키에 기본적으로 제공되는 향상된 보안 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="32c46-108">전체 액세스 키는 만료되지 않으며, 사용자 소유의 모든 항목에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="32c46-109">이 키는 삭제되면 다시 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="32c46-110">다음 이미지에서는 범위가 지정된 API 키를 만들 때 사용할 수 있는 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-110">The following image shows the options available when creating a scoped API key.</span></span>

![API 키 만들기](media/creating-APIkeys/PSGallery_KeyScoped.png)

<span data-ttu-id="32c46-112">이 예에서는 **AzureRMDataFactory** 라는 API 키를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="32c46-113">이 키 값은 'AzureRM.DataFactory'로 시작하고 365일 동안 유효한 이름의 패키지를 푸시하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="32c46-114">동일한 조직 내의 여러 팀이 서로 다른 패키지에서 작업하는 일반적인 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="32c46-115">팀 멤버에게는 자신이 작업할 특정 패키지에 대한 권한이 부여되는 키가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="32c46-116">만료 값은 부실하거나 잊어버린 키를 사용하지 않도록 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="32c46-117">GLOB 패턴 사용</span><span class="sxs-lookup"><span data-stu-id="32c46-117">Using glob patterns</span></span>

<span data-ttu-id="32c46-118">여러 패키지에서 작업하는 경우 GLOB 패턴을 사용하여 여러 패키지를 하나의 그룹으로 일치시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="32c46-119">API 키 권한은 GLOB 패턴과 일치하는 모든 새 패키지에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="32c46-120">예를 들어 앞의 예에서는 **GLOB 패턴** 값으로 'AzureRM.DataFactory \*'를 사용하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="32c46-121">패키지가 GLOB 패턴과 일치하므로 이 키를 사용하여 'AzureRm.DataFactoryV2.Netcore'라는 패키지를 푸시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="32c46-122">안전하게 API 키 만들기</span><span class="sxs-lookup"><span data-stu-id="32c46-122">Create API keys securely</span></span>

<span data-ttu-id="32c46-123">보안을 위해 새로 만든 키 값은 화면에 표시되지 않으며, 아래와 같이 [복사] 단추로만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![새 API 키 값 가져오기](media/creating-APIkeys/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="32c46-125">API 키 값은 만들거나 새로 고친 직후에만 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="32c46-126">표시되지 않으며, 페이지를 새로 고친 후에는 다시 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="32c46-127">키 값을 잃어버리면 [다시 생성]을 사용하고, 다시 생성된 후에 키를 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="32c46-128">키 권한 및 만료</span><span class="sxs-lookup"><span data-stu-id="32c46-128">Key permissions and expiration</span></span>

<span data-ttu-id="32c46-129">범위가 지정된 API 키는 다음 권한 중 하나를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="32c46-130">새 패키지 푸시</span><span class="sxs-lookup"><span data-stu-id="32c46-130">Push new packages</span></span>
- <span data-ttu-id="32c46-131">새 패키지 또는 업데이트 패키지 푸시</span><span class="sxs-lookup"><span data-stu-id="32c46-131">Push new or update packages</span></span>
- <span data-ttu-id="32c46-132">패키지 나열 취소</span><span class="sxs-lookup"><span data-stu-id="32c46-132">Unlist packages</span></span>

<span data-ttu-id="32c46-133">모든 새 키는 만료됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-133">Every new key has an expiration.</span></span> <span data-ttu-id="32c46-134">만료 값은 일 단위로 측정됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-134">The expiration value is measured in days.</span></span> <span data-ttu-id="32c46-135">만료에 사용할 수 있는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="32c46-136">1일</span><span class="sxs-lookup"><span data-stu-id="32c46-136">1 day</span></span>
- <span data-ttu-id="32c46-137">90일</span><span class="sxs-lookup"><span data-stu-id="32c46-137">90 days</span></span>
- <span data-ttu-id="32c46-138">180일</span><span class="sxs-lookup"><span data-stu-id="32c46-138">180 days</span></span>
- <span data-ttu-id="32c46-139">270일</span><span class="sxs-lookup"><span data-stu-id="32c46-139">270 days</span></span>
- <span data-ttu-id="32c46-140">365일(기본값)</span><span class="sxs-lookup"><span data-stu-id="32c46-140">365 days (default)</span></span>

<span data-ttu-id="32c46-141">키를 만든 후에는 이러한 설정을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="32c46-142">만료되지 않는 새 키는 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="32c46-143">기존 API 키 편집 및 삭제</span><span class="sxs-lookup"><span data-stu-id="32c46-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="32c46-144">기존 키의 일부 설정은 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="32c46-145">앞에서 설명한 대로 기존 API 키에 대한 보안 범위를 수정하거나 만료 시간을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="32c46-146">변경할 수 있는 옵션은 다음 스크린샷과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-146">The changeable options are shown in the following screenshot:</span></span>

![API 키 값 편집](media/creating-APIkeys/PSGallery_EditAPIKey.png)

<span data-ttu-id="32c46-148">키로 제어되는 패키지를 변경하려면 목록에서 개별 패키지를 선택하거나 GLOB 패턴을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="32c46-149">**다시 생성** 을 클릭하면 새 키 값이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="32c46-150">키를 처음 만들 때와 마찬가지로 키 값을 업데이트하는 즉시 **복사** 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="32c46-151">이 페이지에서 나가면 **복사** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="32c46-152">**삭제** 를 클릭하면 확인 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="32c46-153">키가 삭제되면 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="32c46-154">키 만료</span><span class="sxs-lookup"><span data-stu-id="32c46-154">Key expiration</span></span>

<span data-ttu-id="32c46-155">만료되기 10일 전에 PowerShell 갤러리에서 API 키의 계정 소유자에게 경고 이메일을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="32c46-156">만료 후에는 키를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="32c46-157">API 키 관리 페이지의 위쪽에 더 이상 유효하지 않은 키를 보여 주는 경고 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="32c46-158">그러면 새 키 값을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c46-158">You can generate a new key value.</span></span>

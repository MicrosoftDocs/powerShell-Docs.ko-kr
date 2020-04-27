---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC 보관 리소스
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954770"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="c3302-103">DSC 보관 리소스</span><span class="sxs-lookup"><span data-stu-id="c3302-103">DSC Archive Resource</span></span>

> <span data-ttu-id="c3302-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="c3302-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="c3302-105">Windows PowerShell DSC(필요한 상태 구성)의 보관 리소스는 특정 경로에서 보관(.zip) 파일의 압축을 푸는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3302-106">구문</span><span class="sxs-lookup"><span data-stu-id="c3302-106">Syntax</span></span>

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="c3302-107">속성</span><span class="sxs-lookup"><span data-stu-id="c3302-107">Properties</span></span>

|<span data-ttu-id="c3302-108">속성</span><span class="sxs-lookup"><span data-stu-id="c3302-108">Property</span></span> |<span data-ttu-id="c3302-109">Description</span><span class="sxs-lookup"><span data-stu-id="c3302-109">Description</span></span> |
|---|---|
|<span data-ttu-id="c3302-110">대상</span><span class="sxs-lookup"><span data-stu-id="c3302-110">Destination</span></span> |<span data-ttu-id="c3302-111">보관 파일 내용을 추출해 놓을 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="c3302-112">경로</span><span class="sxs-lookup"><span data-stu-id="c3302-112">Path</span></span> |<span data-ttu-id="c3302-113">보관 파일의 원본 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-113">Specifies the source path of the archive file.</span></span> |
|<span data-ttu-id="c3302-114">체크섬</span><span class="sxs-lookup"><span data-stu-id="c3302-114">Checksum</span></span> |<span data-ttu-id="c3302-115">두 파일이 동일한 것인지 결정할 때 사용할 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="c3302-116">**Checksum**을 지정하지 않은 경우 비교에 파일 또는 디렉터리 이름만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-116">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="c3302-117">유효한 값은 다음과 같습니다. **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span><span class="sxs-lookup"><span data-stu-id="c3302-117">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> <span data-ttu-id="c3302-118">**Validate** 없이 **Checksum**을 지정하는 경우, 구성이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-118">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> |
|<span data-ttu-id="c3302-119">Force</span><span class="sxs-lookup"><span data-stu-id="c3302-119">Force</span></span> |<span data-ttu-id="c3302-120">특정 파일 작업(예: 파일 덮어쓰기나 비어 있지 않은 디렉터리 삭제)을 수행하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-120">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="c3302-121">**Force** 속성을 사용하면 이러한 오류가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-121">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="c3302-122">기본값은 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-122">The default value is **False**.</span></span> |
|<span data-ttu-id="c3302-123">유효성 검사</span><span class="sxs-lookup"><span data-stu-id="c3302-123">Validate</span></span>| <span data-ttu-id="c3302-124">보관 파일이 서명과 일치하는지 여부를 결정하려면 **체크섬** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-124">Uses the **Checksum** property to determine if the archive matches the signature.</span></span> <span data-ttu-id="c3302-125">**Validate** 없이 **Checksum**을 지정하는 경우, 구성이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-125">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> <span data-ttu-id="c3302-126">**Checksum** 없이**Validate**를 지정하면 기본적으로 _SHA-256_ **Checksum**이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-126">If you specify **Validate** without **Checksum**, a _SHA-256_ **Checksum** is used by default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c3302-127">공용 속성</span><span class="sxs-lookup"><span data-stu-id="c3302-127">Common properties</span></span>

|<span data-ttu-id="c3302-128">속성</span><span class="sxs-lookup"><span data-stu-id="c3302-128">Property</span></span> |<span data-ttu-id="c3302-129">Description</span><span class="sxs-lookup"><span data-stu-id="c3302-129">Description</span></span> |
|---|---|
|<span data-ttu-id="c3302-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c3302-130">DependsOn</span></span> |<span data-ttu-id="c3302-131">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c3302-132">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c3302-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="c3302-133">Ensure</span></span> |<span data-ttu-id="c3302-134">보관 파일의 내용이 **Destination**에 있는지 확인할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-134">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="c3302-135">내용이 있도록 하려면 이 속성을 **Present**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-135">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="c3302-136">내용이 없도록 하려면 이 속성을 **Absent**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-136">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="c3302-137">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="c3302-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c3302-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="c3302-139">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="c3302-140">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="c3302-141">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3302-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="c3302-142">예제</span><span class="sxs-lookup"><span data-stu-id="c3302-142">Example</span></span>

<span data-ttu-id="c3302-143">다음 예제에서는 Archive 리소스를 사용하여 `Test.zip`이라는 보관 파일의 내용이 존재하고 지정된 대상에 압축이 풀리도록 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c3302-143">The following example shows how to use the Archive resource to ensure that the contents of an archive file called `Test.zip` exist and are extracted at a given destination.</span></span>

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```
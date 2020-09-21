---
ms.date: 07/16/2020
keywords: dsc,powershell,configuration,setup
title: DSC 보관 리소스
ms.openlocfilehash: cbe32012c2035fb3e145bd06fadd73cdba93fd3e
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463791"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="4d7aa-103">DSC 보관 리소스</span><span class="sxs-lookup"><span data-stu-id="4d7aa-103">DSC Archive Resource</span></span>

> <span data-ttu-id="4d7aa-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="4d7aa-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="4d7aa-105">Windows PowerShell DSC(필요한 상태 구성)의 보관 리소스는 특정 경로에서 보관(.zip) 파일의 압축을 푸는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d7aa-106">구문</span><span class="sxs-lookup"><span data-stu-id="4d7aa-106">Syntax</span></span>

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="4d7aa-107">속성</span><span class="sxs-lookup"><span data-stu-id="4d7aa-107">Properties</span></span>

|<span data-ttu-id="4d7aa-108">속성</span><span class="sxs-lookup"><span data-stu-id="4d7aa-108">Property</span></span> |<span data-ttu-id="4d7aa-109">Description</span><span class="sxs-lookup"><span data-stu-id="4d7aa-109">Description</span></span> |
|---|---|
| <span data-ttu-id="4d7aa-110">대상</span><span class="sxs-lookup"><span data-stu-id="4d7aa-110">Destination</span></span> | <span data-ttu-id="4d7aa-111">보관 파일 내용을 추출해 놓을 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
| <span data-ttu-id="4d7aa-112">경로</span><span class="sxs-lookup"><span data-stu-id="4d7aa-112">Path</span></span> | <span data-ttu-id="4d7aa-113">보관 파일의 원본 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-113">Specifies the source path of the archive file.</span></span> |
| <span data-ttu-id="4d7aa-114">체크섬</span><span class="sxs-lookup"><span data-stu-id="4d7aa-114">Checksum</span></span> | <span data-ttu-id="4d7aa-115">두 파일이 동일한 것인지 결정할 때 사용할 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="4d7aa-116">**Checksum**을 지정하지 않은 경우 비교에 파일 또는 디렉터리 이름만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-116">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="4d7aa-117">유효한 값은 다음과 같습니다. **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-117">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> <span data-ttu-id="4d7aa-118">**Validate** 없이 **Checksum**을 지정하는 경우, 구성이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-118">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> |
| <span data-ttu-id="4d7aa-119">자격 증명</span><span class="sxs-lookup"><span data-stu-id="4d7aa-119">Credential</span></span> | <span data-ttu-id="4d7aa-120">필요한 경우 지정된 보관 경로 및 대상에 액세스할 권한이 있는 사용자 계정의 자격 증명입니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-120">The credential of a user account with permissions to access the specified archive path and destination if needed.</span></span> |
| <span data-ttu-id="4d7aa-121">Force</span><span class="sxs-lookup"><span data-stu-id="4d7aa-121">Force</span></span> | <span data-ttu-id="4d7aa-122">특정 파일 작업(예: 파일 덮어쓰기나 비어 있지 않은 디렉터리 삭제)을 수행하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-122">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="4d7aa-123">**Force** 속성을 사용하면 이러한 오류가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-123">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="4d7aa-124">기본값은 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-124">The default value is **False**.</span></span> |
| <span data-ttu-id="4d7aa-125">유효성 검사</span><span class="sxs-lookup"><span data-stu-id="4d7aa-125">Validate</span></span>| <span data-ttu-id="4d7aa-126">보관 파일이 서명과 일치하는지 여부를 결정하려면 **체크섬** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-126">Uses the **Checksum** property to determine if the archive matches the signature.</span></span> <span data-ttu-id="4d7aa-127">**Validate** 없이 **Checksum**을 지정하는 경우, 구성이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-127">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> <span data-ttu-id="4d7aa-128">**체크섬** 없이 **유효성 검사**를 지정하면 기본적으로 _SHA-256_ **체크섬**이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-128">If you specify **Validate** without **Checksum**, a _SHA-256_ **Checksum** is used by default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="4d7aa-129">공용 속성</span><span class="sxs-lookup"><span data-stu-id="4d7aa-129">Common properties</span></span>

|<span data-ttu-id="4d7aa-130">속성</span><span class="sxs-lookup"><span data-stu-id="4d7aa-130">Property</span></span> |<span data-ttu-id="4d7aa-131">Description</span><span class="sxs-lookup"><span data-stu-id="4d7aa-131">Description</span></span> |
|---|---|
|<span data-ttu-id="4d7aa-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4d7aa-132">DependsOn</span></span> |<span data-ttu-id="4d7aa-133">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4d7aa-134">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-134">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="4d7aa-135">Ensure</span><span class="sxs-lookup"><span data-stu-id="4d7aa-135">Ensure</span></span> |<span data-ttu-id="4d7aa-136">보관 파일의 내용이 **Destination**에 있는지 확인할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-136">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="4d7aa-137">내용이 있도록 하려면 이 속성을 **Present**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-137">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="4d7aa-138">내용이 없도록 하려면 이 속성을 **Absent**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-138">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="4d7aa-139">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-139">The default value is **Present**.</span></span> |
|<span data-ttu-id="4d7aa-140">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4d7aa-140">PsDscRunAsCredential</span></span> |<span data-ttu-id="4d7aa-141">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-141">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="4d7aa-142">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-142">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="4d7aa-143">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-143">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="4d7aa-144">예제</span><span class="sxs-lookup"><span data-stu-id="4d7aa-144">Example</span></span>

<span data-ttu-id="4d7aa-145">다음 예제에서는 Archive 리소스를 사용하여 `Test.zip`이라는 보관 파일의 내용이 존재하고 사용하고 권한 부여되는 지정된 대상에 압축이 풀리도록 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4d7aa-145">The following example shows how to use the Archive resource to ensure that the contents of an archive file called `Test.zip` exist and are extracted at a given destination using and authorized.</span></span>

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```

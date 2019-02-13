---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 보관 리소스
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682683"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="f0dba-103">DSC 보관 리소스</span><span class="sxs-lookup"><span data-stu-id="f0dba-103">DSC Archive Resource</span></span>

> <span data-ttu-id="f0dba-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f0dba-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f0dba-105">Windows PowerShell DSC(필요한 상태 구성)의 보관 리소스는 특정 경로에서 보관(.zip) 파일의 압축을 푸는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="f0dba-106">구문</span><span class="sxs-lookup"><span data-stu-id="f0dba-106">Syntax</span></span>
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="f0dba-107">속성</span><span class="sxs-lookup"><span data-stu-id="f0dba-107">Properties</span></span>

|  <span data-ttu-id="f0dba-108">속성</span><span class="sxs-lookup"><span data-stu-id="f0dba-108">Property</span></span>  |  <span data-ttu-id="f0dba-109">설명</span><span class="sxs-lookup"><span data-stu-id="f0dba-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="f0dba-110">대상</span><span class="sxs-lookup"><span data-stu-id="f0dba-110">Destination</span></span>| <span data-ttu-id="f0dba-111">보관 파일 내용을 추출해 놓을 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="f0dba-112">경로</span><span class="sxs-lookup"><span data-stu-id="f0dba-112">Path</span></span>| <span data-ttu-id="f0dba-113">보관 파일의 원본 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-113">Specifies the source path of the archive file.</span></span>|
| <span data-ttu-id="f0dba-114">__Checksum__</span><span class="sxs-lookup"><span data-stu-id="f0dba-114">__Checksum__</span></span>| <span data-ttu-id="f0dba-115">두 파일이 동일한 것인지 결정할 때 사용할 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="f0dba-116">__Checksum__을 지정하지 않은 경우 비교에 파일 또는 디렉터리 이름만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="f0dba-117">유효한 값은 다음과 같습니다. Sha-1, SHA-256, SHA-512, createdDate, modifiedDate, none (기본값).</span><span class="sxs-lookup"><span data-stu-id="f0dba-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="f0dba-118">__Validate__ 없이 __Checksum__을 지정하는 경우, 구성이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>|
| <span data-ttu-id="f0dba-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="f0dba-119">Ensure</span></span>| <span data-ttu-id="f0dba-120">보관 파일의 내용이 __Destination__에 있는지 확인할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="f0dba-121">내용이 있도록 하려면 이 속성을 __Present__으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="f0dba-122">내용이 없도록 하려면 이 속성을 __Absent__으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="f0dba-123">기본값은 __Present__입니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-123">The default value is __Present__.</span></span>|
| <span data-ttu-id="f0dba-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f0dba-124">DependsOn</span></span> | <span data-ttu-id="f0dba-125">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f0dba-126">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="f0dba-127">유효성 검사</span><span class="sxs-lookup"><span data-stu-id="f0dba-127">Validate</span></span>| <span data-ttu-id="f0dba-128">보관 파일이 서명과 일치하는지 여부를 결정하려면 체크섬 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="f0dba-129">유효성 검사 없이 체크섬을 지정하면 구성이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="f0dba-130">체크섬 없이 유효성 검사를 지정하면 기본적으로 SHA-256 체크섬이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>|
| <span data-ttu-id="f0dba-131">Force</span><span class="sxs-lookup"><span data-stu-id="f0dba-131">Force</span></span>| <span data-ttu-id="f0dba-132">특정 파일 작업(예: 파일 덮어쓰기나 비어 있지 않은 디렉터리 삭제)을 수행하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="f0dba-133">Force 속성을 사용하면 이러한 오류가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="f0dba-134">기본값은 False입니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-134">The default value is False.</span></span>|

## <a name="example"></a><span data-ttu-id="f0dba-135">예제</span><span class="sxs-lookup"><span data-stu-id="f0dba-135">Example</span></span>

<span data-ttu-id="f0dba-136">다음 예제에서는 보관 리소스를 사용하여 Test.zip이라는 보관 파일의 내용이 존재하고 지정된 대상에 압축이 풀리도록 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f0dba-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```
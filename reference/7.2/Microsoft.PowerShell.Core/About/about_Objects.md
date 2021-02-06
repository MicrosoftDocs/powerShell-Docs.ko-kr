---
description: PowerShell의 개체에 대 한 필수 정보를 제공 합니다.
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_objects?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Objects
ms.openlocfilehash: bfb66e72a74d20379123558b85047097dc801e9d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602688"
---
# <a name="about-objects"></a><span data-ttu-id="04158-103">개체 정보</span><span class="sxs-lookup"><span data-stu-id="04158-103">About Objects</span></span>

## <a name="short-description"></a><span data-ttu-id="04158-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="04158-104">Short Description</span></span>
<span data-ttu-id="04158-105">PowerShell의 개체에 대 한 필수 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="04158-105">Provides essential information about objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="04158-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="04158-106">Long Description</span></span>

<span data-ttu-id="04158-107">PowerShell에서 수행 하는 모든 작업은 개체의 컨텍스트 내에서 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="04158-107">Every action you take in PowerShell occurs within the context of objects.</span></span> <span data-ttu-id="04158-108">데이터를 한 명령에서 다음 명령으로 이동 하면 하나 이상의 식별 가능한 개체로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="04158-108">As data moves from one command to the next, it moves as one or more identifiable objects.</span></span> <span data-ttu-id="04158-109">그런 다음 개체는 항목을 나타내는 데이터의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="04158-109">An object, then, is a collection of data that represents an item.</span></span> <span data-ttu-id="04158-110">개체는 세 가지 유형의 데이터 즉, 개체 형식, 해당 메서드 및 속성으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04158-110">An object is made up of three types of data: the objects type, its methods, and its properties.</span></span>

## <a name="types-methods-and-properties"></a><span data-ttu-id="04158-111">형식, 메서드 및 속성</span><span class="sxs-lookup"><span data-stu-id="04158-111">Types, Methods, and Properties</span></span>

<span data-ttu-id="04158-112">개체 형식은 개체의 종류를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="04158-112">The object type tells what kind of object it is.</span></span> <span data-ttu-id="04158-113">예를 들어 파일을 나타내는 개체는 FileInfo 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="04158-113">For example, an object that represents a file is a FileInfo object.</span></span>

<span data-ttu-id="04158-114">개체 메서드는 개체에 대해 수행할 수 있는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="04158-114">The object methods are actions that you can perform on the object.</span></span>
<span data-ttu-id="04158-115">예를 들어, FileInfo 개체에는 파일을 복사 하는 데 사용할 수 있는 CopyTo 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04158-115">For example, FileInfo objects have a CopyTo method that you can use to copy the file.</span></span>

<span data-ttu-id="04158-116">개체 속성은 개체에 대 한 정보를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="04158-116">Object properties store information about the object.</span></span> <span data-ttu-id="04158-117">예를 들어, FileInfo 개체에는 파일에 가장 최근에 액세스 한 날짜와 시간을 저장 하는 LastWriteTime 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04158-117">For example, FileInfo objects have a LastWriteTime property that stores the date and time that the file was most recently accessed.</span></span>

<span data-ttu-id="04158-118">개체를 사용 하는 경우 명령에서 해당 메서드 및 속성을 사용 하 여 작업을 수행 하 고 데이터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04158-118">When working with objects, you can use their methods and properties in commands to take action and manage data.</span></span>

## <a name="objects-in-pipelines"></a><span data-ttu-id="04158-119">파이프라인의 개체</span><span class="sxs-lookup"><span data-stu-id="04158-119">Objects in Pipelines</span></span>

<span data-ttu-id="04158-120">파이프라인에서 명령을 결합 하면 서로 정보를 개체로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="04158-120">When commands are combined in a pipeline, they pass information to each other as objects.</span></span> <span data-ttu-id="04158-121">첫 번째 명령이 실행 될 때 파이프라인에서 하나 이상의 개체를 두 번째 명령으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="04158-121">When the first command runs, it sends one or more objects down the pipeline to the second command.</span></span> <span data-ttu-id="04158-122">두 번째 명령은 첫 번째 명령에서 개체를 받아서 처리 한 다음 새 개체 또는 수정 된 개체를 파이프라인의 다음 명령에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="04158-122">The second command receives the objects from the first command, processes the objects, and then passes new or revised objects to the next command in the pipeline.</span></span>
<span data-ttu-id="04158-123">파이프라인의 모든 명령이 실행 될 때까지 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04158-123">This continues until all commands in the pipeline run.</span></span>

<span data-ttu-id="04158-124">다음 예제에서는 개체가 한 명령에서 다음 명령으로 전달 되는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="04158-124">The following example demonstrates how objects are passed from one command to the next:</span></span>

```powershell
Get-ChildItem C: | where { $_.PsIsContainer -eq $false } | Format-List
```

<span data-ttu-id="04158-125">첫 번째 명령은 `Get-ChildItem C:` 파일 시스템의 루트 디렉터리에 있는 각 항목에 대 한 파일 또는 디렉터리 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="04158-125">The first command `Get-ChildItem C:` returns a file or directory object for each item in the root directory of the file system.</span></span> <span data-ttu-id="04158-126">파일 및 디렉터리 개체는 파이프라인에서 두 번째 명령으로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04158-126">The file and directory objects are passed down the pipeline to the second command.</span></span>

<span data-ttu-id="04158-127">두 번째 명령은 `where { $_.PsIsContainer -eq $false }` 모든 파일 시스템 개체의 PsIsContainer 속성을 사용 하 여 PsIsContainer 속성에 false (false) 값이 있는 파일만 선택 합니다 \$ .</span><span class="sxs-lookup"><span data-stu-id="04158-127">The second command `where { $_.PsIsContainer -eq $false }` uses the PsIsContainer property of all file system objects to select only files, which have a value of False (\$false) in their PsIsContainer property.</span></span> <span data-ttu-id="04158-128">컨테이너 이며, 따라서 PsIsContainer 속성에 True (true) 값이 있는 폴더는 \$ 선택 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04158-128">Folders, which are containers and, thus, have a value of True (\$true) in their PsIsContainer property, are not selected.</span></span>

<span data-ttu-id="04158-129">두 번째 명령은 파일 개체만 목록의 파일 개체를 표시 하는 세 번째 명령에 전달 합니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="04158-129">The second command passes only the file objects to the third command `Format-List`, which displays the file objects in a list.</span></span>

## <a name="see-also"></a><span data-ttu-id="04158-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04158-130">See Also</span></span>

[<span data-ttu-id="04158-131">about_Methods</span><span class="sxs-lookup"><span data-stu-id="04158-131">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="04158-132">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="04158-132">about_Object_Creation</span></span>](about_Object_Creation.md)

[<span data-ttu-id="04158-133">about_Properties</span><span class="sxs-lookup"><span data-stu-id="04158-133">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="04158-134">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="04158-134">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="04158-135">Get-Member</span><span class="sxs-lookup"><span data-stu-id="04158-135">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)


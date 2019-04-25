---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: 카탈로그 cmdlet
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057640"
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="5d5e0-103">카탈로그 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5d5e0-103">Catalog Cmdlets</span></span>

<span data-ttu-id="5d5e0-104">Windows 카탈로그 파일을 생성하고 유효성을 검사하는 두 개의 새로운 cmdlet을 [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) 모듈에 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>

## <a name="new-filecatalog"></a><span data-ttu-id="5d5e0-105">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="5d5e0-105">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="5d5e0-106">`New-FileCatalog`는 폴더 및 파일 집합에 대한 Windows 카탈로그 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="5d5e0-107">카탈로그 파일에는 지정된 경로에 있는 모든 파일에 대한 해시가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="5d5e0-108">사용자는 폴더 집합을 이러한 폴더를 나타내는 해당 카탈로그 파일과 함께 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="5d5e0-109">카탈로그 파일은 콘텐츠를 받는 사람이 카탈로그를 만든 후 폴더가 변경되었는지 여부를 확인하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="5d5e0-110">카탈로그 버전 1 및 2 생성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="5d5e0-111">버전 1은 SHA1 해시 알고리즘을 사용하여 파일 해시를 만들고 버전 2는 SHA256을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="5d5e0-112">*Windows Server 2008 R2* 및 *Windows 7*에서는 카탈로그 버전 2가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="5d5e0-113">*Windows 8*, *Windows Server 2012* 이상 플랫폼을 사용하는 경우 카탈로그 버전 2를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>

<span data-ttu-id="5d5e0-114">기존 모듈에 이 명령을 사용하려면 모듈 매니페스트의 위치와 일치하도록 CatalogFilePath 및 Path 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="5d5e0-115">아래 예제에서는 모듈 매니페스트가 C:\Program Files\Windows PowerShell\Modules\Pester에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="5d5e0-116">이 cmdlet은 카탈로그 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-116">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="5d5e0-117">카탈로그 파일(위 예제에서 Pester.cat)의 무결성을 확인하려면 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet을 사용하여 카탈로그 파일에 서명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>


## <a name="test-filecatalog"></a><span data-ttu-id="5d5e0-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="5d5e0-118">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="5d5e0-119">`Test-FileCatalog`는 폴더 집합을 나타내는 카탈로그의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="5d5e0-120">이 cmdlet은 카탈로그 파일에서 찾은 모든 파일의 해시 및 상대 경로를 디스크에 저장된 내용과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="5d5e0-121">파일 해시 및 경로 간의 불일치를 발견하면 `ValidationFailed` 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span>
<span data-ttu-id="5d5e0-122">사용자는 `Detailed` 스위치를 사용하여 이 모든 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="5d5e0-123">카탈로그의 서명 상태는 `Signature` 필드로 표시되며, 이는 카탈로그 파일에 대해 [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet을 호출하는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet on the catalog file.</span></span>
<span data-ttu-id="5d5e0-124">사용자는 `FilesToSkip` 매개 변수를 사용하여 유효성 검사 시 파일을 건너뛸 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span>

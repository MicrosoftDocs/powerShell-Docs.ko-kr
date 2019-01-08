---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Linux nxArchive 리소스용 DSC
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047701"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="ea0a4-103">Linux nxArchive 리소스용 DSC</span><span class="sxs-lookup"><span data-stu-id="ea0a4-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="ea0a4-104">PowerShell DSC(필요한 상태 구성)의 **nxArchive** 리소스는 Linux 노드 상의 특정 경로에서 보관(.tar, .zip) 파일의 압축을 푸는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ea0a4-105">구문</span><span class="sxs-lookup"><span data-stu-id="ea0a4-105">Syntax</span></span>

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="ea0a4-106">속성</span><span class="sxs-lookup"><span data-stu-id="ea0a4-106">Properties</span></span>

|  <span data-ttu-id="ea0a4-107">속성</span><span class="sxs-lookup"><span data-stu-id="ea0a4-107">Property</span></span> |  <span data-ttu-id="ea0a4-108">설명</span><span class="sxs-lookup"><span data-stu-id="ea0a4-108">Description</span></span> |
|---|---|
| <span data-ttu-id="ea0a4-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="ea0a4-109">SourcePath</span></span>| <span data-ttu-id="ea0a4-110">보관 파일의 원본 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="ea0a4-111">.tar, .zip 또는 .tar.gz 파일이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
| <span data-ttu-id="ea0a4-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="ea0a4-112">DestinationPath</span></span>| <span data-ttu-id="ea0a4-113">보관 파일 내용을 추출해 놓을 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="ea0a4-114">체크섬</span><span class="sxs-lookup"><span data-stu-id="ea0a4-114">Checksum</span></span>| <span data-ttu-id="ea0a4-115">소스 보관 파일이 업데이트되었는지 결정할 때 사용할 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="ea0a4-116">값은 "ctime", "mtime" 또는 "md5"입니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="ea0a4-117">기본값은 "md5"입니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-117">The default value is "md5".</span></span>|
| <span data-ttu-id="ea0a4-118">Force</span><span class="sxs-lookup"><span data-stu-id="ea0a4-118">Force</span></span>| <span data-ttu-id="ea0a4-119">특정 파일 작업(예: 파일 덮어쓰기나 비어 있지 않은 디렉터리 삭제)을 수행하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="ea0a4-120">**Force** 속성을 사용하면 이러한 오류가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="ea0a4-121">기본값은 **$false**입니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-121">The default value is **$false**.</span></span>|
| <span data-ttu-id="ea0a4-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ea0a4-122">DependsOn</span></span> | <span data-ttu-id="ea0a4-123">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ea0a4-124">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 **ID**가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="ea0a4-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="ea0a4-125">Ensure</span></span>| <span data-ttu-id="ea0a4-126">보관 파일의 내용이 **Destination**에 있는지 확인할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="ea0a4-127">내용이 있도록 하려면 이 속성을 "Present"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="ea0a4-128">내용이 없도록 하려면 이 속성을 "Absent"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="ea0a4-129">기본값은 "Present"입니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-129">The default value is "Present".</span></span>|

## <a name="example"></a><span data-ttu-id="ea0a4-130">예제</span><span class="sxs-lookup"><span data-stu-id="ea0a4-130">Example</span></span>

<span data-ttu-id="ea0a4-131">다음 예제에서는 **nxArchive** 리소스를 사용하여 `website.tar`이라는 보관 파일의 내용이 존재하고 지정된 대상에 압축이 풀리도록 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="ea0a4-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```
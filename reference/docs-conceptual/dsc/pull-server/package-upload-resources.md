---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 리소스 패키지 및 끌어오기 서버에 업로드
ms.openlocfilehash: 8aac343d7495ecda94ed76d1d97079397eecd65f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278507"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="45e37-103">리소스 패키지 및 끌어오기 서버에 업로드</span><span class="sxs-lookup"><span data-stu-id="45e37-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="45e37-104">아래 섹션에서는 끌어오기 서버를 이미 설정했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="45e37-105">끌어오기 서버를 설정하지 않은 경우에는 다음 가이드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="45e37-106">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="45e37-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="45e37-107">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="45e37-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="45e37-108">구성, 리소스를 다운로드하고 해당 상태를 보고하도록 각 대상 노드를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="45e37-109">이 문서에서는 다운로드할 수 있도록 리소스를 업로드하고 자동으로 리소스를 다운로드하도록 클라이언트를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="45e37-110">노드가 할당된 구성을 받으면 **끌어오기** 또는 **밀어넣기**(v5)를 통해 LCM에 지정된 위치에서 구성에 필요한 모든 리소스를 자동으로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="45e37-111">패키지 리소스 모듈</span><span class="sxs-lookup"><span data-stu-id="45e37-111">Package Resource Modules</span></span>

<span data-ttu-id="45e37-112">다운로드할 클라이언트에 사용 가능한 각 리소스는 ".zip" 파일에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="45e37-113">아래 예제에서는 [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) 리소스를 사용하여 필요한 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="45e37-114">클라이언트에서 PowerShell 4.0을 사용하는 경우 리소스 폴더 구조를 평면화하고 모든 버전 폴더를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="45e37-115">자세한 내용은 [여러 리소스 버전](../configurations/import-dscresource.md#multiple-resource-versions)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45e37-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="45e37-116">원하는 유틸리티, 스크립트 또는 메서드를 사용하여 리소스 디렉터리를 압축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="45e37-117">Windows에서는 "xPSDesiredStateConfiguration" 디렉터리를 ‘마우스 오른쪽 단추로 클릭’하고 "보내기", "압축 폴더"를 차례로 선택합니다. </span><span class="sxs-lookup"><span data-stu-id="45e37-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![마우스 오른쪽 단추로 클릭](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="45e37-119">리소스 보관 파일 이름 지정</span><span class="sxs-lookup"><span data-stu-id="45e37-119">Naming the Resource Archive</span></span>

<span data-ttu-id="45e37-120">다음 형식을 사용하여 리소스 보관 파일 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="45e37-121">위의 예제에서 "xPSDesiredStateConfiguration.zip"의 이름을 "xPSDesiredStateConfiguration_8.4.4.0.zip"으로 바꿔야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="45e37-122">CheckSum 만들기</span><span class="sxs-lookup"><span data-stu-id="45e37-122">Create CheckSums</span></span>

<span data-ttu-id="45e37-123">리소스 모듈이 압축되고 이름이 바뀐 후 **CheckSum**을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="45e37-124">**CheckSum**은 클라이언트의 LCM에서 리소스가 변경되었고 다시 다운로드되어야 하는지 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="45e37-125">아래 예제와 같이 **New-DSCCheckSum** cmdlet을 사용하여 [CheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="45e37-126">출력은 표시되지 않지만 이제 "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum" 파일이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="45e37-127">`New-DSCCheckSum` 매개 변수를 사용하여 파일 디렉터리에서 `-Path`을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="45e37-128">체크섬이 이미 있는 경우 `-Force` 매개 변수를 사용하여 체크섬을 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="45e37-129">리소스 보관 파일을 저장할 위치</span><span class="sxs-lookup"><span data-stu-id="45e37-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="45e37-130">DSC HTTP 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="45e37-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="45e37-131">HTTP 끌어오기 서버를 설정할 때 [DSC HTTP 끌어오기 서버 설정](pullServer.md)에 설명된 대로 **ModulePath** 및 **ConfigurationPath** 키의 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="45e37-132">**ConfigurationPath** 키는 ".mof" 파일을 저장해야 하는 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="45e37-133">**ModulePath**는 DSC 리소스 모듈을 저장해야 하는 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="45e37-134">SMB 공유</span><span class="sxs-lookup"><span data-stu-id="45e37-134">On an SMB Share</span></span>

<span data-ttu-id="45e37-135">**ResourceRepositoryShare**를 지정한 경우 끌어오기 클라이언트를 설정할 때 **ResourceRepositoryShare** 블록의 **SourcePath** 디렉터리에 보관 파일과 체크섬을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

<span data-ttu-id="45e37-136">**ConfigurationRepositoryShare**만 지정한 경우 끌어오기 클라이언트를 설정할 때 **ConfigurationRepositoryShare** 블록의 **SourcePath** 디렉터리에 보관 파일과 체크섬을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="45e37-137">리소스 업데이트</span><span class="sxs-lookup"><span data-stu-id="45e37-137">Updating resources</span></span>

<span data-ttu-id="45e37-138">보관 파일의 이름에서 버전 번호를 변경하거나 새 체크섬을 만들어 노드가 강제로 해당 리소스를 업데이트하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="45e37-139">끌어오기 클라이언트는 필요한 리소스의 최신 버전을 확인할 뿐 아니라 해당 LCM을 새로 고칠 때 업데이트된 체크섬을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="45e37-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="45e37-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45e37-140">See also</span></span>

- [<span data-ttu-id="45e37-141">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="45e37-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="45e37-142">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="45e37-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

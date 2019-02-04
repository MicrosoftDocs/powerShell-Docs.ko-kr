---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 패키지 및 끌어오기 서버에 업로드 리소스
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682968"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="cee27-103">패키지 및 끌어오기 서버에 업로드 리소스</span><span class="sxs-lookup"><span data-stu-id="cee27-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="cee27-104">아래 섹션에서는 끌어오기 서버를 설정한 이미 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="cee27-105">끌어오기 서버를 설정 하지 않은 경우에 다음 가이드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="cee27-106">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="cee27-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="cee27-107">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="cee27-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="cee27-108">각 대상 노드를 구성, 리소스를 다운로드 하 여 해당 상태를 보고할 수도 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="cee27-109">이 문서에서는, 다운로드 하 고 리소스를 자동으로 다운로드 하도록 클라이언트 구성에 사용할 수 있도록 리소스를 업로드 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="cee27-110">노드를 통해 할당된 된 구성의 받을 때 **끌어오기** 하거나 **푸시** (v5)에 자동으로 다운로드 LCM에 지정 된 위치에서 구성에 필요한 모든 리소스.</span><span class="sxs-lookup"><span data-stu-id="cee27-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="cee27-111">패키지 리소스 모듈</span><span class="sxs-lookup"><span data-stu-id="cee27-111">Package Resource Modules</span></span>

<span data-ttu-id="cee27-112">각 리소스를 다운로드 하려면 클라이언트에 사용할 수 있는 ".zip" 파일에 저장 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="cee27-113">아래 예제를 사용 하는 데 필요한 단계에 표시 됩니다는 [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="cee27-114">PowerShell 4.0을 사용 하는 모든 클라이언트에 있으면 리소스 폴더 구조를 flaten 해야 하 고 버전 폴더를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="cee27-115">자세한 내용은 [여러 리소스 버전](../configurations/import-dscresource.md#multiple-resource-versions)합니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="cee27-116">모든 유틸리티, 스크립트 또는 선호 하는 메서드를 사용 하 여 리소스 디렉터리를 압축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="cee27-117">Windows를 수행할 수 있습니다 *마우스 오른쪽 단추로 클릭* "xPSDesiredStateConfiguration" 디렉터리에 "송신", 한 다음 "압축 된 폴더"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![마우스 오른쪽 단추로 클릭](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="cee27-119">리소스 보관 파일 이름 지정</span><span class="sxs-lookup"><span data-stu-id="cee27-119">Naming the Resource Archive</span></span>

<span data-ttu-id="cee27-120">리소스 보관 파일을 다음 형식으로 명명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="cee27-121">위의 예에서 "xPSDesiredStateConfiguration.zip" 이름이 바뀐된 "xPSDesiredStateConfiguration_8.4.4.0.zip" 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="cee27-122">체크섬 만들기</span><span class="sxs-lookup"><span data-stu-id="cee27-122">Create CheckSums</span></span>

<span data-ttu-id="cee27-123">만들려는 리소스 모듈 압축 되었으며 이름이 변경 되 면을 **체크섬**합니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="cee27-124">합니다 **체크섬** 되, 클라이언트에서 LCM에 의해 확인 변경 된 리소스를 다시 다운로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="cee27-125">만들 수 있습니다는 **체크섬** 사용 하 여 합니다 [New-dscchecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) , 아래 예제와 같이 cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cee27-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="cee27-126">출력 없음, 표시 되지만 "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum" 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="cee27-127">실행할 수도 있습니다 `New-DSCCheckSum` 사용 하 여 파일의 디렉터리와 비교 합니다 `-Path` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="cee27-128">체크섬을 이미 있는 경우 적용할 수 있습니다 사용 하 여 다시 만들어야 합니다 `-Force` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="cee27-129">리소스 보관 파일을 저장할 위치</span><span class="sxs-lookup"><span data-stu-id="cee27-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="cee27-130">DSC HTTP 끌어오기 서버에서</span><span class="sxs-lookup"><span data-stu-id="cee27-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="cee27-131">설정할 때 HTTP 끌어오기 서버에 설명 된 대로 [DSC HTTP 끌어오기 서버 설정](pullServer.md)에 대 한 디렉터리를 지정 합니다 **ModulePath** 및 **ConfigurationPath** 키입니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="cee27-132">합니다 **ConfigurationPath** 키 ".mof" 파일이 저장 될 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="cee27-133">합니다 **ModulePath** 모든 DSC 리소스 모듈이 저장 될 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="cee27-134">SMB 공유에</span><span class="sxs-lookup"><span data-stu-id="cee27-134">On an SMB Share</span></span>

<span data-ttu-id="cee27-135">지정한 경우는 **ResourceRepositoryShare**보관 및 체크섬 끌어오기 클라이언트 설정 저장 하는 경우를 **SourcePath** 디렉터리는 **ResourceRepositoryShare** 블록.</span><span class="sxs-lookup"><span data-stu-id="cee27-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

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

<span data-ttu-id="cee27-136">만 지정한 경우는 **ConfigurationRepositoryShare**보관 및 체크섬 끌어오기 클라이언트 설정 저장 하는 경우를 **SourcePath** 디렉터리는  **ConfigurationRepositoryShare** 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="cee27-137">리소스 업데이트</span><span class="sxs-lookup"><span data-stu-id="cee27-137">Updating resources</span></span>

<span data-ttu-id="cee27-138">보관 파일의 이름에 버전 번호를 변경 하거나 새 체크섬을 만들어 해당 리소스를 업데이트 하려면 노드를 강제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="cee27-139">끌어오기 클라이언트는 필요한 리소스의 최신 버전 확인 뿐만 아니라 해당 LCM 새로 고칠 때 체크섬을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="cee27-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="cee27-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cee27-140">See also</span></span>

- [<span data-ttu-id="cee27-141">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="cee27-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="cee27-142">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="cee27-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

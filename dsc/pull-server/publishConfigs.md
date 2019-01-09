---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 구성 Id (v4/v5)를 사용 하 여 끌어오기 서버에 게시
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402399"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="1c55b-103">구성 Id (v4/v5)를 사용 하 여 끌어오기 서버에 게시</span><span class="sxs-lookup"><span data-stu-id="1c55b-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="1c55b-104">아래 섹션에서는 끌어오기 서버를 설정한 이미 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="1c55b-105">끌어오기 서버를 설정 하지 않은 경우에 다음 가이드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="1c55b-106">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="1c55b-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="1c55b-107">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="1c55b-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="1c55b-108">각 대상 노드를 구성, 리소스를 다운로드 하 여 해당 상태를 보고할 수도 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="1c55b-109">이 문서에서는, 다운로드 하 고 리소스를 자동으로 다운로드 하도록 클라이언트 구성에 사용할 수 있도록 리소스를 업로드 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="1c55b-110">노드를 통해 할당된 된 구성의 받을 때 **끌어오기** 하거나 **푸시** (v5)에 자동으로 다운로드 LCM에 지정 된 위치에서 구성에 필요한 모든 리소스.</span><span class="sxs-lookup"><span data-stu-id="1c55b-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="1c55b-111">구성 컴파일</span><span class="sxs-lookup"><span data-stu-id="1c55b-111">Compile Configurations</span></span>

<span data-ttu-id="1c55b-112">저장 하 고 첫 번째 단계로 [구성을](../configurations/configurations.md) ".mof" 파일로 컴파일하는 끌어오기 서버에서.</span><span class="sxs-lookup"><span data-stu-id="1c55b-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="1c55b-113">제네릭 및 더 많은 클라이언트에 적용 가능한 구성 되도록 사용 하 여 `localhost` 노드 블록에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="1c55b-114">아래 예제에서는 표시를 사용 하는 구성 셸을 `localhost` 특정 클라이언트 이름 대신 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="1c55b-115">일반 구성, 컴파일되면 "localhost.mof" 파일이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="1c55b-116">MOF 파일 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="1c55b-116">Renaming the MOF file</span></span>

<span data-ttu-id="1c55b-117">제공 하는 끌어오기 서버의 구성 ".mof" 파일을 저장할 수 있습니다 **ConfigurationName** 하거나 **ConfigurationID**합니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="1c55b-118">끌어오기 클라이언트 설정 하려는 방법에 따라 올바르게 컴파일된 ".mof" 파일의 이름을 바꾸려면 아래 섹션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="1c55b-119">구성 Id (GUID)</span><span class="sxs-lookup"><span data-stu-id="1c55b-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="1c55b-120">하기 위해 "localhost.mof" 파일 이름을 변경 해야 합니다 "<GUID>.mof" 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="1c55b-121">임의 만들 수 있습니다 **Guid** 아래 또는 사용 하 여 예제를 사용 하 여 [New-guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c55b-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="1c55b-122">샘플 출력</span><span class="sxs-lookup"><span data-stu-id="1c55b-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="1c55b-123">그런 다음 허용 가능한 메서드를 사용 하 여 ".mof" 파일을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="1c55b-124">아래 예제에서 사용 하는 [Rename-item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c55b-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="1c55b-125">사용에 대 한 자세한 내용은 **Guid** 환경에서 참조 [Guid에 대 한 계획](/powershell/dsc/secureserver#guids)합니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="1c55b-126">구성 이름</span><span class="sxs-lookup"><span data-stu-id="1c55b-126">Configuration Names</span></span>

<span data-ttu-id="1c55b-127">하기 위해 "localhost.mof" 파일 이름을 변경 해야 합니다 "<Configuration Name>.mof" 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="1c55b-128">다음 예제에서는 이전 섹션의 구성 이름을 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="1c55b-129">그런 다음 허용 가능한 메서드를 사용 하 여 ".mof" 파일을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="1c55b-130">아래 예제에서 사용 하는 [Rename-item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c55b-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="1c55b-131">체크섬 만들기</span><span class="sxs-lookup"><span data-stu-id="1c55b-131">Create the CheckSum</span></span>

<span data-ttu-id="1c55b-132">각 ".mof" 파일 연결된 ".checksum" 파일로 있어야 끌어오기 서버 또는 SMB 공유에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="1c55b-133">이 파일에는 클라이언트가 연결된 ".mof" 파일에 변경 하 고 다시 다운로드 해야 하는 경우 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="1c55b-134">만들 수 있습니다는 **체크섬** 사용 하 여 합니다 [New-dscchecksum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c55b-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="1c55b-135">실행할 수도 있습니다 `New-DSCCheckSum` 사용 하 여 파일의 디렉터리와 비교 합니다 `-Path` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="1c55b-136">체크섬을 이미 있는 경우 적용할 수 있습니다 사용 하 여 다시 만들어야 합니다 `-Force` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="1c55b-137">다음 예제에서는 이전 섹션에서 ".mof" 파일이 포함 된 디렉터리를 지정 하 고 사용 하 여 `-Force` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="1c55b-138">출력이 표시 됩니다 있지만 이제는 "<GUID or Configuration Name>. mof.checksum" 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="1c55b-139">MOF 파일 및 체크섬을 저장할 위치</span><span class="sxs-lookup"><span data-stu-id="1c55b-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="1c55b-140">DSC HTTP 끌어오기 서버에서</span><span class="sxs-lookup"><span data-stu-id="1c55b-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="1c55b-141">설정할 때 HTTP 끌어오기 서버에 설명 된 대로 [DSC HTTP 끌어오기 서버 설정](pullServer.md)에 대 한 디렉터리를 지정 합니다 **ModulePath** 및 **ConfigurationPath** 키입니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="1c55b-142">합니다 **ConfigurationPath** 키 ".mof" 파일이 저장 될 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="1c55b-143">합니다 **ConfigurationPath** ".mof" 파일과 ".checksum" 파일 저장 될 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="1c55b-144">SMB 공유에</span><span class="sxs-lookup"><span data-stu-id="1c55b-144">On an SMB Share</span></span>

<span data-ttu-id="1c55b-145">SMB 공유를 사용 하 여 끌어오기 클라이언트를 설정 하는 경우 지정 된 **ConfigurationRepositoryShare**합니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="1c55b-146">모든 ".mof" 파일과 ".checksum" 다음에 저장할지를 **SourcePath** 에서 디렉터리를 **ConfigurationRepositoryShare** 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="1c55b-147">다음 단계</span><span class="sxs-lookup"><span data-stu-id="1c55b-147">Next Steps</span></span>

<span data-ttu-id="1c55b-148">다음으로, 지정 된 구성을 끌어오기를 끌어오기 클라이언트를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c55b-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="1c55b-149">자세한 내용은 다음 가이드 중 하나를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c55b-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="1c55b-150">구성 Id (v4)를 사용 하 여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="1c55b-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="1c55b-151">구성 Id (v5)를 사용 하 여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="1c55b-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="1c55b-152">구성 이름 (v5)를 사용 하 여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="1c55b-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="1c55b-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1c55b-153">See also</span></span>

- [<span data-ttu-id="1c55b-154">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="1c55b-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="1c55b-155">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="1c55b-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="1c55b-156">패키지 및 끌어오기 서버에 업로드 리소스</span><span class="sxs-lookup"><span data-stu-id="1c55b-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)

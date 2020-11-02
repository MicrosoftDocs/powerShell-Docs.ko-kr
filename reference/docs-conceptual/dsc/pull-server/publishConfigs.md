---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 구성 ID를 사용하여 끌어오기 서버에 게시(v4/v5)
description: 이 문서에서는 다운로드할 수 있도록 리소스를 업로드하고 자동으로 리소스를 다운로드하도록 클라이언트를 구성하는 방법을 보여 줍니다.
ms.openlocfilehash: 20e12e3cac6b6e4a86563576f4a915429b18aadb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646829"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="d2921-104">구성 ID를 사용하여 끌어오기 서버에 게시(v4/v5)</span><span class="sxs-lookup"><span data-stu-id="d2921-104">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="d2921-105">아래 섹션에서는 끌어오기 서버를 이미 설정했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-105">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="d2921-106">끌어오기 서버를 설정하지 않은 경우에는 다음 가이드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-106">If you haven't set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="d2921-107">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="d2921-107">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="d2921-108">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="d2921-108">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="d2921-109">구성, 리소스를 다운로드하고 해당 상태를 보고하도록 각 대상 노드를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-109">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="d2921-110">이 문서에서는 다운로드할 수 있도록 리소스를 업로드하고 자동으로 리소스를 다운로드하도록 클라이언트를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-110">This article shows you how to upload resources so they're available to be downloaded, and configure clients to automatically download resources.</span></span> <span data-ttu-id="d2921-111">노드가 할당된 구성을 받으면 **끌어오기** 또는 **밀어넣기** (v5)를 통해 LCM(로컬 구성 관리자)의 지정된 위치에서 구성에 필요한 모든 리소스를 자동으로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-111">When the node receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the Local Configuration Manager (LCM).</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="d2921-112">구성 컴파일</span><span class="sxs-lookup"><span data-stu-id="d2921-112">Compile configurations</span></span>

<span data-ttu-id="d2921-113">끌어오기 서버에서 [구성](../configurations/configurations.md)을 저장하는 첫 번째 단계는 구성을 `.mof` 파일로 컴파일하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-113">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into `.mof` files.</span></span> <span data-ttu-id="d2921-114">구성을 제네릭으로 설정하고 더 많은 클라이언트에 적용하려면 Node 블록에서 `localhost`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-114">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="d2921-115">아래 예제에서는 특정 클라이언트 이름 대신 `localhost`를 사용하는 구성 셸을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-115">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="d2921-116">일반 구성을 컴파일한 후에는 `localhost.mof` 파일이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-116">Once you've compiled your generic configuration, you should have a `localhost.mof` file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="d2921-117">MOF 파일 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="d2921-117">Renaming the MOF file</span></span>

<span data-ttu-id="d2921-118">**ConfigurationName** 또는 **ConfigurationID** 를 통해 끌어오기 서버에서 구성 `.mof` 파일을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-118">You can store Configuration `.mof` files on a Pull Server by **ConfigurationName** or **ConfigurationID** .</span></span> <span data-ttu-id="d2921-119">끌어오기 클라이언트 설정을 어떻게 계획하는지에 따라 아래 섹션을 선택하여 컴파일된 `.mof` 파일의 이름을 제대로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-119">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled `.mof` files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="d2921-120">구성 ID(GUID)</span><span class="sxs-lookup"><span data-stu-id="d2921-120">Configuration IDs (GUID)</span></span>

<span data-ttu-id="d2921-121">파일의 이름을 `localhost.mof` 파일에서 `<GUID>.mof` 파일로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-121">You'll need to rename your `localhost.mof` file to `<GUID>.mof` file.</span></span> <span data-ttu-id="d2921-122">아래 예제 또는 [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet을 사용하여 임의의 **Guid** 를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-122">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="d2921-123">샘플 출력</span><span class="sxs-lookup"><span data-stu-id="d2921-123">Sample Output</span></span>

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="d2921-124">그런 다음, 허용되는 메서드를 사용하여 `.mof` 파일의 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-124">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="d2921-125">아래 예제에서는 [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-125">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="d2921-126">환경에서 **Guid** 를 사용하는 방법에 대한 자세한 내용은 [Guid에 대한 계획](secureServer.md#guids)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2921-126">For more information about using **Guids** in your environment, see [Plan for Guids](secureServer.md#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="d2921-127">구성 이름</span><span class="sxs-lookup"><span data-stu-id="d2921-127">Configuration names</span></span>

<span data-ttu-id="d2921-128">파일의 이름을 `localhost.mof` 파일에서 `<Configuration Name>.mof` 파일로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-128">You'll need to rename your `localhost.mof` file to `<Configuration Name>.mof` file.</span></span> <span data-ttu-id="d2921-129">다음 예제에서는 이전 섹션의 구성 이름이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-129">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="d2921-130">그런 다음, 허용되는 메서드를 사용하여 `.mof` 파일의 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-130">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="d2921-131">아래 예제에서는 [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-131">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="d2921-132">체크섬 만들기</span><span class="sxs-lookup"><span data-stu-id="d2921-132">Create the checkSum</span></span>

<span data-ttu-id="d2921-133">끌어오기 서버에 저장된 각 `.mof` 파일 또는 SMB 공유에는 연결된 `.checksum` 파일이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-133">Each `.mof` file stored on a Pull Server, or SMB share needs to have an associated `.checksum` file.</span></span>
<span data-ttu-id="d2921-134">이 파일을 통해 클라이언트는 연결된 `.mof` 파일이 변경되어 다시 다운로드되어야 하는 시기를 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-134">This file lets clients know when the associated `.mof` file has changed and should be downloaded again.</span></span>

<span data-ttu-id="d2921-135">[New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet을 사용하여 **CheckSum** 을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-135">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="d2921-136">`-Path` 매개 변수를 사용하여 파일 디렉터리에서 `New-DSCCheckSum`을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-136">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span>
<span data-ttu-id="d2921-137">체크섬이 이미 있는 경우 `-Force` 매개 변수를 사용하여 체크섬을 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-137">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="d2921-138">다음 예제에서는 이전 섹션의 `.mof` 파일을 포함하는 디렉터리를 지정했고 `-Force` 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-138">The following example specified a directory containing the `.mof` file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="d2921-139">출력은 표시되지 않지만 이제 `<GUID or Configuration Name>.mof.checksum` 파일이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-139">No output will be shown, but you should now see a `<GUID or Configuration Name>.mof.checksum` file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="d2921-140">MOF 파일 및 체크섬을 저장할 위치</span><span class="sxs-lookup"><span data-stu-id="d2921-140">Where to store MOF files and checkSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="d2921-141">DSC HTTP 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="d2921-141">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="d2921-142">HTTP 끌어오기 서버를 설정할 때 [DSC HTTP 끌어오기 서버 설정](pullServer.md)에 설명된 대로 **ModulePath** 및 **ConfigurationPath** 키의 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-142">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="d2921-143">**ModulePath** 키는 모듈의 패키지 `.zip` 파일을 저장할 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-143">The **ModulePath** key indicates where a module's packaged `.zip` files should be stored.</span></span> <span data-ttu-id="d2921-144">**ConfigurationPath** 는 `.mof` 파일과 `.checksum` 파일을 저장해야 하는 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-144">The **ConfigurationPath** indicates where any `.mof` files and `.checksum` files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="d2921-145">SMB 공유</span><span class="sxs-lookup"><span data-stu-id="d2921-145">On an SMB share</span></span>

<span data-ttu-id="d2921-146">SMB 공유를 사용하도록 끌어오기 클라이언트를 설정할 때 **ConfigurationRepositoryShare** 를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-146">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare** .</span></span>
<span data-ttu-id="d2921-147">모든 `.mof` 파일과 `.checksum` 파일은 **ConfigurationRepositoryShare** 블록의 **SourcePath** 디렉터리에 저장되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-147">All `.mof` files and `.checksum` files should be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="d2921-148">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d2921-148">Next steps</span></span>

<span data-ttu-id="d2921-149">다음으로, 지정된 구성을 끌어오도록 끌어오기 클라이언트를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2921-149">Next, you'll want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="d2921-150">자세한 내용은 다음 가이드 중 하나를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2921-150">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="d2921-151">구성 ID를 사용하여 끌어오기 클라이언트 설정(v4)</span><span class="sxs-lookup"><span data-stu-id="d2921-151">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="d2921-152">구성 ID를 사용하여 끌어오기 클라이언트 설정(v5)</span><span class="sxs-lookup"><span data-stu-id="d2921-152">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="d2921-153">구성 이름을 사용하여 끌어오기 클라이언트 설정(v5)</span><span class="sxs-lookup"><span data-stu-id="d2921-153">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="d2921-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2921-154">See also</span></span>

- [<span data-ttu-id="d2921-155">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="d2921-155">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="d2921-156">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="d2921-156">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="d2921-157">리소스 패키지 및 끌어오기 서버에 업로드</span><span class="sxs-lookup"><span data-stu-id="d2921-157">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)

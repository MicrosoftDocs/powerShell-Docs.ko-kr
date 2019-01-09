---
ms.date: 12/12/2018
keywords: dsc, powershell, 구성, 서비스, 설치
title: 구성 작성, 컴파일 및 적용
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402348"
---
> <span data-ttu-id="3eac9-103">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3eac9-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="3eac9-104">구성 작성, 컴파일 및 적용</span><span class="sxs-lookup"><span data-stu-id="3eac9-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="3eac9-105">이 연습에서는 DSC(필요한 상태 구성) 구성을 만들고 적용하는 과정을 처음부터 끝까지 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="3eac9-106">다음 예제에서는 작성 하는 매우 간단한 구성을 적용 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="3eac9-107">"HelloWorld.txt" 파일이 로컬 컴퓨터에 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="3eac9-108">파일을 삭제 하는 경우 DSC는 다시 다음에 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="3eac9-109">DSC 란 무엇 이며 작동 원리의 개요를 참조 하세요 [개발자를 위한 개요 Desired State Configuration](../overview/overview.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="3eac9-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="3eac9-110">Requirements</span></span>

<span data-ttu-id="3eac9-111">이 예제를 실행 하려면 PowerShell 4.0 이상을 실행 하 고 컴퓨터를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="3eac9-112">구성 작성</span><span class="sxs-lookup"><span data-stu-id="3eac9-112">Write the configuration</span></span>

<span data-ttu-id="3eac9-113">DSC [구성](configurations.md)은 하나 이상의 대상 컴퓨터(노드)를 구성할 방법을 정의하는 특수한 PowerShell 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="3eac9-114">PowerShell ISE 또는 다른 PowerShell 편집기에서 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

<span data-ttu-id="3eac9-115">"HelloWorld.ps1"로 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="3eac9-116">구성을 정의 하는 것은 함수 정의 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="3eac9-117">**Node** 블록은 구성할 대상 노드를 지정하며, 이 경우는 `localhost`입니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="3eac9-118">구성을 하나를 호출 [리소스](../resources/resources.md)는 `File` 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="3eac9-119">리소스는 대상 노드가 구성에 정의된 상태에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="3eac9-120">구성 컴파일</span><span class="sxs-lookup"><span data-stu-id="3eac9-120">Compile the configuration</span></span>

<span data-ttu-id="3eac9-121">노드에 DSC 구성을 적용하려면 먼저 MOF 파일로 컴파일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="3eac9-122">구성을 함수 처럼 실행 정의한 모든 노드에 대해 하나의 ".mof" 파일을 컴파일하는 `Node` 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="3eac9-123">구성을 실행 하기 위해 해야 할 *도트 소싱* "HelloWorld.ps1" 스크립트를 현재 범위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="3eac9-124">자세한 내용은 [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing)합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<span data-ttu-id="3eac9-125">*도트 소싱* 를 저장 한 경로로, 뒤에 입력 하 여 "HelloWorld.ps1" 스크립트는 `. ` (점, 공백).</span><span class="sxs-lookup"><span data-stu-id="3eac9-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="3eac9-126">그런 다음 할 구성을 함수 처럼 호출 하 여 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-126">You may then, run your configuration by calling it like a Function.</span></span>

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

<span data-ttu-id="3eac9-127">그러면 다음과 같은 출력이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="3eac9-128">구성 적용</span><span class="sxs-lookup"><span data-stu-id="3eac9-128">Apply the configuration</span></span>

<span data-ttu-id="3eac9-129">이제 MOF를 컴파일했으므로 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 호출하여 구성을 대상 노드(이 경우 로컬 컴퓨터)에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="3eac9-130">`Start-DscConfiguration` cmdlet 지시 합니다 [구성 관리자 (LCM (로컬)](../managing-nodes/metaConfig.md), 구성을 적용 하려면 DSC의 엔진입니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="3eac9-131">LCM은 DSC 리소스를 호출하여 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="3eac9-132">아래 코드를 사용 하 여 실행 된 `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3eac9-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="3eac9-133">"localhost.mof" 저장 된 디렉터리 경로 지정 합니다 `-Path` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="3eac9-134">합니다 `Start-DSCConfiguration` cmdlet에 대 한 지정 된 디렉터리를 조사 "\<computername\>.mof" 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="3eac9-135">`Start-DSCConfiguration` cmdlet은 찾은 각 ".mof" 파일 이름 ("localhost", "server01", "dc-02" 등)으로 지정 된 컴퓨터 이름에 적용 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="3eac9-136">경우는 `-Wait` 매개 변수를 지정 하지 않으면 `Start-DSCConfiguration` 작업을 수행 하는 백그라운드 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="3eac9-137">지정 하는 `-Verbose` 매개 변수를 사용 하면 볼 수 있습니다 합니다 **Verbose** 작업의 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="3eac9-138">`-Wait`및 `-Verbose` 모두 선택적 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="3eac9-139">구성 테스트</span><span class="sxs-lookup"><span data-stu-id="3eac9-139">Test the configuration</span></span>

<span data-ttu-id="3eac9-140">한 번의 `Start-DSCConfiguration` cmdlet 완료 되 면 지정한 위치에 있는 "HelloWorld.txt" 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="3eac9-141">포함 된 콘텐츠를 확인할 수 있습니다 합니다 [Get-content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3eac9-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="3eac9-142">할 수도 있습니다 *테스트할* 사용 하 여 현재 상태 [Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="3eac9-143">출력 노드는 현재 적용된 된 구성을 준수 하는 경우 "True" 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="3eac9-144">구성을 다시 적용</span><span class="sxs-lookup"><span data-stu-id="3eac9-144">Re-applying the configuration</span></span>

<span data-ttu-id="3eac9-145">구성을 다시 적용 하세요를 구성 하 여 만든 텍스트 파일을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="3eac9-146">사용 합니다 `Start-DSCConfiguration` cmdlet을 사용 합니다 `-UseExisting` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="3eac9-147">합니다 `-UseExisting` 매개 변수 지시 `Start-DSCConfiguration` "current.mof" 파일에 다시 적용 하려면 구성 적용을 가장 최근에 성공적으로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="3eac9-148">다음 단계</span><span class="sxs-lookup"><span data-stu-id="3eac9-148">Next steps</span></span>

- <span data-ttu-id="3eac9-149">DSC 구성에 대한 자세한 내용은 [DSC 구성](configurations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eac9-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="3eac9-150">[DSC 리소스](../resources/resources.md)에서는 어떤 DSC 리소스를 사용할 수 있으며 사용자 지정 DSC 리소스를 만드는 방법은 무엇인지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="3eac9-151">[PowerShell 갤러리](https://www.powershellgallery.com/)에서는 DSC 구성 및 리소스를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eac9-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

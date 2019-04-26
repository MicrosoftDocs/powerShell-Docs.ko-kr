---
title: PowerShell 이진 모듈을 작성 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: 9ddb3bc172c66314603d2be4df5192a76c92e05d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082229"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="1e0ed-102">PowerShell 이진 모듈을 작성하는 방법</span><span class="sxs-lookup"><span data-stu-id="1e0ed-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="1e0ed-103">이진 모듈에는 cmdlet 클래스를 포함 하는 모든 어셈블리 (.dll) 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="1e0ed-104">기본적으로 이진 모듈을 가져올 때 어셈블리의 모든 cmdlet은 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="1e0ed-105">그러나 해당 루트 모듈은 어셈블리 모듈 매니페스트 만들기에서 가져온 cmdlet을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="1e0ed-106">(예를 들어 매니페스트의 CmdletsToExport 키를 사용할 수 있음 필요한 cmdlet만을 내보내려면.) 또한 이진 모듈 추가 파일, 디렉터리 구조와 다른 단일 cmdlet 없는 유용한 관리 정보에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="1e0ed-107">다음 절차를 만들고 PowerShell 이진 모듈을 설치 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="1e0ed-108">만들기 및 PowerShell 이진 모듈을 설치 하는 방법</span><span class="sxs-lookup"><span data-stu-id="1e0ed-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="1e0ed-109">이진 PowerShell 솔루션을 만듭니다 (작성 된 cmdlet와 같은 C#), 기능을 사용 하 여 필요한 하 고이 제대로 실행 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="1e0ed-110">코드의 관점에서 이진 모듈의 핵심에는 단순히 cmdlet 어셈블리입니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="1e0ed-111">사실, PowerShell에서 cmdlet을 단일 어셈블리를 로드 / 언로드에 개발자 추가 작업 없이 측면에서 모듈로 간주 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="1e0ed-112">Cmdlet을 작성 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell Cmdlet 작성](../cmdlet/writing-a-windows-powershell-cmdlet.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="1e0ed-113">필요한 경우 솔루션의 나머지 부분을 만듭니다. (추가 cmdlet, XML 파일 및 등) 및 모듈 매니페스트를 사용 하 여 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="1e0ed-114">솔루션에서 cmdlet 어셈블리를 설명 하는 것 외에도 원하는 내보내고 가져올 모듈, cmdlet, 노출 되 고 모듈로 이동 하는 추가 파일은 모듈 매니페스트를 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span> <span data-ttu-id="1e0ed-115">그러나 앞에서 설명한 대로 PowerShell 모듈을 추가 작업 없이 같은 이진 cmdlet을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span> <span data-ttu-id="1e0ed-116">따라서 모듈 매니페스트는 주로 단일 패키지에 여러 파일 결합 또는 명시적으로 지정된 된 어셈블리에 대 한 게시를 제어 하기 위한에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span> <span data-ttu-id="1e0ed-117">자세한 내용은 [PowerShell 모듈 매니페스트 작성 방법](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-117">For more information, see [How to Write a PowerShell Module Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span></span>

   <span data-ttu-id="1e0ed-118">다음 코드는 매우 간단한 C# 모듈로 사용할 수 있는 동일한 파일에서 세 개의 cmdlet을 포함 하는 코드 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. <span data-ttu-id="1e0ed-119">솔루션 패키지에 패키지 위치를 저장 및 PowerShell 모듈 경로에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="1e0ed-120">`PSModulePath` 전역 환경 변수는 PowerShell 모듈을 찾을를 사용 하 여 기본 경로 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="1e0ed-121">예를 들어, 시스템에서 모듈을 저장 하기 위한 일반적인 경로 것 `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`입니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="1e0ed-122">기본 경로 사용 하지 않는 경우 명시적으로 설치 하는 동안 모듈의 위치를 명시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="1e0ed-123">여러 어셈블리 및 솔루션에 대 한 파일을 저장할 폴더를 해야 하는 대로 모듈을 저장 폴더를 만들어 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="1e0ed-124">기술적으로 수행 되지 해야에 어디서 나 모듈을 설치 하는 `PSModulePath` -것은 PowerShell 모듈에 대해 검색 하는 기본 위치 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="1e0ed-125">그러나 어딘가 다른 모듈을 저장 하는 것에 대 한 이유가 없다면이 위해 모범 사례를 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="1e0ed-126">자세한 내용은 [PowerShell 모듈 설치](./installing-a-powershell-module.md) 하 고 [PowerShell 모듈 설치 경로 수정](./modifying-the-psmodulepath-installation-path.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="1e0ed-127">호출 하 여 PowerShell 모듈 가져오기 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="1e0ed-128">호출 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 모듈 활성 메모리에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="1e0ed-129">PowerShell 3.0을 사용 하 고 나중에 호출 하는 경우 코드에서 모듈의 이름을 가져올 수도; 자세한 내용은 [PowerShell 모듈을 가져오는](./importing-a-powershell-module.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="1e0ed-130">모듈로 스냅인 어셈블리 가져오기</span><span class="sxs-lookup"><span data-stu-id="1e0ed-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="1e0ed-131">이진 모듈로 스냅인 어셈블리에 존재 하는 Cmdlet 및 공급자를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="1e0ed-132">스냅인 어셈블리 이진 모듈을 로드할 경우 스냅인의 공급자와 cmdlet은 사용자에 게 사용할 수 있지만 어셈블리에 스냅인 클래스 무시 되 고 스냅인을 등록 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="1e0ed-133">결과적으로, cmdlet 및 공급자를 세션에 사용할 수 있지만 Windows PowerShell에서 제공 된 스냅인 cmdlet은 스냅인을 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="1e0ed-134">또한 이진 모듈의 일부로 스냅인에서 참조 하는 모든 형식 또는 형식 파일을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span> <span data-ttu-id="1e0ed-135">서식 지정 및 형식 파일을 가져오는 모듈 매니페스트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-135">To import the formatting and types files you must create a module manifest.</span></span> <span data-ttu-id="1e0ed-136">하세요 [PowerShell 모듈 매니페스트를 작성 하는 방법을](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)합니다.</span><span class="sxs-lookup"><span data-stu-id="1e0ed-136">See, [How to Write a PowerShell Module Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e0ed-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e0ed-137">See Also</span></span>

[<span data-ttu-id="1e0ed-138">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="1e0ed-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

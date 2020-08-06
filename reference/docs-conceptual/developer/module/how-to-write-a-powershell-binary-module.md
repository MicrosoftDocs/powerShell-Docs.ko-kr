---
title: PowerShell 이진 모듈을 작성 하는 방법 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 92395bd6b8be1bd3741888eb3716d62f0253e213
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779270"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="052c7-102">PowerShell 이진 모듈을 작성하는 방법</span><span class="sxs-lookup"><span data-stu-id="052c7-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="052c7-103">이진 모듈은 cmdlet 클래스를 포함 하는 모든 어셈블리 (.dll)가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="052c7-104">기본적으로 이진 모듈을 가져올 때 어셈블리의 모든 cmdlet을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="052c7-105">그러나 루트 모듈이 어셈블리인 모듈 매니페스트를 만들어 가져오는 cmdlet을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="052c7-106">예를 들어 매니페스트의 CmdletsToExport 키를 사용 하 여 필요한 cmdlet만 내보낼 수 있습니다. 또한 이진 모듈에는 단일 cmdlet에서 사용할 수 없는 추가 파일, 디렉터리 구조 및 유용한 관리 정보의 다른 부분이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="052c7-107">다음 절차에서는 PowerShell 이진 모듈을 만들고 설치 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="052c7-108">PowerShell 이진 모듈을 만들고 설치 하는 방법</span><span class="sxs-lookup"><span data-stu-id="052c7-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="052c7-109">필요한 기능이 포함 된 이진 PowerShell 솔루션 (예: c #으로 작성 된 cmdlet)을 만들고 제대로 실행 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="052c7-110">코드 관점에서 이진 모듈의 핵심은 단순히 cmdlet 어셈블리입니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="052c7-111">실제로 PowerShell은 로드 및 언로드 측면에서 단일 cmdlet 어셈블리를 모듈로 처리 하며 개발자의 추가 작업은 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="052c7-112">Cmdlet을 작성 하는 방법에 대 한 자세한 내용은 [Windows PowerShell Cmdlet 작성](../cmdlet/writing-a-windows-powershell-cmdlet.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="052c7-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="052c7-113">필요한 경우 추가 cmdlet, XML 파일 등의 나머지 솔루션을 만들고 모듈 매니페스트를 사용 하 여 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="052c7-114">모듈 매니페스트는 솔루션의 cmdlet 어셈블리를 설명 하는 것 외에도 모듈을 내보내고 가져오는 방법, 노출 되는 cmdlet 및 모듈에 추가 되는 추가 파일을 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="052c7-115">앞서 설명한 것 처럼 PowerShell은 추가 작업 없이 모듈 처럼 이진 cmdlet을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="052c7-116">따라서 모듈 매니페스트는 주로 여러 파일을 단일 패키지로 결합 하거나 지정 된 어셈블리에 대 한 게시를 명시적으로 제어 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="052c7-117">자세한 내용은 [PowerShell 모듈 매니페스트를 작성 하는 방법](how-to-write-a-powershell-module-manifest.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="052c7-117">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="052c7-118">다음 코드는 모듈로 사용할 수 있는 동일한 파일에 세 개의 cmdlet이 포함 된 매우 간단한 c # 코드 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

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

3. <span data-ttu-id="052c7-119">솔루션을 패키지 하 고 PowerShell 모듈 경로의 어딘가에 패키지를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="052c7-120">`PSModulePath`전역 환경 변수는 PowerShell이 모듈을 찾는 데 사용 하는 기본 경로를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="052c7-121">예를 들어 시스템에 모듈을 저장 하는 일반적인 경로는 `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>` 입니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="052c7-122">기본 경로를 사용 하지 않는 경우 설치 하는 동안 모듈의 위치를 명시적으로 명시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="052c7-123">솔루션에 대 한 여러 어셈블리와 파일을 저장 하는 폴더가 필요할 수 있으므로 모듈을 저장할 폴더를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="052c7-124">기술적으로는의 어디에 나 모듈을 설치할 필요가 없습니다. 즉, `PSModulePath` PowerShell이 모듈을 찾을 기본 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="052c7-125">그러나 모듈을 다른 위치에 저장 해야 하는 경우를 제외 하 고이 작업을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="052c7-126">자세한 내용은 [Powershell 모듈](./installing-a-powershell-module.md) 설치 및 [Powershell 모듈 설치 경로 수정](./modifying-the-psmodulepath-installation-path.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="052c7-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="052c7-127">[Import-module에 대 한](/powershell/module/Microsoft.PowerShell.Core/Import-Module)호출을 사용 하 여 모듈을 PowerShell로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="052c7-128">[Import-module을 호출 하면 모듈이](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 활성 메모리에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="052c7-129">PowerShell 3.0 이상 버전을 사용 하는 경우 코드에서 모듈의 이름만 호출 하면 해당 모듈의 이름도 가져옵니다. 자세한 내용은 [PowerShell 모듈 가져오기](./importing-a-powershell-module.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="052c7-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="052c7-130">스냅인 어셈블리를 모듈로 가져오기</span><span class="sxs-lookup"><span data-stu-id="052c7-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="052c7-131">스냅인 어셈블리에 존재 하는 cmdlet 및 공급자를 이진 모듈로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="052c7-132">스냅인 어셈블리를 이진 모듈로 로드 하면 해당 스냅인의 cmdlet 및 공급자가 사용자에 게 제공 되지만 어셈블리의 스냅인 클래스는 무시 되 고 스냅인이 등록 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="052c7-133">따라서 Windows PowerShell에서 제공 하는 스냅인 cmdlet은 cmdlet 및 공급자를 세션에서 사용할 수 있는 경우에도 스냅인을 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="052c7-134">또한 스냅인에서 참조 하는 서식 지정 또는 형식 파일은 이진 모듈의 일부로 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="052c7-135">서식 지정 및 형식 파일을 가져오려면 모듈 매니페스트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="052c7-135">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="052c7-136">[PowerShell 모듈 매니페스트를 작성 하는 방법](how-to-write-a-powershell-module-manifest.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="052c7-136">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="052c7-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="052c7-137">See Also</span></span>

[<span data-ttu-id="052c7-138">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="052c7-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

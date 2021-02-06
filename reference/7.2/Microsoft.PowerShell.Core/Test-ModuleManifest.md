---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-modulemanifest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ModuleManifest
ms.openlocfilehash: c86a7253335b91011d2eb225bc53d1c5cc671aff
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603263"
---
# <span data-ttu-id="49f27-102">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="49f27-102">Test-ModuleManifest</span></span>

## <span data-ttu-id="49f27-103">개요</span><span class="sxs-lookup"><span data-stu-id="49f27-103">SYNOPSIS</span></span>
<span data-ttu-id="49f27-104">모듈 매니페스트 파일이 모듈의 내용을 정확하게 설명하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-104">Verifies that a module manifest file accurately describes the contents of a module.</span></span>

## <span data-ttu-id="49f27-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="49f27-105">SYNTAX</span></span>

```
Test-ModuleManifest [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="49f27-106">설명</span><span class="sxs-lookup"><span data-stu-id="49f27-106">DESCRIPTION</span></span>

<span data-ttu-id="49f27-107">**New-modulemanifest** cmdlet은 모듈 매니페스트 (. psd1) 파일에 나열 된 파일이 실제로 지정 된 경로에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-107">The **Test-ModuleManifest** cmdlet verifies that the files that are listed in the module manifest (.psd1) file are actually in the specified paths.</span></span>

<span data-ttu-id="49f27-108">이 cmdlet은 모듈 작성자가 매니페스트 파일을 테스트하는 데 도움을 주기 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-108">This cmdlet is designed to help module authors test their manifest files.</span></span>
<span data-ttu-id="49f27-109">모듈 사용자는 스크립트와 명령에서이 cmdlet을 사용 하 여 모듈에 종속 된 스크립트를 실행 하기 전에 오류를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-109">Module users can also use this cmdlet in scripts and commands to detect errors before they run scripts that depend on the module.</span></span>

<span data-ttu-id="49f27-110">**New-modulemanifest** 는 모듈을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-110">**Test-ModuleManifest** returns an object that represents the module.</span></span>
<span data-ttu-id="49f27-111">Get-Module 반환 하는 것과 동일한 형식의 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-111">This is the same type of object that Get-Module returns.</span></span>
<span data-ttu-id="49f27-112">매니페스트에 지정된 위치에 파일이 없는 경우 이 cmdlet은 없는 각 파일에 대한 오류도 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-112">If any files are not in the locations specified in the manifest, the cmdlet also generates an error for each missing file.</span></span>

## <span data-ttu-id="49f27-113">예제</span><span class="sxs-lookup"><span data-stu-id="49f27-113">EXAMPLES</span></span>

### <span data-ttu-id="49f27-114">예제 1: 매니페스트 테스트</span><span class="sxs-lookup"><span data-stu-id="49f27-114">Example 1: Test a manifest</span></span>

```powershell
test-ModuleManifest -Path "$pshome\Modules\TestModule.psd1"
```

<span data-ttu-id="49f27-115">이 명령은 TestModule.psd1 모듈 매니페스트를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-115">This command tests the TestModule.psd1 module manifest.</span></span>

### <span data-ttu-id="49f27-116">예제 2: 파이프라인을 사용 하 여 매니페스트 테스트</span><span class="sxs-lookup"><span data-stu-id="49f27-116">Example 2: Test a manifest by using the pipeline</span></span>

```powershell
"$pshome\Modules\TestModule.psd1" | test-modulemanifest
```

```Output
Test-ModuleManifest : The specified type data file 'C:\Windows\System32\Wi
ndowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml' could not be processed because the file was not found. Please correct the path and try again.
At line:1 char:34
+ "$pshome\Modules\TestModule.psd1" | test-modulemanifest <<<<
+ CategoryInfo          : ResourceUnavailable: (C:\Windows\System32\WindowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml:String) [Test-ModuleManifest], FileNotFoundException
+ FullyQualifiedErrorId : Modules_TypeDataFileNotFound,Microsoft.PowerShell.Commands.TestModuleManifestCommandName

Name              : TestModule
Path              : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule\TestModule.psd1
Description       :
Guid              : 6f0f1387-cd25-4902-b7b4-22cff6aefa7b
Version           : 1.0
ModuleBase        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule
ModuleType        : Manifest
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="49f27-117">이 명령은 파이프라인 연산자 (|)를 사용 하 여 **new-modulemanifest** 에 경로 문자열을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-117">This command uses a pipeline operator (|) to send a path string to **Test-ModuleManifest**.</span></span>

<span data-ttu-id="49f27-118">명령 출력에서는 매니페스트에 나열된 TestTypes.ps1xml 파일을 찾을 수 없어서 테스트가 실패했음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-118">The command output shows that the test failed, because the TestTypes.ps1xml file, which was listed in the manifest, was not found.</span></span>

### <span data-ttu-id="49f27-119">예제 3: 모듈 매니페스트를 테스트 하는 함수 작성</span><span class="sxs-lookup"><span data-stu-id="49f27-119">Example 3: Write a function to test a module manifest</span></span>

```powershell
function Test-ManifestBool ($path)
```

```Output
{$a = dir $path | Test-ModuleManifest -ErrorAction SilentlyContinue; $?}
```

<span data-ttu-id="49f27-120">이 함수는 **new-modulemanifest** 와 유사 하지만 부울 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-120">This function is like **Test-ModuleManifest**, but it returns a Boolean value.</span></span>
<span data-ttu-id="49f27-121">함수는 매니페스트가 테스트를 통과 한 경우 $True을 반환 하 고 그렇지 않으면 $False 합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-121">The function returns $True if the manifest passed the test and $False otherwise.</span></span>

<span data-ttu-id="49f27-122">함수는 Get-ChildItem cmdlet, alias = dir을 사용 하 여 $path 변수로 지정 된 모듈 매니페스트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-122">The function uses the Get-ChildItem cmdlet, alias = dir, to get the module manifest specified by the $path variable.</span></span>
<span data-ttu-id="49f27-123">이 명령은 파이프라인 연산자 (|)를 사용 하 여 파일 개체를 **new-modulemanifest** 에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-123">The command uses a pipeline operator (|) to pass the file object to **Test-ModuleManifest**.</span></span>

<span data-ttu-id="49f27-124">**New-modulemanifest** 는 값이 SilentlyContinue 인 *erroraction* 일반 매개 변수를 사용 하 여 명령이 생성 하는 오류를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-124">**Test-ModuleManifest** uses the *ErrorAction* common parameter with a value of SilentlyContinue to suppress the display of any errors that the command generates.</span></span>
<span data-ttu-id="49f27-125">또한 **new-modulemanifest** 에서 반환 하는 **psmoduleinfo** 개체를 $a 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-125">It also saves the **PSModuleInfo** object that **Test-ModuleManifest** returns in the $a variable.</span></span>
<span data-ttu-id="49f27-126">따라서 개체는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-126">Therefore, the object is not displayed.</span></span>

<span data-ttu-id="49f27-127">그러면 별도의 명령에서 함수에 $?의 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-127">Then, in a separate command, the function displays the value of the $?</span></span>
<span data-ttu-id="49f27-128">자동 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-128">automatic variable.</span></span>
<span data-ttu-id="49f27-129">이전 명령에서 오류를 생성 하지 않으면 명령은 $True를 표시 하 고, 그렇지 않으면 $False 합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-129">If the previous command generates no error, the command displays $True, and $False otherwise.</span></span>

<span data-ttu-id="49f27-130">**Import-module 명령이 나** 모듈을 사용 하는 명령 앞에 올 수 있는 조건문과 같은 조건문에서이 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-130">You can use this function in conditional statements, such as those that might precede an **Import-Module** command or a command that uses the module.</span></span>

## <span data-ttu-id="49f27-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="49f27-131">PARAMETERS</span></span>

### <span data-ttu-id="49f27-132">-Path</span><span class="sxs-lookup"><span data-stu-id="49f27-132">-Path</span></span>

<span data-ttu-id="49f27-133">매니페스트 파일의 경로와 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-133">Specifies a path and file name for the manifest file.</span></span>
<span data-ttu-id="49f27-134">Psd1 파일 이름 확장명을 가진 모듈 매니페스트 파일의 선택적 경로 및 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-134">Enter an optional path and name of the module manifest file that has the .psd1 file name extension.</span></span>
<span data-ttu-id="49f27-135">기본 위치는 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-135">The default location is the current directory.</span></span>
<span data-ttu-id="49f27-136">와일드 카드 문자는 지원 되지만 단일 모듈 매니페스트 파일로 확인 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-136">Wildcard characters are supported, but must resolve to a single module manifest file.</span></span>
<span data-ttu-id="49f27-137">이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-137">This parameter is required.</span></span>
<span data-ttu-id="49f27-138">**New-modulemanifest** 에 대 한 경로를 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-138">You can also pipe a path to **Test-ModuleManifest**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="49f27-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="49f27-139">CommonParameters</span></span>

<span data-ttu-id="49f27-140">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="49f27-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="49f27-141">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49f27-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="49f27-142">입력</span><span class="sxs-lookup"><span data-stu-id="49f27-142">INPUTS</span></span>

### <span data-ttu-id="49f27-143">System.String</span><span class="sxs-lookup"><span data-stu-id="49f27-143">System.String</span></span>

<span data-ttu-id="49f27-144">모듈 매니페스트에 대 한 경로를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-144">You can pipe the path to a module manifest to this cmdlet.</span></span>

## <span data-ttu-id="49f27-145">출력</span><span class="sxs-lookup"><span data-stu-id="49f27-145">OUTPUTS</span></span>

### <span data-ttu-id="49f27-146">System.object..</span><span class="sxs-lookup"><span data-stu-id="49f27-146">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="49f27-147">이 cmdlet은 모듈을 나타내는 **Psmoduleinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-147">This cmdlet returns a **PSModuleInfo** object that represents the module.</span></span>
<span data-ttu-id="49f27-148">매니페스트에 오류가 있는 경우에도 이 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="49f27-148">It returns this object even if the manifest has errors.</span></span>

## <span data-ttu-id="49f27-149">참고</span><span class="sxs-lookup"><span data-stu-id="49f27-149">NOTES</span></span>

## <span data-ttu-id="49f27-150">관련 링크</span><span class="sxs-lookup"><span data-stu-id="49f27-150">RELATED LINKS</span></span>

[<span data-ttu-id="49f27-151">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="49f27-151">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="49f27-152">Get-Module</span><span class="sxs-lookup"><span data-stu-id="49f27-152">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="49f27-153">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="49f27-153">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="49f27-154">New-Module</span><span class="sxs-lookup"><span data-stu-id="49f27-154">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="49f27-155">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="49f27-155">New-ModuleManifest</span></span>](New-ModuleManifest.md)

[<span data-ttu-id="49f27-156">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="49f27-156">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="49f27-157">about_Modules</span><span class="sxs-lookup"><span data-stu-id="49f27-157">about_Modules</span></span>](About/about_Modules.md)


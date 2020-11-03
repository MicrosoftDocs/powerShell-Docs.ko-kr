---
description: Alias
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_alias_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 별칭 공급자
ms.openlocfilehash: 994bd183f047123502f7e152c59b0d8aeb32a1b9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223593"
---
# <a name="alias-provider"></a><span data-ttu-id="5e9d5-104">별칭 공급자</span><span class="sxs-lookup"><span data-stu-id="5e9d5-104">Alias provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="5e9d5-105">공급자 이름</span><span class="sxs-lookup"><span data-stu-id="5e9d5-105">Provider name</span></span>

<span data-ttu-id="5e9d5-106">Alias</span><span class="sxs-lookup"><span data-stu-id="5e9d5-106">Alias</span></span>

## <a name="drives"></a><span data-ttu-id="5e9d5-107">드라이브</span><span class="sxs-lookup"><span data-stu-id="5e9d5-107">Drives</span></span>

`Alias:`

## <a name="capabilities"></a><span data-ttu-id="5e9d5-108">기능</span><span class="sxs-lookup"><span data-stu-id="5e9d5-108">Capabilities</span></span>

<span data-ttu-id="5e9d5-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="5e9d5-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="5e9d5-110">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="5e9d5-110">Short description</span></span>

<span data-ttu-id="5e9d5-111">PowerShell 별칭 및 해당 별칭이 나타내는 값에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-111">Provides access to the PowerShell aliases and the values that they represent.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="5e9d5-112">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="5e9d5-112">Detailed description</span></span>

<span data-ttu-id="5e9d5-113">Powershell **별칭** 공급자를 통해 powershell에서 별칭을 가져오고 추가, 변경 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-113">The PowerShell **Alias** provider lets you get, add, change, clear, and delete aliases in PowerShell.</span></span>

<span data-ttu-id="5e9d5-114">별칭은 스크립트를 포함 하 여 cmdlet, 함수, 실행 파일의 대체 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-114">An alias is an alternate name for a cmdlet, function, executable file, including scripts.</span></span> <span data-ttu-id="5e9d5-115">PowerShell에는 기본 제공 별칭 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-115">PowerShell includes a set of built-in aliases.</span></span> <span data-ttu-id="5e9d5-116">현재 세션과 PowerShell 프로필에 고유한 별칭을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-116">You can add your own aliases to the current session and to your PowerShell profile.</span></span>

<span data-ttu-id="5e9d5-117">**별칭** 드라이브는 별칭 개체만 포함 하는 플랫 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-117">The **Alias** drive is a flat namespace that contains only the alias objects.</span></span>
<span data-ttu-id="5e9d5-118">별칭에는 하위 항목이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-118">The aliases have no child items.</span></span>

<span data-ttu-id="5e9d5-119">**별칭** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-119">The **Alias** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="5e9d5-120">Get-Location</span><span class="sxs-lookup"><span data-stu-id="5e9d5-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="5e9d5-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="5e9d5-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="5e9d5-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="5e9d5-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="5e9d5-123">New-Item</span><span class="sxs-lookup"><span data-stu-id="5e9d5-123">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="5e9d5-124">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="5e9d5-124">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="5e9d5-125">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="5e9d5-125">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="5e9d5-126">PowerShell에는 별칭을 보고 변경할 수 있도록 설계 된 cmdlet 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-126">PowerShell includes a set of cmdlets that are designed to view and to change aliases.</span></span> <span data-ttu-id="5e9d5-127">**별칭** cmdlet을 사용 하는 경우 이름에 드라이브를 지정할 필요가 없습니다 `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-127">When you use **Alias** cmdlets, you do not need to specify the `Alias:` drive in the name.</span></span> <span data-ttu-id="5e9d5-128">이 문서에서는 **별칭** cmdlet 작업에 대해 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-128">This article does not cover working with **Alias** cmdlets.</span></span>

- [<span data-ttu-id="5e9d5-129">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="5e9d5-129">Export-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [<span data-ttu-id="5e9d5-130">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="5e9d5-130">Get-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [<span data-ttu-id="5e9d5-131">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="5e9d5-131">Import-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [<span data-ttu-id="5e9d5-132">New-Alias</span><span class="sxs-lookup"><span data-stu-id="5e9d5-132">New-Alias</span></span>](xref:Microsoft.PowerShell.Utility.New-Alias)
- [<span data-ttu-id="5e9d5-133">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="5e9d5-133">Set-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Set-Alias)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="5e9d5-134">이 공급자가 노출 하는 형식</span><span class="sxs-lookup"><span data-stu-id="5e9d5-134">Types exposed by this provider</span></span>

<span data-ttu-id="5e9d5-135">각 별칭은 [system.management.automation.aliasinfo](/dotnet/api/system.management.automation.aliasinfo) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-135">Each alias is an instance of the [System.Management.Automation.AliasInfo](/dotnet/api/system.management.automation.aliasinfo) class.</span></span>

## <a name="navigating-the-alias-drive"></a><span data-ttu-id="5e9d5-136">별칭 드라이브 탐색</span><span class="sxs-lookup"><span data-stu-id="5e9d5-136">Navigating the Alias drive</span></span>

<span data-ttu-id="5e9d5-137">**별칭** 공급자는 드라이브에 해당 데이터 저장소를 노출 합니다 `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-137">The **Alias** provider exposes its data store in the `Alias:` drive.</span></span> <span data-ttu-id="5e9d5-138">별칭을 사용 하려면 다음 명령을 사용 하 여 해당 위치를 드라이브로 변경할 수 있습니다 `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-138">To work with aliases, you can change your location to the `Alias:` drive by using the following command:</span></span>

```powershell
Set-Location Alias:
```

<span data-ttu-id="5e9d5-139">파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-139">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="5e9d5-140">예를 들어 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-140">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="5e9d5-141">다른 PowerShell 드라이브에서 별칭 공급자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-141">You can also work with the Alias provider from any other PowerShell drive.</span></span> <span data-ttu-id="5e9d5-142">다른 위치에서 별칭을 참조 하려면 `Alias:` 경로에 드라이브 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-142">To reference an alias from another location, use the `Alias:` drive name in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="5e9d5-143">PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-143">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="5e9d5-144">`dir`및 등의 명령은 `ls` 이제 [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭입니다 `cd` .는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-144">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="5e9d5-145">및 `pwd` 은 [(는) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-145">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

### <a name="displaying-the-contents-of-the-alias-drive"></a><span data-ttu-id="5e9d5-146">Alias: 드라이브의 내용 표시</span><span class="sxs-lookup"><span data-stu-id="5e9d5-146">Displaying the Contents of the Alias: drive</span></span>

<span data-ttu-id="5e9d5-147">이 명령은 현재 위치가 드라이브인 경우 모든 별칭 목록을 가져옵니다 `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-147">This command gets the list of all the aliases when the current location is the `Alias:` drive.</span></span> <span data-ttu-id="5e9d5-148">와일드 카드 문자를 사용 하 여 `*` 현재 위치의 모든 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-148">It uses a wildcard character `*` to indicate all the contents of the current location.</span></span>

```powershell
PS Alias:\> Get-Item -Path *
```

<span data-ttu-id="5e9d5-149">드라이브에서 `Alias:` `.` 현재 위치를 나타내는 점 및 `*` 현재 위치의 모든 항목을 나타내는 와일드 카드 문자는 동일한 효과를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-149">In the `Alias:` drive, a dot `.`, which represents the current location, and a wildcard character `*`, which represents all items in the current location, have the same effect.</span></span> <span data-ttu-id="5e9d5-150">예를 들어 `Get-Item -Path .` 또는 `Get-Item \*` 는 동일한 결과를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-150">For example, `Get-Item -Path .` or `Get-Item \*` produce the same result.</span></span>

<span data-ttu-id="5e9d5-151">별칭 공급자는 컨테이너를 포함 하지 않으므로와 함께 사용할 경우 위의 명령이 동일한 결과를 가집니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-151">The Alias provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Alias:
```

### <a name="get-a-selected-alias"></a><span data-ttu-id="5e9d5-152">선택한 별칭 가져오기</span><span class="sxs-lookup"><span data-stu-id="5e9d5-152">Get a selected alias</span></span>

<span data-ttu-id="5e9d5-153">이 명령은 별칭을 가져옵니다 `ls` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-153">This command gets the `ls` alias.</span></span>
<span data-ttu-id="5e9d5-154">경로를 포함 하기 때문에 모든 PowerShell 드라이브에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-154">Because it includes the path, you can use it in any PowerShell drive.</span></span>

```powershell
Get-Item -Path Alias:ls
```

<span data-ttu-id="5e9d5-155">드라이브에 있는 경우 `Alias:` 경로에서 드라이브 이름을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-155">If you are in the `Alias:` drive, you can omit the drive name from the path.</span></span>

<span data-ttu-id="5e9d5-156">공급자 경로에 달러 기호 ()를 접두사로 사용 하 여 별칭에 대 한 정의를 검색할 수도 있습니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-156">You can also retrieve the definition for an alias by prefixing the provider path with the dollar sign (`$`).</span></span>

```powershell
$Alias:ls
```

### <a name="get-all-aliases-for-a-specific-cmdlet"></a><span data-ttu-id="5e9d5-157">특정 cmdlet에 대 한 모든 별칭 가져오기</span><span class="sxs-lookup"><span data-stu-id="5e9d5-157">Get all aliases for a specific cmdlet</span></span>

<span data-ttu-id="5e9d5-158">이 명령은 cmdlet과 연결 된 별칭 목록을 가져옵니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-158">This command gets a list of the aliases that are associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="5e9d5-159">Cmdlet 이름을 저장 하는 **Definition** 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-159">It uses the **Definition** property, which stores the cmdlet name.</span></span>

```powershell
Get-Item -Path Alias:* | Where-Object {$_.Definition -eq "Get-ChildItem"}
```

## <a name="creating-aliases"></a><span data-ttu-id="5e9d5-160">별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="5e9d5-160">Creating aliases</span></span>

### <a name="create-an-alias-from-the-alias-drive"></a><span data-ttu-id="5e9d5-161">별칭: 드라이브에서 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-161">Create an alias from the Alias: drive</span></span>

<span data-ttu-id="5e9d5-162">이 명령은 `serv` cmdlet에 대 한 별칭을 만듭니다 `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-162">This command creates the `serv` alias for the `Get-Service` cmdlet.</span></span> <span data-ttu-id="5e9d5-163">현재 위치가 드라이브에 있기 때문에 `Alias:` `-Path` 매개 변수는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-163">Because the current location is in the `Alias:` drive, the `-Path` parameter is not needed.</span></span>

<span data-ttu-id="5e9d5-164">또한이 명령은 `-Options` 동적 매개 변수를 사용 하 여 별칭에 대 한 **AllScope** 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-164">This command also uses the `-Options` dynamic parameter to set the **AllScope** option on the alias.</span></span> <span data-ttu-id="5e9d5-165">`-Options`매개 변수는 `New-Item` 드라이브에 있는 경우에만 cmdlet에서 사용할 수 있습니다 `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-165">The `-Options` parameter is available in the `New-Item` cmdlet only when you are in the `Alias:` drive.</span></span> <span data-ttu-id="5e9d5-166">점 ( `.` )은 별칭 드라이브인 현재 디렉터리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-166">The dot (`.`) indicates the current directory, which is the alias drive.</span></span>

```
PS Alias:\> New-Item -Path . -Name serv -Value Get-Service -Options "AllScope"
```

### <a name="create-an-alias-with-an-absolute-path"></a><span data-ttu-id="5e9d5-167">절대 경로를 사용 하 여 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="5e9d5-167">Create an alias with an absolute path</span></span>

<span data-ttu-id="5e9d5-168">명령을 호출하는 모든 항목에 대한 별칭을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-168">You can create an alias for any item that invokes a command.</span></span>
<span data-ttu-id="5e9d5-169">이 명령은 `np` 에 대 한 별칭을 만듭니다 `Notepad.exe` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-169">This command creates the `np` alias for `Notepad.exe`.</span></span>

```powershell
New-Item -Path Alias:np -Value c:\windows\notepad.exe
```

### <a name="create-an-alias-to-a-new-function"></a><span data-ttu-id="5e9d5-170">새 함수에 대 한 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="5e9d5-170">Create an alias to a new function</span></span>

<span data-ttu-id="5e9d5-171">모든 함수에 대한 별칭을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-171">You can create an alias for any function.</span></span> <span data-ttu-id="5e9d5-172">이 기능을 사용하여 cmdlet과 해당 매개 변수를 둘 다 포함하는 별칭을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-172">You can use this feature to create an alias that includes both a cmdlet and its parameters.</span></span>

<span data-ttu-id="5e9d5-173">첫 번째 명령은 `CD32` 현재 디렉터리를 디렉터리로 변경 하는 함수를 만듭니다 `System32` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-173">The first command creates the `CD32` function, which changes the current directory to the `System32` directory.</span></span> <span data-ttu-id="5e9d5-174">두 번째 명령은 `go` 함수에 대 한 별칭을 만듭니다 `CD32` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-174">The second command creates the `go` alias for the `CD32` function.</span></span>

<span data-ttu-id="5e9d5-175">명령이 완료 되 면 또는 중 하나를 사용 하 여 함수를 호출할 수 있습니다 `CD32` `go` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-175">When the command is complete, you can use either `CD32` or `go` to invoke the function.</span></span>

```powershell
function CD32 {Set-Location -Path c:\windows\system32}
Set-Item -Path Alias:go -Value CD32
```

## <a name="changing-aliases"></a><span data-ttu-id="5e9d5-176">별칭 변경</span><span class="sxs-lookup"><span data-stu-id="5e9d5-176">Changing aliases</span></span>

### <a name="change-the-options-of-an-alias"></a><span data-ttu-id="5e9d5-177">별칭의 옵션을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-177">Change the options of an alias</span></span>

<span data-ttu-id="5e9d5-178">`Set-Item`Cmdlet을 `-Options` 동적 매개 변수와 함께 사용 하 여 별칭의 속성 값을 변경할 수 있습니다 `-Options` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-178">You can use the `Set-Item` cmdlet with the `-Options` dynamic parameter to change the value of the `-Options` property of an alias.</span></span>

<span data-ttu-id="5e9d5-179">이 명령은 별칭에 대 한 **AllScope** 및 **ReadOnly** 옵션을 설정 합니다 `dir` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-179">This command sets the **AllScope** and **ReadOnly** options for the `dir` alias.</span></span> <span data-ttu-id="5e9d5-180">이 명령은 `-Options` cmdlet의 동적 매개 변수를 사용 합니다 `Set-Item` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-180">The command uses the `-Options` dynamic parameter of the `Set-Item` cmdlet.</span></span> <span data-ttu-id="5e9d5-181">`-Options`매개 변수는 `Set-Item` **별칭** 또는 **함수** 공급자와 함께 사용할 때에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-181">The `-Options` parameter is available in `Set-Item` when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path Alias:dir -Options "AllScope,ReadOnly"
```

### <a name="change-an-aliases-referenced-command"></a><span data-ttu-id="5e9d5-182">참조 된 별칭 변경 명령</span><span class="sxs-lookup"><span data-stu-id="5e9d5-182">Change an aliases referenced command</span></span>

<span data-ttu-id="5e9d5-183">이 명령은 cmdlet을 사용 하 여 cmdlet 대신 cmdlet을 `Set-Item` 나타내도록 별칭을 변경 합니다 `gp` `Get-Process` `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-183">This command uses the `Set-Item` cmdlet to change the `gp` alias so that it represents the `Get-Process` cmdlet instead of the `Get-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="5e9d5-184">`-Force`별칭의 **Options** 속성 값 `gp` 이로 설정 되어 있기 때문에 매개 변수가 필요 합니다 `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-184">The `-Force` parameter is required because the value of the **Options** property of the `gp` alias is set to `ReadOnly`.</span></span> <span data-ttu-id="5e9d5-185">명령이 드라이브 내에서 전송 되므로 `Alias:` 경로에 드라이브가 지정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-185">Because the command is submitted from within the `Alias:` drive, the drive is not specified in the path.</span></span>

```powershell
Set-Item -Path gp -Value Get-Process -Force
```

<span data-ttu-id="5e9d5-186">변경 내용은 별칭과 명령 간의 연결을 정의하는 네 가지 속성에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-186">The change affects the four properties that define the association between the alias and the command.</span></span> <span data-ttu-id="5e9d5-187">변경의 결과를 보려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-187">To view the effect of the change, type the following command:</span></span>

```powershell
Get-Item -Path gp | Format-List -Property *
```

### <a name="rename-an-alias"></a><span data-ttu-id="5e9d5-188">별칭 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="5e9d5-188">Rename an alias</span></span>

<span data-ttu-id="5e9d5-189">이 명령은 cmdlet을 사용 하 여 `Rename-Item` `popd` 별칭을로 변경 `pop` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-189">This command uses the `Rename-Item` cmdlet to change the `popd` alias to `pop`.</span></span>

```powershell
Rename-Item -Path Alias:popd -NewName pop
```

## <a name="copying-an-alias"></a><span data-ttu-id="5e9d5-190">별칭 복사</span><span class="sxs-lookup"><span data-stu-id="5e9d5-190">Copying an alias</span></span>

<span data-ttu-id="5e9d5-191">이 명령은 `pushd` `push` cmdlet에 대 한 새 별칭이 만들어지도록 별칭을 복사 합니다 `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-191">This command copies the `pushd` alias so that a new `push` alias is created for the `Push-Location` cmdlet.</span></span>

<span data-ttu-id="5e9d5-192">새 별칭이 만들어지면 해당 **Description** 속성의 값은 null입니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-192">When the new alias is created, its **Description** property has a null value.</span></span>
<span data-ttu-id="5e9d5-193">및 **옵션** 속성의 값은 `None` 입니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-193">And, its **Option** property has a value of `None`.</span></span> <span data-ttu-id="5e9d5-194">명령이 드라이브 내에서 실행 된 경우 `Alias:` 매개 변수 값에서 드라이브 이름을 생략할 수 있습니다 `-Path` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-194">If the command is issued from within the `Alias:` drive, you can omit the drive name from the value of the `-Path` parameter.</span></span>

```powershell
Copy-Item -Path Alias:pushd -Destination Alias:push
```

## <a name="deleting-an-alias"></a><span data-ttu-id="5e9d5-195">별칭 삭제</span><span class="sxs-lookup"><span data-stu-id="5e9d5-195">Deleting an alias</span></span>

<span data-ttu-id="5e9d5-196">이 명령은 `serv` 현재 세션에서 별칭을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-196">This command deletes the `serv` alias from the current session.</span></span>
<span data-ttu-id="5e9d5-197">PowerShell 드라이브에서이 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-197">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Item -Path Alias:serv
```

<span data-ttu-id="5e9d5-198">이 명령은 "s"로 시작하는 별칭을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-198">This command deletes aliases that begin with "s".</span></span>
<span data-ttu-id="5e9d5-199">읽기 전용 별칭은 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-199">It does not delete read-only aliases.</span></span>

```powershell
Clear-Item -Path Alias:s*
```

### <a name="delete-read-only-aliases"></a><span data-ttu-id="5e9d5-200">읽기 전용 별칭 삭제</span><span class="sxs-lookup"><span data-stu-id="5e9d5-200">Delete read-only aliases</span></span>

<span data-ttu-id="5e9d5-201">이 명령은 현재 세션에서 모든 별칭을 삭제 합니다. 단, `Constant` 해당 **옵션** 속성에 대 한 값을 가진 별칭은 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-201">This command deletes all aliases from the current session, except those with a value of `Constant` for their **Options** property.</span></span> <span data-ttu-id="5e9d5-202">`-Force`매개 변수를 사용 하면 **Options** 속성의 값이 인 별칭을 삭제할 수 있습니다 `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-202">The `-Force` parameter allows the command to delete aliases whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Alias:* -Force
```

## <a name="dynamic-parameters"></a><span data-ttu-id="5e9d5-203">동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5e9d5-203">Dynamic parameters</span></span>

<span data-ttu-id="5e9d5-204">동적 매개 변수는 PowerShell 공급자가 추가 하는 cmdlet 매개 변수 이며, 공급자 사용 드라이브에서 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-204">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="5e9d5-205">옵션 [ScopedItemOptions]</span><span class="sxs-lookup"><span data-stu-id="5e9d5-205">Options [System.Management.Automation.ScopedItemOptions]</span></span>

<span data-ttu-id="5e9d5-206">별칭의 **Options** 속성 값을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-206">Determines the value of the **Options** property of an alias.</span></span>

- <span data-ttu-id="5e9d5-207">**None** : 옵션이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-207">**None** : No options.</span></span> <span data-ttu-id="5e9d5-208">이 값은 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-208">This value is the default.</span></span>
- <span data-ttu-id="5e9d5-209">**상수** : 별칭을 삭제할 수 없으며 해당 속성을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-209">**Constant** :The alias cannot be deleted and its properties cannot be changed.</span></span>
  <span data-ttu-id="5e9d5-210">**상수** 는 별칭을 만드는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-210">**Constant** is available only when you create an alias.</span></span> <span data-ttu-id="5e9d5-211">기존 별칭의 옵션을 **Constant** 로 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-211">You cannot change the option of an existing alias to **Constant**.</span></span>
- <span data-ttu-id="5e9d5-212">**비공개** : 별칭은 자식 범위가 아니라 현재 범위 에서만 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-212">**Private** :The alias is visible only in the current scope, not in the child  scopes.</span></span>
- <span data-ttu-id="5e9d5-213">**ReadOnly** : 별칭의 속성은 매개 변수를 사용 하는 경우를 제외 하 고 변경할 수 없습니다 `-Force` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-213">**ReadOnly** :The properties of the alias cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="5e9d5-214">를 사용 하 여 별칭을 삭제할 수 있습니다 `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="5e9d5-214">You can use `Remove-Item` to delete the alias.</span></span>
- <span data-ttu-id="5e9d5-215">**AllScope** : 별칭이 만들어진 모든 새 범위로 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-215">**AllScope** :The alias is copied to any new scopes that are created.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5e9d5-216">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="5e9d5-216">Cmdlets supported</span></span>

- [<span data-ttu-id="5e9d5-217">New-Item</span><span class="sxs-lookup"><span data-stu-id="5e9d5-217">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="5e9d5-218">Set-Item</span><span class="sxs-lookup"><span data-stu-id="5e9d5-218">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="5e9d5-219">파이프라인 사용</span><span class="sxs-lookup"><span data-stu-id="5e9d5-219">Using the pipeline</span></span>

<span data-ttu-id="5e9d5-220">공급자 cmdlet은 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-220">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="5e9d5-221">파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-221">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="5e9d5-222">공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-222">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="5e9d5-223">도움말 보기</span><span class="sxs-lookup"><span data-stu-id="5e9d5-223">Getting help</span></span>

<span data-ttu-id="5e9d5-224">Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-224">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="5e9d5-225">파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 의 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9d5-225">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path alias:
```

## <a name="see-also"></a><span data-ttu-id="5e9d5-226">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e9d5-226">See also</span></span>

[<span data-ttu-id="5e9d5-227">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="5e9d5-227">about_Aliases</span></span>](../About/about_Aliases.md)

[<span data-ttu-id="5e9d5-228">about_Providers</span><span class="sxs-lookup"><span data-stu-id="5e9d5-228">about_Providers</span></span>](../About/about_Providers.md)

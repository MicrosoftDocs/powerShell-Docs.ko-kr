---
description: 레지스트리
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 레지스트리 공급자
ms.openlocfilehash: 2d57afc164885b4d207108a360215e63a5431632
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599741"
---
# <a name="registry-provider"></a><span data-ttu-id="4554e-103">레지스트리 공급자</span><span class="sxs-lookup"><span data-stu-id="4554e-103">Registry provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="4554e-104">공급자 이름</span><span class="sxs-lookup"><span data-stu-id="4554e-104">Provider name</span></span>

<span data-ttu-id="4554e-105">레지스트리</span><span class="sxs-lookup"><span data-stu-id="4554e-105">Registry</span></span>

## <a name="drives"></a><span data-ttu-id="4554e-106">드라이브</span><span class="sxs-lookup"><span data-stu-id="4554e-106">Drives</span></span>

<span data-ttu-id="4554e-107">`HKLM:`, `HKCU:`</span><span class="sxs-lookup"><span data-stu-id="4554e-107">`HKLM:`, `HKCU:`</span></span>

## <a name="capabilities"></a><span data-ttu-id="4554e-108">기능</span><span class="sxs-lookup"><span data-stu-id="4554e-108">Capabilities</span></span>

<span data-ttu-id="4554e-109">**Shouldprocess**, **UseTransactions**</span><span class="sxs-lookup"><span data-stu-id="4554e-109">**ShouldProcess**, **UseTransactions**</span></span>

## <a name="short-description"></a><span data-ttu-id="4554e-110">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="4554e-110">Short description</span></span>

<span data-ttu-id="4554e-111">PowerShell에서 레지스트리 키, 항목 및 값에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-111">Provides access to the registry keys, entries, and values in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="4554e-112">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="4554e-112">Detailed description</span></span>

<span data-ttu-id="4554e-113">PowerShell **레지스트리** 공급자를 사용 하 여 powershell에서 레지스트리 키, 항목 및 값을 가져오고 추가, 변경 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-113">The PowerShell **Registry** provider lets you get, add, change, clear, and delete registry keys, entries, and values in PowerShell.</span></span>

<span data-ttu-id="4554e-114">**레지스트리** 드라이브는 컴퓨터의 레지스트리 키와 하위 키를 포함 하는 계층적 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-114">The **Registry** drives are a hierarchical namespace containing the registry keys and subkeys on your computer.</span></span> <span data-ttu-id="4554e-115">레지스트리 항목 및 값은 이러한 계층 구조의 구성 요소가 아니라</span><span class="sxs-lookup"><span data-stu-id="4554e-115">Registry entries and values are not components of that hierarchy.</span></span> <span data-ttu-id="4554e-116">각 키의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-116">Instead, they are properties of each of the keys.</span></span>

<span data-ttu-id="4554e-117">**레지스트리** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-117">The **Registry** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="4554e-118">Get-Location</span><span class="sxs-lookup"><span data-stu-id="4554e-118">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="4554e-119">Set-Location</span><span class="sxs-lookup"><span data-stu-id="4554e-119">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="4554e-120">Get-Item</span><span class="sxs-lookup"><span data-stu-id="4554e-120">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="4554e-121">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4554e-121">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="4554e-122">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="4554e-122">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="4554e-123">Move-Item</span><span class="sxs-lookup"><span data-stu-id="4554e-123">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="4554e-124">New-Item</span><span class="sxs-lookup"><span data-stu-id="4554e-124">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="4554e-125">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="4554e-125">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="4554e-126">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4554e-126">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="4554e-127">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4554e-127">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="4554e-128">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4554e-128">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="4554e-129">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4554e-129">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="4554e-130">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="4554e-130">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="4554e-131">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="4554e-131">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="4554e-132">이 공급자가 노출 하는 형식</span><span class="sxs-lookup"><span data-stu-id="4554e-132">Types exposed by this provider</span></span>

<span data-ttu-id="4554e-133">레지스트리 키는 [Microsoft Win32 RegistryKey](/dotnet/api/microsoft.win32.registrykey) 클래스의 인스턴스로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-133">Registry keys are represented as instances of the [Microsoft.Win32.RegistryKey](/dotnet/api/microsoft.win32.registrykey) class.</span></span> <span data-ttu-id="4554e-134">레지스트리 항목은 [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) 클래스의 인스턴스로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-134">Registry entries are represented as instances of the [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) class.</span></span>

## <a name="navigating-the-registry-drives"></a><span data-ttu-id="4554e-135">레지스트리 드라이브 탐색</span><span class="sxs-lookup"><span data-stu-id="4554e-135">Navigating the Registry drives</span></span>

<span data-ttu-id="4554e-136">**레지스트리** 공급자는 해당 데이터 저장소를 두 개의 기본 드라이브로 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-136">The **Registry** provider exposes its data store as two default drives.</span></span> <span data-ttu-id="4554e-137">HKEY_LOCAL_MACHINE 레지스트리 위치는 드라이브에 매핑되고 `HKLM:` HKEY_CURRENT_USER는 드라이브에 매핑됩니다 `HKCU:` .</span><span class="sxs-lookup"><span data-stu-id="4554e-137">The registry location HKEY_LOCAL_MACHINE is mapped to the `HKLM:` drive and HKEY_CURRENT_USER is mapped to the `HKCU:` drive.</span></span> <span data-ttu-id="4554e-138">레지스트리를 사용 하려면 `HKLM:` 다음 명령을 사용 하 여 해당 위치를 드라이브로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-138">To work with the registry, you can change your location to the `HKLM:` drive using the following command.</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="4554e-139">파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-139">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="4554e-140">예를 들어 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-140">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="4554e-141">다른 PowerShell 드라이브에서 **레지스트리** 공급자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-141">You can also work with the **Registry** provider from any other PowerShell drive.</span></span> <span data-ttu-id="4554e-142">다른 위치에서 레지스트리 키를 참조 하려면 경로에 드라이브 이름 ( `HKLM:` ,)을 사용 `HKCU:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-142">To reference a registry key from another location, use the drive name (`HKLM:`, `HKCU:`) in the path.</span></span> <span data-ttu-id="4554e-143">백슬래시 ( \\ ) 또는 슬래시 (/)를 사용 하 여 **레지스트리** 드라이브의 수준을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-143">Use a backslash (\\) or a forward slash (/) to indicate a level of the **Registry** drive.</span></span>

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> <span data-ttu-id="4554e-144">PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-144">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="4554e-145">`dir`및 등의 명령은 `ls` 이제 [get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭이 고, `cd` 는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭이 고, `pwd` 은 (는 [) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-145">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location), and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

<span data-ttu-id="4554e-146">마지막 예제에서는 **레지스트리** 공급자를 탐색 하는 데 사용할 수 있는 다른 경로 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-146">This last example shows another path syntax you can use to navigate the **Registry** provider.</span></span> <span data-ttu-id="4554e-147">이 구문에서는 공급자 이름과 두 개의 콜론이 차례로 사용 `::` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-147">This syntax uses the provider name, followed by two colons `::`.</span></span> <span data-ttu-id="4554e-148">이 구문을 사용 하면 매핑된 드라이브 이름 대신 전체 하이브 이름을 사용할 수 있습니다 `HKLM` .</span><span class="sxs-lookup"><span data-stu-id="4554e-148">This syntax allows you to use the full HIVE name, instead of the mapped drive name `HKLM`.</span></span>

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a><span data-ttu-id="4554e-149">레지스트리 키의 내용 표시</span><span class="sxs-lookup"><span data-stu-id="4554e-149">Displaying the contents of registry keys</span></span>

<span data-ttu-id="4554e-150">레지스트리는 키, 하위 키 및 항목으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-150">The registry is divided into keys, subkeys, and entries.</span></span> <span data-ttu-id="4554e-151">레지스트리 구조에 대 한 자세한 내용은 [레지스트리 구조](/windows/desktop/sysinfo/structure-of-the-registry)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4554e-151">For more information about registry structure, see [Structure of the Registry](/windows/desktop/sysinfo/structure-of-the-registry).</span></span>

<span data-ttu-id="4554e-152">**레지스트리** 드라이브에서 각 키는 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-152">In a **Registry** drive, each key is a container.</span></span> <span data-ttu-id="4554e-153">키에는 원하는 수 만큼의 키가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-153">A key can contain any number of keys.</span></span> <span data-ttu-id="4554e-154">부모 키가 있는 레지스트리 키를 하위 키 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-154">A registry key that has a parent key is called a subkey.</span></span> <span data-ttu-id="4554e-155">를 사용 하 여 `Get-ChildItem` 레지스트리 키를 보고 `Set-Location` 키 경로를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-155">You can use `Get-ChildItem` to view registry keys and `Set-Location` to navigate to a key path.</span></span>

<span data-ttu-id="4554e-156">레지스트리 값은 레지스트리 키의 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-156">Registry values are attributes of a registry key.</span></span> <span data-ttu-id="4554e-157">**레지스트리** 드라이브에서는 **항목 속성** 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-157">In the **Registry** drive, they are called **Item Properties**.</span></span> <span data-ttu-id="4554e-158">레지스트리 키에는 자식 키와 항목 속성이 모두 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-158">A registry key can have both children keys and item properties.</span></span>

<span data-ttu-id="4554e-159">이 예에서는와의 차이가 `Get-Item` `Get-ChildItem` 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-159">In this example, the difference between `Get-Item` and `Get-ChildItem` is shown.</span></span> <span data-ttu-id="4554e-160">`Get-Item`"스풀러" 레지스트리 키에서를 사용 하는 경우 해당 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-160">When you use `Get-Item` on the "Spooler" registry key, you can view its properties.</span></span>

```
PS C:\ > Get-Item -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services


Name        Property
----        --------
Spooler     DependOnService    : {RPCSS, http}
            Description        : @%systemroot%\system32\spoolsv.exe,-2
            DisplayName        : @%systemroot%\system32\spoolsv.exe,-1
            ErrorControl       : 1
            FailureActions     : {16, 14, 0, 0...}
            Group              : SpoolerGroup
            ImagePath          : C:\WINDOWS\System32\spoolsv.exe
            ObjectName         : LocalSystem
            RequiredPrivileges : {SeTcbPrivilege, SeImpersonatePrivilege, ...
            ServiceSidType     : 1
            Start              : 2
            Type               : 27
```

<span data-ttu-id="4554e-161">각 레지스트리 키에는 하위 키도 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-161">Each registry key can also have subkeys.</span></span> <span data-ttu-id="4554e-162">`Get-Item`레지스트리 키에서를 사용 하는 경우 하위 키가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-162">When you use `Get-Item` on a registry key, the subkeys are not displayed.</span></span> <span data-ttu-id="4554e-163">`Get-ChildItem`이 cmdlet은 각 하위 키의 속성을 포함 하 여 "스풀러" 키의 자식 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-163">The `Get-ChildItem` cmdlet will show you children items of the "Spooler" key, including each subkey's properties.</span></span> <span data-ttu-id="4554e-164">을 사용할 때는 부모 키 속성이 표시 되지 않습니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="4554e-164">The parent keys properties are not shown when using `Get-ChildItem`.</span></span>

```
PS C:\> Get-ChildItem -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler


Name             Property
----             --------
Performance      Close           : PerfClose
                 Collect         : PerfCollect
                 Collect Timeout : 2000
                 Library         : C:\Windows\System32\winspool.drv
                 Object List     : 1450
                 Open            : PerfOpen
                 Open Timeout    : 4000
Security         Security : {1, 0, 20, 128...}
```

<span data-ttu-id="4554e-165">이 `Get-Item` cmdlet은 현재 위치에서 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-165">The `Get-Item` cmdlet can also be used on the current location.</span></span> <span data-ttu-id="4554e-166">다음 예제에서는 "스풀러" 레지스트리 키로 이동 하 여 항목 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-166">The following example navigates to the "Spooler" registry key and gets the item properties.</span></span>
<span data-ttu-id="4554e-167">점은 `.` 현재 위치를 나타내는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-167">The dot `.` is used to indicate the current location.</span></span>

```
PS C:\> cd HKLM:\System\CurrentControlSet\Services\Spooler
PS HKLM:\SYSTEM\CurrentControlSet\Services\Spooler> Get-Item .

    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services

Name             Property
----             --------
Spooler          DependOnService    : {RPCSS, http}
                 Description        : @%systemroot%\system32\spoolsv.exe,-2
...
```

<span data-ttu-id="4554e-168">이 섹션에서 설명 하는 cmdlet에 대 한 자세한 내용은 다음 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4554e-168">For more information on the cmdlets covered in this section, see the following articles.</span></span>

<span data-ttu-id="4554e-169">-[항목 가져오기](xref:Microsoft.PowerShell.Management.Get-Item) 
- [Get ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="4554e-169">-[Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
-[Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span></span>

## <a name="viewing-registry-key-values"></a><span data-ttu-id="4554e-170">레지스트리 키 값 보기</span><span class="sxs-lookup"><span data-stu-id="4554e-170">Viewing registry key values</span></span>

<span data-ttu-id="4554e-171">레지스트리 키 값은 각 레지스트리 키의 속성으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-171">Registry key values are stored as properties of each registry key.</span></span> <span data-ttu-id="4554e-172">`Get-ItemProperty`Cmdlet은 지정한 이름을 사용 하 여 레지스트리 키 속성을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-172">The `Get-ItemProperty` cmdlet views registry key properties using the name you specify.</span></span> <span data-ttu-id="4554e-173">결과는 사용자가 지정 하는 속성을 포함 하는 **PSCustomObject** 입니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-173">The result is a **PSCustomObject** containing the properties you specify.</span></span>

<span data-ttu-id="4554e-174">다음 예에서는 cmdlet을 사용 하 여 `Get-ItemProperty` 모든 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-174">The Following example uses the `Get-ItemProperty` cmdlet to view all properties.</span></span> <span data-ttu-id="4554e-175">결과 개체를 변수에 저장 하면 원하는 속성 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-175">Storing the resulting object in a variable allows you to access the desired property value.</span></span>

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

<span data-ttu-id="4554e-176">매개 변수의 값을 지정 `-Name` 하면 사용자가 지정 하는 속성이 선택 되 고 **PSCustomObject** 이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-176">Specifying a value for the `-Name` parameter selects the properties you specify and returns the **PSCustomObject**.</span></span>  <span data-ttu-id="4554e-177">다음 예제에서는 매개 변수를 사용할 때 출력의 차이점을 보여 줍니다 `-Name` .</span><span class="sxs-lookup"><span data-stu-id="4554e-177">The following example shows the difference in output when you use the `-Name` parameter.</span></span>

```
PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem

BUILD                      : 17134.1
Installation Directory     : C:\WINDOWS\system32\WBEM
MOF Self-Install Directory : C:\WINDOWS\system32\WBEM\MOF
PSPath                     : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName                : Wbem
PSDrive                    : HKLM
PSProvider                 : Microsoft.PowerShell.Core\Registry

PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD

BUILD        : 17134.1
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName  : Wbem
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
```

<span data-ttu-id="4554e-178">PowerShell 5.0부터 `Get-ItemPropertyValue` cmdlet은 지정한 속성 값만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-178">Beginning in PowerShell 5.0, the `Get-ItemPropertyValue` cmdlet returns only the value of the property you specify.</span></span>

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

<span data-ttu-id="4554e-179">이 섹션에 사용 된 cmdlet에 대 한 자세한 내용은 다음 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4554e-179">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="4554e-180">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4554e-180">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="4554e-181">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="4554e-181">Get-ItemPropertyValue</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a><span data-ttu-id="4554e-182">레지스트리 키 값 변경</span><span class="sxs-lookup"><span data-stu-id="4554e-182">Changing registry key values</span></span>

<span data-ttu-id="4554e-183">`Set-ItemProperty`Cmdlet은 레지스트리 키에 대 한 특성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-183">The `Set-ItemProperty` cmdlet will set attributes for registry keys.</span></span> <span data-ttu-id="4554e-184">다음 예에서는 `Set-ItemProperty` 를 사용 하 여 스풀러 서비스 시작 유형을 수동으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-184">The following example uses `Set-ItemProperty` to change the spooler service start type to manual.</span></span> <span data-ttu-id="4554e-185">이 예에서는 cmdlet을 사용 하 여 **Starttype** 을 *자동* 으로 다시 변경 합니다 `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="4554e-185">The example changes the **StartType** back to *Automatic* using the `Set-Service` cmdlet.</span></span>

```
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler Automatic

PS C:\> $path = "HKLM:\SYSTEM\CurrentControlSet\Services\Spooler\"
PS C:\> Set-ItemProperty -Path $path -Name Start -Value 3
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler    Manual

PS C:\> Set-Service -Name Spooler -StartupType Automatic
```

<span data-ttu-id="4554e-186">각 레지스트리 키에는 *기본값이* 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-186">Each registry key has a *default* value.</span></span> <span data-ttu-id="4554e-187">또는 중 하나를 사용 하 여 레지스트리 키에 대 한 *기본값* 을 변경할 수 있습니다 `Set-Item` `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="4554e-187">You can change the *default* value for a registry key with either `Set-Item` or `Set-ItemProperty`.</span></span>

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

<span data-ttu-id="4554e-188">이 섹션에 사용 된 cmdlet에 대 한 자세한 내용은 다음 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4554e-188">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="4554e-189">Set-Item</span><span class="sxs-lookup"><span data-stu-id="4554e-189">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="4554e-190">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4554e-190">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a><span data-ttu-id="4554e-191">레지스트리 키 및 값 만들기</span><span class="sxs-lookup"><span data-stu-id="4554e-191">Creating registry keys and values</span></span>

<span data-ttu-id="4554e-192">`New-Item`Cmdlet은 사용자가 제공한 이름을 사용 하 여 레지스트리 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-192">The `New-Item` cmdlet will create registry keys with a name that you provide.</span></span>
<span data-ttu-id="4554e-193">`mkdir`Cmdlet을 내부적으로 호출 하는 함수를 사용할 수도 있습니다 `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="4554e-193">You can also use the `mkdir` function, which calls the `New-Item` cmdlet internally.</span></span>

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

<span data-ttu-id="4554e-194">Cmdlet을 사용 `New-ItemProperty` 하 여 지정 하는 레지스트리 키에 값을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-194">You can use the `New-ItemProperty` cmdlet to create values in a registry key that you specify.</span></span> <span data-ttu-id="4554e-195">다음 예에서는 ContosoCompany 레지스트리 키에 새 DWORD 값을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-195">The following example creates a new DWORD value on the ContosoCompany registry key.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> <span data-ttu-id="4554e-196">허용 되는 다른 유형 값에 대해서는이 문서의 동적 매개 변수 섹션을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-196">Review the dynamic parameters section in this article for other allowed type values.</span></span>

<span data-ttu-id="4554e-197">자세한 cmdlet 사용법은 [get-itemproperty](xref:Microsoft.PowerShell.Management.New-ItemProperty)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4554e-197">For detailed cmdlet usage, see [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).</span></span>

## <a name="copying-registry-keys-and-values"></a><span data-ttu-id="4554e-198">레지스트리 키 및 값 복사</span><span class="sxs-lookup"><span data-stu-id="4554e-198">Copying registry keys and values</span></span>

<span data-ttu-id="4554e-199">**레지스트리** 공급자에서 cmdlet을 사용 하 여 `Copy-Item` 레지스트리 키와 값을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-199">In the **Registry** provider, use the `Copy-Item` cmdlet copies registry keys and values.</span></span> <span data-ttu-id="4554e-200">Cmdlet을 사용 `Copy-ItemProperty` 하 여 레지스트리 값만 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-200">Use the `Copy-ItemProperty` cmdlet to copy registry values only.</span></span>
<span data-ttu-id="4554e-201">다음 명령은 "Contoso" 레지스트리 키와 해당 속성을 지정 된 위치 "HKLM: \ Software\Fabrikam"에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-201">The following command copies the "Contoso" registry key, and its properties to the specified location "HKLM:\Software\Fabrikam".</span></span>

<span data-ttu-id="4554e-202">`Copy-Item` 대상 키가 없는 경우 해당 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-202">`Copy-Item` creates the destination key if it does not exist.</span></span> <span data-ttu-id="4554e-203">대상 키가 있으면에서 `Copy-Item` 원본 키의 복제본을 대상 키의 자식 항목 (하위 키)으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-203">If the destination key exists, `Copy-Item` creates a duplicate of the source key as a child item (subkey) of the destination key.</span></span>

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

<span data-ttu-id="4554e-204">다음 명령은 cmdlet을 사용 하 여 " `Copy-ItemProperty` Contoso" 키의 "서버" 값을 "Fabrikam" 키에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-204">The following command uses the `Copy-ItemProperty` cmdlet to copy the "Server" value from the "Contoso" key to the "Fabrikam" key.</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

<span data-ttu-id="4554e-205">이 섹션에 사용 된 cmdlet에 대 한 자세한 내용은 다음 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4554e-205">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="4554e-206">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="4554e-206">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="4554e-207">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4554e-207">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a><span data-ttu-id="4554e-208">레지스트리 키 및 값 이동</span><span class="sxs-lookup"><span data-stu-id="4554e-208">Moving registry keys and values</span></span>

<span data-ttu-id="4554e-209">`Move-Item`및 `Move-ItemProperty` cmdlet은 "복사" 대응 항목 처럼 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-209">The `Move-Item` and `Move-ItemProperty` cmdlets behave like their "Copy" counterparts.</span></span> <span data-ttu-id="4554e-210">대상이 있으면에서 `Move-Item` 원본 키를 대상 키 아래로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-210">If the destination exists, `Move-Item` moves the source key underneath the destination key.</span></span> <span data-ttu-id="4554e-211">대상 키가 없으면 원본 키가 대상 경로로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-211">If the destination key does not exist, the source key is moved to the destination path.</span></span>

<span data-ttu-id="4554e-212">다음 명령은 "Contoso" 키를 "HKLM: \ \S\fabrikam" 경로로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-212">The following command moves the "Contoso" key to the path "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

<span data-ttu-id="4554e-213">이 명령은 "HKLM: \ SOFTWARE\ContosoCompany"의 모든 속성을 "HKLM: \ \S\fabrikam"으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-213">This command moves all of the properties from "HKLM:\SOFTWARE\ContosoCompany" to "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

<span data-ttu-id="4554e-214">이 섹션에 사용 된 cmdlet에 대 한 자세한 내용은 다음 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4554e-214">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="4554e-215">Move-Item</span><span class="sxs-lookup"><span data-stu-id="4554e-215">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="4554e-216">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4554e-216">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a><span data-ttu-id="4554e-217">레지스트리 키 및 값 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="4554e-217">Renaming registry keys and values</span></span>

<span data-ttu-id="4554e-218">파일 및 폴더와 마찬가지로 레지스트리 키와 값의 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-218">You can rename registry keys and values just like you would files and folders.</span></span>
<span data-ttu-id="4554e-219">`Rename-Item` 레지스트리 키의 이름을 바꾸고 레지스트리 `Rename-ItemProperty` 값의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-219">`Rename-Item` renames registry keys, while `Rename-ItemProperty` renames registry values.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a><span data-ttu-id="4554e-220">보안 설명자 변경</span><span class="sxs-lookup"><span data-stu-id="4554e-220">Changing security descriptors</span></span>

<span data-ttu-id="4554e-221">및 cmdlet을 사용 하 여 레지스트리 키에 대 한 액세스를 제한할 수 있습니다 `Get-Acl` `Set-Acl` .</span><span class="sxs-lookup"><span data-stu-id="4554e-221">You can restrict access to registry keys using the `Get-Acl` and `Set-Acl` cmdlets.</span></span> <span data-ttu-id="4554e-222">다음 예에서는 모든 권한이 있는 새 사용자를 "HKLM: \ \Ent\contoso" 레지스트리 키에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-222">The following example adds a new user with full control to the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

<span data-ttu-id="4554e-223">더 많은 예제 및 cmdlet 사용 세부 정보는 다음 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4554e-223">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="4554e-224">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="4554e-224">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="4554e-225">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="4554e-225">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a><span data-ttu-id="4554e-226">레지스트리 키 및 값 제거 및 지우기</span><span class="sxs-lookup"><span data-stu-id="4554e-226">Removing and clearing registry keys and values</span></span>

<span data-ttu-id="4554e-227">**제거 항목** 을 사용 하 여 포함 된 항목을 제거할 수 있지만 항목에 다른 항목이 들어 있는 경우 제거를 확인 하는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-227">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="4554e-228">다음 예에서는 "HKLM: \ SOFTWARE\Contoso" 키를 삭제 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-228">The following example attempts to delete a key "HKLM:\SOFTWARE\Contoso".</span></span>

```
PS C:\> dir HKLM:\SOFTWARE\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Contoso

Name                           Property
----                           --------
ChildKey

PS C:\> Remove-Item -Path HKLM:\SOFTWARE\Contoso

Confirm
The item at HKLM:\SOFTWARE\Contoso has children and the -Recurse
parameter was not specified. If you continue, all children will be removed
with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="4554e-229">메시지를 표시 하지 않고 포함 된 항목을 삭제 하려면 `-Recurse` 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-229">To delete contained items without prompting, specify the `-Recurse` parameter.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

<span data-ttu-id="4554e-230">"Hklm: \ software\contoso" 내에서 모든 항목을 제거 하 고 "HKLM: \ SOFTWARE\Contoso" 자체를 제거 하려는 경우 후행 백슬래시 `\` 와 와일드 카드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-230">If you wanted to remove all items within "HKLM:\SOFTWARE\Contoso" but not "HKLM:\SOFTWARE\Contoso" itself, use a trailing backslash `\` followed by a wildcard.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

<span data-ttu-id="4554e-231">이 명령은 "HKLM: \ ContosoTest \Contoso" 레지스트리 키에서 "" 레지스트리 값을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-231">This command deletes the "ContosoTest" registry value from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

<span data-ttu-id="4554e-232">`Clear-Item` 키에 대 한 레지스트리 값을 모두 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-232">`Clear-Item` clears all registry values for a key.</span></span> <span data-ttu-id="4554e-233">다음 예에서는 "HKLM: \ SOFTWARE\Contoso" 레지스트리 키에서 모든 값을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-233">The following example clears all values from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span> <span data-ttu-id="4554e-234">특정 속성만 지우려면를 사용 `Clear-ItemProperty` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-234">To clear only a specific property, use `Clear-ItemProperty`.</span></span>

```
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name           Property
----           --------
Contoso        Server     : {a, b, c}
               HereString : {This is text which contains
               newlines. It also contains "quoted" strings}
               (default)  : 1

PS HKLM:\SOFTWARE\> Clear-Item .\Contoso\
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
Contoso
```

<span data-ttu-id="4554e-235">더 많은 예제 및 cmdlet 사용 세부 정보는 다음 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4554e-235">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="4554e-236">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="4554e-236">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="4554e-237">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4554e-237">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="4554e-238">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="4554e-238">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="4554e-239">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4554e-239">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a><span data-ttu-id="4554e-240">동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4554e-240">Dynamic parameters</span></span>

<span data-ttu-id="4554e-241">동적 매개 변수는 PowerShell 공급자가 추가 하는 cmdlet 매개 변수 이며, 공급자 사용 드라이브에서 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-241">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="type-microsoftwin32registryvaluekind"></a><span data-ttu-id="4554e-242"><RegistryValueKind를 입력></span><span class="sxs-lookup"><span data-stu-id="4554e-242">Type <Microsoft.Win32.RegistryValueKind></span></span>

<span data-ttu-id="4554e-243">레지스트리 값의 데이터 형식을 설정하거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-243">Establishes or changes the data type of a registry value.</span></span> <span data-ttu-id="4554e-244">기본값은 `String` (REG_SZ)입니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-244">The default is `String` (REG_SZ).</span></span>

<span data-ttu-id="4554e-245">이 매개 변수는 [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet에서 제대로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-245">This parameter works as designed on the [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet.</span></span> <span data-ttu-id="4554e-246">또한 레지스트리 드라이브의 [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet에도 사용할 수 있지만 효과는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-246">It is also available on the [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet in the registry drives, but it has no effect.</span></span>

|<span data-ttu-id="4554e-247">값</span><span class="sxs-lookup"><span data-stu-id="4554e-247">Value</span></span> | <span data-ttu-id="4554e-248">설명</span><span class="sxs-lookup"><span data-stu-id="4554e-248">Description</span></span> |
| ---- | ----------- |
| `String` | <span data-ttu-id="4554e-249">null로 끝나는 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-249">Specifies a null-terminated string.</span></span> <span data-ttu-id="4554e-250">REG_SZ와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-250">Equivalent to REG_SZ.</span></span> |
| `ExpandString` | <span data-ttu-id="4554e-251">확장 되지 않은를 포함 하는 null로 끝나는 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-251">Specifies a null-terminated string that contains unexpanded</span></span> |
|                | <span data-ttu-id="4554e-252">다음 경우에 확장 되는 환경 변수에 대 한 참조</span><span class="sxs-lookup"><span data-stu-id="4554e-252">references to environment variables that are expanded when</span></span> |
|                | <span data-ttu-id="4554e-253">값이 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-253">the value is retrieved.</span></span> <span data-ttu-id="4554e-254">REG_EXPAND_SZ와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-254">Equivalent to REG_EXPAND_SZ.</span></span> |
| `Binary` | <span data-ttu-id="4554e-255">임의의 형식으로 된 이진 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-255">Specifies binary data in any form.</span></span> <span data-ttu-id="4554e-256">REG_BINARY와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-256">Equivalent to REG_BINARY.</span></span> |
| `DWord` | <span data-ttu-id="4554e-257">32비트 이진수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-257">Specifies a 32-bit binary number.</span></span> <span data-ttu-id="4554e-258">REG_DWORD와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-258">Equivalent to REG_DWORD.</span></span> |
| `MultiString` | <span data-ttu-id="4554e-259">에서 종료 하는 null로 끝나는 문자열의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-259">Specifies an array of null-terminated strings terminated by</span></span> |
|               | <span data-ttu-id="4554e-260">두 null 문자</span><span class="sxs-lookup"><span data-stu-id="4554e-260">two null characters.</span></span> <span data-ttu-id="4554e-261">REG_MULTI_SZ와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-261">Equivalent to REG_MULTI_SZ.</span></span> |
| `QWord` | <span data-ttu-id="4554e-262">64비트 이진수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-262">Specifies a 64-bit binary number.</span></span> <span data-ttu-id="4554e-263">REG_QWORD와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-263">Equivalent to REG_QWORD.</span></span> |
| `Unknown` | <span data-ttu-id="4554e-264">지원 되지 않는 레지스트리 데이터 형식을 나타냅니다 (예:).</span><span class="sxs-lookup"><span data-stu-id="4554e-264">Indicates an unsupported registry data type, such as</span></span> |
|           | <span data-ttu-id="4554e-265">REG_RESOURCE_LIST.</span><span class="sxs-lookup"><span data-stu-id="4554e-265">REG_RESOURCE_LIST.</span></span> |

#### <a name="cmdlets-supported"></a><span data-ttu-id="4554e-266">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="4554e-266">Cmdlets supported</span></span>

- [<span data-ttu-id="4554e-267">Set-Item</span><span class="sxs-lookup"><span data-stu-id="4554e-267">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="4554e-268">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4554e-268">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a><span data-ttu-id="4554e-269">파이프라인 사용</span><span class="sxs-lookup"><span data-stu-id="4554e-269">Using the pipeline</span></span>

<span data-ttu-id="4554e-270">공급자 cmdlet은 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-270">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="4554e-271">파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-271">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span> <span data-ttu-id="4554e-272">공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4554e-272">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="4554e-273">도움말 보기</span><span class="sxs-lookup"><span data-stu-id="4554e-273">Getting help</span></span>

<span data-ttu-id="4554e-274">Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-274">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="4554e-275">파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 `Get-Help` 파일 시스템 드라이브에서 명령을 실행 하거나 **Path** 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4554e-275">To get the help topics that are customized for the file system drive, run a `Get-Help` command in a file system drive or use the **Path** parameter to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a><span data-ttu-id="4554e-276">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4554e-276">See also</span></span>

 [<span data-ttu-id="4554e-277">about_Providers</span><span class="sxs-lookup"><span data-stu-id="4554e-277">about_Providers</span></span>](../About/about_Providers.md)


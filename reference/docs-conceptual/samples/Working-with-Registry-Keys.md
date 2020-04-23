---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 레지스트리 키 작업
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736848"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="927da-103">레지스트리 키 작업</span><span class="sxs-lookup"><span data-stu-id="927da-103">Working with Registry Keys</span></span>

<span data-ttu-id="927da-104">레지스트리 키는 PowerShell 드라이브에 있는 항목이므로 레지스트리 키에 대한 작업 수행은 파일 및 폴더 작업과 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="927da-104">Because registry keys are items on PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="927da-105">한 가지 중요한 차이점은 레지스트리 기반 PowerShell 드라이브의 모든 항목은 파일 시스템 드라이브의 폴더와 같이 컨테이너라는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="927da-105">One critical difference is that every item on a registry-based PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="927da-106">그러나 레지스트리 항목 및 연결된 값은 고유한 항목이 아니라 항목의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="927da-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="927da-107">레지스트리 키의 모든 하위 키 표시</span><span class="sxs-lookup"><span data-stu-id="927da-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="927da-108">`Get-ChildItem`을 사용하여 레지스트리 키 바로 아래에 있는 항목을 모두 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="927da-108">You can show all items directly within a registry key by using `Get-ChildItem`.</span></span> <span data-ttu-id="927da-109">선택적 **Force** 매개 변수를 추가하면 숨겨진 항목이나 시스템 항목을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="927da-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="927da-110">예를 들어 다음 명령은 `HKCU:` 레지스트리 하이브에 해당하는 Windows PowerShell 드라이브 `HKEY_CURRENT_USER` 바로 아래에 있는 항목을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="927da-110">For example, this command displays the items directly within PowerShell drive `HKCU:`, which corresponds to the `HKEY_CURRENT_USER` registry hive:</span></span>

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

<span data-ttu-id="927da-111">이러한 키는 레지스트리 편집기(Regedit.exe)의 `HKEY_CURRENT_USER`에 표시되는 최상위 키입니다.</span><span class="sxs-lookup"><span data-stu-id="927da-111">These are the top-level keys visible under `HKEY_CURRENT_USER` in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="927da-112">레지스트리 공급자 이름(뒤에 `::`이 옴)을 지정하여 레지스트리 경로를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="927da-112">You can also specify this registry path by specifying the registry provider's name, followed by `::`.</span></span> <span data-ttu-id="927da-113">레지스트리 공급자의 전체 이름이 `Microsoft.PowerShell.Core\Registry`가 되지만 `Registry`로만 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="927da-113">The registry provider's full name is `Microsoft.PowerShell.Core\Registry`, but this can be shortened to just `Registry`.</span></span> <span data-ttu-id="927da-114">다음 명령은 `HKCU:` 바로 아래에 있는 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="927da-114">Any of the following commands will list the contents directly under `HKCU:`.</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="927da-115">이 명령은 `DIR`Cmd.exe**의**  명령이나 UNIX 셸의 `ls`를 사용하는 것과 매우 유사한 방법으로 바로 아래에 포함된 항목만 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="927da-115">These commands list only the directly contained items, much like using `DIR` in **Cmd.exe** or `ls` in a UNIX shell.</span></span> <span data-ttu-id="927da-116">포함된 항목을 모두 보려면 **Recurse** 매개 변수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="927da-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="927da-117">`HKCU:`의 모든 레지스트리 키를 나열하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="927da-117">To list all registry keys in `HKCU:`, use the following command.</span></span>

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

<span data-ttu-id="927da-118">`Get-ChildItem`은 **Path**, **Filter**, **Include** 및 **Exclude** 매개 변수로 복잡한 필터링 기능을 수행할 수 있지만 이러한 변수는 일반적으로 이름을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="927da-118">`Get-ChildItem` can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="927da-119">`Where-Object` cmdlet을 사용하여 항목의 다른 속성을 기반으로 복잡한 필터링을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="927da-119">You can perform complex filtering based on other properties of items by using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="927da-120">다음 명령은 `HKCU:\Software` 내에서 정확히 한 개의 하위 키와 네 개의 값을 갖는 모든 키를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="927da-120">The following command finds all keys within `HKCU:\Software` that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="927da-121">키 복사</span><span class="sxs-lookup"><span data-stu-id="927da-121">Copying Keys</span></span>

<span data-ttu-id="927da-122">`Copy-Item`을 사용하여 복사를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="927da-122">Copying is done with `Copy-Item`.</span></span> <span data-ttu-id="927da-123">다음 예제에서는 `CurrentVersion`의 `HKLM:\SOFTWARE\Microsoft\Windows\` 하위 키와 모든 속성을 `HKCU:\`로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="927da-123">The following example copies the `CurrentVersion` subkey of `HKLM:\SOFTWARE\Microsoft\Windows\` and all of its properties to `HKCU:\`.</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

<span data-ttu-id="927da-124">레지스트리 편집기나 `Get-ChildItem`을 사용하여 새 키를 검사하면 포함된 하위 키가 새 위치에 복사되지 않은 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="927da-124">If you examine this new key in the registry editor or by using `Get-ChildItem`, you notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="927da-125">컨테이너의 내용을 모두 복사하려면 **Recurse** 매개 변수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="927da-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="927da-126">위의 복사 명령을 재귀적으로 실행하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="927da-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

<span data-ttu-id="927da-127">파일 시스템 복사를 위해 이전부터 사용하던 다른 도구를 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="927da-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="927da-128">예를 들어 **reg.exe**, **regini.exe**, **regedit.exe** 같은 레지스트리 편집 도구와 **WScript.Shell** 및 WMI의 **StdRegProv** 클래스와 같이 레지스트리 편집을 지원하는 COM 개체를 Windows PowerShell에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="927da-128">Any registry editing tools—including **reg.exe**, **regini.exe**, **regedit.exe**, and COM objects that support registry editing, such as **WScript.Shell** and WMI's **StdRegProv** class can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="927da-129">키 만들기</span><span class="sxs-lookup"><span data-stu-id="927da-129">Creating Keys</span></span>

<span data-ttu-id="927da-130">레지스트리에서 새 키를 만드는 것은 파일 시스템에서 새 항목을 만드는 것보다 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="927da-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="927da-131">모든 레지스트리 키가 컨테이너이므로 항목 유형을 지정할 필요 없이 다음과 같이 명시적 경로만 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="927da-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

<span data-ttu-id="927da-132">다음과 같이 공급자 기반 경로를 사용하여 키를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="927da-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="927da-133">키 삭제</span><span class="sxs-lookup"><span data-stu-id="927da-133">Deleting Keys</span></span>

<span data-ttu-id="927da-134">기본적으로 항목 삭제는 모든 공급자에 대해 동일하게 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="927da-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="927da-135">다음 명령은 항목을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="927da-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="927da-136">특정 키 아래에 있는 모든 키 제거</span><span class="sxs-lookup"><span data-stu-id="927da-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="927da-137">`Remove-Item`을 사용하면 포함된 항목을 제거할 수 있지만 이 항목에 다른 항목이 들어 있는 경우 제거를 확인하는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="927da-137">You can remove contained items by using `Remove-Item`, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="927da-138">예를 들어 앞에서 만든 `HKCU:\CurrentVersion` 하위 키를 삭제하려고 하면 다음과 같은 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="927da-138">For example, if we attempt to delete the `HKCU:\CurrentVersion` subkey we created, we see this:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="927da-139">확인 메시지 없이 포함된 항목을 삭제하려면 다음과 같이 **Recurse** 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="927da-139">To delete contained items without prompting, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="927da-140">`HKCU:\CurrentVersion` 내에서 모든 항목을 제거하지만 `HKCU:\CurrentVersion` 자체는 제거하지 않으려는 경우 다음을 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="927da-140">If you wanted to remove all items within `HKCU:\CurrentVersion` but not `HKCU:\CurrentVersion` itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```

---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 레지스트리 항목 작업
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403119"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="f56ea-103">레지스트리 항목 작업</span><span class="sxs-lookup"><span data-stu-id="f56ea-103">Working with Registry Entries</span></span>

<span data-ttu-id="f56ea-104">레지스트리 항목은 키의 속성이어서 직접 검색할 수 없으므로 레지스트리 항목으로 작업할 경우 약간 다른 방법으로 접근해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="f56ea-105">레지스트리 항목 나열</span><span class="sxs-lookup"><span data-stu-id="f56ea-105">Listing Registry Entries</span></span>

<span data-ttu-id="f56ea-106">다양한 방법으로 레지스트리 항목을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="f56ea-107">가장 간단한 방법은 속성 이름을 키와 연결하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="f56ea-108">예를 들어 **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion** 레지스트리 키에 있는 항목의 이름을 표시하려면 **Get-Item**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="f56ea-109">레지스트리 키에는 키에 있는 레지스트리 항목의 목록인 "Property" 제네릭 이름을 가진 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="f56ea-110">다음 명령은 Property 속성을 선택하고 목록에 표시되도록 항목을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="f56ea-111">레지스트리 항목을 읽기 쉽게 표시하려면 **Get-ItemProperty**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

<span data-ttu-id="f56ea-112">키의 Windows PowerShell 관련 속성은 모두 "PS" 접두사가 붙어 있습니다(예: **PSPath**, **PSParentPath**, **PSChildName** 및 **PSProvider**).</span><span class="sxs-lookup"><span data-stu-id="f56ea-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="f56ea-113">"**.**" 표기법을 사용하여 현재 위치를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="f56ea-114">먼저 **Set-Location**을 사용하여 **CurrentVersion** 레지스트리 컨테이너로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="f56ea-115">또는 기본 제공 HKLM PSDrive를 **Set-Location**과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="f56ea-116">그런 다음 현재 위치에 "**.**" 표기법을 사용하여 전체 경로를 지정하지 않고 속성을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="f56ea-117">경로 확장은 파일 시스템에서와 동일하게 작동하므로 이 위치에서 **Get-ItemProperty -Path ..\\Help**를 사용하여 **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help**에 대한 **ItemProperty** 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="f56ea-118">단일 레지스트리 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="f56ea-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="f56ea-119">레지스트리 키에서 특정 항목을 검색하려면 여러 가지 방법 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="f56ea-120">이 예제에서는 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**에서 **DevicePath** 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="f56ea-121">**Get-ItemProperty**에서 **Path** 매개 변수를 사용하여 키의 이름을 지정하고, **Name** 매개 변수를 사용하여 **DevicePath** 항목의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="f56ea-122">이 명령은 표준 Windows PowerShell 속성과 **DevicePath** 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="f56ea-123">**Get-ItemProperty**에는 **Filter**, **Include** 및 **Exclude** 매개 변수가 있지만 속성 이름을 필터링하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="f56ea-124">이러한 매개 변수를 레지스트리 키(항목 경로)라고 하며 레지스트리 항목(항목 속성)이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="f56ea-125">다른 옵션으로 Reg.exe 명령줄 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="f56ea-126">reg.exe에 대한 도움말을 보려면 명령 프롬프트에서 **reg.exe /?** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="f56ea-127">.</span><span class="sxs-lookup"><span data-stu-id="f56ea-127">at a command prompt.</span></span> <span data-ttu-id="f56ea-128">DevicePath 항목을 찾으려면 다음 명령에 표시된 대로 reg.exe를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="f56ea-129">**WshShell COM** 개체를 사용하여 일부 레지스트리 항목을 찾을 수도 있습니다. 이 방법은 대규모 이진 데이터나 "\\"와 같은 문자를 포함하는 레지스트리 항목 이름에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="f56ea-130">\\ 구분 기호를 사용하여 속성 이름을 항목 경로에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="f56ea-131">새 레지스트리 항목 만들기</span><span class="sxs-lookup"><span data-stu-id="f56ea-131">Creating New Registry Entries</span></span>

<span data-ttu-id="f56ea-132">"PowerShellPath"라는 새 항목을 **CurrentVersion** 키에 추가하려면 키 경로, 항목 이름, 항목 값과 함께 **New-ItemProperty**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="f56ea-133">이 예제에서는 Windows PowerShell의 설치 디렉터리 경로를 저장하는 Windows PowerShell 변수 값 **$PSHome**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="f56ea-134">다음 명령을 사용하여 새 항목을 키에 추가할 수 있습니다. 이 명령은 새 항목에 대한 정보도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="f56ea-135">**PropertyType**은 다음 표에서 **Microsoft.Win32.RegistryValueKind** 열거형 멤버의 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="f56ea-136">PropertyType 값</span><span class="sxs-lookup"><span data-stu-id="f56ea-136">PropertyType Value</span></span>|<span data-ttu-id="f56ea-137">의미</span><span class="sxs-lookup"><span data-stu-id="f56ea-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="f56ea-138">이진</span><span class="sxs-lookup"><span data-stu-id="f56ea-138">Binary</span></span>|<span data-ttu-id="f56ea-139">이진 데이터</span><span class="sxs-lookup"><span data-stu-id="f56ea-139">Binary data</span></span>|
|<span data-ttu-id="f56ea-140">Dword</span><span class="sxs-lookup"><span data-stu-id="f56ea-140">DWord</span></span>|<span data-ttu-id="f56ea-141">유효한 UInt32 숫자</span><span class="sxs-lookup"><span data-stu-id="f56ea-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="f56ea-142">ExpandString</span><span class="sxs-lookup"><span data-stu-id="f56ea-142">ExpandString</span></span>|<span data-ttu-id="f56ea-143">동적으로 확장되는 환경 변수를 포함할 수 있는 문자열</span><span class="sxs-lookup"><span data-stu-id="f56ea-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="f56ea-144">MultiString</span><span class="sxs-lookup"><span data-stu-id="f56ea-144">MultiString</span></span>|<span data-ttu-id="f56ea-145">다중 행 문자열</span><span class="sxs-lookup"><span data-stu-id="f56ea-145">A multiline string</span></span>|
|<span data-ttu-id="f56ea-146">문자열</span><span class="sxs-lookup"><span data-stu-id="f56ea-146">String</span></span>|<span data-ttu-id="f56ea-147">임의의 문자열 값</span><span class="sxs-lookup"><span data-stu-id="f56ea-147">Any string value</span></span>|
|<span data-ttu-id="f56ea-148">Qword</span><span class="sxs-lookup"><span data-stu-id="f56ea-148">QWord</span></span>|<span data-ttu-id="f56ea-149">8바이트 이진 데이터</span><span class="sxs-lookup"><span data-stu-id="f56ea-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="f56ea-150">**Path** 매개 변수에 대한 값의 배열을 지정하여 여러 위치에 레지스트리 항목을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="f56ea-151">**Force** 매개 변수를 **New-ItemProperty** 명령에 추가하여 기존 레지스트리 항목 값을 덮어쓸 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="f56ea-152">레지스트리 항목 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="f56ea-152">Renaming Registry Entries</span></span>

<span data-ttu-id="f56ea-153">**PowerShellPath** 항목의 이름을 "PSHome"으로 바꾸려면 **Rename-ItemProperty**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="f56ea-154">이름을 바꾼 값을 표시하려면 **PassThru** 매개 변수를 명령에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="f56ea-155">레지스트리 항목 삭제</span><span class="sxs-lookup"><span data-stu-id="f56ea-155">Deleting Registry Entries</span></span>

<span data-ttu-id="f56ea-156">PSHome 및 PowerShellPath 레지스트리 항목을 모두 삭제하려면 **Remove-ItemProperty**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f56ea-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
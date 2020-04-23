---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 레지스트리 항목 작업
ms.openlocfilehash: c1fd6f57f13240eb2039f2d5756796678800aee0
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030723"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="3d5a0-103">레지스트리 항목 작업</span><span class="sxs-lookup"><span data-stu-id="3d5a0-103">Working with Registry Entries</span></span>

<span data-ttu-id="3d5a0-104">레지스트리 항목은 키의 속성이어서 직접 검색할 수 없으므로 레지스트리 항목으로 작업할 경우 약간 다른 방법으로 접근해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

## <a name="listing-registry-entries"></a><span data-ttu-id="3d5a0-105">레지스트리 항목 나열</span><span class="sxs-lookup"><span data-stu-id="3d5a0-105">Listing Registry Entries</span></span>

<span data-ttu-id="3d5a0-106">다양한 방법으로 레지스트리 항목을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="3d5a0-107">가장 간단한 방법은 속성 이름을 키와 연결하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="3d5a0-108">예를 들어 레지스트리 키 `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`의 항목 이름을 보려면 `Get-Item`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="3d5a0-109">레지스트리 키에는 키에 있는 레지스트리 항목의 목록인 "Property" 제네릭 이름을 가진 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="3d5a0-110">다음 명령은 Property 속성을 선택하고 목록에 표시되도록 항목을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="3d5a0-111">레지스트리 항목을 읽기 쉽게 보려면 `Get-ItemProperty`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

<span data-ttu-id="3d5a0-112">키의 Windows PowerShell 관련 속성은 모두 "PS" 접두사가 붙어 있습니다(예: **PSPath**, **PSParentPath**, **PSChildName** 및 **PSProvider**).</span><span class="sxs-lookup"><span data-stu-id="3d5a0-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="3d5a0-113">`*.*` 표기법을 사용하여 현재 위치를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="3d5a0-114">먼저 `Set-Location`을 사용하여 **CurrentVersion** 레지스트리 컨테이너로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="3d5a0-115">또는 기본 제공 HKLM PSDrive를 `Set-Location`과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="3d5a0-116">그런 다음, 현재 위치에 `*.*` 표기법을 사용하여 전체 경로를 지정하지 않고 속성을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="3d5a0-117">경로 확장은 파일 시스템에서와 동일하게 작동하므로 이 위치에서 **를 사용하여** 에 대한 `HKLM:\SOFTWARE\Microsoft\Windows\Help`ItemProperty`Get-ItemProperty -Path ..\Help` 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

## <a name="getting-a-single-registry-entry"></a><span data-ttu-id="3d5a0-118">단일 레지스트리 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="3d5a0-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="3d5a0-119">레지스트리 키에서 특정 항목을 검색하려면 여러 가지 방법 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="3d5a0-120">이 예제에서는 **에서** DevicePath`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`의 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="3d5a0-121">`Get-ItemProperty`를 사용하면서, **Path** 매개 변수를 사용하여 키의 이름을 지정하고, **Name** 매개 변수를 사용하여 **DevicePath** 항목의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="3d5a0-122">이 명령은 표준 Windows PowerShell 속성과 **DevicePath** 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="3d5a0-123">`Get-ItemProperty`에는 **Filter**, **Include** 및 **Exclude** 매개 변수가 있지만 속성 이름을 기준으로 필터링하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="3d5a0-124">이러한 매개 변수를 레지스트리 키(항목 경로)라고 하며 레지스트리 항목이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-124">These parameters refer to registry keys, which are item paths and not registry entries.</span></span> <span data-ttu-id="3d5a0-125">레지스트리 항목은 항목 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-125">Registry entries which are item properties.</span></span>

<span data-ttu-id="3d5a0-126">다른 옵션으로 Reg.exe 명령줄 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="3d5a0-127">reg.exe에 대한 도움말을 보려면 명령 프롬프트에 `reg.exe /?`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="3d5a0-128">DevicePath 항목을 찾으려면 다음 명령에 표시된 대로 reg.exe를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="3d5a0-129">**WshShell** COM 개체를 사용하여 일부 레지스트리 항목을 찾을 수도 있습니다. 이 방법은 대규모 이진 데이터나 “\\”와 같은 문자를 포함하는 레지스트리 항목 이름에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="3d5a0-130">\\ 구분 기호를 사용하여 속성 이름을 항목 경로에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a><span data-ttu-id="3d5a0-131">단일 레지스트리 항목 설정</span><span class="sxs-lookup"><span data-stu-id="3d5a0-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="3d5a0-132">레지스트리 키에서 특정 항목을 변경하려면 여러 가지 방법 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="3d5a0-133">이 예제에서는 **아래의**Path`HKEY_CURRENT_USER\Environment` 항목을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="3d5a0-134">**Path** 항목은 실행 파일을 찾는 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="3d5a0-135">**를 사용하여** Path`Get-ItemProperty` 항목의 현재 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="3d5a0-136">`;`으로 구분하여 새 값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="3d5a0-137">지정된 키, 항목 이름 및 값과 함께 `Set-ItemProperty`를 사용하여 레지스트리 항목을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="3d5a0-138">`Set-ItemProperty`에는 **Filter**, **Include** 및 **Exclude** 매개 변수가 있지만 속성 이름을 기준으로 필터링하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-138">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="3d5a0-139">이러한 매개 변수를 레지스트리 키(항목 경로)라고 하며 레지스트리 항목(항목 속성)이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="3d5a0-140">다른 옵션으로 Reg.exe 명령줄 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="3d5a0-141">reg.exe에 대한 도움말을 보려면 명령 프롬프트에서 **reg.exe /?** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="3d5a0-142">.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-142">at a command prompt.</span></span>

<span data-ttu-id="3d5a0-143">다음 예제에서는 위 예제에 추가된 경로를 제거하여 **Path** 항목을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="3d5a0-144">`Get-ItemProperty`는 `reg query`에서 반환된 문자열을 구문 분석할 필요가 없도록 현재 값을 검색하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-144">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="3d5a0-145">**SubString** 및 **LastIndexOf** 메서드는 **Path** 항목에 추가된 마지막 경로를 검색하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a><span data-ttu-id="3d5a0-146">새 레지스트리 항목 만들기</span><span class="sxs-lookup"><span data-stu-id="3d5a0-146">Creating New Registry Entries</span></span>

<span data-ttu-id="3d5a0-147">“PowerShellPath”라는 새 항목을 **CurrentVersion** 키에 추가하려면 키 경로, 항목 이름, 항목 값과 함께 `New-ItemProperty`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="3d5a0-148">이 예제에서는 Windows PowerShell의 설치 디렉터리 경로를 저장하는 Windows PowerShell 변수 값 `$PSHome`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="3d5a0-149">다음 명령을 사용하여 새 항목을 키에 추가할 수 있습니다. 이 명령은 새 항목에 대한 정보도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="3d5a0-150">**PropertyType**은 다음 표에서 **Microsoft.Win32.RegistryValueKind** 열거형 멤버의 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="3d5a0-151">PropertyType 값</span><span class="sxs-lookup"><span data-stu-id="3d5a0-151">PropertyType Value</span></span>|<span data-ttu-id="3d5a0-152">의미</span><span class="sxs-lookup"><span data-stu-id="3d5a0-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="3d5a0-153">이진</span><span class="sxs-lookup"><span data-stu-id="3d5a0-153">Binary</span></span>|<span data-ttu-id="3d5a0-154">이진 데이터</span><span class="sxs-lookup"><span data-stu-id="3d5a0-154">Binary data</span></span>|
|<span data-ttu-id="3d5a0-155">Dword</span><span class="sxs-lookup"><span data-stu-id="3d5a0-155">DWord</span></span>|<span data-ttu-id="3d5a0-156">유효한 UInt32 숫자</span><span class="sxs-lookup"><span data-stu-id="3d5a0-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="3d5a0-157">ExpandString</span><span class="sxs-lookup"><span data-stu-id="3d5a0-157">ExpandString</span></span>|<span data-ttu-id="3d5a0-158">동적으로 확장되는 환경 변수를 포함할 수 있는 문자열</span><span class="sxs-lookup"><span data-stu-id="3d5a0-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="3d5a0-159">MultiString</span><span class="sxs-lookup"><span data-stu-id="3d5a0-159">MultiString</span></span>|<span data-ttu-id="3d5a0-160">다중 행 문자열</span><span class="sxs-lookup"><span data-stu-id="3d5a0-160">A multiline string</span></span>|
|<span data-ttu-id="3d5a0-161">String</span><span class="sxs-lookup"><span data-stu-id="3d5a0-161">String</span></span>|<span data-ttu-id="3d5a0-162">임의의 문자열 값</span><span class="sxs-lookup"><span data-stu-id="3d5a0-162">Any string value</span></span>|
|<span data-ttu-id="3d5a0-163">Qword</span><span class="sxs-lookup"><span data-stu-id="3d5a0-163">QWord</span></span>|<span data-ttu-id="3d5a0-164">8바이트 이진 데이터</span><span class="sxs-lookup"><span data-stu-id="3d5a0-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="3d5a0-165">**Path** 매개 변수에 대한 값의 배열을 지정하여 여러 위치에 레지스트리 항목을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="3d5a0-166">**Force** 매개 변수를 `New-ItemProperty` 명령에 추가하여 기존 레지스트리 항목 값을 덮어쓸 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

## <a name="renaming-registry-entries"></a><span data-ttu-id="3d5a0-167">레지스트리 항목 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="3d5a0-167">Renaming Registry Entries</span></span>

<span data-ttu-id="3d5a0-168">**PowerShellPath** 항목의 이름을 “PSHome”으로 바꾸려면 `Rename-ItemProperty`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="3d5a0-169">이름을 바꾼 값을 표시하려면 **PassThru** 매개 변수를 명령에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a><span data-ttu-id="3d5a0-170">레지스트리 항목 삭제</span><span class="sxs-lookup"><span data-stu-id="3d5a0-170">Deleting Registry Entries</span></span>

<span data-ttu-id="3d5a0-171">PSHome 및 PowerShellPath 레지스트리 항목을 모두 삭제하려면 `Remove-ItemProperty`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d5a0-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```

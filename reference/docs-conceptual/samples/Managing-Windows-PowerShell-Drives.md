---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 드라이브 관리
description: PowerShell 드라이브는 PowerShell의 파일 시스템 드라이브처럼 사용자가 액세스할 수 있는 데이터 저장소 위치입니다. 기본적으로 PowerShell에는 파일 시스템, 레지스트리, 인증서 저장소 등을 지원하는 공급자가 포함되어 있습니다.
ms.openlocfilehash: e4e5347c3f3458f25cea31c8e5a499474985220a
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500337"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="9d678-105">Windows PowerShell 드라이브 관리</span><span class="sxs-lookup"><span data-stu-id="9d678-105">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="9d678-106">*Windows PowerShell 드라이브* 는 Windows PowerShell의 파일 시스템 드라이브처럼 사용자가 액세스할 수 있는 데이터 저장소 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-106">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="9d678-107">Windows PowerShell 공급자가 파일 시스템 드라이브(C: 및 D: 포함), 레지스트리 드라이브(HKCU: 및 HKLM:), 인증서 드라이브(Cert:) 등과 같은 일부 드라이브를 만들고, 사용자는 자신의 Windows PowerShell 드라이브를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-107">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="9d678-108">이러한 드라이브는 매우 유용하지만 Windows PowerShell 내에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-108">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="9d678-109">파일 탐색기, Cmd.exe 등과 같은 다른 Windows 도구를 사용하여 이 드라이브에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-109">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="9d678-110">Windows PowerShell에서는 Windows PowerShell 드라이브 작업을 위한 명령에 명사 **PSDrive** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-110">Windows PowerShell uses the noun, **PSDrive** , for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="9d678-111">Windows PowerShell 세션의 Windows PowerShell 드라이브 목록을 보려면 **Get-PSDrive** cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-111">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

<span data-ttu-id="9d678-112">표시되는 드라이브는 시스템의 드라이브에 따라 다르지만 목록은 위에 표시된 **Get-PSDrive** 명령의 출력과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-112">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="9d678-113">파일 시스템 드라이브는 Windows PowerShell 드라이브의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-113">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="9d678-114">공급자 열의 FileSystem 항목으로 파일 시스템 드라이브를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-114">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="9d678-115">Windows PowerShell FileSystem 공급자는 Windows PowerShell의 파일 시스템 드라이브를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-115">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="9d678-116">**Get-PSDrive** cmdlet의 구문을 보려면 **Get-Command** 명령을 **Syntax** 매개 변수와 함께 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-116">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="9d678-117">**PSProvider** 매개 변수를 사용하면 특정 공급자가 지원하는 Windows PowerShell 드라이브만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-117">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="9d678-118">예를 들어 Windows PowerShell FileSystem 공급자가 지원하는 Windows PowerShell 드라이브만 표시하려면 **Get-PSDrive** 명령을 **PSProvider** 매개 변수 및 **FileSystem** 값과 함께 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-118">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="9d678-119">레지스트리 하이브를 나타내는 Windows PowerShell 드라이브를 보려면 **PSProvider** 매개 변수를 사용하여 Windows PowerShell 레지스트리 공급자가 지원하는 Windows PowerShell 드라이브만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-119">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="9d678-120">표준 위치 cmdlet을 Windows PowerShell 드라이브와 함께 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-120">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="9d678-121">새 Windows PowerShell 드라이브 추가(New-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="9d678-121">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="9d678-122">**New-PSDrive** 명령을 사용하여 자체 Windows PowerShell 드라이브를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-122">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="9d678-123">**New-PSDrive** 명령의 구문을 가져오려면 **Get-Command** 명령을 **Syntax** 매개 변수와 함께 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-123">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="9d678-124">새 Windows PowerShell 드라이브를 만들려면 다음과 같은 세 가지 매개 변수를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-124">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="9d678-125">드라이브의 이름(모든 유효한 Windows PowerShell 이름 사용 가능)</span><span class="sxs-lookup"><span data-stu-id="9d678-125">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="9d678-126">PSProvider(파일 시스템 위치의 경우 "FileSystem", 레지스트리 위치의 경우 "Registry" 사용)</span><span class="sxs-lookup"><span data-stu-id="9d678-126">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="9d678-127">루트(새 드라이브의 루트 경로)</span><span class="sxs-lookup"><span data-stu-id="9d678-127">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="9d678-128">예를 들어 컴퓨터의 Microsoft Office 애플리케이션을 포함하는 폴더에 매핑되는 "Office" 드라이브를 만들 수 있습니다(예: **C:\\Program Files\\Microsoft Office\\OFFICE11** ).</span><span class="sxs-lookup"><span data-stu-id="9d678-128">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11** .</span></span> <span data-ttu-id="9d678-129">드라이브를 만들려면 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-129">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="9d678-130">일반적으로 경로는 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-130">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="9d678-131">모든 Windows PowerShell 드라이브를 나타낼 때와 마찬가지로 이름 뒤에 콜론( **:** )을 사용하여 새 Windows PowerShell 드라이브를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-131">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon ( **:** ).</span></span>

<span data-ttu-id="9d678-132">Windows PowerShell 드라이브를 사용하면 많은 작업을 훨씬 간편하게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-132">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="9d678-133">예를 들어 Windows 레지스트리의 가장 중요한 일부 키는 매우 긴 경로를 사용하여 액세스하기 번거롭고 기억하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-133">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="9d678-134">중요 구성 정보는 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion** 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-134">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion** .</span></span> <span data-ttu-id="9d678-135">CurrentVersion 레지스트리 키의 항목을 보고 변경하려면 다음과 같이 입력하여 해당 키의 루트로 사용할 Windows PowerShell 드라이브를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-135">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="9d678-136">그런 다음 다른 드라이브와 마찬가지로 위치를 **cvkey:** 드라이브로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-136">You can then change location to the **cvkey:** drive as you would any other drive:</span></span>

```
PS> cd cvkey:
```

<span data-ttu-id="9d678-137">또는</span><span class="sxs-lookup"><span data-stu-id="9d678-137">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="9d678-138">New-PsDrive cmdlet은 현재 Windows PowerShell 세션에만 새 드라이브를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-138">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="9d678-139">따라서 Windows PowerShell 창을 닫으면 새 드라이브가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-139">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="9d678-140">Windows PowerShell 드라이브를 저장하려면 Export-Console cmdlet을 사용하여 현재 Windows PowerShell 세션을 내보낸 다음 PowerShell.exe **PSConsoleFile** 매개 변수를 사용하여 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-140">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="9d678-141">또는 새 드라이브를 Windows PowerShell 프로필에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-141">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="9d678-142">Windows PowerShell 드라이브 삭제(Remove-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="9d678-142">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="9d678-143">**Remove-PSDrive** cmdlet을 사용하여 Windows PowerShell에서 드라이브를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-143">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="9d678-144">**Remove-PSDrive** cmdlet은 사용하기 쉽습니다. 특정 Windows PowerShell 드라이브를 삭제하려면 Windows PowerShell 드라이브 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-144">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="9d678-145">예를 들어 **Office:** Windows PowerShell 드라이브를 추가한 경우( **New-PSDrive** 항목 참조) 다음과 같이 입력하여 해당 드라이브를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-145">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="9d678-146">**New-PSDrive** 에 표시된 **cvkey:** Windows PowerShell 드라이브를 삭제하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-146">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="9d678-147">Windows PowerShell 드라이브는 쉽게 삭제할 수 있지만 드라이브 내에서는 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-147">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="9d678-148">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-148">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="9d678-149">Windows PowerShell 외부 드라이브 추가 및 제거</span><span class="sxs-lookup"><span data-stu-id="9d678-149">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="9d678-150">Windows PowerShell은 Windows에서 추가되거나 제거된 파일 시스템 드라이브(매핑되는 네트워크 드라이브, 연결된 USB 드라이브, WSH(Windows 스크립트 호스트) 스크립트에서 **net use** 명령 또는 **WScript.NetworkMapNetworkDrive** 및 **RemoveNetworkDrive** 메서드를 사용하여 삭제한 드라이브 등)를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9d678-150">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSDrive
ms.openlocfilehash: bfcef6f5277368d172977c81e69a79548af81f92
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211617"
---
# <span data-ttu-id="f96af-103">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="f96af-103">New-PSDrive</span></span>

## <span data-ttu-id="f96af-104">개요</span><span class="sxs-lookup"><span data-stu-id="f96af-104">SYNOPSIS</span></span>
<span data-ttu-id="f96af-105">임시 및 영구 매핑된 네트워크 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-105">Creates temporary and persistent mapped network drives.</span></span>

## <span data-ttu-id="f96af-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f96af-106">SYNTAX</span></span>

### <span data-ttu-id="f96af-107">모두</span><span class="sxs-lookup"><span data-stu-id="f96af-107">All</span></span>

```
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Description <String>]
 [-Scope <String>] [-Persist] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="f96af-108">설명</span><span class="sxs-lookup"><span data-stu-id="f96af-108">DESCRIPTION</span></span>

<span data-ttu-id="f96af-109">`New-PSDrive`Cmdlet은 네트워크 드라이브, 로컬 컴퓨터의 디렉터리, 레지스트리 키, 원격 컴퓨터의 파일 시스템 위치에 연결 된 영구 Windows 매핑된 네트워크 드라이브와 같이 데이터 저장소의 위치에 매핑되고 연결 된 임시 및 영구 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-109">The `New-PSDrive` cmdlet creates temporary and persistent drives that are mapped to or associated with a location in a data store, such as a network drive, a directory on the local computer, or a registry key, and persistent Windows mapped network drives that are associated with a file system location on a remote computer.</span></span>

<span data-ttu-id="f96af-110">임시 드라이브는 현재 PowerShell 세션 및 현재 세션에서 만든 세션에만 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-110">Temporary drives exist only in the current PowerShell session and in sessions that you create in the current session.</span></span> <span data-ttu-id="f96af-111">PowerShell에서 유효한 임의의 이름을 가질 수 있으며 모든 로컬 또는 원격 리소스에 매핑될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-111">They can have any name that is valid in PowerShell and can be mapped to any local or remote resource.</span></span> <span data-ttu-id="f96af-112">매핑된 네트워크 드라이브와 마찬가지로 임시 PowerShell 드라이브를 사용 하 여 연결 된 데이터 저장소의 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-112">You can use temporary PowerShell drives to access data in the associated data store, just as you would do with any mapped network drive.</span></span> <span data-ttu-id="f96af-113">를 사용 하 여 드라이브에 위치를 변경 하 `Set-Location` 고 또는을 사용 하 여 드라이브의 내용에 액세스할 수 있습니다 `Get-Item` `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="f96af-113">You can change locations into the drive, by using `Set-Location`, and access the contents of the drive by using `Get-Item` or `Get-ChildItem`.</span></span>

<span data-ttu-id="f96af-114">임시 드라이브는 PowerShell에만 알려져 있으므로 파일 탐색기, WMI(Windows Management Instrumentation) (WMI), COM (구성 요소 개체 모델), Microsoft .NET 프레임 워크를 사용 하거나 **NET use** 와 같은 도구를 사용 하 여 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-114">Because temporary drives are known only to PowerShell, you can't access them by using File Explorer, Windows Management Instrumentation (WMI), Component Object Model (COM), Microsoft .NET Framework, or with tools such as **net use** .</span></span>

<span data-ttu-id="f96af-115">PowerShell 3.0에서에 추가 된 기능은 다음과 `New-PSDrive` 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-115">The following features were added to `New-PSDrive` in PowerShell 3.0:</span></span>

- <span data-ttu-id="f96af-116">매핑된 네트워크 드라이브</span><span class="sxs-lookup"><span data-stu-id="f96af-116">Mapped network drives.</span></span> <span data-ttu-id="f96af-117">의 **Persist** 매개 변수를 사용 `New-PSDrive` 하 여 Windows 매핑된 네트워크 드라이브를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-117">You can use the **Persist** parameter of `New-PSDrive` to create Windows mapped network drives.</span></span> <span data-ttu-id="f96af-118">임시 PowerShell 드라이브와 달리 Windows 매핑된 네트워크 드라이브는 특정 세션에 국한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-118">Unlike temporary PowerShell drives, Windows mapped network drives aren't session-specific.</span></span> <span data-ttu-id="f96af-119">이러한 파일은 Windows에 저장 되며 파일 탐색기 및 **net use** 와 같은 표준 windows 도구를 사용 하 여 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-119">They're saved in Windows and they can be managed by using standard Windows tools, such as File Explorer and **net use** .</span></span> <span data-ttu-id="f96af-120">매핑된 네트워크 드라이브는 드라이브 문자 이름을 가져야 하며 원격 파일 시스템 위치에 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-120">Mapped network drives must have a drive-letter name and be connected to a remote file system location.</span></span> <span data-ttu-id="f96af-121">명령의 범위가 로컬로 지정 되 고, 점 소싱이 없으면 **persist** 매개 변수는 명령이 실행 되는 범위를 벗어나 **PSDrive** 생성을 유지 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-121">When your command is scoped locally, no dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which the command is running.</span></span> <span data-ttu-id="f96af-122">`New-PSDrive`스크립트 내에서 실행 하는 경우 드라이브를 무기한으로 유지 하려면 스크립트를 점으로 원본으로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-122">If you're running `New-PSDrive` inside a script, and you want the drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="f96af-123">최상의 결과를 위해 새 드라이브를 무기한 유지 하려면 명령에 **Scope** 매개 변수를 추가 하 고 해당 값을 **Global** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-123">For best results, to force a new drive to persist indefinitely, add the **Scope** parameter to your command, and set its value to **Global** .</span></span> <span data-ttu-id="f96af-124">점 소싱에 대 한 자세한 내용은 [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f96af-124">For more information about dot-sourcing, see [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing).</span></span>
- <span data-ttu-id="f96af-125">외부 드라이브.</span><span class="sxs-lookup"><span data-stu-id="f96af-125">External drives.</span></span> <span data-ttu-id="f96af-126">외부 드라이브가 컴퓨터에 연결 되 면 PowerShell에서 자동으로 새 드라이브를 나타내는 **PSDrive** 를 파일 시스템에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-126">When an external drive is connected to the computer, PowerShell automatically adds a **PSDrive** to the file system that represents the new drive.</span></span> <span data-ttu-id="f96af-127">PowerShell을 다시 시작할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-127">You don't have to restart PowerShell.</span></span> <span data-ttu-id="f96af-128">마찬가지로 컴퓨터에서 외부 드라이브의 연결이 끊어지면 PowerShell에서 제거 된 드라이브를 나타내는 **PSDrive** 를 자동으로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-128">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the **PSDrive** that represents the removed drive.</span></span>
- <span data-ttu-id="f96af-129">UNC (범용 명명 규칙) 경로에 대 한 자격 증명</span><span class="sxs-lookup"><span data-stu-id="f96af-129">Credentials for Universal Naming Convention (UNC) paths.</span></span>

<span data-ttu-id="f96af-130">**Root** 매개 변수 값이 UNC 경로 (예:) 인 경우 `\\Server\Share` **credential** 매개 변수 값에 지정 된 자격 증명을 사용 하 여 **PSDrive** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-130">When the value of the **Root** parameter is a UNC path, such as `\\Server\Share`, the credential specified in the value of the **Credential** parameter is used to create the **PSDrive** .</span></span> <span data-ttu-id="f96af-131">그렇지 않으면 새 파일 시스템 드라이브를 만들 때 **자격 증명이** 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-131">Otherwise, **Credential** isn't effective when you're creating new file system drives.</span></span>

<span data-ttu-id="f96af-132">일부 코드 샘플에서는 스 플랫를 사용 하 여 줄 길이를 줄이고 가독성을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-132">Some code samples use splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="f96af-133">자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f96af-133">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="f96af-134">예제</span><span class="sxs-lookup"><span data-stu-id="f96af-134">EXAMPLES</span></span>

### <span data-ttu-id="f96af-135">예 1: 네트워크 공유에 매핑된 임시 드라이브 만들기</span><span class="sxs-lookup"><span data-stu-id="f96af-135">Example 1: Create a temporary drive mapped to a network share</span></span>

<span data-ttu-id="f96af-136">이 예제에서는 네트워크 공유에 매핑된 임시 PowerShell 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-136">This example creates a temporary PowerShell drive that's mapped to a network share.</span></span>

```powershell
New-PSDrive -Name "Public" -PSProvider "FileSystem" -Root "\\Server01\Public"
```

```Output
Name       Provider      Root
----       --------      ----
Public     FileSystem    \\Server01\Public
```

<span data-ttu-id="f96af-137">`New-PSDrive`**Name** 매개 변수를 사용 하 여 명명 된 powershell 드라이브를 지정 하 `Public` 고 **psprovider** 매개 변수를 사용 하 여 powershell 공급자를 지정 `FileSystem` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-137">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `Public` and the **PSProvider** parameter to specify the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="f96af-138">**Root** 매개 변수는 네트워크 공유의 UNC 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-138">The **Root** parameter specifies the network share's UNC path.</span></span>

<span data-ttu-id="f96af-139">PowerShell 세션에서 콘텐츠를 보려면 다음을 수행 합니다. `Get-ChildItem -Path Public:`</span><span class="sxs-lookup"><span data-stu-id="f96af-139">To view the contents from a PowerShell session: `Get-ChildItem -Path Public:`</span></span>

### <span data-ttu-id="f96af-140">예 2: 로컬 디렉터리에 매핑된 임시 드라이브 만들기</span><span class="sxs-lookup"><span data-stu-id="f96af-140">Example 2: Create a temporary drive mapped to a local directory</span></span>

<span data-ttu-id="f96af-141">이 예제에서는 로컬 컴퓨터의 디렉터리에 대 한 액세스를 제공 하는 임시 PowerShell 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-141">This example creates a temporary PowerShell drive that provides access to a directory on the local computer.</span></span>

```powershell
$parameters = @{
    Name = "MyDocs"
    PSProvider = "FileSystem"
    Root = "C:\Users\User01\Documents"
    Description = "Maps to my My Documents folder."
}
New-PSDrive @parameters
```

```Output
Name        Provider      Root
----        --------      ----
MyDocs      FileSystem    C:\Users\User01\Documents
```

<span data-ttu-id="f96af-142">스 플랫는 매개 변수 키 및 값을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-142">Splatting creates the parameter keys and values.</span></span> <span data-ttu-id="f96af-143">**Name** 매개 변수는 드라이브 이름 **mydocs** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-143">The **Name** parameter specifies the drive name, **MyDocs** .</span></span> <span data-ttu-id="f96af-144">**Psprovider** 매개 변수는 PowerShell 공급자를 지정 합니다 `FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="f96af-144">The **PSProvider** parameter specifies the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="f96af-145">**Root** 로컬 컴퓨터의 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-145">**Root** specifies the local computer's directory.</span></span> <span data-ttu-id="f96af-146">**Description** 매개 변수는 드라이브의 용도를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-146">The **Description** parameter describes the drive's purpose.</span></span> <span data-ttu-id="f96af-147">`New-PSDrive` splatted 매개 변수를 사용 하 여 `MyDocs` 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-147">`New-PSDrive` uses the splatted parameters to create the `MyDocs` drive.</span></span>

<span data-ttu-id="f96af-148">PowerShell 세션에서 콘텐츠를 보려면 다음을 수행 합니다. `Get-ChildItem -Path MyDocs:`</span><span class="sxs-lookup"><span data-stu-id="f96af-148">To view the contents from a PowerShell session: `Get-ChildItem -Path MyDocs:`</span></span>

### <span data-ttu-id="f96af-149">예 3: 레지스트리 키에 대 한 임시 드라이브 만들기</span><span class="sxs-lookup"><span data-stu-id="f96af-149">Example 3: Create a temporary drive for a registry key</span></span>

<span data-ttu-id="f96af-150">이 예제에서는 레지스트리 키에 대 한 액세스를 제공 하는 임시 PowerShell 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-150">This example creates a temporary PowerShell drive that provides access to a registry key.</span></span> <span data-ttu-id="f96af-151">레지스트리 키에 매핑되는 MyCompany 라는 드라이브를 만듭니다 `HKLM:\Software\MyCompany` .</span><span class="sxs-lookup"><span data-stu-id="f96af-151">It creates a drive named MyCompany that is mapped to the `HKLM:\Software\MyCompany` registry key.</span></span>

```powershell
New-PSDrive -Name "MyCompany" -PSProvider "Registry" -Root "HKLM:\Software\MyCompany"
```

```Output
Name           Provider      Root
----           --------      ----
MyCompany      Registry      HKLM:\Software\MyCompany
```

<span data-ttu-id="f96af-152">`New-PSDrive`**Name** 매개 변수를 사용 하 여 명명 된 powershell 드라이브를 지정 하 `MyCompany` 고 **psprovider** 매개 변수를 사용 하 여 powershell 공급자를 지정 `Registry` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-152">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `MyCompany` and the **PSProvider** parameter to specify the PowerShell `Registry` provider.</span></span> <span data-ttu-id="f96af-153">**Root** 매개 변수는 레지스트리 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-153">The **Root** parameter specifies the registry location.</span></span>

<span data-ttu-id="f96af-154">PowerShell 세션에서 콘텐츠를 보려면 다음을 수행 합니다. `Get-ChildItem -Path MyCompany:`</span><span class="sxs-lookup"><span data-stu-id="f96af-154">To view the contents from a PowerShell session: `Get-ChildItem -Path MyCompany:`</span></span>

### <span data-ttu-id="f96af-155">예제 4: 자격 증명을 사용 하 여 영구 매핑된 네트워크 드라이브 만들기</span><span class="sxs-lookup"><span data-stu-id="f96af-155">Example 4: Create a persistent mapped network drive using credentials</span></span>

<span data-ttu-id="f96af-156">이 예제에서는 도메인 서비스 계정의 자격 증명을 사용 하 여 인증 된 네트워크 드라이브를 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-156">This example maps a network drive that's authenticated with a domain service account's credentials.</span></span>
<span data-ttu-id="f96af-157">자격 증명을 저장 하는 **PSCredential** 개체 및 암호를 **SecureString** 으로 저장 하는 방법에 대 한 자세한 내용은 **Credential** 매개 변수의 설명을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f96af-157">For more information about the **PSCredential** object that stores credentials and how passwords are stored as a **SecureString** , see the **Credential** parameter's description.</span></span>

```powershell
$cred = Get-Credential -Credential Contoso\ServiceAccount
New-PSDrive -Name "S" -Root "\\Server01\Scripts" -Persist -PSProvider "FileSystem" -Credential $cred
Net Use
```

```Output
Status       Local     Remote                    Network
---------------------------------------------------------
OK           S:        \\Server01\Scripts        Microsoft Windows Network
```

> [!NOTE]
> <span data-ttu-id="f96af-158">스크립트에서 위의 코드 조각을 사용 하는 경우 **범위** 매개 변수 값을 "Global"로 설정 하 여 드라이브가 현재 범위를 벗어나 유지 되도록 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f96af-158">Remember, if you use the above snippet in a script, set the **Scope** parameter value to "Global" to ensure the drive persists outside the current scope.</span></span>

<span data-ttu-id="f96af-159">`$cred`변수는 서비스 계정의 자격 증명을 포함 하는 **PSCredential** 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-159">The `$cred` variable stores a **PSCredential** object that contains the service account's credentials.</span></span> <span data-ttu-id="f96af-160">`Get-Credential`**SecureString** 에 저장 된 암호를 입력 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-160">`Get-Credential` prompts you to enter the password that's stored in a **SecureString** .</span></span>

<span data-ttu-id="f96af-161">`New-PSDrive` 여러 매개 변수를 사용 하 여 매핑된 네트워크 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-161">`New-PSDrive` creates the mapped network drive by using several parameters.</span></span> <span data-ttu-id="f96af-162">**이름** Windows에서 `S` 허용 하는 드라이브 문자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-162">**Name** specifies the `S` drive letter that Windows accepts.</span></span> <span data-ttu-id="f96af-163">및 **Root** `\\Server01\Scripts` 는 원격 컴퓨터의 위치로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-163">and **Root** defines `\\Server01\Scripts` as the location on a remote computer.</span></span> <span data-ttu-id="f96af-164">**지속** 은 로컬 컴퓨터에 저장 되는 Windows 매핑된 네트워크 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-164">**Persist** creates a Windows mapped network drive that's saved on the local computer.</span></span> <span data-ttu-id="f96af-165">**Psprovider** 는 공급자를 지정 합니다 `FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="f96af-165">**PSProvider** specifies the `FileSystem` provider.</span></span> <span data-ttu-id="f96af-166">**자격 증명** 은 `$cred` 변수를 사용 하 여 인증을 위한 서비스 계정 자격 증명을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-166">**Credential** uses the `$cred` variable to get the service account credentials for authentication.</span></span>

<span data-ttu-id="f96af-167">매핑된 드라이브는 PowerShell 세션, 파일 탐색기 및 **net use** 와 같은 도구를 사용 하 여 로컬 컴퓨터에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-167">The mapped drive can be viewed on the local computer in PowerShell sessions, File Explorer, and with tools such as **net use** .</span></span> <span data-ttu-id="f96af-168">PowerShell 세션에서 콘텐츠를 보려면 다음을 수행 합니다. `Get-ChildItem -Path S:`</span><span class="sxs-lookup"><span data-stu-id="f96af-168">To view the contents from a PowerShell session: `Get-ChildItem -Path S:`</span></span>

### <span data-ttu-id="f96af-169">예 5: 영구 및 임시 드라이브 만들기</span><span class="sxs-lookup"><span data-stu-id="f96af-169">Example 5: Create persistent and temporary drives</span></span>

<span data-ttu-id="f96af-170">이 예제에서는 영구 매핑된 네트워크 드라이브와 동일한 네트워크 공유에 매핑된 임시 PowerShell 드라이브 간의 차이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-170">This example shows the difference between a persistent mapped network drive and a temporary PowerShell drive that is mapped to the same network share.</span></span>

<span data-ttu-id="f96af-171">PowerShell 세션을 닫은 다음 새 세션을 열면 임시를 `PSDrive:` 사용할 수 없지만 영구 `X:` 드라이브를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-171">If you close the PowerShell session and then open a new session, the temporary `PSDrive:` isn't available, but the persistent `X:` drive is available.</span></span> <span data-ttu-id="f96af-172">네트워크 드라이브를 매핑하는 데 사용할 방법을 결정 하는 경우 드라이브를 사용 하는 방법을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-172">When deciding which method to use to map network drives, consider how you'll use the drive.</span></span> <span data-ttu-id="f96af-173">예를 들어 영구적인 지 여부 및 드라이브를 다른 Windows 기능에 표시 해야 하는지 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-173">For example, whether it has to be persistent, and whether the drive has to be visible to other Windows features.</span></span>

```powershell
# Create a temporary PowerShell drive called PSDrive:
# that's mapped to the \\Server01\Public network share.
New-PSDrive -Name "PSDrive" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Use the Persist parameter of New-PSDrive to create the X: mapped network drive,
# which is also mapped to the \\Server01\Public network share.
New-PSDrive -Persist -Name "X" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Now, you can use the Get-PSDrive drive cmdlet to examine the two drives.
# The drives appear to be the same, although the network share name appears only
# in the root of the PSDrive: drive.
Get-PSDrive -Name "PSDrive", "X"
```

```Output
Name       Provider      Root
----       --------      ----

PsDrive    FileSystem    \\Server01\public
X          FileSystem    X:\
```

```powershell
# Get-Member cmdlet shows that the drives have the same object type,
# System.Management.Automation.PSDriveInfo.
Get-PSDrive "PSDrive", "x" | Get-Member
```

```Output
TypeName: System.Management.Automation.PSDriveInfo

Name                MemberType   Definition
----                ----------   ----------
CompareTo           Method       System.Int32 CompareTo(PSDriveInfo drive),
Equals              Method       System.Boolean Equals(Object obj),
GetHashCode         Method       System.Int32 GetHashCode()
...
```

```powershell
# Net Use and Get-CimInstance for the Win32_LogicalDisk class,
# and Win32_NetworkConnection class find only the persistent X: drive.
# PowerShell temporary drives are known only to PowerShell.
Net Use
Get-CimInstance Win32_LogicalDisk | Format-Table -Property DeviceID
Get-CimInstance Win32_NetworkConnection
```

```Output
Status       Local     Remote                    Network
--------------------------------------------------------
OK           X:        \\contoso-pc\data         Microsoft Windows Network

deviceid
--------
C:
D:
X:

LocalName    RemoteName              ConnectionState          Status
---------    ----------              ---------------          ------
X:           \\products\public       Disconnected             Unavailable
```

## <span data-ttu-id="f96af-174">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f96af-174">PARAMETERS</span></span>

### <span data-ttu-id="f96af-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f96af-175">-Confirm</span></span>

<span data-ttu-id="f96af-176">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-176">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f96af-177">-Credential</span><span class="sxs-lookup"><span data-stu-id="f96af-177">-Credential</span></span>

<span data-ttu-id="f96af-178">이 작업을 수행할 수 있는 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-178">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="f96af-179">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-179">The default is the current user.</span></span>

<span data-ttu-id="f96af-180">PowerShell 3.0부터 **Root** 매개 변수 값이 UNC 경로인 경우 자격 증명을 사용 하 여 파일 시스템 드라이브를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-180">Since PowerShell 3.0, when the value of the **Root** parameter is a UNC path, you can use credentials to create file system drives.</span></span>

<span data-ttu-id="f96af-181">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="f96af-181">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="f96af-182">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-182">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="f96af-183">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-183">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="f96af-184">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="f96af-184">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f96af-185">-Description</span><span class="sxs-lookup"><span data-stu-id="f96af-185">-Description</span></span>

<span data-ttu-id="f96af-186">드라이브에 대한 간단한 텍스트 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-186">Specifies a brief text description of the drive.</span></span> <span data-ttu-id="f96af-187">문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-187">Type any string.</span></span>

<span data-ttu-id="f96af-188">모든 세션 드라이브에 대 한 설명을 보려면를 참조 하십시오 `Get-PSDrive | Format-Table Name, Description` .</span><span class="sxs-lookup"><span data-stu-id="f96af-188">To see the descriptions of all the session's drives, `Get-PSDrive | Format-Table Name, Description`.</span></span>

<span data-ttu-id="f96af-189">특정 드라이브에 대 한 설명을 보려면을 입력 `(Get-PSDrive <DriveName>).Description` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-189">To see the description of a particular drive, type `(Get-PSDrive <DriveName>).Description`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f96af-190">-Name</span><span class="sxs-lookup"><span data-stu-id="f96af-190">-Name</span></span>

<span data-ttu-id="f96af-191">새 드라이브의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-191">Specifies a name for the new drive.</span></span> <span data-ttu-id="f96af-192">영구 매핑된 네트워크 드라이브의 경우 드라이브 문자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-192">For persistent mapped network drives, use a drive letter.</span></span> <span data-ttu-id="f96af-193">임시 PowerShell 드라이브의 경우 드라이브 문자로 제한 되지 않으며 유효한 문자열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-193">For temporary PowerShell drives, you aren't limited to drive letters, use any valid string.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f96af-194">-유지</span><span class="sxs-lookup"><span data-stu-id="f96af-194">-Persist</span></span>

<span data-ttu-id="f96af-195">이 cmdlet이 Windows 매핑된 네트워크 드라이브를 생성 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-195">Indicates that this cmdlet creates a Windows mapped network drive.</span></span> <span data-ttu-id="f96af-196">**Persist** 매개 변수는 Windows 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-196">The **Persist** parameter is only available on Windows.</span></span>

<span data-ttu-id="f96af-197">매핑된 네트워크 드라이브는 로컬 컴퓨터의 Windows에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-197">Mapped network drives are saved in Windows on the local computer.</span></span> <span data-ttu-id="f96af-198">이러한 파일은 세션에 한정 되지 않고 영구적 이며 파일 탐색기 및 기타 도구에서 보고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-198">They're persistent, not session-specific, and can be viewed and managed in File Explorer and other tools.</span></span>

<span data-ttu-id="f96af-199">점 소싱을 사용 하지 않고 로컬로 명령 범위를 설정한 경우 **persist** 매개 변수는 명령을 실행 하는 범위를 벗어나 **PSDrive** 생성을 유지 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-199">When you scope the command locally, without dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which you run the command.</span></span> <span data-ttu-id="f96af-200">`New-PSDrive`스크립트 내에서를 실행 하는 경우 새 드라이브를 무기한 유지 하려면 스크립트를 점으로 원본으로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-200">If you run `New-PSDrive` inside a script, and you want the new drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="f96af-201">최상의 결과를 위해 새 드라이브를 강제로 유지 하려면 **Scope** 매개 변수 값으로 **Global** 을 지정 하 고 명령에 **persist** 를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-201">For best results, to force a new drive to persist, specify **Global** as the value of the **Scope** parameter and include **Persist** in your command.</span></span>

<span data-ttu-id="f96af-202">드라이브의 이름은 문자 (예: 또는) 여야 합니다 `D` `E` .</span><span class="sxs-lookup"><span data-stu-id="f96af-202">The name of the drive must be a letter, such as `D` or `E`.</span></span> <span data-ttu-id="f96af-203">**Root** 매개 변수 값은 다른 컴퓨터의 UNC 경로 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-203">The value of **Root** parameter must be a UNC path of a different computer.</span></span> <span data-ttu-id="f96af-204">**Psprovider** 매개 변수의 값은 이어야 합니다 `FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="f96af-204">The **PSProvider** parameter's value must be `FileSystem`.</span></span>

<span data-ttu-id="f96af-205">Windows 매핑된 네트워크 드라이브의 연결을 끊으려면 cmdlet을 사용 `Remove-PSDrive` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-205">To disconnect a Windows mapped network drive, use the `Remove-PSDrive` cmdlet.</span></span> <span data-ttu-id="f96af-206">Windows 매핑된 네트워크 드라이브 연결을 끊으면 매핑이 현재 세션에서 삭제될 뿐만 아니라 컴퓨터에서도 영구적으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-206">When you disconnect a Windows mapped network drive, the mapping is permanently deleted from the computer, not just deleted from the current session.</span></span>

<span data-ttu-id="f96af-207">매핑된 네트워크 드라이브는 특정 사용자 계정에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-207">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="f96af-208">다른 사용자의 자격 증명을 사용 하 여 다른 사용자의 자격 증명을 사용 하는 세션에서 만든 매핑된 드라이브는 다른 자격 증명을 사용 하 여 시작 된 세션</span><span class="sxs-lookup"><span data-stu-id="f96af-208">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f96af-209">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="f96af-209">-PSProvider</span></span>

<span data-ttu-id="f96af-210">이러한 종류의 드라이브를 지 원하는 PowerShell 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-210">Specifies the PowerShell provider that supports drives of this kind.</span></span>

<span data-ttu-id="f96af-211">예를 들어 드라이브가 네트워크 공유 또는 파일 시스템 디렉터리와 연결 된 경우 PowerShell 공급자는 `FileSystem` 입니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-211">For example, if the drive is associated with a network share or file system directory, the PowerShell provider is `FileSystem`.</span></span> <span data-ttu-id="f96af-212">드라이브가 레지스트리 키와 연결 된 경우 공급자는 `Registry` 입니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-212">If the drive is associated with a registry key, the provider is `Registry`.</span></span>

<span data-ttu-id="f96af-213">임시 PowerShell 드라이브를 PowerShell 공급자와 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-213">Temporary PowerShell drives can be associated with any PowerShell provider.</span></span> <span data-ttu-id="f96af-214">매핑된 네트워크 드라이브는 공급자에만 연결할 수 있습니다 `FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="f96af-214">Mapped network drives can be associated only with the `FileSystem` provider.</span></span>

<span data-ttu-id="f96af-215">PowerShell 세션에서 공급자 목록을 보려면 cmdlet을 사용 합니다 `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="f96af-215">To see a list of the providers in your PowerShell session, use the `Get-PSProvider` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f96af-216">-루트</span><span class="sxs-lookup"><span data-stu-id="f96af-216">-Root</span></span>

<span data-ttu-id="f96af-217">PowerShell 드라이브가 매핑된 데이터 저장소 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-217">Specifies the data store location to which a PowerShell drive is mapped.</span></span>

<span data-ttu-id="f96af-218">예를 들어와 같은 네트워크 공유 또는와 같은 `\\Server01\Public` `C:\Program Files` 레지스트리 키를 지정 `HKLM:\Software\Microsoft` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-218">For example, specify a network share, such as `\\Server01\Public`, a local directory, such as `C:\Program Files`, or a registry key, such as `HKLM:\Software\Microsoft`.</span></span>

<span data-ttu-id="f96af-219">임시 PowerShell 드라이브는 지원 되는 모든 공급자 드라이브의 로컬 또는 원격 위치에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-219">Temporary PowerShell drives can be associated with a local or remote location on any supported provider drive.</span></span> <span data-ttu-id="f96af-220">매핑된 네트워크 드라이브는 원격 컴퓨터의 파일 시스템 위치에만 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-220">Mapped network drives can be associated only with a file system location on a remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f96af-221">-범위</span><span class="sxs-lookup"><span data-stu-id="f96af-221">-Scope</span></span>

<span data-ttu-id="f96af-222">드라이브의 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-222">Specifies a scope for the drive.</span></span> <span data-ttu-id="f96af-223">이 매개 변수에 허용 되는 값은 **전역** , **로컬** 및 **스크립트** 이거나 현재 범위를 기준으로 하는 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-223">The acceptable values for this parameter are: **Global** , **Local** , and **Script** , or a number relative to the current scope.</span></span> <span data-ttu-id="f96af-224">범위는 0에서 범위 수 까지입니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-224">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="f96af-225">현재 범위 번호는 0이 고 해당 부모는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-225">The current scope number is 0 and its parent is 1.</span></span> <span data-ttu-id="f96af-226">자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f96af-226">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f96af-227">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f96af-227">-WhatIf</span></span>

<span data-ttu-id="f96af-228">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-228">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f96af-229">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-229">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f96af-230">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f96af-230">CommonParameters</span></span>

<span data-ttu-id="f96af-231">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-231">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="f96af-232">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f96af-232">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f96af-233">입력</span><span class="sxs-lookup"><span data-stu-id="f96af-233">INPUTS</span></span>

### <span data-ttu-id="f96af-234">없음</span><span class="sxs-lookup"><span data-stu-id="f96af-234">None</span></span>

<span data-ttu-id="f96af-235">이 cmdlet에 대 한 입력을 파이프라인으로 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-235">You can't pipeline input to this cmdlet.</span></span>

## <span data-ttu-id="f96af-236">출력</span><span class="sxs-lookup"><span data-stu-id="f96af-236">OUTPUTS</span></span>

### <span data-ttu-id="f96af-237">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="f96af-237">System.Management.Automation.PSDriveInfo</span></span>

## <span data-ttu-id="f96af-238">참고</span><span class="sxs-lookup"><span data-stu-id="f96af-238">NOTES</span></span>

<span data-ttu-id="f96af-239">`New-PSDrive` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-239">`New-PSDrive` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="f96af-240">세션에서 사용할 수 있는 공급자를 나열 하려면를 사용 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-240">To list the providers available in your session, use `Get-PSProvider`.</span></span> <span data-ttu-id="f96af-241">공급자에 대 한 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f96af-241">For more information about providers, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="f96af-242">매핑된 네트워크 드라이브는 특정 사용자 계정에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f96af-242">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="f96af-243">다른 사용자의 자격 증명을 사용 하 여 다른 사용자의 자격 증명을 사용 하는 세션에서 만든 매핑된 드라이브는 다른 자격 증명을 사용 하 여 시작 된 세션</span><span class="sxs-lookup"><span data-stu-id="f96af-243">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

## <span data-ttu-id="f96af-244">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f96af-244">RELATED LINKS</span></span>

[<span data-ttu-id="f96af-245">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f96af-245">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="f96af-246">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="f96af-246">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="f96af-247">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="f96af-247">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="f96af-248">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="f96af-248">Remove-PSDrive</span></span>](Remove-PSDrive.md)


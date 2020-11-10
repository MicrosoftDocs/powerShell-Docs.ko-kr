---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/save-help?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Help
ms.openlocfilehash: 88d36c7e919e11be7b8c1568bd28f6badb789539
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391326"
---
# <span data-ttu-id="bb411-103">Save-Help</span><span class="sxs-lookup"><span data-stu-id="bb411-103">Save-Help</span></span>

## <span data-ttu-id="bb411-104">개요</span><span class="sxs-lookup"><span data-stu-id="bb411-104">SYNOPSIS</span></span>
<span data-ttu-id="bb411-105">최신 도움말 파일을 다운로드하여 파일 시스템 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-105">Downloads and saves the newest help files to a file system directory.</span></span>

## <span data-ttu-id="bb411-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bb411-106">SYNTAX</span></span>

### <span data-ttu-id="bb411-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="bb411-107">Path (Default)</span></span>

```
Save-Help [-DestinationPath] <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

### <span data-ttu-id="bb411-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="bb411-108">LiteralPath</span></span>

```
Save-Help -LiteralPath <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

## <span data-ttu-id="bb411-109">설명</span><span class="sxs-lookup"><span data-stu-id="bb411-109">DESCRIPTION</span></span>

<span data-ttu-id="bb411-110">`Save-Help`Cmdlet은 PowerShell 모듈에 대 한 최신 도움말 파일을 다운로드 하 여 지정한 디렉터리에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-110">The `Save-Help` cmdlet downloads the newest help files for PowerShell modules and saves them to a directory that you specify.</span></span> <span data-ttu-id="bb411-111">이 기능을 통해 인터넷에 액세스할 수 없는 컴퓨터에서 도움말 파일을 업데이트할 수 있으며, 여러 컴퓨터에서 도움말 파일을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-111">This feature lets you update the help files on computers that do not have access to the Internet, and makes it easier to update the help files on multiple computers.</span></span>

<span data-ttu-id="bb411-112">Windows PowerShell 3.0에서는 `Save-Help` 로컬 컴퓨터에 설치 된 모듈에 대해서만 작업을 수행 했습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-112">In Windows PowerShell 3.0, `Save-Help` worked only for modules that are installed on the local computer.</span></span> <span data-ttu-id="bb411-113">원격 컴퓨터에서 모듈을 가져올 수도 있지만 PowerShell 원격을 사용 하 여 원격 컴퓨터에서 **Psmoduleinfo** 개체에 대 한 참조를 가져올 수도 있지만, **HelpInfoUri** 속성은 유지 되지 않고 `Save-Help` 원격 모듈 도움말에 대해 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-113">Although it was possible to import a module from a remote computer, or obtain a reference to a **PSModuleInfo** object from a remote computer by using PowerShell remoting, the **HelpInfoUri** property was not preserved, and `Save-Help` would not work for remote module Help.</span></span>

<span data-ttu-id="bb411-114">Windows PowerShell 4.0에서 **HelpInfoUri** 속성은 PowerShell 원격 기능을 통해 유지 되며이를 통해 `Save-Help` 원격 컴퓨터에 설치 된 모듈에 대해 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-114">In Windows PowerShell 4.0, the **HelpInfoUri** property is preserved over PowerShell remoting, which enables `Save-Help` to work for modules that are installed on remote computers.</span></span> <span data-ttu-id="bb411-115">인터넷에 액세스할 수 없는 **PSModuleInfo** `Export-Clixml` 컴퓨터에서를 실행 하 고, 인터넷에 액세스할 수 있는 컴퓨터에서 개체를 가져온 다음 `Save-Help` **psmoduleinfo** 개체에서 실행 하 여 psmoduleinfo 개체를 디스크 또는 이동식 미디어에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-115">It is also possible to save a **PSModuleInfo** object to disk or removable media by running `Export-Clixml` on a computer that does not have Internet access, import the object on a computer that does have Internet access, and then run `Save-Help` on the **PSModuleInfo** object.</span></span> <span data-ttu-id="bb411-116">이동식 저장소 미디어 (예: USB 드라이브)를 사용 하 여 저장 된 도움말을 원격 컴퓨터로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-116">The saved help can be transported to the remote computer by using removable storage media, such as a USB drive.</span></span> <span data-ttu-id="bb411-117">을 실행 하 여 원격 컴퓨터에 도움말을 설치할 수 있습니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb411-117">The help can be installed on the remote computer by running `Update-Help`.</span></span> <span data-ttu-id="bb411-118">이 프로세스는 어떤 유형의 네트워크에도 액세스할 수 없는 컴퓨터에 도움말을 설치하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-118">This process can be used to install help on computers that do not have any kind of network access.</span></span>

<span data-ttu-id="bb411-119">저장 된 도움말 파일을 설치 하려면 cmdlet을 실행 `Update-Help` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-119">To install saved help files, run the `Update-Help` cmdlet.</span></span> <span data-ttu-id="bb411-120">**SourcePath** 매개 변수를 추가 하 여 도움말 파일을 저장 한 폴더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-120">Add its **SourcePath** parameter to specify the folder in which you saved the Help files.</span></span>

<span data-ttu-id="bb411-121">매개 변수가 없으면 `Save-Help` 명령은 세션의 모든 모듈에 대 한 최신 도움말과 **PSModulePath** 환경 변수에 나열 된 위치에 있는 컴퓨터에 설치 된 모듈을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-121">Without parameters, a `Save-Help` command downloads the newest help for all modules in the session and for modules that are installed on the computer in a location listed in the **PSModulePath** environment variable.</span></span> <span data-ttu-id="bb411-122">이 작업은 경고 없이 업데이트할 수 있는 도움말을 지원 하지 않는 모듈을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-122">This action skips modules that do not support Updatable Help without warning.</span></span>

<span data-ttu-id="bb411-123">`Save-Help`Cmdlet은 대상 폴더에 있는 도움말 파일의 버전을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-123">The `Save-Help` cmdlet checks the version of any help files in the destination folder.</span></span> <span data-ttu-id="bb411-124">최신 도움말 파일을 사용할 수 있는 경우이 cmdlet은 인터넷에서 최신 도움말 파일을 다운로드 한 다음 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-124">If newer help files are available, this cmdlet downloads the newest help files from the Internet, and then saves them in the folder.</span></span> <span data-ttu-id="bb411-125">Cmdlet은 cmdlet과 마찬가지로 `Save-Help` 작동 `Update-Help` 합니다. 단, 캐비닛 파일에서 도움말 파일을 추출 하 여 컴퓨터에 설치 하는 대신 다운로드 한 캐비닛 (.cab) 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-125">The `Save-Help` cmdlet works just like the `Update-Help` cmdlet, except that it saves the downloaded cabinet (.cab) files, instead of extracting the help files from the cabinet files and installing them on the computer.</span></span>

<span data-ttu-id="bb411-126">각 모듈에 대해 저장된 도움말은 도움말 정보(HelpInfo XML) 파일과 각 UI 문화권의 도움말 파일 캐비닛(.cab) 파일로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-126">The saved help for each module consists of one help information (HelpInfo XML) file and one cabinet (.cab) file for the help files each UI culture.</span></span> <span data-ttu-id="bb411-127">캐비닛 파일에서 도움말 파일을 추출할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-127">You do not have to extract the help files from the cabinet file.</span></span> <span data-ttu-id="bb411-128">`Update-Help`Cmdlet은 도움말 파일을 추출 하 고, 안전을 위해 XML의 유효성을 검사 한 다음, 모듈 폴더의 언어별 하위 폴더에 도움말 파일 및 도움말 정보 파일을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-128">The `Update-Help` cmdlet extracts the help files, validates the XML for safety, and then installs the help files and the help information file in a language-specific subfolder of the module folder.</span></span>

<span data-ttu-id="bb411-129">PowerShell 설치 폴더 ()에서 모듈에 대 한 도움말 파일을 저장 하려면 `$pshome\Modules` 관리자 권한으로 실행 옵션을 사용 하 여 powershell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-129">To save the help files for modules in the PowerShell installation folder (`$pshome\Modules`), start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="bb411-130">이러한 모듈에 대한 도움말 파일을 다운로드하려면 컴퓨터에서 Administrators 그룹의 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-130">You must be a member of the Administrators group on the computer to download the help files for these modules.</span></span>

<span data-ttu-id="bb411-131">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-131">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="bb411-132">예제</span><span class="sxs-lookup"><span data-stu-id="bb411-132">EXAMPLES</span></span>

### <span data-ttu-id="bb411-133">예제 1: DhcpServer 모듈에 대 한 도움말 저장</span><span class="sxs-lookup"><span data-stu-id="bb411-133">Example 1: Save the help for the DhcpServer module</span></span>

```powershell
# Option 1: Run Invoke-Command to get the PSModuleInfo object for the remote DHCP Server module,
# save the PSModuleInfo object in the variable $m, and then run Save-Help.

$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock { Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 2: Open a PSSession--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$s = New-PSSession -ComputerName "RemoteServer"
$m = Get-Module -PSSession $s -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 3: Open a CIM session--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$c = New-CimSession -ComputerName "RemoteServer"
$m = Get-Module -CimSession $c -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"
```

<span data-ttu-id="bb411-134">이 예에서는 `Save-Help` 로컬 컴퓨터에 **DhcpServer** 모듈 또는 DHCP 서버 역할을 설치 하지 않고 인터넷에 연결 된 클라이언트 컴퓨터에서 **DhcpServer** 모듈에 대 한 도움말을 저장 하는 데 사용 하는 세 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-134">This example shows three different ways to use `Save-Help` to save the help for the **DhcpServer** module from an Internet-connected client computer, without installing the **DhcpServer** module or the DHCP Server role on the local computer.</span></span>

### <span data-ttu-id="bb411-135">예 2: DhcpServer 모듈에 대 한 도움말 설치</span><span class="sxs-lookup"><span data-stu-id="bb411-135">Example 2: Install help for the DhcpServer module</span></span>

```powershell
# First, run Export-CliXml to export the PSModuleInfo object to a shared folder or to removable media.

$m = Get-Module -Name "DhcpServer" -ListAvailable
Export-CliXml -Path "E:\UsbFlashDrive\DhcpModule.xml" -InputObject $m

# Next, transport the removable media to a computer that has Internet access, and then import the
# PSModuleInfo object with Import-CliXml. Run Save-Help to save the Help for the imported DhcpServer
# module PSModuleInfo object.

$deserialized_m = Import-CliXml "E:\UsbFlashDrive\DhcpModule.xml"
Save-Help -Module $deserialized_m -DestinationPath "E:\UsbFlashDrive\SavedHelp"

# Finally, transport the removable media back to the computer that does not have network access, and
# then install the help by running Update-Help.

Update-Help -Module DhcpServer -SourcePath "E:\UsbFlashDrive\SavedHelp"
```

<span data-ttu-id="bb411-136">이 예제에서는 인터넷에 액세스할 수 없는 컴퓨터의 **DhcpServer** 모듈에 대해 예제 1에서 저장 한 도움말을 설치 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-136">This example shows how to install help that you saved in Example 1 for the **DhcpServer** module on a computer that does not have Internet access.</span></span>

### <span data-ttu-id="bb411-137">예 3: 모든 모듈에 대 한 도움말 저장</span><span class="sxs-lookup"><span data-stu-id="bb411-137">Example 3: Save help for all modules</span></span>

```powershell
Save-Help -DestinationPath "\\Server01\FileShare01"
```

<span data-ttu-id="bb411-138">이 명령은 로컬 컴퓨터에서 Windows용 UI 문화권 집합에 있는 모든 모듈에 대한 최신 도움말 파일을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-138">This command downloads the newest help files for all modules in the UI culture set for Windows on the local computer.</span></span> <span data-ttu-id="bb411-139">도움말 파일은 폴더에 저장 `\\Server01\Fileshare01` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-139">It saves the help files in the `\\Server01\Fileshare01` folder.</span></span>

### <span data-ttu-id="bb411-140">예 4: 컴퓨터의 모듈에 대 한 도움말 저장</span><span class="sxs-lookup"><span data-stu-id="bb411-140">Example 4: Save help for a module on the computer</span></span>

```powershell
Save-Help -Module ServerManager -DestinationPath "\\Server01\FileShare01" -Credential Domain01/Admin01
```

<span data-ttu-id="bb411-141">이 명령은 **ServerManager** 모듈에 대 한 최신 도움말 파일을 다운로드 한 다음 폴더에 저장 `\\Server01\Fileshare01` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-141">This command downloads the newest help files for the **ServerManager** module, and then saves them in the `\\Server01\Fileshare01` folder.</span></span>

<span data-ttu-id="bb411-142">모듈이 컴퓨터에 설치되면 모듈을 현재 세션으로 가져오지 않은 경우에도 **Module** 매개 변수 값으로 모듈 이름을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-142">When a module is installed on the computer, you can type the module name as the value of the **Module** parameter, even if the module is not imported into the current session.</span></span>

<span data-ttu-id="bb411-143">이 명령은 **Credential** 매개 변수를 사용하여 파일 공유에 쓸 수 있는 권한을 가진 사용자의 자격 증명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-143">The command uses the **Credential** parameter to supply the credentials of a user who has permission to write to the file share.</span></span>

### <span data-ttu-id="bb411-144">예 5: 다른 컴퓨터의 모듈에 대 한 도움말 저장</span><span class="sxs-lookup"><span data-stu-id="bb411-144">Example 5: Save help for a module on a different computer</span></span>

```powershell
Invoke-Command -ComputerName Server02 {Get-Module -Name CustomSQL -ListAvailable} | Save-Help -DestinationPath \\Server01\FileShare01 -Credential Domain01\Admin01
```

<span data-ttu-id="bb411-145">이러한 명령은 **Customsql** 모듈에 대 한 최신 도움말 파일을 다운로드 하 여 폴더에 저장 합니다 `\\Server01\Fileshare01` .</span><span class="sxs-lookup"><span data-stu-id="bb411-145">These commands download the newest help files for the **CustomSQL** module and save them in the `\\Server01\Fileshare01` folder.</span></span>

<span data-ttu-id="bb411-146">**Customsql** 모듈이 컴퓨터에 설치 되어 있지 않기 때문에 시퀀스에는 `Invoke-Command` Server02 컴퓨터에서 customsql 모듈에 대 한 module 개체를 가져온 다음 모듈 개체를 cmdlet으로 파이프 하는 명령이 포함 되어 있습니다 `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb411-146">Because the **CustomSQL** module is not installed on the computer, the sequence includes an `Invoke-Command` command that gets the module object for the CustomSQL module from the Server02 computer and then pipes the module object to the `Save-Help` cmdlet.</span></span>

<span data-ttu-id="bb411-147">컴퓨터에 모듈이 설치 되어 있지 않으면에서 `Save-Help` 최신 도움말 파일의 위치에 대 한 정보를 포함 하는 module 개체가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-147">When a module is not installed on the computer, `Save-Help` needs the module object, which includes information about the location of the newest help files.</span></span>

### <span data-ttu-id="bb411-148">예제 6: 여러 언어로 된 모듈에 대 한 도움말 저장</span><span class="sxs-lookup"><span data-stu-id="bb411-148">Example 6: Save help for a module in multiple languages</span></span>

```powershell
Save-Help -Module Microsoft.PowerShell* -UICulture de-DE, en-US, fr-FR, ja-JP -DestinationPath "D:\Help"
```

<span data-ttu-id="bb411-149">이 명령은 4 가지 UI 문화권의 PowerShell 핵심 모듈에 대 한 도움말을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-149">This command saves help for the PowerShell Core modules in four different UI cultures.</span></span> <span data-ttu-id="bb411-150">이러한 로캘의 언어 팩을 컴퓨터에 설치할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-150">The language packs for these locales do not have to be installed on the computer.</span></span>

<span data-ttu-id="bb411-151">`Save-Help` 는 모듈 소유자가 번역 된 파일을 인터넷에서 사용할 수 있도록 설정 하는 경우에만 다른 UI 문화권의 모듈에 대 한 도움말 파일을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-151">`Save-Help` can download help files for modules in different UI cultures only when the module owner makes the translated files available on the Internet.</span></span>

### <span data-ttu-id="bb411-152">예 7: 매일 한 번 이상 도움말 저장</span><span class="sxs-lookup"><span data-stu-id="bb411-152">Example 7: Save help more than one time each day</span></span>

```powershell
Save-Help -Force -DestinationPath "\\Server3\AdminShare\Help"
```

<span data-ttu-id="bb411-153">이 명령은 컴퓨터에 설치된 모든 모듈을 대한 도움말을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-153">This command saves help for all modules that are installed on the computer.</span></span> <span data-ttu-id="bb411-154">이 명령은 **Force** 매개 변수를 지정 하 여 `Save-Help` cmdlet이 24 시간 마다 두 번 이상 도움말을 다운로드 하지 못하도록 하는 규칙을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-154">The command specifies the **Force** parameter to override the rule that prevents the `Save-Help` cmdlet from downloading help more than once in each 24-hour period.</span></span>

<span data-ttu-id="bb411-155">**Force** 매개 변수도 1gb 제한과 우회 버전 검사를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-155">The **Force** parameter also overrides the 1 GB restriction and circumvents version checking.</span></span>
<span data-ttu-id="bb411-156">따라서 버전이 대상 폴더의 버전 보다 최신 버전이 아닌 경우에도 파일을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-156">Therefore, you can download files even if the version is not later than the version in the destination folder.</span></span>

<span data-ttu-id="bb411-157">이 명령은 cmdlet을 사용 하 여 `Save-Help` 도움말 파일을 다운로드 하 여 지정 된 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-157">The command uses the `Save-Help` cmdlet to download and save the help files to the specified folder.</span></span>
<span data-ttu-id="bb411-158">**Force** 매개 변수는 매일 여러 번 명령을 실행 해야 하는 경우에 필요 `Save-Help` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-158">The **Force** parameter is required when you have to run a `Save-Help` command more than one time each day.</span></span>

## <span data-ttu-id="bb411-159">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bb411-159">PARAMETERS</span></span>

### <span data-ttu-id="bb411-160">-Credential</span><span class="sxs-lookup"><span data-stu-id="bb411-160">-Credential</span></span>

<span data-ttu-id="bb411-161">사용자 자격 증명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-161">Specifies a user credential.</span></span> <span data-ttu-id="bb411-162">이 cmdlet은 **DestinationPath** 매개 변수로 지정 된 파일 시스템 위치에 액세스할 수 있는 권한이 있는 사용자의 자격 증명을 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-162">This cmdlet runs the command by using credentials of a user who has permission to access the file system location specified by the **DestinationPath** parameter.</span></span> <span data-ttu-id="bb411-163">이 매개 변수는 **DestinationPath** 또는 **LiteralPath** 매개 변수가 명령에 사용 되는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-163">This parameter is valid only when the **DestinationPath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="bb411-164">이 매개 변수를 사용 하면 `Save-Help` 원격 컴퓨터에서 **DestinationPath** 매개 변수를 사용 하는 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-164">This parameter enables you to run `Save-Help` commands that use the **DestinationPath** parameter on remote computers.</span></span> <span data-ttu-id="bb411-165">명시적 자격 증명을 제공 하 여 원격 컴퓨터에서 명령을 실행 하 고 액세스 거부 오류가 발생 하거나 CredSSP 인증을 사용 하 여 자격 증명을 위임 하지 않고도 세 번째 컴퓨터의 파일 공유에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-165">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="bb411-166">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="bb411-166">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="bb411-167">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-167">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="bb411-168">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-168">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="bb411-169">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="bb411-169">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb411-170">-DestinationPath</span><span class="sxs-lookup"><span data-stu-id="bb411-170">-DestinationPath</span></span>

<span data-ttu-id="bb411-171">도움말 파일이 저장 되는 폴더의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-171">Specifies the path of the folder in which the help files are saved.</span></span> <span data-ttu-id="bb411-172">파일 이름 또는 파일 이름 확장명은 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="bb411-172">Do not specify a file name or file name extension.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb411-173">-Force</span><span class="sxs-lookup"><span data-stu-id="bb411-173">-Force</span></span>

<span data-ttu-id="bb411-174">이 cmdlet은 하루에 한 번 제한을 따르지 않고 버전 검사를 건너뛰고 1gb 제한을 초과 하는 파일을 다운로드 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-174">Indicates that this cmdlet does not follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="bb411-175">이 매개 변수를 사용 하지 않으면 각 `Save-Help` 24 시간 동안 각 모듈에 대해 하나의 명령만 허용 되며, 다운로드는 모듈 당 1gb의 압축 되지 않은 콘텐츠로 제한 되며, 모듈에 대 한 도움말 파일은 컴퓨터의 파일 보다 최신 버전인 경우에만 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-175">Without this parameter, only one `Save-Help` command for each module is permitted in each 24-hour period, downloads are limited to 1 GB of uncompressed content per module, and help files for a module are installed only when they are newer than the files on the computer.</span></span>

<span data-ttu-id="bb411-176">매일 한 번 제한은 도움말 파일을 호스트 하는 서버를 보호 하 고 `Save-Help` PowerShell 프로필에 명령을 추가 하는 것이 실용적입니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-176">The once-per-day limit protects the servers that host the help files, and makes it practical for you to add a `Save-Help` command to your PowerShell profile.</span></span>

<span data-ttu-id="bb411-177">**Force** 매개 변수 없이 여러 ui 문화권의 모듈에 대 한 도움말을 저장 하려면 동일한 명령에 모든 ui 문화권을 포함 합니다 (예:).`Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`</span><span class="sxs-lookup"><span data-stu-id="bb411-177">To save help for a module in multiple UI cultures without the **Force** parameter, include all UI cultures in the same command, such as: `Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb411-178">-변수인 fullyqualifiedmodule</span><span class="sxs-lookup"><span data-stu-id="bb411-178">-FullyQualifiedModule</span></span>

<span data-ttu-id="bb411-179">**ModuleSpecification** 개체 형식으로 지정 된 이름을 사용 하 여 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-179">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span> <span data-ttu-id="bb411-180">[ModuleSpecification 생성자 (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)의 설명 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb411-180">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="bb411-181">예를 들어 **변수인 fullyqualifiedmodule** 매개 변수는 다음 형식 중 하나로 지정 된 모듈 이름을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-181">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="bb411-182">**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-182">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="bb411-183">**모듈** 매개 변수와 동일한 명령에 **변수인 fullyqualifiedmodule** 매개 변수를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-183">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="bb411-184">두 매개 변수는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-184">the two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bb411-185">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="bb411-185">-LiteralPath</span></span>

<span data-ttu-id="bb411-186">대상 폴더의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-186">Specifies a path of the destination folder.</span></span> <span data-ttu-id="bb411-187">**DestinationPath** 매개 변수 값과 달리 **LiteralPath** 매개 변수의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-187">Unlike the value of the **DestinationPath** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="bb411-188">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-188">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="bb411-189">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="bb411-189">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="bb411-190">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-190">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb411-191">-모듈</span><span class="sxs-lookup"><span data-stu-id="bb411-191">-Module</span></span>

<span data-ttu-id="bb411-192">이 cmdlet이 도움말을 다운로드 하는 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-192">Specifies modules for which this cmdlet downloads help.</span></span> <span data-ttu-id="bb411-193">하나 이상의 모듈 이름 또는 이름 패턴를 쉼표로 구분 된 목록 또는 각 줄에 하나의 모듈 이름이 있는 파일에 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-193">Enter one or more module names or name patters in a comma-separated list or in a file that has one module name on each line.</span></span> <span data-ttu-id="bb411-194">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="bb411-195">Cmdlet에서로 모듈 개체를 파이프 할 수도 있습니다 `Get-Module` `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb411-195">You can also pipe module objects from the `Get-Module` cmdlet to `Save-Help`.</span></span>

<span data-ttu-id="bb411-196">기본적으로는 `Save-Help` 업데이트할 수 있는 도움말을 지원 하 고 로컬 컴퓨터에 **PSModulePath** 환경 변수에 나열 된 위치에 설치 되어 있는 모든 모듈에 대 한 도움말을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-196">By default, `Save-Help` downloads help for all modules that support Updatable Help and are installed on the local computer in a location listed in the **PSModulePath** environment variable.</span></span>

<span data-ttu-id="bb411-197">컴퓨터에 설치 되지 않은 모듈에 대 한 도움말을 저장 하려면 `Get-Module` 원격 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-197">To save help for modules that are not installed on the computer, run a `Get-Module` command on a remote computer.</span></span> <span data-ttu-id="bb411-198">그런 다음 결과 모듈 개체를 cmdlet으로 파이프 `Save-Help` 하거나 모듈 개체를 **모듈** 또는 **InputObject** 매개 변수의 값으로 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-198">Then pipe the resulting module objects to the `Save-Help` cmdlet or submit the module objects as the value of the **Module** or **InputObject** parameters.</span></span>

<span data-ttu-id="bb411-199">지정한 모듈이 컴퓨터에 설치되어 있는 경우 모듈 이름 또는 모듈 개체를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-199">If the module that you specify is installed on the computer, you can enter the module name or a module object.</span></span> <span data-ttu-id="bb411-200">모듈이 컴퓨터에 설치 되어 있지 않은 경우 cmdlet에서 반환 된 것과 같은 모듈 개체를 입력 해야 합니다 `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="bb411-200">If the module is not installed on the computer, you must enter a module object, such as one returned by the `Get-Module` cmdlet.</span></span>

<span data-ttu-id="bb411-201">Cmdlet의 **module** 매개 변수는 `Save-Help` 모듈 파일 또는 모듈 매니페스트 파일의 전체 경로를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-201">The **Module** parameter of the `Save-Help` cmdlet does not accept the full path of a module file or module manifest file.</span></span> <span data-ttu-id="bb411-202">**PSModulePath** 위치에 없는 모듈에 대 한 도움말을 저장 하려면 명령을 실행 하기 전에 모듈을 현재 세션으로 가져옵니다 `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb411-202">To save help for a module that is not in a **PSModulePath** location, import the module into the current session before you run the `Save-Help` command.</span></span>

<span data-ttu-id="bb411-203">"\*" (모두)의 값은 컴퓨터에 설치 되어 있는 모든 모듈에 대 한 도움말을 업데이트 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-203">A value of "\*" (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="bb411-204">여기에는 업데이트할 수 있는 도움말을 지원 하지 않는 모듈도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-204">This includes modules that do not support Updatable Help.</span></span> <span data-ttu-id="bb411-205">이 값은 명령이 업데이트할 수 있는 도움말을 지원 하지 않는 모듈을 발견 하면 오류를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-205">This value might generate errors when the command encounters modules that do not support Updatable Help.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="bb411-206">-UICulture</span><span class="sxs-lookup"><span data-stu-id="bb411-206">-UICulture</span></span>

<span data-ttu-id="bb411-207">이 cmdlet이 업데이트 된 도움말 파일을 가져오는 UI 문화권 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-207">Specifies UI culture values for which this cmdlet gets updated help files.</span></span> <span data-ttu-id="bb411-208">등의 언어 코드를 하나 이상 입력 `es-ES` 합니다. 예를 들어, 문화권 개체를 포함 하는 변수 또는 문화권 개체를 가져오는 명령 (예: 또는 명령)을 입력 `Get-Culture` `Get-UICulture` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-208">Enter one or more language codes, such as `es-ES`, a variable that contains culture objects, or a command that gets culture objects, such as a `Get-Culture` or `Get-UICulture` command.</span></span>

<span data-ttu-id="bb411-209">와일드카드 문자는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-209">Wildcard characters are not permitted.</span></span> <span data-ttu-id="bb411-210">부분 언어 코드 (예: "de")를 지정 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="bb411-210">Do not specify a partial language code, such as "de".</span></span>

<span data-ttu-id="bb411-211">기본적으로는 `Save-Help` Windows 또는 대체 문화권에 대해 설정 된 UI 문화권의 도움말 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-211">By default, `Save-Help` gets help files in the UI culture set for Windows or its fallback culture.</span></span>
<span data-ttu-id="bb411-212">**UICulture** 매개 변수를 지정 하는 경우는 `Save-Help` 대체 문화권이 아니라 지정 된 UI 문화권에 대 한 도움말만 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-212">If you specify the **UICulture** parameter, `Save-Help` looks for help only for the specified UI culture, not in any fallback culture.</span></span>

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: Current UI culture
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb411-213">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="bb411-213">-UseDefaultCredentials</span></span>

<span data-ttu-id="bb411-214">이 cmdlet은 현재 사용자의 자격 증명을 사용 하 여 웹 다운로드를 포함 하 여 명령을 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-214">Indicates that this cmdlet runs the command, including the web download, with the credentials of the current user.</span></span> <span data-ttu-id="bb411-215">기본적으로 명령은 명시적 자격 증명 없이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-215">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="bb411-216">이 매개 변수는 웹 다운로드에서 NTLM, 협상 또는 kerberos 기반 인증을 사용하는 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-216">This parameter is effective only when the web download uses NTLM, negotiate, or Kerberos-based authentication.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb411-217">-범위</span><span class="sxs-lookup"><span data-stu-id="bb411-217">-Scope</span></span>

<span data-ttu-id="bb411-218">이 매개 변수는이 cmdlet에서 아무 작업도 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-218">This paramater does nothing in this cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bb411-219">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb411-219">CommonParameters</span></span>

<span data-ttu-id="bb411-220">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bb411-220">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bb411-221">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb411-221">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bb411-222">입력</span><span class="sxs-lookup"><span data-stu-id="bb411-222">INPUTS</span></span>

### <span data-ttu-id="bb411-223">System.object..</span><span class="sxs-lookup"><span data-stu-id="bb411-223">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="bb411-224">Cmdlet에서 모듈 매개 변수로 모듈 개체를 파이프 할 수 있습니다 `Get-Module` **Module** `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb411-224">You can pipe a module object from the `Get-Module` cmdlet to the **Module** parameter of `Save-Help`.</span></span>

## <span data-ttu-id="bb411-225">출력</span><span class="sxs-lookup"><span data-stu-id="bb411-225">OUTPUTS</span></span>

### <span data-ttu-id="bb411-226">없음</span><span class="sxs-lookup"><span data-stu-id="bb411-226">None</span></span>

<span data-ttu-id="bb411-227">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-227">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="bb411-228">참고</span><span class="sxs-lookup"><span data-stu-id="bb411-228">NOTES</span></span>

- <span data-ttu-id="bb411-229">모듈에 대 한 도움말을 $pshome \Modules 폴더에 저장 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-229">To save help for modules in the $pshome\Modules folder, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="bb411-230">컴퓨터의 Administrators 그룹 구성원만 $pshome \Modules 폴더의 모듈에 대 한 도움말을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-230">Only members of the Administrators group on the computer can download help for modules in the $pshome\Modules folder.</span></span>
- <span data-ttu-id="bb411-231">각 모듈에 대해 저장된 도움말은 도움말 정보(HelpInfo XML) 파일과 각 UI 문화권의 도움말 파일 캐비닛(.cab) 파일로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-231">The saved help for each module consists of one help information (HelpInfo XML) file and one cabinet (.cab) file for the help files each UI culture.</span></span> <span data-ttu-id="bb411-232">캐비닛 파일에서 도움말 파일을 추출할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-232">You do not have to extract the help files from the cabinet file.</span></span> <span data-ttu-id="bb411-233">`Update-Help`Cmdlet은 도움말 파일을 추출 하 고 XML의 유효성을 검사 한 다음 모듈 폴더의 언어별 하위 폴더에 도움말 파일 및 도움말 정보 파일을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-233">The `Update-Help` cmdlet extracts the help files, validates the XML, and then installs the help files and the help information file in a language-specific subfolder of the module folder.</span></span>
- <span data-ttu-id="bb411-234">`Save-Help`Cmdlet은 컴퓨터에 설치 되지 않은 모듈에 대 한 도움말을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-234">The `Save-Help` cmdlet can save help for modules that are not installed on the computer.</span></span> <span data-ttu-id="bb411-235">그러나 도움말 파일이 module 폴더에 설치 되기 때문에 `Update-Help` cmdlet은 컴퓨터에 설치 된 모듈에 대해서만 업데이트 된 도움말 파일을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-235">However, because help files are installed in the module folder, the `Update-Help` cmdlet can install updated help file only for modules that are installed on the computer.</span></span>
- <span data-ttu-id="bb411-236">에서 `Save-Help` 모듈에 대해 업데이트 된 도움말 파일을 찾을 수 없거나 지정 된 언어로 업데이트 된 도움말 파일을 찾을 수 없는 경우 오류 메시지를 표시 하지 않고 자동으로 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-236">If `Save-Help` cannot find updated help files for a module, or cannot find updated help files in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="bb411-237">명령으로 저장 된 파일을 보려면 **Verbose** 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-237">To see which files were saved by the command, specify the **Verbose** parameter.</span></span>
- <span data-ttu-id="bb411-238">모듈은 업데이트할 수 있는 도움말의 가장 작은 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-238">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="bb411-239">모듈의 모든 cmdlet에 대 한 특정 cmdlet에 대 한 도움말은 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-239">You cannot save help for a particular cmdlet, only for all cmdlets in module.</span></span> <span data-ttu-id="bb411-240">특정 cmdlet이 포함 된 모듈을 찾으려면 **ModuleName** 속성을 cmdlet과 함께 사용 합니다 ( `Get-Command` 예:). `(Get-Command \<cmdlet-name\>).ModuleName`</span><span class="sxs-lookup"><span data-stu-id="bb411-240">To find the module that contains a particular cmdlet, use the **ModuleName** property together with the `Get-Command` cmdlet, for example, `(Get-Command \<cmdlet-name\>).ModuleName`</span></span>
- <span data-ttu-id="bb411-241">`Save-Help` 모든 모듈과 PowerShell 핵심 스냅인을 지원 합니다. 다른 스냅인은 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-241">`Save-Help` supports all modules and the PowerShell Core snap-ins. It does not support any other snap-ins.</span></span>
- <span data-ttu-id="bb411-242">`Update-Help`및 `Save-Help` cmdlet은 다음 포트를 사용 하 여 도움말 파일을 다운로드 합니다. HTTP의 경우 포트 80, HTTPS의 경우 포트 443</span><span class="sxs-lookup"><span data-stu-id="bb411-242">The `Update-Help` and `Save-Help` cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>
- <span data-ttu-id="bb411-243">`Update-Help`및 `Save-Help` cmdlet은 Windows 사전 설치 환경 (Windows PE)에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb411-243">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="bb411-244">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bb411-244">RELATED LINKS</span></span>

[<span data-ttu-id="bb411-245">Get-Help</span><span class="sxs-lookup"><span data-stu-id="bb411-245">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="bb411-246">Get-Module</span><span class="sxs-lookup"><span data-stu-id="bb411-246">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="bb411-247">Update-Help</span><span class="sxs-lookup"><span data-stu-id="bb411-247">Update-Help</span></span>](Update-Help.md)

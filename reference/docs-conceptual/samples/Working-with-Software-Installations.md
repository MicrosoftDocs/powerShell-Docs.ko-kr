---
ms.date: 06/03/2019
keywords: powershell,cmdlet
title: 소프트웨어 설치 작업
ms.openlocfilehash: 6d2111a332f0e8c1b545186d3d950e936aed1834
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830297"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="f2dca-103">소프트웨어 설치 작업</span><span class="sxs-lookup"><span data-stu-id="f2dca-103">Working with Software Installations</span></span>

<span data-ttu-id="f2dca-104">Windows Installer를 사용하도록 설계된 애플리케이션은 WMI의 **Win32_Product** 클래스를 통해 액세스할 수 있지만, 현재 출시된 일부 애플리케이션에서는 Windows Installer를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="f2dca-105">대체 설치 루틴을 사용하는 애플리케이션은 일반적으로 Windows Installer에서 관리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-105">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="f2dca-106">이러한 애플리케이션으로 작업하기 위한 구체적인 기술은 설치 관리자 소프트웨어와 애플리케이션 개발자의 결정에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-106">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="f2dca-107">예를 들어, 파일을 폴더에 복사하여 컴퓨터에 설치하는 애플리케이션은 일반적으로 여기에 설명된 기술을 사용하여 관리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-107">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="f2dca-108">이러한 애플리케이션은 [파일 및 폴더 작업0](Working-with-Files-and-Folders.md) 섹션에 설명된 기술을 사용하여 파일 및 폴더로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-108">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="f2dca-109">**Win32_Product** 클래스는 최적화된 쿼리는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-109">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="f2dca-110">와일드카드 필터를 사용하는 쿼리로 인해 WMI는 MSI 공급자를 사용하여 설치된 모든 제품을 열거한 다음 전체 목록을 순차적으로 구문 분석하여 필터를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-110">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="f2dca-111">이렇게 하면 설치된 패키지의 일관성 검사, 설치 확인 및 복구도 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-111">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="f2dca-112">유효성 검사는 느린 프로세스이므로 이벤트 로그에 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-112">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="f2dca-113">자세한 내용은 기술 자료 문서 [기술 문서 974524](https://support.microsoft.com/help/974524)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f2dca-113">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="f2dca-114">Windows Installer 애플리케이션 나열</span><span class="sxs-lookup"><span data-stu-id="f2dca-114">Listing Windows Installer Applications</span></span>

<span data-ttu-id="f2dca-115">로컬 또는 원격 시스템에서 Windows Installer를 사용하여 설치한 애플리케이션을 나열하려면 다음과 같은 간단한 WMI 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-115">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

<span data-ttu-id="f2dca-116">모든 **Win32_Product** 개체의 속성을 디스플레이에 표시하려면 값이 `*`인 형식 지정 `Format-List`cmdlet의 **Properties** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-116">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.2 (x64)
Version               : 16.72.26629
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.2 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.2 (x64)
IdentifyingNumber     : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20180816
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\414c96e.msi
PackageCache          : C:\WINDOWS\Installer\414c96e.msi
PackageCode           : {D20AC783-1EC5-4A58-9277-F452F5EB9AD9}
PackageName           : dotnet-runtime-2.1.2-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

<span data-ttu-id="f2dca-117">또는 `Get-CimInstance` **Filter** 매개 변수를 사용하여 Microsoft .NET Framework 2.0만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-117">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="f2dca-118">**Filter** 매개 변수 값은 Windows PowerShell 구문이 아니라 WQL(WMI 쿼리 언어) 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-118">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="f2dca-119">예:</span><span class="sxs-lookup"><span data-stu-id="f2dca-119">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="f2dca-120">원하는 속성만 나열하려면 형식 지정 cmdlet의 **Property** 매개 변수를 사용하여 원하는 속성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-120">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.2 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\414c96e.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="f2dca-121">모든 제거 가능한 애플리케이션 나열</span><span class="sxs-lookup"><span data-stu-id="f2dca-121">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="f2dca-122">대부분의 표준 애플리케이션에서는 Windows에 제거 프로그램을 등록하므로 Windows 레지스트리에서 제거 프로그램을 찾아서 로컬로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-122">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="f2dca-123">시스템에서 모든 애플리케이션을 찾을 수 있는 확실한 방법은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-123">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="f2dca-124">그러나 **프로그램 추가 또는 제거**에 목록이 표시된 모든 프로그램을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-124">However, it is possible to find all programs with listings displayed in **Add or Remove Programs**.</span></span> <span data-ttu-id="f2dca-125">**프로그램 추가 또는 제거**에서는 다음 레지스트리 키에서 이러한 애플리케이션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-125">**Add or Remove Programs** finds these applications in the following registry key:</span></span>

<span data-ttu-id="f2dca-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="f2dca-127">이 키를 조사하여 애플리케이션을 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-127">We can examine this key to find applications.</span></span> <span data-ttu-id="f2dca-128">제거 키를 눈에 잘 띄게 하려면 Windows PowerShell 드라이브를 이 레지스트리 위치에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-128">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
<span data-ttu-id="f2dca-129">이제 "Uninstall" 드라이브를 사용하여 애플리케이션 설치를 빠르고 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-129">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="f2dca-130">Uninstall에서 레지스트리 키의 수를 계산하여 설치된 애플리케이션 수를 확인할 수 있습니다. PowerShell 드라이브:</span><span class="sxs-lookup"><span data-stu-id="f2dca-130">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```
(Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="f2dca-131">**Get-ChildItem**에서 시작하여 다양한 기술로 이 애플리케이션 목록을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-131">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="f2dca-132">애플리케이션 목록을 가져와서 **$UninstallableApplications** 변수에 저장하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-132">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="f2dca-133">Uninstall 아래에 레지스트리 키의 레지스트리 항목 값을 표시하려면 레지스트리 키의 GetValue 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-133">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="f2dca-134">메서드 값은 레지스트리 항목의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-134">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="f2dca-135">예를 들어 Uninstall 키에서 애플리케이션의 표시 이름을 찾으려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-135">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="f2dca-136">이러한 값이 고유하다는 보장은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-136">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="f2dca-137">다음 예에서는 두 개의 설치된 항목이 "Windows Media Encoder 9 Series"로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-137">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```powershell
$UninstallableApplications | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}
```

```Output
Name                           Property
----                           --------
{ACC73072-9AD5-416C-94BF-D82DD AuthorizedCDFPrefix :
CEA0F1B}                       Comments            :
                               Contact             :
                               DisplayVersion      : 16.72.26629
                               HelpLink            :
                               HelpTelephone       :
                               InstallDate         : 20180816
                               InstallLocation     :
                               InstallSource       : C:\ProgramData\Package
                               Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
                               ModifyPath          : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               NoModify            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 67156
                               SystemComponent     : 1
                               UninstallString     : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 16
                               VersionMinor        : 72
                               WindowsInstaller    : 1
                               Version             : 273180677
                               Language            : 1033
                               DisplayName         : Microsoft .NET Core Runtime - 2.1.2 (x64)
```

## <a name="installing-applications"></a><span data-ttu-id="f2dca-138">애플리케이션 설치</span><span class="sxs-lookup"><span data-stu-id="f2dca-138">Installing Applications</span></span>

<span data-ttu-id="f2dca-139">**Win32_Product** 클래스를 사용하여 Windows Installer 패키지를 원격 또는 로컬로 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-139">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="f2dca-140">애플리케이션을 설치하려면 "관리자로 실행" 옵션으로 PowerShell을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-140">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="f2dca-141">WMI 하위 시스템에서는 Windows PowerShell 경로를 이해하지 못하므로 원격으로 설치할 경우 UNC(범용 명명 규칙) 네트워크 경로를 사용하여 .msi 패키지의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-141">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="f2dca-142">예를 들어 네트워크 공유 `\\AppServ\dsp`에 있는 NewPackage.msi 패키지를 원격 컴퓨터 PC01에 설치하려면 PowerShell 프롬프트에 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-142">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="f2dca-143">Windows Installer 기술을 사용하지 않는 애플리케이션의 경우 애플리케이션별로 자동화된 배포 방법이 제공될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-143">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="f2dca-144">애플리케이션에 대한 설명서를 확인하거나 애플리케이션 공급업체의 지원 시스템에 문의합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-144">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="f2dca-145">애플리케이션 제거</span><span class="sxs-lookup"><span data-stu-id="f2dca-145">Removing Applications</span></span>

<span data-ttu-id="f2dca-146">PowerShell을 사용하여 Windows Installer 패키지를 제거하는 작업은 패키지를 설치하는 방법과 거의 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-146">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="f2dca-147">다음 예에서는 이름을 기반으로 제거할 패키지를 선택합니다. 경우에 따라 **IdentifyingNumber**를 사용하여 필터링하는 것이 더 쉬울 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-147">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="f2dca-148">로컬에서 수행하더라도 다른 애플리케이션을 제거하는 것은 그리 간단하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-148">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="f2dca-149">**UninstallString** 속성을 추출하여 이러한 애플리케이션에 대한 명령줄 제거 문자열을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-149">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="f2dca-150">이 방법은 Windows Installer 애플리케이션과 Uninstall 키 아래에 표시되는 이전 프로그램에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-150">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="f2dca-151">원하는 경우 표시 이름을 사용하여 출력을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-151">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="f2dca-152">하지만 이러한 문자열은 Windows PowerShell 프롬프트에서 수정 없이 직접 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-152">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="f2dca-153">Windows Installer 애플리케이션 업그레이드</span><span class="sxs-lookup"><span data-stu-id="f2dca-153">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="f2dca-154">애플리케이션을 업그레이드하려면 애플리케이션의 이름과 애플리케이션 업그레이드 패키지의 경로를 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-154">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="f2dca-155">해당 정보를 사용하여 단일 Windows PowerShell 명령으로 애플리케이션을 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dca-155">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```

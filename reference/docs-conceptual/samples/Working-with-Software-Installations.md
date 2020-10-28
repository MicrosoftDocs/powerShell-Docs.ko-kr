---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 소프트웨어 설치 작업
description: 이 문서에서는 WMI를 사용하여 Windows에 설치된 소프트웨어를 관리하는 방법을 보여줍니다.
ms.openlocfilehash: 3cf8e3c58e9f2814e2551b3602bd7b47b375aed8
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500881"
---
# <a name="working-with-software-installations"></a>소프트웨어 설치 작업

Windows Installer를 사용하도록 설계된 응용 프로그램은 WMI의 **Win32_Product** 클래스를 통해 액세스할 수 있지만, 현재 출시된 일부 응용 프로그램에서는 Windows Installer를 사용하지 않습니다.
대체 설치 루틴을 사용하는 애플리케이션은 일반적으로 Windows Installer에서 관리하지 않습니다.
이러한 애플리케이션으로 작업하기 위한 구체적인 기술은 설치 관리자 소프트웨어와 애플리케이션 개발자의 결정에 따라 다릅니다. 예를 들어, 파일을 폴더에 복사하여 컴퓨터에 설치하는 애플리케이션은 일반적으로 여기에 설명된 기술을 사용하여 관리할 수 없습니다. 이러한 애플리케이션은 [파일 및 폴더 작업0](Working-with-Files-and-Folders.md) 섹션에 설명된 기술을 사용하여 파일 및 폴더로 관리할 수 있습니다.

> [!CAUTION]
> **Win32_Product** 클래스는 최적화된 쿼리는 아닙니다. 와일드카드 필터를 사용하는 쿼리로 인해 WMI는 MSI 공급자를 사용하여 설치된 모든 제품을 열거한 다음 전체 목록을 순차적으로 구문 분석하여 필터를 처리합니다. 이렇게 하면 설치된 패키지의 일관성 검사, 설치 확인 및 복구도 시작됩니다. 유효성 검사는 느린 프로세스이므로 이벤트 로그에 오류가 발생할 수 있습니다. 자세한 내용은 기술 자료 문서 [기술 문서 974524](https://support.microsoft.com/help/974524)를 참조하세요.

## <a name="listing-windows-installer-applications"></a>Windows Installer 애플리케이션 나열

로컬 또는 원격 시스템에서 Windows Installer를 사용하여 설치한 애플리케이션을 나열하려면 다음과 같은 간단한 WMI 쿼리를 사용합니다.

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

모든 **Win32_Product** 개체의 속성을 디스플레이에 표시하려면 값이 `*`인 형식 지정 `Format-List`cmdlet의 **Properties** 매개 변수를 사용합니다.

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.5 (x64)
Version               : 16.84.26919
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.5 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.5 (x64)
IdentifyingNumber     : {BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20181105
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}v16.84.26919\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\4f97a771.msi
PackageCache          : C:\WINDOWS\Installer\4f97a771.msi
PackageCode           : {9A271A10-039D-49EA-8D24-043D91B9F915}
PackageName           : dotnet-runtime-2.1.5-win-x64.msi
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

또는 `Get-CimInstance` **Filter** 매개 변수를 사용하여 Microsoft .NET 2.0 Runtime만 선택할 수 있습니다. **Filter** 매개 변수 값은 Windows PowerShell 구문이 아니라 WQL(WMI 쿼리 언어) 구문을 사용합니다. 예를 들면 다음과 같습니다.

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

원하는 속성만 나열하려면 형식 지정 cmdlet의 **Property** 매개 변수를 사용하여 원하는 속성을 나열합니다.

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.5 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\4f97a771.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>모든 제거 가능한 애플리케이션 나열

대부분의 표준 애플리케이션에서는 Windows에 제거 프로그램을 등록하므로 Windows 레지스트리에서 제거 프로그램을 찾아서 로컬로 작업할 수 있습니다. 시스템에서 모든 애플리케이션을 찾을 수 있는 확실한 방법은 없습니다. 그러나 다음 레지스트리 키에서 **프로그램 추가 또는 제거** 에 목록이 표시된 모든 프로그램을 찾을 수 있습니다.

`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.

이 키를 조사하여 애플리케이션을 찾을 수도 있습니다. 제거 키를 눈에 잘 띄게 하려면 Windows PowerShell 드라이브를 이 레지스트리 위치에 매핑할 수 있습니다.

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

이제 "Uninstall" 드라이브를 사용하여 애플리케이션 설치를 빠르고 쉽게 찾을 수 있습니다. Uninstall에서 레지스트리 키의 수를 계산하여 설치된 애플리케이션 수를 확인할 수 있습니다. PowerShell 드라이브:

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

`Get-ChildItem`에서 시작하여 다양한 기술로 이 애플리케이션 목록을 검색할 수 있습니다. 애플리케이션 목록을 가져와서 `$UninstallableApplications` 변수에 저장하려면 다음 명령을 사용합니다.

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

Uninstall 아래에 레지스트리 키의 레지스트리 항목 값을 표시하려면 레지스트리 키의 GetValue 메서드를 사용합니다. 메서드 값은 레지스트리 항목의 이름입니다.

예를 들어 Uninstall 키에서 애플리케이션의 표시 이름을 찾으려면 다음 명령을 사용합니다.

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

이러한 값이 고유하다는 보장은 없습니다. 다음 예에서는 두 개의 설치된 항목이 "Windows Media Encoder 9 Series"로 표시됩니다.

```powershell
$UninstallableApplications | Where-Object -FilterScript {
  $_.GetValue("DisplayName") -eq "Microsoft Silverlight"
}
```

```Output
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name                           Property
----                           --------
{89F4137D-6C26-4A84-BDB8-2E5A4 AuthorizedCDFPrefix :
BB71E00}                       Comments            :
                               Contact             :
                               DisplayVersion      : 5.1.50918.0
                               HelpLink            : https://go.microsoft.com/fwlink/?LinkID=91955
                               HelpTelephone       :
                               InstallDate         : 20190115
                               InstallLocation     : C:\Program Files\Microsoft Silverlight\
                               InstallSource       : c:\ef64c54526db9c34cd477c103e68a254\
                               ModifyPath          : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               NoModify            : 1
                               NoRepair            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 236432
                               UninstallString     : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 5
                               VersionMinor        : 1
                               WindowsInstaller    : 1
                               Version             : 84002534
                               Language            : 1033
                               DisplayName         : Microsoft Silverlight
                               sEstimatedSize2     : 79214
```

## <a name="installing-applications"></a>애플리케이션 설치

**Win32_Product** 클래스를 사용하여 Windows Installer 패키지를 원격 또는 로컬로 설치할 수 있습니다.

> [!NOTE]
> 애플리케이션을 설치하려면 "관리자로 실행" 옵션으로 PowerShell을 시작해야 합니다.

WMI 하위 시스템에서는 Windows PowerShell 경로를 이해하지 못하므로 원격으로 설치할 경우 UNC(범용 명명 규칙) 네트워크 경로를 사용하여 .msi 패키지의 경로를 지정합니다. 예를 들어 네트워크 공유 `\\AppServ\dsp`에 있는 NewPackage.msi 패키지를 원격 컴퓨터 PC01에 설치하려면 PowerShell 프롬프트에 다음 명령을 입력합니다.

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

Windows Installer 기술을 사용하지 않는 애플리케이션의 경우 애플리케이션별로 자동화된 배포 방법이 제공될 수 있습니다. 애플리케이션에 대한 설명서를 확인하거나 애플리케이션 공급업체의 지원 시스템에 문의합니다.

## <a name="removing-applications"></a>애플리케이션 제거

PowerShell을 사용하여 Windows Installer 패키지를 제거하는 작업은 패키지를 설치하는 방법과 거의 동일합니다. 다음 예에서는 이름을 기반으로 제거할 패키지를 선택합니다. 경우에 따라 **IdentifyingNumber** 를 사용하여 필터링하는 것이 더 쉬울 수도 있습니다.

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

로컬에서 수행하더라도 다른 애플리케이션을 제거하는 것은 그리 간단하지 않습니다. **UninstallString** 속성을 추출하여 이러한 응용 프로그램에 대한 명령줄 제거 문자열을 찾을 수 있습니다.
이 방법은 Windows Installer 애플리케이션과 Uninstall 키 아래에 표시되는 이전 프로그램에 적용됩니다.

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

원하는 경우 표시 이름을 사용하여 출력을 필터링할 수 있습니다.

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

하지만 이러한 문자열은 Windows PowerShell 프롬프트에서 수정 없이 직접 사용할 수 없습니다.

## <a name="upgrading-windows-installer-applications"></a>Windows Installer 애플리케이션 업그레이드

애플리케이션을 업그레이드하려면 애플리케이션의 이름과 애플리케이션 업그레이드 패키지의 경로를 알고 있어야 합니다. 해당 정보를 사용하여 단일 Windows PowerShell 명령으로 애플리케이션을 업그레이드할 수 있습니다.

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```

---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 소프트웨어 설치 작업
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 9369e3c5ac670895cd4fbd3ebc895c50efd02051
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293234"
---
# <a name="working-with-software-installations"></a>소프트웨어 설치 작업

Windows Installer를 사용하도록 설계된 애플리케이션은 WMI의 **Win32_Product** 클래스를 통해 액세스할 수 있지만, 현재 출시된 일부 애플리케이션에서는 Windows Installer를 사용하지 않습니다. Windows Installer에서는 설치 가능한 애플리케이션으로 작업하는 데 가장 광범위한 표준 기술을 제공하므로, 여기서는 이러한 애플리케이션을 중심으로 살펴보겠습니다. 대체 설치 루틴을 사용하는 애플리케이션은 일반적으로 Windows Installer에서 관리하지 않습니다. 이러한 애플리케이션으로 작업하기 위한 구체적인 기술은 설치 관리자 소프트웨어와 애플리케이션 개발자의 결정에 따라 다릅니다.

> [!NOTE]
> 애플리케이션 파일을 컴퓨터에 복사하여 설치하는 애플리케이션은 일반적으로 여기에 설명된 기술을 사용하여 관리할 수 없습니다. 이러한 애플리케이션은 "파일 및 폴더 작업" 섹션에 설명된 기술을 사용하여 파일 및 폴더로 관리할 수 있습니다.

## <a name="listing-windows-installer-applications"></a>Windows Installer 애플리케이션 나열

로컬 또는 원격 시스템에서 Windows Installer를 사용하여 설치한 애플리케이션을 나열하려면 다음과 같은 간단한 WMI 쿼리를 사용합니다.

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

모든 Win32_Product 개체의 속성을 디스플레이에 표시하려면 값이 \*(모두)인 형식 지정 cmdlet(예: Format-List cmdlet)의 Properties 매개 변수를 사용합니다.

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

또는 **Get-WmiObject Filter** 매개 변수를 사용하여 Microsoft .NET Framework 2.0만 선택할 수 있습니다. 이 명령에 사용되는 필터는 WMI 필터이므로 Windows PowerShell 구문을 사용하지 않고 WQL(WMI Query Language) 구문을 사용합니다. 대신:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

WQL 쿼리에서는 Windows PowerShell에서는 특별한 의미를 갖는 공백, 등호(=) 등과 같은 문자를 자주 사용합니다. 따라서 필터 매개 변수 값을 물음표로 항상 묶는 것이 좋습니다. 가독성이 향상되지는 않지만 Windows PowerShell 이스케이프 문자인 억음 악센트 기호(\`)를 사용할 수도 있습니다. 다음 명령은 이전 명령과 동일하고 동일한 결과를 반환하지만 전체 필터 문자열을 따옴표로 묶는 대신 억음 기호를 사용하여 특수 문자를 이스케이프합니다.

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

원하는 속성만 나열하려면 형식 지정 cmdlet의 Property 매개 변수를 사용하여 원하는 속성을 나열합니다.

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

마지막으로 설치된 애플리케이션의 이름만 찾으려면 간단히 **Format-Wide** 문을 사용하여 출력을 간소화합니다.

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

설치를 위해 Windows Installer를 사용한 애플리케이션을 다양한 방법으로 찾을 수 있지만 다른 애플리케이션에 대해서는 고려하지 않습니다. 대부분의 표준 애플리케이션에서는 Windows에 제거 프로그램을 등록하므로 Windows 레지스트리에서 제거 프로그램을 찾아서 로컬로 작업할 수 있습니다.

## <a name="listing-all-uninstallable-applications"></a>모든 제거 가능한 애플리케이션 나열

시스템에서 모든 애플리케이션을 찾는 보장된 방법은 없지만 프로그램 추가/제거 대화 상자에 표시되는 목록을 사용하여 모든 프로그램을 찾을 수 있습니다. 프로그램 추가/제거에서는 다음 레지스트리 키에서 이러한 애플리케이션을 찾습니다.

**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.

이 키를 조사하여 애플리케이션을 찾을 수도 있습니다. 제거 키를 눈에 잘 띄게 하려면 Windows PowerShell 드라이브를 이 레지스트리 위치에 매핑할 수 있습니다.

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> **HKLM:** 드라이브는 **HKEY_LOCAL_MACHINE**의 루트에 매핑되므로 제거 키 경로에서 해당 드라이브를 사용했습니다. **HKLM:** 대신 **HKLM** 또는 **HKEY_LOCAL_MACHINE**을 사용하여 레지스트리 경로를 지정할 수도 있습니다. 기존 레지스트리 드라이브를 사용하면 탭 완성 기능을 사용하여 키 이름을 채울 수 있으므로 키 이름을 직접 입력할 필요가 없다는 이점이 있습니다.

이제 "Uninstall" 드라이브를 사용하여 애플리케이션 설치를 빠르고 쉽게 찾을 수 있습니다. Uninstall에서 레지스트리 키의 수를 계산하여 설치된 애플리케이션 수를 확인할 수 있습니다. Windows PowerShell 드라이브:

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

**Get-ChildItem**에서 시작하여 다양한 기술로 이 애플리케이션 목록을 검색할 수 있습니다. 애플리케이션 목록을 가져와서 **$UninstallableApplications** 변수에 저장하려면 다음 명령을 사용합니다.

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> 명확하게 하기 위해 여기서는 긴 변수 이름을 사용했습니다. 실제로는 긴 이름을 사용할 이유가 없습니다. 변수 이름에 대해 탭 완성 기능을 사용할 수 있지만 시간을 단축하기 위해 1-2자 이름을 사용할 수도 있습니다. 설명이 포함된 긴 이름은 다시 사용할 코드를 개발할 때 가장 유용합니다.

Uninstall 아래에 레지스트리 키의 레지스트리 항목 값을 표시하려면 레지스트리 키의 GetValue 메서드를 사용합니다. 메서드 값은 레지스트리 항목의 이름입니다.

예를 들어 Uninstall 키에서 애플리케이션의 표시 이름을 찾으려면 다음 명령을 사용합니다.

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

이러한 값이 고유하다는 보장은 없습니다. 다음 예에서는 두 개의 설치된 항목이 "Windows Media Encoder 9 Series"로 표시됩니다.

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

## <a name="installing-applications"></a>애플리케이션 설치

**Win32_Product** 클래스를 사용하여 Windows Installer 패키지를 원격 또는 로컬로 설치할 수 있습니다.

> [!NOTE]
> Windows Vista 및 Windows Server 2008 이상 버전에서 애플리케이션을 설치하려면 "관리자 권한으로 실행" 옵션을 사용하여 Windows PowerShell을 시작해야 합니다.

WMI 하위 시스템에서는 Windows PowerShell 경로를 이해하지 못하므로 원격으로 설치할 경우 UNC(범용 명명 규칙) 네트워크 경로를 사용하여 .msi 패키지의 경로를 지정합니다. 예를 들어 네트워크 공유 \\\\AppServ\\dsp에 있는 NewPackage.msi 패키지를 원격 컴퓨터 PC01에 설치하려면 Windows PowerShell 프롬프트에 다음 명령을 입력합니다.

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

Windows Installer 기술을 사용하지 않는 애플리케이션의 경우 애플리케이션별로 자동화된 배포 방법이 제공될 수 있습니다. 배포 자동화 방법이 있는지 확인하려면 애플리케이션의 설명서를 참조하거나 애플리케이션 공급업체의 지원 시스템에 문의하세요. 경우에 따라 애플리케이션 공급업체에서 설치 자동화를 위해 애플리케이션을 특별히 설계하지 않았더라도 설치 관리자 소프트웨어 제조업체에서 자동화 기술을 제공할 수도 있습니다.

## <a name="removing-applications"></a>애플리케이션 제거

Windows PowerShell을 사용하여 Windows Installer 패키지를 제거하는 작업은 패키지를 설치하는 방법과 거의 동일합니다. 다음 예에서는 이름을 기반으로 제거할 패키지를 선택합니다. 경우에 따라 **IdentifyingNumber**를 사용하여 필터링하는 것이 더 쉬울 수도 있습니다.

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

로컬에서 수행하더라도 다른 애플리케이션을 제거하는 것은 그리 간단하지 않습니다. **UninstallString** 속성을 추출하여 이러한 애플리케이션에 대한 명령줄 제거 문자열을 찾을 수 있습니다. 이 방법은 Windows Installer 애플리케이션과 Uninstall 키 아래에 표시되는 이전 프로그램에 적용됩니다.

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

원하는 경우 표시 이름을 사용하여 출력을 필터링할 수 있습니다.

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

하지만 이러한 문자열은 Windows PowerShell 프롬프트에서 수정 없이 직접 사용할 수 없습니다.

## <a name="upgrading-windows-installer-applications"></a>Windows Installer 애플리케이션 업그레이드

애플리케이션을 업그레이드하려면 애플리케이션의 이름과 애플리케이션 업그레이드 패키지의 경로를 알고 있어야 합니다. 해당 정보를 사용하여 단일 Windows PowerShell 명령으로 애플리케이션을 업그레이드할 수 있습니다.

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```
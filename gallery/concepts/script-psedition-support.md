---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: 호환되는 PowerShell 버전이 있는 스크립트
ms.openlocfilehash: e364879f611429a8583e550fb7704431e456fbb1
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655279"
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="83ca1-103">호환되는 PowerShell 버전이 있는 스크립트</span><span class="sxs-lookup"><span data-stu-id="83ca1-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="83ca1-104">버전 5.1부터 PowerShell은 다양한 기능 집합 및 플랫폼 호환성을 나타내는 다양한 버전으로 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="83ca1-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="83ca1-105">데스크톱 버전 .NET Framework를 기반으로 하며 스크립트 및 모듈의 전체 설치 공간 버전의 Server Core와 같은 Windows 및 Windows 데스크톱에서 실행 중인 PowerShell 버전을 대상으로 호환성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="83ca1-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>

- <span data-ttu-id="83ca1-106">**Core Edition:** .NET Core를 기반으로 하며 스크립트 및 Nano Server와 같은 Windows 및 Windows IoT의 축소 버전에서 실행 되는 powershell 버전을 대상으로 하는 모듈을 사용 하 여 호환성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="83ca1-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="83ca1-107">실행 중인 PowerShell의 에디션이 $PSVersionTable의 PSEdition 속성에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="83ca1-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="83ca1-108">스크립트 작성자는 `#requires` 문에 PSEdition 매개 변수를 사용하여 호환되는 PowerShell 버전에서 실행되지 않은 경우 스크립트가 실행되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83ca1-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a `#requires` statement.</span></span>

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="83ca1-109">PowerShell 갤러리 사용자는 특정 PowerShell 버전에서 지원되는 스크립트 목록을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83ca1-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="83ca1-110">PSEdition_Desktop 및 PSEdition_Core 태그가 없는 스크립트는 PowerShell Desktop 버전에서 제대로 작동하는 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="83ca1-110">Scripts without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop edition.</span></span>

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="83ca1-111">자세한 내용</span><span class="sxs-lookup"><span data-stu-id="83ca1-111">More details</span></span>

- [<span data-ttu-id="83ca1-112">PSEditions가 있는 모듈</span><span class="sxs-lookup"><span data-stu-id="83ca1-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="83ca1-113">PowerShellGallery의 PSEditions 지원</span><span class="sxs-lookup"><span data-stu-id="83ca1-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0a481fb9d4f2aab89bc448c71b01f1d541cf24bc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682388"
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="392e0-102">PowerShell 5.0 이상의 Side-by-Side 버전 지원</span><span class="sxs-lookup"><span data-stu-id="392e0-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="392e0-103">이제 Windows PowerShell 5.0 이상에서 실행되는 Install-Module, Update-Module 및 Publish-Module cmdlet에서 SxS(side-by-side) 모듈 버전이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="392e0-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="392e0-104">또한 게시할 버전을 지정하기 위해 Publish-Module cmdlet에 -RequiredVersion 매개 변수를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="392e0-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="392e0-105">이제 Path 매개 변수는 버전 폴더로 모듈 기본 경로를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="392e0-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="392e0-106">**Install-Module 예제:**</span><span class="sxs-lookup"><span data-stu-id="392e0-106">**Install-Module examples:**</span></span>
```powershell
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Get-InstalledModule -Name PSScriptAnalyzer -AllVersions

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```

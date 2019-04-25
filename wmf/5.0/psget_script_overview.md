---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3c1fcf94174b99490b19963662ef1ccdf6cebfec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085071"
---
# <a name="powershell-script-discovery-install-and-management-with-powershellget"></a><span data-ttu-id="6de43-102">PowerShellGet을 사용하여 PowerShell 스크립트 검색, 설치 및 관리</span><span class="sxs-lookup"><span data-stu-id="6de43-102">PowerShell Script Discovery, Install and Management with PowerShellGet</span></span>

<span data-ttu-id="6de43-103">WMF 5.0 RTM 릴리스에서는 PowerShell 스크립트 공유 기능이 PowerShellGet에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6de43-103">PowerShell Script sharing feature got added to the PowerShellGet in the WMF 5.0 RTM release.</span></span>
<span data-ttu-id="6de43-104">PowerShell 스크립트를 지원하기 위해 다음과 같은 새 cmdlet이 PowerShell 모듈에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="6de43-104">The following new cmdlets are added to the PowerShellGet module for supporting the PowerShell Scripts.</span></span>
```powershell
PS C:\\windows\\system32&gt; Get-Command \*script\* -Module PowerShellGet | Sort-Object -Property Noun, Verb
CommandType Name Version Source
----------- ---- ------- ------
Function Get-InstalledScript 1.0.0.1 PowerShellGet
Function Find-Script 1.0.0.1 PowerShellGet
Function Install-Script 1.0.0.1 PowerShellGet
Function Publish-Script 1.0.0.1 PowerShellGet
Function Save-Script 1.0.0.1 PowerShellGet
Function Uninstall-Script 1.0.0.1 PowerShellGet
Function Update-Script 1.0.0.1 PowerShellGet
Function New-ScriptFileInfo 1.0.0.1 PowerShellGet
Function Test-ScriptFileInfo 1.0.0.1 PowerShellGet
Function Update-ScriptFileInfo 1.0.0.1 PowerShellGet
-   **Find-Script** cmdlet lets you to discover the script files with different search criteria like name, tag, filter, command name, version range, exact version, all versions, including its dependencies and from specific or all registered repositories.
-   **Save-Script** cmdlet lets you to review the script file by saving it to a specified location.
-   **Install-Script** cmdlet lets you to install a specific script file along with its dependencies to the specified scope. By default, scripts are installed to the AllUsers scope.
-   **Update-Script** cmdlet lets you to do in-place update of the script files which were installed using Install-Script cmdlet.
-   **Get-InstalledScript** cmdlet lets you to get the list of script files which were installed using Install-Script cmdlet.
-   **Uninstall-Script** cmdlet lets you to uninstall the installed script files.
-   **Publish-Script** cmdlet lets you to publish your script file with valid metadata like Version, Guid, Author, and Description, etc.
-   **New-ScriptFileInfo** cmdlet lets you to create a new script file with metadata like Version, Guid, Author, and Description, etc.
-   **Update-ScriptFileInfo** cmdlet lets you to update the existing script file metadata.
-   **Test-ScriptFileInfo** cmdlet lets you to validate and get the script file metadata.
```

<span data-ttu-id="6de43-105">스크립트 공유 Cmdlet의 구문:</span><span class="sxs-lookup"><span data-stu-id="6de43-105">Syntax of script sharing Cmdlets:</span></span>
```powershell
**New-ScriptFileInfo** \[-Path\] &lt;string&gt; -Description &lt;string&gt; \[-Version &lt;version&gt;\] \[-Author &lt;string&gt;\] \[-Guid &lt;guid&gt;\] \[-CompanyName &lt;string&gt;\] \[-Copyright &lt;string&gt;\] \[-RequiredModules &lt;Object\[\]&gt;\] \[-ExternalModuleDependencies &lt;string\[\]&gt;\] \[-RequiredScripts &lt;string\[\]&gt;\] \[-ExternalScriptDependencies &lt;string\[\]&gt;\] \[-Tags &lt;string\[\]&gt;\] \[-ProjectUri &lt;uri&gt;\] \[-LicenseUri &lt;uri&gt;\] \[-IconUri &lt;uri&gt;\] \[-ReleaseNotes &lt;string\[\]&gt;\] \[-PassThru\] \[-Force\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

**Test-ScriptFileInfo** \[-Path\] &lt;string&gt; \[&lt;CommonParameters&gt;\]

**Test-ScriptFileInfo** -LiteralPath &lt;string&gt; \[&lt;CommonParameters&gt;\]

**Update-ScriptFileInfo** \[-Path\] &lt;string&gt; \[-Version &lt;version&gt;\] \[-Author &lt;string&gt;\] \[-Guid &lt;guid&gt;\] \[-Description &lt;string&gt;\] \[-CompanyName &lt;string&gt;\] \[-Copyright &lt;string&gt;\] \[-RequiredModules &lt;Object\[\]&gt;\] \[-ExternalModuleDependencies &lt;string\[\]&gt;\] \[-RequiredScripts &lt;string\[\]&gt;\] \[-ExternalScriptDependencies &lt;string\[\]&gt;\] \[-Tags &lt;string\[\]&gt;\] \[-ProjectUri &lt;uri&gt;\] \[-LicenseUri &lt;uri&gt;\] \[-IconUri &lt;uri&gt;\] \[-ReleaseNotes &lt;string\[\]&gt;\] \[-PassThru\] \[-Force\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

**Update-ScriptFileInfo** \[-LiteralPath\] &lt;string&gt; \[-Version &lt;version&gt;\] \[-Author &lt;string&gt;\] \[-Guid &lt;guid&gt;\] \[-Description &lt;string&gt;\] \[-CompanyName &lt;string&gt;\] \[-Copyright &lt;string&gt;\] \[-RequiredModules &lt;Object\[\]&gt;\] \[-ExternalModuleDependencies &lt;string\[\]&gt;\] \[-RequiredScripts &lt;string\[\]&gt;\] \[-ExternalScriptDependencies &lt;string\[\]&gt;\] \[-Tags &lt;string\[\]&gt;\] \[-ProjectUri &lt;uri&gt;\] \[-LicenseUri &lt;uri&gt;\] \[-IconUri &lt;uri&gt;\] \[-ReleaseNotes &lt;string\[\]&gt;\] \[-PassThru\] \[-Force\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

**Find-Script** \[\[-Name\] &lt;string\[\]&gt;\] \[-MinimumVersion &lt;version&gt;\] \[-MaximumVersion &lt;version&gt;\] \[-RequiredVersion &lt;version&gt;\] \[-AllVersions\] \[-IncludeDependencies\] \[-Filter &lt;string&gt;\] \[-Tag &lt;string\[\]&gt;\] \[-Includes &lt;string\[\]&gt;\] \[-Command &lt;string\[\]&gt;\] \[-Repository &lt;string\[\]&gt;\] \[&lt;CommonParameters&gt;\]

**Install-Script** \[-Name\] &lt;string\[\]&gt; \[-MinimumVersion &lt;version&gt;\] \[-MaximumVersion &lt;version&gt;\] \[-RequiredVersion &lt;version&gt;\] \[-Repository &lt;string\[\]&gt;\] \[-Scope &lt;string&gt;\] \[-Force\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

**Install-Script** \[-InputObject\] &lt;psobject\[\]&gt; \[-Scope &lt;string&gt;\] \[-Force\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

**Update-Script** \[\[-Name\] &lt;string\[\]&gt;\] \[-RequiredVersion &lt;version&gt;\] \[-MaximumVersion &lt;version&gt;\] \[-Force\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

**Get-InstalledScript** \[\[-Name\] &lt;string\[\]&gt;\] \[-MinimumVersion &lt;version&gt;\] \[-RequiredVersion &lt;version&gt;\] \[-MaximumVersion &lt;version&gt;\] \[&lt;CommonParameters&gt;\]

**Uninstall-Script** \[-Name\] &lt;string\[\]&gt; \[-MinimumVersion &lt;version&gt;\] \[-RequiredVersion &lt;version&gt;\] \[-MaximumVersion &lt;version&gt;\] \[-Force\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

**Uninstall-Script** \[-InputObject\] &lt;psobject\[\]&gt; \[-Force\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

**Save-Script** \[-Name\] &lt;string\[\]&gt; -Path &lt;string&gt; \[-MinimumVersion &lt;version&gt;\] \[-MaximumVersion &lt;version&gt;\] \[-RequiredVersion &lt;version&gt;\] \[-Repository &lt;string\[\]&gt;\] \[-Force\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

**Save-Script** \[-Name\] &lt;string\[\]&gt; -LiteralPath &lt;string&gt; \[-MinimumVersion &lt;version&gt;\] \[-MaximumVersion &lt;version&gt;\] \[-RequiredVersion &lt;version&gt;\] \[-Repository &lt;string\[\]&gt;\] \[-Force\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

**Save-Script** \[-InputObject\] &lt;psobject\[\]&gt; -LiteralPath &lt;string&gt; \[-Force\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

**Save-Script** \[-InputObject\] &lt;psobject\[\]&gt; -Path &lt;string&gt; \[-Force\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

**Publish-Script** -Path &lt;string&gt; \[-NuGetApiKey &lt;string&gt;\] \[-Repository &lt;string&gt;\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

**Publish-Script** -LiteralPath &lt;string&gt; \[-NuGetApiKey &lt;string&gt;\] \[-Repository &lt;string&gt;\] \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]
```

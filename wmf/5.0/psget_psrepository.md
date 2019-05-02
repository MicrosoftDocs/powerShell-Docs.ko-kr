---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5ac9566979e1b761249f5cc7c62ed44047a2b9f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058015"
---
# <a name="register-a-powershell-repository"></a>PowerShell 리포지토리 등록
내부 리포지토리에 대해 작동하도록 PowerShellGet을 구성할 수 있습니다. 이렇게 구성하려면 다음과 같은 추가 기능을 사용합니다.
- Register-PSRepository: 현재 사용자에 대해 리포지토리를 등록합니다.
- Unregister-PSRepository: 현재 사용자에 대해 등록된 리포지토리를 제거합니다.
- Set-PSRepository: 등록된 리포지토리에 대해 값을 설정합니다.
- Get-PSRepository: 현재 사용자에 대해 등록된 리포지토리를 모두 가져옵니다.

리포지토리를 등록한 후에는 Find-Module 및 Install-Module을 사용하여 작업할 수 있습니다.

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```

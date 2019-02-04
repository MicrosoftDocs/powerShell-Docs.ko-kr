---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cd3338ae305896e282056a871974e5f899ef6ff5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681138"
---
# <a name="reporting-on-jea"></a><span data-ttu-id="bf036-102">JEA에 대한 보고</span><span class="sxs-lookup"><span data-stu-id="bf036-102">Reporting on JEA</span></span>

<span data-ttu-id="bf036-103">JEA 구성의 상태를 보고하려면 다음을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf036-103">In order to report on the state of your JEA configuration, you can use:</span></span>

1. <span data-ttu-id="bf036-104">**Get-PSSessionConfiguration** - 지정된 컴퓨터에서 등록된 모든 엔드포인트 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bf036-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2. <span data-ttu-id="bf036-105">**Get-PSSessionCapability** - 특정 엔드포인트에 대해 지정된 사용자에게 제공되는 기능을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="bf036-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="bf036-106">다음은 **Get-PSSessionCapability**의 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="bf036-106">Here's an example of **Get-PSSessionCapability**:</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           clear -> Clear-Host
Alias           cls -> Clear-Host
Alias           exsn -> Exit-PSSession
Alias           gcm -> Get-Command
Alias           measure -> Measure-Object
Alias           select -> Select-Object
Function        Clear-Host
Function        Exit-PSSession
Function        Get-Command
Function        Get-FormatData
Function        Get-Help
Function        Get-UserInfo
Function        Measure-Object
Function        Out-Default
Function        Select-Object
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...
```

<span data-ttu-id="bf036-107">JEA 세션 중 사용자가 수행한 _작업_을 보고하려면 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf036-107">To report on the _actions_ users took during a JEA session, you can:</span></span>

1. <span data-ttu-id="bf036-108">해당 JEA 엔드포인트에 대해 “자격 증명 입력” 기록을 사용하고 기록 디렉터리에서 각 사용자의 작업에 대한 전체 로그를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="bf036-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="bf036-109">PowerShell 모듈 로깅을 켜고 PowerShell 이벤트 로그를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="bf036-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>
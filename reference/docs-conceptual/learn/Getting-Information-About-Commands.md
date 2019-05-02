---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 명령에 대한 정보 가져오기
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 7af83e3a0e776d96e580b442430357b4ea063a72
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057709"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="3d290-103">명령에 대한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="3d290-103">Getting information about commands</span></span>

<span data-ttu-id="3d290-104">PowerShell `Get-Command`는 현재 세션에서 사용할 수 있는 모든 명령을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="3d290-105">`Get-Command` cmdlet을 실행하면 다음 출력과 유사한 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

<span data-ttu-id="3d290-106">이 출력은 내부 명령을 표 형식으로 요약하는 **cmd.exe**의 도움말 출력과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-106">This output looks a lot like the Help output of **cmd.exe**: a tabular summary of internal commands.</span></span> <span data-ttu-id="3d290-107">위에 표시된 `Get-Command` 명령 출력의 발췌 부분에서 표시되는 모든 명령의 CommandType은 Cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="3d290-108">cmdlet은 PowerShell의 내장 명령 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="3d290-109">이 형식은 **cmd.exe**의 `dir` 및 `cd`와 같은 명령이나 Unix 셸(예: bash)의 기본 제공 명령과 거의 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-109">This type corresponds roughly to commands like `dir` and `cd` in **cmd.exe** or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="3d290-110">`Get-Command` cmdlet에는 각 cmdlet의 구문을 반환하는 **Syntax** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="3d290-111">다음 예제에서는 `Get-Help` cmdlet의 구문을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="3d290-112">유형별로 사용 가능한 명령 표시</span><span class="sxs-lookup"><span data-stu-id="3d290-112">Displaying available command by type</span></span>

<span data-ttu-id="3d290-113">`Get-Command`명령은 현재 세션에 있는 cmdlet만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="3d290-114">PowerShell에서는 실제로 다양한 유형의 명령을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="3d290-115">별칭</span><span class="sxs-lookup"><span data-stu-id="3d290-115">Aliases</span></span>
- <span data-ttu-id="3d290-116">함수</span><span class="sxs-lookup"><span data-stu-id="3d290-116">Functions</span></span>
- <span data-ttu-id="3d290-117">스크립트</span><span class="sxs-lookup"><span data-stu-id="3d290-117">Scripts</span></span>

<span data-ttu-id="3d290-118">외부 실행 파일 또는 등록된 파일 형식 처리기가 있는 파일도 명령으로 분류됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="3d290-119">세션의 모든 명령을 가져오려면 다음과 같이 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="3d290-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="3d290-120">이 목록에는 검색 경로에 있는 외부 명령이 포함되므로 수천 개의 항목이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="3d290-121">찾을 명령의 수를 줄이는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="3d290-122">별표(\*)는 PowerShell 명령 인수에서 와일드카드 일치에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="3d290-123">\*는 "하나 이상의 문자 일치"를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="3d290-124">`Get-Command a*`를 입력하여 문자 "a"로 시작하는 모든 명령을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="3d290-125">**cmd.exe**의 와일드카드 일치와 달리 PowerShell의 와일드카드는 점(.)도 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-125">Unlike wildcard matching in **cmd.exe**, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="3d290-126">다른 형식의 네이티브 명령을 가져오려면 `Get-Command`의 **CommandType** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d290-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="3d290-127">cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3d290-127">cmdlet.</span></span>

<span data-ttu-id="3d290-128">명령에 할당된 애칭인 명령 별칭을 가져오려면 다음과 같이 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="3d290-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="3d290-129">현재 세션의 함수를 가져오려면 다음과 같이 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="3d290-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="3d290-130">PowerShell의 검색 경로에 스크립트를 표시하려면 다음과 같이 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="3d290-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```
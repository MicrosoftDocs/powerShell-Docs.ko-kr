---
ms.date: 08/23/2018
keywords: powershell,cmdlet
title: PowerShell 파이프라인 이해
ms.openlocfilehash: 3033a4fe1a704fbbfa76e6d38662c8b22c3dbd9b
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030382"
---
# <a name="understanding-pipelines"></a><span data-ttu-id="03f7c-103">파이프라인 이해</span><span class="sxs-lookup"><span data-stu-id="03f7c-103">Understanding pipelines</span></span>

<span data-ttu-id="03f7c-104">파이프라인은 일련의 파이프 세그먼트가 연결된 것처럼 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="03f7c-105">파이프라인을 따라 이동하는 항목은 각 세그먼트를 통과합니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="03f7c-106">PowerShell에서 파이프라인을 만들려면 여러 명령을 파이프 연산자 "|"로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-106">To create a pipeline in PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="03f7c-107">그러면 각 명령의 출력이 그 다음 명령의 입력으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="03f7c-108">파이프라인에 사용되는 표기법은 다른 셸에 사용되는 표기법과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-108">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="03f7c-109">얼핏 보면 파이프라인이 PowerShell과 어떻게 다른지 명확하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-109">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="03f7c-110">화면에 텍스트가 표시되어 있는 경우에도 PowerShell은 명령 사이에 있는 텍스트가 아닌 개체를 파이프합니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-110">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

## <a name="the-powershell-pipeline"></a><span data-ttu-id="03f7c-111">PowerShell 파이프라인</span><span class="sxs-lookup"><span data-stu-id="03f7c-111">The PowerShell pipeline</span></span>

<span data-ttu-id="03f7c-112">파이프라인은 명령줄 인터페이스에 사용되는 가장 중요한 개념이라고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-112">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="03f7c-113">적절히 사용하는 경우 파이프라인은 복잡한 명령을 사용할 필요를 줄여주고, 명령의 작업 흐름을 보다 쉽게 확인할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-113">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work for the commands.</span></span> <span data-ttu-id="03f7c-114">파이프라인에 있는 각 명령(파이프라인 요소)은 해당 출력을 파이프라인에 있는 다음 명령에 항목 단위로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-114">Each command in a pipeline (called a pipeline element) passes its output to the next command in the pipeline, item-by-item.</span></span> <span data-ttu-id="03f7c-115">따라서 명령이 한 번에 둘 이상의 항목을 처리할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-115">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="03f7c-116">그 결과 리소스 사용량이 줄어들고 출력이 바로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-116">The result is reduced resource consumption and the ability to begin getting the output immediately.</span></span>

<span data-ttu-id="03f7c-117">예를 들어 `Out-Host` cmdlet을 사용하여 다른 명령의 출력을 페이지 단위로 표시하면 다음과 같이 일반 텍스트가 페이지 단위로 나뉘어져 화면에 표시된 것처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-117">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="03f7c-118">페이징을 사용하면 전체 페이지를 표시할 준비가 되면 처리가 `Out-Host` cmdlet으로 전송되므로 역시 CPU 사용률을 줄이는 데 효과가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-118">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="03f7c-119">파이프라인의 앞에 나오는 cmdlet은 출력의 다음 페이지를 사용할 수 있게 될 때까지 실행을 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-119">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

<span data-ttu-id="03f7c-120">다음 명령을 비교하여 Windows 작업 관리자에서 파이프가 CPU 및 메모리 사용량에 어떻게 영향을 미치는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-120">You can see how piping impacts CPU and memory usage in the Windows Task Manager by comparing the following commands:</span></span>

- `Get-ChildItem C:\Windows -Recurse`
- `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`

> [!NOTE]
> <span data-ttu-id="03f7c-121">**페이징** 매개 변수는 일부 PowerShell 호스트에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-121">The **Paging** parameter is not supported by all PowerShell hosts.</span></span> <span data-ttu-id="03f7c-122">예를 들어 PowerShell ISE에서 **페이징** 매개 변수를 사용하려는 경우 다음 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-122">For example, when you try to use the **Paging** parameter in the PowerShell ISE, you see the following error:</span></span>
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a><span data-ttu-id="03f7c-123">파이프라인의 개체</span><span class="sxs-lookup"><span data-stu-id="03f7c-123">Objects in the pipeline</span></span>

<span data-ttu-id="03f7c-124">PowerShell에서 cmdlet을 실행하면 개체를 콘솔 창에 텍스트로 표시해야 하므로 텍스트 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-124">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="03f7c-125">텍스트 출력에 출력되는 개체의 모든 속성이 표시되지는 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-125">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="03f7c-126">예를 들어 `Get-Location` cmdlet을 고려해보세요.</span><span class="sxs-lookup"><span data-stu-id="03f7c-126">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="03f7c-127">현재 위치가 C 드라이브의 루트인 경우 `Get-Location`을 실행하면 다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-127">If you run `Get-Location` while your current location is the root of the C drive, you see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="03f7c-128">텍스트 출력은 `Get-Location`에서 반환된 개체의 완전한 표현이 아니라 정보의 요약입니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-128">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="03f7c-129">화면에 표시되는 데이터에 서식을 지정하는 프로세스에 따라 출력의 제목이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-129">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

<span data-ttu-id="03f7c-130">출력을 `Get-Member` cmdlet으로 파이프하면 `Get-Location`에서 반환된 개체에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-130">When you pipe the output to the `Get-Member` cmdlet you get information about the object returned by `Get-Location`.</span></span>

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="03f7c-131">`Get-Location`는 현재 경로 및 기타 정보를 포함하는 **PathInfo** 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="03f7c-131">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>

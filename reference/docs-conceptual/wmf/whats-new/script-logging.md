---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: 스크립트 추적 및 로깅
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147803"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="fbc40-103">스크립트 추적 및 로깅</span><span class="sxs-lookup"><span data-stu-id="fbc40-103">Script Tracing and Logging</span></span>

<span data-ttu-id="fbc40-104">PowerShell에는 cmdlet의 호출을 기록하는 **LogPipelineExecutionDetails** 그룹 정책 설정이 이미 있지만 PowerShell의 스크립트 언어는 기록 및 감사할 수 있는 여러 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="fbc40-105">새로운 세부 스크립트 추적 기능을 사용하여 시스템에서 PowerShell 스크립트 작업을 자세히 추적하고 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="fbc40-106">세부 스크립트 추적을 사용하도록 설정하면 PowerShell에서 모든 스크립트 블록을 ETW 이벤트 로그 **Microsoft-Windows-PowerShell/Operational**에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="fbc40-107">스크립트 블록에서 다른 스크립트 블록을 만드는 경우(예: `Invoke-Expression` 호출) 호출된 스크립트 블록도 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="fbc40-108">로깅은 **관리 템플릿** -> **Windows 구성 요소** -> **Windows PowerShell**에서 **PowerShell 스크립트 블록 로깅 켜기** 그룹 정책 설정을 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell**.</span></span>

<span data-ttu-id="fbc40-109">이벤트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-109">The events are:</span></span>

| <span data-ttu-id="fbc40-110">채널</span><span class="sxs-lookup"><span data-stu-id="fbc40-110">Channel</span></span> |                               <span data-ttu-id="fbc40-111">작동</span><span class="sxs-lookup"><span data-stu-id="fbc40-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="fbc40-112">수준</span><span class="sxs-lookup"><span data-stu-id="fbc40-112">Level</span></span>   | <span data-ttu-id="fbc40-113">Verbose</span><span class="sxs-lookup"><span data-stu-id="fbc40-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="fbc40-114">Opcode</span><span class="sxs-lookup"><span data-stu-id="fbc40-114">Opcode</span></span>  | <span data-ttu-id="fbc40-115">만들기</span><span class="sxs-lookup"><span data-stu-id="fbc40-115">Create</span></span>                                                                  |
| <span data-ttu-id="fbc40-116">작업</span><span class="sxs-lookup"><span data-stu-id="fbc40-116">Task</span></span>    | <span data-ttu-id="fbc40-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="fbc40-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="fbc40-118">키워드</span><span class="sxs-lookup"><span data-stu-id="fbc40-118">Keyword</span></span> | <span data-ttu-id="fbc40-119">Runspace</span><span class="sxs-lookup"><span data-stu-id="fbc40-119">Runspace</span></span>                                                                |
| <span data-ttu-id="fbc40-120">EventId</span><span class="sxs-lookup"><span data-stu-id="fbc40-120">EventId</span></span> | <span data-ttu-id="fbc40-121">Engine_ScriptBlockCompiled(0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="fbc40-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="fbc40-122">메시지</span><span class="sxs-lookup"><span data-stu-id="fbc40-122">Message</span></span> | <span data-ttu-id="fbc40-123">Scriptblock 텍스트를 만드는 중(%1/%2):</span><span class="sxs-lookup"><span data-stu-id="fbc40-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="fbc40-124">%3</span><span class="sxs-lookup"><span data-stu-id="fbc40-124">%3</span></span> </br> <span data-ttu-id="fbc40-125">ScriptBlock ID: %4</span><span class="sxs-lookup"><span data-stu-id="fbc40-125">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="fbc40-126">메시지에 포함된 텍스트는 컴파일된 스크립트 블록의 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="fbc40-127">ID는 스크립트 블록의 사용 기간 동안 유지되는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="fbc40-128">자세한 정보 로깅을 사용하도록 설정하면 기능에서 시작 및 끝 표식을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="fbc40-129">채널</span><span class="sxs-lookup"><span data-stu-id="fbc40-129">Channel</span></span> |                                 <span data-ttu-id="fbc40-130">작동</span><span class="sxs-lookup"><span data-stu-id="fbc40-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="fbc40-131">수준</span><span class="sxs-lookup"><span data-stu-id="fbc40-131">Level</span></span>   | <span data-ttu-id="fbc40-132">Verbose</span><span class="sxs-lookup"><span data-stu-id="fbc40-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="fbc40-133">Opcode</span><span class="sxs-lookup"><span data-stu-id="fbc40-133">Opcode</span></span>  | <span data-ttu-id="fbc40-134">열기/닫기</span><span class="sxs-lookup"><span data-stu-id="fbc40-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="fbc40-135">작업</span><span class="sxs-lookup"><span data-stu-id="fbc40-135">Task</span></span>    | <span data-ttu-id="fbc40-136">CommandStart/CommandStop</span><span class="sxs-lookup"><span data-stu-id="fbc40-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="fbc40-137">키워드</span><span class="sxs-lookup"><span data-stu-id="fbc40-137">Keyword</span></span> | <span data-ttu-id="fbc40-138">Runspace</span><span class="sxs-lookup"><span data-stu-id="fbc40-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="fbc40-139">EventId</span><span class="sxs-lookup"><span data-stu-id="fbc40-139">EventId</span></span> | <span data-ttu-id="fbc40-140">ScriptBlock\_Invoke\_Start\_Detail(0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="fbc40-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="fbc40-141">ScriptBlock\_Invoke\_Complete\_Detail(0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="fbc40-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="fbc40-142">메시지</span><span class="sxs-lookup"><span data-stu-id="fbc40-142">Message</span></span> | <span data-ttu-id="fbc40-143">ScriptBlock ID 호출을 시작/완료했습니다. %1</span><span class="sxs-lookup"><span data-stu-id="fbc40-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="fbc40-144">Runspace ID: %2</span><span class="sxs-lookup"><span data-stu-id="fbc40-144">Runspace ID: %2</span></span> |

<span data-ttu-id="fbc40-145">ID는 이벤트 ID 0x1008과 상호 관련될 수 있는 스크립트 블록을 나타내는 GUID이고 Runspace ID는 이 스크립트 블록이 실행된 runspace를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="fbc40-146">호출 메시지의 백분율 기호는 구조화된 ETW 속성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="fbc40-147">이러한 속성은 메시지 테스트에서 실제 값으로 대체되지만 액세스할 수 있는 보다 강력한 방법은 Get-WinEvent cmdlet을 사용하여 메시지를 검색한 다음 메시지의 **속성** 배열을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="fbc40-148">다음은 이 기능을 사용하여 스크립트를 암호화하여 난독 처리하려는 악의적인 시도를 해결하는 방법의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

<span data-ttu-id="fbc40-149">이 명령을 실행하면 다음과 같은 로그 항목이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-149">Running this generates the following log entries:</span></span>

```Output
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

스크립트 블록 길이가 단일 이벤트의 용량을 초과하는 경우 PowerShell이 스크립트를 여러 부분으로 나눕니다. <span data-ttu-id="fbc40-151">다음은 로그 메시지에서 스크립트를 다시 결합하는 샘플 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="fbc40-152">보존 버퍼가 제한된 모든 로깅 시스템과 마찬가지로 이 인프라를 공격하는 한 가지 방법은 가상 이벤트로 로그를 넘쳐나게 하여 이전 증거를 숨기는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="fbc40-153">이 공격으로부터 보호하려면 특정 형식의 이벤트 로그 컬렉션에서 Windows 이벤트 전달을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc40-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="fbc40-154">자세한 내용은 [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)(Windows 이벤트 로그 모니터링을 통해 악의적 사용자 포착)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbc40-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>
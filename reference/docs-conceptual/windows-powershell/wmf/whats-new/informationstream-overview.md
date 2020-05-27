---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: 정보 스트림
ms.openlocfilehash: 39cb3c36a70530b3ff9777edc74b88d276cbbb7c
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808929"
---
# <a name="information-stream"></a><span data-ttu-id="ac527-103">정보 스트림</span><span class="sxs-lookup"><span data-stu-id="ac527-103">Information Stream</span></span>

<span data-ttu-id="ac527-104">PowerShell 5.0에서는 새로운 구조적 **정보** 스트림을 사용하여 스크립트와 호스트 간에 정형 데이터를 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="ac527-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="ac527-105">`Write-Host`는 출력을 **정보** 스트림으로 내보내 캡처하거나 무시할 수 있도록 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ac527-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="ac527-106">`Write-Information`InformationVariable**및**InformationAction**일반 매개 변수와 함께 사용되는 새로운** cmdlet은 더 많은 유연성 및 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ac527-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="ac527-107">다음 함수는 새로운 **정보** 스트림을 활용하는 cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac527-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

<span data-ttu-id="ac527-108">다음 예제에서는 이 함수를 실행한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ac527-108">The following examples show the results of running this function.</span></span>

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

<span data-ttu-id="ac527-109">`$r` 변수는 스크립트 변수 `$p`에서 프로세스 정보를 캡처했습니다.</span><span class="sxs-lookup"><span data-stu-id="ac527-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="ac527-110">`Write-Host` cmdlet과 달리 **의** InformationVariable`Write-Information` 매개 변수를 사용하면 출력을 변수에 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac527-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="ac527-111">**태그**를 사용하여 **정보** 스트림에 전송되는 메시지에 대한 별도 채널을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac527-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

<span data-ttu-id="ac527-112">태그를 사용하여 **정보** 스트림에 메시지를 보내면 해당 메시지는 호스트 애플리케이션에 표시되지 않지만 태그 이름을 사용하여 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac527-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="ac527-113">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="ac527-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```

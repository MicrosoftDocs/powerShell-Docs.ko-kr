---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e01f6ceea361f5a9b3de645346d0652986b6267d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057233"
---
# <a name="nonewline-parameter"></a><span data-ttu-id="3cc40-102">NoNewLine 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cc40-102">NoNewLine parameter</span></span>
<span data-ttu-id="3cc40-103">**Out-File**, **Add-Content** 및 **Set-Content**는 단순히 출력 뒤에 오는 새 줄을 생략하는 새로운 **–NoNewline** 스위치를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc40-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="3cc40-104">**–NoNewline**을 지정하지 않으면 각 조각이 별도의 줄에 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cc40-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```

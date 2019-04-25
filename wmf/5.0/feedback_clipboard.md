---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057301"
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="af0fd-102">클립보드 cmdlet</span><span class="sxs-lookup"><span data-stu-id="af0fd-102">Clipboard cmdlets</span></span>
<span data-ttu-id="af0fd-103">**Get-Clipboard** 및 **Set-Clipboard**를 사용하면 Windows PowerShell 세션 간에 콘텐츠를 더 쉽게 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af0fd-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="af0fd-104">예를 들어, Windows 탐색기를 사용하여 세 개의 파일을 클립보드에 복사하는 경우(예: 파일을 선택한 후 `ctrl-c`를 누름) 클립보드의 내용을 파일 목록으로 손쉽게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af0fd-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="af0fd-105">클립보드 cmdlet은 이미지, 오디오 파일, 파일 목록 및 텍스트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="af0fd-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: aa2e9540af8b3d4c5de5e00377a84e0e5edd6e4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680382"
---
# <a name="new-temporaryfile"></a><span data-ttu-id="254cb-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="254cb-102">New-TemporaryFile</span></span>
<span data-ttu-id="254cb-103">경우에 따라 스크립트에서 임시 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="254cb-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="254cb-104">**New-TemporaryFile** cmdlet을 사용하면 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="254cb-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="254cb-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="254cb-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="254cb-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="254cb-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="254cb-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="254cb-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>

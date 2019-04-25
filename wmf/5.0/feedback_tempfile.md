---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: aa2e9540af8b3d4c5de5e00377a84e0e5edd6e4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057857"
---
# <a name="new-temporaryfile"></a><span data-ttu-id="3fda5-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="3fda5-102">New-TemporaryFile</span></span>
<span data-ttu-id="3fda5-103">경우에 따라 스크립트에서 임시 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fda5-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="3fda5-104">**New-TemporaryFile** cmdlet을 사용하면 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fda5-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="3fda5-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="3fda5-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="3fda5-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="3fda5-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="3fda5-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="3fda5-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>

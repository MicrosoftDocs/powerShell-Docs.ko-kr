---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085329"
---
# <a name="new-guid"></a><span data-ttu-id="3eac1-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="3eac1-102">New-Guid</span></span>
<span data-ttu-id="3eac1-103">종종 스크립트(또는 DSC 리소스 작성)에는 고유 식별자가 필요했습니다.</span><span class="sxs-lookup"><span data-stu-id="3eac1-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="3eac1-104">GUID는 잘 작동하고 .NET Framework Guid 클래스를 호출하여 쉽게 생성할 수 있지만 cmdlet을 사용하면 .NET Framework 클래스에 익숙하지 않은 최종 사용자가 더 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eac1-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="3eac1-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="3eac1-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="3eac1-106">Guid</span><span class="sxs-lookup"><span data-stu-id="3eac1-106">Guid</span></span>

----

<span data-ttu-id="3eac1-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="3eac1-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>

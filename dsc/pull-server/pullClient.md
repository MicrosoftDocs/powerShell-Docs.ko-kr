---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 끌어오기 클라이언트 설정
ms.openlocfilehash: b7cd6dc0087eb8368c5467df4c3c7266ed704451
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681863"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="72e53-103">DSC 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="72e53-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="72e53-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="72e53-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="72e53-105">끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72e53-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="72e53-106">관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="72e53-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="72e53-107">각 대상 노드는 끌어오기 모드를 사용하도록 지시받고 끌어오기 서버에 연결하여 구성 및 리소스를 가져올 수 있는 URL 또는 파일 위치와 보고서 데이터를 보내야 하는 URL 또는 파일 위치를 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72e53-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="72e53-108">다음 항목에서는 끌어오기 클라이언트를 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="72e53-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="72e53-109">구성 이름을 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="72e53-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="72e53-110">구성 ID를 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="72e53-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="72e53-111">**참고**: 이러한 항목은 PowerShell 5.0에 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="72e53-111">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="72e53-112">PowerShell 4.0에서 끌어오기 클라이언트를 설정하려면 [PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID4.md)을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="72e53-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>
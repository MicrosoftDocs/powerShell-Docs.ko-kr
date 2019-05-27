---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: 소프트웨어 인벤토리 로깅(SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855438"
---
# <a name="software-inventory-logging-sil"></a><span data-ttu-id="a67cd-103">소프트웨어 인벤토리 로깅(SIL)</span><span class="sxs-lookup"><span data-stu-id="a67cd-103">Software Inventory Logging (SIL)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a67cd-104">SIL이 이미 실행되고 있는 Windows Server 2012 R2 서버에 WMF 5.x를 설치하는 경우 설치 프로세스에서 소프트웨어 인벤토리 로깅 기능을 잘못 중지하므로 WMF 설치 후 Start-SilLogging cmdlet을 한 번 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a67cd-104">When installing WMF 5.x on a Windows Server 2012 R2 Server that is already running SIL, it is necessary to run the Start-SilLogging cmdlet once after the WMF install, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

<span data-ttu-id="a67cd-105">소프트웨어 인벤토리 로깅을 사용하면 서버에 로컬로 설치된 Microsoft 소프트웨어에 대한 정확한 정보를 가져오는 운영 비용을 줄일 수 있지만 특히 IT 환경(소프트웨어가 IT 환경에서 설치되어 실행되고 있는 것으로 가정)의 여러 서버에서 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="a67cd-105">Software Inventory Logging helps reduce the operational costs of getting accurate information about the Microsoft software installed locally on a server, but especially across many servers in an IT environment (assuming the software is installed and running across the IT environment).</span></span> <span data-ttu-id="a67cd-106">설정된 다음에는 이 데이터를 집계 서버로 전달하고 균일한 자동 프로세스를 사용하여 로그 데이터를 한 곳에 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a67cd-106">Provided one is set up, you can forward this data to an aggregation server, and collect the log data in one place by using a uniform, automatic process.</span></span>

<span data-ttu-id="a67cd-107">각 컴퓨터를 직접 쿼리하여 소프트웨어 인벤토리 데이터를 로깅할 수도 있지만 소프트웨어 인벤토리 로깅에서는 각 서버에서 시작되는 전달(네트워크를 통해) 아키텍처를 사용하여 많은 소프트웨어 인벤토리 및 자산 관리 시나리오에 일반적인 서버 검색 문제를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a67cd-107">While you can also log software inventory data by querying each computer directly, Software Inventory Logging, by employing a forwarding (over the network) architecture initiated by each server, can overcome server discovery challenges that are typical for many software inventory and asset management scenarios.</span></span> <span data-ttu-id="a67cd-108">소프트웨어 인벤토리 로깅에서는 SSL을 사용하여 HTTPS를 통해 집계 서버로 전달되는 데이터를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="a67cd-108">Software Inventory Logging uses SSL to secure data that is forwarded over HTTPS to an aggregation server.</span></span> <span data-ttu-id="a67cd-109">데이터를 한 곳에 저장하면 필요할 때 보다 쉽게 데이터를 분석, 조작 및 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a67cd-109">Storing the data in one place makes the data easier to analyze, manipulate, and share when necessary.</span></span>

<span data-ttu-id="a67cd-110">이러한 데이터는 이 기능의 일부로 Microsoft에 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a67cd-110">None of this data is sent to Microsoft as part of the feature functionality.</span></span> <span data-ttu-id="a67cd-111">소프트웨어 인벤토리 로깅 데이터 및 기능은 서버 소프트웨어의 라이선스 소유자 및 관리자만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a67cd-111">Software Inventory Logging data and functionality is meant for the sole use of the server software’s licensed owner and administrators.</span></span>

<span data-ttu-id="a67cd-112">소프트웨어 인벤토리 로깅 cmdlet에 대한 자세한 내용 및 설명서는 [Windows Server 2012 R2의 소프트웨어 인벤토리 로깅 관리](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11))를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a67cd-112">For more information and documentation about Software Inventory Logging cmdlets, see [Manage Software Inventory Logging in Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).</span></span>

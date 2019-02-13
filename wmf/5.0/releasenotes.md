---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 07ebcfd37cc3e1f38a9434ffa8d86f479b89ee0f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680633"
---
# <a name="windows-management-framework-wmf-50-rtm-release-notes-overview"></a><span data-ttu-id="2a8d4-102">WMF(Windows Management Framework) 5.0 RTM 릴리스 정보 개요</span><span class="sxs-lookup"><span data-stu-id="2a8d4-102">Windows Management Framework (WMF) 5.0 RTM Release Notes Overview</span></span>

<span data-ttu-id="2a8d4-103">**WMF 5.0은 WMF 5.1에서 대체 됩니다. WMF 5.0을 사용하는 사용자는 지원을 받기 위해 WMF 5.1로 업그레이드해야 합니다. [WMF 5.1 설치 지침](../5.1/install-configure.md)** 을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="2a8d4-103">**WMF 5.0 is superseded by WMF 5.1. Users with WMF 5.0 must upgrade to WMF 5.1 to receive support. Please follow the [installation intructions of WMF 5.1](../5.1/install-configure.md)**</span></span>

<span data-ttu-id="2a8d4-104">WMF(Windows Management Framework) 5.0 RTM은 WMF 4.0에서 업데이트된 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2a8d4-104">Windows Management Framework (WMF) 5.0 RTM brings functionality that has been updated from WMF 4.0.</span></span> <span data-ttu-id="2a8d4-105">WMF 5.0 RTM은 **Windows Server 2012 R2**, **Windows Server 2012**, **Windows Server 2008 R2**, **Windows 8.1** 및 **Windows 7 SP1**에 설치하는 경우에만 사용할 수 있고 업데이트된 버전을 포함하거나 다음과 같은 기능을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="2a8d4-105">WMF 5.0 RTM is available for installation only on **Windows Server 2012 R2**, **Windows Server 2012**, **Windows Server 2008 R2**, **Windows 8.1**, and **Windows 7 SP1** and contains updated versions or introduction of the following features:</span></span>

- <span data-ttu-id="2a8d4-106">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a8d4-106">Windows PowerShell</span></span>
- <span data-ttu-id="2a8d4-107">JEA(Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="2a8d4-107">Just Enough Administration (JEA)</span></span>
- <span data-ttu-id="2a8d4-108">Windows PowerShell DSC(원하는 상태 구성)</span><span class="sxs-lookup"><span data-stu-id="2a8d4-108">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="2a8d4-109">Windows PowerShell ISE(통합 스크립팅 환경)</span><span class="sxs-lookup"><span data-stu-id="2a8d4-109">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>
- <span data-ttu-id="2a8d4-110">Windows PowerShell 웹 서비스(관리 OData IIS 확장)</span><span class="sxs-lookup"><span data-stu-id="2a8d4-110">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="2a8d4-111">WinRM(Windows Remote Management)</span><span class="sxs-lookup"><span data-stu-id="2a8d4-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="2a8d4-112">WMI(Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="2a8d4-112">Windows Management Instrumentation (WMI)</span></span>

<span data-ttu-id="2a8d4-113">WMF 5.0 RTM은 [WMF 5.0 Production Preview](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx)를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="2a8d4-113">WMF 5.0 RTM replaces the [WMF 5.0 Production Preview](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx).</span></span> <span data-ttu-id="2a8d4-114">WMF 5.0 Production Preview를 제거하지 않고도 WMF 5.0 RTM을 설치할 수 있지만 WMF 5.0 RTM을 설치하기 전에 WMF 5.0 preview의 다른 모든 이전 릴리스를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a8d4-114">You can install WMF 5.0 RTM without uninstalling WMF 5.0 Production Preview, but you must uninstall all other older releases of WMF 5.0 previews before installing the WMF 5.0 RTM.</span></span>

<span data-ttu-id="2a8d4-115">*참고:* Windows 10을 실행하는 경우 Windows 10의 11월 업데이트(버전 1511)로 업데이트하여 WMF 5.0 RTM에서 제공되는 것과 동일한 기능 집합을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a8d4-115">*Note:* If you are running Windows 10, you can get the same set of functionality available in WMF 5.0 RTM by updating to the November update of Windows 10 (Version 1511).</span></span> <span data-ttu-id="2a8d4-116">Windows 10 시스템을 아직 업데이트하지 않은 경우 시작 단추를 선택한 다음 설정 > 업데이트 및 보안 > Windows 업데이트 > 업데이트 확인을 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="2a8d4-116">If you have not already updated your Windows 10 system, select the Start button, then select Settings > Update & security > Windows Update > Check for updates.</span></span>

---
ms.date: 08/12/2017
ms.topic: conceptual
keywords: 'wmf,powershell,setup'
title: WMF 5.1 릴리스 정보
---

# <a name="windows-management-framework-wmf-51"></a><span data-ttu-id="7db10-103">WMF(Windows Management Framework) 5.1</span><span class="sxs-lookup"><span data-stu-id="7db10-103">Windows Management Framework (WMF) 5.1</span></span>

<span data-ttu-id="7db10-104">WMF는 기존 Windows 시스템을 Windows Server 2016과 함께 릴리스된 PowerShell, WMI, WinRM 및 SIL(소프트웨어 인벤토리 로깅) 구성 요소 버전으로 업데이트하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7db10-104">WMF provides users with the ability to update existing Windows systems to the versions of PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>

<span data-ttu-id="7db10-105">WMF 5.1은 Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 및 2012 R2에 설치할 수 있으며 WMF 5.0 RTM보다 개선된 많은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7db10-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="7db10-106">새 cmdlet: 로컬 사용자 및 그룹; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="7db10-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="7db10-107">서명된 모듈, JEA 모듈 설치 등의 PowerShellGet 개선 사항</span><span class="sxs-lookup"><span data-stu-id="7db10-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="7db10-108">PackageManagement에서 컨테이너, CBS 설치, EXE 기반 설치, CAB 패키지에 대한 지원 추가</span><span class="sxs-lookup"><span data-stu-id="7db10-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="7db10-109">DSC 및 PowerShell 클래스에 대한 디버깅 개선 사항</span><span class="sxs-lookup"><span data-stu-id="7db10-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="7db10-110">끌어오기 서버에서 나오는 카탈로그 서명 모듈 적용 및 PowerShellGet cmdlet을 사용할 경우를 비롯한 보안 향상</span><span class="sxs-lookup"><span data-stu-id="7db10-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="7db10-111">다양한 사용자 요청 및 문제에 대한 응답</span><span class="sxs-lookup"><span data-stu-id="7db10-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="7db10-112">이 릴리스의 새로운 기능에 대해 알아보려면 [새로운 시나리오 및 기능](https://docs.microsoft.com/powershell/wmf/5.1/scenarios-features) 아래에 나열된 항목을 찾아보세요.</span><span class="sxs-lookup"><span data-stu-id="7db10-112">To learn about what is new in this release, browse the topics listed under [New Scenarios and Features](https://docs.microsoft.com/powershell/wmf/5.1/scenarios-features).</span></span>

<span data-ttu-id="7db10-113">[설치 및 구성](https://docs.microsoft.com/powershell/wmf/5.1/install-configure) 항목에서는 요구 사항과 WMF에 대한 설치 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7db10-113">The [Install and Configure](https://docs.microsoft.com/powershell/wmf/5.1/install-configure) topic lists the requirements and provides installation instructions for WMF.</span></span>

<span data-ttu-id="7db10-114">[호환성](https://docs.microsoft.com/powershell/wmf/5.1/compatibility) 항목에는 어떤 Windows 릴리스에 어떤 WMF 버전을 설치할 수 있는지가 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7db10-114">The [Compatibility](https://docs.microsoft.com/powershell/wmf/5.1/compatibility) topic lists which versions of WMF may be installed on which Windows releases.</span></span>

<span data-ttu-id="7db10-115">[제품 호환성](https://docs.microsoft.com/powershell/wmf/5.1/productincompat)에는 현재 WMF 5.1 사용이 승인되지 않은 Microsoft 애플리케이션이 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7db10-115">[Product Compatibility](https://docs.microsoft.com/powershell/wmf/5.1/productincompat) lists the Microsoft applications that have not approved WMF 5.1 for use at this time.</span></span>

<span data-ttu-id="7db10-116">WMF 구성 요소에 대한 자세한 내용은 다음 MSDN 설명서에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7db10-116">Details for the components of WMF will be found in MSDN documentation:</span></span>

- [<span data-ttu-id="7db10-117">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="7db10-117">PowerShell 5.1</span></span>](https://docs.microsoft.com/powershell/)
- <span data-ttu-id="7db10-118">[WMI](https://msdn.microsoft.com/library/jj152383(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="7db10-118">[WMI](https://msdn.microsoft.com/library/jj152383(v=vs.85).aspx)</span></span>
- <span data-ttu-id="7db10-119">[WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="7db10-119">[WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx)</span></span>
- <span data-ttu-id="7db10-120">[소프트웨어 인벤토리 로깅](https://technet.microsoft.com/library/dn383584(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="7db10-120">[Software Inventory Logging](https://technet.microsoft.com/library/dn383584(v=ws.11).aspx)</span></span>

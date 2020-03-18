---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: Windows PowerShell 웹 액세스 제거
ms.openlocfilehash: 3c2c83525f5a240976eef215b5eac939796c91e8
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279013"
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="58db1-103">Windows PowerShell 웹 액세스 제거</span><span class="sxs-lookup"><span data-stu-id="58db1-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="58db1-104">업데이트 날짜: 2013년 6월 24일</span><span class="sxs-lookup"><span data-stu-id="58db1-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="58db1-105">적용 대상: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="58db1-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="58db1-106">이 항목의 단계에서는 Windows PowerShell 웹 액세스 웹 사이트 및 해당 애플리케이션을 설치된 게이트웨이 서버에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="58db1-107">사용자에게 알림</span><span class="sxs-lookup"><span data-stu-id="58db1-107">Notify users</span></span>

<span data-ttu-id="58db1-108">시작하기 전에 웹 기반 콘솔의 사용자에게 웹 사이트가 제거됨을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="58db1-109">자동으로 설치된 IIS나 기타 기능은 Windows PowerShell 웹 액세스에서 실행되어야 하므로, Windows PowerShell 웹 액세스를 제거해도 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="58db1-110">제거 프로세스에서는 Windows PowerShell 웹 액세스가 종속된 기능을 설치된 상태로 남겨 두기 때문에 필요한 경우 이러한 기능을 별도로 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="58db1-111">권장(빠른) 제거</span><span class="sxs-lookup"><span data-stu-id="58db1-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="58db1-112">이 섹션의 절차에서는 Windows PowerShell cmdlet을 사용하여</span><span class="sxs-lookup"><span data-stu-id="58db1-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="58db1-113">Windows PowerShell 웹 액세스 웹 애플리케이션 및</span><span class="sxs-lookup"><span data-stu-id="58db1-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="58db1-114">Windows PowerShell 웹 액세스 기능을</span><span class="sxs-lookup"><span data-stu-id="58db1-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="58db1-115">모두 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="58db1-116">1단계: cmdlet을 사용하여 웹 애플리케이션 삭제</span><span class="sxs-lookup"><span data-stu-id="58db1-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="58db1-117">다음 중 하나를 수행하여 Windows PowerShell 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-117">Do one of the following to open a Windows PowerShell session.</span></span>

   - <span data-ttu-id="58db1-118">Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>
   - <span data-ttu-id="58db1-119">Windows **시작** 화면에서 **Windows PowerShell**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="58db1-120">`Uninstall-PswaWebApplication`을 입력하고 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>

   1. <span data-ttu-id="58db1-121">고유의 사용자 지정 웹 사이트 이름을 지정한 경우 `-WebsiteName` 매개 변수를 명령에 추가하고 웹 사이트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

      `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`

   1. <span data-ttu-id="58db1-122">기본 애플리케이션(**pswa**)이 아닌 사용자 지정 웹 애플리케이션을 사용한 경우 `-WebApplicationName` 매개 변수를 명령에 추가하고 웹 애플리케이션의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

      `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`

   1. <span data-ttu-id="58db1-123">테스트 인증서를 사용하는 경우, 다음 예제와 같이 cmdlet에 `DeleteTestCertificate` 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

      `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="58db1-124">2단계: cmdlet을 사용하여 Windows PowerShell 웹 액세스 제거</span><span class="sxs-lookup"><span data-stu-id="58db1-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="58db1-125">다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="58db1-126">세션이가 이미 열려 있으면 다음 단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-126">If a session is already open, go on to the next step.</span></span>

    - <span data-ttu-id="58db1-127">Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>
    - <span data-ttu-id="58db1-128">Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="58db1-129">다음을 입력하고 **Enter** 키를 누릅니다. 여기서 *computer_name*은 Windows PowerShell 웹 액세스를 제거할 원격 서버를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="58db1-130">제거 작업에 필요한 경우 `-Restart` 매개 변수를 추가하여 대상 서버를 자동으로 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart`

    <span data-ttu-id="58db1-131">역할 및 기능을 오프라인 VHD에서 제거하려는 경우에는 `-ComputerName` 매개 변수와 `-VHD` 매개 변수를 모두 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="58db1-132">`-ComputerName` 매개 변수에는 VHD를 탑재할 서버의 이름이 포함되며, `-VHD` 매개 변수에는 지정된 서버에서의 VHD 파일 경로가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart`

1. <span data-ttu-id="58db1-133">제거가 완료되면 서버 관리자에서 **모든 서버** 페이지를 열고 기능을 제거한 서버를 선택한 후 선택한 서버 페이지에서 **역할 및 기능** 타일을 확인하여 Windows PowerShell 웹 액세스가 제거되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="58db1-134">또한 선택한 서버(Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;)를 대상으로 `Get-WindowsFeature` cmdlet을 실행하여 서버에 설치된 역할 및 기능 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server  (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features  that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="58db1-135">사용자 지정 제거</span><span class="sxs-lookup"><span data-stu-id="58db1-135">Custom uninstallation</span></span>

<span data-ttu-id="58db1-136">이 섹션의 절차를 따라서 서버 관리자의 역할 및 기능 제거 마법사 및 IIS 관리자 콘솔을 사용하여 Windows PowerShell 웹 액세스 웹 애플리케이션 및 Windows PowerShell 웹 액세스 기능을 모두 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="58db1-137">1단계: IIS 관리자를 사용하여 웹 애플리케이션 삭제</span><span class="sxs-lookup"><span data-stu-id="58db1-137">Step 1: Delete the web application using IIS Manager</span></span>

1. <span data-ttu-id="58db1-138">다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="58db1-139">콘솔이 이미 열려 있으면 다음 단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-139">If it is already open, go on to the next step.</span></span>

   - <span data-ttu-id="58db1-140">Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="58db1-141">서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

   - <span data-ttu-id="58db1-142">Windows **시작** 화면에서 **IIS(인터넷 정보 서비스) 관리자** 이름의 일부를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="58db1-143">**응용 프로그램** 결과에 바로 가기가 표시되면 이를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="58db1-144">IIS 관리자의 트리 창에서 Windows PowerShell 웹 액세스 웹 애플리케이션이 실행 중인 웹 사이트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="58db1-145">**작업** 창의 **웹 사이트 관리**에서 **중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="58db1-146">트리 창에서 Windows PowerShell 웹 액세스 웹 애플리케이션이 실행 중인 웹 사이트의 웹 애플리케이션을 마우스 오른쪽 단추로 클릭한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="58db1-147">트리 창에서 **애플리케이션 풀**을 선택하고 Windows PowerShell 웹 액세스 애플리케이션 폴더를 선택한 후 **작업** 창에서 **중지**를 선택하고 내용 창에서 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="58db1-148">IIS 관리자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-148">Close IIS Manager.</span></span>

   > [!WARNING]
   > <span data-ttu-id="58db1-149">인증서는 제거 과정에서 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-149">The certificate is not deleted during uninstallation.</span></span> <span data-ttu-id="58db1-150">자체 서명된 인증서를 만들었거나 테스트 인증서를 사용한 경우에 이 인증서를 제거하려면 IIS 관리자에서 해당 인증서를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-150">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="58db1-151">2단계: 역할 및 기능 제거 마법사를 사용하여 Windows PowerShell 웹 액세스 제거</span><span class="sxs-lookup"><span data-stu-id="58db1-151">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="58db1-152">서버 관리자가 이미 열려 있으면 다음 단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-152">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="58db1-153">서버 관리자가 아직 열려 있지 않으면 다음 중 하나를 수행하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-153">If Server Manager is not already open, open it by doing one of the following.</span></span>

    - <span data-ttu-id="58db1-154">Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-154">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>
    - <span data-ttu-id="58db1-155">Windows **시작** 화면에서 **서버 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-155">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="58db1-156">**관리** 메뉴에서 **역할 및 기능 제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-156">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="58db1-157">**대상 서버 선택** 페이지에서 기능을 제거할 서버나 오프라인 VHD를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-157">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="58db1-158">오프라인 VHD를 선택하려면 먼저 VHD가 탑재될 서버를 선택한 다음 VHD 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-158">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="58db1-159">대상 서버를 선택하고 나면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-159">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="58db1-160">다시 **다음** 을 클릭하여 **기능 제거** 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-160">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="58db1-161">**Windows PowerShell 웹 액세스**확인란의 선택을 취소하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-161">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="58db1-162">**제거 선택 확인** 페이지에서 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58db1-162">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="58db1-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58db1-163">See Also</span></span>

- [<span data-ttu-id="58db1-164">Windows PowerShell 웹 액세스 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="58db1-164">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="58db1-165">IIS 관리자 7.0 도움말</span><span class="sxs-lookup"><span data-stu-id="58db1-165">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)
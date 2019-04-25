---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3d74217621d00dfd68cad1c45d187a9c2ffb9980
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085281"
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="35b51-102">알려진 문제 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="35b51-102">Known Issues and Limitations</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="35b51-103">처음으로 사용할 때 PowerShell 바로 가기가 끊어짐</span><span class="sxs-lookup"><span data-stu-id="35b51-103">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="35b51-104">**해결 방법:** 다음 작업 중 하나를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="35b51-104">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="35b51-105">PowerShell 바로 가기를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="35b51-106">"Windows PowerShell"을 선택하여 일반 권한 모드로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="35b51-107">PowerShell 바로 가기를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="35b51-108">"Windows PowerShell"을 마우스 오른쪽 단추로 클릭하고 "관리자 권한으로 실행"을 선택하여 관리자 권한 모드로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="35b51-109">위 작업 중 하나를 수행했으면 PowerShell 바로 가기가 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="35b51-110">이러한 작업은 한 번만 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-110">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="35b51-111">PowerShell 모듈 및 DSC 리소스가 Windows 7의 ExecutionPolicy에 대해 오류를 보고함</span><span class="sxs-lookup"><span data-stu-id="35b51-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="35b51-112">Windows 7에서 PowerShell 모듈 및 DSC 리소스를 사용하면 ExecutionPolicy에 대해 오류가 보고될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="35b51-113">**해결 방법:** 다음 명령을 관리자 권한 PowerShell 세션에서 실행(관리자 권한으로 실행)하여 ExecutionPolicy를 RemoteSigned로 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="35b51-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="35b51-114">이전 원격 Exchange 엔드포인트에 연결하면 충돌이 발생함</span><span class="sxs-lookup"><span data-stu-id="35b51-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="35b51-115">이전 Exchange 엔드포인트는 새 엔드포인트로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="35b51-116">충돌을 발생시키는 리디렉션 논리에 버그가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="35b51-117">**해결 방법:** 새 엔드포인트에 직접 연결하세요.</span><span class="sxs-lookup"><span data-stu-id="35b51-117">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="35b51-118">Windows Server 2012 R2에 WMF 5.0 설치 후 소프트웨어 인벤토리 로깅 기능이 잘못 중지됨</span><span class="sxs-lookup"><span data-stu-id="35b51-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="35b51-119">SIL이 이미 실행되고 있는 Windows Server 2012 R2에 WMF 5.0을 설치하면 소프트웨어 인벤토리 로깅 기능이 설치 후 잘못 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="35b51-120">**해결 방법:** 설치 프로세스에서 소프트웨어 인벤토리 로깅 기능을 잘못 중지할 수 있으므로 WMF 설치 후에 Start-SilLogging cmdlet을 한 번 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="35b51-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="35b51-121">-LiteralPath 및 -Recurse가 함께 사용되는 경우 `Get-ChildItem`이 작동하지 않음</span><span class="sxs-lookup"><span data-stu-id="35b51-121">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="35b51-122">디렉터리 이름에 잘못된 와일드카드 문자가 포함된 경우 -LiteralPath와 -Recurse를 함께 사용하면 `Get-ChildItem`에서 예상된 결과를 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-122">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="35b51-123">**해결 방법:** 적합하지는 않지만 현재 해결 방법은 cmdlet을 사용하지 않고 스크립트에서 재귀를 구현하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="35b51-124">WMF 5.0 설치 후 Sysprep 실패</span><span class="sxs-lookup"><span data-stu-id="35b51-124">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="35b51-125">이 문제에 대한 해결 방법에는 실행 중인 Windows Server의 버전에 따라 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="35b51-126">**해결 방법:**</span><span class="sxs-lookup"><span data-stu-id="35b51-126">**Resolution:**</span></span>

- <span data-ttu-id="35b51-127">**Windows Server 2008 R2**를 실행 중인 시스템의 경우</span><span class="sxs-lookup"><span data-stu-id="35b51-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="35b51-128">관리자 권한으로 PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-128">Open PowerShell as an administrator</span></span>
  2. <span data-ttu-id="35b51-129">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-129">Run the following command</span></span>

     ```powershell
     Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="35b51-130">명령을 실행하고 예상되는 오류는 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-130">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="35b51-131">\Windows\System32\Logfiles\SIL\ 디렉터리에 있는 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="35b51-132">모든 사용 가능한 중요 Windows 업데이트를 설치하고 Sysyprep 작업을 정상적으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="35b51-133">**Windows Server 2012**를 실행 중인 시스템의 경우</span><span class="sxs-lookup"><span data-stu-id="35b51-133">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="35b51-134">Sysprep을 실행할 서버에서 WMF 5.0을 설치한 후 관리자 권한으로 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2. <span data-ttu-id="35b51-135">\Windows\System32\Sysprep\ActionFiles\ 디렉터리의 Generize.xml을 Windows 디렉터리 외부 위치(예: C:\)에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3. <span data-ttu-id="35b51-136">Generalize.xml 복사본을 메모장으로 엽니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-136">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="35b51-137">다음 텍스트를 찾아 제거합니다. 각 텍스트를 한 번씩 삭제해야 합니다(문서의 끝 부분에 있음).</span><span class="sxs-lookup"><span data-stu-id="35b51-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="35b51-138">Generalize.xml의 편집된 복사본을 저장하고 파일을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="35b51-139">관리자 권한으로 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-139">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="35b51-140">다음 명령을 실행하여 system32 폴더에서 Generalize.xml 파일의 소유권을 갖도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="35b51-141">다음 명령을 실행하여 파일에 대한 적절한 권한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-141">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="35b51-142">확인 프롬프트에서 예를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-142">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="35b51-143">`<AdministratorUserName>`을 컴퓨터에서 관리자인 사용자 이름으로 대체해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="35b51-144">예를 들어, "Administrator"가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-144">For example, "Administrator".</span></span>

  9. <span data-ttu-id="35b51-145">다음 명령을 사용하여 편집 및 저장한 파일을 Sysprep 디렉터리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="35b51-146">예를 선택하여 덮어씁니다(덮어쓸지 여부를 묻는 메시지가 표시되지 않는다면, 입력한 경로를 다시 확인하세요.).</span><span class="sxs-lookup"><span data-stu-id="35b51-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="35b51-147">Generalize.xml의 편집 복사본이 C:\에 복사되었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="35b51-148">이제 이 해결 방법으로 Generalize.xml이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="35b51-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="35b51-149">활성화된 일반화 옵션으로 Sysprep을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="35b51-149">Please run Sysprep with the generalize option enabled.</span></span>
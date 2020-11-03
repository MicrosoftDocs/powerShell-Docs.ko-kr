---
description: PowerShell 실행 정책을 준수 하도록 스크립트에 서명 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Signing
ms.openlocfilehash: 060a53d4d08700e541fb6bcd388ffb4167a271a3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222345"
---
# <a name="about-signing"></a><span data-ttu-id="05089-104">서명 정보</span><span class="sxs-lookup"><span data-stu-id="05089-104">About Signing</span></span>

## <a name="short-description"></a><span data-ttu-id="05089-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="05089-105">Short description</span></span>
<span data-ttu-id="05089-106">PowerShell 실행 정책을 준수 하도록 스크립트에 서명 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-106">Explains how to sign scripts so that they comply with the PowerShell execution policies.</span></span>

## <a name="long-description"></a><span data-ttu-id="05089-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="05089-107">Long description</span></span>

<span data-ttu-id="05089-108">제한 된 실행 정책은 스크립트를 실행 하는 것을 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-108">The Restricted execution policy does not permit any scripts to run.</span></span> <span data-ttu-id="05089-109">**AllSigned** 및 **RemoteSigned** 실행 정책은 PowerShell에서 디지털 서명이 없는 스크립트를 실행 하는 것을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-109">The **AllSigned** and **RemoteSigned** execution policies prevent PowerShell from running scripts that do not have a digital signature.</span></span>

<span data-ttu-id="05089-110">이 항목에서는 실행 정책이 **RemoteSigned** 때에도 서명 되지 않은 선택한 스크립트를 실행 하는 방법 및 사용자가 직접 사용 하기 위해 스크립트에 서명 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-110">This topic explains how to run selected scripts that are not signed, even while the execution policy is **RemoteSigned** , and how to sign scripts for your own use.</span></span>

<span data-ttu-id="05089-111">PowerShell 실행 정책에 대 한 자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05089-111">For more information about PowerShell execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

## <a name="to-permit-signed-scripts-to-run"></a><span data-ttu-id="05089-112">서명 된 스크립트의 실행을 허용 하려면</span><span class="sxs-lookup"><span data-stu-id="05089-112">To permit signed scripts to run</span></span>

<span data-ttu-id="05089-113">컴퓨터에서 처음으로 PowerShell을 시작 하면 **제한** 된 실행 정책 (기본값)이 적용 될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-113">When you start PowerShell on a computer for the first time, the **Restricted** execution policy (the default) is likely to be in effect.</span></span>

<span data-ttu-id="05089-114">**제한** 된 정책은 스크립트를 실행 하는 것을 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-114">The **Restricted** policy does not permit any scripts to run.</span></span>

<span data-ttu-id="05089-115">컴퓨터에서 유효한 실행 정책을 찾으려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-115">To find the effective execution policy on your computer, type:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="05089-116">로컬 컴퓨터에서 작성 하는 서명 되지 않은 스크립트를 실행 하 고 다른 사용자 로부터 서명 된 스크립트를 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 하 고 다음 명령을 사용 하 여 컴퓨터의 실행 정책을 **RemoteSigned** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-116">To run unsigned scripts that you write on your local computer and signed scripts from other users, start PowerShell with the Run as Administrator option and then use the following command to change the execution policy on the computer to **RemoteSigned** :</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="05089-117">자세한 내용은 cmdlet에 대 한 도움말 항목을 참조 하세요 `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="05089-117">For more information, see the help topic for the `Set-ExecutionPolicy` cmdlet.</span></span>

## <a name="running-unsigned-scripts-using-the-remotesigned-execution-policy"></a><span data-ttu-id="05089-118">RemoteSigned 실행 정책을 사용 하 여 서명 되지 않은 스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="05089-118">Running unsigned scripts using the RemoteSigned execution policy</span></span>

<span data-ttu-id="05089-119">PowerShell 실행 정책이 **RemoteSigned** 인 경우 powershell은 인터넷에서 다운로드 한 서명 되지 않은 스크립트를 실행 하지 않습니다. 즉, 전자 메일 및 인스턴트 메시징 프로그램을 통해 수신 하는 서명 되지 않은 스크립트를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-119">If your PowerShell execution policy is **RemoteSigned** , PowerShell will not run unsigned scripts that are downloaded from the internet, including unsigned scripts you receive through email and instant messaging programs.</span></span>

<span data-ttu-id="05089-120">다운로드 한 스크립트를 실행 하려고 하면 PowerShell에서 다음과 같은 오류 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05089-120">If you try to run a downloaded script, PowerShell displays the following error message:</span></span>

```Output
The file <file-name> cannot be loaded. The file <file-name> is not digitally
signed. The script will not execute on the system. Please see "Get-Help
about_Signing" for more details.
```

<span data-ttu-id="05089-121">스크립트를 실행 하기 전에 코드를 검토 하 여 신뢰 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-121">Before you run the script, review the code to be sure that you trust it.</span></span>
<span data-ttu-id="05089-122">스크립트는 실행 프로그램과 동일한 효과를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="05089-122">Scripts have the same effect as any executable program.</span></span>

<span data-ttu-id="05089-123">서명 되지 않은 스크립트를 실행 하려면 Unblock-File cmdlet을 사용 하거나 다음 절차를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-123">To run an unsigned script, use the Unblock-File cmdlet or use the following procedure.</span></span>

1. <span data-ttu-id="05089-124">컴퓨터에 스크립트 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-124">Save the script file on your computer.</span></span>
2. <span data-ttu-id="05089-125">시작을 클릭 하 고 내 컴퓨터를 클릭 한 다음 저장 된 스크립트 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-125">Click Start, click My Computer, and locate the saved script file.</span></span>
3. <span data-ttu-id="05089-126">스크립트 파일을 마우스 오른쪽 단추로 클릭 한 다음 속성을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-126">Right-click the script file, and then click Properties.</span></span>
4. <span data-ttu-id="05089-127">차단 해제를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-127">Click Unblock.</span></span>

<span data-ttu-id="05089-128">인터넷에서 다운로드 한 스크립트가 디지털 서명 되어 있지만 아직 게시자를 신뢰 하도록 선택 하지 않은 경우 PowerShell에서 다음 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-128">If a script that was downloaded from the internet is digitally signed, but you have not yet chosen to trust its publisher, PowerShell displays the following message:</span></span>

```Output
Do you want to run software from this untrusted publisher?
The file <file-name> is published by CN=<publisher-name>. This
publisher is not trusted on your system. Only run scripts
from trusted publishers.

[V] Never run  [D] Do not run  [R] Run once  [A] Always run
[?] Help (default is "D"):
```

<span data-ttu-id="05089-129">게시자를 신뢰 하는 경우 "한 번 실행" 또는 "항상 실행"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-129">If you trust the publisher, select "Run once" or "Always run."</span></span> <span data-ttu-id="05089-130">게시자를 신뢰 하지 않는 경우 "실행 안 함" 또는 "실행 안 함" 중 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-130">If you do not trust the publisher, select either "Never run" or "Do not run."</span></span> <span data-ttu-id="05089-131">"실행 안 함" 또는 "항상 실행"을 선택 하는 경우 PowerShell에서이 게시자에 대 한 메시지를 다시 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-131">If you select "Never run" or "Always run," PowerShell will not prompt you again for this publisher.</span></span>

## <a name="methods-of-signing-scripts"></a><span data-ttu-id="05089-132">스크립트 서명 방법</span><span class="sxs-lookup"><span data-stu-id="05089-132">Methods of signing scripts</span></span>

<span data-ttu-id="05089-133">작성 하는 스크립트와 다른 원본에서 가져온 스크립트에 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-133">You can sign the scripts that you write and the scripts that you obtain from other sources.</span></span> <span data-ttu-id="05089-134">스크립트에 서명 하기 전에 각 명령을 검사 하 여 실행 해도 안전한 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-134">Before you sign any script, examine each command to verify that it is safe to run.</span></span>

<span data-ttu-id="05089-135">코드 서명에 대 한 모범 사례는 [코드 서명 모범 사례](/previous-versions/windows/hardware/design/dn653556(v=vs.85))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05089-135">For best practices about code signing, see [Code-Signing Best Practices](/previous-versions/windows/hardware/design/dn653556(v=vs.85)).</span></span>

<span data-ttu-id="05089-136">스크립트 파일에 서명 하는 방법에 대 한 자세한 내용은 [get-authenticodesignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="05089-136">For more information about how to sign a script file, see [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature).</span></span>

<span data-ttu-id="05089-137">`New-SelfSignedCertificate`PowerShell 3.0의 PKI 모듈에 도입 된 cmdlet은 테스트에 적합 한 자체 서명 된 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05089-137">The `New-SelfSignedCertificate` cmdlet, introduced in the PKI module in PowerShell 3.0, creates a self-signed certificate that is Appropriate for testing.</span></span> <span data-ttu-id="05089-138">자세한 내용은 New-SelfSignedCertificate cmdlet에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05089-138">For more information, see the help topic for the New-SelfSignedCertificate cmdlet.</span></span>

<span data-ttu-id="05089-139">스크립트에 디지털 서명을 추가 하려면 코드 서명 인증서를 사용 하 여 서명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-139">To add a digital signature to a script, you must sign it with a code signing certificate.</span></span> <span data-ttu-id="05089-140">스크립트 파일에 서명 하는 데 적합 한 두 가지 유형의 인증서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-140">Two types of certificates are suitable for signing a script file:</span></span>

- <span data-ttu-id="05089-141">인증 기관에서 만든 인증서: 유료로 공개 인증 기관에서 id를 확인 하 고 코드 서명 인증서를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-141">Certificates that are created by a certification authority: For a fee, a public certification authority verifies your identity and gives you a code signing certificate.</span></span> <span data-ttu-id="05089-142">신뢰할 수 있는 인증 기관에서 인증서를 구매 하는 경우 다른 컴퓨터가 인증 기관을 신뢰 하므로 Windows를 실행 하는 다른 컴퓨터의 사용자와 스크립트를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-142">When you purchase your certificate from a reputable certification authority, you are able to share your script with users on other computers that are running Windows because those other computers trust the certification authority.</span></span>

- <span data-ttu-id="05089-143">만든 인증서: 인증서를 만드는 기관에 해당 하는 자체 서명 된 인증서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-143">Certificates that you create: You can create a self-signed certificate for which your computer is the authority that creates the certificate.</span></span> <span data-ttu-id="05089-144">이 인증서는 무료로 제공 되며 컴퓨터에서 스크립트를 작성, 서명 및 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-144">This certificate is free of charge and enables you to write, sign, and run scripts on your computer.</span></span> <span data-ttu-id="05089-145">그러나 자체 서명 된 인증서로 서명 된 스크립트는 다른 컴퓨터에서 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-145">However, a script signed by a self-signed certificate will not run on other computers.</span></span>

<span data-ttu-id="05089-146">일반적으로 자체 서명 된 인증서를 사용 하 여 사용자가 직접 작성 하는 스크립트에 서명 하 고 안전 하 게 확인 한 다른 원본에서 가져온 스크립트에 서명 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-146">Typically, you would use a self-signed certificate only to sign scripts that you write for your own use and to sign scripts that you get from other sources that you have verified to be safe.</span></span> <span data-ttu-id="05089-147">기업 내 에서도 공유 되는 스크립트에는 적합 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-147">It is not appropriate for scripts that will be shared, even within an enterprise.</span></span>

<span data-ttu-id="05089-148">자체 서명 된 인증서를 만드는 경우 인증서에서 강력한 개인 키 보호를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-148">If you create a self-signed certificate, be sure to enable strong private key protection on your certificate.</span></span> <span data-ttu-id="05089-149">그러면 악성 프로그램이 사용자를 대신해 스크립트에 서명 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-149">This prevents malicious programs from signing scripts on your behalf.</span></span> <span data-ttu-id="05089-150">지침은이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-150">The instructions are included at the end of this topic.</span></span>

## <a name="create-a-self-signed-certificate"></a><span data-ttu-id="05089-151">자체 서명된 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="05089-151">Create a self-signed certificate</span></span>

<span data-ttu-id="05089-152">에서 자체 서명 된 인증서를 만들려면 `New-SelfSignedCertificate` PKI 모듈에서 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-152">To create a self-signed certificate in use the `New-SelfSignedCertificate` cmdlet in the PKI module.</span></span> <span data-ttu-id="05089-153">이 모듈은 PowerShell 3.0에 도입 되었으며 Windows 8 및 Windows Server 2012에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-153">This module is introduced in PowerShell 3.0 and is included in Windows 8 and Windows Server 2012.</span></span> <span data-ttu-id="05089-154">자세한 내용은 cmdlet에 대 한 도움말 항목을 참조 하세요 `New-SelfSignedCertificate` .</span><span class="sxs-lookup"><span data-stu-id="05089-154">For more information, see the help topic for the `New-SelfSignedCertificate` cmdlet.</span></span>

<span data-ttu-id="05089-155">이전 버전의 Windows에서 자체 서명 된 인증서를 만들려면 인증서 생성 도구를 사용 `MakeCert.exe` 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-155">To create a self-signed certificate in earlier versions of Windows, use the Certificate Creation tool `MakeCert.exe`.</span></span> <span data-ttu-id="05089-156">이 도구는 Microsoft .NET SDK (버전 1.1 이상) 및 Microsoft Windows SDK에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-156">This tool is included in the Microsoft .NET SDK (versions 1.1 and later) and in the Microsoft Windows SDK.</span></span>

<span data-ttu-id="05089-157">MakeCert.exe 도구의 구문 및 매개 변수 설명에 대 한 자세한 내용은 [인증서 생성 도구 (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05089-157">For more information about the syntax and the parameter descriptions of the MakeCert.exe tool, see [Certificate Creation Tool (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80)).</span></span>

<span data-ttu-id="05089-158">MakeCert.exe 도구를 사용 하 여 인증서를 만들려면 SDK 명령 프롬프트 창에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-158">To use the MakeCert.exe tool to create a certificate, run the following commands in an SDK Command Prompt window.</span></span>

<span data-ttu-id="05089-159">참고: 첫 번째 명령은 컴퓨터에 대 한 로컬 인증 기관을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05089-159">Note: The first command creates a local certification authority for your computer.</span></span> <span data-ttu-id="05089-160">두 번째 명령은 인증 기관에서 개인 인증서를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-160">The second command generates a personal certificate from the certification authority.</span></span>

<span data-ttu-id="05089-161">참고: 정확히 표시 된 대로 명령을 복사 하거나 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-161">Note: You can copy or type the commands exactly as they appear.</span></span> <span data-ttu-id="05089-162">인증서 이름을 변경할 수는 있지만 대체가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-162">No substitutions are necessary, although you can change the certificate name.</span></span>

```powershell
makecert -n "CN=PowerShell Local Certificate Root" -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer `
-ss Root -sr localMachine

makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

<span data-ttu-id="05089-163">MakeCert.exe 도구는 개인 키 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-163">The MakeCert.exe tool will prompt you for a private key password.</span></span> <span data-ttu-id="05089-164">암호는 사용자의 동의 없이 인증서를 사용 하거나 액세스할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-164">The password ensures that no one can use or access the certificate without your consent.</span></span>
<span data-ttu-id="05089-165">기억할 수 있는 암호를 만들고 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-165">Create and enter a password that you can remember.</span></span> <span data-ttu-id="05089-166">이 암호는 나중에 인증서를 검색 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-166">You will use this password later to retrieve the certificate.</span></span>

<span data-ttu-id="05089-167">인증서가 올바르게 생성 되었는지 확인 하려면 다음 명령을 사용 하 여 컴퓨터의 인증서 저장소에 있는 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="05089-167">To verify that the certificate was generated correctly, use the following command to get the certificate in the certificate store on the computer.</span></span> <span data-ttu-id="05089-168">파일 시스템 디렉터리에서 인증서 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-168">You will not find a certificate file in the file system directory.</span></span>

<span data-ttu-id="05089-169">PowerShell 프롬프트에서 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-169">At the PowerShell prompt, type:</span></span>

```powershell
Get-ChildItem cert:\CurrentUser\my -codesigning
```

<span data-ttu-id="05089-170">이 명령은 PowerShell 인증서 공급자를 사용 하 여 인증서에 대 한 정보를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-170">This command uses the PowerShell Certificate provider to view information about the certificate.</span></span>

<span data-ttu-id="05089-171">인증서를 만든 경우 출력에는 다음과 같은 디스플레이에서 인증서를 식별 하는 **지문이** 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05089-171">If the certificate was created, the output shows the **thumbprint** that identifies the certificate in a display that resembles the following:</span></span>

```Output
Directory: Microsoft.PowerShell.Security\Certificate::CurrentUser\My

Thumbprint                                Subject
----------                                -------
4D4917CB140714BA5B81B96E0B18AAF2C4564FDF  CN=PowerShell User ]
```

## <a name="sign-a-script"></a><span data-ttu-id="05089-172">스크립트 서명</span><span class="sxs-lookup"><span data-stu-id="05089-172">Sign a script</span></span>

<span data-ttu-id="05089-173">자체 서명 된 인증서를 만든 후 스크립트에 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-173">After you create a self-signed certificate, you can sign scripts.</span></span> <span data-ttu-id="05089-174">**AllSigned** 실행 정책을 사용 하는 경우 스크립트에 서명 하면 사용자의 컴퓨터에서 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-174">If you use the **AllSigned** execution policy, signing a script permits you to run the script on your computer.</span></span>

<span data-ttu-id="05089-175">다음 샘플 스크립트는 `Add-Signature.ps1` 스크립트에 서명 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-175">The following sample script, `Add-Signature.ps1`, signs a script.</span></span> <span data-ttu-id="05089-176">그러나 **AllSigned** 실행 정책을 사용 하는 경우 `Add-Signature.ps1` 스크립트를 실행 하기 전에 서명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-176">However, if you are using the **AllSigned** execution policy, you must sign the `Add-Signature.ps1` script before you run it.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05089-177">ASCII 또는 UTF8NoBOM 인코딩을 사용 하 여 스크립트를 저장 해야 합니다. 다른 인코딩을 사용 하는 스크립트 파일에 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-177">The script must be saved using ASCII or UTF8NoBOM encoding.You can sign a script file that uses a different encoding.</span></span> <span data-ttu-id="05089-178">하지만 스크립트가 실행 되지 않거나 스크립트를 포함 하는 모듈을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-178">But the script fails to run or the module containing the script fails to import.</span></span>

<span data-ttu-id="05089-179">이 스크립트를 사용 하려면 텍스트 파일에 다음 텍스트를 복사 하 고 이름을로 `Add-Signature.ps1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-179">To use this script, copy the following text into a text file, and name it `Add-Signature.ps1`.</span></span>

```powershell
## Signs a file
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

<span data-ttu-id="05089-180">스크립트 파일에 서명 하려면 `Add-Signature.ps1` PowerShell 명령 프롬프트에서 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-180">To sign the `Add-Signature.ps1` script file, type the following commands at the PowerShell command prompt:</span></span>

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

<span data-ttu-id="05089-181">스크립트가 서명 된 후 로컬 컴퓨터에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-181">After the script is signed, you can run it on the local computer.</span></span> <span data-ttu-id="05089-182">그러나 PowerShell 실행 정책에 신뢰할 수 있는 기관의 디지털 서명이 필요한 컴퓨터에서는 스크립트가 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-182">However, the script will not run on computers on which the PowerShell execution policy requires a digital signature from a trusted authority.</span></span> <span data-ttu-id="05089-183">시도 하면 PowerShell에서 다음과 같은 오류 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-183">If you try, PowerShell displays the following error message:</span></span>

```Output
The file C:\remote_file.ps1 cannot be loaded. The signature of the
certificate cannot be verified.
At line:1 char:15
+ .\ remote_file.ps1 <<<<
```

<span data-ttu-id="05089-184">작성 하지 않은 스크립트를 실행할 때 PowerShell에서이 메시지가 표시 되는 경우 서명 되지 않은 스크립트를 처리 하는 것 처럼 파일을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-184">If PowerShell displays this message when you run a script that you did not write, treat the file as you would treat any unsigned script.</span></span> <span data-ttu-id="05089-185">코드를 검토 하 여 스크립트를 신뢰할 수 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-185">Review the code to determine whether you can trust the script.</span></span>

## <a name="enable-strong-private-key-protection-for-your-certificate"></a><span data-ttu-id="05089-186">인증서에 대해 강력한 개인 키 보호 사용</span><span class="sxs-lookup"><span data-stu-id="05089-186">Enable strong private key protection for your certificate</span></span>

<span data-ttu-id="05089-187">컴퓨터에 개인 인증서가 있는 경우 악성 프로그램은 사용자를 대신해 스크립트에 서명 하 여 PowerShell을 실행 하도록 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-187">If you have a private certificate on your computer, malicious programs might be able to sign scripts on your behalf, which authorizes PowerShell to run them.</span></span>

<span data-ttu-id="05089-188">사용자를 대신해 자동 서명을 방지 하려면 인증서 관리자를 사용 `Certmgr.exe` 하 여 서명 인증서를 파일로 내보냅니다 `.pfx` .</span><span class="sxs-lookup"><span data-stu-id="05089-188">To prevent automated signing on your behalf, use Certificate Manager `Certmgr.exe` to export your signing certificate to a `.pfx` file.</span></span> <span data-ttu-id="05089-189">인증서 관리자는 Microsoft .NET SDK, Microsoft Windows SDK 및 internet Explorer에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-189">Certificate Manager is included in the Microsoft .NET SDK, the Microsoft Windows SDK, and in internet Explorer.</span></span>

<span data-ttu-id="05089-190">인증서를 내보내려면:</span><span class="sxs-lookup"><span data-stu-id="05089-190">To export the certificate:</span></span>

1. <span data-ttu-id="05089-191">인증서 관리자를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-191">Start Certificate Manager.</span></span>
2. <span data-ttu-id="05089-192">PowerShell 로컬 인증서 루트에서 발급 한 인증서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-192">Select the certificate issued by PowerShell Local Certificate Root.</span></span>
3. <span data-ttu-id="05089-193">내보내기를 클릭 하 여 인증서 내보내기 마법사를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-193">Click Export to start the Certificate Export Wizard.</span></span>
4. <span data-ttu-id="05089-194">"예, 개인 키를 내보냅니다."를 선택 하 고 다음을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-194">Select "Yes, export the private key", and then click Next.</span></span>
5. <span data-ttu-id="05089-195">"강력한 보호 사용"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-195">Select "Enable strong protection."</span></span>
6. <span data-ttu-id="05089-196">암호를 입력 한 다음 다시 입력 하 여 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-196">Type a password, and then type it again to confirm.</span></span>
7. <span data-ttu-id="05089-197">.Pfx 파일 이름 확장명을 가진 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-197">Type a file name that has the .pfx file name extension.</span></span>
8. <span data-ttu-id="05089-198">마침을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-198">Click Finish.</span></span>

<span data-ttu-id="05089-199">인증서를 다시 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="05089-199">To re-import the certificate:</span></span>

1. <span data-ttu-id="05089-200">인증서 관리자를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-200">Start Certificate Manager.</span></span>
2. <span data-ttu-id="05089-201">가져오기를 클릭 하 여 인증서 가져오기 마법사를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-201">Click Import to start the Certificate Import Wizard.</span></span>
3. <span data-ttu-id="05089-202">내보내기 프로세스 중에 만든 .pfx 파일의 위치를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="05089-202">Open to the location of the .pfx file that you created during the export process.</span></span>
4. <span data-ttu-id="05089-203">암호 페이지에서 "강력한 개인 키 보호 사용"을 선택 하 고 내보내기 프로세스 중에 할당 한 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-203">On the Password page, select "Enable strong private key protection", and then enter the password that you assigned during the export process.</span></span>
5. <span data-ttu-id="05089-204">개인 인증서 저장소를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-204">Select the Personal certificate store.</span></span>
6. <span data-ttu-id="05089-205">마침을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-205">Click Finish.</span></span>

## <a name="prevent-the-signature-from-expiring"></a><span data-ttu-id="05089-206">서명이 만료 되지 않도록 방지</span><span class="sxs-lookup"><span data-stu-id="05089-206">Prevent the signature from expiring</span></span>

<span data-ttu-id="05089-207">스크립트의 디지털 서명은 서명 인증서가 만료 될 때까지 유효 하거나, 타임 스탬프 서버에서 서명 인증서가 유효한 동안 스크립트가 서명 되었는지 확인할 수 있을 때까지 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="05089-207">The digital signature in a script is valid until the signing certificate expires or as long as a timestamp server can verify that the script was signed while the signing certificate was valid.</span></span>

<span data-ttu-id="05089-208">대부분의 서명 인증서는 1 년 동안만 유효 하므로 타임 스탬프 서버를 사용 하면 사용자가 스크립트를 사용 하 여 많은 연도를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05089-208">Because most signing certificates are valid for one year only, using a time stamp server ensures that users can use your script for many years to come.</span></span>

## <a name="see-also"></a><span data-ttu-id="05089-209">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05089-209">See also</span></span>

[<span data-ttu-id="05089-210">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="05089-210">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="05089-211">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="05089-211">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="05089-212">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="05089-212">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="05089-213">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="05089-213">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="05089-214">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="05089-214">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

<span data-ttu-id="05089-215">[코드 서명 소개](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="05089-215">[Introduction to Code Signing](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span></span>

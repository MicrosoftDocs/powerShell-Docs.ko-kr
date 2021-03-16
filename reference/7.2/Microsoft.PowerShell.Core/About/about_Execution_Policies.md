---
description: PowerShell 실행 정책에 대해 설명 하 고 관리 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 1a2b8458b39233f96d47a52e3fea21b31e9b3c42
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603303"
---
# <a name="about-execution-policies"></a><span data-ttu-id="10fdb-103">실행 정책 정보</span><span class="sxs-lookup"><span data-stu-id="10fdb-103">About Execution Policies</span></span>

## <a name="short-description"></a><span data-ttu-id="10fdb-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="10fdb-104">Short Description</span></span>
<span data-ttu-id="10fdb-105">PowerShell 실행 정책에 대해 설명 하 고 관리 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-105">Describes the PowerShell execution policies and explains how to manage them.</span></span>

## <a name="long-description"></a><span data-ttu-id="10fdb-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="10fdb-106">Long Description</span></span>

<span data-ttu-id="10fdb-107">PowerShell의 실행 정책은 PowerShell에서 구성 파일을 로드 하 고 스크립트를 실행 하는 조건을 제어 하는 안전 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-107">PowerShell's execution policy is a safety feature that controls the conditions under which PowerShell loads configuration files and runs scripts.</span></span> <span data-ttu-id="10fdb-108">이 기능은 악의적인 스크립트의 실행을 방지 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-108">This feature helps prevent the execution of malicious scripts.</span></span>

<span data-ttu-id="10fdb-109">Windows 컴퓨터에서 로컬 컴퓨터, 현재 사용자 또는 특정 세션에 대 한 실행 정책을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-109">On a Windows computer you can set an execution policy for the local computer, for the current user, or for a particular session.</span></span> <span data-ttu-id="10fdb-110">그룹 정책 설정을 사용 하 여 컴퓨터 및 사용자에 대 한 실행 정책을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-110">You can also use a Group Policy setting to set execution policies for computers and users.</span></span>

<span data-ttu-id="10fdb-111">로컬 컴퓨터 및 현재 사용자에 대 한 실행 정책이 레지스트리에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-111">Execution policies for the local computer and current user are stored in the registry.</span></span> <span data-ttu-id="10fdb-112">PowerShell 프로필에서 실행 정책을 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-112">You don't need to set execution policies in your PowerShell profile.</span></span>
<span data-ttu-id="10fdb-113">특정 세션에 대 한 실행 정책은 메모리에만 저장 되며 세션을 닫으면 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-113">The execution policy for a particular session is stored only in memory and is lost when the session is closed.</span></span>

<span data-ttu-id="10fdb-114">실행 정책은 사용자 작업을 제한 하는 보안 시스템이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-114">The execution policy isn't a security system that restricts user actions.</span></span> <span data-ttu-id="10fdb-115">예를 들어 사용자는 스크립트를 실행할 수 없는 경우 명령줄에서 스크립트 내용을 입력 하 여 정책을 쉽게 우회할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-115">For example, users can easily bypass a policy by typing the script contents at the command line when they cannot run a script.</span></span> <span data-ttu-id="10fdb-116">대신, 실행 정책은 사용자가 기본 규칙을 설정 하 고 실수로 위반 하지 않도록 방지 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-116">Instead, the execution policy helps users to set basic rules and prevents them from violating them unintentionally.</span></span>

<span data-ttu-id="10fdb-117">비 Windows 컴퓨터의 기본 실행 정책은 **무제한** 이며 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-117">On non-Windows computers, the default execution policy is **Unrestricted** and cannot be changed.</span></span> <span data-ttu-id="10fdb-118">`Set-ExecutionPolicy`Cmdlet을 사용할 수 있지만 PowerShell에서 지원 되지 않는 콘솔 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-118">The `Set-ExecutionPolicy` cmdlet is available, but PowerShell displays a console message that it's not supported.</span></span> <span data-ttu-id="10fdb-119">는 `Get-ExecutionPolicy` windows가 아닌 플랫폼에서 **무제한** 을 반환 하지만, 이러한 플랫폼은 windows 보안 영역을 구현 하지 않기 때문에이 동작은 **무시** 와 매우 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-119">While `Get-ExecutionPolicy` returns **Unrestricted** on non-Windows platforms, the behavior really matches **Bypass** because those platforms do not implement the Windows Security Zones.</span></span>

## <a name="powershell-execution-policies"></a><span data-ttu-id="10fdb-120">PowerShell 실행 정책</span><span class="sxs-lookup"><span data-stu-id="10fdb-120">PowerShell execution policies</span></span>

<span data-ttu-id="10fdb-121">이러한 정책을 적용 하는 것은 Windows 플랫폼 에서만 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-121">Enforcement of these policies only occurs on Windows platforms.</span></span> <span data-ttu-id="10fdb-122">PowerShell 실행 정책은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-122">The PowerShell execution policies are as follows:</span></span>

### <a name="allsigned"></a><span data-ttu-id="10fdb-123">AllSigned</span><span class="sxs-lookup"><span data-stu-id="10fdb-123">AllSigned</span></span>

- <span data-ttu-id="10fdb-124">스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-124">Scripts can run.</span></span>
- <span data-ttu-id="10fdb-125">로컬 컴퓨터에서 작성하는 스크립트를 포함하여 모든 스크립트와 구성 파일에 신뢰할 수 있는 판매자의 서명이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-125">Requires that all scripts and configuration files be signed by a trusted publisher, including scripts that you write on the local computer.</span></span>
- <span data-ttu-id="10fdb-126">아직 신뢰할 수 있거나 신뢰할 수 없는 것으로 분류 하지 않은 게시자의 스크립트를 실행 하기 전에 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-126">Prompts you before running scripts from publishers that you haven't yet classified as trusted or untrusted.</span></span>
- <span data-ttu-id="10fdb-127">서명 되었지만 악의적인 스크립트를 실행 하는 위험</span><span class="sxs-lookup"><span data-stu-id="10fdb-127">Risks running signed, but malicious, scripts.</span></span>

### <a name="bypass"></a><span data-ttu-id="10fdb-128">바이패스</span><span class="sxs-lookup"><span data-stu-id="10fdb-128">Bypass</span></span>

- <span data-ttu-id="10fdb-129">아무것도 차단되지 않으며 경고 또는 프롬프트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-129">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="10fdb-130">이 실행 정책은 powershell 스크립트가 대규모 응용 프로그램에 기본 제공 되는 구성 또는 PowerShell이 자체 보안 모델을 포함 하는 프로그램의 기반이 되는 구성에 맞게 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-130">This execution policy is designed for configurations in which a PowerShell script is built in to a larger application or for configurations in which PowerShell is the foundation for a program that has its own security model.</span></span>

### <a name="default"></a><span data-ttu-id="10fdb-131">기본값</span><span class="sxs-lookup"><span data-stu-id="10fdb-131">Default</span></span>

- <span data-ttu-id="10fdb-132">기본 실행 정책을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-132">Sets the default execution policy.</span></span>
- <span data-ttu-id="10fdb-133">Windows 클라이언트에 대해 **제한** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-133">**Restricted** for Windows clients.</span></span>
- <span data-ttu-id="10fdb-134">Windows 서버에 대 한 **RemoteSigned** .</span><span class="sxs-lookup"><span data-stu-id="10fdb-134">**RemoteSigned** for Windows servers.</span></span>

### <a name="remotesigned"></a><span data-ttu-id="10fdb-135">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="10fdb-135">RemoteSigned</span></span>

- <span data-ttu-id="10fdb-136">Windows server 컴퓨터에 대 한 기본 실행 정책입니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-136">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="10fdb-137">스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-137">Scripts can run.</span></span>
- <span data-ttu-id="10fdb-138">전자 메일 및 인스턴트 메시징 프로그램을 포함 하는 인터넷에서 다운로드 한 스크립트 및 구성 파일에 신뢰할 수 있는 게시자의 디지털 서명이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-138">Requires a digital signature from a trusted publisher on scripts and configuration files that are downloaded from the internet which includes email and instant messaging programs.</span></span>
- <span data-ttu-id="10fdb-139">로컬 컴퓨터에 작성 되 고 인터넷에서 다운로드 되지 않은 스크립트에 디지털 서명이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-139">Doesn't require digital signatures on scripts that are written on the local computer and not downloaded from the internet.</span></span>
- <span data-ttu-id="10fdb-140">Cmdlet을 사용 하는 등의 방법으로 스크립트가 차단 해제 된 경우 인터넷에서 다운로드 되 고 서명 되지 않은 스크립트를 실행 합니다 `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="10fdb-140">Runs scripts that are downloaded from the internet and not signed, if the scripts are unblocked, such as by using the `Unblock-File` cmdlet.</span></span>
- <span data-ttu-id="10fdb-141">인터넷 및 서명 된 스크립트 이외의 원본에서 서명 되지 않은 스크립트를 실행 하는 위험 (악성이 될 수 있음)</span><span class="sxs-lookup"><span data-stu-id="10fdb-141">Risks running unsigned scripts from sources other than the internet and signed scripts that could be malicious.</span></span>

### <a name="restricted"></a><span data-ttu-id="10fdb-142">제한</span><span class="sxs-lookup"><span data-stu-id="10fdb-142">Restricted</span></span>

- <span data-ttu-id="10fdb-143">Windows 클라이언트 컴퓨터에 대 한 기본 실행 정책입니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-143">The default execution policy for Windows client computers.</span></span>
- <span data-ttu-id="10fdb-144">는 개별 명령을 허용 하지만 스크립트를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-144">Permits individual commands, but does not allow scripts.</span></span>
- <span data-ttu-id="10fdb-145">서식 지정 및 구성 파일 ( `.ps1xml` ), 모듈 스크립트 파일 ( `.psm1` ) 및 PowerShell 프로필 ()을 비롯 한 모든 스크립트 파일의 실행을 방지 `.ps1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-145">Prevents running of all script files, including formatting and configuration files (`.ps1xml`), module script files (`.psm1`), and PowerShell profiles (`.ps1`).</span></span>

### <a name="undefined"></a><span data-ttu-id="10fdb-146">정의되지 않음</span><span class="sxs-lookup"><span data-stu-id="10fdb-146">Undefined</span></span>

- <span data-ttu-id="10fdb-147">현재 범위에 설정 된 실행 정책이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-147">There is no execution policy set in the current scope.</span></span>
- <span data-ttu-id="10fdb-148">모든 범위의 실행 정책이 **정의 되지 않은** 경우에는 windows 클라이언트와 windows Server의 **RemoteSigned** 에 대 한 유효 실행 정책이 **제한** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-148">If the execution policy in all scopes is **Undefined**, the effective execution policy is **Restricted** for Windows clients and **RemoteSigned** for Windows Server.</span></span>

### <a name="unrestricted"></a><span data-ttu-id="10fdb-149">제한 없음</span><span class="sxs-lookup"><span data-stu-id="10fdb-149">Unrestricted</span></span>

- <span data-ttu-id="10fdb-150">비 Windows 컴퓨터에 대 한 기본 실행 정책은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-150">The default execution policy for non-Windows computers and cannot be changed.</span></span>
- <span data-ttu-id="10fdb-151">서명 되지 않은 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-151">Unsigned scripts can run.</span></span> <span data-ttu-id="10fdb-152">악의적인 스크립트를 실행할 위험이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-152">There is a risk of running malicious scripts.</span></span>
- <span data-ttu-id="10fdb-153">로컬 인트라넷 영역에서 가져오지 않은 스크립트 및 구성 파일을 실행 하기 전에 사용자에 게 경고 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-153">Warns the user before running scripts and configuration files that are not from the local intranet zone.</span></span>

> [!NOTE]
> <span data-ttu-id="10fdb-154">Unc (범용 명명 규칙) 경로를 인터넷 경로에서 구분 하지 않는 시스템에서는 UNC 경로에 의해 식별 되는 스크립트를 **RemoteSigned** 실행 정책으로 실행 하도록 허용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-154">On systems that do not distinguish Universal Naming Convention (UNC) paths from internet paths, scripts that are identified by a UNC path might not be permitted to run with the **RemoteSigned** execution policy.</span></span>

## <a name="execution-policy-scope"></a><span data-ttu-id="10fdb-155">실행 정책 범위</span><span class="sxs-lookup"><span data-stu-id="10fdb-155">Execution policy scope</span></span>

<span data-ttu-id="10fdb-156">특정 범위에만 적용 되는 실행 정책을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-156">You can set an execution policy that is effective only in a particular scope.</span></span>

<span data-ttu-id="10fdb-157">**범위** 에 대 한 유효한 값은 **MachinePolicy**, **userpolicy**, **Process**, **CurrentUser** 및 **LocalMachine** 입니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-157">The valid values for **Scope** are **MachinePolicy**, **UserPolicy**, **Process**, **CurrentUser**, and **LocalMachine**.</span></span> <span data-ttu-id="10fdb-158">실행 정책을 설정할 때 기본값은 **LocalMachine** 입니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-158">**LocalMachine** is the default when setting an execution policy.</span></span>

<span data-ttu-id="10fdb-159">**범위** 값은 우선 순위에 따라 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-159">The **Scope** values are listed in precedence order.</span></span> <span data-ttu-id="10fdb-160">더 제한적인 정책이 더 낮은 우선 순위로 설정 된 경우에도 우선 순위가 높은 정책은 현재 세션에서 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-160">The policy that takes precedence is effective in the current session, even if a more restrictive policy was set at a lower level of precedence.</span></span>

<span data-ttu-id="10fdb-161">자세한 내용은 [set-executionpolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="10fdb-161">For more information, see [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).</span></span>

### <a name="machinepolicy"></a><span data-ttu-id="10fdb-162">MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="10fdb-162">MachinePolicy</span></span>

<span data-ttu-id="10fdb-163">컴퓨터의 모든 사용자에 대해 그룹 정책 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-163">Set by a Group Policy for all users of the computer.</span></span>

### <a name="userpolicy"></a><span data-ttu-id="10fdb-164">UserPolicy</span><span class="sxs-lookup"><span data-stu-id="10fdb-164">UserPolicy</span></span>

<span data-ttu-id="10fdb-165">컴퓨터의 현재 사용자에 대 한 그룹 정책 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-165">Set by a Group Policy for the current user of the computer.</span></span>

### <a name="process"></a><span data-ttu-id="10fdb-166">프로세스</span><span class="sxs-lookup"><span data-stu-id="10fdb-166">Process</span></span>

<span data-ttu-id="10fdb-167">**프로세스** 범위는 현재 PowerShell 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-167">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="10fdb-168">실행 정책은 레지스트리가 아닌 환경 변수에 저장 됩니다 `$env:PSExecutionPolicyPreference` .</span><span class="sxs-lookup"><span data-stu-id="10fdb-168">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="10fdb-169">PowerShell 세션이 닫히면 변수와 값이 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-169">When the PowerShell session is closed, the variable and value are deleted.</span></span>

### <a name="currentuser"></a><span data-ttu-id="10fdb-170">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="10fdb-170">CurrentUser</span></span>

<span data-ttu-id="10fdb-171">실행 정책이 현재 사용자에게만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-171">The execution policy affects only the current user.</span></span> <span data-ttu-id="10fdb-172">**HKEY_CURRENT_USER** 레지스트리 하위 키에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-172">It's stored in the **HKEY_CURRENT_USER** registry subkey.</span></span>

### <a name="localmachine"></a><span data-ttu-id="10fdb-173">LocalMachine</span><span class="sxs-lookup"><span data-stu-id="10fdb-173">LocalMachine</span></span>

<span data-ttu-id="10fdb-174">실행 정책은 현재 컴퓨터의 모든 사용자에 게 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-174">The execution policy affects all users on the current computer.</span></span> <span data-ttu-id="10fdb-175">**HKEY_LOCAL_MACHINE** 레지스트리 하위 키에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-175">It's stored in the **HKEY_LOCAL_MACHINE** registry subkey.</span></span>

## <a name="managing-the-execution-policy-with-powershell"></a><span data-ttu-id="10fdb-176">PowerShell을 사용 하 여 실행 정책 관리</span><span class="sxs-lookup"><span data-stu-id="10fdb-176">Managing the execution policy with PowerShell</span></span>

<span data-ttu-id="10fdb-177">현재 PowerShell 세션의 유효 실행 정책을 가져오려면 cmdlet을 사용 합니다 `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="10fdb-177">To get the effective execution policy for the current PowerShell session, use the `Get-ExecutionPolicy` cmdlet.</span></span>

<span data-ttu-id="10fdb-178">다음 명령은 유효한 실행 정책을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-178">The following command gets the effective execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="10fdb-179">현재 세션에 영향을 주는 모든 실행 정책을 가져오고 우선 순위에 따라 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-179">To get all of the execution policies that affect the current session and display them in precedence order:</span></span>

```powershell
Get-ExecutionPolicy -List
```

<span data-ttu-id="10fdb-180">결과는 다음 예제 출력과 유사 하 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-180">The result looks similar to the following sample output:</span></span>

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       AllSigned
```

<span data-ttu-id="10fdb-181">이 경우 현재 사용자에 대 한 실행 정책이 로컬 컴퓨터에 설정 된 실행 정책 보다 우선적으로 적용 되기 때문에 유효한 실행 정책이 **RemoteSigned** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-181">In this case, the effective execution policy is **RemoteSigned** because the execution policy for the current user takes precedence over the execution policy set for the local computer.</span></span>

<span data-ttu-id="10fdb-182">특정 범위에 대 한 실행 정책을 설정 하려면의 **scope** 매개 변수를 사용 `Get-ExecutionPolicy` 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-182">To get the execution policy set for a particular scope, use the **Scope** parameter of `Get-ExecutionPolicy`.</span></span>

<span data-ttu-id="10fdb-183">예를 들어 다음 명령은 **CurrentUser** 범위에 대 한 실행 정책을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-183">For example, the following command gets the execution policy for the **CurrentUser** scope:</span></span>

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a><span data-ttu-id="10fdb-184">실행 정책 변경</span><span class="sxs-lookup"><span data-stu-id="10fdb-184">Change the execution policy</span></span>

<span data-ttu-id="10fdb-185">Windows 컴퓨터에서 PowerShell 실행 정책을 변경 하려면 cmdlet을 사용 합니다 `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="10fdb-185">To change the PowerShell execution policy on your Windows computer, use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="10fdb-186">변경 내용은 즉시 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-186">The change is effective immediately.</span></span> <span data-ttu-id="10fdb-187">PowerShell을 다시 시작할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-187">You don't need to restart PowerShell.</span></span>

<span data-ttu-id="10fdb-188">**LocalMachine** 또는 **CurrentUser** 범위에 대 한 실행 정책을 설정 하면 변경 내용이 레지스트리에 저장 되 고 다시 변경 될 때까지 유효 하 게 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-188">If you set the execution policy for the scopes **LocalMachine** or the **CurrentUser**, the change is saved in the registry and remains effective until you change it again.</span></span>

<span data-ttu-id="10fdb-189">**프로세스** 범위에 대 한 실행 정책을 설정 하면 레지스트리에 저장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-189">If you set the execution policy for the **Process** scope, it's not saved in the registry.</span></span> <span data-ttu-id="10fdb-190">실행 정책은 현재 프로세스와 모든 자식 프로세스가 닫힐 때까지 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-190">The execution policy is retained until the current process and any child processes are closed.</span></span>

> [!NOTE]
> <span data-ttu-id="10fdb-191">Windows Vista 이상 버전의 Windows에서 로컬 컴퓨터 **LocalMachine** 범위에 대 한 실행 정책을 변경 하는 명령을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-191">In Windows Vista and later versions of Windows, to run commands that change the execution policy for the local computer, **LocalMachine** scope, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="10fdb-192">실행 정책을 변경 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-192">To change your execution policy:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

<span data-ttu-id="10fdb-193">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="10fdb-193">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="10fdb-194">특정 범위에서 실행 정책을 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-194">To set the execution policy in a particular scope:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

<span data-ttu-id="10fdb-195">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="10fdb-195">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

<span data-ttu-id="10fdb-196">실행 정책을 변경 하는 명령은 성공 하지만 유효 실행 정책을 변경 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-196">A command to change an execution policy can succeed but still not change the effective execution policy.</span></span>

<span data-ttu-id="10fdb-197">예를 들어 로컬 컴퓨터에 대 한 실행 정책을 설정 하는 명령은 성공 하지만 현재 사용자의 실행 정책에 의해 재정의 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-197">For example, a command that sets the execution policy for the local computer can succeed but be overridden by the execution policy for the current user.</span></span>

### <a name="remove-the-execution-policy"></a><span data-ttu-id="10fdb-198">실행 정책 제거</span><span class="sxs-lookup"><span data-stu-id="10fdb-198">Remove the execution policy</span></span>

<span data-ttu-id="10fdb-199">특정 범위에 대 한 실행 정책을 제거 하려면 실행 정책을 **Undefined** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-199">To remove the execution policy for a particular scope, set the execution policy to **Undefined**.</span></span>

<span data-ttu-id="10fdb-200">예를 들어 로컬 컴퓨터의 모든 사용자에 대 한 실행 정책을 제거 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-200">For example, to remove the execution policy for all the users of the local computer:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

<span data-ttu-id="10fdb-201">**범위** 에 대 한 실행 정책을 제거 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-201">To remove the execution policy for a **Scope**:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

<span data-ttu-id="10fdb-202">어떤 범위에도 실행 정책이 설정 되지 않은 경우 유효한 실행 정책이 Windows 클라이언트의 기본값인로 **제한** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-202">If no execution policy is set in any scope, the effective execution policy is **Restricted**, which is the default for Windows clients.</span></span>

### <a name="set-a-different-policy-for-one-session"></a><span data-ttu-id="10fdb-203">한 세션에 대해 다른 정책 설정</span><span class="sxs-lookup"><span data-stu-id="10fdb-203">Set a different policy for one session</span></span>

<span data-ttu-id="10fdb-204">**pwsh.exe** 의 **set-executionpolicy** 매개 변수를 사용 하 여 새 PowerShell 세션의 실행 정책을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-204">You can use the **ExecutionPolicy** parameter of **pwsh.exe** to set an execution policy for a new PowerShell session.</span></span> <span data-ttu-id="10fdb-205">이 정책은 현재 세션 및 자식 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-205">The policy affects only the current session and child sessions.</span></span>

<span data-ttu-id="10fdb-206">새 세션에 대 한 실행 정책을 설정 하려면 명령줄에서 **cmd.exe** 또는 powershell과 같은 powershell을 시작한 후 **pwsh.exe** 의 **set-executionpolicy** 매개 변수를 사용 하 여 실행 정책을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-206">To set the execution policy for a new session, start PowerShell at the command line, such as **cmd.exe** or from PowerShell, and then use the **ExecutionPolicy** parameter of **pwsh.exe** to set the execution policy.</span></span>

<span data-ttu-id="10fdb-207">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="10fdb-207">For example:</span></span>

```powershell
pwsh.exe -ExecutionPolicy AllSigned
```

<span data-ttu-id="10fdb-208">설정 하는 실행 정책은 레지스트리에 저장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-208">The execution policy that you set isn't stored in the registry.</span></span> <span data-ttu-id="10fdb-209">대신, `$env:PSExecutionPolicyPreference` 환경 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-209">Instead, it's stored in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="10fdb-210">정책이 설정 된 세션을 닫으면 변수가 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-210">The variable is deleted when you close the session in which the policy is set.</span></span> <span data-ttu-id="10fdb-211">변수 값을 편집 하 여 정책을 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-211">You cannot change the policy by editing the variable value.</span></span>

<span data-ttu-id="10fdb-212">세션 중에 세션에 대해 설정 된 실행 정책이 로컬 컴퓨터 또는 현재 사용자의 레지스트리에 설정 된 실행 정책 보다 우선 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-212">During the session, the execution policy that is set for the session takes precedence over an execution policy that is set in the registry for the local computer or current user.</span></span> <span data-ttu-id="10fdb-213">그러나 그룹 정책를 사용 하 여 설정 된 실행 정책 보다 우선 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-213">However, it doesn't take precedence over the execution policy set by using a Group Policy.</span></span>

## <a name="use-group-policy-to-manage-execution-policy"></a><span data-ttu-id="10fdb-214">그룹 정책를 사용 하 여 실행 정책 관리</span><span class="sxs-lookup"><span data-stu-id="10fdb-214">Use Group Policy to Manage Execution Policy</span></span>

<span data-ttu-id="10fdb-215">그룹 정책 **스크립트 실행** 설정을 사용 하 여 엔터프라이즈의 컴퓨터에 대 한 실행 정책을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-215">You can use the **Turn on Script Execution** Group Policy setting to manage the execution policy of computers in your enterprise.</span></span> <span data-ttu-id="10fdb-216">그룹 정책 설정은 모든 범위에서 PowerShell에 설정 된 실행 정책을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-216">The Group Policy setting overrides the execution policies set in PowerShell in all scopes.</span></span>

<span data-ttu-id="10fdb-217">**스크립트 실행** 설정 정책 설정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-217">The **Turn on Script Execution** policy settings are as follows:</span></span>

- <span data-ttu-id="10fdb-218">**스크립트 실행** 을 사용 하지 않도록 설정 하면 스크립트가 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-218">If you disable **Turn on Script Execution**, scripts do not run.</span></span> <span data-ttu-id="10fdb-219">이는 **제한** 된 실행 정책과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-219">This is equivalent to the **Restricted** execution policy.</span></span>
- <span data-ttu-id="10fdb-220">**스크립트 실행** 을 사용 하도록 설정 하는 경우 실행 정책을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-220">If you enable **Turn on Script Execution**, you can select an execution policy.</span></span> <span data-ttu-id="10fdb-221">그룹 정책 설정은 다음 실행 정책 설정과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-221">The Group Policy settings are equivalent to the following execution policy settings:</span></span>

  | <span data-ttu-id="10fdb-222">그룹 정책</span><span class="sxs-lookup"><span data-stu-id="10fdb-222">Group Policy</span></span>                                  | <span data-ttu-id="10fdb-223">실행 정책</span><span class="sxs-lookup"><span data-stu-id="10fdb-223">Execution Policy</span></span> |
  | --------------------------------------------- | ---------------- |
  | <span data-ttu-id="10fdb-224">모든 스크립트 허용</span><span class="sxs-lookup"><span data-stu-id="10fdb-224">Allow all scripts</span></span>                             | <span data-ttu-id="10fdb-225">제한 없음</span><span class="sxs-lookup"><span data-stu-id="10fdb-225">Unrestricted</span></span>     |
  | <span data-ttu-id="10fdb-226">로컬 스크립트 및 원격 서명 된 스크립트 허용</span><span class="sxs-lookup"><span data-stu-id="10fdb-226">Allow local scripts and remote signed scripts</span></span> | <span data-ttu-id="10fdb-227">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="10fdb-227">RemoteSigned</span></span>     |
  | <span data-ttu-id="10fdb-228">서명 된 스크립트만 허용</span><span class="sxs-lookup"><span data-stu-id="10fdb-228">Allow only signed scripts</span></span>                     | <span data-ttu-id="10fdb-229">AllSigned</span><span class="sxs-lookup"><span data-stu-id="10fdb-229">AllSigned</span></span>        |

- <span data-ttu-id="10fdb-230">**설정 스크립트 실행** 이 구성 되지 않은 경우에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-230">If **Turn on Script Execution** is not configured, it has no effect.</span></span> <span data-ttu-id="10fdb-231">PowerShell에서 설정 된 실행 정책이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-231">The execution policy set in PowerShell is effective.</span></span>

<span data-ttu-id="10fdb-232">PowerShellExecutionPolicy 및 PowerShellExecutionPolicy 파일은 다음 경로에 그룹 정책 편집기의 컴퓨터 구성 및 사용자 구성 노드에 대 한 **스크립트 실행 정책 설정** 정책을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-232">The PowerShellExecutionPolicy.adm and PowerShellExecutionPolicy.admx files add the **Turn on Script Execution** policy to the Computer Configuration and User Configuration nodes in Group Policy Editor in the following paths.</span></span>

<span data-ttu-id="10fdb-233">Windows XP 및 Windows Server 2003:</span><span class="sxs-lookup"><span data-stu-id="10fdb-233">For Windows XP and Windows Server 2003:</span></span>

<span data-ttu-id="10fdb-234">관리 템플릿 \ PowerShell</span><span class="sxs-lookup"><span data-stu-id="10fdb-234">Administrative Templates\Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="10fdb-235">Windows Vista 이상 버전의 경우:</span><span class="sxs-lookup"><span data-stu-id="10fdb-235">For Windows Vista and later versions of Windows:</span></span>

<span data-ttu-id="10fdb-236">관리 Templates\Classic 관리 템플릿 </span><span class="sxs-lookup"><span data-stu-id="10fdb-236">Administrative Templates\Classic Administrative Templates</span></span>\
<span data-ttu-id="10fdb-237">Windows s PowerShell</span><span class="sxs-lookup"><span data-stu-id="10fdb-237">Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="10fdb-238">컴퓨터 구성 노드에서 설정 된 정책은 사용자 구성 노드에 설정 된 정책 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-238">Policies set in the Computer Configuration node take precedence over policies set in the User Configuration node.</span></span>

<span data-ttu-id="10fdb-239">자세한 내용은 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10fdb-239">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

### <a name="execution-policy-precedence"></a><span data-ttu-id="10fdb-240">실행 정책 우선 순위</span><span class="sxs-lookup"><span data-stu-id="10fdb-240">Execution policy precedence</span></span>

<span data-ttu-id="10fdb-241">세션에 대 한 유효한 실행 정책을 결정할 때 PowerShell은 다음 우선 순위에 따라 실행 정책을 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-241">When determining the effective execution policy for a session, PowerShell evaluates the execution policies in the following precedence order:</span></span>

- <span data-ttu-id="10fdb-242">그룹 정책: MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="10fdb-242">Group Policy: MachinePolicy</span></span>
- <span data-ttu-id="10fdb-243">그룹 정책: UserPolicy</span><span class="sxs-lookup"><span data-stu-id="10fdb-243">Group Policy: UserPolicy</span></span>
- <span data-ttu-id="10fdb-244">실행 정책: Process (or `pwsh.exe -ExecutionPolicy` )</span><span class="sxs-lookup"><span data-stu-id="10fdb-244">Execution Policy: Process (or `pwsh.exe -ExecutionPolicy`)</span></span>
- <span data-ttu-id="10fdb-245">실행 정책: CurrentUser</span><span class="sxs-lookup"><span data-stu-id="10fdb-245">Execution Policy: CurrentUser</span></span>
- <span data-ttu-id="10fdb-246">실행 정책: LocalMachine</span><span class="sxs-lookup"><span data-stu-id="10fdb-246">Execution Policy: LocalMachine</span></span>

## <a name="manage-signed-and-unsigned-scripts"></a><span data-ttu-id="10fdb-247">서명 및 서명 되지 않은 스크립트 관리</span><span class="sxs-lookup"><span data-stu-id="10fdb-247">Manage signed and unsigned scripts</span></span>

<span data-ttu-id="10fdb-248">Windows에서 Internet Explorer 및 Microsoft Edge와 같은 프로그램은 다운로드 된 파일에 대체 데이터 스트림을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-248">In Windows, programs like Internet Explorer and Microsoft Edge add an alternate data stream to files that are downloaded.</span></span> <span data-ttu-id="10fdb-249">이렇게 하면 파일이 "인터넷에서 제공"으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-249">This marks the file as "coming from the Internet".</span></span> <span data-ttu-id="10fdb-250">PowerShell 실행 정책이 **RemoteSigned** 인 경우 powershell은 전자 메일 및 인스턴트 메시징 프로그램을 포함 하는 인터넷에서 다운로드 한 서명 되지 않은 스크립트를 실행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-250">If your PowerShell execution policy is **RemoteSigned**, PowerShell won't run unsigned scripts that are downloaded from the internet which includes email and instant messaging programs.</span></span>

<span data-ttu-id="10fdb-251">스크립트에 서명 하거나 실행 정책을 변경 하지 않고 서명 되지 않은 스크립트를 실행 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-251">You can sign the script or elect to run an unsigned script without changing the execution policy.</span></span>

<span data-ttu-id="10fdb-252">PowerShell 3.0부터 cmdlet의 **Stream** 매개 변수를 사용 하 여 `Get-Item` 차단 된 파일이 인터넷에서 다운로드 되어 해당 파일을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-252">Beginning in PowerShell 3.0, you can use the **Stream** parameter of the `Get-Item` cmdlet to detect files that are blocked because they were downloaded from the internet.</span></span> <span data-ttu-id="10fdb-253">Cmdlet을 사용 `Unblock-File` 하 여 PowerShell에서 실행할 수 있도록 스크립트를 차단 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-253">Use the `Unblock-File` cmdlet to unblock the scripts so that you can run them in PowerShell.</span></span>

<span data-ttu-id="10fdb-254">자세한 내용은 [about_Signing](about_Signing.md), [항목 가져오기](xref:Microsoft.PowerShell.Management.Get-Item)및 [파일 차단 해제](xref:Microsoft.PowerShell.Utility.Unblock-File)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="10fdb-254">For more information, see [about_Signing](about_Signing.md), [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item), and [Unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File).</span></span>

> [!NOTE]
> <span data-ttu-id="10fdb-255">파일을 다운로드 하는 다른 방법은 인터넷 영역에서 가져온 파일을 표시 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-255">Other methods of downloading files may not mark the files as coming from the Internet Zone.</span></span> <span data-ttu-id="10fdb-256">일부 사례:</span><span class="sxs-lookup"><span data-stu-id="10fdb-256">Some examples include:</span></span>
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a><span data-ttu-id="10fdb-257">Windows Server Core 및 Window Nano Server에 대 한 실행 정책</span><span class="sxs-lookup"><span data-stu-id="10fdb-257">Execution policy on Windows Server Core and Window Nano Server</span></span>

<span data-ttu-id="10fdb-258">특정 조건에서 Windows Server Core 또는 Windows Nano Server에서 PowerShell 6을 실행 하면 다음 오류와 함께 실행 정책이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-258">When PowerShell 6 is run on Windows Server Core or Windows Nano Server under certain conditions, execution policies can fail with the following error:</span></span>

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="10fdb-259">PowerShell은 Windows Desktop Shell ()의 Api를 사용 하 여 `explorer.exe` 스크립트 파일 영역의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-259">PowerShell uses APIs in the Windows Desktop Shell (`explorer.exe`) to validate the Zone of a script file.</span></span> <span data-ttu-id="10fdb-260">Windows Shell은 windows Server Core 및 Windows Nano Server에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-260">The Windows Shell is not available on Windows Server Core and Windows Nano Server.</span></span>

<span data-ttu-id="10fdb-261">Windows 데스크톱 셸을 사용할 수 없거나 응답 하지 않는 경우 Windows 시스템에서이 오류를 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-261">You could also get this error on any Windows system if the Windows Desktop Shell is unavailable or unresponsive.</span></span> <span data-ttu-id="10fdb-262">예를 들어 로그온 하는 동안 Windows 데스크톱이 준비 되기 전에 PowerShell 로그온 스크립트가 실행을 시작할 수 있으며,이로 인해 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-262">For example, during sign on, a PowerShell logon script could start execution before the Windows Desktop is ready, resulting in failure.</span></span>

<span data-ttu-id="10fdb-263">**바이패스** 또는 **AllSigned** 실행 정책을 사용 하는 경우에는 문제를 방지 하는 영역 검사가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10fdb-263">Using an execution policy of **ByPass** or **AllSigned** does not require a Zone check which avoids the problem.</span></span>

## <a name="see-also"></a><span data-ttu-id="10fdb-264">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10fdb-264">See Also</span></span>

[<span data-ttu-id="10fdb-265">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="10fdb-265">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="10fdb-266">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="10fdb-266">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="10fdb-267">about_Signing</span><span class="sxs-lookup"><span data-stu-id="10fdb-267">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="10fdb-268">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="10fdb-268">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="10fdb-269">Get-Item</span><span class="sxs-lookup"><span data-stu-id="10fdb-269">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

[<span data-ttu-id="10fdb-270">Pwsh 콘솔 도움말</span><span class="sxs-lookup"><span data-stu-id="10fdb-270">Pwsh Console Help</span></span>](about_pwsh.md)

[<span data-ttu-id="10fdb-271">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="10fdb-271">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="10fdb-272">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="10fdb-272">Unblock-File</span></span>](xref:Microsoft.PowerShell.Utility.Unblock-File)

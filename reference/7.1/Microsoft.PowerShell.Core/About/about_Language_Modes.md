---
description: 언어 모드 및 PowerShell 세션에 미치는 영향을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: 0b94125574bc65359b264225bb6c64231c1052d7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220441"
---
# <a name="about-language-modes"></a><span data-ttu-id="cc405-104">언어 모드 정보</span><span class="sxs-lookup"><span data-stu-id="cc405-104">About Language Modes</span></span>

## <a name="short-description"></a><span data-ttu-id="cc405-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="cc405-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="cc405-106">언어 모드 및 PowerShell 세션에 미치는 영향을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-106">Explains language modes and their effect on PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="cc405-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="cc405-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="cc405-108">PowerShell 세션의 언어 모드에서는 세션에서 사용할 수 있는 PowerShell 언어 요소를 부분적으로 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-108">The language mode of a PowerShell session determines, in part, which elements of the PowerShell language can be used in the session.</span></span>

<span data-ttu-id="cc405-109">PowerShell은 다음과 같은 언어 모드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-109">PowerShell supports the following language modes:</span></span>

- <span data-ttu-id="cc405-110">FullLanguage</span><span class="sxs-lookup"><span data-stu-id="cc405-110">FullLanguage</span></span>
- <span data-ttu-id="cc405-111">ConstrainedLanguage (PowerShell 3.0에 도입 됨)</span><span class="sxs-lookup"><span data-stu-id="cc405-111">ConstrainedLanguage (introduced in PowerShell 3.0)</span></span>
- <span data-ttu-id="cc405-112">RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="cc405-112">RestrictedLanguage</span></span>
- <span data-ttu-id="cc405-113">NoLanguage</span><span class="sxs-lookup"><span data-stu-id="cc405-113">NoLanguage</span></span>

### <a name="what-is-a-language-mode"></a><span data-ttu-id="cc405-114">언어 모드는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="cc405-114">WHAT IS A LANGUAGE MODE?</span></span>

<span data-ttu-id="cc405-115">언어 모드는 세션에서 허용 되는 언어 요소를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-115">The language mode determines the language elements that are permitted in the session.</span></span>

<span data-ttu-id="cc405-116">언어 모드는 실제로 세션을 만드는 데 사용 되는 세션 구성 (또는 "끝점")의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-116">The language mode is actually a property of the session configuration (or "endpoint") that is used to create the session.</span></span> <span data-ttu-id="cc405-117">특정 세션 구성을 사용 하는 모든 세션에는 세션 구성의 언어 모드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-117">All sessions that use a particular session configuration have the language mode of the session configuration.</span></span>

<span data-ttu-id="cc405-118">모든 PowerShell 세션에는 cmdlet을 사용 하 여 만든 pssession `New-PSSession` , ComputerName 매개 변수를 사용 하는 임시 세션, powershell을 시작할 때 표시 되는 기본 세션 등의 언어 모드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-118">All PowerShell sessions have a language mode, including PSSessions that you create by using the `New-PSSession` cmdlet, temporary sessions that use the ComputerName parameter, and the default sessions that appear when you start PowerShell.</span></span>

<span data-ttu-id="cc405-119">원격 세션은 원격 컴퓨터의 세션 구성을 사용 하 여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-119">Remote sessions are created by using the session configurations on the remote computer.</span></span> <span data-ttu-id="cc405-120">세션 구성에 설정 된 언어 모드는 세션의 언어 모드를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-120">The language mode set in the session configuration determines the language mode of the session.</span></span> <span data-ttu-id="cc405-121">PSSession의 세션 구성을 지정 하려면 세션을 만드는 cmdlet의 ConfigurationName 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-121">To specify the session configuration of a PSSession, use the ConfigurationName parameter of cmdlets that create a session.</span></span>

### <a name="language-modes"></a><span data-ttu-id="cc405-122">언어 모드</span><span class="sxs-lookup"><span data-stu-id="cc405-122">LANGUAGE MODES</span></span>

<span data-ttu-id="cc405-123">이 섹션에서는 PowerShell 세션의 언어 모드에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-123">This section describes the language modes in PowerShell sessions.</span></span>

#### <a name="full-language-fulllanguage"></a><span data-ttu-id="cc405-124">전체 언어 (FullLanguage)</span><span class="sxs-lookup"><span data-stu-id="cc405-124">FULL LANGUAGE (FullLanguage)</span></span>

<span data-ttu-id="cc405-125">FullLanguage 모드는 세션의 모든 언어 요소를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-125">The FullLanguage mode permits all language elements in the session.</span></span>
<span data-ttu-id="cc405-126">FullLanguage는 Windows RT를 제외한 모든 Windows 버전에서 기본 세션의 기본 언어 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-126">FullLanguage is the default language mode for default sessions on all versions of Windows except for Windows RT.</span></span>

#### <a name="restricted-language-restrictedlanguage"></a><span data-ttu-id="cc405-127">제한 된 언어 (RestrictedLanguage)</span><span class="sxs-lookup"><span data-stu-id="cc405-127">RESTRICTED LANGUAGE (RestrictedLanguage)</span></span>

<span data-ttu-id="cc405-128">RestrictedLanguage 모드에서 사용자는 명령 (cmdlet, 함수, CIM 명령 및 워크플로)을 실행할 수 있지만 스크립트 블록을 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-128">In RestrictedLanguage mode, users may run commands (cmdlets, functions, CIM commands, and workflows) but are not permitted to use script blocks.</span></span>

<span data-ttu-id="cc405-129">기본적으로 RestrictedLanguage 모드에서는 다음 변수만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-129">By default, only the following variables are permitted in RestrictedLanguage mode:</span></span>

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

<span data-ttu-id="cc405-130">RestrictedLanguage 모드를 사용 하는 모듈 매니페스트는 다음과 같은 추가 변수도 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-130">Module manifests, which use RestrictedLanguage mode, permit the following additional variables as well:</span></span>

- `$PSScriptRoot`
- <span data-ttu-id="cc405-131">`$PSEdition` (PowerShell Core에서)</span><span class="sxs-lookup"><span data-stu-id="cc405-131">`$PSEdition` (in PowerShell Core)</span></span>
- <span data-ttu-id="cc405-132">`$EnabledExperimentalFeatures` (PowerShell Core에서)</span><span class="sxs-lookup"><span data-stu-id="cc405-132">`$EnabledExperimentalFeatures` (in PowerShell Core)</span></span>

<span data-ttu-id="cc405-133">다음 비교 연산자만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-133">Only the following comparison operators are permitted:</span></span>

- <span data-ttu-id="cc405-134">`-eq` 다릅니다</span><span class="sxs-lookup"><span data-stu-id="cc405-134">`-eq` (equal)</span></span>
- <span data-ttu-id="cc405-135">`-gt` (보다 큼)</span><span class="sxs-lookup"><span data-stu-id="cc405-135">`-gt` (greater-than)</span></span>
- <span data-ttu-id="cc405-136">`-lt` (보다 작음)</span><span class="sxs-lookup"><span data-stu-id="cc405-136">`-lt` (less-than)</span></span>

<span data-ttu-id="cc405-137">대입문, 속성 참조 및 메서드 호출은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-137">Assignment statements, property references, and method calls are not permitted.</span></span>

#### <a name="no-language-nolanguage"></a><span data-ttu-id="cc405-138">언어 없음 (NoLanguage)</span><span class="sxs-lookup"><span data-stu-id="cc405-138">NO LANGUAGE (NoLanguage)</span></span>

<span data-ttu-id="cc405-139">NoLanguage 모드는 API를 통해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-139">NoLanguage mode can only be used through the API.</span></span> <span data-ttu-id="cc405-140">NoLanguage 모드는 모든 형식의 스크립트 텍스트가 허용 되지 않음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-140">NoLanguage mode means no script text of any form is permitted.</span></span> <span data-ttu-id="cc405-141">이를 통해 구문 분석 되 고 실행 되는 PowerShell 스크립트의 조각을 보내는 **Addscript ()** 메서드를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-141">This precludes the use of the **AddScript()** method which sends fragments of PowerShell script to be parsed and executed.</span></span> <span data-ttu-id="cc405-142">파서를 통과 하지 않는 **Addcommand ()** 및 **addcommand ()** 만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-142">You can only use **AddCommand()** and **AddParameter()** which don't go through the parser.</span></span>

#### <a name="constrained-language-constrained-language"></a><span data-ttu-id="cc405-143">제약이 있는 언어 (제한 언어)</span><span class="sxs-lookup"><span data-stu-id="cc405-143">CONSTRAINED LANGUAGE (Constrained Language)</span></span>

<span data-ttu-id="cc405-144">ConstrainedLanguage 모드는 모든 cmdlet 및 모든 PowerShell 언어 요소를 허용 하지만 허용 된 형식을 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-144">The ConstrainedLanguage mode permits all cmdlets and all PowerShell language elements, but it limits permitted types.</span></span>

<span data-ttu-id="cc405-145">ConstrainedLanguage 모드는 Windows RT에서 UMCI (사용자 모드 코드 무결성)를 지원 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-145">ConstrainedLanguage mode is designed to support User Mode Code Integrity (UMCI) on Windows RT.</span></span> <span data-ttu-id="cc405-146">이 모드는 Windows RT에서 유일 하 게 지원 되는 언어 모드 이지만 지원 되는 모든 시스템에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-146">It is the only supported language mode on Windows RT, but it is available on all supported systems.</span></span>

<span data-ttu-id="cc405-147">UMCI는 Windows RT 기반 장치에 Microsoft 서명 및 Microsoft 인증 앱만 설치 하도록 허용 하 여 ARM 장치를 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-147">UMCI protects ARM devices by allowing only Microsoft-signed and Microsoft-certified apps to be installed on Windows RT-based devices.</span></span>
<span data-ttu-id="cc405-148">ConstrainedLanguage 모드를 사용 하면 사용자가 PowerShell을 사용 하 여 UMCI를 우회 하거나 위반할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-148">ConstrainedLanguage mode prevents users from using PowerShell to circumvent or violate UMCI.</span></span>

<span data-ttu-id="cc405-149">ConstrainedLanguage 모드의 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-149">The features of ConstrainedLanguage mode are as follows:</span></span>

- <span data-ttu-id="cc405-150">Windows 모듈의 모든 cmdlet 및 기타 UMCI 승인 된 cmdlet은 완전히 작동 하며, 명시 된 경우를 제외 하 고 시스템 리소스에 대 한 완전 한 액세스 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-150">All cmdlets in Windows modules, and other UMCI-approved cmdlets, are fully functional and have complete access to system resources, except as noted.</span></span>

- <span data-ttu-id="cc405-151">PowerShell 스크립트 언어의 모든 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-151">All elements of the PowerShell scripting language are permitted.</span></span>

- <span data-ttu-id="cc405-152">Windows에 포함 된 모든 모듈을 가져올 수 있으며, 모듈 내보내기가 세션에서 실행 하는 모든 명령을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-152">All modules included in Windows can be imported and all commands that the modules export run in the session.</span></span>

- <span data-ttu-id="cc405-153">PowerShell 워크플로에서 스크립트 워크플로 (PowerShell 언어로 작성 된 워크플로)를 작성 하 고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-153">In PowerShell Workflow, you can write and run script workflows (workflows written in the PowerShell language).</span></span> <span data-ttu-id="cc405-154">XAML 기반 워크플로는 지원 되지 않으므로를 사용 하는 등의 스크립트 워크플로에서는 XAML을 실행할 수 없습니다 `Invoke-Expression -Language XAML` .</span><span class="sxs-lookup"><span data-stu-id="cc405-154">XAML-based workflows are not supported and you cannot run XAML in a script workflow, such as by using `Invoke-Expression -Language XAML`.</span></span> <span data-ttu-id="cc405-155">또한 중첩 된 워크플로가 허용 되지만 워크플로는 다른 워크플로를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-155">Also, workflows cannot call other workflows, although nested workflows are permitted.</span></span>

- <span data-ttu-id="cc405-156">`Add-Type`Cmdlet은 서명 된 어셈블리를 로드할 수 있지만 임의의 c # 코드 또는 Win32 api는 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-156">The `Add-Type` cmdlet can load signed assemblies, but it cannot load arbitrary C# code or Win32 APIs.</span></span>

- <span data-ttu-id="cc405-157">이 `New-Object` cmdlet은 허용 되는 형식 (아래 참조)에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-157">The `New-Object` cmdlet can be used only on allowed types (listed below).</span></span>

- <span data-ttu-id="cc405-158">PowerShell에서 허용 되는 유형 (아래에 나열 됨)만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-158">Only allowed types (listed below) can be used in PowerShell.</span></span> <span data-ttu-id="cc405-159">다른 형식은 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-159">Other types are not permitted.</span></span>

- <span data-ttu-id="cc405-160">형식을 변환할 수 있지만 결과가 허용 되는 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-160">Type conversion is permitted, but only when the result is an allowed type.</span></span>

- <span data-ttu-id="cc405-161">문자열 입력을 형식으로 변환 하는 Cmdlet 매개 변수는 결과 형식이 허용 되는 형식인 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-161">Cmdlet parameters that convert string input to types work only when the resulting type is an allowed type.</span></span>

- <span data-ttu-id="cc405-162">**ToString ()** 메서드 및 허용 되는 형식 (아래 나열 됨)의 .net 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-162">The **ToString()** method and the .NET methods of allowed types (listed below) can be invoked.</span></span> <span data-ttu-id="cc405-163">다른 메서드는 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-163">Other methods cannot be invoked.</span></span>

- <span data-ttu-id="cc405-164">사용자는 허용 된 형식의 모든 속성을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-164">Users can get all properties of allowed types.</span></span> <span data-ttu-id="cc405-165">사용자는 코어 유형에만 속성 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-165">Users can set the values of properties only on Core types.</span></span> <span data-ttu-id="cc405-166">다음 COM 개체만 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-166">Only the following COM objects are permitted:</span></span>

  - <span data-ttu-id="cc405-167">**Scripting. 사전**</span><span class="sxs-lookup"><span data-stu-id="cc405-167">**Scripting.Dictionary**</span></span>
  - <span data-ttu-id="cc405-168">**Scripting.FileSystemObject**</span><span class="sxs-lookup"><span data-stu-id="cc405-168">**Scripting.FileSystemObject**</span></span>
  - <span data-ttu-id="cc405-169">**VBScript. RegExp**</span><span class="sxs-lookup"><span data-stu-id="cc405-169">**VBScript.RegExp**</span></span>

<span data-ttu-id="cc405-170">ConstrainedLanguage 모드에서 허용 되는 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-170">The following types are permitted in ConstrainedLanguage mode.</span></span> <span data-ttu-id="cc405-171">사용자는 속성을 가져오고, 메서드를 호출 하 고, 개체를 이러한 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-171">Users can get properties, invoke methods, and convert objects to these types.</span></span>

<span data-ttu-id="cc405-172">허용 되는 형식:</span><span class="sxs-lookup"><span data-stu-id="cc405-172">Allowed Types:</span></span>

- <span data-ttu-id="cc405-173">AliasAttribute</span><span class="sxs-lookup"><span data-stu-id="cc405-173">AliasAttribute</span></span>
- <span data-ttu-id="cc405-174">AllowEmptyCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="cc405-174">AllowEmptyCollectionAttribute</span></span>
- <span data-ttu-id="cc405-175">AllowEmptyStringAttribute</span><span class="sxs-lookup"><span data-stu-id="cc405-175">AllowEmptyStringAttribute</span></span>
- <span data-ttu-id="cc405-176">AllowNullAttribute</span><span class="sxs-lookup"><span data-stu-id="cc405-176">AllowNullAttribute</span></span>
- <span data-ttu-id="cc405-177">배열</span><span class="sxs-lookup"><span data-stu-id="cc405-177">Array</span></span>
- <span data-ttu-id="cc405-178">Bool</span><span class="sxs-lookup"><span data-stu-id="cc405-178">Bool</span></span>
- <span data-ttu-id="cc405-179">byte</span><span class="sxs-lookup"><span data-stu-id="cc405-179">byte</span></span>
- <span data-ttu-id="cc405-180">char</span><span class="sxs-lookup"><span data-stu-id="cc405-180">char</span></span>
- <span data-ttu-id="cc405-181">CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="cc405-181">CmdletBindingAttribute</span></span>
- <span data-ttu-id="cc405-182">DateTime</span><span class="sxs-lookup"><span data-stu-id="cc405-182">DateTime</span></span>
- <span data-ttu-id="cc405-183">decimal</span><span class="sxs-lookup"><span data-stu-id="cc405-183">decimal</span></span>
- <span data-ttu-id="cc405-184">DirectoryEntry</span><span class="sxs-lookup"><span data-stu-id="cc405-184">DirectoryEntry</span></span>
- <span data-ttu-id="cc405-185">DirectorySearcher</span><span class="sxs-lookup"><span data-stu-id="cc405-185">DirectorySearcher</span></span>
- <span data-ttu-id="cc405-186">double</span><span class="sxs-lookup"><span data-stu-id="cc405-186">double</span></span>
- <span data-ttu-id="cc405-187">float</span><span class="sxs-lookup"><span data-stu-id="cc405-187">float</span></span>
- <span data-ttu-id="cc405-188">GUID</span><span class="sxs-lookup"><span data-stu-id="cc405-188">Guid</span></span>
- <span data-ttu-id="cc405-189">Hashtable</span><span class="sxs-lookup"><span data-stu-id="cc405-189">Hashtable</span></span>
- <span data-ttu-id="cc405-190">int</span><span class="sxs-lookup"><span data-stu-id="cc405-190">int</span></span>
- <span data-ttu-id="cc405-191">Int16</span><span class="sxs-lookup"><span data-stu-id="cc405-191">Int16</span></span>
- <span data-ttu-id="cc405-192">long</span><span class="sxs-lookup"><span data-stu-id="cc405-192">long</span></span>
- <span data-ttu-id="cc405-193">ManagementClass</span><span class="sxs-lookup"><span data-stu-id="cc405-193">ManagementClass</span></span>
- <span data-ttu-id="cc405-194">ManagementObject</span><span class="sxs-lookup"><span data-stu-id="cc405-194">ManagementObject</span></span>
- <span data-ttu-id="cc405-195">ManagementObjectSearcher</span><span class="sxs-lookup"><span data-stu-id="cc405-195">ManagementObjectSearcher</span></span>
- <span data-ttu-id="cc405-196">NullString</span><span class="sxs-lookup"><span data-stu-id="cc405-196">NullString</span></span>
- <span data-ttu-id="cc405-197">OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="cc405-197">OutputTypeAttribute</span></span>
- <span data-ttu-id="cc405-198">ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="cc405-198">ParameterAttribute</span></span>
- <span data-ttu-id="cc405-199">PSCredential</span><span class="sxs-lookup"><span data-stu-id="cc405-199">PSCredential</span></span>
- <span data-ttu-id="cc405-200">PSDefaultValueAttribute</span><span class="sxs-lookup"><span data-stu-id="cc405-200">PSDefaultValueAttribute</span></span>
- <span data-ttu-id="cc405-201">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="cc405-201">PSListModifier</span></span>
- <span data-ttu-id="cc405-202">PSObject</span><span class="sxs-lookup"><span data-stu-id="cc405-202">PSObject</span></span>
- <span data-ttu-id="cc405-203">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="cc405-203">PSPrimitiveDictionary</span></span>
- <span data-ttu-id="cc405-204">PSReference</span><span class="sxs-lookup"><span data-stu-id="cc405-204">PSReference</span></span>
- <span data-ttu-id="cc405-205">PSTypeNameAttribute</span><span class="sxs-lookup"><span data-stu-id="cc405-205">PSTypeNameAttribute</span></span>
- <span data-ttu-id="cc405-206">Regex</span><span class="sxs-lookup"><span data-stu-id="cc405-206">Regex</span></span>
- <span data-ttu-id="cc405-207">SByte</span><span class="sxs-lookup"><span data-stu-id="cc405-207">SByte</span></span>
- <span data-ttu-id="cc405-208">문자열</span><span class="sxs-lookup"><span data-stu-id="cc405-208">string</span></span>
- <span data-ttu-id="cc405-209">SupportsWildcardsAttribute</span><span class="sxs-lookup"><span data-stu-id="cc405-209">SupportsWildcardsAttribute</span></span>
- <span data-ttu-id="cc405-210">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="cc405-210">SwitchParameter</span></span>
- <span data-ttu-id="cc405-211">System.object. CultureInfo</span><span class="sxs-lookup"><span data-stu-id="cc405-211">System.Globalization.CultureInfo</span></span>
- <span data-ttu-id="cc405-212">시스템 .Net. IPAddress</span><span class="sxs-lookup"><span data-stu-id="cc405-212">System.Net.IPAddress</span></span>
- <span data-ttu-id="cc405-213">시스템 .Net. 메일 주소</span><span class="sxs-lookup"><span data-stu-id="cc405-213">System.Net.Mail.MailAddress</span></span>
- <span data-ttu-id="cc405-214">BigInteger</span><span class="sxs-lookup"><span data-stu-id="cc405-214">System.Numerics.BigInteger</span></span>
- <span data-ttu-id="cc405-215">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="cc405-215">System.Security.SecureString</span></span>
- <span data-ttu-id="cc405-216">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="cc405-216">TimeSpan</span></span>
- <span data-ttu-id="cc405-217">UInt16</span><span class="sxs-lookup"><span data-stu-id="cc405-217">UInt16</span></span>
- <span data-ttu-id="cc405-218">UInt32</span><span class="sxs-lookup"><span data-stu-id="cc405-218">UInt32</span></span>
- <span data-ttu-id="cc405-219">UInt64</span><span class="sxs-lookup"><span data-stu-id="cc405-219">UInt64</span></span>

### <a name="finding-the-language-mode-of-a-session-configuration"></a><span data-ttu-id="cc405-220">세션 구성의 언어 모드 찾기</span><span class="sxs-lookup"><span data-stu-id="cc405-220">FINDING THE LANGUAGE MODE OF A SESSION CONFIGURATION</span></span>

<span data-ttu-id="cc405-221">세션 구성 파일을 사용 하 여 세션 구성을 만드는 경우 세션 구성에는 LanguageMode 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-221">When a session configuration is created by using a session configuration file, the session configuration has a LanguageMode property.</span></span> <span data-ttu-id="cc405-222">LanguageMode 속성 값을 가져와서 언어 모드를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-222">You can find the language mode by getting the value of the LanguageMode property.</span></span>

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

<span data-ttu-id="cc405-223">다른 세션 구성에서는 세션 구성을 사용 하 여 만든 세션의 언어 모드를 찾아 언어 모드를 간접적으로 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-223">On other session configurations, you can find the language mode indirectly by finding the language mode of a session that is created by using the session configuration.</span></span>

### <a name="finding-the-language-mode-of-a-session"></a><span data-ttu-id="cc405-224">세션의 언어 모드 찾기</span><span class="sxs-lookup"><span data-stu-id="cc405-224">FINDING THE LANGUAGE MODE OF A SESSION</span></span>

<span data-ttu-id="cc405-225">세션 상태의 LanguageMode 속성 값을 가져와 FullLanguage 또는 ConstrainedLanguage 세션의 언어 모드를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-225">You can find the language mode of a FullLanguage or ConstrainedLanguage session by getting the value of the LanguageMode property of the session state.</span></span>

<span data-ttu-id="cc405-226">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="cc405-226">For example:</span></span>

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

<span data-ttu-id="cc405-227">그러나 RestrictedLanguage 및 NoLanguage 모드를 사용 하는 세션에서는 점 메서드를 사용 하 여 속성 값을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-227">However, in sessions with RestrictedLanguage and NoLanguage modes, you cannot use the dot method to get property values.</span></span> <span data-ttu-id="cc405-228">대신 오류 메시지가 언어 모드를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-228">Instead, the error message reveals the language mode.</span></span>

<span data-ttu-id="cc405-229">`$ExecutionContext.SessionState.LanguageMode`RestrictedLanguage 세션에서 명령을 실행 하면 PowerShell에서 PropertyReferenceNotSupportedInDataSection 및 VariableReferenceNotSupportedInDataSection 오류 메시지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-229">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a RestrictedLanguage session, PowerShell returns the PropertyReferenceNotSupportedInDataSection and VariableReferenceNotSupportedInDataSection error messages.</span></span>

- <span data-ttu-id="cc405-230">PropertyReferenceNotSupportedInDataSection: 제한 된 언어 모드 또는 데이터 섹션에는 속성 참조를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-230">PropertyReferenceNotSupportedInDataSection: Property references are not allowed in restricted language mode or a Data section.</span></span>
- <span data-ttu-id="cc405-231">제한 된 언어 모드에서 참조할 수 없는 변수를 VariableReferenceNotSupportedInDataSection 하거나 데이터 섹션을 참조 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-231">VariableReferenceNotSupportedInDataSection A variable that cannot be referenced in restricted language mode or a Data section is being referenced.</span></span>

<span data-ttu-id="cc405-232">`$ExecutionContext.SessionState.LanguageMode`NoLanguage 세션에서 명령을 실행 하면 PowerShell에서 ScriptsNotAllowed 오류 메시지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-232">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a NoLanguage session, PowerShell returns the ScriptsNotAllowed error message.</span></span>

- <span data-ttu-id="cc405-233">ScriptsNotAllowed:이 runspace에서 구문을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-233">ScriptsNotAllowed: The syntax is not supported by this runspace.</span></span> <span data-ttu-id="cc405-234">언어가 언어 모드에 있지 않기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc405-234">This might be because it is in no-language mode.</span></span>

## <a name="keywords"></a><span data-ttu-id="cc405-235">어</span><span class="sxs-lookup"><span data-stu-id="cc405-235">KEYWORDS</span></span>

- <span data-ttu-id="cc405-236">about_ConstrainedLanguage</span><span class="sxs-lookup"><span data-stu-id="cc405-236">about_ConstrainedLanguage</span></span>
- <span data-ttu-id="cc405-237">about_FullLanguage</span><span class="sxs-lookup"><span data-stu-id="cc405-237">about_FullLanguage</span></span>
- <span data-ttu-id="cc405-238">about_NoLanguage</span><span class="sxs-lookup"><span data-stu-id="cc405-238">about_NoLanguage</span></span>
- <span data-ttu-id="cc405-239">about_RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="cc405-239">about_RestrictedLanguage</span></span>

## <a name="see-also"></a><span data-ttu-id="cc405-240">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cc405-240">SEE ALSO</span></span>

- [<span data-ttu-id="cc405-241">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="cc405-241">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)
- [<span data-ttu-id="cc405-242">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="cc405-242">about_Session_Configurations</span></span>](about_Session_Configurations.md)


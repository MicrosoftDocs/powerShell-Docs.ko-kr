---
description: 언어 모드 및 PowerShell 세션에 미치는 영향을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: a75afd5149f3d290a8ec377417d4920b0ad6b526
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222690"
---
# <a name="about-language-modes"></a><span data-ttu-id="79d1a-104">언어 모드 정보</span><span class="sxs-lookup"><span data-stu-id="79d1a-104">About Language Modes</span></span>

## <a name="short-description"></a><span data-ttu-id="79d1a-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="79d1a-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="79d1a-106">언어 모드 및 PowerShell 세션에 미치는 영향을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-106">Explains language modes and their effect on PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="79d1a-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="79d1a-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="79d1a-108">PowerShell 세션의 언어 모드에서는 세션에서 사용할 수 있는 PowerShell 언어 요소를 부분적으로 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-108">The language mode of a PowerShell session determines, in part, which elements of the PowerShell language can be used in the session.</span></span>

<span data-ttu-id="79d1a-109">PowerShell은 다음과 같은 언어 모드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-109">PowerShell supports the following language modes:</span></span>

- <span data-ttu-id="79d1a-110">FullLanguage</span><span class="sxs-lookup"><span data-stu-id="79d1a-110">FullLanguage</span></span>
- <span data-ttu-id="79d1a-111">ConstrainedLanguage (PowerShell 3.0에 도입 됨)</span><span class="sxs-lookup"><span data-stu-id="79d1a-111">ConstrainedLanguage (introduced in PowerShell 3.0)</span></span>
- <span data-ttu-id="79d1a-112">RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="79d1a-112">RestrictedLanguage</span></span>
- <span data-ttu-id="79d1a-113">NoLanguage</span><span class="sxs-lookup"><span data-stu-id="79d1a-113">NoLanguage</span></span>

### <a name="what-is-a-language-mode"></a><span data-ttu-id="79d1a-114">언어 모드는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="79d1a-114">WHAT IS A LANGUAGE MODE?</span></span>

<span data-ttu-id="79d1a-115">언어 모드는 세션에서 허용 되는 언어 요소를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-115">The language mode determines the language elements that are permitted in the session.</span></span>

<span data-ttu-id="79d1a-116">언어 모드는 실제로 세션을 만드는 데 사용 되는 세션 구성 (또는 "끝점")의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-116">The language mode is actually a property of the session configuration (or "endpoint") that is used to create the session.</span></span> <span data-ttu-id="79d1a-117">특정 세션 구성을 사용 하는 모든 세션에는 세션 구성의 언어 모드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-117">All sessions that use a particular session configuration have the language mode of the session configuration.</span></span>

<span data-ttu-id="79d1a-118">모든 PowerShell 세션에는 cmdlet을 사용 하 여 만든 pssession `New-PSSession` , ComputerName 매개 변수를 사용 하는 임시 세션, powershell을 시작할 때 표시 되는 기본 세션 등의 언어 모드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-118">All PowerShell sessions have a language mode, including PSSessions that you create by using the `New-PSSession` cmdlet, temporary sessions that use the ComputerName parameter, and the default sessions that appear when you start PowerShell.</span></span>

<span data-ttu-id="79d1a-119">원격 세션은 원격 컴퓨터의 세션 구성을 사용 하 여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-119">Remote sessions are created by using the session configurations on the remote computer.</span></span> <span data-ttu-id="79d1a-120">세션 구성에 설정 된 언어 모드는 세션의 언어 모드를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-120">The language mode set in the session configuration determines the language mode of the session.</span></span> <span data-ttu-id="79d1a-121">PSSession의 세션 구성을 지정 하려면 세션을 만드는 cmdlet의 ConfigurationName 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-121">To specify the session configuration of a PSSession, use the ConfigurationName parameter of cmdlets that create a session.</span></span>

### <a name="language-modes"></a><span data-ttu-id="79d1a-122">언어 모드</span><span class="sxs-lookup"><span data-stu-id="79d1a-122">LANGUAGE MODES</span></span>

<span data-ttu-id="79d1a-123">이 섹션에서는 PowerShell 세션의 언어 모드에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-123">This section describes the language modes in PowerShell sessions.</span></span>

#### <a name="full-language-fulllanguage"></a><span data-ttu-id="79d1a-124">전체 언어 (FullLanguage)</span><span class="sxs-lookup"><span data-stu-id="79d1a-124">FULL LANGUAGE (FullLanguage)</span></span>

<span data-ttu-id="79d1a-125">FullLanguage 모드는 세션의 모든 언어 요소를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-125">The FullLanguage mode permits all language elements in the session.</span></span>
<span data-ttu-id="79d1a-126">FullLanguage는 Windows RT를 제외한 모든 Windows 버전에서 기본 세션의 기본 언어 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-126">FullLanguage is the default language mode for default sessions on all versions of Windows except for Windows RT.</span></span>

#### <a name="restricted-language-restrictedlanguage"></a><span data-ttu-id="79d1a-127">제한 된 언어 (RestrictedLanguage)</span><span class="sxs-lookup"><span data-stu-id="79d1a-127">RESTRICTED LANGUAGE (RestrictedLanguage)</span></span>

<span data-ttu-id="79d1a-128">RestrictedLanguage 모드에서 사용자는 명령 (cmdlet, 함수, CIM 명령 및 워크플로)을 실행할 수 있지만 스크립트 블록을 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-128">In RestrictedLanguage mode, users may run commands (cmdlets, functions, CIM commands, and workflows) but are not permitted to use script blocks.</span></span>

<span data-ttu-id="79d1a-129">기본적으로 RestrictedLanguage 모드에서는 다음 변수만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-129">By default, only the following variables are permitted in RestrictedLanguage mode:</span></span>

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

<span data-ttu-id="79d1a-130">다음 비교 연산자만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-130">Only the following comparison operators are permitted:</span></span>

- <span data-ttu-id="79d1a-131">`-eq` 다릅니다</span><span class="sxs-lookup"><span data-stu-id="79d1a-131">`-eq` (equal)</span></span>
- <span data-ttu-id="79d1a-132">`-gt` (보다 큼)</span><span class="sxs-lookup"><span data-stu-id="79d1a-132">`-gt` (greater-than)</span></span>
- <span data-ttu-id="79d1a-133">`-lt` (보다 작음)</span><span class="sxs-lookup"><span data-stu-id="79d1a-133">`-lt` (less-than)</span></span>

<span data-ttu-id="79d1a-134">대입문, 속성 참조 및 메서드 호출은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-134">Assignment statements, property references, and method calls are not permitted.</span></span>

#### <a name="no-language-nolanguage"></a><span data-ttu-id="79d1a-135">언어 없음 (NoLanguage)</span><span class="sxs-lookup"><span data-stu-id="79d1a-135">NO LANGUAGE (NoLanguage)</span></span>

<span data-ttu-id="79d1a-136">NoLanguage 모드는 API를 통해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-136">NoLanguage mode can only be used through the API.</span></span> <span data-ttu-id="79d1a-137">NoLanguage 모드는 모든 형식의 스크립트 텍스트가 허용 되지 않음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-137">NoLanguage mode means no script text of any form is permitted.</span></span> <span data-ttu-id="79d1a-138">이를 통해 구문 분석 되 고 실행 되는 PowerShell 스크립트의 조각을 보내는 **Addscript ()** 메서드를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-138">This precludes the use of the **AddScript()** method which sends fragments of PowerShell script to be parsed and executed.</span></span> <span data-ttu-id="79d1a-139">파서를 통과 하지 않는 **Addcommand ()** 및 **addcommand ()** 만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-139">You can only use **AddCommand()** and **AddParameter()** which don't go through the parser.</span></span>

#### <a name="constrained-language-constrained-language"></a><span data-ttu-id="79d1a-140">제약이 있는 언어 (제한 언어)</span><span class="sxs-lookup"><span data-stu-id="79d1a-140">CONSTRAINED LANGUAGE (Constrained Language)</span></span>

<span data-ttu-id="79d1a-141">ConstrainedLanguage 모드는 모든 cmdlet 및 모든 PowerShell 언어 요소를 허용 하지만 허용 된 형식을 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-141">The ConstrainedLanguage mode permits all cmdlets and all PowerShell language elements, but it limits permitted types.</span></span>

<span data-ttu-id="79d1a-142">ConstrainedLanguage 모드는 Windows RT에서 UMCI (사용자 모드 코드 무결성)를 지원 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-142">ConstrainedLanguage mode is designed to support User Mode Code Integrity (UMCI) on Windows RT.</span></span> <span data-ttu-id="79d1a-143">이 모드는 Windows RT에서 유일 하 게 지원 되는 언어 모드 이지만 지원 되는 모든 시스템에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-143">It is the only supported language mode on Windows RT, but it is available on all supported systems.</span></span>

<span data-ttu-id="79d1a-144">UMCI는 Windows RT 기반 장치에 Microsoft 서명 및 Microsoft 인증 앱만 설치 하도록 허용 하 여 ARM 장치를 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-144">UMCI protects ARM devices by allowing only Microsoft-signed and Microsoft-certified apps to be installed on Windows RT-based devices.</span></span>
<span data-ttu-id="79d1a-145">ConstrainedLanguage 모드를 사용 하면 사용자가 PowerShell을 사용 하 여 UMCI를 우회 하거나 위반할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-145">ConstrainedLanguage mode prevents users from using PowerShell to circumvent or violate UMCI.</span></span>

<span data-ttu-id="79d1a-146">ConstrainedLanguage 모드의 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-146">The features of ConstrainedLanguage mode are as follows:</span></span>

- <span data-ttu-id="79d1a-147">Windows 모듈의 모든 cmdlet 및 기타 UMCI 승인 된 cmdlet은 완전히 작동 하며, 명시 된 경우를 제외 하 고 시스템 리소스에 대 한 완전 한 액세스 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-147">All cmdlets in Windows modules, and other UMCI-approved cmdlets, are fully functional and have complete access to system resources, except as noted.</span></span>

- <span data-ttu-id="79d1a-148">PowerShell 스크립트 언어의 모든 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-148">All elements of the PowerShell scripting language are permitted.</span></span>

- <span data-ttu-id="79d1a-149">Windows에 포함 된 모든 모듈을 가져올 수 있으며, 모듈 내보내기가 세션에서 실행 하는 모든 명령을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-149">All modules included in Windows can be imported and all commands that the modules export run in the session.</span></span>

- <span data-ttu-id="79d1a-150">PowerShell 워크플로에서 스크립트 워크플로 (PowerShell 언어로 작성 된 워크플로)를 작성 하 고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-150">In PowerShell Workflow, you can write and run script workflows (workflows written in the PowerShell language).</span></span> <span data-ttu-id="79d1a-151">XAML 기반 워크플로는 지원 되지 않으므로를 사용 하는 등의 스크립트 워크플로에서는 XAML을 실행할 수 없습니다 `Invoke-Expression -Language XAML` .</span><span class="sxs-lookup"><span data-stu-id="79d1a-151">XAML-based workflows are not supported and you cannot run XAML in a script workflow, such as by using `Invoke-Expression -Language XAML`.</span></span> <span data-ttu-id="79d1a-152">또한 중첩 된 워크플로가 허용 되지만 워크플로는 다른 워크플로를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-152">Also, workflows cannot call other workflows, although nested workflows are permitted.</span></span>

- <span data-ttu-id="79d1a-153">`Add-Type`Cmdlet은 서명 된 어셈블리를 로드할 수 있지만 임의의 c # 코드 또는 Win32 api는 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-153">The `Add-Type` cmdlet can load signed assemblies, but it cannot load arbitrary C# code or Win32 APIs.</span></span>

- <span data-ttu-id="79d1a-154">이 `New-Object` cmdlet은 허용 되는 형식 (아래 참조)에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-154">The `New-Object` cmdlet can be used only on allowed types (listed below).</span></span>

- <span data-ttu-id="79d1a-155">PowerShell에서 허용 되는 유형 (아래에 나열 됨)만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-155">Only allowed types (listed below) can be used in PowerShell.</span></span> <span data-ttu-id="79d1a-156">다른 형식은 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-156">Other types are not permitted.</span></span>

- <span data-ttu-id="79d1a-157">형식을 변환할 수 있지만 결과가 허용 되는 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-157">Type conversion is permitted, but only when the result is an allowed type.</span></span>

- <span data-ttu-id="79d1a-158">문자열 입력을 형식으로 변환 하는 Cmdlet 매개 변수는 결과 형식이 허용 되는 형식인 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-158">Cmdlet parameters that convert string input to types work only when the resulting type is an allowed type.</span></span>

- <span data-ttu-id="79d1a-159">**ToString ()** 메서드 및 허용 되는 형식 (아래 나열 됨)의 .net 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-159">The **ToString()** method and the .NET methods of allowed types (listed below) can be invoked.</span></span> <span data-ttu-id="79d1a-160">다른 메서드는 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-160">Other methods cannot be invoked.</span></span>

- <span data-ttu-id="79d1a-161">사용자는 허용 된 형식의 모든 속성을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-161">Users can get all properties of allowed types.</span></span> <span data-ttu-id="79d1a-162">사용자는 코어 유형에만 속성 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-162">Users can set the values of properties only on Core types.</span></span> <span data-ttu-id="79d1a-163">다음 COM 개체만 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-163">Only the following COM objects are permitted:</span></span>

  - <span data-ttu-id="79d1a-164">**Scripting. 사전**</span><span class="sxs-lookup"><span data-stu-id="79d1a-164">**Scripting.Dictionary**</span></span>
  - <span data-ttu-id="79d1a-165">**Scripting.FileSystemObject**</span><span class="sxs-lookup"><span data-stu-id="79d1a-165">**Scripting.FileSystemObject**</span></span>
  - <span data-ttu-id="79d1a-166">**VBScript. RegExp**</span><span class="sxs-lookup"><span data-stu-id="79d1a-166">**VBScript.RegExp**</span></span>

<span data-ttu-id="79d1a-167">ConstrainedLanguage 모드에서 허용 되는 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-167">The following types are permitted in ConstrainedLanguage mode.</span></span> <span data-ttu-id="79d1a-168">사용자는 속성을 가져오고, 메서드를 호출 하 고, 개체를 이러한 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-168">Users can get properties, invoke methods, and convert objects to these types.</span></span>

<span data-ttu-id="79d1a-169">허용 되는 형식:</span><span class="sxs-lookup"><span data-stu-id="79d1a-169">Allowed Types:</span></span>

- <span data-ttu-id="79d1a-170">AliasAttribute</span><span class="sxs-lookup"><span data-stu-id="79d1a-170">AliasAttribute</span></span>
- <span data-ttu-id="79d1a-171">AllowEmptyCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="79d1a-171">AllowEmptyCollectionAttribute</span></span>
- <span data-ttu-id="79d1a-172">AllowEmptyStringAttribute</span><span class="sxs-lookup"><span data-stu-id="79d1a-172">AllowEmptyStringAttribute</span></span>
- <span data-ttu-id="79d1a-173">AllowNullAttribute</span><span class="sxs-lookup"><span data-stu-id="79d1a-173">AllowNullAttribute</span></span>
- <span data-ttu-id="79d1a-174">배열</span><span class="sxs-lookup"><span data-stu-id="79d1a-174">Array</span></span>
- <span data-ttu-id="79d1a-175">Bool</span><span class="sxs-lookup"><span data-stu-id="79d1a-175">Bool</span></span>
- <span data-ttu-id="79d1a-176">byte</span><span class="sxs-lookup"><span data-stu-id="79d1a-176">byte</span></span>
- <span data-ttu-id="79d1a-177">char</span><span class="sxs-lookup"><span data-stu-id="79d1a-177">char</span></span>
- <span data-ttu-id="79d1a-178">CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="79d1a-178">CmdletBindingAttribute</span></span>
- <span data-ttu-id="79d1a-179">DateTime</span><span class="sxs-lookup"><span data-stu-id="79d1a-179">DateTime</span></span>
- <span data-ttu-id="79d1a-180">decimal</span><span class="sxs-lookup"><span data-stu-id="79d1a-180">decimal</span></span>
- <span data-ttu-id="79d1a-181">DirectoryEntry</span><span class="sxs-lookup"><span data-stu-id="79d1a-181">DirectoryEntry</span></span>
- <span data-ttu-id="79d1a-182">DirectorySearcher</span><span class="sxs-lookup"><span data-stu-id="79d1a-182">DirectorySearcher</span></span>
- <span data-ttu-id="79d1a-183">double</span><span class="sxs-lookup"><span data-stu-id="79d1a-183">double</span></span>
- <span data-ttu-id="79d1a-184">float</span><span class="sxs-lookup"><span data-stu-id="79d1a-184">float</span></span>
- <span data-ttu-id="79d1a-185">GUID</span><span class="sxs-lookup"><span data-stu-id="79d1a-185">Guid</span></span>
- <span data-ttu-id="79d1a-186">Hashtable</span><span class="sxs-lookup"><span data-stu-id="79d1a-186">Hashtable</span></span>
- <span data-ttu-id="79d1a-187">int</span><span class="sxs-lookup"><span data-stu-id="79d1a-187">int</span></span>
- <span data-ttu-id="79d1a-188">Int16</span><span class="sxs-lookup"><span data-stu-id="79d1a-188">Int16</span></span>
- <span data-ttu-id="79d1a-189">long</span><span class="sxs-lookup"><span data-stu-id="79d1a-189">long</span></span>
- <span data-ttu-id="79d1a-190">ManagementClass</span><span class="sxs-lookup"><span data-stu-id="79d1a-190">ManagementClass</span></span>
- <span data-ttu-id="79d1a-191">ManagementObject</span><span class="sxs-lookup"><span data-stu-id="79d1a-191">ManagementObject</span></span>
- <span data-ttu-id="79d1a-192">ManagementObjectSearcher</span><span class="sxs-lookup"><span data-stu-id="79d1a-192">ManagementObjectSearcher</span></span>
- <span data-ttu-id="79d1a-193">NullString</span><span class="sxs-lookup"><span data-stu-id="79d1a-193">NullString</span></span>
- <span data-ttu-id="79d1a-194">OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="79d1a-194">OutputTypeAttribute</span></span>
- <span data-ttu-id="79d1a-195">ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="79d1a-195">ParameterAttribute</span></span>
- <span data-ttu-id="79d1a-196">PSCredential</span><span class="sxs-lookup"><span data-stu-id="79d1a-196">PSCredential</span></span>
- <span data-ttu-id="79d1a-197">PSDefaultValueAttribute</span><span class="sxs-lookup"><span data-stu-id="79d1a-197">PSDefaultValueAttribute</span></span>
- <span data-ttu-id="79d1a-198">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="79d1a-198">PSListModifier</span></span>
- <span data-ttu-id="79d1a-199">PSObject</span><span class="sxs-lookup"><span data-stu-id="79d1a-199">PSObject</span></span>
- <span data-ttu-id="79d1a-200">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="79d1a-200">PSPrimitiveDictionary</span></span>
- <span data-ttu-id="79d1a-201">PSReference</span><span class="sxs-lookup"><span data-stu-id="79d1a-201">PSReference</span></span>
- <span data-ttu-id="79d1a-202">PSTypeNameAttribute</span><span class="sxs-lookup"><span data-stu-id="79d1a-202">PSTypeNameAttribute</span></span>
- <span data-ttu-id="79d1a-203">Regex</span><span class="sxs-lookup"><span data-stu-id="79d1a-203">Regex</span></span>
- <span data-ttu-id="79d1a-204">SByte</span><span class="sxs-lookup"><span data-stu-id="79d1a-204">SByte</span></span>
- <span data-ttu-id="79d1a-205">문자열</span><span class="sxs-lookup"><span data-stu-id="79d1a-205">string</span></span>
- <span data-ttu-id="79d1a-206">SupportsWildcardsAttribute</span><span class="sxs-lookup"><span data-stu-id="79d1a-206">SupportsWildcardsAttribute</span></span>
- <span data-ttu-id="79d1a-207">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="79d1a-207">SwitchParameter</span></span>
- <span data-ttu-id="79d1a-208">System.object. CultureInfo</span><span class="sxs-lookup"><span data-stu-id="79d1a-208">System.Globalization.CultureInfo</span></span>
- <span data-ttu-id="79d1a-209">시스템 .Net. IPAddress</span><span class="sxs-lookup"><span data-stu-id="79d1a-209">System.Net.IPAddress</span></span>
- <span data-ttu-id="79d1a-210">시스템 .Net. 메일 주소</span><span class="sxs-lookup"><span data-stu-id="79d1a-210">System.Net.Mail.MailAddress</span></span>
- <span data-ttu-id="79d1a-211">BigInteger</span><span class="sxs-lookup"><span data-stu-id="79d1a-211">System.Numerics.BigInteger</span></span>
- <span data-ttu-id="79d1a-212">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="79d1a-212">System.Security.SecureString</span></span>
- <span data-ttu-id="79d1a-213">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="79d1a-213">TimeSpan</span></span>
- <span data-ttu-id="79d1a-214">UInt16</span><span class="sxs-lookup"><span data-stu-id="79d1a-214">UInt16</span></span>
- <span data-ttu-id="79d1a-215">UInt32</span><span class="sxs-lookup"><span data-stu-id="79d1a-215">UInt32</span></span>
- <span data-ttu-id="79d1a-216">UInt64</span><span class="sxs-lookup"><span data-stu-id="79d1a-216">UInt64</span></span>

### <a name="finding-the-language-mode-of-a-session-configuration"></a><span data-ttu-id="79d1a-217">세션 구성의 언어 모드 찾기</span><span class="sxs-lookup"><span data-stu-id="79d1a-217">FINDING THE LANGUAGE MODE OF A SESSION CONFIGURATION</span></span>

<span data-ttu-id="79d1a-218">세션 구성 파일을 사용 하 여 세션 구성을 만드는 경우 세션 구성에는 LanguageMode 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-218">When a session configuration is created by using a session configuration file, the session configuration has a LanguageMode property.</span></span> <span data-ttu-id="79d1a-219">LanguageMode 속성 값을 가져와서 언어 모드를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-219">You can find the language mode by getting the value of the LanguageMode property.</span></span>

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

<span data-ttu-id="79d1a-220">다른 세션 구성에서는 세션 구성을 사용 하 여 만든 세션의 언어 모드를 찾아 언어 모드를 간접적으로 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-220">On other session configurations, you can find the language mode indirectly by finding the language mode of a session that is created by using the session configuration.</span></span>

### <a name="finding-the-language-mode-of-a-session"></a><span data-ttu-id="79d1a-221">세션의 언어 모드 찾기</span><span class="sxs-lookup"><span data-stu-id="79d1a-221">FINDING THE LANGUAGE MODE OF A SESSION</span></span>

<span data-ttu-id="79d1a-222">세션 상태의 LanguageMode 속성 값을 가져와 FullLanguage 또는 ConstrainedLanguage 세션의 언어 모드를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-222">You can find the language mode of a FullLanguage or ConstrainedLanguage session by getting the value of the LanguageMode property of the session state.</span></span>

<span data-ttu-id="79d1a-223">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="79d1a-223">For example:</span></span>

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

<span data-ttu-id="79d1a-224">그러나 RestrictedLanguage 및 NoLanguage 모드를 사용 하는 세션에서는 점 메서드를 사용 하 여 속성 값을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-224">However, in sessions with RestrictedLanguage and NoLanguage modes, you cannot use the dot method to get property values.</span></span> <span data-ttu-id="79d1a-225">대신 오류 메시지가 언어 모드를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-225">Instead, the error message reveals the language mode.</span></span>

<span data-ttu-id="79d1a-226">`$ExecutionContext.SessionState.LanguageMode`RestrictedLanguage 세션에서 명령을 실행 하면 PowerShell에서 PropertyReferenceNotSupportedInDataSection 및 VariableReferenceNotSupportedInDataSection 오류 메시지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-226">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a RestrictedLanguage session, PowerShell returns the PropertyReferenceNotSupportedInDataSection and VariableReferenceNotSupportedInDataSection error messages.</span></span>

- <span data-ttu-id="79d1a-227">PropertyReferenceNotSupportedInDataSection: 제한 된 언어 모드 또는 데이터 섹션에는 속성 참조를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-227">PropertyReferenceNotSupportedInDataSection: Property references are not allowed in restricted language mode or a Data section.</span></span>
- <span data-ttu-id="79d1a-228">제한 된 언어 모드에서 참조할 수 없는 변수를 VariableReferenceNotSupportedInDataSection 하거나 데이터 섹션을 참조 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-228">VariableReferenceNotSupportedInDataSection A variable that cannot be referenced in restricted language mode or a Data section is being referenced.</span></span>

<span data-ttu-id="79d1a-229">`$ExecutionContext.SessionState.LanguageMode`NoLanguage 세션에서 명령을 실행 하면 PowerShell에서 ScriptsNotAllowed 오류 메시지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-229">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a NoLanguage session, PowerShell returns the ScriptsNotAllowed error message.</span></span>

- <span data-ttu-id="79d1a-230">ScriptsNotAllowed:이 runspace에서 구문을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-230">ScriptsNotAllowed: The syntax is not supported by this runspace.</span></span> <span data-ttu-id="79d1a-231">언어가 언어 모드에 있지 않기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79d1a-231">This might be because it is in no-language mode.</span></span>

## <a name="keywords"></a><span data-ttu-id="79d1a-232">어</span><span class="sxs-lookup"><span data-stu-id="79d1a-232">KEYWORDS</span></span>

- <span data-ttu-id="79d1a-233">about_ConstrainedLanguage</span><span class="sxs-lookup"><span data-stu-id="79d1a-233">about_ConstrainedLanguage</span></span>
- <span data-ttu-id="79d1a-234">about_FullLanguage</span><span class="sxs-lookup"><span data-stu-id="79d1a-234">about_FullLanguage</span></span>
- <span data-ttu-id="79d1a-235">about_NoLanguage</span><span class="sxs-lookup"><span data-stu-id="79d1a-235">about_NoLanguage</span></span>
- <span data-ttu-id="79d1a-236">about_RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="79d1a-236">about_RestrictedLanguage</span></span>

## <a name="see-also"></a><span data-ttu-id="79d1a-237">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79d1a-237">SEE ALSO</span></span>

- [<span data-ttu-id="79d1a-238">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="79d1a-238">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)
- [<span data-ttu-id="79d1a-239">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="79d1a-239">about_Session_Configurations</span></span>](about_Session_Configurations.md)

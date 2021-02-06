---
description: PowerShell에서 cmdlet 및 명령에 대 한 대체 이름을 사용 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_aliases?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Aliases
ms.openlocfilehash: e8b93e2b687e779048784c1eedb15fa53972b8b0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605023"
---
# <a name="about-aliases"></a><span data-ttu-id="e35d3-103">별칭 정보</span><span class="sxs-lookup"><span data-stu-id="e35d3-103">About Aliases</span></span>

## <a name="short-description"></a><span data-ttu-id="e35d3-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="e35d3-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="e35d3-105">PowerShell에서 cmdlet 및 명령에 대 한 대체 이름을 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-105">Describes how to use alternate names for cmdlets and commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="e35d3-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="e35d3-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="e35d3-107">별칭은 cmdlet 또는 명령 요소 (예: 함수, 스크립트, 파일 또는 실행 파일)에 대 한 대체 이름 또는 애칭입니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-107">An alias is an alternate name or nickname for a cmdlet or for a command element, such as a function, script, file, or executable file.</span></span> <span data-ttu-id="e35d3-108">PowerShell 명령에서 명령 이름 대신 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-108">You can use the alias instead of the command name in any PowerShell commands.</span></span>

<span data-ttu-id="e35d3-109">별칭을 만들려면 New-Alias cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-109">To create an alias, use the New-Alias cmdlet.</span></span> <span data-ttu-id="e35d3-110">예를 들어 다음 명령은 cmdlet에 대 한 "가스" 별칭을 만듭니다 `Get-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="e35d3-110">For example, the following command creates the "gas" alias for the `Get-AuthenticodeSignature` cmdlet:</span></span>

```powershell
New-Alias -Name gas -Value Get-AuthenticodeSignature
```

<span data-ttu-id="e35d3-111">Cmdlet 이름에 대 한 별칭을 만든 후에는 cmdlet 이름 대신 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-111">After you create the alias for the cmdlet name, you can use the alias instead of the cmdlet name.</span></span> <span data-ttu-id="e35d3-112">예를 들어 SqlScript.ps1 파일의 Authenticode 서명을 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-112">For example, to get the Authenticode signature for the SqlScript.ps1 file, type:</span></span>

```powershell
Get-AuthenticodeSignature SqlScript.ps1
```

<span data-ttu-id="e35d3-113">또는 다음과 같이 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-113">Or, type:</span></span>

```powershell
gas SqlScript.ps1
```

<span data-ttu-id="e35d3-114">Microsoft Office Word에 대 한 별칭으로 "word"를 만드는 경우에는 다음 대신 "word"를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-114">If you create "word" as the alias for Microsoft Office Word, you can type "word" instead of the following:</span></span>

```powershell
"C:\Program Files\Microsoft Office\Office11\Winword.exe"
```

## <a name="built-in-aliases"></a><span data-ttu-id="e35d3-115">기본 제공 별칭</span><span class="sxs-lookup"><span data-stu-id="e35d3-115">BUILT-IN ALIASES</span></span>

<span data-ttu-id="e35d3-116">PowerShell에는 Set-Location cmdlet에 대 한 "cd" 및 "chdir"을 포함 하는 기본 제공 별칭 집합과 Get-ChildItem cmdlet에 대 한 "ls" 및 "dir"이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-116">PowerShell includes a set of built-in aliases, including "cd" and "chdir" for the Set-Location cmdlet, and "ls" and "dir" for the Get-ChildItem cmdlet.</span></span>

<span data-ttu-id="e35d3-117">기본 제공 별칭을 포함 하 여 컴퓨터의 모든 별칭을 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-117">To get all the aliases on the computer, including the built-in aliases, type:</span></span>

```powershell
Get-Alias
```

## <a name="alias-cmdlets"></a><span data-ttu-id="e35d3-118">별칭 CMDLET</span><span class="sxs-lookup"><span data-stu-id="e35d3-118">ALIAS CMDLETS</span></span>

<span data-ttu-id="e35d3-119">PowerShell에는 별칭을 사용 하도록 설계 된 다음 cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-119">PowerShell includes the following cmdlets, which are designed for working with aliases:</span></span>

- <span data-ttu-id="e35d3-120">`Get-Alias` -현재 세션의 모든 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-120">`Get-Alias` - Gets all the aliases in the current session.</span></span>
- <span data-ttu-id="e35d3-121">`New-Alias` -새 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-121">`New-Alias` - Creates a new alias.</span></span>
- <span data-ttu-id="e35d3-122">`Set-Alias` -별칭을 만들거나 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-122">`Set-Alias` - Creates or changes an alias.</span></span>
- <span data-ttu-id="e35d3-123">`Export-Alias` -하나 이상의 별칭을 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-123">`Export-Alias` - Exports one or more aliases to a file.</span></span>
- <span data-ttu-id="e35d3-124">`Import-Alias` -PowerShell로 별칭 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-124">`Import-Alias` - Imports an alias file into PowerShell.</span></span>

<span data-ttu-id="e35d3-125">Cmdlet에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e35d3-125">For detailed information about the cmdlets, type:</span></span>

```powershell
Get-Help <cmdlet-Name> -Detailed
```

<span data-ttu-id="e35d3-126">예를 들어 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-126">For example, type:</span></span>

```powershell
Get-Help Export-Alias -Detailed
```

## <a name="creating-an-alias"></a><span data-ttu-id="e35d3-127">별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="e35d3-127">CREATING AN ALIAS</span></span>

<span data-ttu-id="e35d3-128">새 별칭을 만들려면 New-Alias cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-128">To create a new alias, use the New-Alias cmdlet.</span></span> <span data-ttu-id="e35d3-129">예를 들어 Get-help에 대 한 "gh" 별칭을 만들려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-129">For example, to create the "gh" alias for Get-Help, type:</span></span>

```powershell
New-Alias -Name gh -Value Get-Help
```

<span data-ttu-id="e35d3-130">전체 cmdlet 이름을 사용 하는 것 처럼 명령에 별칭을 사용할 수 있으며, 매개 변수와 함께 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-130">You can use the alias in commands, just as you would use the full cmdlet name, and you can use the alias with parameters.</span></span>

<span data-ttu-id="e35d3-131">예를 들어 Get-WmiObject cmdlet에 대 한 자세한 도움말을 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-131">For example, to get detailed Help for the Get-WmiObject cmdlet, type:</span></span>

```powershell
Get-Help Get-WmiObject -Detailed
```

<span data-ttu-id="e35d3-132">또는 다음과 같이 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-132">Or, type:</span></span>

```powershell
gh Get-WmiObject -Detailed
```

## <a name="saving-aliases"></a><span data-ttu-id="e35d3-133">별칭 저장</span><span class="sxs-lookup"><span data-stu-id="e35d3-133">SAVING ALIASES</span></span>

<span data-ttu-id="e35d3-134">만든 별칭은 현재 세션에만 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-134">The aliases that you create are saved only in the current session.</span></span> <span data-ttu-id="e35d3-135">다른 세션에서 별칭을 사용 하려면 PowerShell 프로필에 별칭을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-135">To use the aliases in a different session, add the alias to your PowerShell profile.</span></span> <span data-ttu-id="e35d3-136">또는 Export-Alias cmdlet을 사용 하 여 별칭을 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-136">Or, use the Export-Alias cmdlet to save the aliases to a file.</span></span>

<span data-ttu-id="e35d3-137">더 자세한 내용을 보려면 다음을 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="e35d3-137">For more information, type:</span></span>

```powershell
Get-Help about_Profiles
```

## <a name="getting-aliases"></a><span data-ttu-id="e35d3-138">별칭 가져오기</span><span class="sxs-lookup"><span data-stu-id="e35d3-138">GETTING ALIASES</span></span>

<span data-ttu-id="e35d3-139">기본 제공 별칭, PowerShell 프로필의 별칭 및 현재 세션에서 만든 별칭을 포함 하 여 현재 세션의 모든 별칭을 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-139">To get all the aliases in the current session, including the built-in aliases, the aliases in your PowerShell profiles, and the aliases that you have created in the current session, type:</span></span>

```powershell
Get-Alias
```

<span data-ttu-id="e35d3-140">특정 별칭을 가져오려면 Get-Alias cmdlet의 Name 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-140">To get particular aliases, use the Name parameter of the Get-Alias cmdlet.</span></span> <span data-ttu-id="e35d3-141">예를 들어 "p"로 시작 하는 별칭을 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-141">For example, to get aliases that begin with "p", type:</span></span>

```powershell
Get-Alias -Name p*
```

<span data-ttu-id="e35d3-142">특정 항목에 대 한 별칭을 가져오려면 정의 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-142">To get the aliases for a particular item, use the Definition parameter.</span></span> <span data-ttu-id="e35d3-143">예를 들어 Get-ChildItem cmdlet에 대 한 별칭을 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-143">For example, to get the aliases for the Get-ChildItem cmdlet type:</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

### <a name="get-alias-output"></a><span data-ttu-id="e35d3-144">가져오기 별칭 출력</span><span class="sxs-lookup"><span data-stu-id="e35d3-144">GET-ALIAS OUTPUT</span></span>

<span data-ttu-id="e35d3-145">Get-Alias는 System.management.automation.aliasinfo 개체 (System.management.automation.aliasinfo) 인 개체의 한 가지 유형만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-145">Get-Alias returns only one type of object, an AliasInfo object (System.Management.Automation.AliasInfo).</span></span> <span data-ttu-id="e35d3-146">하이픈을 포함 하지 않는 별칭의 이름 (예: "cd")은 다음 형식으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-146">The name of aliases that don't include a hyphen, such as "cd" are displayed in the following format:</span></span>

```powershell
Get-Alias ac
```

```Output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Alias           ac -> Add-Content
```

<span data-ttu-id="e35d3-147">이렇게 하면 필요한 정보를 쉽고 빠르게 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-147">This makes it very quick and easy to get the information that you need.</span></span>

<span data-ttu-id="e35d3-148">하이픈을 포함하는 별칭에는 화살표 기반 별칭 이름 형식이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-148">The arrow-based alias name format is not used for aliases that include a hyphen.</span></span> <span data-ttu-id="e35d3-149">이러한 이름은 일반적인 약어 나 애칭 대신 cmdlet 및 함수에 대 한 기본 대체 이름이 될 수 있으며 작성자는 명확 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-149">These are likely to be preferred substitute names for cmdlets and functions, instead of typical abbreviations or nicknames, and the author might not want them to be as evident.</span></span>

## <a name="alternate-names-for-commands-with-parameters"></a><span data-ttu-id="e35d3-150">매개 변수가 있는 명령의 대체 이름</span><span class="sxs-lookup"><span data-stu-id="e35d3-150">ALTERNATE NAMES FOR COMMANDS WITH PARAMETERS</span></span>

<span data-ttu-id="e35d3-151">Cmdlet, 스크립트, 함수 또는 실행 파일에 별칭을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-151">You can assign an alias to a cmdlet, script, function, or executable file.</span></span> <span data-ttu-id="e35d3-152">명령 및 매개 변수에 별칭을 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-152">You cannot assign an alias to a command and its parameters.</span></span> <span data-ttu-id="e35d3-153">예를 들어 cmdlet에 별칭을 할당할 수는 `Get-Eventlog` 있지만 명령에 별칭을 할당할 수는 없습니다 `Get-Eventlog -LogName System` .</span><span class="sxs-lookup"><span data-stu-id="e35d3-153">For example, you can assign an alias to the `Get-Eventlog` cmdlet, but you cannot assign an alias to the `Get-Eventlog -LogName System` command.</span></span>

<span data-ttu-id="e35d3-154">명령을 포함 하는 함수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-154">You can create a function that includes the command.</span></span> <span data-ttu-id="e35d3-155">함수를 만들려면 "function" 이라는 단어를 입력 한 다음 함수 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-155">To create a function, type the word "function" followed by a name for the function.</span></span> <span data-ttu-id="e35d3-156">명령을 입력 하 고 중괄호 ()로 묶습니다 {} .</span><span class="sxs-lookup"><span data-stu-id="e35d3-156">Type the command, and enclose it in braces ({}).</span></span>

<span data-ttu-id="e35d3-157">예를 들어 다음 명령은 syslog 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-157">For example, the following command creates the syslog function.</span></span> <span data-ttu-id="e35d3-158">이 함수는 `Get-Eventlog -LogName System` 다음 명령을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-158">This function represents the `Get-Eventlog -LogName System` command:</span></span>

```powershell
function Get-SystemEventlog {Get-Eventlog -LogName System}
Set-Alias -Name syslog -Value Get-SystemEventlog
```

<span data-ttu-id="e35d3-159">이제 명령 대신 "syslog"를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-159">You can now type "syslog" instead of the command.</span></span> <span data-ttu-id="e35d3-160">새 함수에 대 한 별칭을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-160">And, you can create aliases for the new function.</span></span>

<span data-ttu-id="e35d3-161">함수에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e35d3-161">For more information about functions, type:</span></span>

```powershell
Get-Help about_Functions
```

## <a name="alias-objects"></a><span data-ttu-id="e35d3-162">별칭 개체</span><span class="sxs-lookup"><span data-stu-id="e35d3-162">ALIAS OBJECTS</span></span>

<span data-ttu-id="e35d3-163">PowerShell 별칭은 System.management.automation.aliasinfo 클래스의 인스턴스인 개체로 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-163">PowerShell aliases are represented by objects that are instances of the System.Management.Automation.AliasInfo class.</span></span> <span data-ttu-id="e35d3-164">이 형식의 개체에 대 한 자세한 내용은 PowerShell SDK의 [System.management.automation.aliasinfo 클래스][aliasinfo] 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e35d3-164">For more information about this type of object, see [AliasInfo Class][aliasinfo] in the PowerShell SDK.</span></span>

<span data-ttu-id="e35d3-165">별칭 개체의 속성 및 메서드를 보려면 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-165">To view the properties and methods of the alias objects, get the aliases.</span></span>
<span data-ttu-id="e35d3-166">그런 다음 Get-Member cmdlet으로 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-166">Then, pipe them to the Get-Member cmdlet.</span></span> <span data-ttu-id="e35d3-167">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="e35d3-167">For example:</span></span>

```powershell
Get-Alias | Get-Member
```

<span data-ttu-id="e35d3-168">별칭 등의 특정 별칭 속성 값을 보려면 `dir` 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-168">To view the values of the properties of a specific alias, such as the `dir` alias, get the alias.</span></span> <span data-ttu-id="e35d3-169">그런 다음 Format-List cmdlet으로 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-169">Then, pipe it to the Format-List cmdlet.</span></span> <span data-ttu-id="e35d3-170">예를 들어 다음 명령은 "dir" 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-170">For example, the following command gets the "dir" alias.</span></span> <span data-ttu-id="e35d3-171">그런 다음이 명령은 별칭을 Format-List cmdlet으로 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-171">Next, the command pipes the alias to the Format-List cmdlet.</span></span> <span data-ttu-id="e35d3-172">그런 다음이 명령은 와일드 카드 문자 ()와 함께 Format-List의 Property 매개 변수를 사용 \* 하 여 별칭의 모든 속성을 표시 합니다 `dir` .</span><span class="sxs-lookup"><span data-stu-id="e35d3-172">Then, the command uses the Property parameter of Format-List with a wildcard character (\*) to display all the properties of the `dir` alias.</span></span> <span data-ttu-id="e35d3-173">다음 명령은 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-173">The following command performs these tasks:</span></span>

```powershell
Get-Alias -Name dir | Format-List -Property *
```

## <a name="powershell-alias-provider"></a><span data-ttu-id="e35d3-174">PowerShell 별칭 공급자</span><span class="sxs-lookup"><span data-stu-id="e35d3-174">PowerShell ALIAS PROVIDER</span></span>

<span data-ttu-id="e35d3-175">PowerShell에는 별칭 공급자가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-175">PowerShell includes the Alias provider.</span></span> <span data-ttu-id="e35d3-176">별칭 공급자를 사용 하면 파일 시스템 드라이브와 마찬가지로 PowerShell에서 별칭을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-176">The Alias provider lets you view the aliases in PowerShell as though they were on a file system drive.</span></span>

<span data-ttu-id="e35d3-177">별칭 공급자는 Alias: 드라이브를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-177">The Alias provider exposes the Alias: drive.</span></span> <span data-ttu-id="e35d3-178">Alias: 드라이브로 이동 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-178">To go into the Alias: drive, type:</span></span>

```powershell
Set-Location Alias:
```

<span data-ttu-id="e35d3-179">드라이브의 내용을 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-179">To view the contents of the drive, type:</span></span>

```powershell
Get-ChildItem
```

<span data-ttu-id="e35d3-180">다른 PowerShell 드라이브에서 드라이브의 내용을 보려면 드라이브 이름으로 경로를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-180">To view the contents of the drive from another PowerShell drive, begin the path with the drive name.</span></span> <span data-ttu-id="e35d3-181">콜론 (:)을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-181">Include the colon (:).</span></span> <span data-ttu-id="e35d3-182">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="e35d3-182">For example:</span></span>

```powershell
Get-ChildItem -Path Alias:
```

<span data-ttu-id="e35d3-183">특정 별칭에 대 한 정보를 가져오려면 드라이브 이름과 별칭 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-183">To get information about a particular alias, type the drive name and the alias name.</span></span> <span data-ttu-id="e35d3-184">또는 이름 패턴을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-184">Or, type a name pattern.</span></span> <span data-ttu-id="e35d3-185">예를 들어 "p"로 시작 하는 모든 별칭을 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e35d3-185">For example, to get all the aliases that begin with "p", type:</span></span>

```powershell
Get-ChildItem -Path Alias:p*
```

<span data-ttu-id="e35d3-186">PowerShell 별칭 공급자에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e35d3-186">For more information about the PowerShell Alias provider, type:</span></span>

```powershell
Get-Help Alias
```

## <a name="see-also"></a><span data-ttu-id="e35d3-187">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e35d3-187">SEE ALSO</span></span>

- [<span data-ttu-id="e35d3-188">New-Alias</span><span class="sxs-lookup"><span data-stu-id="e35d3-188">New-Alias</span></span>](xref:Microsoft.PowerShell.Utility.New-Alias)
- [<span data-ttu-id="e35d3-189">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="e35d3-189">Get-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [<span data-ttu-id="e35d3-190">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="e35d3-190">Set-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Set-Alias)
- [<span data-ttu-id="e35d3-191">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="e35d3-191">Export-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [<span data-ttu-id="e35d3-192">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="e35d3-192">Import-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [<span data-ttu-id="e35d3-193">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="e35d3-193">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)
- [<span data-ttu-id="e35d3-194">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="e35d3-194">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="e35d3-195">about_functions</span><span class="sxs-lookup"><span data-stu-id="e35d3-195">about_functions</span></span>](about_functions.md)
- [<span data-ttu-id="e35d3-196">about_profiles</span><span class="sxs-lookup"><span data-stu-id="e35d3-196">about_profiles</span></span>](about_profiles.md)
- [<span data-ttu-id="e35d3-197">about_providers</span><span class="sxs-lookup"><span data-stu-id="e35d3-197">about_providers</span></span>](about_providers.md)

<!-- External links -->
[aliasinfo]: /dotnet/api/system.management.automation.aliasinfo

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Path
ms.openlocfilehash: a79f12739643a873703b39d9d07e8b7db01dfbb4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602682"
---
# <span data-ttu-id="8707c-102">Test-Path</span><span class="sxs-lookup"><span data-stu-id="8707c-102">Test-Path</span></span>

## <span data-ttu-id="8707c-103">개요</span><span class="sxs-lookup"><span data-stu-id="8707c-103">SYNOPSIS</span></span>
<span data-ttu-id="8707c-104">경로의 모든 요소가 있는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-104">Determines whether all elements of a path exist.</span></span>

## <span data-ttu-id="8707c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8707c-105">SYNTAX</span></span>

### <span data-ttu-id="8707c-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="8707c-106">Path (Default)</span></span>

```
Test-Path [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="8707c-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8707c-107">LiteralPath</span></span>

```
Test-Path -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

## <span data-ttu-id="8707c-108">설명</span><span class="sxs-lookup"><span data-stu-id="8707c-108">DESCRIPTION</span></span>

<span data-ttu-id="8707c-109">`Test-Path`Cmdlet은 경로의 모든 요소가 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-109">The `Test-Path` cmdlet determines whether all elements of the path exist.</span></span> <span data-ttu-id="8707c-110">`$True`모든 요소가 존재 하는 경우를 반환 하 고, `$False` 없는 경우를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-110">It returns `$True` if all elements exist and `$False` if any are missing.</span></span> <span data-ttu-id="8707c-111">경로 구문이 올바른지 여부와 경로가 컨테이너 또는 터미널 또는 리프 요소로 이어질 수 있는지 여부도 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-111">It can also tell whether the path syntax is valid and whether the path leads to a container or a terminal or leaf element.</span></span> <span data-ttu-id="8707c-112">`Path`가 공백 문자열 이면 `$False` 이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-112">If the `Path` is whitespace an empty string, then `$False` is returned.</span></span> <span data-ttu-id="8707c-113">`Path`이 `$null` , 배열 `$null` 또는 빈 배열인 경우 종료 되지 않는 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-113">If the `Path` is `$null`, array of `$null` or empty array, a non-terminating error is returned.</span></span>

## <span data-ttu-id="8707c-114">예제</span><span class="sxs-lookup"><span data-stu-id="8707c-114">EXAMPLES</span></span>

### <span data-ttu-id="8707c-115">예제 1: 경로 테스트</span><span class="sxs-lookup"><span data-stu-id="8707c-115">Example 1: Test a path</span></span>

```powershell
Test-Path -Path "C:\Documents and Settings\DavidC"
```

```Output
True
```

<span data-ttu-id="8707c-116">이 명령은 경로의 모든 요소, 즉 C: 디렉터리, 문서 및 설정 디렉터리 및 DavidC 디렉터리를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-116">This command checks whether all elements in the path exist, that is, the C: directory, the Documents and Settings directory, and the DavidC directory.</span></span> <span data-ttu-id="8707c-117">누락 된 항목이 있으면 cmdlet에서을 반환 `$False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-117">If any are missing, the cmdlet returns `$False`.</span></span>
<span data-ttu-id="8707c-118">그렇지 않으면 `$True`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-118">Otherwise, it returns `$True`.</span></span>

### <span data-ttu-id="8707c-119">예 2: 프로필 경로 테스트</span><span class="sxs-lookup"><span data-stu-id="8707c-119">Example 2: Test the path of a profile</span></span>

```powershell
Test-Path -Path $profile
```

```Output
False
```

```powershell
Test-Path -Path $profile -IsValid
```

```Output
True
```

<span data-ttu-id="8707c-120">이러한 명령은 PowerShell 프로필 경로를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-120">These commands test the path of the PowerShell profile.</span></span>

<span data-ttu-id="8707c-121">첫 번째 명령은 경로의 모든 요소가 있는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-121">The first command determines whether all elements in the path exist.</span></span> <span data-ttu-id="8707c-122">두 번째 명령은 경로의 구문이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-122">The second command determines whether the syntax of the path is correct.</span></span> <span data-ttu-id="8707c-123">이 경우 경로는 이지만 `$False` 구문이 올바릅니다 `$True` .</span><span class="sxs-lookup"><span data-stu-id="8707c-123">In this case, the path is `$False`, but the syntax is correct `$True`.</span></span> <span data-ttu-id="8707c-124">이러한 명령은 프로필이 `$profile` 없는 경우에도 프로필 위치를 가리키는 자동 변수인를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-124">These commands use `$profile`, the automatic variable that points to the location for the profile, even if the profile does not exist.</span></span>

<span data-ttu-id="8707c-125">자동 변수에 대한 자세한 내용은 about_Automatic_Variables를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8707c-125">For more information about automatic variables, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="8707c-126">예제 3: 지정 된 형식 외에 파일이 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="8707c-126">Example 3: Check whether there are any files besides a specified type</span></span>

```powershell
Test-Path -Path "C:\CAD\Commercial Buildings\*" -Exclude *.dwg
```

```Output
False
```

<span data-ttu-id="8707c-127">이 명령은 상용 빌딩 디렉터리에 있는 파일이 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-127">This command checks whether there are any files in the Commercial Buildings directory other than .dwg files.</span></span>

<span data-ttu-id="8707c-128">이 명령은 **path** 매개 변수를 사용 하 여 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-128">The command uses the **Path** parameter to specify the path.</span></span> <span data-ttu-id="8707c-129">경로에 공백이 포함 되어 있기 때문에 경로는 따옴표로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-129">Because the path includes a space, the path is enclosed in quotation marks.</span></span> <span data-ttu-id="8707c-130">경로 끝의 별표는 Commercial Building 디렉터리의 내용을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-130">The asterisk at the end of the path indicates the contents of the Commercial Building directory.</span></span> <span data-ttu-id="8707c-131">이와 같은 긴 경로를 사용 하 여 경로의 처음 몇 글자를 입력 한 다음 TAB 키를 사용 하 여 경로를 완성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-131">With long paths, such as this one, type the first few letters of the path, and then use the TAB key to complete the path.</span></span>

<span data-ttu-id="8707c-132">이 명령은 **Exclude** 매개 변수를 지정 하 여 평가에서 생략 되는 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-132">The command specifies the **Exclude** parameter to specify files that will be omitted from the evaluation.</span></span>

<span data-ttu-id="8707c-133">이 경우 디렉터리에는. 개의 dwg 파일만 있으므로 결과는 `$False` 입니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-133">In this case, because the directory contains only .dwg files, the result is `$False`.</span></span>

### <span data-ttu-id="8707c-134">예제 4: 파일 확인</span><span class="sxs-lookup"><span data-stu-id="8707c-134">Example 4: Check for a file</span></span>

```powershell
Test-Path -Path $profile -PathType leaf
```

```Output
True
```

<span data-ttu-id="8707c-135">이 명령은 변수에 저장 된 경로가 파일로 이어질 지 여부를 확인 `$profile` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-135">This command checks whether the path stored in the `$profile` variable leads to a file.</span></span> <span data-ttu-id="8707c-136">이 경우 PowerShell 프로필은 파일 이기 때문에 `.ps1` cmdlet은을 반환 `$True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-136">In this case, because the PowerShell profile is a `.ps1` file, the cmdlet returns `$True`.</span></span>

### <span data-ttu-id="8707c-137">예 5: 레지스트리에서 경로 확인</span><span class="sxs-lookup"><span data-stu-id="8707c-137">Example 5: Check paths in the Registry</span></span>

<span data-ttu-id="8707c-138">이러한 명령은 `Test-Path` PowerShell 레지스트리 공급자와 함께를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-138">These commands use `Test-Path` with the PowerShell registry provider.</span></span>

<span data-ttu-id="8707c-139">첫 번째 명령은 시스템에서 **Microsoft PowerShell** 레지스트리 키의 레지스트리 경로가 올바른지 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-139">The first command tests whether the registry path of the **Microsoft.PowerShell** registry key is correct on the system.</span></span> <span data-ttu-id="8707c-140">PowerShell이 올바르게 설치 된 경우 cmdlet은을 반환 `$True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-140">If PowerShell is installed correctly, the cmdlet returns `$True`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8707c-141">`Test-Path` 모든 PowerShell 공급자에서 제대로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-141">`Test-Path` does not work correctly with all PowerShell providers.</span></span> <span data-ttu-id="8707c-142">예를 들어를 사용 `Test-Path` 하 여 레지스트리 키의 경로를 테스트할 수 있지만 레지스트리 항목의 경로를 테스트 하는 데 사용 하는 경우 `$False` 레지스트리 항목이 존재 하더라도 항상를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-142">For example, you can use `Test-Path` to test the path of a registry key, but if you use it to test the path of a registry entry, it always returns `$False`, even if the registry entry is present.</span></span>

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell"
```

```Output
True
```

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell\ExecutionPolicy"
```

```Output
False
```

### <span data-ttu-id="8707c-143">예제 6: 파일이 지정 된 날짜 보다 최신인 경우 테스트</span><span class="sxs-lookup"><span data-stu-id="8707c-143">Example 6: Test if a file is newer than a specified date</span></span>

<span data-ttu-id="8707c-144">이 명령은 **Newerthan** 동적 매개 변수를 사용 하 여 컴퓨터의 "PowerShell.exe" 파일이 "7 월 13 2009" 보다 최신 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-144">This command uses the **NewerThan** dynamic parameter to determine whether the "PowerShell.exe" file on the computer is newer than "July 13, 2009".</span></span>

<span data-ttu-id="8707c-145">NewerThan 매개 변수는 파일 시스템 드라이브에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-145">The NewerThan parameter works only in file system drives.</span></span>

```powershell
Test-Path $pshome\PowerShell.exe -NewerThan "July 13, 2009"
```

```Output
True
```

### <span data-ttu-id="8707c-146">예 7: 값으로 null을 사용 하 여 경로 테스트</span><span class="sxs-lookup"><span data-stu-id="8707c-146">Example 7: Test a path with null as the value</span></span>

<span data-ttu-id="8707c-147">, 배열 또는 빈 배열에 대해 반환 된 오류는 `null` `null` 종료 되지 않는 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-147">The error returned for `null`, array of `null` or empty array is a non-terminating error.</span></span> <span data-ttu-id="8707c-148">을 사용 하 여 표시 하지 않을 수 있습니다 `-ErrorAction SilentlyContinue` .</span><span class="sxs-lookup"><span data-stu-id="8707c-148">It can be suppress by using `-ErrorAction SilentlyContinue`.</span></span> <span data-ttu-id="8707c-149">다음 예에서는 오류를 반환 하는 모든 사례를 보여 줍니다 `NullPathNotPermitted` .</span><span class="sxs-lookup"><span data-stu-id="8707c-149">The following example shows all cases which return the `NullPathNotPermitted` error.</span></span>

```powershell
Test-Path $null
Test-Path $null, $null
Test-Path @()
```

```Output
Test-Path : Cannot bind argument to parameter 'Path' because it is null.
At line:1 char:11
+ Test-Path $null
+           ~~~~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorNullNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

### <span data-ttu-id="8707c-150">예 8: 값으로 공백을 사용 하 여 경로 테스트</span><span class="sxs-lookup"><span data-stu-id="8707c-150">Example 8: Test a path with whitespace as the value</span></span>

<span data-ttu-id="8707c-151">매개 변수에 대 한 공백 또는 빈 문자열이 제공 되 면 `-Path` **False** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-151">When a whitespace or empty string is provided for the the `-Path` parameter, it returns **False**.</span></span>
<span data-ttu-id="8707c-152">다음 예제에서는 공백과 빈 문자열을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-152">The following example show whitespace and empty string.</span></span>

```powershell
Test-Path ' '
Test-Path ''
```

```Output
False
False
```

## <span data-ttu-id="8707c-153">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8707c-153">PARAMETERS</span></span>

### <span data-ttu-id="8707c-154">-Credential</span><span class="sxs-lookup"><span data-stu-id="8707c-154">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="8707c-155">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-155">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="8707c-156">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-156">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8707c-157">-제외</span><span class="sxs-lookup"><span data-stu-id="8707c-157">-Exclude</span></span>

<span data-ttu-id="8707c-158">이 cmdlet이 생략 하는 항목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-158">Specifies items that this cmdlet omits.</span></span> <span data-ttu-id="8707c-159">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-159">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="8707c-160">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-160">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="8707c-161">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-161">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8707c-162">-Filter</span><span class="sxs-lookup"><span data-stu-id="8707c-162">-Filter</span></span>

<span data-ttu-id="8707c-163">공급자의 형식 또는 언어로 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-163">Specifies a filter in the format or language of the provider.</span></span> <span data-ttu-id="8707c-164">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-164">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="8707c-165">와일드 카드 문자를 포함 한 필터 구문은 공급자에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-165">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span> <span data-ttu-id="8707c-166">필터는 개체를 검색 한 후 개체를 검색 하는 대신 개체를 검색할 때 공급자가 개체를 검색할 때 적용 하므로 다른 매개 변수 보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-166">Filters are more efficient than other parameters, because the provider applies them when it retrieves the objects instead of having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8707c-167">-포함</span><span class="sxs-lookup"><span data-stu-id="8707c-167">-Include</span></span>

<span data-ttu-id="8707c-168">이 cmdlet이 테스트할 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-168">Specifies paths that this cmdlet tests.</span></span> <span data-ttu-id="8707c-169">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-169">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="8707c-170">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-170">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="8707c-171">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-171">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8707c-172">-IsValid</span><span class="sxs-lookup"><span data-stu-id="8707c-172">-IsValid</span></span>

<span data-ttu-id="8707c-173">경로의 요소가 존재 하는지 여부에 관계 없이이 cmdlet이 경로 구문을 테스트 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-173">Indicates that this cmdlet tests the syntax of the path, regardless of whether the elements of the path exist.</span></span> <span data-ttu-id="8707c-174">이 cmdlet은 `$True` 경로 구문이 유효 하면를 반환 하 고 그렇지 않으면를 반환 `$False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-174">This cmdlet returns `$True` if the path syntax is valid and `$False` if it is not.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8707c-175">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8707c-175">-LiteralPath</span></span>

<span data-ttu-id="8707c-176">테스트할 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-176">Specifies a path to be tested.</span></span> <span data-ttu-id="8707c-177">**Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-177">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="8707c-178">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-178">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="8707c-179">PowerShell에서 이스케이프 시퀀스로 해석할 수 있는 문자가 경로에 포함 된 경우에는 해석 되지 않도록 경로를 작은따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-179">If the path includes characters that could be interpreted by PowerShell as escape sequences, you must enclose the path in single quote so that they won't be interpreted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8707c-180">-NewerThan</span><span class="sxs-lookup"><span data-stu-id="8707c-180">-NewerThan</span></span>

<span data-ttu-id="8707c-181">시간을 **DateTime** 개체로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-181">Specify a time as a **DateTime** object.</span></span>

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8707c-182">-OlderThan</span><span class="sxs-lookup"><span data-stu-id="8707c-182">-OlderThan</span></span>

<span data-ttu-id="8707c-183">시간을 **DateTime** 개체로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-183">Specify a time as a **DateTime** object.</span></span>

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8707c-184">-Path</span><span class="sxs-lookup"><span data-stu-id="8707c-184">-Path</span></span>

<span data-ttu-id="8707c-185">테스트할 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-185">Specifies a path to be tested.</span></span> <span data-ttu-id="8707c-186">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-186">Wildcard characters are permitted.</span></span> <span data-ttu-id="8707c-187">경로에 공백이 포함된 경우 경로를 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-187">If the path includes spaces, enclose it in quotation marks.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="8707c-188">-PathType</span><span class="sxs-lookup"><span data-stu-id="8707c-188">-PathType</span></span>

<span data-ttu-id="8707c-189">경로에 있는 마지막 요소의 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-189">Specifies the type of the final element in the path.</span></span> <span data-ttu-id="8707c-190">이 cmdlet은 `$True` 요소가 지정 된 형식이 면를 반환 하 고, 그렇지 않으면를 반환 `$False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-190">This cmdlet returns `$True` if the element is of the specified type and `$False` if it is not.</span></span> <span data-ttu-id="8707c-191">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8707c-192">컨테이너.</span><span class="sxs-lookup"><span data-stu-id="8707c-192">Container.</span></span>
  <span data-ttu-id="8707c-193">디렉터리 또는 레지스트리 키와 같이 다른 요소를 포함하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-193">An element that contains other elements, such as a directory or registry key.</span></span>
- <span data-ttu-id="8707c-194">수준이.</span><span class="sxs-lookup"><span data-stu-id="8707c-194">Leaf.</span></span>
  <span data-ttu-id="8707c-195">파일과 같이 다른 요소를 포함하지 않는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-195">An element that does not contain other elements, such as a file.</span></span>
- <span data-ttu-id="8707c-196">일부.</span><span class="sxs-lookup"><span data-stu-id="8707c-196">Any.</span></span>
  <span data-ttu-id="8707c-197">컨테이너 또는 리프입니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-197">Either a container or a leaf.</span></span>

<span data-ttu-id="8707c-198">경로에서 마지막 요소가 특정 유형인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-198">Tells whether the final element in the path is of a particular type.</span></span>

> [!CAUTION]
>
> <span data-ttu-id="8707c-199">최대 PowerShell 버전 6.1.2에서 **IsValid** 및 **pathtype** 스위치를 함께 지정 하면 `Test-Path` cmdlet은 **pathtype** 스위치를 무시 하 고 경로 형식의 유효성을 검사 하지 않고 구문의 유효성만 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-199">Up to PowerShell version 6.1.2, when the **IsValid** and **PathType** switches are specified together, the `Test-Path` cmdlet ignores the **PathType** switch and only validates the syntactic path without validating the path type.</span></span>
>
> <span data-ttu-id="8707c-200">[#8607 문제](https://github.com/PowerShell/PowerShell/issues/8607)에 따라이 동작을 수정 하는 것이 이후 버전에서 변경 될 수 있습니다. **IsValid** 및 **pathtype** 스위치는 개별 매개 변수 집합에 속하므로 이러한 혼동을 피하기 위해 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-200">According to [issue #8607](https://github.com/PowerShell/PowerShell/issues/8607), fixing this behavior may be a breaking change in a future version, where the **IsValid** and **PathType** switches belong to separate parameter sets, and thus, cannot be used together avoiding this confusion.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.TestPathType
Parameter Sets: (All)
Aliases: Type
Accepted values: Any, Container, Leaf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8707c-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8707c-201">CommonParameters</span></span>

<span data-ttu-id="8707c-202">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-202">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="8707c-203">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8707c-203">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8707c-204">입력</span><span class="sxs-lookup"><span data-stu-id="8707c-204">INPUTS</span></span>

### <span data-ttu-id="8707c-205">System.String</span><span class="sxs-lookup"><span data-stu-id="8707c-205">System.String</span></span>

<span data-ttu-id="8707c-206">경로를 포함 하지만 리터럴 경로를 포함 하지 않는 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-206">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="8707c-207">출력</span><span class="sxs-lookup"><span data-stu-id="8707c-207">OUTPUTS</span></span>

### <span data-ttu-id="8707c-208">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="8707c-208">System.Boolean</span></span>

<span data-ttu-id="8707c-209">이 cmdlet은 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-209">The cmdlet returns a **Boolean** value.</span></span>

## <span data-ttu-id="8707c-210">참고</span><span class="sxs-lookup"><span data-stu-id="8707c-210">NOTES</span></span>

<span data-ttu-id="8707c-211">경로 명사 ( **path** cmdlet **)를 포함** 하는 cmdlet은 경로 이름으로 작동 하며 모든 PowerShell 공급자가 해석할 수 있는 간결한 형식으로 이름을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-211">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="8707c-212">이 cmdlet은 경로 이름의 전체 또는 일부를 특정 형식으로 표시하려는 프로그램 및 스크립트에 사용하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-212">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span>
<span data-ttu-id="8707c-213">이러한 **이름은 다른 이름**, **Normpath**, **Realpath**, **Join** 또는 기타 경로 조작자를 사용할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-213">Use them as you would use **Dirname**, **Normpath**, **Realpath**, **Join**, or other path manipulators.</span></span>

<span data-ttu-id="8707c-214">는 `Test-Path` 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-214">The `Test-Path` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="8707c-215">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8707c-215">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="8707c-216">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8707c-216">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="8707c-217">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8707c-217">RELATED LINKS</span></span>

[<span data-ttu-id="8707c-218">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="8707c-218">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="8707c-219">Join-Path</span><span class="sxs-lookup"><span data-stu-id="8707c-219">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="8707c-220">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="8707c-220">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="8707c-221">Split-Path</span><span class="sxs-lookup"><span data-stu-id="8707c-221">Split-Path</span></span>](Split-Path.md)

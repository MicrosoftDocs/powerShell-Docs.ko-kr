---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: e2498c02d42123e207b49e622654d3cb881fc0fc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601458"
---
# <span data-ttu-id="3f18e-102">Split-Path</span><span class="sxs-lookup"><span data-stu-id="3f18e-102">Split-Path</span></span>

## <span data-ttu-id="3f18e-103">개요</span><span class="sxs-lookup"><span data-stu-id="3f18e-103">SYNOPSIS</span></span>
<span data-ttu-id="3f18e-104">경로의 지정된 일부를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-104">Returns the specified part of a path.</span></span>

## <span data-ttu-id="3f18e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3f18e-105">SYNTAX</span></span>

### <span data-ttu-id="3f18e-106">ParentSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="3f18e-106">ParentSet (Default)</span></span>

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="3f18e-107">LeafSet</span><span class="sxs-lookup"><span data-stu-id="3f18e-107">LeafSet</span></span>

```
Split-Path [-Path] <String[]> -Leaf [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="3f18e-108">LeafBaseSet</span><span class="sxs-lookup"><span data-stu-id="3f18e-108">LeafBaseSet</span></span>

```
Split-Path [-Path] <String[]> -LeafBase [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="3f18e-109">ExtensionSet</span><span class="sxs-lookup"><span data-stu-id="3f18e-109">ExtensionSet</span></span>

```
Split-Path [-Path] <String[]> -Extension [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="3f18e-110">QualifierSet</span><span class="sxs-lookup"><span data-stu-id="3f18e-110">QualifierSet</span></span>

```
Split-Path [-Path] <String[]> -Qualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="3f18e-111">NoQualifierSet</span><span class="sxs-lookup"><span data-stu-id="3f18e-111">NoQualifierSet</span></span>

```
Split-Path [-Path] <String[]> -NoQualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="3f18e-112">IsAbsoluteSet</span><span class="sxs-lookup"><span data-stu-id="3f18e-112">IsAbsoluteSet</span></span>

```
Split-Path [-Path] <String[]> [-Resolve] -IsAbsolute [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="3f18e-113">LiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="3f18e-113">LiteralPathSet</span></span>

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="3f18e-114">설명</span><span class="sxs-lookup"><span data-stu-id="3f18e-114">DESCRIPTION</span></span>

<span data-ttu-id="3f18e-115">`Split-Path`Cmdlet은 부모 폴더, 하위 폴더 또는 파일 이름 등 경로의 지정한 부분만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-115">The `Split-Path` cmdlet returns only the specified part of a path, such as the parent folder, a subfolder, or a file name.</span></span> <span data-ttu-id="3f18e-116">또한 분할 경로에서 참조하는 항목을 가져오고 해당 경로가 상대 경로인지 아니면 절대 경로인지 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-116">It can also get items that are referenced by the split path and tell whether the path is relative or absolute.</span></span>

<span data-ttu-id="3f18e-117">이 cmdlet을 사용하여 경로의 선택한 부분만 가져오거나 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-117">You can use this cmdlet to get or submit only a selected part of a path.</span></span>

## <span data-ttu-id="3f18e-118">예제</span><span class="sxs-lookup"><span data-stu-id="3f18e-118">EXAMPLES</span></span>

### <span data-ttu-id="3f18e-119">예제 1: 경로의 한정자 가져오기</span><span class="sxs-lookup"><span data-stu-id="3f18e-119">Example 1: Get the qualifier of a path</span></span>

```powershell
Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
```

```Output
HKCU:
```

<span data-ttu-id="3f18e-120">이 명령은 경로의 한정자만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-120">This command returns only the qualifier of the path.</span></span> <span data-ttu-id="3f18e-121">한정자는 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-121">The qualifier is the drive.</span></span>

### <span data-ttu-id="3f18e-122">예제 2: 파일 이름 표시</span><span class="sxs-lookup"><span data-stu-id="3f18e-122">Example 2: Display file names</span></span>

```powershell
Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
```

```Output
Pass1.log
Pass2.log
...
```

<span data-ttu-id="3f18e-123">이 명령은 분할 경로에서 참조하는 파일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-123">This command displays the files that are referenced by the split path.</span></span> <span data-ttu-id="3f18e-124">이 경로는 마지막 항목 (리프)으로 분할 되기 때문에 명령에 파일 이름만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-124">Because this path is split to the last item, also known as the leaf, the command displays only the file names.</span></span>

<span data-ttu-id="3f18e-125">**Resolve** 매개 변수는 분할 경로를 `Split-Path` 표시 하는 대신 분할 경로에서 참조 하는 항목을 표시 하도록에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-125">The **Resolve** parameter tells `Split-Path` to display the items that the split path references, instead of displaying the split path.</span></span>

<span data-ttu-id="3f18e-126">모든 `Split-Path` 명령과 마찬가지로이 명령은 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-126">Like all `Split-Path` commands, this command returns strings.</span></span> <span data-ttu-id="3f18e-127">이는 파일을 나타내는 **FileInfo** 개체를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-127">It does not return **FileInfo** objects that represent the files.</span></span>

### <span data-ttu-id="3f18e-128">예제 3: 부모 컨테이너 가져오기</span><span class="sxs-lookup"><span data-stu-id="3f18e-128">Example 3: Get the parent container</span></span>

```powershell
Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
```

```Output
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

<span data-ttu-id="3f18e-129">이 명령은 경로의 상위 컨테이너만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-129">This command returns only the parent containers of the path.</span></span> <span data-ttu-id="3f18e-130">분할을 지정 하는 매개 변수는 포함 되지 않으므로는 `Split-Path` 분할 위치 기본값 ( **Parent**)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-130">Because it does not include any parameters to specify the split, `Split-Path` uses the split location default, which is **Parent**.</span></span>

### <span data-ttu-id="3f18e-131">예제 4: 경로가 절대 경로 인지 확인</span><span class="sxs-lookup"><span data-stu-id="3f18e-131">Example 4: Determines whether a path is absolute</span></span>

```powershell
Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
```

```Output
False
```

<span data-ttu-id="3f18e-132">이 명령은 경로가 절대 경로인지 상대 경로인지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-132">This command determines whether the path is relative or absolute.</span></span> <span data-ttu-id="3f18e-133">이 경우 경로는 점 ()으로 표시 되는 현재 폴더를 기준으로 하기 때문에를 `.` 반환 `$False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-133">In this case, because the path is relative to the current folder, which is represented by a dot (`.`), it returns `$False`.</span></span>

### <span data-ttu-id="3f18e-134">예 5: 지정 된 경로로 위치 변경</span><span class="sxs-lookup"><span data-stu-id="3f18e-134">Example 5: Change location to a specified path</span></span>

```powershell
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

<span data-ttu-id="3f18e-135">이 명령은 사용자의 위치를 PowerShell 프로필이 포함 된 폴더로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-135">This command changes your location to the folder that contains the PowerShell profile.</span></span>

<span data-ttu-id="3f18e-136">괄호 안의 명령은를 사용 하 여 `Split-Path` 기본 제공 변수에 저장 된 경로의 부모만 반환 `$Profile` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-136">The command in parentheses uses `Split-Path` to return only the parent of the path stored in the built-in `$Profile` variable.</span></span> <span data-ttu-id="3f18e-137">**부모** 매개 변수는 기본 분할 위치 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-137">The **Parent** parameter is the default split location parameter.</span></span>
<span data-ttu-id="3f18e-138">따라서 명령에서 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-138">Therefore, you can omit it from the command.</span></span> <span data-ttu-id="3f18e-139">괄호는 명령을 먼저 실행 하기 위한 PowerShell을 직접 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-139">The parentheses direct PowerShell to run the command first.</span></span> <span data-ttu-id="3f18e-140">이는 긴 경로 이름을 가진 폴더로 이동 하는 유용한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-140">This is a useful way to move to a folder that has a long path name.</span></span>

### <span data-ttu-id="3f18e-141">예제 6: 파이프라인을 사용 하 여 경로 분할</span><span class="sxs-lookup"><span data-stu-id="3f18e-141">Example 6: Split a path by using the pipeline</span></span>

```powershell
'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
```

```Output
C:\Documents and Settings\User01\My Documents
```

<span data-ttu-id="3f18e-142">이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 에 대 한 경로를 보냅니다 `Split-Path` .</span><span class="sxs-lookup"><span data-stu-id="3f18e-142">This command uses a pipeline operator (`|`) to send a path to `Split-Path`.</span></span> <span data-ttu-id="3f18e-143">경로는 단일 토큰이라는 것을 나타내기 위해 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-143">The path is enclosed in quotation marks to indicate that it is a single token.</span></span>

## <span data-ttu-id="3f18e-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3f18e-144">PARAMETERS</span></span>

### <span data-ttu-id="3f18e-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="3f18e-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="3f18e-146">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-146">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="3f18e-147">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="3f18e-148">-확장</span><span class="sxs-lookup"><span data-stu-id="3f18e-148">-Extension</span></span>

<span data-ttu-id="3f18e-149">이 cmdlet은 리프의 확장명만 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-149">Indicates that this cmdlet returns only the extension of the leaf.</span></span> <span data-ttu-id="3f18e-150">예를 들어 경로에서 `C:\Test\Logs\Pass1.log` 만 반환 `.log` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-150">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `.log`.</span></span>

<span data-ttu-id="3f18e-151">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-151">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ExtensionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3f18e-152">-IsAbsolute</span><span class="sxs-lookup"><span data-stu-id="3f18e-152">-IsAbsolute</span></span>

<span data-ttu-id="3f18e-153">경로가 절대 경로 이면이 cmdlet $True을 반환 하 고, 상대 경로 이면 $False 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-153">Indicates that this cmdlet returns $True if the path is absolute and $False if it is relative.</span></span> <span data-ttu-id="3f18e-154">절대 경로는 길이가 0 보다 크고 점 ()을 사용 `.` 하 여 현재 경로를 나타내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-154">An absolute path has a length greater than zero and does not use a dot (`.`) to indicate the current path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3f18e-155">-리프</span><span class="sxs-lookup"><span data-stu-id="3f18e-155">-Leaf</span></span>

<span data-ttu-id="3f18e-156">이 cmdlet이 경로의 마지막 항목 또는 컨테이너만 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-156">Indicates that this cmdlet returns only the last item or container in the path.</span></span> <span data-ttu-id="3f18e-157">예를 들어 경로에서 `C:\Test\Logs\Pass1.log` pass1.log만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-157">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3f18e-158">-LeafBase</span><span class="sxs-lookup"><span data-stu-id="3f18e-158">-LeafBase</span></span>

<span data-ttu-id="3f18e-159">이 cmdlet은 리프의 기본 이름만 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-159">Indicates that this cmdlet returns only base name of the leaf.</span></span> <span data-ttu-id="3f18e-160">예를 들어 경로에서 `C:\Test\Logs\Pass1.log` 만 반환 `Pass1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-160">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `Pass1`.</span></span>

<span data-ttu-id="3f18e-161">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-161">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafBaseSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3f18e-162">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3f18e-162">-LiteralPath</span></span>

<span data-ttu-id="3f18e-163">분할할 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-163">Specifies the paths to be split.</span></span> <span data-ttu-id="3f18e-164">**Path** 와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-164">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="3f18e-165">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-165">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="3f18e-166">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="3f18e-166">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="3f18e-167">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-167">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3f18e-168">-NoQualifier</span><span class="sxs-lookup"><span data-stu-id="3f18e-168">-NoQualifier</span></span>

<span data-ttu-id="3f18e-169">이 cmdlet이 한정자가 없는 경로를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-169">Indicates that this cmdlet returns the path without the qualifier.</span></span> <span data-ttu-id="3f18e-170">파일 시스템 또는 레지스트리 공급자의 경우 한정자는 공급자 경로의 드라이브 (예: 또는)입니다 `C:` `HKCU:` .</span><span class="sxs-lookup"><span data-stu-id="3f18e-170">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span> <span data-ttu-id="3f18e-171">예를 들어 경로에서 `C:\Test\Logs\Pass1.log` 만 반환 `\Test\Logs\Pass1.log` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-171">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `\Test\Logs\Pass1.log`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3f18e-172">-부모</span><span class="sxs-lookup"><span data-stu-id="3f18e-172">-Parent</span></span>

<span data-ttu-id="3f18e-173">이 cmdlet이 경로에 지정 된 항목 또는 컨테이너의 부모 컨테이너만 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-173">Indicates that this cmdlet returns only the parent containers of the item or of the container specified by the path.</span></span> <span data-ttu-id="3f18e-174">예를 들어 경로에서을 `C:\Test\Logs\Pass1.log` 반환 `C:\Test\Logs` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-174">For example, in the path `C:\Test\Logs\Pass1.log`, it returns `C:\Test\Logs`.</span></span>
<span data-ttu-id="3f18e-175">**부모** 매개 변수는 기본 분할 위치 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-175">The **Parent** parameter is the default split location parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParentSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3f18e-176">-Path</span><span class="sxs-lookup"><span data-stu-id="3f18e-176">-Path</span></span>

<span data-ttu-id="3f18e-177">분할할 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-177">Specifies the paths to be split.</span></span> <span data-ttu-id="3f18e-178">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-178">Wildcard characters are permitted.</span></span> <span data-ttu-id="3f18e-179">경로에 공백이 포함된 경우 경로를 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-179">If the path includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="3f18e-180">이 cmdlet에 대 한 경로를 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-180">You can also pipe a path to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ParentSet, LeafSet, LeafBaseSet, ExtensionSet, QualifierSet, NoQualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="3f18e-181">-한정자</span><span class="sxs-lookup"><span data-stu-id="3f18e-181">-Qualifier</span></span>

<span data-ttu-id="3f18e-182">이 cmdlet이 지정 된 경로의 한정자만 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-182">Indicates that this cmdlet returns only the qualifier of the specified path.</span></span> <span data-ttu-id="3f18e-183">파일 시스템 또는 레지스트리 공급자의 경우 한정자는 공급자 경로의 드라이브 (예: 또는)입니다 `C:` `HKCU:` .</span><span class="sxs-lookup"><span data-stu-id="3f18e-183">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3f18e-184">-해결</span><span class="sxs-lookup"><span data-stu-id="3f18e-184">-Resolve</span></span>

<span data-ttu-id="3f18e-185">이 cmdlet은 path 요소를 표시 하는 대신 결과 분할 경로에서 참조 하는 항목을 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-185">Indicates that this cmdlet displays the items that are referenced by the resulting split path instead of displaying the path elements.</span></span>

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

### <span data-ttu-id="3f18e-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3f18e-186">CommonParameters</span></span>

<span data-ttu-id="3f18e-187">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3f18e-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3f18e-188">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f18e-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3f18e-189">입력</span><span class="sxs-lookup"><span data-stu-id="3f18e-189">INPUTS</span></span>

### <span data-ttu-id="3f18e-190">System.String</span><span class="sxs-lookup"><span data-stu-id="3f18e-190">System.String</span></span>

<span data-ttu-id="3f18e-191">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-191">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="3f18e-192">출력</span><span class="sxs-lookup"><span data-stu-id="3f18e-192">OUTPUTS</span></span>

### <span data-ttu-id="3f18e-193">System.object, System.string</span><span class="sxs-lookup"><span data-stu-id="3f18e-193">System.String, System.Boolean</span></span>

<span data-ttu-id="3f18e-194">`Split-Path` 텍스트 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-194">`Split-Path` returns text strings.</span></span> <span data-ttu-id="3f18e-195">**Resolve** 매개 변수를 지정 하는 경우는 `Split-Path` 항목의 위치를 설명 하는 문자열을 반환 합니다 .이는 **FileInfo** 또는 **RegistryKey** 개체와 같은 항목을 나타내는 개체를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-195">When you specify the **Resolve** parameter, `Split-Path` returns a string that describes the location of the items; it does not return objects that represent the items, such as a **FileInfo** or **RegistryKey** object.</span></span>

<span data-ttu-id="3f18e-196">**Isabsolute** 매개 변수를 지정 하면에서 `Split-Path` **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-196">When you specify the **IsAbsolute** parameter, `Split-Path` returns a **Boolean** value.</span></span>

## <span data-ttu-id="3f18e-197">참고</span><span class="sxs-lookup"><span data-stu-id="3f18e-197">NOTES</span></span>

- <span data-ttu-id="3f18e-198">분할 위치 매개 변수 (**한정자**, **부모**, **확장명**, **리프**, **LeafBase** 및 **noqualifier**)는 배타적입니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-198">The split location parameters (**Qualifier**, **Parent**, **Extension**, **Leaf**, **LeafBase**, and **NoQualifier**) are exclusive.</span></span> <span data-ttu-id="3f18e-199">각 명령에서 하나만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-199">You can use only one in each command.</span></span>

- <span data-ttu-id="3f18e-200">경로 명사 ( **path** cmdlet **)를 포함** 하는 cmdlet은 경로 이름으로 작동 하며 모든 PowerShell 공급자가 해석할 수 있는 간결한 형식으로 이름을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-200">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="3f18e-201">이 cmdlet은 경로 이름의 전체 또는 일부를 특정 형식으로 표시하려는 프로그램 및 스크립트에 사용하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-201">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="3f18e-202">이를 사용 하 여 파일 **이름**, **Normpath**, **Realpath**, **조인** 또는 기타 경로 조작자를 사용 하는 방식으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-202">Use them in the way that you would use **Dirname**, **Normpath**, **Realpath**, **Join**, or other path manipulators.</span></span>

- <span data-ttu-id="3f18e-203">여러 공급자와 함께 **Path** cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-203">You can use the **Path** cmdlets together with several providers.</span></span> <span data-ttu-id="3f18e-204">여기에는 파일 시스템, 레지스트리 및 인증서 공급자가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-204">These include the FileSystem, Registry, and Certificate providers.</span></span>

- <span data-ttu-id="3f18e-205">`Split-Path` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-205">`Split-Path` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="3f18e-206">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f18e-206">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="3f18e-207">자세한 내용은 About_Providers를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f18e-207">For more information, see about_Providers.</span></span>

## <span data-ttu-id="3f18e-208">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3f18e-208">RELATED LINKS</span></span>

[<span data-ttu-id="3f18e-209">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="3f18e-209">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="3f18e-210">Join-Path</span><span class="sxs-lookup"><span data-stu-id="3f18e-210">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="3f18e-211">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="3f18e-211">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="3f18e-212">Test-Path</span><span class="sxs-lookup"><span data-stu-id="3f18e-212">Test-Path</span></span>](Test-Path.md)
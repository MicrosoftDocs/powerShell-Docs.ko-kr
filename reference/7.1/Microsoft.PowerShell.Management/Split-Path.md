---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: c0ee5552e33792f208faba63dc05ddb93473bc49
ms.sourcegitcommit: 9a53e53e7a3ef9ac0a212c61005efff9e9902452
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/18/2020
ms.locfileid: "93219617"
---
# <span data-ttu-id="a8f21-103">Split-Path</span><span class="sxs-lookup"><span data-stu-id="a8f21-103">Split-Path</span></span>

## <span data-ttu-id="a8f21-104">개요</span><span class="sxs-lookup"><span data-stu-id="a8f21-104">SYNOPSIS</span></span>
<span data-ttu-id="a8f21-105">경로의 지정된 일부를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-105">Returns the specified part of a path.</span></span>

## <span data-ttu-id="a8f21-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a8f21-106">SYNTAX</span></span>

### <span data-ttu-id="a8f21-107">ParentSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="a8f21-107">ParentSet (Default)</span></span>

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="a8f21-108">LeafSet</span><span class="sxs-lookup"><span data-stu-id="a8f21-108">LeafSet</span></span>

```
Split-Path [-Path] <String[]> -Leaf [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="a8f21-109">LeafBaseSet</span><span class="sxs-lookup"><span data-stu-id="a8f21-109">LeafBaseSet</span></span>

```
Split-Path [-Path] <String[]> -LeafBase [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="a8f21-110">ExtensionSet</span><span class="sxs-lookup"><span data-stu-id="a8f21-110">ExtensionSet</span></span>

```
Split-Path [-Path] <String[]> -Extension [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="a8f21-111">QualifierSet</span><span class="sxs-lookup"><span data-stu-id="a8f21-111">QualifierSet</span></span>

```
Split-Path [-Path] <String[]> -Qualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="a8f21-112">NoQualifierSet</span><span class="sxs-lookup"><span data-stu-id="a8f21-112">NoQualifierSet</span></span>

```
Split-Path [-Path] <String[]> -NoQualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="a8f21-113">IsAbsoluteSet</span><span class="sxs-lookup"><span data-stu-id="a8f21-113">IsAbsoluteSet</span></span>

```
Split-Path [-Path] <String[]> [-Resolve] -IsAbsolute [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="a8f21-114">LiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="a8f21-114">LiteralPathSet</span></span>

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="a8f21-115">설명</span><span class="sxs-lookup"><span data-stu-id="a8f21-115">DESCRIPTION</span></span>

<span data-ttu-id="a8f21-116">`Split-Path`Cmdlet은 부모 폴더, 하위 폴더 또는 파일 이름 등 경로의 지정한 부분만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-116">The `Split-Path` cmdlet returns only the specified part of a path, such as the parent folder, a subfolder, or a file name.</span></span> <span data-ttu-id="a8f21-117">또한 분할 경로에서 참조하는 항목을 가져오고 해당 경로가 상대 경로인지 아니면 절대 경로인지 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-117">It can also get items that are referenced by the split path and tell whether the path is relative or absolute.</span></span>

<span data-ttu-id="a8f21-118">이 cmdlet을 사용하여 경로의 선택한 부분만 가져오거나 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-118">You can use this cmdlet to get or submit only a selected part of a path.</span></span>

## <span data-ttu-id="a8f21-119">예제</span><span class="sxs-lookup"><span data-stu-id="a8f21-119">EXAMPLES</span></span>

### <span data-ttu-id="a8f21-120">예제 1: 경로의 한정자 가져오기</span><span class="sxs-lookup"><span data-stu-id="a8f21-120">Example 1: Get the qualifier of a path</span></span>

```powershell
Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
```

```Output
HKCU:
```

<span data-ttu-id="a8f21-121">이 명령은 경로의 한정자만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-121">This command returns only the qualifier of the path.</span></span> <span data-ttu-id="a8f21-122">한정자는 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-122">The qualifier is the drive.</span></span>

### <span data-ttu-id="a8f21-123">예제 2: 파일 이름 표시</span><span class="sxs-lookup"><span data-stu-id="a8f21-123">Example 2: Display file names</span></span>

```powershell
Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
```

```Output
Pass1.log
Pass2.log
...
```

<span data-ttu-id="a8f21-124">이 명령은 분할 경로에서 참조하는 파일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-124">This command displays the files that are referenced by the split path.</span></span> <span data-ttu-id="a8f21-125">이 경로는 마지막 항목 (리프)으로 분할 되기 때문에 명령에 파일 이름만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-125">Because this path is split to the last item, also known as the leaf, the command displays only the file names.</span></span>

<span data-ttu-id="a8f21-126">**Resolve** 매개 변수는 분할 경로를 `Split-Path` 표시 하는 대신 분할 경로에서 참조 하는 항목을 표시 하도록에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-126">The **Resolve** parameter tells `Split-Path` to display the items that the split path references, instead of displaying the split path.</span></span>

<span data-ttu-id="a8f21-127">모든 `Split-Path` 명령과 마찬가지로이 명령은 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-127">Like all `Split-Path` commands, this command returns strings.</span></span> <span data-ttu-id="a8f21-128">이는 파일을 나타내는 **FileInfo** 개체를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-128">It does not return **FileInfo** objects that represent the files.</span></span>

### <span data-ttu-id="a8f21-129">예제 3: 부모 컨테이너 가져오기</span><span class="sxs-lookup"><span data-stu-id="a8f21-129">Example 3: Get the parent container</span></span>

```powershell
Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
```

```Output
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

<span data-ttu-id="a8f21-130">이 명령은 경로의 상위 컨테이너만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-130">This command returns only the parent containers of the path.</span></span> <span data-ttu-id="a8f21-131">분할을 지정 하는 매개 변수는 포함 되지 않으므로는 `Split-Path` 분할 위치 기본값 ( **Parent** )을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-131">Because it does not include any parameters to specify the split, `Split-Path` uses the split location default, which is **Parent**.</span></span>

### <span data-ttu-id="a8f21-132">예제 4: 경로가 절대 경로 인지 확인</span><span class="sxs-lookup"><span data-stu-id="a8f21-132">Example 4: Determines whether a path is absolute</span></span>

```powershell
Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
```

```Output
False
```

<span data-ttu-id="a8f21-133">이 명령은 경로가 절대 경로인지 상대 경로인지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-133">This command determines whether the path is relative or absolute.</span></span> <span data-ttu-id="a8f21-134">이 경우 경로는 점 ()으로 표시 되는 현재 폴더를 기준으로 하기 때문에를 `.` 반환 `$False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-134">In this case, because the path is relative to the current folder, which is represented by a dot (`.`), it returns `$False`.</span></span>

### <span data-ttu-id="a8f21-135">예 5: 지정 된 경로로 위치 변경</span><span class="sxs-lookup"><span data-stu-id="a8f21-135">Example 5: Change location to a specified path</span></span>

```powershell
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

<span data-ttu-id="a8f21-136">이 명령은 사용자의 위치를 PowerShell 프로필이 포함 된 폴더로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-136">This command changes your location to the folder that contains the PowerShell profile.</span></span>

<span data-ttu-id="a8f21-137">괄호 안의 명령은를 사용 하 여 `Split-Path` 기본 제공 변수에 저장 된 경로의 부모만 반환 `$Profile` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-137">The command in parentheses uses `Split-Path` to return only the parent of the path stored in the built-in `$Profile` variable.</span></span> <span data-ttu-id="a8f21-138">**부모** 매개 변수는 기본 분할 위치 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-138">The **Parent** parameter is the default split location parameter.</span></span>
<span data-ttu-id="a8f21-139">따라서 명령에서 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-139">Therefore, you can omit it from the command.</span></span> <span data-ttu-id="a8f21-140">괄호는 명령을 먼저 실행 하기 위한 PowerShell을 직접 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-140">The parentheses direct PowerShell to run the command first.</span></span> <span data-ttu-id="a8f21-141">이는 긴 경로 이름을 가진 폴더로 이동 하는 유용한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-141">This is a useful way to move to a folder that has a long path name.</span></span>

### <span data-ttu-id="a8f21-142">예제 6: 파이프라인을 사용 하 여 경로 분할</span><span class="sxs-lookup"><span data-stu-id="a8f21-142">Example 6: Split a path by using the pipeline</span></span>

```powershell
'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
```

```Output
C:\Documents and Settings\User01\My Documents
```

<span data-ttu-id="a8f21-143">이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 에 대 한 경로를 보냅니다 `Split-Path` .</span><span class="sxs-lookup"><span data-stu-id="a8f21-143">This command uses a pipeline operator (`|`) to send a path to `Split-Path`.</span></span> <span data-ttu-id="a8f21-144">경로는 단일 토큰이라는 것을 나타내기 위해 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-144">The path is enclosed in quotation marks to indicate that it is a single token.</span></span>

## <span data-ttu-id="a8f21-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a8f21-145">PARAMETERS</span></span>

### <span data-ttu-id="a8f21-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="a8f21-146">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a8f21-147">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-147">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="a8f21-148">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-148">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="a8f21-149">-확장</span><span class="sxs-lookup"><span data-stu-id="a8f21-149">-Extension</span></span>

<span data-ttu-id="a8f21-150">이 cmdlet은 리프의 확장명만 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-150">Indicates that this cmdlet returns only the extension of the leaf.</span></span> <span data-ttu-id="a8f21-151">예를 들어 경로에서 `C:\Test\Logs\Pass1.log` 만 반환 `.log` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-151">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `.log`.</span></span>

<span data-ttu-id="a8f21-152">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-152">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="a8f21-153">-IsAbsolute</span><span class="sxs-lookup"><span data-stu-id="a8f21-153">-IsAbsolute</span></span>

<span data-ttu-id="a8f21-154">경로가 절대 경로 이면이 cmdlet $True을 반환 하 고, 상대 경로 이면 $False 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-154">Indicates that this cmdlet returns $True if the path is absolute and $False if it is relative.</span></span> <span data-ttu-id="a8f21-155">절대 경로는 길이가 0 보다 크고 점 ()을 사용 `.` 하 여 현재 경로를 나타내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-155">An absolute path has a length greater than zero and does not use a dot (`.`) to indicate the current path.</span></span>

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

### <span data-ttu-id="a8f21-156">-리프</span><span class="sxs-lookup"><span data-stu-id="a8f21-156">-Leaf</span></span>

<span data-ttu-id="a8f21-157">이 cmdlet이 경로의 마지막 항목 또는 컨테이너만 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-157">Indicates that this cmdlet returns only the last item or container in the path.</span></span> <span data-ttu-id="a8f21-158">예를 들어 경로에서 `C:\Test\Logs\Pass1.log` pass1.log만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-158">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only Pass1.log.</span></span>

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

### <span data-ttu-id="a8f21-159">-LeafBase</span><span class="sxs-lookup"><span data-stu-id="a8f21-159">-LeafBase</span></span>

<span data-ttu-id="a8f21-160">이 cmdlet은 리프의 기본 이름만 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-160">Indicates that this cmdlet returns only base name of the leaf.</span></span> <span data-ttu-id="a8f21-161">예를 들어 경로에서 `C:\Test\Logs\Pass1.log` 만 반환 `Pass1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-161">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `Pass1`.</span></span>

<span data-ttu-id="a8f21-162">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-162">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="a8f21-163">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a8f21-163">-LiteralPath</span></span>

<span data-ttu-id="a8f21-164">분할할 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-164">Specifies the paths to be split.</span></span> <span data-ttu-id="a8f21-165">**Path** 와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-165">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="a8f21-166">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-166">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="a8f21-167">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="a8f21-167">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a8f21-168">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-168">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="a8f21-169">-NoQualifier</span><span class="sxs-lookup"><span data-stu-id="a8f21-169">-NoQualifier</span></span>

<span data-ttu-id="a8f21-170">이 cmdlet이 한정자가 없는 경로를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-170">Indicates that this cmdlet returns the path without the qualifier.</span></span> <span data-ttu-id="a8f21-171">파일 시스템 또는 레지스트리 공급자의 경우 한정자는 공급자 경로의 드라이브 (예: 또는)입니다 `C:` `HKCU:` .</span><span class="sxs-lookup"><span data-stu-id="a8f21-171">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span> <span data-ttu-id="a8f21-172">예를 들어 경로에서 `C:\Test\Logs\Pass1.log` 만 반환 `\Test\Logs\Pass1.log` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-172">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `\Test\Logs\Pass1.log`.</span></span>

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

### <span data-ttu-id="a8f21-173">-부모</span><span class="sxs-lookup"><span data-stu-id="a8f21-173">-Parent</span></span>

<span data-ttu-id="a8f21-174">이 cmdlet이 경로에 지정 된 항목 또는 컨테이너의 부모 컨테이너만 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-174">Indicates that this cmdlet returns only the parent containers of the item or of the container specified by the path.</span></span> <span data-ttu-id="a8f21-175">예를 들어 경로에서을 `C:\Test\Logs\Pass1.log` 반환 `C:\Test\Logs` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-175">For example, in the path `C:\Test\Logs\Pass1.log`, it returns `C:\Test\Logs`.</span></span>
<span data-ttu-id="a8f21-176">**부모** 매개 변수는 기본 분할 위치 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-176">The **Parent** parameter is the default split location parameter.</span></span>

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

### <span data-ttu-id="a8f21-177">-Path</span><span class="sxs-lookup"><span data-stu-id="a8f21-177">-Path</span></span>

<span data-ttu-id="a8f21-178">분할할 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-178">Specifies the paths to be split.</span></span> <span data-ttu-id="a8f21-179">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-179">Wildcard characters are permitted.</span></span> <span data-ttu-id="a8f21-180">경로에 공백이 포함된 경우 경로를 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-180">If the path includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="a8f21-181">이 cmdlet에 대 한 경로를 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-181">You can also pipe a path to this cmdlet.</span></span>

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

### <span data-ttu-id="a8f21-182">-한정자</span><span class="sxs-lookup"><span data-stu-id="a8f21-182">-Qualifier</span></span>

<span data-ttu-id="a8f21-183">이 cmdlet이 지정 된 경로의 한정자만 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-183">Indicates that this cmdlet returns only the qualifier of the specified path.</span></span> <span data-ttu-id="a8f21-184">파일 시스템 또는 레지스트리 공급자의 경우 한정자는 공급자 경로의 드라이브 (예: 또는)입니다 `C:` `HKCU:` .</span><span class="sxs-lookup"><span data-stu-id="a8f21-184">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span>

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

### <span data-ttu-id="a8f21-185">-해결</span><span class="sxs-lookup"><span data-stu-id="a8f21-185">-Resolve</span></span>

<span data-ttu-id="a8f21-186">이 cmdlet은 path 요소를 표시 하는 대신 결과 분할 경로에서 참조 하는 항목을 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-186">Indicates that this cmdlet displays the items that are referenced by the resulting split path instead of displaying the path elements.</span></span>

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

### <span data-ttu-id="a8f21-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a8f21-187">CommonParameters</span></span>

<span data-ttu-id="a8f21-188">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a8f21-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a8f21-189">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a8f21-189">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a8f21-190">입력</span><span class="sxs-lookup"><span data-stu-id="a8f21-190">INPUTS</span></span>

### <span data-ttu-id="a8f21-191">System.String</span><span class="sxs-lookup"><span data-stu-id="a8f21-191">System.String</span></span>

<span data-ttu-id="a8f21-192">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-192">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="a8f21-193">출력</span><span class="sxs-lookup"><span data-stu-id="a8f21-193">OUTPUTS</span></span>

### <span data-ttu-id="a8f21-194">System.object, System.string</span><span class="sxs-lookup"><span data-stu-id="a8f21-194">System.String, System.Boolean</span></span>

<span data-ttu-id="a8f21-195">`Split-Path` 텍스트 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-195">`Split-Path` returns text strings.</span></span> <span data-ttu-id="a8f21-196">**Resolve** 매개 변수를 지정 하는 경우는 `Split-Path` 항목의 위치를 설명 하는 문자열을 반환 합니다 .이는 **FileInfo** 또는 **RegistryKey** 개체와 같은 항목을 나타내는 개체를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-196">When you specify the **Resolve** parameter, `Split-Path` returns a string that describes the location of the items; it does not return objects that represent the items, such as a **FileInfo** or **RegistryKey** object.</span></span>

<span data-ttu-id="a8f21-197">**Isabsolute** 매개 변수를 지정 하면에서 `Split-Path` **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-197">When you specify the **IsAbsolute** parameter, `Split-Path` returns a **Boolean** value.</span></span>

## <span data-ttu-id="a8f21-198">참고</span><span class="sxs-lookup"><span data-stu-id="a8f21-198">NOTES</span></span>

- <span data-ttu-id="a8f21-199">분할 위치 매개 변수 ( **한정자** , **부모** , **확장명** , **리프** , **LeafBase** 및 **noqualifier** )는 배타적입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-199">The split location parameters ( **Qualifier** , **Parent** , **Extension** , **Leaf** , **LeafBase** , and **NoQualifier** ) are exclusive.</span></span> <span data-ttu-id="a8f21-200">각 명령에서 하나만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-200">You can use only one in each command.</span></span>

- <span data-ttu-id="a8f21-201">경로 명사 ( **path** cmdlet **)를 포함** 하는 cmdlet은 경로 이름으로 작동 하며 모든 PowerShell 공급자가 해석할 수 있는 간결한 형식으로 이름을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-201">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="a8f21-202">이 cmdlet은 경로 이름의 전체 또는 일부를 특정 형식으로 표시하려는 프로그램 및 스크립트에 사용하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-202">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="a8f21-203">이를 사용 하 여 파일 **이름** , **Normpath** , **Realpath** , **조인** 또는 기타 경로 조작자를 사용 하는 방식으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-203">Use them in the way that you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

- <span data-ttu-id="a8f21-204">여러 공급자와 함께 **Path** cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-204">You can use the **Path** cmdlets together with several providers.</span></span> <span data-ttu-id="a8f21-205">여기에는 파일 시스템, 레지스트리 및 인증서 공급자가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-205">These include the FileSystem, Registry, and Certificate providers.</span></span>

- <span data-ttu-id="a8f21-206">`Split-Path` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-206">`Split-Path` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a8f21-207">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f21-207">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="a8f21-208">자세한 내용은 About_Providers를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a8f21-208">For more information, see about_Providers.</span></span>

## <span data-ttu-id="a8f21-209">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a8f21-209">RELATED LINKS</span></span>

[<span data-ttu-id="a8f21-210">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="a8f21-210">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="a8f21-211">Join-Path</span><span class="sxs-lookup"><span data-stu-id="a8f21-211">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="a8f21-212">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="a8f21-212">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="a8f21-213">Test-Path</span><span class="sxs-lookup"><span data-stu-id="a8f21-213">Test-Path</span></span>](Test-Path.md)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: d5a4e16f06ae98532f9716deb87dcadac50f8081
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211529"
---
# <span data-ttu-id="e2532-103">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="e2532-103">Resolve-Path</span></span>

## <span data-ttu-id="e2532-104">개요</span><span class="sxs-lookup"><span data-stu-id="e2532-104">SYNOPSIS</span></span>
<span data-ttu-id="e2532-105">경로에서 와일드카드 문자를 확인하고 경로 내용을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-105">Resolves the wildcard characters in a path, and displays the path contents.</span></span>

## <span data-ttu-id="e2532-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e2532-106">SYNTAX</span></span>

### <span data-ttu-id="e2532-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="e2532-107">Path (Default)</span></span>

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="e2532-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e2532-108">LiteralPath</span></span>

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="e2532-109">설명</span><span class="sxs-lookup"><span data-stu-id="e2532-109">DESCRIPTION</span></span>

<span data-ttu-id="e2532-110">`Resolve-Path`Cmdlet은 지정 된 위치에서 와일드 카드 패턴과 일치 하는 항목과 컨테이너를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-110">The `Resolve-Path` cmdlet displays the items and containers that match the wildcard pattern at the location specified.</span></span> <span data-ttu-id="e2532-111">일치 항목에는 파일, 폴더, 레지스트리 키 또는 PSDrive 공급자에서 액세스할 수 있는 기타 개체가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-111">The match can include files, folders, registry keys, or any other object accessible from a PSDrive provider.</span></span>

## <span data-ttu-id="e2532-112">예제</span><span class="sxs-lookup"><span data-stu-id="e2532-112">EXAMPLES</span></span>

### <span data-ttu-id="e2532-113">예 1: 홈 폴더 경로를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-113">Example 1: Resolve the home folder path</span></span>

<span data-ttu-id="e2532-114">물결표 문자 (~)는 현재 사용자의 홈 폴더에 대 한 약식 표기법입니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-114">The tilde character (~) is shorthand notation for the current user's home folder.</span></span> <span data-ttu-id="e2532-115">이 예에서는 정규화 `Resolve-Path` 된 경로 값을 반환 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-115">This example shows `Resolve-Path` returning the fully qualified path value.</span></span>

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### <span data-ttu-id="e2532-116">예 2: Windows 폴더의 경로 확인</span><span class="sxs-lookup"><span data-stu-id="e2532-116">Example 2: Resolve the path of the Windows folder</span></span>

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="e2532-117">이 명령은 C: 드라이브의 루트에서 실행 하면 C: 드라이브의 Windows 폴더 경로를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-117">When run from the root of the C: drive, this command returns the path of the Windows folder in the C: drive.</span></span>

### <span data-ttu-id="e2532-118">예제 3: Windows 폴더의 모든 경로 가져오기</span><span class="sxs-lookup"><span data-stu-id="e2532-118">Example 3: Get all paths in the Windows folder</span></span>

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

<span data-ttu-id="e2532-119">이 명령은 C:\Windows 폴더의 모든 폴더를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-119">This command returns all of the folders in the C:\Windows folder.</span></span> <span data-ttu-id="e2532-120">이 명령은 파이프라인 연산자 (|)를 사용 하 여 경로 문자열을로 보냅니다 `Resolve-Path` .</span><span class="sxs-lookup"><span data-stu-id="e2532-120">The command uses a pipeline operator (|) to send a path string to `Resolve-Path`.</span></span>

### <span data-ttu-id="e2532-121">예제 4: UNC 경로 확인</span><span class="sxs-lookup"><span data-stu-id="e2532-121">Example 4: Resolve a UNC path</span></span>

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

<span data-ttu-id="e2532-122">이 명령은 UNC(범용 명명 규칙) 경로를 확인하며 경로의 공유를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-122">This command resolves a Universal Naming Convention (UNC) path and returns the shares in the path.</span></span>

### <span data-ttu-id="e2532-123">예 5: 상대 경로 가져오기</span><span class="sxs-lookup"><span data-stu-id="e2532-123">Example 5: Get relative paths</span></span>

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

<span data-ttu-id="e2532-124">이 명령은 C: 드라이브 루트에서 디렉터리에 대한 상대 경로를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-124">This command returns relative paths for the directories at the root of the C: drive.</span></span>

### <span data-ttu-id="e2532-125">예제 6: 대괄호가 포함 된 경로 확인</span><span class="sxs-lookup"><span data-stu-id="e2532-125">Example 6: Resolve a path containing brackets</span></span>

<span data-ttu-id="e2532-126">이 예제에서는 **LiteralPath** 매개 변수를 사용 하 여 테스트 \[ xml 하위 폴더의 경로를 확인 합니다 \] .</span><span class="sxs-lookup"><span data-stu-id="e2532-126">This example uses the **LiteralPath** parameter to resolve the path of the Test\[xml\] subfolder.</span></span>
<span data-ttu-id="e2532-127">**LiteralPath** 를 사용 하면 대괄호가 정규식이 아닌 일반 문자로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-127">Using **LiteralPath** causes the brackets to be treated as normal characters rather than a regular expression.</span></span>

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## <span data-ttu-id="e2532-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e2532-128">PARAMETERS</span></span>

### <span data-ttu-id="e2532-129">-Credential</span><span class="sxs-lookup"><span data-stu-id="e2532-129">-Credential</span></span>

<span data-ttu-id="e2532-130">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-130">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="e2532-131">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-131">The default is the current user.</span></span>

<span data-ttu-id="e2532-132">User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나 **PSCredential** 개체를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-132">Type a user name, such as User01 or Domain01\User01, or pass a **PSCredential** object.</span></span> <span data-ttu-id="e2532-133">Cmdlet을 사용 하 여 **PSCredential** 개체를 만들 수 있습니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="e2532-133">You can create a **PSCredential** object using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="e2532-134">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-134">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="e2532-135">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-135">This parameter is not supported by any providers installed with PowerShell.</span></span>

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

### <span data-ttu-id="e2532-136">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e2532-136">-LiteralPath</span></span>

<span data-ttu-id="e2532-137">확인할 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-137">Specifies the path to be resolved.</span></span>
<span data-ttu-id="e2532-138">**LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-138">The value of the **LiteralPath** parameter is used exactly as typed.</span></span>
<span data-ttu-id="e2532-139">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-139">No characters are interpreted as wildcard characters.</span></span>
<span data-ttu-id="e2532-140">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="e2532-140">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="e2532-141">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-141">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="e2532-142">-Path</span><span class="sxs-lookup"><span data-stu-id="e2532-142">-Path</span></span>

<span data-ttu-id="e2532-143">확인할 PowerShell 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-143">Specifies the PowerShell path to resolve.</span></span>
<span data-ttu-id="e2532-144">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-144">This parameter is required.</span></span>
<span data-ttu-id="e2532-145">경로 문자열을로 파이프 할 수도 있습니다 `Resolve-Path` .</span><span class="sxs-lookup"><span data-stu-id="e2532-145">You can also pipe a path string to `Resolve-Path`.</span></span>
<span data-ttu-id="e2532-146">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-146">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e2532-147">-상대</span><span class="sxs-lookup"><span data-stu-id="e2532-147">-Relative</span></span>

<span data-ttu-id="e2532-148">이 cmdlet이 상대 경로를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-148">Indicates that this cmdlet returns a relative path.</span></span>

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

### <span data-ttu-id="e2532-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e2532-149">CommonParameters</span></span>

<span data-ttu-id="e2532-150">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e2532-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e2532-151">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2532-151">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="e2532-152">입력</span><span class="sxs-lookup"><span data-stu-id="e2532-152">INPUTS</span></span>

### <span data-ttu-id="e2532-153">System.String</span><span class="sxs-lookup"><span data-stu-id="e2532-153">System.String</span></span>

<span data-ttu-id="e2532-154">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-154">You can pipe a string that contains a path to this cmdlet</span></span>

## <span data-ttu-id="e2532-155">출력</span><span class="sxs-lookup"><span data-stu-id="e2532-155">OUTPUTS</span></span>

### <span data-ttu-id="e2532-156">System.web. PathInfo, System.string</span><span class="sxs-lookup"><span data-stu-id="e2532-156">System.Management.Automation.PathInfo, System.String</span></span>

<span data-ttu-id="e2532-157">**Pathinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-157">Returns a **PathInfo** object.</span></span> <span data-ttu-id="e2532-158">**상대** 매개 변수를 지정 하는 경우 확인 된 경로에 대 한 문자열 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-158">Returns a string value for the resolved path if you specify the **Relative** parameter.</span></span>

## <span data-ttu-id="e2532-159">참고</span><span class="sxs-lookup"><span data-stu-id="e2532-159">NOTES</span></span>

<span data-ttu-id="e2532-160">`*-Path`Cmdlet은 파일 시스템, 레지스트리 및 인증서 공급자와 함께 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-160">The `*-Path` cmdlets work with the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="e2532-161">`Resolve-Path` 는 모든 공급자에서 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-161">`Resolve-Path` is designed to work with any provider.</span></span> <span data-ttu-id="e2532-162">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-162">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="e2532-163">자세한 내용은 [about_providers](../microsoft.powershell.core/about/about_providers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e2532-163">For more information, see [about_providers](../microsoft.powershell.core/about/about_providers.md).</span></span>

<span data-ttu-id="e2532-164">`Resolve-Path` 기존 경로만 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-164">`Resolve-Path` only resolves existing paths.</span></span> <span data-ttu-id="e2532-165">아직 존재 하지 않는 위치를 확인 하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2532-165">It cannot be used to resolve a location that does not exist yet.</span></span>

## <span data-ttu-id="e2532-166">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e2532-166">RELATED LINKS</span></span>

[<span data-ttu-id="e2532-167">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="e2532-167">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="e2532-168">Join-Path</span><span class="sxs-lookup"><span data-stu-id="e2532-168">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="e2532-169">Split-Path</span><span class="sxs-lookup"><span data-stu-id="e2532-169">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="e2532-170">Test-Path</span><span class="sxs-lookup"><span data-stu-id="e2532-170">Test-Path</span></span>](Test-Path.md)


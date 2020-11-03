---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: fa66e42e182a7dea830ab30373682e4d1e6601e3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210626"
---
# <span data-ttu-id="061e1-103">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="061e1-103">Convert-Path</span></span>

## <span data-ttu-id="061e1-104">개요</span><span class="sxs-lookup"><span data-stu-id="061e1-104">SYNOPSIS</span></span>
<span data-ttu-id="061e1-105">PowerShell 경로에서 PowerShell 공급자 경로로 경로를 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-105">Converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="061e1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="061e1-106">SYNTAX</span></span>

### <span data-ttu-id="061e1-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="061e1-107">Path (Default)</span></span>

```
Convert-Path [-Path] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="061e1-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="061e1-108">LiteralPath</span></span>

```
Convert-Path -LiteralPath <String[]> [<CommonParameters>]
```

## <span data-ttu-id="061e1-109">설명</span><span class="sxs-lookup"><span data-stu-id="061e1-109">DESCRIPTION</span></span>

<span data-ttu-id="061e1-110">`Convert-Path`Cmdlet은 powershell 경로에서 powershell 공급자 경로로 경로를 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-110">The `Convert-Path` cmdlet converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="061e1-111">예제</span><span class="sxs-lookup"><span data-stu-id="061e1-111">EXAMPLES</span></span>

### <span data-ttu-id="061e1-112">예제 1: 작업 디렉터리를 표준 파일 시스템 경로로 변환</span><span class="sxs-lookup"><span data-stu-id="061e1-112">Example 1: Convert the working directory to a standard file system path</span></span>

<span data-ttu-id="061e1-113">이 예에서는 점 ()으로 표시 되는 현재 작업 디렉터리를 `.` 표준 파일 시스템 경로로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-113">This example converts the current working directory, which is represented by a dot (`.`), to a standard FileSystem path.</span></span>

```
PS C:\> Convert-Path .
C:\
```

### <span data-ttu-id="061e1-114">예제 2: 공급자 경로를 표준 레지스트리 경로로 변환</span><span class="sxs-lookup"><span data-stu-id="061e1-114">Example 2: Convert a provider path to a standard registry path</span></span>

<span data-ttu-id="061e1-115">이 예에서는 PowerShell 공급자 경로를 표준 레지스트리 경로로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-115">This example converts the PowerShell provider path to a standard registry path.</span></span>

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### <span data-ttu-id="061e1-116">예제 3: 경로를 문자열로 변환</span><span class="sxs-lookup"><span data-stu-id="061e1-116">Example 3: Convert a path to a string</span></span>

<span data-ttu-id="061e1-117">이 예에서는 FileSystem 공급자 인 현재 공급자의 홈 디렉터리에 대 한 경로를 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-117">This example converts the path to the home directory of the current provider, which is the FileSystem provider, to a string.</span></span>

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## <span data-ttu-id="061e1-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="061e1-118">PARAMETERS</span></span>

### <span data-ttu-id="061e1-119">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="061e1-119">-LiteralPath</span></span>

<span data-ttu-id="061e1-120">변환할 경로를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-120">Specifies, as a string array, the path to be converted.</span></span> <span data-ttu-id="061e1-121">**LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-121">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="061e1-122">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-122">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="061e1-123">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="061e1-123">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="061e1-124">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-124">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="061e1-125">-Path</span><span class="sxs-lookup"><span data-stu-id="061e1-125">-Path</span></span>

<span data-ttu-id="061e1-126">변환할 PowerShell 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-126">Specifies the PowerShell path to be converted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="061e1-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="061e1-127">CommonParameters</span></span>

<span data-ttu-id="061e1-128">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="061e1-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="061e1-129">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="061e1-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="061e1-130">입력</span><span class="sxs-lookup"><span data-stu-id="061e1-130">INPUTS</span></span>

### <span data-ttu-id="061e1-131">System.String</span><span class="sxs-lookup"><span data-stu-id="061e1-131">System.String</span></span>

<span data-ttu-id="061e1-132">리터럴 경로를 제외 하 고이 cmdlet에 경로를 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-132">You can pipe a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="061e1-133">출력</span><span class="sxs-lookup"><span data-stu-id="061e1-133">OUTPUTS</span></span>

### <span data-ttu-id="061e1-134">System.String</span><span class="sxs-lookup"><span data-stu-id="061e1-134">System.String</span></span>

<span data-ttu-id="061e1-135">이 cmdlet은 변환 된 경로를 포함 하는 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-135">This cmdlet returns a string that contains the converted path.</span></span>

## <span data-ttu-id="061e1-136">참고</span><span class="sxs-lookup"><span data-stu-id="061e1-136">NOTES</span></span>

<span data-ttu-id="061e1-137">경로 명사를 포함 하는 cmdlet은 경로 이름을 조작 하 고 모든 PowerShell 공급자가 해석할 수 있는 간결한 형식으로 이름을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-137">The cmdlets that contain the Path noun manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="061e1-138">이 cmdlet은 경로 이름의 전체 또는 일부를 특정 형식으로 표시하려는 프로그램 및 스크립트에 사용하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-138">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="061e1-139">이를 사용 하 여 다른 **이름** , **Normpath** , **Realpath** , **Join** 또는 기타 경로 조작자를 사용 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-139">Use them like you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

<span data-ttu-id="061e1-140">파일 시스템, 레지스트리 및 인증서 공급자를 포함하여 여러 공급자와 함께 Path cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-140">You can use the path cmdlets with several providers, including the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="061e1-141">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-141">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="061e1-142">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-142">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="061e1-143">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="061e1-143">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="061e1-144">`Convert-Path` 기존 경로만 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-144">`Convert-Path` only converts existing paths.</span></span> <span data-ttu-id="061e1-145">아직 존재 하지 않는 위치를 변환 하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="061e1-145">It cannot be used to convert a location that does not exist yet.</span></span>

## <span data-ttu-id="061e1-146">관련 링크</span><span class="sxs-lookup"><span data-stu-id="061e1-146">RELATED LINKS</span></span>

[<span data-ttu-id="061e1-147">Join-Path</span><span class="sxs-lookup"><span data-stu-id="061e1-147">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="061e1-148">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="061e1-148">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="061e1-149">Split-Path</span><span class="sxs-lookup"><span data-stu-id="061e1-149">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="061e1-150">Test-Path</span><span class="sxs-lookup"><span data-stu-id="061e1-150">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="061e1-151">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="061e1-151">Get-PSProvider</span></span>](Get-PSProvider.md)

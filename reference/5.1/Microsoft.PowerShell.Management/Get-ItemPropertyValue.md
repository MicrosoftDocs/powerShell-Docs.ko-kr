---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: 2dbbbfeac3810f79b976b6a68ab3089e91707fb3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215417"
---
# <span data-ttu-id="d2423-103">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="d2423-103">Get-ItemPropertyValue</span></span>

## <span data-ttu-id="d2423-104">개요</span><span class="sxs-lookup"><span data-stu-id="d2423-104">SYNOPSIS</span></span>
<span data-ttu-id="d2423-105">지정 된 항목에 대 한 하나 이상의 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-105">Gets the value for one or more properties of a specified item.</span></span>

## <span data-ttu-id="d2423-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d2423-106">SYNTAX</span></span>

### <span data-ttu-id="d2423-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="d2423-107">Path (Default)</span></span>

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="d2423-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d2423-108">LiteralPath</span></span>

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="d2423-109">설명</span><span class="sxs-lookup"><span data-stu-id="d2423-109">DESCRIPTION</span></span>

<span data-ttu-id="d2423-110">는 `Get-ItemPropertyValue` *Path* 또는 *LiteralPath* 매개 변수를 사용 하 여 지정한 경로에 있는 *Name* 매개 변수를 사용할 때 지정 하는 속성의 현재 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-110">The `Get-ItemPropertyValue` gets the current value for a property that you specify when you use the *Name* parameter, located in a path that you specify with either the *Path* or *LiteralPath* parameters.</span></span>

## <span data-ttu-id="d2423-111">예제</span><span class="sxs-lookup"><span data-stu-id="d2423-111">EXAMPLES</span></span>

### <span data-ttu-id="d2423-112">예제 1: ProductID 속성 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="d2423-112">Example 1: Get the value of the ProductID property</span></span>

<span data-ttu-id="d2423-113">이 명령은 Windows 레지스트리 공급자에 있는 "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" 개체의 **ProductID** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-113">This command gets the value of the **ProductID** property of the "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" object in the Windows Registry provider.</span></span>

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### <span data-ttu-id="d2423-114">예 2: 파일 또는 폴더의 마지막 쓰기 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="d2423-114">Example 2: Get the last write time of a file or folder</span></span>

<span data-ttu-id="d2423-115">이 명령은 파일 시스템 공급자에서 작업 하는 "C:\Users\Test\Documents\ModuleToAssembly" 폴더에서 **LastWriteTime** 속성의 값 또는 파일 또는 폴더가 마지막으로 변경 된 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-115">This command gets the value of the **LastWriteTime** property, or the last time a file or folder was changed, from the "C:\Users\Test\Documents\ModuleToAssembly" folder, working in the FileSystem provider.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### <span data-ttu-id="d2423-116">예제 3: 파일 또는 폴더의 여러 속성 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="d2423-116">Example 3: Get multiple property values of a file or folder</span></span>

<span data-ttu-id="d2423-117">이 명령은 폴더의 **LastWriteTime** , **CreationTime** 및 **Root** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-117">This command gets the values of the **LastWriteTime** , **CreationTime** , and **Root** properties of a folder.</span></span>
<span data-ttu-id="d2423-118">속성 값은 속성 이름을 지정한 순서 대로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-118">The property values are returned in the order in which you specified the property names.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime,CreationTime,Root
```

```output
Wednesday, September 3, 2014 2:53:22 PM
Wednesday, September 3, 2014 2:53:10 PM

Name              : C:\
Parent            :
Exists            : True
Root              : C:\
FullName          : C:\
Extension         :
CreationTime      : 9/1/2014 4:59:45 AM
CreationTimeUtc   : 9/1/2014 11:59:45 AM
LastAccessTime    : 9/27/2014 5:22:02 PM
LastAccessTimeUtc : 9/28/2014 12:22:02 AM
LastWriteTime     : 9/27/2014 5:22:02 PM
LastWriteTimeUtc  : 9/28/2014 12:22:02 AM
Attributes        : Hidden, System, Directory
BaseName          : C:\
Target            :
LinkType          :
Mode              : d--hs-
```

## <span data-ttu-id="d2423-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d2423-119">PARAMETERS</span></span>

### <span data-ttu-id="d2423-120">-Credential</span><span class="sxs-lookup"><span data-stu-id="d2423-120">-Credential</span></span>

<span data-ttu-id="d2423-121">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-121">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="d2423-122">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-122">The default is the current user.</span></span>

<span data-ttu-id="d2423-123">"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="d2423-123">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="d2423-124">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-124">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="d2423-125">이 매개 변수는 Windows PowerShell과 함께 설치된 모든 공급자에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-125">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

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

### <span data-ttu-id="d2423-126">-제외</span><span class="sxs-lookup"><span data-stu-id="d2423-126">-Exclude</span></span>

<span data-ttu-id="d2423-127">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-127">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="d2423-128">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-128">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="d2423-129">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-129">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="d2423-130">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-130">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d2423-131">-Filter</span><span class="sxs-lookup"><span data-stu-id="d2423-131">-Filter</span></span>

<span data-ttu-id="d2423-132">공급자의 형식 또는 언어로 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-132">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="d2423-133">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-133">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="d2423-134">와일드 카드 문자를 포함 한 필터 구문은 공급자에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-134">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="d2423-135">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-135">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="d2423-136">-포함</span><span class="sxs-lookup"><span data-stu-id="d2423-136">-Include</span></span>

<span data-ttu-id="d2423-137">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="d2423-138">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-138">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="d2423-139">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-139">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="d2423-140">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d2423-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d2423-141">-LiteralPath</span></span>

<span data-ttu-id="d2423-142">속성의 현재 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-142">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="d2423-143">**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-143">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="d2423-144">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-144">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="d2423-145">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="d2423-145">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="d2423-146">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d2423-147">-Name</span><span class="sxs-lookup"><span data-stu-id="d2423-147">-Name</span></span>

<span data-ttu-id="d2423-148">검색할 속성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-148">Specifies the name of the property or properties to retrieve.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2423-149">-Path</span><span class="sxs-lookup"><span data-stu-id="d2423-149">-Path</span></span>

<span data-ttu-id="d2423-150">항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-150">Specifies the path to the item or items.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d2423-151">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="d2423-151">-UseTransaction</span></span>

<span data-ttu-id="d2423-152">활성 트랜잭션에 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-152">Includes the command in the active transaction.</span></span>
<span data-ttu-id="d2423-153">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-153">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="d2423-154">자세한 내용은 about_Transactions를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2423-154">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2423-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d2423-155">CommonParameters</span></span>

<span data-ttu-id="d2423-156">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-156">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="d2423-157">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2423-157">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="d2423-158">입력</span><span class="sxs-lookup"><span data-stu-id="d2423-158">INPUTS</span></span>

### <span data-ttu-id="d2423-159">System.String</span><span class="sxs-lookup"><span data-stu-id="d2423-159">System.String</span></span>

<span data-ttu-id="d2423-160">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-160">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="d2423-161">출력</span><span class="sxs-lookup"><span data-stu-id="d2423-161">OUTPUTS</span></span>

### <span data-ttu-id="d2423-162">System.string, System.string, System.web</span><span class="sxs-lookup"><span data-stu-id="d2423-162">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="d2423-163">이 cmdlet은 가져온 각 항목 속성 값에 대해 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-163">This cmdlet returns an object for each item property value that it gets.</span></span>
<span data-ttu-id="d2423-164">개체 유형은 검색 된 속성 값에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-164">The object type depends on the property value that is retrieved.</span></span>
<span data-ttu-id="d2423-165">예를 들어 파일 시스템 드라이브에서 cmdlet은 파일 또는 폴더를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-165">For example, in a file system drive, the cmdlet might return a file or folder.</span></span>

## <span data-ttu-id="d2423-166">참고</span><span class="sxs-lookup"><span data-stu-id="d2423-166">NOTES</span></span>

<span data-ttu-id="d2423-167">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-167">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="d2423-168">세션에서 사용할 수 있는 공급자를 나열 하려면 cmdlet을 실행 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2423-168">To list the providers available in your session, run the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="d2423-169">자세한 내용은 About_Providers를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2423-169">For more information, see about_Providers.</span></span>

## <span data-ttu-id="d2423-170">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d2423-170">RELATED LINKS</span></span>

[<span data-ttu-id="d2423-171">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d2423-171">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="d2423-172">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d2423-172">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="d2423-173">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d2423-173">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="d2423-174">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d2423-174">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="d2423-175">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d2423-175">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="d2423-176">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d2423-176">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="d2423-177">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d2423-177">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="d2423-178">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d2423-178">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="d2423-179">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="d2423-179">Get-PSProvider</span></span>](Get-PSProvider.md)

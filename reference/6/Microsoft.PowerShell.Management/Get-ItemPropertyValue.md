---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: fe49b968c859060b6f1c82c27bac87b33dabe079
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216329"
---
# <span data-ttu-id="34fbb-103">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="34fbb-103">Get-ItemPropertyValue</span></span>

## <span data-ttu-id="34fbb-104">개요</span><span class="sxs-lookup"><span data-stu-id="34fbb-104">SYNOPSIS</span></span>
<span data-ttu-id="34fbb-105">지정 된 항목에 대 한 하나 이상의 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-105">Gets the value for one or more properties of a specified item.</span></span>

## <span data-ttu-id="34fbb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="34fbb-106">SYNTAX</span></span>

### <span data-ttu-id="34fbb-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="34fbb-107">Path (Default)</span></span>

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="34fbb-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="34fbb-108">LiteralPath</span></span>

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="34fbb-109">설명</span><span class="sxs-lookup"><span data-stu-id="34fbb-109">DESCRIPTION</span></span>

<span data-ttu-id="34fbb-110">는 `Get-ItemPropertyValue` *Path* 또는 *LiteralPath* 매개 변수를 사용 하 여 지정한 경로에 있는 *Name* 매개 변수를 사용할 때 지정 하는 속성의 현재 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-110">The `Get-ItemPropertyValue` gets the current value for a property that you specify when you use the *Name* parameter, located in a path that you specify with either the *Path* or *LiteralPath* parameters.</span></span>

## <span data-ttu-id="34fbb-111">예제</span><span class="sxs-lookup"><span data-stu-id="34fbb-111">EXAMPLES</span></span>

### <span data-ttu-id="34fbb-112">예제 1: ProductID 속성 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="34fbb-112">Example 1: Get the value of the ProductID property</span></span>

<span data-ttu-id="34fbb-113">이 명령은 Windows 레지스트리 공급자에 있는 "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" 개체의 **ProductID** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-113">This command gets the value of the **ProductID** property of the "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" object in the Windows Registry provider.</span></span>

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### <span data-ttu-id="34fbb-114">예 2: 파일 또는 폴더의 마지막 쓰기 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="34fbb-114">Example 2: Get the last write time of a file or folder</span></span>

<span data-ttu-id="34fbb-115">이 명령은 파일 시스템 공급자에서 작업 하는 "C:\Users\Test\Documents\ModuleToAssembly" 폴더에서 **LastWriteTime** 속성의 값 또는 파일 또는 폴더가 마지막으로 변경 된 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-115">This command gets the value of the **LastWriteTime** property, or the last time a file or folder was changed, from the "C:\Users\Test\Documents\ModuleToAssembly" folder, working in the FileSystem provider.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### <span data-ttu-id="34fbb-116">예제 3: 파일 또는 폴더의 여러 속성 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="34fbb-116">Example 3: Get multiple property values of a file or folder</span></span>

<span data-ttu-id="34fbb-117">이 명령은 폴더의 **LastWriteTime** , **CreationTime** 및 **Root** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-117">This command gets the values of the **LastWriteTime** , **CreationTime** , and **Root** properties of a folder.</span></span> <span data-ttu-id="34fbb-118">속성 값은 속성 이름을 지정한 순서 대로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-118">The property values are returned in the order in which you specified the property names.</span></span>

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

## <span data-ttu-id="34fbb-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="34fbb-119">PARAMETERS</span></span>

### <span data-ttu-id="34fbb-120">-Credential</span><span class="sxs-lookup"><span data-stu-id="34fbb-120">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="34fbb-121">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-121">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="34fbb-122">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-122">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="34fbb-123">-제외</span><span class="sxs-lookup"><span data-stu-id="34fbb-123">-Exclude</span></span>

<span data-ttu-id="34fbb-124">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-124">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="34fbb-125">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-125">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="34fbb-126">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-126">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="34fbb-127">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-127">Wildcard characters are permitted.</span></span> <span data-ttu-id="34fbb-128">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="34fbb-128">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="34fbb-129">-Filter</span><span class="sxs-lookup"><span data-stu-id="34fbb-129">-Filter</span></span>

<span data-ttu-id="34fbb-130">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-130">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="34fbb-131">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-131">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="34fbb-132">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-132">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="34fbb-133">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-133">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="34fbb-134">-포함</span><span class="sxs-lookup"><span data-stu-id="34fbb-134">-Include</span></span>

<span data-ttu-id="34fbb-135">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-135">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="34fbb-136">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="34fbb-137">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-137">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="34fbb-138">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="34fbb-139">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="34fbb-139">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="34fbb-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="34fbb-140">-LiteralPath</span></span>

<span data-ttu-id="34fbb-141">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-141">Specifies a path to one or more locations.</span></span> <span data-ttu-id="34fbb-142">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-142">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="34fbb-143">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="34fbb-144">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="34fbb-144">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="34fbb-145">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-145">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="34fbb-146">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34fbb-146">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="34fbb-147">-Name</span><span class="sxs-lookup"><span data-stu-id="34fbb-147">-Name</span></span>

<span data-ttu-id="34fbb-148">검색할 속성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-148">Specifies the name of the property or properties to retrieve.</span></span>
<span data-ttu-id="34fbb-149">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-149">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="34fbb-150">-Path</span><span class="sxs-lookup"><span data-stu-id="34fbb-150">-Path</span></span>

<span data-ttu-id="34fbb-151">항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-151">Specifies the path to the item or items.</span></span>
<span data-ttu-id="34fbb-152">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-152">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="34fbb-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="34fbb-153">CommonParameters</span></span>

<span data-ttu-id="34fbb-154">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-154">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="34fbb-155">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34fbb-155">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="34fbb-156">입력</span><span class="sxs-lookup"><span data-stu-id="34fbb-156">INPUTS</span></span>

### <span data-ttu-id="34fbb-157">System.String</span><span class="sxs-lookup"><span data-stu-id="34fbb-157">System.String</span></span>

<span data-ttu-id="34fbb-158">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-158">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="34fbb-159">출력</span><span class="sxs-lookup"><span data-stu-id="34fbb-159">OUTPUTS</span></span>

### <span data-ttu-id="34fbb-160">System.string, System.string, System.web</span><span class="sxs-lookup"><span data-stu-id="34fbb-160">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="34fbb-161">이 cmdlet은 가져온 각 항목 속성 값에 대해 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-161">This cmdlet returns an object for each item property value that it gets.</span></span>
<span data-ttu-id="34fbb-162">개체 유형은 검색 된 속성 값에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-162">The object type depends on the property value that is retrieved.</span></span>
<span data-ttu-id="34fbb-163">예를 들어 파일 시스템 드라이브에서 cmdlet은 파일 또는 폴더를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-163">For example, in a file system drive, the cmdlet might return a file or folder.</span></span>

## <span data-ttu-id="34fbb-164">참고</span><span class="sxs-lookup"><span data-stu-id="34fbb-164">NOTES</span></span>

<span data-ttu-id="34fbb-165">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-165">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="34fbb-166">세션에서 사용할 수 있는 공급자를 나열 하려면 cmdlet을 실행 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="34fbb-166">To list the providers available in your session, run the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="34fbb-167">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34fbb-167">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="34fbb-168">관련 링크</span><span class="sxs-lookup"><span data-stu-id="34fbb-168">RELATED LINKS</span></span>

[<span data-ttu-id="34fbb-169">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="34fbb-169">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="34fbb-170">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="34fbb-170">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="34fbb-171">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="34fbb-171">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="34fbb-172">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="34fbb-172">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="34fbb-173">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="34fbb-173">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="34fbb-174">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="34fbb-174">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="34fbb-175">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="34fbb-175">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="34fbb-176">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="34fbb-176">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="34fbb-177">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="34fbb-177">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="34fbb-178">about_Providers</span><span class="sxs-lookup"><span data-stu-id="34fbb-178">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

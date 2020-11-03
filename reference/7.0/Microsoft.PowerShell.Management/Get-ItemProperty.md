---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: 5ef804e0274c0caaa6da1cf8714ab8aae1899068
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93209690"
---
# <span data-ttu-id="a0a85-103">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a0a85-103">Get-ItemProperty</span></span>

## <span data-ttu-id="a0a85-104">개요</span><span class="sxs-lookup"><span data-stu-id="a0a85-104">SYNOPSIS</span></span>
<span data-ttu-id="a0a85-105">지정된 항목의 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-105">Gets the properties of a specified item.</span></span>

## <span data-ttu-id="a0a85-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a0a85-106">SYNTAX</span></span>

### <span data-ttu-id="a0a85-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="a0a85-107">Path (Default)</span></span>

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="a0a85-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a0a85-108">LiteralPath</span></span>

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="a0a85-109">설명</span><span class="sxs-lookup"><span data-stu-id="a0a85-109">DESCRIPTION</span></span>

<span data-ttu-id="a0a85-110">`Get-ItemProperty`Cmdlet은 지정 된 항목의 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-110">The `Get-ItemProperty` cmdlet gets the properties of the specified items.</span></span>
<span data-ttu-id="a0a85-111">예를 들어이 cmdlet을 사용 하 여 파일 개체의 LastAccessTime 속성 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-111">For example, you can use this cmdlet to get the value of the LastAccessTime property of a file object.</span></span> <span data-ttu-id="a0a85-112">이 cmdlet을 사용 하 여 레지스트리 항목 및 해당 값을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-112">You can also use this cmdlet to view registry entries and their values.</span></span>

## <span data-ttu-id="a0a85-113">예제</span><span class="sxs-lookup"><span data-stu-id="a0a85-113">EXAMPLES</span></span>

### <span data-ttu-id="a0a85-114">예 1: 특정 디렉터리에 대 한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="a0a85-114">Example 1: Get information about a specific directory</span></span>

<span data-ttu-id="a0a85-115">이 명령은 디렉터리에 대 한 정보를 가져옵니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="a0a85-115">This command gets information about the `C:\Windows` directory.</span></span>

```powershell
Get-ItemProperty C:\Windows
```

### <span data-ttu-id="a0a85-116">예 2: 특정 파일의 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="a0a85-116">Example 2: Get the properties of a specific file</span></span>

<span data-ttu-id="a0a85-117">이 명령은 파일의 속성을 가져옵니다 `C:\Test\Weather.xls` .</span><span class="sxs-lookup"><span data-stu-id="a0a85-117">This command gets the properties of the `C:\Test\Weather.xls` file.</span></span>
<span data-ttu-id="a0a85-118">결과를 cmdlet으로 파이프 하 여 `Format-List` 출력을 목록으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-118">The result is piped to the `Format-List` cmdlet to display the output as a list.</span></span>

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### <span data-ttu-id="a0a85-119">예제 3: 레지스트리 하위 키에 레지스트리 항목의 값 이름 및 데이터 표시</span><span class="sxs-lookup"><span data-stu-id="a0a85-119">Example 3: Display the value name and data of registry entries in a registry subkey</span></span>

<span data-ttu-id="a0a85-120">이 명령은 "CurrentVersion" 레지스트리 하위 키에 포함 된 각 레지스트리 항목의 값 이름과 데이터를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-120">This command displays the value name and data of each of the registry entries contained in the "CurrentVersion" registry subkey.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

> [!NOTE]
> <span data-ttu-id="a0a85-121">이 명령을 사용 하려면 `HKLM:` 레지스트리의 "HKEY_LOCAL_MACHINE" 하이브에 매핑되는 라는 PowerShell 드라이브가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-121">This command requires that there is a PowerShell drive named `HKLM:` that is mapped to the "HKEY_LOCAL_MACHINE" hive of the registry.</span></span>
>
> <span data-ttu-id="a0a85-122">기본적으로 PowerShell에서 해당 이름과 매핑을 가진 드라이브를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-122">A drive with that name and mapping is available in PowerShell by default.</span></span>
> <span data-ttu-id="a0a85-123">또는 공급자 이름으로 시작되고 그 뒤에 두 개의 콜론이 오는 대체</span><span class="sxs-lookup"><span data-stu-id="a0a85-123">Alternatively, the path to this registry subkey can be specified by using the following alternative path that begins with the provider name followed by two colons:</span></span>
>
> <span data-ttu-id="a0a85-124">`Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="a0a85-124">`Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

### <span data-ttu-id="a0a85-125">예제 4: 레지스트리 하위 키에서 레지스트리 항목의 값 이름 및 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="a0a85-125">Example 4: Get the value name and data of a registry entry in a registry subkey</span></span>

<span data-ttu-id="a0a85-126">이 명령은 "CurrentVersion" 레지스트리 하위 키에 있는 "ProgramFilesDir" 레지스트리 항목의 값 이름과 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-126">This command gets the value name and data of the "ProgramFilesDir" registry entry in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="a0a85-127">**경로** 는 하위 키를 지정 하 고 **name** 매개 변수는 항목의 값 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-127">The **Path** specifies the subkey and the **Name** parameter specifies the value name of the entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### <span data-ttu-id="a0a85-128">예 5: 레지스트리 키에서 레지스트리 항목의 값 이름 및 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="a0a85-128">Example 5: Get the value names and data of registry entries in a registry key</span></span>

<span data-ttu-id="a0a85-129">이 명령은 "PowerShellEngine" 레지스트리 키에 있는 레지스트리 항목의 값 이름과 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-129">This command gets the value names and data of the registry entries in the "PowerShellEngine" registry key.</span></span> <span data-ttu-id="a0a85-130">결과는 다음과 같은 샘플 출력에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-130">The results are shown in the following sample output.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
```

## <span data-ttu-id="a0a85-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a0a85-131">PARAMETERS</span></span>

### <span data-ttu-id="a0a85-132">-Credential</span><span class="sxs-lookup"><span data-stu-id="a0a85-132">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a0a85-133">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-133">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="a0a85-134">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-134">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a0a85-135">-제외</span><span class="sxs-lookup"><span data-stu-id="a0a85-135">-Exclude</span></span>

<span data-ttu-id="a0a85-136">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-136">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="a0a85-137">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a0a85-138">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-138">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a0a85-139">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="a0a85-140">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="a0a85-140">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a0a85-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="a0a85-141">-Filter</span></span>

<span data-ttu-id="a0a85-142">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-142">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="a0a85-143">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-143">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="a0a85-144">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-144">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="a0a85-145">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-145">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="a0a85-146">-포함</span><span class="sxs-lookup"><span data-stu-id="a0a85-146">-Include</span></span>

<span data-ttu-id="a0a85-147">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-147">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="a0a85-148">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-148">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a0a85-149">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-149">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="a0a85-150">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-150">Wildcard characters are permitted.</span></span> <span data-ttu-id="a0a85-151">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="a0a85-151">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a0a85-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a0a85-152">-LiteralPath</span></span>

<span data-ttu-id="a0a85-153">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-153">Specifies a path to one or more locations.</span></span> <span data-ttu-id="a0a85-154">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-154">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="a0a85-155">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-155">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a0a85-156">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="a0a85-156">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a0a85-157">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-157">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a0a85-158">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a0a85-158">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="a0a85-159">-Name</span><span class="sxs-lookup"><span data-stu-id="a0a85-159">-Name</span></span>

<span data-ttu-id="a0a85-160">검색할 속성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-160">Specifies the name of the property or properties to retrieve.</span></span>
<span data-ttu-id="a0a85-161">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-161">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a0a85-162">-Path</span><span class="sxs-lookup"><span data-stu-id="a0a85-162">-Path</span></span>

<span data-ttu-id="a0a85-163">항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-163">Specifies the path to the item or items.</span></span>
<span data-ttu-id="a0a85-164">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-164">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="a0a85-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a0a85-165">CommonParameters</span></span>

<span data-ttu-id="a0a85-166">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-166">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a0a85-167">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0a85-167">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a0a85-168">입력</span><span class="sxs-lookup"><span data-stu-id="a0a85-168">INPUTS</span></span>

### <span data-ttu-id="a0a85-169">System.String</span><span class="sxs-lookup"><span data-stu-id="a0a85-169">System.String</span></span>

<span data-ttu-id="a0a85-170">경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="a0a85-170">You can pipe a string that contains a path to `Get-ItemProperty`.</span></span>

## <span data-ttu-id="a0a85-171">출력</span><span class="sxs-lookup"><span data-stu-id="a0a85-171">OUTPUTS</span></span>

### <span data-ttu-id="a0a85-172">System.string, System.string, System.web</span><span class="sxs-lookup"><span data-stu-id="a0a85-172">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="a0a85-173">`Get-ItemProperty` 가져오는 각 항목 속성에 대 한 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-173">`Get-ItemProperty` returns an object for each item property that it gets.</span></span> <span data-ttu-id="a0a85-174">개체 유형은 검색된 개체에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-174">The object type depends on the object that is retrieved.</span></span> <span data-ttu-id="a0a85-175">예를 들어 파일 시스템 드라이브에서는 파일 또는 폴더가 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-175">For example, in a file system drive, it might return a file or folder.</span></span>

## <span data-ttu-id="a0a85-176">참고</span><span class="sxs-lookup"><span data-stu-id="a0a85-176">NOTES</span></span>

<span data-ttu-id="a0a85-177">`Get-ItemProperty`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-177">The `Get-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a0a85-178">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0a85-178">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="a0a85-179">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0a85-179">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a0a85-180">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a0a85-180">RELATED LINKS</span></span>

[<span data-ttu-id="a0a85-181">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a0a85-181">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="a0a85-182">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a0a85-182">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="a0a85-183">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a0a85-183">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="a0a85-184">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a0a85-184">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="a0a85-185">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a0a85-185">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="a0a85-186">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a0a85-186">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="a0a85-187">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a0a85-187">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="a0a85-188">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a0a85-188">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

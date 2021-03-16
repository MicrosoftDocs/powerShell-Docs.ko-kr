---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: 59b7ea7f675d72dd90d970306c60107bd3f1de87
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599570"
---
# <span data-ttu-id="bae39-102">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae39-102">New-ItemProperty</span></span>

## <span data-ttu-id="bae39-103">개요</span><span class="sxs-lookup"><span data-stu-id="bae39-103">SYNOPSIS</span></span>
<span data-ttu-id="bae39-104">항목의 새 속성을 만들고 해당 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-104">Creates a new property for an item and sets its value.</span></span>

## <span data-ttu-id="bae39-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bae39-105">SYNTAX</span></span>

### <span data-ttu-id="bae39-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="bae39-106">Path (Default)</span></span>

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bae39-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="bae39-107">LiteralPath</span></span>

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bae39-108">설명</span><span class="sxs-lookup"><span data-stu-id="bae39-108">DESCRIPTION</span></span>

<span data-ttu-id="bae39-109">`New-ItemProperty`Cmdlet은 지정 된 항목에 대 한 새 속성을 만들고 해당 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-109">The `New-ItemProperty` cmdlet creates a new property for a specified item and sets its value.</span></span>
<span data-ttu-id="bae39-110">레지스트리 값은 레지스트리 키 항목의 속성이기 때문에 일반적으로 이 cmdlet은 새 레지스트리 값을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-110">Typically, this cmdlet is used to create new registry values, because registry values are properties of a registry key item.</span></span>

<span data-ttu-id="bae39-111">이 cmdlet은 개체에 속성을 추가하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-111">This cmdlet does not add properties to an object.</span></span>

- <span data-ttu-id="bae39-112">개체의 인스턴스에 속성을 추가 하려면 cmdlet을 사용 `Add-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-112">To add a property to an instance of an object, use the `Add-Member` cmdlet.</span></span>
- <span data-ttu-id="bae39-113">특정 유형의 모든 개체에 속성을 추가 하려면 Types.ps1xml 파일을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-113">To add a property to all objects of a particular type, modify the Types.ps1xml file.</span></span>

## <span data-ttu-id="bae39-114">예제</span><span class="sxs-lookup"><span data-stu-id="bae39-114">EXAMPLES</span></span>

### <span data-ttu-id="bae39-115">예제 1: 레지스트리 항목 추가</span><span class="sxs-lookup"><span data-stu-id="bae39-115">Example 1: Add a registry entry</span></span>

<span data-ttu-id="bae39-116">이 명령은 새 레지스트리 항목인 "NoOfEmployees"를 "HKLM: \ Software hive"의 "MyCompany" 키에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-116">This command adds a new registry entry, "NoOfEmployees", to the "MyCompany" key of the "HKLM:\Software hive".</span></span>

<span data-ttu-id="bae39-117">첫 번째 명령은 **path** 매개 변수를 사용 하 여 "MyCompany" 레지스트리 키의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-117">The first command uses the **Path** parameter to specify the path of the "MyCompany" registry key.</span></span>
<span data-ttu-id="bae39-118">**Name** 매개 변수를 사용 하 여 항목의 이름을 지정 하 고 **value** 매개 변수를 사용 하 여 해당 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-118">It uses the **Name** parameter to specify a name for the entry and the **Value** parameter to specify its value.</span></span>

<span data-ttu-id="bae39-119">두 번째 명령은 cmdlet을 사용 하 여 `Get-ItemProperty` 새 레지스트리 항목을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-119">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>

```powershell
New-ItemProperty -Path "HKLM:\Software\MyCompany" -Name "NoOfEmployees" -Value 822
Get-ItemProperty "HKLM:\Software\MyCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\mycompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : mycompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 822
```

### <span data-ttu-id="bae39-120">예제 2: 레지스트리 항목을 키에 추가</span><span class="sxs-lookup"><span data-stu-id="bae39-120">Example 2: Add a registry entry to a key</span></span>

<span data-ttu-id="bae39-121">이 명령은 새 레지스트리 항목을 레지스트리 키에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-121">This command adds a new registry entry to a registry key.</span></span>
<span data-ttu-id="bae39-122">키를 지정 하기 위해 파이프라인 연산자 ()를 사용 하 여 `|` 키를 나타내는 개체를로 보냅니다 `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="bae39-122">To specify the key, it uses a pipeline operator (`|`) to send an object that represents the key to `New-ItemProperty`.</span></span>

<span data-ttu-id="bae39-123">명령의 첫 번째 부분에서는 cmdlet을 사용 하 여 `Get-Item` "MyCompany" 레지스트리 키를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-123">The first part of the command uses the `Get-Item` cmdlet to get the "MyCompany" registry key.</span></span>
<span data-ttu-id="bae39-124">파이프라인 연산자는 명령 결과를에 보냅니다 .이 명령은 `New-ItemProperty` 새 레지스트리 항목 ("NoOfLocations") 및 해당 값 (3)을 "MyCompany" 키에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-124">The pipeline operator sends the results of the command to `New-ItemProperty`, which adds the new registry entry ("NoOfLocations"), and its value (3), to the "MyCompany" key.</span></span>

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

<span data-ttu-id="bae39-125">이 명령은 PowerShell의 매개 변수 바인딩 기능이 `RegistryKey` `Get-Item` 의 **LiteralPath** 매개 변수와 함께 반환 되는 개체의 경로를 연결 하기 때문에 작동 합니다 `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="bae39-125">This command works because the parameter-binding feature of PowerShell associates the path of the `RegistryKey` object that `Get-Item` returns with the **LiteralPath** parameter of `New-ItemProperty`.</span></span> <span data-ttu-id="bae39-126">자세한 내용은 [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bae39-126">For more information, see [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).</span></span>

### <span data-ttu-id="bae39-127">예제 3: Here-String을 사용 하 여 레지스트리에 다중 문자열 값 만들기</span><span class="sxs-lookup"><span data-stu-id="bae39-127">Example 3: Create a MultiString value in the registry using a Here-String</span></span>

<span data-ttu-id="bae39-128">이 예제에서는 다음 문자열을 사용 하 여 다중 문자열 값을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-128">This example creates a MultiString value using a Here-String.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'HereString' -PropertyType MultiString -Value @"
This is text which contains newlines
It can also contain "quoted" strings
"@
$newValue.multistring
```

```output
This is text which contains newlines
It can also contain "quoted" strings
```

### <span data-ttu-id="bae39-129">예제 4: 배열을 사용 하 여 레지스트리에 다중 문자열 값 만들기</span><span class="sxs-lookup"><span data-stu-id="bae39-129">Example 4: Create a MultiString value in the registry using an array</span></span>

<span data-ttu-id="bae39-130">예제에서는 값 배열을 사용 하 여 값을 만드는 방법을 보여 줍니다 `MultiString` .</span><span class="sxs-lookup"><span data-stu-id="bae39-130">The example shows how to use an array of values to create the `MultiString` value.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
```

## <span data-ttu-id="bae39-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bae39-131">PARAMETERS</span></span>

### <span data-ttu-id="bae39-132">-Credential</span><span class="sxs-lookup"><span data-stu-id="bae39-132">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="bae39-133">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-133">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="bae39-134">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-134">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="bae39-135">-제외</span><span class="sxs-lookup"><span data-stu-id="bae39-135">-Exclude</span></span>

<span data-ttu-id="bae39-136">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-136">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="bae39-137">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="bae39-138">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-138">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="bae39-139">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="bae39-140">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="bae39-140">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="bae39-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="bae39-141">-Filter</span></span>

<span data-ttu-id="bae39-142">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-142">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="bae39-143">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-143">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="bae39-144">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-144">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="bae39-145">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-145">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="bae39-146">-Force</span><span class="sxs-lookup"><span data-stu-id="bae39-146">-Force</span></span>

<span data-ttu-id="bae39-147">Cmdlet이 다른 방법으로는 사용자가 액세스할 수 없는 개체에 대 한 속성을 강제로 만들도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-147">Forces the cmdlet to create a property on an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="bae39-148">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-148">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="bae39-149">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bae39-149">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bae39-150">-포함</span><span class="sxs-lookup"><span data-stu-id="bae39-150">-Include</span></span>

<span data-ttu-id="bae39-151">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-151">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="bae39-152">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-152">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="bae39-153">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-153">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="bae39-154">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-154">Wildcard characters are permitted.</span></span> <span data-ttu-id="bae39-155">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="bae39-155">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="bae39-156">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="bae39-156">-LiteralPath</span></span>

<span data-ttu-id="bae39-157">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-157">Specifies a path to one or more locations.</span></span> <span data-ttu-id="bae39-158">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-158">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="bae39-159">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-159">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="bae39-160">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="bae39-160">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="bae39-161">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-161">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="bae39-162">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bae39-162">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="bae39-163">-Name</span><span class="sxs-lookup"><span data-stu-id="bae39-163">-Name</span></span>

<span data-ttu-id="bae39-164">새 속성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-164">Specifies a name for the new property.</span></span>
<span data-ttu-id="bae39-165">속성이 레지스트리 항목인 경우 이 매개 변수는 항목의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-165">If the property is a registry entry, this parameter specifies the name of the entry.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bae39-166">-Path</span><span class="sxs-lookup"><span data-stu-id="bae39-166">-Path</span></span>

<span data-ttu-id="bae39-167">항목의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-167">Specifies the path of the item.</span></span>
<span data-ttu-id="bae39-168">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-168">Wildcard characters are permitted.</span></span>
<span data-ttu-id="bae39-169">이 매개 변수는이 cmdlet이 새 속성을 추가 하는 항목을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-169">This parameter identifies the item to which this cmdlet adds the new property.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bae39-170">-PropertyType</span><span class="sxs-lookup"><span data-stu-id="bae39-170">-PropertyType</span></span>

<span data-ttu-id="bae39-171">이 cmdlet이 추가 하는 속성의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-171">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="bae39-172">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bae39-173">**String**: null로 끝나는 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-173">**String**: Specifies a null-terminated string.</span></span> <span data-ttu-id="bae39-174">**REG_SZ** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-174">Equivalent to **REG_SZ**.</span></span>
- <span data-ttu-id="bae39-175">**ExpandString**: 값을 검색할 때 확장 되는 환경 변수에 대 한 확장 되지 않은 참조를 포함 하는 null로 끝나는 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-175">**ExpandString**: Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="bae39-176">**REG_EXPAND_SZ** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-176">Equivalent to **REG_EXPAND_SZ**.</span></span>
- <span data-ttu-id="bae39-177">**Binary**: 임의의 형식으로 된 이진 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-177">**Binary**: Specifies binary data in any form.</span></span> <span data-ttu-id="bae39-178">**REG_BINARY** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-178">Equivalent to **REG_BINARY**.</span></span>
- <span data-ttu-id="bae39-179">**DWord**: 32 비트 이진수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-179">**DWord**: Specifies a 32-bit binary number.</span></span> <span data-ttu-id="bae39-180">**REG_DWORD** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-180">Equivalent to **REG_DWORD**.</span></span>
- <span data-ttu-id="bae39-181">**다중 문자열**: 두 null 문자로 끝나는 null로 끝나는 문자열의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-181">**MultiString**: Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="bae39-182">**REG_MULTI_SZ** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-182">Equivalent to **REG_MULTI_SZ**.</span></span>
- <span data-ttu-id="bae39-183">**Qword(64**: 64 비트 이진수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-183">**Qword**: Specifies a 64-bit binary number.</span></span> <span data-ttu-id="bae39-184">**REG_QWORD** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-184">Equivalent to **REG_QWORD**.</span></span>
- <span data-ttu-id="bae39-185">**Unknown**: **REG_RESOURCE_LIST** 와 같은 지원 되지 않는 레지스트리 데이터 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-185">**Unknown**: Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bae39-186">-Value</span><span class="sxs-lookup"><span data-stu-id="bae39-186">-Value</span></span>

<span data-ttu-id="bae39-187">속성 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-187">Specifies the property value.</span></span>
<span data-ttu-id="bae39-188">속성이 레지스트리 항목인 경우 이 매개 변수는 항목의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-188">If the property is a registry entry, this parameter specifies the value of the entry.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bae39-189">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bae39-189">-Confirm</span></span>

<span data-ttu-id="bae39-190">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-190">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bae39-191">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bae39-191">-WhatIf</span></span>

<span data-ttu-id="bae39-192">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-192">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="bae39-193">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-193">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bae39-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bae39-194">CommonParameters</span></span>

<span data-ttu-id="bae39-195">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-195">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="bae39-196">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bae39-196">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="bae39-197">입력</span><span class="sxs-lookup"><span data-stu-id="bae39-197">INPUTS</span></span>

### <span data-ttu-id="bae39-198">없음</span><span class="sxs-lookup"><span data-stu-id="bae39-198">None</span></span>

<span data-ttu-id="bae39-199">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-199">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="bae39-200">출력</span><span class="sxs-lookup"><span data-stu-id="bae39-200">OUTPUTS</span></span>

### <span data-ttu-id="bae39-201">PSCustomObject.</span><span class="sxs-lookup"><span data-stu-id="bae39-201">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="bae39-202">`New-ItemProperty` 새 속성을 포함 하는 사용자 지정 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-202">`New-ItemProperty` returns a custom object that contains the new property.</span></span>

## <span data-ttu-id="bae39-203">참고</span><span class="sxs-lookup"><span data-stu-id="bae39-203">NOTES</span></span>

<span data-ttu-id="bae39-204">`New-ItemProperty` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-204">`New-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="bae39-205">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae39-205">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="bae39-206">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bae39-206">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="bae39-207">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bae39-207">RELATED LINKS</span></span>

[<span data-ttu-id="bae39-208">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae39-208">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="bae39-209">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae39-209">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="bae39-210">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae39-210">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="bae39-211">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae39-211">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="bae39-212">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae39-212">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="bae39-213">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae39-213">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="bae39-214">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae39-214">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="bae39-215">about_Providers</span><span class="sxs-lookup"><span data-stu-id="bae39-215">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

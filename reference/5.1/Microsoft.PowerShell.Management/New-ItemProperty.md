---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: 2569f4778f54f6cdad22e10cf92e727b73c323e3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214610"
---
# <span data-ttu-id="a98c9-103">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a98c9-103">New-ItemProperty</span></span>

## <span data-ttu-id="a98c9-104">개요</span><span class="sxs-lookup"><span data-stu-id="a98c9-104">SYNOPSIS</span></span>
<span data-ttu-id="a98c9-105">항목의 새 속성을 만들고 해당 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-105">Creates a new property for an item and sets its value.</span></span>

## <span data-ttu-id="a98c9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a98c9-106">SYNTAX</span></span>

### <span data-ttu-id="a98c9-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="a98c9-107">Path (Default)</span></span>

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="a98c9-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a98c9-108">LiteralPath</span></span>

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="a98c9-109">설명</span><span class="sxs-lookup"><span data-stu-id="a98c9-109">DESCRIPTION</span></span>

<span data-ttu-id="a98c9-110">`New-ItemProperty`Cmdlet은 지정 된 항목에 대 한 새 속성을 만들고 해당 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-110">The `New-ItemProperty` cmdlet creates a new property for a specified item and sets its value.</span></span>
<span data-ttu-id="a98c9-111">레지스트리 값은 레지스트리 키 항목의 속성이기 때문에 일반적으로 이 cmdlet은 새 레지스트리 값을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-111">Typically, this cmdlet is used to create new registry values, because registry values are properties of a registry key item.</span></span>

<span data-ttu-id="a98c9-112">이 cmdlet은 개체에 속성을 추가하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-112">This cmdlet does not add properties to an object.</span></span>

- <span data-ttu-id="a98c9-113">개체의 인스턴스에 속성을 추가 하려면 cmdlet을 사용 `Add-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-113">To add a property to an instance of an object, use the `Add-Member` cmdlet.</span></span>
- <span data-ttu-id="a98c9-114">특정 유형의 모든 개체에 속성을 추가 하려면 Types.ps1xml 파일을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-114">To add a property to all objects of a particular type, modify the Types.ps1xml file.</span></span>

## <span data-ttu-id="a98c9-115">예제</span><span class="sxs-lookup"><span data-stu-id="a98c9-115">EXAMPLES</span></span>

### <span data-ttu-id="a98c9-116">예제 1: 레지스트리 항목 추가</span><span class="sxs-lookup"><span data-stu-id="a98c9-116">Example 1: Add a registry entry</span></span>

<span data-ttu-id="a98c9-117">이 명령은 새 레지스트리 항목인 "NoOfEmployees"를 "HKLM: \ Software hive"의 "MyCompany" 키에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-117">This command adds a new registry entry, "NoOfEmployees", to the "MyCompany" key of the "HKLM:\Software hive".</span></span>

<span data-ttu-id="a98c9-118">첫 번째 명령은 **path** 매개 변수를 사용 하 여 "MyCompany" 레지스트리 키의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-118">The first command uses the **Path** parameter to specify the path of the "MyCompany" registry key.</span></span>
<span data-ttu-id="a98c9-119">**Name** 매개 변수를 사용 하 여 항목의 이름을 지정 하 고 **value** 매개 변수를 사용 하 여 해당 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-119">It uses the **Name** parameter to specify a name for the entry and the **Value** parameter to specify its value.</span></span>

<span data-ttu-id="a98c9-120">두 번째 명령은 cmdlet을 사용 하 여 `Get-ItemProperty` 새 레지스트리 항목을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-120">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>

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

### <span data-ttu-id="a98c9-121">예제 2: 레지스트리 항목을 키에 추가</span><span class="sxs-lookup"><span data-stu-id="a98c9-121">Example 2: Add a registry entry to a key</span></span>

<span data-ttu-id="a98c9-122">이 명령은 새 레지스트리 항목을 레지스트리 키에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-122">This command adds a new registry entry to a registry key.</span></span> <span data-ttu-id="a98c9-123">키를 지정 하기 위해 파이프라인 연산자 (|)를 사용 하 여 키를 나타내는 개체를로 보냅니다 `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="a98c9-123">To specify the key, it uses a pipeline operator (|) to send an object that represents the key to `New-ItemProperty`.</span></span>

<span data-ttu-id="a98c9-124">명령의 첫 번째 부분에서는 cmdlet을 사용 하 여 `Get-Item` "MyCompany" 레지스트리 키를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-124">The first part of the command uses the `Get-Item` cmdlet to get the "MyCompany" registry key.</span></span> <span data-ttu-id="a98c9-125">파이프라인 연산자는 명령 결과를에 보냅니다 .이 명령은 `New-ItemProperty` 새 레지스트리 항목 ("NoOfLocations") 및 해당 값 (3)을 "MyCompany" 키에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-125">The pipeline operator sends the results of the command to `New-ItemProperty`, which adds the new registry entry ("NoOfLocations"), and its value (3), to the "MyCompany" key.</span></span>

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

<span data-ttu-id="a98c9-126">이 명령은 Windows PowerShell의 매개 변수 바인딩 기능이 `RegistryKey` `Get-Item` 의 **LiteralPath** 매개 변수와 함께 반환 되는 개체의 경로를 연결 하기 때문에 작동 합니다 `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="a98c9-126">This command works because the parameter-binding feature of Windows PowerShell associates the path of the `RegistryKey` object that `Get-Item` returns with the **LiteralPath** parameter of `New-ItemProperty`.</span></span> <span data-ttu-id="a98c9-127">자세한 내용은 [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a98c9-127">For more information, see [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).</span></span>

### <span data-ttu-id="a98c9-128">예제 3: Here-String을 사용 하 여 레지스트리에 다중 문자열 값 만들기</span><span class="sxs-lookup"><span data-stu-id="a98c9-128">Example 3: Create a MultiString value in the registry using a Here-String</span></span>

<span data-ttu-id="a98c9-129">이 예제에서는 다음 문자열을 사용 하 여 다중 문자열 값을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-129">This example creates a MultiString value using a Here-String.</span></span>

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

### <span data-ttu-id="a98c9-130">예제 4: 배열을 사용 하 여 레지스트리에 다중 문자열 값 만들기</span><span class="sxs-lookup"><span data-stu-id="a98c9-130">Example 4: Create a MultiString value in the registry using an array</span></span>

<span data-ttu-id="a98c9-131">예제에서는 값 배열을 사용 하 여 값을 만드는 방법을 보여 줍니다 `MultiString` .</span><span class="sxs-lookup"><span data-stu-id="a98c9-131">The example shows how to use an array of values to create the `MultiString` value.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
```

## <span data-ttu-id="a98c9-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a98c9-132">PARAMETERS</span></span>

### <span data-ttu-id="a98c9-133">-Credential</span><span class="sxs-lookup"><span data-stu-id="a98c9-133">-Credential</span></span>

<span data-ttu-id="a98c9-134">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-134">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="a98c9-135">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-135">The default is the current user.</span></span>

<span data-ttu-id="a98c9-136">"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="a98c9-136">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a98c9-137">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-137">If you type a user name, you are prompted for a password.</span></span>

> [!NOTE]
> <span data-ttu-id="a98c9-138">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-138">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="a98c9-139">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-139">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="a98c9-140">-제외</span><span class="sxs-lookup"><span data-stu-id="a98c9-140">-Exclude</span></span>

<span data-ttu-id="a98c9-141">이 cmdlet이 작업에서 제외 하는 속성 또는 속성을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-141">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="a98c9-142">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-142">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="a98c9-143">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-143">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="a98c9-144">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-144">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a98c9-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="a98c9-145">-Filter</span></span>

<span data-ttu-id="a98c9-146">공급자의 형식 또는 언어로 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-146">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="a98c9-147">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-147">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="a98c9-148">와일드 카드 문자를 포함 한 필터 구문은 공급자에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-148">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span> <span data-ttu-id="a98c9-149">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-149">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a98c9-150">-Force</span><span class="sxs-lookup"><span data-stu-id="a98c9-150">-Force</span></span>

<span data-ttu-id="a98c9-151">Cmdlet이 다른 방법으로는 사용자가 액세스할 수 없는 개체에 대 한 속성을 강제로 만들도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-151">Forces the cmdlet to create a property on an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="a98c9-152">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-152">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="a98c9-153">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a98c9-153">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="a98c9-154">-포함</span><span class="sxs-lookup"><span data-stu-id="a98c9-154">-Include</span></span>

<span data-ttu-id="a98c9-155">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-155">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="a98c9-156">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-156">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="a98c9-157">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-157">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="a98c9-158">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-158">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a98c9-159">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a98c9-159">-LiteralPath</span></span>

<span data-ttu-id="a98c9-160">속성의 현재 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-160">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="a98c9-161">**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-161">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="a98c9-162">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-162">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="a98c9-163">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="a98c9-163">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="a98c9-164">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-164">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="a98c9-165">-Name</span><span class="sxs-lookup"><span data-stu-id="a98c9-165">-Name</span></span>

<span data-ttu-id="a98c9-166">새 속성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-166">Specifies a name for the new property.</span></span>
<span data-ttu-id="a98c9-167">속성이 레지스트리 항목인 경우 이 매개 변수는 항목의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-167">If the property is a registry entry, this parameter specifies the name of the entry.</span></span>

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

### <span data-ttu-id="a98c9-168">-Path</span><span class="sxs-lookup"><span data-stu-id="a98c9-168">-Path</span></span>

<span data-ttu-id="a98c9-169">항목의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-169">Specifies the path of the item.</span></span>
<span data-ttu-id="a98c9-170">이 매개 변수는이 cmdlet이 새 속성을 추가 하는 항목을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-170">This parameter identifies the item to which this cmdlet adds the new property.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a98c9-171">-PropertyType</span><span class="sxs-lookup"><span data-stu-id="a98c9-171">-PropertyType</span></span>

<span data-ttu-id="a98c9-172">이 cmdlet이 추가 하는 속성의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-172">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="a98c9-173">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-173">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a98c9-174">**String** : null로 끝나는 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-174">**String** : Specifies a null-terminated string.</span></span> <span data-ttu-id="a98c9-175">**REG_SZ** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-175">Equivalent to **REG_SZ** .</span></span>
- <span data-ttu-id="a98c9-176">**ExpandString** : 값을 검색할 때 확장 되는 환경 변수에 대 한 확장 되지 않은 참조를 포함 하는 null로 끝나는 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-176">**ExpandString** : Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="a98c9-177">**REG_EXPAND_SZ** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-177">Equivalent to **REG_EXPAND_SZ** .</span></span>
- <span data-ttu-id="a98c9-178">**Binary** : 임의의 형식으로 된 이진 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-178">**Binary** : Specifies binary data in any form.</span></span> <span data-ttu-id="a98c9-179">**REG_BINARY** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-179">Equivalent to **REG_BINARY** .</span></span>
- <span data-ttu-id="a98c9-180">**DWord** : 32 비트 이진수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-180">**DWord** : Specifies a 32-bit binary number.</span></span> <span data-ttu-id="a98c9-181">**REG_DWORD** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-181">Equivalent to **REG_DWORD** .</span></span>
- <span data-ttu-id="a98c9-182">**다중 문자열** : 두 null 문자로 끝나는 null로 끝나는 문자열의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-182">**MultiString** : Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="a98c9-183">**REG_MULTI_SZ** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-183">Equivalent to **REG_MULTI_SZ** .</span></span>
- <span data-ttu-id="a98c9-184">**Qword(64** : 64 비트 이진수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-184">**Qword** : Specifies a 64-bit binary number.</span></span> <span data-ttu-id="a98c9-185">**REG_QWORD** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-185">Equivalent to **REG_QWORD** .</span></span>
- <span data-ttu-id="a98c9-186">**Unknown** : **REG_RESOURCE_LIST** 와 같은 지원 되지 않는 레지스트리 데이터 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-186">**Unknown** : Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST** .</span></span>

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

### <span data-ttu-id="a98c9-187">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="a98c9-187">-UseTransaction</span></span>

<span data-ttu-id="a98c9-188">활성 트랜잭션에 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-188">Includes the command in the active transaction.</span></span>
<span data-ttu-id="a98c9-189">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-189">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="a98c9-190">자세한 내용은 about_Transactions를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a98c9-190">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="a98c9-191">-Value</span><span class="sxs-lookup"><span data-stu-id="a98c9-191">-Value</span></span>

<span data-ttu-id="a98c9-192">속성 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-192">Specifies the property value.</span></span>
<span data-ttu-id="a98c9-193">속성이 레지스트리 항목인 경우 이 매개 변수는 항목의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-193">If the property is a registry entry, this parameter specifies the value of the entry.</span></span>

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

### <span data-ttu-id="a98c9-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a98c9-194">-Confirm</span></span>

<span data-ttu-id="a98c9-195">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-195">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a98c9-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a98c9-196">-WhatIf</span></span>

<span data-ttu-id="a98c9-197">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-197">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a98c9-198">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-198">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a98c9-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a98c9-199">CommonParameters</span></span>

<span data-ttu-id="a98c9-200">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-200">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a98c9-201">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a98c9-201">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a98c9-202">입력</span><span class="sxs-lookup"><span data-stu-id="a98c9-202">INPUTS</span></span>

### <span data-ttu-id="a98c9-203">없음</span><span class="sxs-lookup"><span data-stu-id="a98c9-203">None</span></span>

<span data-ttu-id="a98c9-204">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-204">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a98c9-205">출력</span><span class="sxs-lookup"><span data-stu-id="a98c9-205">OUTPUTS</span></span>

### <span data-ttu-id="a98c9-206">PSCustomObject.</span><span class="sxs-lookup"><span data-stu-id="a98c9-206">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="a98c9-207">`New-ItemProperty` 새 속성을 포함 하는 사용자 지정 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-207">`New-ItemProperty` returns a custom object that contains the new property.</span></span>

## <span data-ttu-id="a98c9-208">참고</span><span class="sxs-lookup"><span data-stu-id="a98c9-208">NOTES</span></span>

<span data-ttu-id="a98c9-209">`New-ItemProperty` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-209">`New-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a98c9-210">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98c9-210">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="a98c9-211">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a98c9-211">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a98c9-212">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a98c9-212">RELATED LINKS</span></span>

[<span data-ttu-id="a98c9-213">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a98c9-213">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="a98c9-214">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a98c9-214">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="a98c9-215">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a98c9-215">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="a98c9-216">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a98c9-216">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="a98c9-217">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a98c9-217">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="a98c9-218">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a98c9-218">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="a98c9-219">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a98c9-219">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="a98c9-220">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a98c9-220">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

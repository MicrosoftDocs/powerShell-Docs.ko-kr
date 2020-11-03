---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: b9a2386b41ec4d64200283a5cd3b802d254b5475
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217282"
---
# <span data-ttu-id="de393-103">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="de393-103">Set-ItemProperty</span></span>

## <span data-ttu-id="de393-104">개요</span><span class="sxs-lookup"><span data-stu-id="de393-104">SYNOPSIS</span></span>
<span data-ttu-id="de393-105">항목의 속성 값을 만들거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-105">Creates or changes the value of a property of an item.</span></span>

## <span data-ttu-id="de393-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="de393-106">SYNTAX</span></span>

### <span data-ttu-id="de393-107">propertyValuePathSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="de393-107">propertyValuePathSet (Default)</span></span>

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### <span data-ttu-id="de393-108">propertyPSObjectPathSet</span><span class="sxs-lookup"><span data-stu-id="de393-108">propertyPSObjectPathSet</span></span>

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### <span data-ttu-id="de393-109">propertyValueLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="de393-109">propertyValueLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### <span data-ttu-id="de393-110">propertyPSObjectLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="de393-110">propertyPSObjectLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

## <span data-ttu-id="de393-111">설명</span><span class="sxs-lookup"><span data-stu-id="de393-111">DESCRIPTION</span></span>

<span data-ttu-id="de393-112">`Set-ItemProperty`Cmdlet은 지정 된 항목의 속성 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-112">The `Set-ItemProperty` cmdlet changes the value of the property of the specified item.</span></span>
<span data-ttu-id="de393-113">이 cmdlet을 사용하여 항목 속성을 설정하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-113">You can use the cmdlet to establish or change the properties of items.</span></span>
<span data-ttu-id="de393-114">예를 들어를 사용 `Set-ItemProperty` 하 여 파일 개체의 **IsReadOnly** 속성 값을로 설정할 수 있습니다 `$True` .</span><span class="sxs-lookup"><span data-stu-id="de393-114">For example, you can use `Set-ItemProperty` to set the value of the **IsReadOnly** property of a file object to `$True`.</span></span>

<span data-ttu-id="de393-115">또한를 사용 `Set-ItemProperty` 하 여 레지스트리 값과 데이터를 만들고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-115">You also use `Set-ItemProperty` to create and change registry values and data.</span></span>
<span data-ttu-id="de393-116">예를 들어 새 레지스트리 항목을 키에 추가하고 해당 값을 구성하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-116">For example, you can add a new registry entry to a key and establish or change its value.</span></span>

## <span data-ttu-id="de393-117">예제</span><span class="sxs-lookup"><span data-stu-id="de393-117">EXAMPLES</span></span>

### <span data-ttu-id="de393-118">예제 1: 파일의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="de393-118">Example 1: Set a property of a file</span></span>

<span data-ttu-id="de393-119">이 명령은 "final.doc" 파일의 **IsReadOnly** 속성 값을 "true"로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-119">This command sets the value of the **IsReadOnly** property of the "final.doc" file to "true".</span></span>
<span data-ttu-id="de393-120">**경로** 를 사용 하 여 파일을 지정 하 고, **이름을** 지정 하 여 속성의 이름을 지정 하 고, **value** 매개 변수를 사용 하 여 새 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-120">It uses **Path** to specify the file, **Name** to specify the name of the property, and the **Value** parameter to specify the new value.</span></span>

<span data-ttu-id="de393-121">이 파일은 IsReadOnly **개체이** 고, 해당 속성 중 **IsReadOnly** 하나일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="de393-121">The file is a **System.IO.FileInfo** object and **IsReadOnly** is just one of its properties.</span></span>
<span data-ttu-id="de393-122">모든 속성을 보려면를 입력 `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType
Property` 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-122">To see all of the properties, type `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType
Property`.</span></span>

<span data-ttu-id="de393-123">`$true`자동 변수는 "TRUE" 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="de393-123">The `$true` automatic variable represents a value of "TRUE".</span></span>
<span data-ttu-id="de393-124">자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="de393-124">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### <span data-ttu-id="de393-125">예제 2: 레지스트리 항목 및 값 만들기</span><span class="sxs-lookup"><span data-stu-id="de393-125">Example 2: Create a registry entry and value</span></span>

<span data-ttu-id="de393-126">이 예제에서는를 사용 하 여 `Set-ItemProperty` 새 레지스트리 항목을 만들고 항목에 값을 할당 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="de393-126">This example shows how to use `Set-ItemProperty` to create a new registry entry and to assign a value to the entry.</span></span> <span data-ttu-id="de393-127">키에 "ContosoCompany" 키에 "NoOfEmployees" 항목을 만들고 `HKLM\Software` 해당 값을 823로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-127">It creates the "NoOfEmployees" entry in the "ContosoCompany" key in `HKLM\Software` key and sets its value to 823.</span></span>

<span data-ttu-id="de393-128">레지스트리 항목은 레지스트리 키 (항목)의 속성으로 간주 되기 때문에를 사용 하 여 `Set-ItemProperty` 레지스트리 항목을 만들고 해당 값을 설정 및 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-128">Because registry entries are considered to be properties of the registry keys, which are items, you use `Set-ItemProperty` to create registry entries, and to establish and change their values.</span></span>

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```Output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 823
```

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 824
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```Output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

<span data-ttu-id="de393-129">첫 번째 명령은 레지스트리 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="de393-129">The first command creates the registry entry.</span></span>
<span data-ttu-id="de393-130">**경로** 를 사용 하 여 드라이브의 경로를 지정 하 `HKLM:` 고 "software\mycompany" 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-130">It uses **Path** to specify the path of the `HKLM:` drive and the "Software\MyCompany" key.</span></span>
<span data-ttu-id="de393-131">이 명령은 **name** 을 사용 하 여 항목 이름 및 **값** 을 지정 하 고 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-131">The command uses **Name** to specify the entry name and **Value** to specify a value.</span></span>

<span data-ttu-id="de393-132">두 번째 명령은 cmdlet을 사용 하 여 `Get-ItemProperty` 새 레지스트리 항목을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-132">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>
<span data-ttu-id="de393-133">또는 cmdlet을 사용 하는 경우 항목 `Get-Item` `Get-ChildItem` 은 항목이 나 자식 항목이 아닌 키의 속성 이므로 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-133">If you use the `Get-Item` or `Get-ChildItem` cmdlets, the entries do not appear because they are properties of a key, not items or child items.</span></span>

<span data-ttu-id="de393-134">세 번째 명령은 **Noofemployees** 항목의 값을 824로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-134">The third command changes the value of the **NoOfEmployees** entry to 824.</span></span>

<span data-ttu-id="de393-135">Cmdlet을 사용 하 여 `New-ItemProperty` 레지스트리 항목 및 해당 값을 만든 다음를 사용 하 여 `Set-ItemProperty` 값을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-135">You can also use the `New-ItemProperty` cmdlet to create the registry entry and its value and then use `Set-ItemProperty` to change the value.</span></span>

<span data-ttu-id="de393-136">드라이브에 대 한 자세한 내용을 보려면 `HKLM:` 를 입력 하십시오 `Get-Help Get-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="de393-136">For more information about the `HKLM:` drive, type `Get-Help Get-PSDrive`.</span></span>
<span data-ttu-id="de393-137">PowerShell을 사용 하 여 레지스트리를 관리 하는 방법에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help Registry` .</span><span class="sxs-lookup"><span data-stu-id="de393-137">For more information about how to use PowerShell to manage the registry, type `Get-Help Registry`.</span></span>

### <span data-ttu-id="de393-138">예제 3: 파이프라인을 사용 하 여 항목 수정</span><span class="sxs-lookup"><span data-stu-id="de393-138">Example 3: Modify an item by using the pipeline</span></span>

<span data-ttu-id="de393-139">이러한 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 항목을로 보내는 방법을 보여 줍니다 `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="de393-139">These commands show how to use a pipeline operator (`|`) to send an item to `Set-ItemProperty`.</span></span>

<span data-ttu-id="de393-140">명령의 첫 번째 부분에서는를 사용 `Get-ChildItem` 하 여 "Weekly.txt" 파일을 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="de393-140">The first part of the command uses `Get-ChildItem` to get an object that represents the "Weekly.txt" file.</span></span> <span data-ttu-id="de393-141">이 명령은 파이프라인 연산자를 사용 하 여 파일 개체를로 보냅니다 `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="de393-141">The command uses a pipeline operator to send the file object to `Set-ItemProperty`.</span></span>
<span data-ttu-id="de393-142">이 `Set-ItemProperty` 명령은 **Name** 및 **value** 매개 변수를 사용 하 여 속성 및 속성의 새 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-142">The `Set-ItemProperty` command uses the **Name** and **Value** parameters to specify the property and its new value.</span></span>

<span data-ttu-id="de393-143">이 명령은 **InputObject** 매개 변수를 사용 하 여를 가져오는 개체를 지정 하는 것과 같습니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="de393-143">This command is equivalent to using the **InputObject** parameter to specify the object that `Get-ChildItem` gets.</span></span>

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
```

## <span data-ttu-id="de393-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="de393-144">PARAMETERS</span></span>

### <span data-ttu-id="de393-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="de393-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="de393-146">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="de393-147">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="de393-148">-제외</span><span class="sxs-lookup"><span data-stu-id="de393-148">-Exclude</span></span>

<span data-ttu-id="de393-149">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-149">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="de393-150">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-150">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="de393-151">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-151">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="de393-152">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-152">Wildcard characters are permitted.</span></span> <span data-ttu-id="de393-153">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="de393-153">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="de393-154">-Filter</span><span class="sxs-lookup"><span data-stu-id="de393-154">-Filter</span></span>

<span data-ttu-id="de393-155">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-155">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="de393-156">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="de393-156">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="de393-157">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-157">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="de393-158">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="de393-158">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="de393-159">-Force</span><span class="sxs-lookup"><span data-stu-id="de393-159">-Force</span></span>

<span data-ttu-id="de393-160">Cmdlet이 다른 방법으로는 사용자가 액세스할 수 없는 항목에 대 한 속성을 설정 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-160">Forces the cmdlet to set a property on items that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="de393-161">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="de393-161">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="de393-162">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de393-162">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="de393-163">-포함</span><span class="sxs-lookup"><span data-stu-id="de393-163">-Include</span></span>

<span data-ttu-id="de393-164">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-164">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="de393-165">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-165">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="de393-166">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-166">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="de393-167">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-167">Wildcard characters are permitted.</span></span> <span data-ttu-id="de393-168">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="de393-168">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="de393-169">-InputObject</span><span class="sxs-lookup"><span data-stu-id="de393-169">-InputObject</span></span>

<span data-ttu-id="de393-170">이 cmdlet이 변경 하는 속성을 가진 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-170">Specifies the object that has the properties that this cmdlet changes.</span></span>
<span data-ttu-id="de393-171">개체가 포함된 변수 또는 개체를 가져오는 명령을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="de393-171">Enter a variable that contains the object or a command that gets the object.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: propertyPSObjectPathSet, propertyPSObjectLiteralPathSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="de393-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="de393-172">-LiteralPath</span></span>

<span data-ttu-id="de393-173">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-173">Specifies a path to one or more locations.</span></span> <span data-ttu-id="de393-174">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="de393-174">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="de393-175">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-175">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="de393-176">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="de393-176">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="de393-177">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-177">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="de393-178">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="de393-178">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyPSObjectLiteralPathSet, propertyValueLiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="de393-179">-Name</span><span class="sxs-lookup"><span data-stu-id="de393-179">-Name</span></span>

<span data-ttu-id="de393-180">속성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-180">Specifies the name of the property.</span></span>

```yaml
Type: System.String
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="de393-181">-PassThru</span><span class="sxs-lookup"><span data-stu-id="de393-181">-PassThru</span></span>

<span data-ttu-id="de393-182">항목 속성을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-182">Returns an object that represents the item property.</span></span>
<span data-ttu-id="de393-183">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-183">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="de393-184">-Path</span><span class="sxs-lookup"><span data-stu-id="de393-184">-Path</span></span>

<span data-ttu-id="de393-185">수정할 속성이 포함 된 항목의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-185">Specifies the path of the items with the property to modify.</span></span>
<span data-ttu-id="de393-186">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-186">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="de393-187">-Type</span><span class="sxs-lookup"><span data-stu-id="de393-187">-Type</span></span>

<span data-ttu-id="de393-188">**Type** 은 레지스트리 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="de393-188">**Type** is a dynamic parameter that the Registry provider adds to the `Set-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="de393-189">이 매개 변수는 레지스트리 드라이브 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-189">This parameter only works in the registry drives.</span></span>

<span data-ttu-id="de393-190">이 cmdlet이 추가 하는 속성의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-190">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="de393-191">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="de393-192">**String** : null로 끝나는 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-192">**String** : Specifies a null-terminated string.</span></span> <span data-ttu-id="de393-193">**REG_SZ** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-193">Equivalent to **REG_SZ**.</span></span>
- <span data-ttu-id="de393-194">**ExpandString** : 값을 검색할 때 확장 되는 환경 변수에 대 한 확장 되지 않은 참조를 포함 하는 null로 끝나는 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-194">**ExpandString** : Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="de393-195">**REG_EXPAND_SZ** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-195">Equivalent to **REG_EXPAND_SZ**.</span></span>
- <span data-ttu-id="de393-196">**Binary** : 임의의 형식으로 된 이진 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-196">**Binary** : Specifies binary data in any form.</span></span> <span data-ttu-id="de393-197">**REG_BINARY** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-197">Equivalent to **REG_BINARY**.</span></span>
- <span data-ttu-id="de393-198">**DWord** : 32 비트 이진수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-198">**DWord** : Specifies a 32-bit binary number.</span></span> <span data-ttu-id="de393-199">**REG_DWORD** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-199">Equivalent to **REG_DWORD**.</span></span>
- <span data-ttu-id="de393-200">**다중 문자열** : 두 null 문자로 끝나는 null로 끝나는 문자열의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-200">**MultiString** : Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="de393-201">**REG_MULTI_SZ** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-201">Equivalent to **REG_MULTI_SZ**.</span></span>
- <span data-ttu-id="de393-202">**Qword(64** : 64 비트 이진수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-202">**Qword** : Specifies a 64-bit binary number.</span></span> <span data-ttu-id="de393-203">**REG_QWORD** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-203">Equivalent to **REG_QWORD**.</span></span>
- <span data-ttu-id="de393-204">**Unknown** : **REG_RESOURCE_LIST** 와 같은 지원 되지 않는 레지스트리 데이터 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="de393-204">**Unknown** : Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST**.</span></span>

```yaml
Type: Microsoft.Win32.RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="de393-205">-Value</span><span class="sxs-lookup"><span data-stu-id="de393-205">-Value</span></span>

<span data-ttu-id="de393-206">속성의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-206">Specifies the value of the property.</span></span>

```yaml
Type: System.Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="de393-207">-Confirm</span><span class="sxs-lookup"><span data-stu-id="de393-207">-Confirm</span></span>

<span data-ttu-id="de393-208">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-208">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="de393-209">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="de393-209">-WhatIf</span></span>

<span data-ttu-id="de393-210">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-210">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="de393-211">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-211">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="de393-212">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="de393-212">CommonParameters</span></span>

<span data-ttu-id="de393-213">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-213">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="de393-214">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de393-214">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="de393-215">입력</span><span class="sxs-lookup"><span data-stu-id="de393-215">INPUTS</span></span>

### <span data-ttu-id="de393-216">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="de393-216">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="de393-217">개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-217">You can pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="de393-218">출력</span><span class="sxs-lookup"><span data-stu-id="de393-218">OUTPUTS</span></span>

### <span data-ttu-id="de393-219">None, PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="de393-219">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="de393-220">이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 변경 된 항목 및 새 속성 값을 나타내는 **PSCustomObject** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-220">This cmdlet generates a **PSCustomObject** object that represents the item that was changed and its new property value, if you specify the **PassThru** parameter.</span></span>
<span data-ttu-id="de393-221">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-221">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="de393-222">참고</span><span class="sxs-lookup"><span data-stu-id="de393-222">NOTES</span></span>

<span data-ttu-id="de393-223">`Set-ItemProperty` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="de393-223">`Set-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="de393-224">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="de393-224">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="de393-225">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de393-225">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="de393-226">관련 링크</span><span class="sxs-lookup"><span data-stu-id="de393-226">RELATED LINKS</span></span>

[<span data-ttu-id="de393-227">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="de393-227">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="de393-228">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="de393-228">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="de393-229">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="de393-229">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="de393-230">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="de393-230">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="de393-231">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="de393-231">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="de393-232">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="de393-232">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="de393-233">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="de393-233">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="de393-234">about_Providers</span><span class="sxs-lookup"><span data-stu-id="de393-234">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

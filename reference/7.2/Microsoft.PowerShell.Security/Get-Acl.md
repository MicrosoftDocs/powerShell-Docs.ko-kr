---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: ed458e7f58ebb61611e2fd9e60430a7330087e8a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600644"
---
# <span data-ttu-id="489e9-102">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="489e9-102">Get-Acl</span></span>

## <span data-ttu-id="489e9-103">개요</span><span class="sxs-lookup"><span data-stu-id="489e9-103">SYNOPSIS</span></span>
<span data-ttu-id="489e9-104">파일 또는 레지스트리 키와 같은 리소스에 대한 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-104">Gets the security descriptor for a resource, such as a file or registry key.</span></span>

## <span data-ttu-id="489e9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="489e9-105">SYNTAX</span></span>

### <span data-ttu-id="489e9-106">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="489e9-106">ByPath (Default)</span></span>

```
Get-Acl [[-Path] <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="489e9-107">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="489e9-107">ByInputObject</span></span>

```
Get-Acl -InputObject <PSObject> [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="489e9-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="489e9-108">ByLiteralPath</span></span>

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="489e9-109">설명</span><span class="sxs-lookup"><span data-stu-id="489e9-109">DESCRIPTION</span></span>

<span data-ttu-id="489e9-110">`Get-Acl`Cmdlet은 파일 또는 리소스의 보안 설명자를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-110">The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="489e9-111">보안 설명자에는 리소스의 ACL(액세스 제어 목록)이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-111">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="489e9-112">ACL은 해당 리소스에 액세스해야 하는 사용자와 사용자 그룹의 사용 권한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-112">The ACL specifies the permissions that users and user groups have to access the resource.</span></span>

<span data-ttu-id="489e9-113">Windows PowerShell 3.0부터의 **InputObject** 매개 변수를 사용 하 여 `Get-Acl` 경로가 없는 개체의 보안 설명자를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-113">Beginning in Windows PowerShell 3.0, you can use the **InputObject** parameter of `Get-Acl` to get the security descriptor of objects that do not have a path.</span></span>

## <span data-ttu-id="489e9-114">예제</span><span class="sxs-lookup"><span data-stu-id="489e9-114">EXAMPLES</span></span>

### <span data-ttu-id="489e9-115">예제 1-폴더에 대 한 ACL 가져오기</span><span class="sxs-lookup"><span data-stu-id="489e9-115">Example 1- Get an ACL for a folder</span></span>

<span data-ttu-id="489e9-116">이 예제에서는 디렉터리의 보안 설명자를 가져옵니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="489e9-116">This example gets the security descriptor of the `C:\Windows` directory.</span></span>

```powershell
Get-Acl C:\Windows
```

### <span data-ttu-id="489e9-117">예 2-와일드 카드를 사용 하 여 폴더에 대 한 ACL 가져오기</span><span class="sxs-lookup"><span data-stu-id="489e9-117">Example 2 - Get an ACL for a folder using wildcards</span></span>

<span data-ttu-id="489e9-118">이 예제에서는 `.log` 이름이로 시작 하는 디렉터리의 모든 파일에 대 한 PowerShell 경로 및 SDDL을 가져옵니다 `C:\Windows` `s` .</span><span class="sxs-lookup"><span data-stu-id="489e9-118">This example gets the PowerShell path and SDDL for all of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

<span data-ttu-id="489e9-119">이 명령은 cmdlet을 사용 하 여 `Get-Acl` 각 로그 파일의 보안 설명자를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-119">The command uses the `Get-Acl` cmdlet to get objects representing the security descriptors of each log file.</span></span> <span data-ttu-id="489e9-120">파이프라인 연산자 ()를 사용 하 여 `|` 결과를 cmdlet으로 보냅니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="489e9-120">It uses a pipeline operator (`|`) to send the results to the `Format-List` cmdlet.</span></span> <span data-ttu-id="489e9-121">이 명령은의 **Property** 매개 변수를 사용 하 여 `Format-List` 각 보안 설명자 개체의 **PsPath** 및 **SDDL** 속성만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-121">The command uses the **Property** parameter of `Format-List` to display only the **PsPath** and **SDDL** properties of each security descriptor object.</span></span>

<span data-ttu-id="489e9-122">테이블에서 긴 값이 잘려서 표시 되기 때문에 목록은 PowerShell에서 자주 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-122">Lists are often used in PowerShell, because long values appear truncated in tables.</span></span>

<span data-ttu-id="489e9-123">**SDDL** 값은 보안 설명자에 모든 정보를 포함하는 간단한 텍스트 문자열이므로 시스템 관리자에게 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-123">The **SDDL** values are valuable to system administrators, because they are simple text strings that contain all of the information in the security descriptor.</span></span> <span data-ttu-id="489e9-124">또한 쉽게 전달 및 저장하고 필요한 경우 구문을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-124">As such, they are easy to pass and store, and they can be parsed when needed.</span></span>

### <span data-ttu-id="489e9-125">예 3-ACL에 대 한 감사 항목 수 가져오기</span><span class="sxs-lookup"><span data-stu-id="489e9-125">Example 3 - Get count of Audit entries for an ACL</span></span>

<span data-ttu-id="489e9-126">이 예제에서는 `.log` `C:\Windows` 디렉터리에서 이름이로 시작 하는 파일의 보안 설명자를 가져옵니다 `s` .</span><span class="sxs-lookup"><span data-stu-id="489e9-126">This example gets the security descriptors of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

<span data-ttu-id="489e9-127">**Audit** 매개 변수를 사용하여 보안 설명자의 SACL에서 감사 레코드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-127">It uses the **Audit** parameter to get the audit records from the SACL in the security descriptor.</span></span>
<span data-ttu-id="489e9-128">그런 다음 cmdlet을 사용 하 여 `ForEach-Object` 각 파일에 연결 된 감사 레코드 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-128">Then it uses the `ForEach-Object` cmdlet to count the number of audit records associated with each file.</span></span> <span data-ttu-id="489e9-129">결과는 각 로그 파일의 감사 레코드 수를 나타내는 숫자 목록으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-129">The result is a list of numbers representing the number of audit records for each log file.</span></span>

### <span data-ttu-id="489e9-130">예 4-레지스트리 키에 대 한 ACL 가져오기</span><span class="sxs-lookup"><span data-stu-id="489e9-130">Example 4 - Get an ACL for a registry key</span></span>

<span data-ttu-id="489e9-131">이 예제에서는 cmdlet을 사용 하 여 `Get-Acl` 레지스트리의 제어 하위 키 ()에 대 한 보안 설명자를 가져옵니다 `HKLM:\SYSTEM\CurrentControlSet\Control` .</span><span class="sxs-lookup"><span data-stu-id="489e9-131">This example uses the `Get-Acl` cmdlet to get the security descriptor of the Control subkey (`HKLM:\SYSTEM\CurrentControlSet\Control`) of the registry.</span></span>

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

<span data-ttu-id="489e9-132">**Path** 매개 변수는 제어 하위 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-132">The **Path** parameter specifies the Control subkey.</span></span> <span data-ttu-id="489e9-133">파이프라인 연산자 ( `|` )는 명령에 가져오는 보안 설명자를 전달 합니다 .이 설명자는 `Get-Acl` `Format-List` 보안 설명자의 속성을 목록으로 서식 지정 하 여 쉽게 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-133">The pipeline operator (`|`) passes the security descriptor that `Get-Acl` gets to the `Format-List` command, which formats the properties of the security descriptor as a list so that they are easy to read.</span></span>

### <span data-ttu-id="489e9-134">예 5- **InputObject** 를 사용 하 여 ACL 가져오기</span><span class="sxs-lookup"><span data-stu-id="489e9-134">Example 5 - Get an ACL using **InputObject**</span></span>

<span data-ttu-id="489e9-135">이 예제에서는의 **InputObject** 매개 변수를 사용 하 여 `Get-Acl` 저장소 하위 시스템 개체의 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-135">This example uses the **InputObject** parameter of `Get-Acl` to get the security descriptor of a storage subsystem object.</span></span>

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## <span data-ttu-id="489e9-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="489e9-136">PARAMETERS</span></span>

### <span data-ttu-id="489e9-137">-감사</span><span class="sxs-lookup"><span data-stu-id="489e9-137">-Audit</span></span>

<span data-ttu-id="489e9-138">SACL(시스템 액세스 제어 목록)에서 보안 설명자의 감사 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-138">Gets the audit data for the security descriptor from the system access control list (SACL).</span></span>

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

### <span data-ttu-id="489e9-139">-제외</span><span class="sxs-lookup"><span data-stu-id="489e9-139">-Exclude</span></span>

<span data-ttu-id="489e9-140">지정된 항목을 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-140">Omits the specified items.</span></span> <span data-ttu-id="489e9-141">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-141">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="489e9-142">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-142">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="489e9-143">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-143">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="489e9-144">-Filter</span><span class="sxs-lookup"><span data-stu-id="489e9-144">-Filter</span></span>

<span data-ttu-id="489e9-145">공급자의 형식 또는 언어에 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-145">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="489e9-146">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-146">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="489e9-147">와일드카드 사용을 포함한 필터 구문은 공급자에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-147">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="489e9-148">필터는 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 필터를 적용 하기 때문에 다른 매개 변수 보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-148">Filters are more efficient than other parameters, because the provider applies them when getting the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="489e9-149">-포함</span><span class="sxs-lookup"><span data-stu-id="489e9-149">-Include</span></span>

<span data-ttu-id="489e9-150">지정된 항목만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-150">Gets only the specified items.</span></span> <span data-ttu-id="489e9-151">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-151">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="489e9-152">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-152">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="489e9-153">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-153">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="489e9-154">-Path</span><span class="sxs-lookup"><span data-stu-id="489e9-154">-Path</span></span>

<span data-ttu-id="489e9-155">리소스의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-155">Specifies the path to a resource.</span></span> <span data-ttu-id="489e9-156">`Get-Acl` 경로로 표시 되는 리소스의 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-156">`Get-Acl` gets the security descriptor of the resource indicated by the path.</span></span> <span data-ttu-id="489e9-157">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-157">Wildcards are permitted.</span></span> <span data-ttu-id="489e9-158">**Path** 매개 변수를 생략 하는 경우 `Get-Acl` 현재 디렉터리의 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-158">If you omit the **Path** parameter, `Get-Acl` gets the security descriptor of the current directory.</span></span>

<span data-ttu-id="489e9-159">매개 변수 이름("Path")은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-159">The parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="489e9-160">-InputObject</span><span class="sxs-lookup"><span data-stu-id="489e9-160">-InputObject</span></span>

<span data-ttu-id="489e9-161">지정된 개체에 대한 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-161">Gets the security descriptor for the specified object.</span></span> <span data-ttu-id="489e9-162">개체가 포함된 변수 또는 개체를 가져오는 명령을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="489e9-162">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="489e9-163">경로 이외의 개체는로 파이프 할 수 없습니다 `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="489e9-163">You cannot pipe an object, other than a path, to `Get-Acl`.</span></span> <span data-ttu-id="489e9-164">대신 명령에서 **InputObject** 매개 변수를 명시적으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-164">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="489e9-165">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-165">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="489e9-166">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="489e9-166">-LiteralPath</span></span>

<span data-ttu-id="489e9-167">리소스의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-167">Specifies the path to a resource.</span></span> <span data-ttu-id="489e9-168">**Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-168">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="489e9-169">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-169">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="489e9-170">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="489e9-170">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="489e9-171">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-171">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="489e9-172">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-172">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="489e9-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="489e9-173">CommonParameters</span></span>

<span data-ttu-id="489e9-174">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="489e9-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="489e9-175">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="489e9-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="489e9-176">입력</span><span class="sxs-lookup"><span data-stu-id="489e9-176">INPUTS</span></span>

### <span data-ttu-id="489e9-177">System.String</span><span class="sxs-lookup"><span data-stu-id="489e9-177">System.String</span></span>

<span data-ttu-id="489e9-178">경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="489e9-178">You can pipe a string that contains a path to `Get-Acl`.</span></span>

## <span data-ttu-id="489e9-179">출력</span><span class="sxs-lookup"><span data-stu-id="489e9-179">OUTPUTS</span></span>

### <span data-ttu-id="489e9-180">Accesscontrol-namespace. System.security.accesscontrol.filesecurity, Accesscontrol-namespace 보안, Accesscontrol-namespace. RegistrySecurity (영문).</span><span class="sxs-lookup"><span data-stu-id="489e9-180">System.Security.AccessControl.FileSecurity, System.Security.AccessControl.DirectorySecurity, System.Security.AccessControl.RegistrySecurity</span></span>

<span data-ttu-id="489e9-181">`Get-Acl` 가져오는 Acl을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-181">`Get-Acl` returns an object that represents the ACLs that it gets.</span></span> <span data-ttu-id="489e9-182">개체 유형은 ACL 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-182">The object type depends upon the ACL type.</span></span>

## <span data-ttu-id="489e9-183">참고</span><span class="sxs-lookup"><span data-stu-id="489e9-183">NOTES</span></span>

<span data-ttu-id="489e9-184">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-184">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="489e9-185">기본적으로 리소스에 `Get-Acl` `<provider>::<resource-path>` 대 한 DACL (임의 액세스 제어 목록)에 있는 액세스 제어 항목의 목록 (배열), 리소스의 소유자 및 리소스에 대 한 PowerShell 경로를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-185">By default, `Get-Acl` displays the PowerShell path to the resource (`<provider>::<resource-path>`), the owner of the resource, and "Access", a list (array) of the access control entries in the discretionary access control list (DACL) for the resource.</span></span> <span data-ttu-id="489e9-186">DACL 목록은 리소스 소유자가 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-186">The DACL list is controlled by the resource owner.</span></span>

<span data-ttu-id="489e9-187">결과를 목록 ()으로 지정 하면 `Get-Acl | Format-List` 경로, 소유자 및 액세스 목록 뿐만 아니라 PowerShell에서 다음과 같은 속성 및 속성 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-187">When you format the result as a list, (`Get-Acl | Format-List`), in addition to the path, owner, and access list, PowerShell displays the following properties and property values:</span></span>

- <span data-ttu-id="489e9-188">**그룹**: 소유자의 보안 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-188">**Group**: The security group of the owner.</span></span>
- <span data-ttu-id="489e9-189">**Audit**: SACL (시스템 액세스 제어 목록)에 있는 항목의 목록 (배열)입니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-189">**Audit**:  A list (array) of entries in the system access control list (SACL).</span></span> <span data-ttu-id="489e9-190">SACL은 Windows에서 감사 레코드를 생성하는 대상 액세스 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-190">The SACL specifies the types of access attempts for which Windows generates audit records.</span></span>
- <span data-ttu-id="489e9-191">**Sddl**: 보안 설명자 정의 언어 형식의 단일 텍스트 문자열에 표시 되는 리소스의 보안 설명자입니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-191">**Sddl**: The security descriptor of the resource displayed in a single text string in Security Descriptor Definition Language format.</span></span> <span data-ttu-id="489e9-192">PowerShell은 보안 설명자의 **Getsddlform** 메서드를 사용 하 여이 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-192">PowerShell uses the **GetSddlForm** method of security descriptors to get this data.</span></span>

<span data-ttu-id="489e9-193">`Get-Acl`는 파일 시스템 및 레지스트리 공급자에서 지원 되므로를 사용 하 여 파일 `Get-Acl` 및 디렉터리와 같은 파일 시스템 개체의 ACL과 레지스트리 키, 항목 등의 레지스트리 개체를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="489e9-193">Because `Get-Acl` is supported by the file system and registry providers, you can use `Get-Acl` to view the ACL of file system objects, such as files and directories, and registry objects, such as registry keys and entries.</span></span>

## <span data-ttu-id="489e9-194">관련 링크</span><span class="sxs-lookup"><span data-stu-id="489e9-194">RELATED LINKS</span></span>

[<span data-ttu-id="489e9-195">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="489e9-195">Set-Acl</span></span>](Set-Acl.md)

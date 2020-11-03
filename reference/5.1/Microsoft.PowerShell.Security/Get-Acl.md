---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: 6b862ad6bada3035551d35d592183db5805b232f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214281"
---
# <span data-ttu-id="f9039-103">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="f9039-103">Get-Acl</span></span>

## <span data-ttu-id="f9039-104">개요</span><span class="sxs-lookup"><span data-stu-id="f9039-104">SYNOPSIS</span></span>
<span data-ttu-id="f9039-105">파일 또는 레지스트리 키와 같은 리소스에 대한 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-105">Gets the security descriptor for a resource, such as a file or registry key.</span></span>

## <span data-ttu-id="f9039-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f9039-106">SYNTAX</span></span>

### <span data-ttu-id="f9039-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="f9039-107">ByPath (Default)</span></span>

```
Get-Acl [[-Path] <String[]>] [-Audit] [-AllCentralAccessPolicies] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="f9039-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="f9039-108">ByInputObject</span></span>

```
Get-Acl -InputObject <PSObject> [-Audit] [-AllCentralAccessPolicies] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="f9039-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="f9039-109">ByLiteralPath</span></span>

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-AllCentralAccessPolicies] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="f9039-110">설명</span><span class="sxs-lookup"><span data-stu-id="f9039-110">DESCRIPTION</span></span>

<span data-ttu-id="f9039-111">`Get-Acl`Cmdlet은 파일 또는 리소스의 보안 설명자를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-111">The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="f9039-112">보안 설명자에는 리소스의 ACL(액세스 제어 목록)이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-112">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="f9039-113">ACL은 해당 리소스에 액세스해야 하는 사용자와 사용자 그룹의 사용 권한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-113">The ACL specifies the permissions that users and user groups have to access the resource.</span></span>

<span data-ttu-id="f9039-114">Windows PowerShell 3.0부터의 **InputObject** 매개 변수를 사용 하 여 `Get-Acl` 경로가 없는 개체의 보안 설명자를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-114">Beginning in Windows PowerShell 3.0, you can use the **InputObject** parameter of `Get-Acl` to get the security descriptor of objects that do not have a path.</span></span>

## <span data-ttu-id="f9039-115">예제</span><span class="sxs-lookup"><span data-stu-id="f9039-115">EXAMPLES</span></span>

### <span data-ttu-id="f9039-116">예제 1-폴더에 대 한 ACL 가져오기</span><span class="sxs-lookup"><span data-stu-id="f9039-116">Example 1- Get an ACL for a folder</span></span>

<span data-ttu-id="f9039-117">이 예제에서는 디렉터리의 보안 설명자를 가져옵니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="f9039-117">This example gets the security descriptor of the `C:\Windows` directory.</span></span>

```powershell
Get-Acl C:\Windows
```

### <span data-ttu-id="f9039-118">예 2-와일드 카드를 사용 하 여 폴더에 대 한 ACL 가져오기</span><span class="sxs-lookup"><span data-stu-id="f9039-118">Example 2 - Get an ACL for a folder using wildcards</span></span>

<span data-ttu-id="f9039-119">이 예제에서는 `.log` 이름이로 시작 하는 디렉터리의 모든 파일에 대 한 PowerShell 경로 및 SDDL을 가져옵니다 `C:\Windows` `s` .</span><span class="sxs-lookup"><span data-stu-id="f9039-119">This example gets the PowerShell path and SDDL for all of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

<span data-ttu-id="f9039-120">이 명령은 cmdlet을 사용 하 여 `Get-Acl` 각 로그 파일의 보안 설명자를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-120">The command uses the `Get-Acl` cmdlet to get objects representing the security descriptors of each log file.</span></span> <span data-ttu-id="f9039-121">파이프라인 연산자 ()를 사용 하 여 `|` 결과를 cmdlet으로 보냅니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="f9039-121">It uses a pipeline operator (`|`) to send the results to the `Format-List` cmdlet.</span></span> <span data-ttu-id="f9039-122">이 명령은의 **Property** 매개 변수를 사용 하 여 `Format-List` 각 보안 설명자 개체의 **PsPath** 및 **SDDL** 속성만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-122">The command uses the **Property** parameter of `Format-List` to display only the **PsPath** and **SDDL** properties of each security descriptor object.</span></span>

<span data-ttu-id="f9039-123">테이블에서 긴 값이 잘려서 표시 되기 때문에 목록은 PowerShell에서 자주 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-123">Lists are often used in PowerShell, because long values appear truncated in tables.</span></span>

<span data-ttu-id="f9039-124">**SDDL** 값은 보안 설명자에 모든 정보를 포함하는 간단한 텍스트 문자열이므로 시스템 관리자에게 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-124">The **SDDL** values are valuable to system administrators, because they are simple text strings that contain all of the information in the security descriptor.</span></span> <span data-ttu-id="f9039-125">또한 쉽게 전달 및 저장하고 필요한 경우 구문을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-125">As such, they are easy to pass and store, and they can be parsed when needed.</span></span>

### <span data-ttu-id="f9039-126">예 3-ACL에 대 한 감사 항목 수 가져오기</span><span class="sxs-lookup"><span data-stu-id="f9039-126">Example 3 - Get count of Audit entries for an ACL</span></span>

<span data-ttu-id="f9039-127">이 예제에서는 `.log` `C:\Windows` 디렉터리에서 이름이로 시작 하는 파일의 보안 설명자를 가져옵니다 `s` .</span><span class="sxs-lookup"><span data-stu-id="f9039-127">This example gets the security descriptors of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

<span data-ttu-id="f9039-128">**Audit** 매개 변수를 사용하여 보안 설명자의 SACL에서 감사 레코드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-128">It uses the **Audit** parameter to get the audit records from the SACL in the security descriptor.</span></span>
<span data-ttu-id="f9039-129">그런 다음 cmdlet을 사용 하 여 `ForEach-Object` 각 파일에 연결 된 감사 레코드 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-129">Then it uses the `ForEach-Object` cmdlet to count the number of audit records associated with each file.</span></span> <span data-ttu-id="f9039-130">결과는 각 로그 파일의 감사 레코드 수를 나타내는 숫자 목록으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-130">The result is a list of numbers representing the number of audit records for each log file.</span></span>

### <span data-ttu-id="f9039-131">예 4-레지스트리 키에 대 한 ACL 가져오기</span><span class="sxs-lookup"><span data-stu-id="f9039-131">Example 4 - Get an ACL for a registry key</span></span>

<span data-ttu-id="f9039-132">이 예제에서는 cmdlet을 사용 하 여 `Get-Acl` 레지스트리의 제어 하위 키 ()에 대 한 보안 설명자를 가져옵니다 `HKLM:\SYSTEM\CurrentControlSet\Control` .</span><span class="sxs-lookup"><span data-stu-id="f9039-132">This example uses the `Get-Acl` cmdlet to get the security descriptor of the Control subkey (`HKLM:\SYSTEM\CurrentControlSet\Control`) of the registry.</span></span>

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

<span data-ttu-id="f9039-133">**Path** 매개 변수는 제어 하위 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-133">The **Path** parameter specifies the Control subkey.</span></span> <span data-ttu-id="f9039-134">파이프라인 연산자 ( `|` )는 명령에 가져오는 보안 설명자를 전달 합니다 .이 설명자는 `Get-Acl` `Format-List` 보안 설명자의 속성을 목록으로 서식 지정 하 여 쉽게 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-134">The pipeline operator (`|`) passes the security descriptor that `Get-Acl` gets to the `Format-List` command, which formats the properties of the security descriptor as a list so that they are easy to read.</span></span>

### <span data-ttu-id="f9039-135">예 5- **InputObject** 를 사용 하 여 ACL 가져오기</span><span class="sxs-lookup"><span data-stu-id="f9039-135">Example 5 - Get an ACL using **InputObject**</span></span>

<span data-ttu-id="f9039-136">이 예제에서는의 **InputObject** 매개 변수를 사용 하 여 `Get-Acl` 저장소 하위 시스템 개체의 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-136">This example uses the **InputObject** parameter of `Get-Acl` to get the security descriptor of a storage subsystem object.</span></span>

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## <span data-ttu-id="f9039-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f9039-137">PARAMETERS</span></span>

### <span data-ttu-id="f9039-138">-감사</span><span class="sxs-lookup"><span data-stu-id="f9039-138">-Audit</span></span>

<span data-ttu-id="f9039-139">SACL(시스템 액세스 제어 목록)에서 보안 설명자의 감사 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-139">Gets the audit data for the security descriptor from the system access control list (SACL).</span></span>

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

### <span data-ttu-id="f9039-140">-제외</span><span class="sxs-lookup"><span data-stu-id="f9039-140">-Exclude</span></span>

<span data-ttu-id="f9039-141">지정된 항목을 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-141">Omits the specified items.</span></span> <span data-ttu-id="f9039-142">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-142">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f9039-143">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-143">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="f9039-144">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-144">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="f9039-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="f9039-145">-Filter</span></span>

<span data-ttu-id="f9039-146">공급자의 형식 또는 언어에 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-146">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="f9039-147">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-147">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f9039-148">와일드카드 사용을 포함한 필터 구문은 공급자에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-148">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="f9039-149">필터는 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 필터를 적용 하기 때문에 다른 매개 변수 보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-149">Filters are more efficient than other parameters, because the provider applies them when getting the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="f9039-150">-포함</span><span class="sxs-lookup"><span data-stu-id="f9039-150">-Include</span></span>

<span data-ttu-id="f9039-151">지정된 항목만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-151">Gets only the specified items.</span></span> <span data-ttu-id="f9039-152">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-152">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f9039-153">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-153">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="f9039-154">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-154">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="f9039-155">-Path</span><span class="sxs-lookup"><span data-stu-id="f9039-155">-Path</span></span>

<span data-ttu-id="f9039-156">리소스의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-156">Specifies the path to a resource.</span></span> <span data-ttu-id="f9039-157">`Get-Acl` 경로로 표시 되는 리소스의 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-157">`Get-Acl` gets the security descriptor of the resource indicated by the path.</span></span> <span data-ttu-id="f9039-158">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-158">Wildcards are permitted.</span></span> <span data-ttu-id="f9039-159">**Path** 매개 변수를 생략 하는 경우 `Get-Acl` 현재 디렉터리의 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-159">If you omit the **Path** parameter, `Get-Acl` gets the security descriptor of the current directory.</span></span>

<span data-ttu-id="f9039-160">매개 변수 이름("Path")은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-160">The parameter name ("Path") is optional.</span></span>

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

### <span data-ttu-id="f9039-161">-AllCentralAccessPolicies</span><span class="sxs-lookup"><span data-stu-id="f9039-161">-AllCentralAccessPolicies</span></span>

<span data-ttu-id="f9039-162">컴퓨터에서 사용할 수 있는 모든 중앙 액세스 정책에 대한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-162">Gets information about all central access policies that are enabled on the computer.</span></span>

<span data-ttu-id="f9039-163">Windows Server 2012부터 관리자는 Active Directory 및 그룹 정책를 사용 하 여 사용자 및 그룹에 대 한 중앙 액세스 정책을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-163">Beginning in Windows Server 2012, administrators can use Active Directory and Group Policy to set central access policies for users and groups.</span></span> <span data-ttu-id="f9039-164">자세한 내용은 [동적 Access Control: 시나리오 개요](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f9039-164">For more information, see [Dynamic Access Control: Scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span></span>

<span data-ttu-id="f9039-165">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-165">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f9039-166">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f9039-166">-InputObject</span></span>

<span data-ttu-id="f9039-167">지정된 개체에 대한 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-167">Gets the security descriptor for the specified object.</span></span> <span data-ttu-id="f9039-168">개체가 포함된 변수 또는 개체를 가져오는 명령을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="f9039-168">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="f9039-169">경로 이외의 개체는로 파이프 할 수 없습니다 `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="f9039-169">You cannot pipe an object, other than a path, to `Get-Acl`.</span></span> <span data-ttu-id="f9039-170">대신 명령에서 **InputObject** 매개 변수를 명시적으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-170">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="f9039-171">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-171">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f9039-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f9039-172">-LiteralPath</span></span>

<span data-ttu-id="f9039-173">리소스의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-173">Specifies the path to a resource.</span></span> <span data-ttu-id="f9039-174">**Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-174">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="f9039-175">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-175">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="f9039-176">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="f9039-176">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="f9039-177">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-177">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="f9039-178">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-178">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f9039-179">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="f9039-179">-UseTransaction</span></span>

<span data-ttu-id="f9039-180">활성 트랜잭션에 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-180">Includes the command in the active transaction.</span></span>
<span data-ttu-id="f9039-181">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-181">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="f9039-182">자세한 내용은 about_Transactions를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9039-182">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="f9039-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f9039-183">CommonParameters</span></span>

<span data-ttu-id="f9039-184">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f9039-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f9039-185">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9039-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f9039-186">입력</span><span class="sxs-lookup"><span data-stu-id="f9039-186">INPUTS</span></span>

### <span data-ttu-id="f9039-187">System.String</span><span class="sxs-lookup"><span data-stu-id="f9039-187">System.String</span></span>

<span data-ttu-id="f9039-188">경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="f9039-188">You can pipe a string that contains a path to `Get-Acl`.</span></span>

## <span data-ttu-id="f9039-189">출력</span><span class="sxs-lookup"><span data-stu-id="f9039-189">OUTPUTS</span></span>

### <span data-ttu-id="f9039-190">Accesscontrol-namespace. System.security.accesscontrol.filesecurity, Accesscontrol-namespace 보안, Accesscontrol-namespace. RegistrySecurity (영문).</span><span class="sxs-lookup"><span data-stu-id="f9039-190">System.Security.AccessControl.FileSecurity, System.Security.AccessControl.DirectorySecurity, System.Security.AccessControl.RegistrySecurity</span></span>

<span data-ttu-id="f9039-191">`Get-Acl` 가져오는 Acl을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-191">`Get-Acl` returns an object that represents the ACLs that it gets.</span></span> <span data-ttu-id="f9039-192">개체 유형은 ACL 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-192">The object type depends upon the ACL type.</span></span>

## <span data-ttu-id="f9039-193">참고</span><span class="sxs-lookup"><span data-stu-id="f9039-193">NOTES</span></span>

<span data-ttu-id="f9039-194">기본적으로 리소스에 `Get-Acl` `<provider>::<resource-path>` 대 한 DACL (임의 액세스 제어 목록)에 있는 액세스 제어 항목의 목록 (배열), 리소스의 소유자 및 리소스에 대 한 PowerShell 경로를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-194">By default, `Get-Acl` displays the PowerShell path to the resource (`<provider>::<resource-path>`), the owner of the resource, and "Access", a list (array) of the access control entries in the discretionary access control list (DACL) for the resource.</span></span> <span data-ttu-id="f9039-195">DACL 목록은 리소스 소유자가 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-195">The DACL list is controlled by the resource owner.</span></span>

<span data-ttu-id="f9039-196">결과를 목록 ()으로 지정 하면 `Get-Acl | Format-List` 경로, 소유자 및 액세스 목록 뿐만 아니라 PowerShell에서 다음과 같은 속성 및 속성 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-196">When you format the result as a list, (`Get-Acl | Format-List`), in addition to the path, owner, and access list, PowerShell displays the following properties and property values:</span></span>

- <span data-ttu-id="f9039-197">**그룹** : 소유자의 보안 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-197">**Group** : The security group of the owner.</span></span>
- <span data-ttu-id="f9039-198">**Audit** : SACL (시스템 액세스 제어 목록)에 있는 항목의 목록 (배열)입니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-198">**Audit** :  A list (array) of entries in the system access control list (SACL).</span></span> <span data-ttu-id="f9039-199">SACL은 Windows에서 감사 레코드를 생성하는 대상 액세스 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-199">The SACL specifies the types of access attempts for which Windows generates audit records.</span></span>
- <span data-ttu-id="f9039-200">**Sddl** : 보안 설명자 정의 언어 형식의 단일 텍스트 문자열에 표시 되는 리소스의 보안 설명자입니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-200">**Sddl** : The security descriptor of the resource displayed in a single text string in Security Descriptor Definition Language format.</span></span> <span data-ttu-id="f9039-201">PowerShell은 보안 설명자의 **Getsddlform** 메서드를 사용 하 여이 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-201">PowerShell uses the **GetSddlForm** method of security descriptors to get this data.</span></span>

<span data-ttu-id="f9039-202">`Get-Acl`는 파일 시스템 및 레지스트리 공급자에서 지원 되므로를 사용 하 여 파일 `Get-Acl` 및 디렉터리와 같은 파일 시스템 개체의 ACL과 레지스트리 키, 항목 등의 레지스트리 개체를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9039-202">Because `Get-Acl` is supported by the file system and registry providers, you can use `Get-Acl` to view the ACL of file system objects, such as files and directories, and registry objects, such as registry keys and entries.</span></span>

## <span data-ttu-id="f9039-203">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f9039-203">RELATED LINKS</span></span>

[<span data-ttu-id="f9039-204">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="f9039-204">Set-Acl</span></span>](Set-Acl.md)

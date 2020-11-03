---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: b2c5b8596da085fab3af7a1545569dd65931a5f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215418"
---
# <span data-ttu-id="c1c30-103">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c1c30-103">Get-ItemProperty</span></span>

## <span data-ttu-id="c1c30-104">개요</span><span class="sxs-lookup"><span data-stu-id="c1c30-104">SYNOPSIS</span></span>
<span data-ttu-id="c1c30-105">지정된 항목의 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-105">Gets the properties of a specified item.</span></span>

## <span data-ttu-id="c1c30-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c1c30-106">SYNTAX</span></span>

### <span data-ttu-id="c1c30-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="c1c30-107">Path (Default)</span></span>

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="c1c30-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c1c30-108">LiteralPath</span></span>

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="c1c30-109">설명</span><span class="sxs-lookup"><span data-stu-id="c1c30-109">DESCRIPTION</span></span>

<span data-ttu-id="c1c30-110">`Get-ItemProperty`Cmdlet은 지정 된 항목의 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-110">The `Get-ItemProperty` cmdlet gets the properties of the specified items.</span></span>
<span data-ttu-id="c1c30-111">예를 들어이 cmdlet을 사용 하 여 파일 개체의 LastAccessTime 속성 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-111">For example, you can use this cmdlet to get the value of the LastAccessTime property of a file object.</span></span>
<span data-ttu-id="c1c30-112">이 cmdlet을 사용 하 여 레지스트리 항목 및 해당 값을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-112">You can also use this cmdlet to view registry entries and their values.</span></span>

## <span data-ttu-id="c1c30-113">예제</span><span class="sxs-lookup"><span data-stu-id="c1c30-113">EXAMPLES</span></span>

### <span data-ttu-id="c1c30-114">예 1: 특정 디렉터리에 대 한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="c1c30-114">Example 1: Get information about a specific directory</span></span>

<span data-ttu-id="c1c30-115">이 명령은 "C:\Windows" 디렉터리에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-115">This command gets information about the "C:\Windows" directory.</span></span>

```powershell
Get-ItemProperty C:\Windows
```

### <span data-ttu-id="c1c30-116">예 2: 특정 파일의 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="c1c30-116">Example 2: Get the properties of a specific file</span></span>

<span data-ttu-id="c1c30-117">이 명령은 "C:\Test\Weather.xls" 파일의 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-117">This command gets the properties of the "C:\Test\Weather.xls" file.</span></span>
<span data-ttu-id="c1c30-118">결과를 cmdlet으로 파이프 하 여 `Format-List` 출력을 목록으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-118">The result is piped to the `Format-List` cmdlet to display the output as a list.</span></span>

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### <span data-ttu-id="c1c30-119">예제 3: 레지스트리 하위 키에 레지스트리 항목의 값 이름 및 데이터 표시</span><span class="sxs-lookup"><span data-stu-id="c1c30-119">Example 3: Display the value name and data of registry entries in a registry subkey</span></span>

<span data-ttu-id="c1c30-120">이 명령은 "CurrentVersion" 레지스트리 하위 키에 포함 된 각 레지스트리 항목의 값 이름과 데이터를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-120">This command displays the value name and data of each of the registry entries contained in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="c1c30-121">명령에는 `HKLM:` 레지스트리의 "HKEY_LOCAL_MACHINE" 하이브에 매핑되는 라는 PowerShell 드라이브가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-121">Note that the command requires that there is a PowerShell drive named `HKLM:` that is mapped to the "HKEY_LOCAL_MACHINE" hive of the registry.</span></span>
<span data-ttu-id="c1c30-122">기본적으로 PowerShell에서 해당 이름과 매핑을 가진 드라이브를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-122">A drive with that name and mapping is available in PowerShell by default.</span></span>
<span data-ttu-id="c1c30-123">또는 공급자 이름으로 시작되고 그 뒤에 두 개의 콜론이 오는 대체</span><span class="sxs-lookup"><span data-stu-id="c1c30-123">Alternatively, the path to this registry subkey can be specified by using the following alternative path that begins with the provider name followed by two colons:</span></span>

<span data-ttu-id="c1c30-124">"Registry:: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion"입니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-124">"Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion".</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

### <span data-ttu-id="c1c30-125">예제 4: 레지스트리 하위 키에서 레지스트리 항목의 값 이름 및 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="c1c30-125">Example 4: Get the value name and data of a registry entry in a registry subkey</span></span>

<span data-ttu-id="c1c30-126">이 명령은 "CurrentVersion" 레지스트리 하위 키에 있는 "ProgramFilesDir" 레지스트리 항목의 값 이름과 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-126">This command gets the value name and data of the "ProgramFilesDir" registry entry in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="c1c30-127">이 명령은 **Path** 매개 변수를 사용 하 여 하위 키를 지정 하 고 name 매개 변수를 사용 하 여 항목의 값 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-127">The command uses the **Path** parameter to specify the subkey and the Name parameter to specify the value name of the entry.</span></span>

<span data-ttu-id="c1c30-128">이 명령은 뒤로 틱 또는 억음 악센트 기호 ()를 사용 하 여 \` 두 번째 줄에서 명령을 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-128">The command uses a back tick or grave accent (\`), the PowerShell continuation character, to continue the command on the second line.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### <span data-ttu-id="c1c30-129">예 5: 레지스트리 키에서 레지스트리 항목의 값 이름 및 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="c1c30-129">Example 5: Get the value names and data of registry entries in a registry key</span></span>

<span data-ttu-id="c1c30-130">이 명령은 "PowerShellEngine" 레지스트리 키에 있는 레지스트리 항목의 값 이름과 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-130">This command gets the value names and data of the registry entries in the "PowerShellEngine" registry key.</span></span>
<span data-ttu-id="c1c30-131">결과는 다음과 같은 샘플 출력에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-131">The results are shown in the following sample output.</span></span>

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

### <span data-ttu-id="c1c30-132">예제 6: 레지스트리 값 및 데이터의 결과 가져오기, 서식 지정 및 표시</span><span class="sxs-lookup"><span data-stu-id="c1c30-132">Example 6: Get, format, and display the results of registry values and data</span></span>

<span data-ttu-id="c1c30-133">이 예제에서는 `Get-ItemProperty` 레지스트리 값 및 데이터를 쉽게 확인 하 고 결과를 쉽게 해석할 수 있도록 목록에서 명령의 출력에 서식을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-133">This example shows how to format the output of a `Get-ItemProperty` command in a list to make it easy to see the registry values and data and to make it easy to interpret the results.</span></span>

<span data-ttu-id="c1c30-134">첫 번째 명령은 cmdlet을 사용 하 여 `Get-ItemProperty` **Microsoft PowerShell** 하위 키에 있는 레지스트리 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-134">The first command uses the `Get-ItemProperty` cmdlet to get the registry entries in the **Microsoft.PowerShell** subkey.</span></span>
<span data-ttu-id="c1c30-135">이 하위 키는 PowerShell의 기본 셸에 대 한 옵션을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-135">This subkey stores options for the default shell for PowerShell.</span></span>
<span data-ttu-id="c1c30-136">결과는 다음과 같은 샘플 출력에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-136">The results are shown in the following sample output.</span></span>

<span data-ttu-id="c1c30-137">출력은 "Path" 및 "Set-executionpolicy" 라는 두 개의 레지스트리 항목이 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-137">The output shows that there are two registry entries, "Path" and "ExecutionPolicy".</span></span>
<span data-ttu-id="c1c30-138">레지스트리 키에 포함된 항목이 5개보다 적을 경우 기본적으로 테이블 형식으로 표시되지만 대체로 목록으로 보기가 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-138">When a registry key contains fewer than five entries, by default it is displayed in a table, but it is often easier to view in a list.</span></span>

<span data-ttu-id="c1c30-139">두 번째 명령은 동일한 명령을 사용 `Get-ItemProperty` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-139">The second command uses the same `Get-ItemProperty` command.</span></span>
<span data-ttu-id="c1c30-140">그러나이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 명령의 결과를 cmdlet으로 보냅니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="c1c30-140">However, this time, the command uses a pipeline operator (`|`) to send the results of the command to the `Format-List` cmdlet.</span></span>
<span data-ttu-id="c1c30-141">이 `Format-List` 명령은 ' \* ' (모두) 값으로 Property 매개 변수를 사용 하 여 목록에 있는 개체의 모든 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-141">The `Format-List` command uses the Property parameter with a value of '\*' (all) to display all of the properties of the objects in a list.</span></span>
<span data-ttu-id="c1c30-142">결과는 다음과 같은 샘플 출력에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-142">The results are shown in the following sample output.</span></span>

<span data-ttu-id="c1c30-143">결과 표시에는 "Path" 및 "Set-executionpolicy" 레지스트리 항목이 표시 되 고, 레지스트리 키 개체의 몇 가지 less 속성과 함께 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-143">The resulting display shows the "Path" and "ExecutionPolicy" registry entries, along with several less familiar properties of the registry key object.</span></span>
<span data-ttu-id="c1c30-144">PS와 접두사로 시작 하는 다른 속성은 레지스트리 키를 나타내는 개체와 같은 PowerShell 사용자 지정 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-144">The other properties, prefixed with PS, are properties of PowerShell custom objects, such as the objects that represent the registry keys.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell
```

```output
Path                                                        ExecutionPolicy
----                                                        ---------------
C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe   RemoteSigned
```

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell | Format-List -Property *
```

```output
PSPath          : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds\Micro
soft.PowerShell
PSParentPath    : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds
PSChildName     : Microsoft.PowerShell
PSDrive         : HKLM
PSProvider      : Microsoft.PowerShell.Core\Registry
Path            : C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe
ExecutionPolicy : RemoteSigned
```

## <span data-ttu-id="c1c30-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c1c30-145">PARAMETERS</span></span>

### <span data-ttu-id="c1c30-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="c1c30-146">-Credential</span></span>

<span data-ttu-id="c1c30-147">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-147">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="c1c30-148">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-148">The default is the current user.</span></span>

<span data-ttu-id="c1c30-149">"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="c1c30-149">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="c1c30-150">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-150">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="c1c30-151">이 매개 변수는 Windows PowerShell과 함께 설치된 모든 공급자에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-151">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

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

### <span data-ttu-id="c1c30-152">-제외</span><span class="sxs-lookup"><span data-stu-id="c1c30-152">-Exclude</span></span>

<span data-ttu-id="c1c30-153">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-153">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="c1c30-154">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-154">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="c1c30-155">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-155">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="c1c30-156">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-156">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="c1c30-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="c1c30-157">-Filter</span></span>

<span data-ttu-id="c1c30-158">공급자의 형식 또는 언어로 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-158">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="c1c30-159">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-159">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="c1c30-160">와일드 카드 문자를 포함 한 필터 구문은 공급자에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-160">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="c1c30-161">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-161">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="c1c30-162">-포함</span><span class="sxs-lookup"><span data-stu-id="c1c30-162">-Include</span></span>

<span data-ttu-id="c1c30-163">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-163">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="c1c30-164">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-164">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="c1c30-165">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-165">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="c1c30-166">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-166">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="c1c30-167">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c1c30-167">-LiteralPath</span></span>

<span data-ttu-id="c1c30-168">속성의 현재 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-168">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="c1c30-169">**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-169">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="c1c30-170">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-170">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="c1c30-171">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="c1c30-171">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="c1c30-172">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-172">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="c1c30-173">-Name</span><span class="sxs-lookup"><span data-stu-id="c1c30-173">-Name</span></span>

<span data-ttu-id="c1c30-174">검색할 속성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-174">Specifies the name of the property or properties to retrieve.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1c30-175">-Path</span><span class="sxs-lookup"><span data-stu-id="c1c30-175">-Path</span></span>

<span data-ttu-id="c1c30-176">항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-176">Specifies the path to the item or items.</span></span>

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

### <span data-ttu-id="c1c30-177">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="c1c30-177">-UseTransaction</span></span>

<span data-ttu-id="c1c30-178">활성 트랜잭션에 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-178">Includes the command in the active transaction.</span></span>
<span data-ttu-id="c1c30-179">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-179">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="c1c30-180">자세한 내용은 활성 트랜잭션에 명령 포함을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c1c30-180">For more information, see Includes the command in the active transaction.</span></span>
<span data-ttu-id="c1c30-181">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-181">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="c1c30-182">자세한 내용은 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1c30-182">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="c1c30-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c1c30-183">CommonParameters</span></span>

<span data-ttu-id="c1c30-184">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-184">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="c1c30-185">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1c30-185">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c1c30-186">입력</span><span class="sxs-lookup"><span data-stu-id="c1c30-186">INPUTS</span></span>

### <span data-ttu-id="c1c30-187">System.String</span><span class="sxs-lookup"><span data-stu-id="c1c30-187">System.String</span></span>

<span data-ttu-id="c1c30-188">경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="c1c30-188">You can pipe a string that contains a path to `Get-ItemProperty`.</span></span>

## <span data-ttu-id="c1c30-189">출력</span><span class="sxs-lookup"><span data-stu-id="c1c30-189">OUTPUTS</span></span>

### <span data-ttu-id="c1c30-190">System.string, System.string, System.web</span><span class="sxs-lookup"><span data-stu-id="c1c30-190">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="c1c30-191">`Get-ItemProperty` 가져오는 각 항목 속성에 대 한 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-191">`Get-ItemProperty` returns an object for each item property that it gets.</span></span>
<span data-ttu-id="c1c30-192">개체 유형은 검색된 개체에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-192">The object type depends on the object that is retrieved.</span></span>
<span data-ttu-id="c1c30-193">예를 들어 파일 시스템 드라이브에서는 파일 또는 폴더가 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-193">For example, in a file system drive, it might return a file or folder.</span></span>

## <span data-ttu-id="c1c30-194">참고</span><span class="sxs-lookup"><span data-stu-id="c1c30-194">NOTES</span></span>

<span data-ttu-id="c1c30-195">`Get-ItemProperty`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-195">The `Get-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="c1c30-196">세션에서 사용할 수 있는 공급자를 나열 하려면 ""을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1c30-196">To list the providers available in your session, type "`Get-PSProvider`".</span></span> <span data-ttu-id="c1c30-197">자세한 내용은 About_Providers를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1c30-197">For more information, see about_Providers.</span></span>

## <span data-ttu-id="c1c30-198">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c1c30-198">RELATED LINKS</span></span>

[<span data-ttu-id="c1c30-199">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c1c30-199">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="c1c30-200">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c1c30-200">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="c1c30-201">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c1c30-201">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="c1c30-202">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c1c30-202">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="c1c30-203">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c1c30-203">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="c1c30-204">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c1c30-204">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="c1c30-205">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c1c30-205">Set-ItemProperty</span></span>](Set-ItemProperty.md)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 67d9f351b8ef4936dcb4e9cff6583da0f464bc12
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2020
ms.locfileid: "99600843"
---
# <span data-ttu-id="54cc1-102">Get-Item</span><span class="sxs-lookup"><span data-stu-id="54cc1-102">Get-Item</span></span>

## <span data-ttu-id="54cc1-103">개요</span><span class="sxs-lookup"><span data-stu-id="54cc1-103">SYNOPSIS</span></span>
<span data-ttu-id="54cc1-104">지정된 위치에 있는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-104">Gets the item at the specified location.</span></span>

## <span data-ttu-id="54cc1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="54cc1-105">SYNTAX</span></span>

### <span data-ttu-id="54cc1-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="54cc1-106">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="54cc1-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="54cc1-107">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="54cc1-108">설명</span><span class="sxs-lookup"><span data-stu-id="54cc1-108">DESCRIPTION</span></span>

<span data-ttu-id="54cc1-109">`Get-Item`Cmdlet은 지정 된 위치에 있는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-109">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="54cc1-110">와일드 카드 문자 ()를 사용 하 여 `*` 항목의 모든 내용을 요청 하지 않는 한 해당 위치에 있는 항목의 내용을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-110">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="54cc1-111">이 cmdlet은 PowerShell 공급자가 여러 유형의 데이터 저장소를 탐색 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-111">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="54cc1-112">예제</span><span class="sxs-lookup"><span data-stu-id="54cc1-112">EXAMPLES</span></span>

### <span data-ttu-id="54cc1-113">예 1: 현재 디렉터리 가져오기</span><span class="sxs-lookup"><span data-stu-id="54cc1-113">Example 1: Get the current directory</span></span>

<span data-ttu-id="54cc1-114">이 예제에서는 현재 디렉터리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-114">This example gets the current directory.</span></span> <span data-ttu-id="54cc1-115">점 ('. ')은 현재 위치에 있는 항목 (내용 아님)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-115">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="54cc1-116">예 2: 현재 디렉터리에 있는 모든 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="54cc1-116">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="54cc1-117">이 예제에서는 현재 디렉터리에 있는 모든 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-117">This example gets all the items in the current directory.</span></span> <span data-ttu-id="54cc1-118">와일드 카드 문자 ( `*` )는 현재 항목의 모든 내용을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-118">The wildcard character (`*`) represents all the contents of the current item.</span></span>

```powershell
Get-Item *
```

```output
Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006   9:29 AM            Logs
d----         7/26/2006   9:26 AM            Recs
-a---         7/26/2006   9:28 AM         80 date.csv
-a---         7/26/2006  10:01 AM         30 filenoext
-a---         7/26/2006   9:30 AM      11472 process.doc
-a---         7/14/2006  10:47 AM         30 test.txt
```

### <span data-ttu-id="54cc1-119">예 3: 드라이브의 현재 디렉터리 가져오기</span><span class="sxs-lookup"><span data-stu-id="54cc1-119">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="54cc1-120">이 예제에서는 드라이브의 현재 디렉터리를 가져옵니다 `C:` .</span><span class="sxs-lookup"><span data-stu-id="54cc1-120">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="54cc1-121">검색할 대상 개체는 디렉터리(디렉터리의 내용이 아님)만 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-121">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:\
```

### <span data-ttu-id="54cc1-122">예제 4: 지정 된 드라이브에서 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="54cc1-122">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="54cc1-123">이 예제에서는 드라이브의 항목을 가져옵니다 `C:` .</span><span class="sxs-lookup"><span data-stu-id="54cc1-123">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="54cc1-124">와일드 카드 문자 ( `*` )는 컨테이너 뿐만 아니라 컨테이너의 모든 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-124">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="54cc1-125">PowerShell에서 일반적인 대신 단일 별표 ()를 사용 `*` 하 여 콘텐츠를 가져옵니다 `*.*` .</span><span class="sxs-lookup"><span data-stu-id="54cc1-125">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="54cc1-126">형식은 문자 그대로 해석 되므로 `*.*` 점이 없는 디렉터리나 파일 이름을 검색 하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-126">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="54cc1-127">예 5: 지정 된 디렉터리에서 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="54cc1-127">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="54cc1-128">이 예에서는 디렉터리의 **LastAccessTime** 속성을 가져옵니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="54cc1-128">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="54cc1-129">**LastAccessTime** 은 파일 시스템 디렉터리의 속성 중 하나에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-129">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="54cc1-130">디렉터리의 모든 속성을 보려면를 입력 `(Get-Item <directory-name>) | Get-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-130">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="54cc1-131">예제 6: 레지스트리 키 내용 표시</span><span class="sxs-lookup"><span data-stu-id="54cc1-131">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="54cc1-132">이 예제에서는 **Microsoft PowerShell** 레지스트리 키의 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-132">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="54cc1-133">PowerShell 레지스트리 공급자와 함께이 cmdlet을 사용 하 여 레지스트리 키와 하위 키를 가져올 수 있지만 cmdlet을 사용 `Get-ItemProperty` 하 여 레지스트리 값과 데이터를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-133">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="54cc1-134">예제 7: 제외 된 디렉터리의 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="54cc1-134">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="54cc1-135">이 예제에서는 Windows 디렉터리에서 점 ()이 포함 된 항목 `.` 을 가져오지만로 시작 하지 않는 항목을 가져옵니다 `w*` . 이 예제는 경로에 `*` 항목의 내용을 지정 하는 와일드 카드 문자 ()가 포함 된 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-135">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### <span data-ttu-id="54cc1-136">예 8: hardlink create 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="54cc1-136">Example 8: Getting hardlink information</span></span>

<span data-ttu-id="54cc1-137">PowerShell 6.2에서 hardlink create 정보를 가져오기 위해 대체 뷰가 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-137">In PowerShell 6.2, an alternate view was added to get hardlink information.</span></span> <span data-ttu-id="54cc1-138">Hardlink create 정보를 가져오려면 출력을로 파이프 합니다. `Format-Table -View childrenWithHardlink`</span><span class="sxs-lookup"><span data-stu-id="54cc1-138">To get the hardlink information, pipe the output to `Format-Table -View childrenWithHardlink`</span></span>

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### <span data-ttu-id="54cc1-139">예 9: Windows 이외의 운영 체제에 대 한 출력</span><span class="sxs-lookup"><span data-stu-id="54cc1-139">Example 9: Output for Non-Windows Operating Systems</span></span>

<span data-ttu-id="54cc1-140">Unix 시스템의 PowerShell 7.1에서 cmdlet은 `Get-Item` unix와 비슷한 출력을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-140">In PowerShell 7.1 on Unix systems, the `Get-Item` cmdlet provides Unix-like output:</span></span>

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

<span data-ttu-id="54cc1-141">이제 출력의 일부인 새 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-141">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="54cc1-142">모든 수 **x 모드** 는 Unix 시스템에 표시 되는 파일 사용 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-142">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="54cc1-143">**사용자** 가 파일 소유자입니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-143">**User** is the file owner</span></span>
- <span data-ttu-id="54cc1-144">**그룹이 그룹 소유자입니다.**</span><span class="sxs-lookup"><span data-stu-id="54cc1-144">**Group** is the group owner</span></span>
- <span data-ttu-id="54cc1-145">**크기** 는 Unix 시스템에 표시 되는 파일 또는 디렉터리의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-145">**Size** is the size of the file or directory as represented on a Unix system</span></span>

> [!NOTE]
> <span data-ttu-id="54cc1-146">이 기능은 PowerShell 7.1의 실험적에서 일반으로 이동 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-146">This feature was moved from experimental to mainstream in PowerShell 7.1.</span></span>

## <span data-ttu-id="54cc1-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="54cc1-147">PARAMETERS</span></span>

### <span data-ttu-id="54cc1-148">-스트림</span><span class="sxs-lookup"><span data-stu-id="54cc1-148">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="54cc1-149">이 매개 변수는 Windows 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-149">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="54cc1-150">파일에서 지정한 대체 데이터 스트림을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-150">Gets the specified alternative data stream from the file.</span></span> <span data-ttu-id="54cc1-151">스트림 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-151">Enter the stream name.</span></span> <span data-ttu-id="54cc1-152">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-152">Wildcards are supported.</span></span> <span data-ttu-id="54cc1-153">모든 스트림을 가져오려면 별표 ()를 사용 `*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-153">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="54cc1-154">이 매개 변수는 디렉터리에 사용할 수 있지만 기본적으로 디렉터리에는 데이터 스트림이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-154">This parameter is valid on directories, but note that directories do not have data streams by default.</span></span>

<span data-ttu-id="54cc1-155">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-155">This parameter was introduced in PowerShell 3.0.</span></span>  <span data-ttu-id="54cc1-156">PowerShell 7.2 `Get-Item` 부터는 디렉터리 및 파일에서 대체 데이터 스트림을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-156">As of PowerShell 7.2, `Get-Item` can get alternative data streams from directories as well as files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No alternate file streams
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="54cc1-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="54cc1-157">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="54cc1-158">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-158">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="54cc1-159">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-159">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="54cc1-160">-제외</span><span class="sxs-lookup"><span data-stu-id="54cc1-160">-Exclude</span></span>

<span data-ttu-id="54cc1-161">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-161">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="54cc1-162">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-162">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="54cc1-163">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-163">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="54cc1-164">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-164">Wildcard characters are permitted.</span></span> <span data-ttu-id="54cc1-165">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="54cc1-165">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="54cc1-166">-Filter</span><span class="sxs-lookup"><span data-stu-id="54cc1-166">-Filter</span></span>

<span data-ttu-id="54cc1-167">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-167">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="54cc1-168">[파일 시스템](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터를 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-168">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="54cc1-169">필터는 다른 매개 변수 보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-169">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="54cc1-170">공급자는 검색 된 개체를 PowerShell에서 필터링 하는 대신 개체를 가져올 때 필터를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-170">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="54cc1-171">필터 문자열은 파일을 열거 하기 위해 .NET API에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-171">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="54cc1-172">API는 `*` 및 `?` 와일드 카드만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-172">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="54cc1-173">-Force</span><span class="sxs-lookup"><span data-stu-id="54cc1-173">-Force</span></span>

<span data-ttu-id="54cc1-174">이 cmdlet은 숨겨진 항목과 같이 다른 방법으로는 액세스할 수 없는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-174">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="54cc1-175">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-175">Implementation varies from provider to provider.</span></span> <span data-ttu-id="54cc1-176">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54cc1-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="54cc1-177">**Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-177">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="54cc1-178">-포함</span><span class="sxs-lookup"><span data-stu-id="54cc1-178">-Include</span></span>

<span data-ttu-id="54cc1-179">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-179">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="54cc1-180">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-180">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="54cc1-181">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-181">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="54cc1-182">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-182">Wildcard characters are permitted.</span></span> <span data-ttu-id="54cc1-183">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="54cc1-183">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="54cc1-184">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="54cc1-184">-LiteralPath</span></span>

<span data-ttu-id="54cc1-185">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-185">Specifies a path to one or more locations.</span></span> <span data-ttu-id="54cc1-186">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-186">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="54cc1-187">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-187">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="54cc1-188">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="54cc1-188">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="54cc1-189">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-189">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="54cc1-190">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54cc1-190">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="54cc1-191">-Path</span><span class="sxs-lookup"><span data-stu-id="54cc1-191">-Path</span></span>

<span data-ttu-id="54cc1-192">항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-192">Specifies the path to an item.</span></span> <span data-ttu-id="54cc1-193">이 cmdlet은 지정 된 위치에 있는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-193">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="54cc1-194">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="54cc1-195">이 매개 변수는 필수 이지만 매개 변수 이름 **경로** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-195">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="54cc1-196">점 ()을 사용 `.` 하 여 현재 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-196">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="54cc1-197">와일드 카드 문자 ( `*` )를 사용 하 여 현재 위치의 모든 항목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-197">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="54cc1-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="54cc1-198">CommonParameters</span></span>

<span data-ttu-id="54cc1-199">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="54cc1-199">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="54cc1-200">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54cc1-200">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="54cc1-201">입력</span><span class="sxs-lookup"><span data-stu-id="54cc1-201">INPUTS</span></span>

### <span data-ttu-id="54cc1-202">System.String</span><span class="sxs-lookup"><span data-stu-id="54cc1-202">System.String</span></span>

<span data-ttu-id="54cc1-203">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-203">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="54cc1-204">출력</span><span class="sxs-lookup"><span data-stu-id="54cc1-204">OUTPUTS</span></span>

### <span data-ttu-id="54cc1-205">System.Object</span><span class="sxs-lookup"><span data-stu-id="54cc1-205">System.Object</span></span>

<span data-ttu-id="54cc1-206">이 cmdlet은 가져오는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-206">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="54cc1-207">경로의 개체 유형에 따라 유형이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-207">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="54cc1-208">참고</span><span class="sxs-lookup"><span data-stu-id="54cc1-208">NOTES</span></span>

<span data-ttu-id="54cc1-209">이 cmdlet은 해당 내용이 아닌 항목만 가져오기 때문에 **재귀** 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-209">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="54cc1-210">항목의 내용을 재귀적으로 가져오려면를 사용 `Get-ChildItem` 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-210">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="54cc1-211">레지스트리를 탐색 하려면이 cmdlet을 사용 하 여 레지스트리 키와 `Get-ItemProperty` 레지스트리 값 및 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-211">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="54cc1-212">레지스트리 값은 레지스트리 키의 속성으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-212">The registry values are considered to be properties of the registry key.</span></span>

<span data-ttu-id="54cc1-213">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-213">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="54cc1-214">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc1-214">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="54cc1-215">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54cc1-215">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="54cc1-216">관련 링크</span><span class="sxs-lookup"><span data-stu-id="54cc1-216">RELATED LINKS</span></span>

[<span data-ttu-id="54cc1-217">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="54cc1-217">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="54cc1-218">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="54cc1-218">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="54cc1-219">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="54cc1-219">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="54cc1-220">Move-Item</span><span class="sxs-lookup"><span data-stu-id="54cc1-220">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="54cc1-221">New-Item</span><span class="sxs-lookup"><span data-stu-id="54cc1-221">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="54cc1-222">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="54cc1-222">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="54cc1-223">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="54cc1-223">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="54cc1-224">Set-Item</span><span class="sxs-lookup"><span data-stu-id="54cc1-224">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="54cc1-225">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="54cc1-225">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="54cc1-226">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="54cc1-226">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="54cc1-227">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="54cc1-227">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="54cc1-228">about_Providers</span><span class="sxs-lookup"><span data-stu-id="54cc1-228">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

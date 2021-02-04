---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: d034baf42f064149696f54a198dc97d7ee4e8fe7
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97693080"
---
# <span data-ttu-id="320e0-103">Get-Item</span><span class="sxs-lookup"><span data-stu-id="320e0-103">Get-Item</span></span>

## <span data-ttu-id="320e0-104">개요</span><span class="sxs-lookup"><span data-stu-id="320e0-104">SYNOPSIS</span></span>
<span data-ttu-id="320e0-105">지정된 위치에 있는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-105">Gets the item at the specified location.</span></span>

## <span data-ttu-id="320e0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="320e0-106">SYNTAX</span></span>

### <span data-ttu-id="320e0-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="320e0-107">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="320e0-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="320e0-108">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="320e0-109">설명</span><span class="sxs-lookup"><span data-stu-id="320e0-109">DESCRIPTION</span></span>

<span data-ttu-id="320e0-110">`Get-Item`Cmdlet은 지정 된 위치에 있는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-110">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="320e0-111">와일드 카드 문자 ()를 사용 하 여 `*` 항목의 모든 내용을 요청 하지 않는 한 해당 위치에 있는 항목의 내용을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-111">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="320e0-112">이 cmdlet은 PowerShell 공급자가 여러 유형의 데이터 저장소를 탐색 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-112">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="320e0-113">예제</span><span class="sxs-lookup"><span data-stu-id="320e0-113">EXAMPLES</span></span>

### <span data-ttu-id="320e0-114">예 1: 현재 디렉터리 가져오기</span><span class="sxs-lookup"><span data-stu-id="320e0-114">Example 1: Get the current directory</span></span>

<span data-ttu-id="320e0-115">이 예제에서는 현재 디렉터리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-115">This example gets the current directory.</span></span> <span data-ttu-id="320e0-116">점 ('. ')은 현재 위치에 있는 항목 (내용 아님)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-116">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="320e0-117">예 2: 현재 디렉터리에 있는 모든 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="320e0-117">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="320e0-118">이 예제에서는 현재 디렉터리에 있는 모든 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-118">This example gets all the items in the current directory.</span></span> <span data-ttu-id="320e0-119">와일드 카드 문자 ( `*` )는 현재 항목의 모든 내용을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-119">The wildcard character (`*`) represents all the contents of the current item.</span></span>

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

### <span data-ttu-id="320e0-120">예 3: 드라이브의 현재 디렉터리 가져오기</span><span class="sxs-lookup"><span data-stu-id="320e0-120">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="320e0-121">이 예제에서는 드라이브의 현재 디렉터리를 가져옵니다 `C:` .</span><span class="sxs-lookup"><span data-stu-id="320e0-121">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="320e0-122">검색할 대상 개체는 디렉터리(디렉터리의 내용이 아님)만 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-122">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:\
```

### <span data-ttu-id="320e0-123">예제 4: 지정 된 드라이브에서 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="320e0-123">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="320e0-124">이 예제에서는 드라이브의 항목을 가져옵니다 `C:` .</span><span class="sxs-lookup"><span data-stu-id="320e0-124">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="320e0-125">와일드 카드 문자 ( `*` )는 컨테이너 뿐만 아니라 컨테이너의 모든 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-125">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="320e0-126">PowerShell에서 일반적인 대신 단일 별표 ()를 사용 `*` 하 여 콘텐츠를 가져옵니다 `*.*` .</span><span class="sxs-lookup"><span data-stu-id="320e0-126">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="320e0-127">형식은 문자 그대로 해석 되므로 `*.*` 점이 없는 디렉터리나 파일 이름을 검색 하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-127">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="320e0-128">예 5: 지정 된 디렉터리에서 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="320e0-128">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="320e0-129">이 예에서는 디렉터리의 **LastAccessTime** 속성을 가져옵니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="320e0-129">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="320e0-130">**LastAccessTime** 은 파일 시스템 디렉터리의 속성 중 하나에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-130">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="320e0-131">디렉터리의 모든 속성을 보려면를 입력 `(Get-Item <directory-name>) | Get-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-131">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="320e0-132">예제 6: 레지스트리 키 내용 표시</span><span class="sxs-lookup"><span data-stu-id="320e0-132">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="320e0-133">이 예제에서는 **Microsoft PowerShell** 레지스트리 키의 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-133">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="320e0-134">PowerShell 레지스트리 공급자와 함께이 cmdlet을 사용 하 여 레지스트리 키와 하위 키를 가져올 수 있지만 cmdlet을 사용 `Get-ItemProperty` 하 여 레지스트리 값과 데이터를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-134">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="320e0-135">예제 7: 제외 된 디렉터리의 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="320e0-135">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="320e0-136">이 예제에서는 Windows 디렉터리에서 점 ()이 포함 된 항목 `.` 을 가져오지만로 시작 하지 않는 항목을 가져옵니다 `w*` . 이 예제는 경로에 `*` 항목의 내용을 지정 하는 와일드 카드 문자 ()가 포함 된 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-136">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### <span data-ttu-id="320e0-137">예 8: hardlink create 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="320e0-137">Example 8: Getting hardlink information</span></span>

<span data-ttu-id="320e0-138">PowerShell 6.2에서 hardlink create 정보를 가져오기 위해 대체 뷰가 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-138">In PowerShell 6.2, an alternate view was added to get hardlink information.</span></span> <span data-ttu-id="320e0-139">Hardlink create 정보를 가져오려면 출력을로 파이프 합니다. `Format-Table -View childrenWithHardlink`</span><span class="sxs-lookup"><span data-stu-id="320e0-139">To get the hardlink information, pipe the output to `Format-Table -View childrenWithHardlink`</span></span>

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### <span data-ttu-id="320e0-140">예 9: Windows 이외의 운영 체제에 대 한 출력</span><span class="sxs-lookup"><span data-stu-id="320e0-140">Example 9: Output for Non-Windows Operating Systems</span></span>

<span data-ttu-id="320e0-141">Unix 시스템의 PowerShell 7.1에서 cmdlet은 `Get-Item` unix와 비슷한 출력을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-141">In PowerShell 7.1 on Unix systems, the `Get-Item` cmdlet provides Unix-like output:</span></span>

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

<span data-ttu-id="320e0-142">이제 출력의 일부인 새 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-142">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="320e0-143">모든 수 **x 모드** 는 Unix 시스템에 표시 되는 파일 사용 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-143">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="320e0-144">**사용자** 가 파일 소유자입니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-144">**User** is the file owner</span></span>
- <span data-ttu-id="320e0-145">**그룹이 그룹 소유자입니다.**</span><span class="sxs-lookup"><span data-stu-id="320e0-145">**Group** is the group owner</span></span>
- <span data-ttu-id="320e0-146">**크기** 는 Unix 시스템에 표시 되는 파일 또는 디렉터리의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-146">**Size** is the size of the file or directory as represented on a Unix system</span></span>

> [!NOTE]
> <span data-ttu-id="320e0-147">이 기능은 PowerShell 7.1의 실험적에서 일반으로 이동 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-147">This feature was moved from experimental to mainstream in PowerShell 7.1.</span></span>

## <span data-ttu-id="320e0-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="320e0-148">PARAMETERS</span></span>

### <span data-ttu-id="320e0-149">-스트림</span><span class="sxs-lookup"><span data-stu-id="320e0-149">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="320e0-150">이 매개 변수는 Windows 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-150">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="320e0-151">파일에서 지정된 대체 NTFS 파일 스트림을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-151">Gets the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="320e0-152">스트림 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-152">Enter the stream name.</span></span> <span data-ttu-id="320e0-153">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-153">Wildcards are supported.</span></span> <span data-ttu-id="320e0-154">모든 스트림을 가져오려면 별표 ()를 사용 `*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-154">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="320e0-155">이 매개 변수는 폴더에서 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-155">This parameter isn't valid on folders.</span></span>

<span data-ttu-id="320e0-156">**스트림은** **파일 시스템** 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="320e0-156">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Item` cmdlet.</span></span>
<span data-ttu-id="320e0-157">이 매개 변수는 파일 시스템 드라이브에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-157">This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="320e0-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="320e0-158">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="320e0-159">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-159">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="320e0-160">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-160">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="320e0-161">-제외</span><span class="sxs-lookup"><span data-stu-id="320e0-161">-Exclude</span></span>

<span data-ttu-id="320e0-162">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-162">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="320e0-163">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-163">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="320e0-164">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-164">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="320e0-165">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-165">Wildcard characters are permitted.</span></span> <span data-ttu-id="320e0-166">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="320e0-166">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="320e0-167">-Filter</span><span class="sxs-lookup"><span data-stu-id="320e0-167">-Filter</span></span>

<span data-ttu-id="320e0-168">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-168">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="320e0-169">[파일 시스템](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터를 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-169">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="320e0-170">필터는 다른 매개 변수 보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-170">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="320e0-171">공급자는 검색 된 개체를 PowerShell에서 필터링 하는 대신 개체를 가져올 때 필터를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-171">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="320e0-172">필터 문자열은 파일을 열거 하기 위해 .NET API에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-172">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="320e0-173">API는 `*` 및 `?` 와일드 카드만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-173">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="320e0-174">-Force</span><span class="sxs-lookup"><span data-stu-id="320e0-174">-Force</span></span>

<span data-ttu-id="320e0-175">이 cmdlet은 숨겨진 항목과 같이 다른 방법으로는 액세스할 수 없는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-175">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="320e0-176">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-176">Implementation varies from provider to provider.</span></span> <span data-ttu-id="320e0-177">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="320e0-177">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="320e0-178">**Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-178">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="320e0-179">-포함</span><span class="sxs-lookup"><span data-stu-id="320e0-179">-Include</span></span>

<span data-ttu-id="320e0-180">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-180">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="320e0-181">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-181">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="320e0-182">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-182">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="320e0-183">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-183">Wildcard characters are permitted.</span></span> <span data-ttu-id="320e0-184">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="320e0-184">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="320e0-185">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="320e0-185">-LiteralPath</span></span>

<span data-ttu-id="320e0-186">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-186">Specifies a path to one or more locations.</span></span> <span data-ttu-id="320e0-187">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-187">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="320e0-188">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-188">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="320e0-189">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="320e0-189">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="320e0-190">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-190">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="320e0-191">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="320e0-191">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="320e0-192">-Path</span><span class="sxs-lookup"><span data-stu-id="320e0-192">-Path</span></span>

<span data-ttu-id="320e0-193">항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-193">Specifies the path to an item.</span></span> <span data-ttu-id="320e0-194">이 cmdlet은 지정 된 위치에 있는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-194">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="320e0-195">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-195">Wildcard characters are permitted.</span></span> <span data-ttu-id="320e0-196">이 매개 변수는 필수 이지만 매개 변수 이름 **경로** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-196">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="320e0-197">점 ()을 사용 `.` 하 여 현재 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-197">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="320e0-198">와일드 카드 문자 ( `*` )를 사용 하 여 현재 위치의 모든 항목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-198">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="320e0-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="320e0-199">CommonParameters</span></span>

<span data-ttu-id="320e0-200">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-200">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="320e0-201">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="320e0-201">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="320e0-202">입력</span><span class="sxs-lookup"><span data-stu-id="320e0-202">INPUTS</span></span>

### <span data-ttu-id="320e0-203">System.String</span><span class="sxs-lookup"><span data-stu-id="320e0-203">System.String</span></span>

<span data-ttu-id="320e0-204">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-204">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="320e0-205">출력</span><span class="sxs-lookup"><span data-stu-id="320e0-205">OUTPUTS</span></span>

### <span data-ttu-id="320e0-206">System.Object</span><span class="sxs-lookup"><span data-stu-id="320e0-206">System.Object</span></span>

<span data-ttu-id="320e0-207">이 cmdlet은 가져오는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-207">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="320e0-208">경로의 개체 유형에 따라 유형이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-208">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="320e0-209">참고</span><span class="sxs-lookup"><span data-stu-id="320e0-209">NOTES</span></span>

<span data-ttu-id="320e0-210">이 cmdlet은 해당 내용이 아닌 항목만 가져오기 때문에 **재귀** 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-210">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="320e0-211">항목의 내용을 재귀적으로 가져오려면를 사용 `Get-ChildItem` 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-211">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="320e0-212">레지스트리를 탐색 하려면이 cmdlet을 사용 하 여 레지스트리 키와 `Get-ItemProperty` 레지스트리 값 및 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-212">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="320e0-213">레지스트리 값은 레지스트리 키의 속성으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-213">The registry values are considered to be properties of the registry key.</span></span>

<span data-ttu-id="320e0-214">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-214">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="320e0-215">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="320e0-215">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="320e0-216">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="320e0-216">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="320e0-217">관련 링크</span><span class="sxs-lookup"><span data-stu-id="320e0-217">RELATED LINKS</span></span>

[<span data-ttu-id="320e0-218">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="320e0-218">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="320e0-219">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="320e0-219">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="320e0-220">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="320e0-220">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="320e0-221">Move-Item</span><span class="sxs-lookup"><span data-stu-id="320e0-221">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="320e0-222">New-Item</span><span class="sxs-lookup"><span data-stu-id="320e0-222">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="320e0-223">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="320e0-223">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="320e0-224">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="320e0-224">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="320e0-225">Set-Item</span><span class="sxs-lookup"><span data-stu-id="320e0-225">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="320e0-226">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="320e0-226">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="320e0-227">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="320e0-227">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="320e0-228">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="320e0-228">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="320e0-229">about_Providers</span><span class="sxs-lookup"><span data-stu-id="320e0-229">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)


---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psdrive?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSDrive
ms.openlocfilehash: 7a37857d9a4fb9eb18869ef78dc0ac19dc26367f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215410"
---
# <span data-ttu-id="18d4a-103">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="18d4a-103">Get-PSDrive</span></span>

## <span data-ttu-id="18d4a-104">개요</span><span class="sxs-lookup"><span data-stu-id="18d4a-104">SYNOPSIS</span></span>
<span data-ttu-id="18d4a-105">현재 세션의 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-105">Gets drives in the current session.</span></span>

## <span data-ttu-id="18d4a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="18d4a-106">SYNTAX</span></span>

### <span data-ttu-id="18d4a-107">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="18d4a-107">Name (Default)</span></span>

```
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="18d4a-108">LiteralName</span><span class="sxs-lookup"><span data-stu-id="18d4a-108">LiteralName</span></span>

```
Get-PSDrive [-LiteralName] <String[]> [-Scope <String>] [-PSProvider <String[]>] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="18d4a-109">설명</span><span class="sxs-lookup"><span data-stu-id="18d4a-109">DESCRIPTION</span></span>

<span data-ttu-id="18d4a-110">`Get-PSDrive`Cmdlet은 현재 세션의 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-110">The `Get-PSDrive` cmdlet gets the drives in the current session.</span></span> <span data-ttu-id="18d4a-111">특정 드라이브를 가져오거나 세션의 모든 드라이브를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-111">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="18d4a-112">이 cmdlet은 다음과 같은 종류의 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-112">This cmdlet gets the following types of drives:</span></span>

- <span data-ttu-id="18d4a-113">네트워크 공유에 매핑된 드라이브를 포함 하는 컴퓨터의 Windows 논리 드라이브</span><span class="sxs-lookup"><span data-stu-id="18d4a-113">Windows logical drives on the computer, including drives mapped to network shares.</span></span>
- <span data-ttu-id="18d4a-114">PowerShell 공급자 (예: 인증서:, 함수: 및 별칭: 드라이브)가 노출 하는 드라이브와 Windows PowerShell 레지스트리 공급자가 노출 하는 HKLM: 및 HKCU: 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-114">Drives exposed by PowerShell providers (such as the Certificate:, Function:, and Alias: drives) and the HKLM: and HKCU: drives that are exposed by the Windows PowerShell Registry provider.</span></span>
- <span data-ttu-id="18d4a-115">New-PSDrive cmdlet을 사용 하 여 만드는 세션 지정 임시 드라이브 및 영구 매핑된 네트워크 드라이브</span><span class="sxs-lookup"><span data-stu-id="18d4a-115">Session-specified temporary drives and persistent mapped network drives that you create by using the New-PSDrive cmdlet.</span></span>

<span data-ttu-id="18d4a-116">Windows PowerShell 3.0부터 cmdlet의 **Persist** 매개 변수는 `New-PSDrive` 로컬 컴퓨터에 저장 되어 다른 세션에서 사용할 수 있는 매핑된 네트워크 드라이브를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-116">Beginning in Windows PowerShell 3.0, the **Persist** parameter of the `New-PSDrive` cmdlet can create mapped network drives that are saved on the local computer and are available in other sessions.</span></span> <span data-ttu-id="18d4a-117">자세한 내용은 PSDrive를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="18d4a-117">For more information, see New-PSDrive.</span></span>

<span data-ttu-id="18d4a-118">또한 Windows PowerShell 3.0부터는 외장형 드라이브가 컴퓨터에 연결되어 있으면 Windows PowerShell이 파일 시스템에 새 드라이브를 나타내는 PSDrive를 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-118">Also, beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, Windows PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="18d4a-119">Windows PowerShell을 다시 시작하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-119">You do not need to restart Windows PowerShell.</span></span> <span data-ttu-id="18d4a-120">마찬가지로 컴퓨터에서 외장형 드라이브의 연결이 끊기면 Windows PowerShell에서 제거된 드라이브를 나타내는 PSDrive를 자동으로 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-120">Similarly, when an external drive is disconnected from the computer, Windows PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="18d4a-121">예제</span><span class="sxs-lookup"><span data-stu-id="18d4a-121">EXAMPLES</span></span>

### <span data-ttu-id="18d4a-122">예 1: 현재 세션에서 드라이브 가져오기</span><span class="sxs-lookup"><span data-stu-id="18d4a-122">Example 1: Get drives in the current session</span></span>

```
PS C:\> Get-PSDrive

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
Alias                                  Alias
C                 202.06      23718.91 FileSystem    C:\
Cert                                   Certificate   \
D                1211.06     123642.32 FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
```

<span data-ttu-id="18d4a-123">이 명령은 현재 세션에서 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-123">This command gets the drives in the current session.</span></span>

<span data-ttu-id="18d4a-124">출력에는 하드 드라이브 (C:), CD-ROM 드라이브 (D:), Windows PowerShell 공급자가 제공 하는 드라이브 (Alias:, Cert:, Env:, Function:, HKCU:, HKLM: 및 Variable:)가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-124">The output shows the hard drive (C:), CD-ROM drive (D:), and the drives exposed by the Windows PowerShell providers (Alias:, Cert:, Env:, Function:, HKCU:, HKLM:, and Variable:).</span></span>

### <span data-ttu-id="18d4a-125">예 2: 컴퓨터에서 드라이브 가져오기</span><span class="sxs-lookup"><span data-stu-id="18d4a-125">Example 2: Get a drive on the computer</span></span>

```
PS C:\foo> Get-PSDrive D

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
D                1211.06     123642.32 FileSystem    D:\
```

<span data-ttu-id="18d4a-126">이 명령은 컴퓨터의 D: 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-126">This command gets the D: drive on the computer.</span></span> <span data-ttu-id="18d4a-127">여기서는 명령의 드라이브 문자 다음에 콜론이 붙는 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-127">Note that the drive letter in the command is not followed by a colon.</span></span>

### <span data-ttu-id="18d4a-128">예 3: Windows PowerShell 파일 시스템 공급자에서 지원 되는 모든 드라이브 가져오기</span><span class="sxs-lookup"><span data-stu-id="18d4a-128">Example 3: Get all the drives that are supported by the Windows PowerShell file system provider</span></span>

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
```

<span data-ttu-id="18d4a-129">이 명령은 Windows PowerShell 파일 시스템 공급자가 지원하는 모든 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-129">This command gets all of the drives that are supported by the Windows PowerShell FileSystem provider.</span></span> <span data-ttu-id="18d4a-130">여기에는 고정 드라이브, 논리 파티션, 매핑된 네트워크 드라이브 및 New-PSDrive cmdlet을 사용 하 여 만든 임시 드라이브가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-130">This includes fixed drives, logical partitions, mapped network drives, and temporary drives that you create by using the New-PSDrive cmdlet.</span></span>

### <span data-ttu-id="18d4a-131">예 4: 드라이브가 Windows PowerShell 드라이브 이름으로 사용 되 고 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="18d4a-131">Example 4: Check to see if a drive is in use as a Windows PowerShell drive name</span></span>

```powershell
if (Get-PSDrive X -ErrorAction SilentlyContinue) {
    Write-Host 'The X: drive is already in use.'
} else {
    New-PSDrive -Name X -PSProvider Registry -Root HKLM:\SOFTWARE
}
```

<span data-ttu-id="18d4a-132">이 명령은 Windows PowerShell 드라이브 이름으로 X 드라이브가 이미 사용되고 있는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-132">This command checks to see whether the X drive is already in use as a Windows PowerShell drive name.</span></span>
<span data-ttu-id="18d4a-133">그렇지 않은 경우이 명령은 cmdlet을 사용 하 여 `New-PSDrive` HKLM: \ SOFTWARE 레지스트리 키에 매핑되는 임시 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-133">If it is not, the command uses the `New-PSDrive` cmdlet to create a temporary drive that is mapped to the HKLM:\SOFTWARE registry key.</span></span>

### <span data-ttu-id="18d4a-134">예 5: 파일 시스템 드라이브의 형식 비교</span><span class="sxs-lookup"><span data-stu-id="18d4a-134">Example 5: Compare the types of files system drives</span></span>

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
X                                      Registry      HKLM:\Network

PS C:\> net use
New connections will be remembered.
Status       Local     Remote                    Network
-------------------------------------------------------------------------------
OK           G:        \\Server01\Public         Microsoft Windows Network

PS C:\> [System.IO.DriveInfo]::GetDrives() | Format-Table
Name DriveType DriveFormat IsReady AvailableFreeSpace TotalFreeSpace TotalSize     RootDirectory VolumeLabel
---- --------- ----------- ------- ------------------ -------------- ---------     ------------- -----------
A:\    Network               False                                                 A:\
C:\      Fixed NTFS          True  771920580608       771920580608   988877418496  C:\           Windows
D:\      Fixed NTFS          True  689684144128       689684144128   1990045179904 D:\           Big Drive
E:\      CDRom               False                                                 E:\
G:\    Network NTFS          True      69120000           69120000       104853504 G:\           GratefulDead

PS N:\> Get-CimInstance -Class Win32_LogicalDisk

DeviceID DriveType ProviderName   VolumeName         Size          FreeSpace
-------- --------- ------------   ----------         ----          ---------
A:       4
C:       3                        Windows            988877418496  771926069248
D:       3                        Big!              1990045179904  689684144128
E:       5
G:       4         \\Music\GratefulDead              988877418496  771926069248


PS C:\> Get-CimInstance -Class Win32_NetworkConnection
LocalName RemoteName            ConnectionState Status
--------- ----------            --------------- ------
G:        \\Music\GratefulDead  Connected       OK
```

<span data-ttu-id="18d4a-135">이 예제에서는에 표시 되는 파일 시스템 드라이브의 형식을 `Get-PSDrive` 다른 방법을 사용 하 여 표시 되는 형식과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-135">This example compares the types of file system drives that are displayed by `Get-PSDrive` to those displayed by using other methods.</span></span> <span data-ttu-id="18d4a-136">이 예제에서는 Windows PowerShell에서 드라이브를 표시 하는 다양 한 방법을 보여 줍니다. New-PSDrive cmdlet을 사용 하 여 만든 세션별 드라이브는 Windows PowerShell 에서만 액세스할 수 있다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-136">This example demonstrates different ways to display drives in Windows PowerShell, and it shows that session-specific drives created by using the New-PSDrive cmdlet are accessible only in Windows PowerShell.</span></span>

<span data-ttu-id="18d4a-137">첫 번째 명령은 `Get-PSDrive` 를 사용 하 여 세션의 모든 파일 시스템 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-137">The first command uses `Get-PSDrive` to get all of the file system drives in the session.</span></span> <span data-ttu-id="18d4a-138">여기에는 고정 드라이브 (C: 및 D:), 매핑된 네트워크 드라이브 (G:)가 이 매개 변수는의 **Persist** 매개 변수 `New-PSDrive` 및 PowerShell 드라이브 (T:)를 사용 하 여 `New-PSDrive` **Persist** 매개 변수 없이를 사용 하 여 만든입니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-138">This includes the fixed drives (C: and D:), a mapped network drive (G:) that was created by using the **Persist** parameter of `New-PSDrive`, and a PowerShell drive (T:) that was created by using `New-PSDrive` without the **Persist** parameter.</span></span>

<span data-ttu-id="18d4a-139">**Net use** 명령은 Windows 매핑된 네트워크 드라이브를 표시 합니다 .이 경우 G 드라이브만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-139">The **net use** command displays Windows mapped network drives, in this case it displays only the G drive.</span></span> <span data-ttu-id="18d4a-140">에서 만든 X: 드라이브는 표시 되지 않습니다 `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="18d4a-140">It does not display the X: drive that was created by `New-PSDrive`.</span></span> <span data-ttu-id="18d4a-141">G: 드라이브가 Music GratefulDead에도 매핑되어 있음을 보여 줍니다 \\ \\ \\ .</span><span class="sxs-lookup"><span data-stu-id="18d4a-141">It shows that the G: drive is also mapped to \\\\Music\\GratefulDead.</span></span>

<span data-ttu-id="18d4a-142">세 번째 명령은 Microsoft. NET Framework **System.IO.DriveInfo** 클래스의 **GetDrives** 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-142">The third command uses the **GetDrives** method of the Microsoft .NET Framework **System.IO.DriveInfo** class.</span></span> <span data-ttu-id="18d4a-143">이 명령은 드라이브 G:를 포함 하 여 Windows 파일 시스템 드라이브를 가져오지만에서 만든 드라이브는 가져오지 않습니다 `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="18d4a-143">This command gets the Windows file system drives, including drive G:, but it does not get the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="18d4a-144">네 번째 명령은 cmdlet을 사용 하 여 `Get-CimInstance` **Win32_LogicalDisk** 클래스의 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-144">The fourth command uses the `Get-CimInstance` cmdlet to get the instances of the **Win32_LogicalDisk** class.</span></span> <span data-ttu-id="18d4a-145">A:, C:, D:, E: 및 G: 드라이브를 반환 하지만에서 만든 드라이브는 반환 하지 않습니다 `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="18d4a-145">It returns the A:, C:, D:, E:, and G: drives, but not the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="18d4a-146">마지막 명령은 cmdlet을 사용 하 여 `Get-CimInstance` **Win32_NetworkConnection** 클래스의 인스턴스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-146">The last command uses the `Get-CimInstance` cmdlet to display the instances of the **Win32_NetworkConnection** class.</span></span> <span data-ttu-id="18d4a-147">**Net use** 와 마찬가지로에서 만든 영구 G: 드라이브만 반환 `New-PSDrive` 합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-147">Like **net use** , it returns only the persistent G: drive created by `New-PSDrive`.</span></span>

## <span data-ttu-id="18d4a-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="18d4a-148">PARAMETERS</span></span>

### <span data-ttu-id="18d4a-149">-LiteralName</span><span class="sxs-lookup"><span data-stu-id="18d4a-149">-LiteralName</span></span>

<span data-ttu-id="18d4a-150">드라이브의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-150">Specifies the name of the drive.</span></span>

<span data-ttu-id="18d4a-151">**LiteralName** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-151">The value of **LiteralName** is used exactly as it is typed.</span></span> <span data-ttu-id="18d4a-152">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-152">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="18d4a-153">이름에 이스케이프 문자가 포함된 경우 경로를 작은따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-153">If the name includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="18d4a-154">작은따옴표는 Windows PowerShell이 어떤 문자도 이스케이프 시퀀스로 해석하지 않도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-154">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="18d4a-155">-Name</span><span class="sxs-lookup"><span data-stu-id="18d4a-155">-Name</span></span>

<span data-ttu-id="18d4a-156">이 cmdlet이 작업에서 가져오는 드라이브의 이름 또는 이름을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-156">Specifies, as a string array, the name or name of drives that this cmdlet gets in the operation.</span></span>
<span data-ttu-id="18d4a-157">드라이브 이름이나 문자를 콜론(:) 없이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-157">Type the drive name or letter without a colon (:).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="18d4a-158">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="18d4a-158">-PSProvider</span></span>

<span data-ttu-id="18d4a-159">Windows PowerShell 공급자를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-159">Specifies, as a string array, the Windows PowerShell provider.</span></span> <span data-ttu-id="18d4a-160">이 cmdlet은이 공급자가 지 원하는 드라이브만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-160">This cmdlet gets only the drives supported by this provider.</span></span> <span data-ttu-id="18d4a-161">공급자 이름(예: FileSystem, Registry 또는 Certificate)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-161">Type the name of a provider, such as FileSystem, Registry, or Certificate.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="18d4a-162">-범위</span><span class="sxs-lookup"><span data-stu-id="18d4a-162">-Scope</span></span>

<span data-ttu-id="18d4a-163">이 cmdlet이 드라이브를 가져오는 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-163">Specifies the scope in which this cmdlet gets the drives.</span></span>

<span data-ttu-id="18d4a-164">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-164">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="18d4a-165">전역</span><span class="sxs-lookup"><span data-stu-id="18d4a-165">Global</span></span>
- <span data-ttu-id="18d4a-166">로컬</span><span class="sxs-lookup"><span data-stu-id="18d4a-166">Local</span></span>
- <span data-ttu-id="18d4a-167">스크립트</span><span class="sxs-lookup"><span data-stu-id="18d4a-167">Script</span></span>
- <span data-ttu-id="18d4a-168">현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)입니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-168">a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span> <span data-ttu-id="18d4a-169">"Local"이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-169">"Local" is the default.</span></span>

<span data-ttu-id="18d4a-170">자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="18d4a-170">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="18d4a-171">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="18d4a-171">-UseTransaction</span></span>

<span data-ttu-id="18d4a-172">활성 트랜잭션에 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-172">Includes the command in the active transaction.</span></span> <span data-ttu-id="18d4a-173">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-173">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="18d4a-174">자세한 내용은 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18d4a-174">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="18d4a-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="18d4a-175">CommonParameters</span></span>

<span data-ttu-id="18d4a-176">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="18d4a-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="18d4a-177">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18d4a-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="18d4a-178">입력</span><span class="sxs-lookup"><span data-stu-id="18d4a-178">INPUTS</span></span>

### <span data-ttu-id="18d4a-179">없음</span><span class="sxs-lookup"><span data-stu-id="18d4a-179">None</span></span>

<span data-ttu-id="18d4a-180">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-180">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="18d4a-181">출력</span><span class="sxs-lookup"><span data-stu-id="18d4a-181">OUTPUTS</span></span>

### <span data-ttu-id="18d4a-182">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="18d4a-182">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="18d4a-183">이 cmdlet은 세션의 드라이브를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-183">This cmdlet returns objects that represent the drives in the session.</span></span>

## <span data-ttu-id="18d4a-184">참고</span><span class="sxs-lookup"><span data-stu-id="18d4a-184">NOTES</span></span>

* <span data-ttu-id="18d4a-185">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-185">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="18d4a-186">세션에서 사용할 수 있는 공급자를 나열 하려면 cmdlet을 사용 합니다 `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="18d4a-186">To list the providers available in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="18d4a-187">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18d4a-187">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
* <span data-ttu-id="18d4a-188">New-PSDrive cmdlet의 **Persist** 매개 변수를 사용 하 여 만든 매핑된 네트워크 드라이브는 사용자 계정에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-188">Mapped network drives that are created by using the **Persist** parameter of the New-PSDrive cmdlet are specific to a user account.</span></span> <span data-ttu-id="18d4a-189">관리자 권한으로 실행 옵션을 사용 하거나 다른 사용자의 자격 증명을 사용 하 여 시작한 세션에서 사용자가 만든 매핑된 네트워크 드라이브는 명시적 자격 증명을 사용 하지 않거나 현재 사용자의 자격 증명을 사용 하 여 시작한 세션에서는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="18d4a-189">Mapped network drives that you create in sessions that are started with the Run as administrator option or with the credentials of another user are not visible in sessions that are started without explicit credentials or with the credentials of the current user.</span></span>

## <span data-ttu-id="18d4a-190">관련 링크</span><span class="sxs-lookup"><span data-stu-id="18d4a-190">RELATED LINKS</span></span>

[<span data-ttu-id="18d4a-191">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="18d4a-191">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="18d4a-192">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="18d4a-192">Remove-PSDrive</span></span>](Remove-PSDrive.md)

[<span data-ttu-id="18d4a-193">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="18d4a-193">Get-PSProvider</span></span>](Get-PSProvider.md)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psdrive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSDrive
ms.openlocfilehash: aa83b6318b8e3b07d17cbb3e511bc7ab4aa9a774
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599739"
---
# <span data-ttu-id="a1ca2-102">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="a1ca2-102">Get-PSDrive</span></span>

## <span data-ttu-id="a1ca2-103">개요</span><span class="sxs-lookup"><span data-stu-id="a1ca2-103">SYNOPSIS</span></span>
<span data-ttu-id="a1ca2-104">현재 세션의 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-104">Gets drives in the current session.</span></span>

## <span data-ttu-id="a1ca2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a1ca2-105">SYNTAX</span></span>

### <span data-ttu-id="a1ca2-106">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="a1ca2-106">Name (Default)</span></span>

```
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="a1ca2-107">LiteralName</span><span class="sxs-lookup"><span data-stu-id="a1ca2-107">LiteralName</span></span>

```
Get-PSDrive [-LiteralName] <String[]> [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="a1ca2-108">설명</span><span class="sxs-lookup"><span data-stu-id="a1ca2-108">DESCRIPTION</span></span>

<span data-ttu-id="a1ca2-109">`Get-PSDrive`Cmdlet은 현재 세션의 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-109">The `Get-PSDrive` cmdlet gets the drives in the current session.</span></span> <span data-ttu-id="a1ca2-110">특정 드라이브를 가져오거나 세션의 모든 드라이브를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-110">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="a1ca2-111">이 cmdlet은 다음과 같은 종류의 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-111">This cmdlet gets the following types of drives:</span></span>

- <span data-ttu-id="a1ca2-112">네트워크 공유에 매핑된 드라이브를 포함 하는 컴퓨터의 Windows 논리 드라이브</span><span class="sxs-lookup"><span data-stu-id="a1ca2-112">Windows logical drives on the computer, including drives mapped to network shares.</span></span>
- <span data-ttu-id="a1ca2-113">PowerShell 공급자 (예: 인증서:, 함수: 및 별칭: 드라이브)가 노출 하는 드라이브와 Windows PowerShell 레지스트리 공급자가 노출 하는 HKLM: 및 HKCU: 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-113">Drives exposed by PowerShell providers (such as the Certificate:, Function:, and Alias: drives) and the HKLM: and HKCU: drives that are exposed by the Windows PowerShell Registry provider.</span></span>
- <span data-ttu-id="a1ca2-114">New-PSDrive cmdlet을 사용 하 여 만드는 세션 지정 임시 드라이브 및 영구 매핑된 네트워크 드라이브</span><span class="sxs-lookup"><span data-stu-id="a1ca2-114">Session-specified temporary drives and persistent mapped network drives that you create by using the New-PSDrive cmdlet.</span></span>

<span data-ttu-id="a1ca2-115">Windows PowerShell 3.0부터 cmdlet의 **Persist** 매개 변수는 `New-PSDrive` 로컬 컴퓨터에 저장 되어 다른 세션에서 사용할 수 있는 매핑된 네트워크 드라이브를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-115">Beginning in Windows PowerShell 3.0, the **Persist** parameter of the `New-PSDrive` cmdlet can create mapped network drives that are saved on the local computer and are available in other sessions.</span></span> <span data-ttu-id="a1ca2-116">자세한 내용은 PSDrive를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-116">For more information, see New-PSDrive.</span></span>

<span data-ttu-id="a1ca2-117">또한 Windows PowerShell 3.0부터는 외장형 드라이브가 컴퓨터에 연결되어 있으면 Windows PowerShell이 파일 시스템에 새 드라이브를 나타내는 PSDrive를 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-117">Also, beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, Windows PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="a1ca2-118">Windows PowerShell을 다시 시작하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-118">You do not need to restart Windows PowerShell.</span></span> <span data-ttu-id="a1ca2-119">마찬가지로 컴퓨터에서 외장형 드라이브의 연결이 끊기면 Windows PowerShell에서 제거된 드라이브를 나타내는 PSDrive를 자동으로 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-119">Similarly, when an external drive is disconnected from the computer, Windows PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="a1ca2-120">예제</span><span class="sxs-lookup"><span data-stu-id="a1ca2-120">EXAMPLES</span></span>

### <span data-ttu-id="a1ca2-121">예 1: 현재 세션에서 드라이브 가져오기</span><span class="sxs-lookup"><span data-stu-id="a1ca2-121">Example 1: Get drives in the current session</span></span>

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

<span data-ttu-id="a1ca2-122">이 명령은 현재 세션에서 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-122">This command gets the drives in the current session.</span></span>

<span data-ttu-id="a1ca2-123">출력에는 하드 드라이브 (C:), CD-ROM 드라이브 (D:), Windows PowerShell 공급자가 제공 하는 드라이브 (Alias:, Cert:, Env:, Function:, HKCU:, HKLM: 및 Variable:)가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-123">The output shows the hard drive (C:), CD-ROM drive (D:), and the drives exposed by the Windows PowerShell providers (Alias:, Cert:, Env:, Function:, HKCU:, HKLM:, and Variable:).</span></span>

### <span data-ttu-id="a1ca2-124">예 2: 컴퓨터에서 드라이브 가져오기</span><span class="sxs-lookup"><span data-stu-id="a1ca2-124">Example 2: Get a drive on the computer</span></span>

```
PS C:\foo> Get-PSDrive D

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
D                1211.06     123642.32 FileSystem    D:\
```

<span data-ttu-id="a1ca2-125">이 명령은 컴퓨터의 D: 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-125">This command gets the D: drive on the computer.</span></span> <span data-ttu-id="a1ca2-126">여기서는 명령의 드라이브 문자 다음에 콜론이 붙는 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-126">Note that the drive letter in the command is not followed by a colon.</span></span>

### <span data-ttu-id="a1ca2-127">예 3: Windows PowerShell 파일 시스템 공급자에서 지원 되는 모든 드라이브 가져오기</span><span class="sxs-lookup"><span data-stu-id="a1ca2-127">Example 3: Get all the drives that are supported by the Windows PowerShell file system provider</span></span>

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
```

<span data-ttu-id="a1ca2-128">이 명령은 Windows PowerShell 파일 시스템 공급자가 지원하는 모든 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-128">This command gets all of the drives that are supported by the Windows PowerShell FileSystem provider.</span></span> <span data-ttu-id="a1ca2-129">여기에는 고정 드라이브, 논리 파티션, 매핑된 네트워크 드라이브 및 New-PSDrive cmdlet을 사용 하 여 만든 임시 드라이브가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-129">This includes fixed drives, logical partitions, mapped network drives, and temporary drives that you create by using the New-PSDrive cmdlet.</span></span>

### <span data-ttu-id="a1ca2-130">예 4: 드라이브가 Windows PowerShell 드라이브 이름으로 사용 되 고 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="a1ca2-130">Example 4: Check to see if a drive is in use as a Windows PowerShell drive name</span></span>

```powershell
if (Get-PSDrive X -ErrorAction SilentlyContinue) {
    Write-Host 'The X: drive is already in use.'
} else {
    New-PSDrive -Name X -PSProvider Registry -Root HKLM:\SOFTWARE
}
```

<span data-ttu-id="a1ca2-131">이 명령은 Windows PowerShell 드라이브 이름으로 X 드라이브가 이미 사용되고 있는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-131">This command checks to see whether the X drive is already in use as a Windows PowerShell drive name.</span></span>
<span data-ttu-id="a1ca2-132">그렇지 않은 경우이 명령은 cmdlet을 사용 하 여 `New-PSDrive` HKLM: \ SOFTWARE 레지스트리 키에 매핑되는 임시 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-132">If it is not, the command uses the `New-PSDrive` cmdlet to create a temporary drive that is mapped to the HKLM:\SOFTWARE registry key.</span></span>

### <span data-ttu-id="a1ca2-133">예 5: 파일 시스템 드라이브의 형식 비교</span><span class="sxs-lookup"><span data-stu-id="a1ca2-133">Example 5: Compare the types of files system drives</span></span>

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

<span data-ttu-id="a1ca2-134">이 예제에서는에 표시 되는 파일 시스템 드라이브의 형식을 `Get-PSDrive` 다른 방법을 사용 하 여 표시 되는 형식과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-134">This example compares the types of file system drives that are displayed by `Get-PSDrive` to those displayed by using other methods.</span></span> <span data-ttu-id="a1ca2-135">이 예제에서는 Windows PowerShell에서 드라이브를 표시 하는 다양 한 방법을 보여 줍니다. New-PSDrive cmdlet을 사용 하 여 만든 세션별 드라이브는 Windows PowerShell 에서만 액세스할 수 있다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-135">This example demonstrates different ways to display drives in Windows PowerShell, and it shows that session-specific drives created by using the New-PSDrive cmdlet are accessible only in Windows PowerShell.</span></span>

<span data-ttu-id="a1ca2-136">첫 번째 명령은 `Get-PSDrive` 를 사용 하 여 세션의 모든 파일 시스템 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-136">The first command uses `Get-PSDrive` to get all of the file system drives in the session.</span></span> <span data-ttu-id="a1ca2-137">여기에는 고정 드라이브 (C: 및 D:), 매핑된 네트워크 드라이브 (G:)가 이 매개 변수는의 **Persist** 매개 변수 `New-PSDrive` 및 PowerShell 드라이브 (T:)를 사용 하 여 `New-PSDrive` **Persist** 매개 변수 없이를 사용 하 여 만든입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-137">This includes the fixed drives (C: and D:), a mapped network drive (G:) that was created by using the **Persist** parameter of `New-PSDrive`, and a PowerShell drive (T:) that was created by using `New-PSDrive` without the **Persist** parameter.</span></span>

<span data-ttu-id="a1ca2-138">**Net use** 명령은 Windows 매핑된 네트워크 드라이브를 표시 합니다 .이 경우 G 드라이브만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-138">The **net use** command displays Windows mapped network drives, in this case it displays only the G drive.</span></span> <span data-ttu-id="a1ca2-139">에서 만든 X: 드라이브는 표시 되지 않습니다 `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="a1ca2-139">It does not display the X: drive that was created by `New-PSDrive`.</span></span> <span data-ttu-id="a1ca2-140">G: 드라이브가 Music GratefulDead에도 매핑되어 있음을 보여 줍니다 \\ \\ \\ .</span><span class="sxs-lookup"><span data-stu-id="a1ca2-140">It shows that the G: drive is also mapped to \\\\Music\\GratefulDead.</span></span>

<span data-ttu-id="a1ca2-141">세 번째 명령은 Microsoft. NET Framework **System.IO.DriveInfo** 클래스의 **GetDrives** 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-141">The third command uses the **GetDrives** method of the Microsoft .NET Framework **System.IO.DriveInfo** class.</span></span> <span data-ttu-id="a1ca2-142">이 명령은 드라이브 G:를 포함 하 여 Windows 파일 시스템 드라이브를 가져오지만에서 만든 드라이브는 가져오지 않습니다 `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="a1ca2-142">This command gets the Windows file system drives, including drive G:, but it does not get the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="a1ca2-143">네 번째 명령은 cmdlet을 사용 하 여 `Get-CimInstance` **Win32_LogicalDisk** 클래스의 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-143">The fourth command uses the `Get-CimInstance` cmdlet to get the instances of the **Win32_LogicalDisk** class.</span></span> <span data-ttu-id="a1ca2-144">A:, C:, D:, E: 및 G: 드라이브를 반환 하지만에서 만든 드라이브는 반환 하지 않습니다 `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="a1ca2-144">It returns the A:, C:, D:, E:, and G: drives, but not the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="a1ca2-145">마지막 명령은 cmdlet을 사용 하 여 `Get-CimInstance` **Win32_NetworkConnection** 클래스의 인스턴스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-145">The last command uses the `Get-CimInstance` cmdlet to display the instances of the **Win32_NetworkConnection** class.</span></span> <span data-ttu-id="a1ca2-146">**Net use** 와 마찬가지로에서 만든 영구 G: 드라이브만 반환 `New-PSDrive` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-146">Like **net use**, it returns only the persistent G: drive created by `New-PSDrive`.</span></span>

## <span data-ttu-id="a1ca2-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a1ca2-147">PARAMETERS</span></span>

### <span data-ttu-id="a1ca2-148">-LiteralName</span><span class="sxs-lookup"><span data-stu-id="a1ca2-148">-LiteralName</span></span>

<span data-ttu-id="a1ca2-149">드라이브의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-149">Specifies the name of the drive.</span></span>

<span data-ttu-id="a1ca2-150">**LiteralName** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-150">The value of **LiteralName** is used exactly as it is typed.</span></span> <span data-ttu-id="a1ca2-151">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-151">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a1ca2-152">이름에 이스케이프 문자가 포함된 경우 경로를 작은따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-152">If the name includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a1ca2-153">작은따옴표는 Windows PowerShell이 어떤 문자도 이스케이프 시퀀스로 해석하지 않도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-153">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="a1ca2-154">-Name</span><span class="sxs-lookup"><span data-stu-id="a1ca2-154">-Name</span></span>

<span data-ttu-id="a1ca2-155">이 cmdlet이 작업에서 가져오는 드라이브의 이름 또는 이름을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-155">Specifies, as a string array, the name or name of drives that this cmdlet gets in the operation.</span></span>
<span data-ttu-id="a1ca2-156">드라이브 이름이나 문자를 콜론(:) 없이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-156">Type the drive name or letter without a colon (:).</span></span>

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

### <span data-ttu-id="a1ca2-157">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="a1ca2-157">-PSProvider</span></span>

<span data-ttu-id="a1ca2-158">Windows PowerShell 공급자를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-158">Specifies, as a string array, the Windows PowerShell provider.</span></span> <span data-ttu-id="a1ca2-159">이 cmdlet은이 공급자가 지 원하는 드라이브만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-159">This cmdlet gets only the drives supported by this provider.</span></span> <span data-ttu-id="a1ca2-160">공급자 이름(예: FileSystem, Registry 또는 Certificate)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-160">Type the name of a provider, such as FileSystem, Registry, or Certificate.</span></span>

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

### <span data-ttu-id="a1ca2-161">-범위</span><span class="sxs-lookup"><span data-stu-id="a1ca2-161">-Scope</span></span>

<span data-ttu-id="a1ca2-162">이 cmdlet이 드라이브를 가져오는 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-162">Specifies the scope in which this cmdlet gets the drives.</span></span>

<span data-ttu-id="a1ca2-163">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-163">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a1ca2-164">전역</span><span class="sxs-lookup"><span data-stu-id="a1ca2-164">Global</span></span>
- <span data-ttu-id="a1ca2-165">로컬</span><span class="sxs-lookup"><span data-stu-id="a1ca2-165">Local</span></span>
- <span data-ttu-id="a1ca2-166">스크립트</span><span class="sxs-lookup"><span data-stu-id="a1ca2-166">Script</span></span>
- <span data-ttu-id="a1ca2-167">현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-167">a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span> <span data-ttu-id="a1ca2-168">"Local"이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-168">"Local" is the default.</span></span>

<span data-ttu-id="a1ca2-169">자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-169">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="a1ca2-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a1ca2-170">CommonParameters</span></span>

<span data-ttu-id="a1ca2-171">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a1ca2-172">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a1ca2-173">입력</span><span class="sxs-lookup"><span data-stu-id="a1ca2-173">INPUTS</span></span>

### <span data-ttu-id="a1ca2-174">없음</span><span class="sxs-lookup"><span data-stu-id="a1ca2-174">None</span></span>

<span data-ttu-id="a1ca2-175">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-175">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="a1ca2-176">출력</span><span class="sxs-lookup"><span data-stu-id="a1ca2-176">OUTPUTS</span></span>

### <span data-ttu-id="a1ca2-177">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="a1ca2-177">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="a1ca2-178">이 cmdlet은 세션의 드라이브를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-178">This cmdlet returns objects that represent the drives in the session.</span></span>

## <span data-ttu-id="a1ca2-179">참고</span><span class="sxs-lookup"><span data-stu-id="a1ca2-179">NOTES</span></span>

* <span data-ttu-id="a1ca2-180">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-180">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a1ca2-181">세션에서 사용할 수 있는 공급자를 나열 하려면 cmdlet을 사용 합니다 `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="a1ca2-181">To list the providers available in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="a1ca2-182">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-182">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
* <span data-ttu-id="a1ca2-183">New-PSDrive cmdlet의 **Persist** 매개 변수를 사용 하 여 만든 매핑된 네트워크 드라이브는 사용자 계정에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-183">Mapped network drives that are created by using the **Persist** parameter of the New-PSDrive cmdlet are specific to a user account.</span></span> <span data-ttu-id="a1ca2-184">관리자 권한으로 실행 옵션을 사용 하거나 다른 사용자의 자격 증명을 사용 하 여 시작한 세션에서 사용자가 만든 매핑된 네트워크 드라이브는 명시적 자격 증명을 사용 하지 않거나 현재 사용자의 자격 증명을 사용 하 여 시작한 세션에서는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca2-184">Mapped network drives that you create in sessions that are started with the Run as administrator option or with the credentials of another user are not visible in sessions that are started without explicit credentials or with the credentials of the current user.</span></span>

## <span data-ttu-id="a1ca2-185">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a1ca2-185">RELATED LINKS</span></span>

[<span data-ttu-id="a1ca2-186">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="a1ca2-186">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="a1ca2-187">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="a1ca2-187">Remove-PSDrive</span></span>](Remove-PSDrive.md)

[<span data-ttu-id="a1ca2-188">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="a1ca2-188">Get-PSProvider</span></span>](Get-PSProvider.md)


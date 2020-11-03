---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: 33da44a4a228b57296b85fbafb40da51657df1c1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215465"
---
# <span data-ttu-id="87cd7-103">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="87cd7-103">Get-HotFix</span></span>

## <span data-ttu-id="87cd7-104">개요</span><span class="sxs-lookup"><span data-stu-id="87cd7-104">SYNOPSIS</span></span>
<span data-ttu-id="87cd7-105">로컬 또는 원격 컴퓨터에 설치 된 핫픽스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-105">Gets the hotfixes that are installed on local or remote computers.</span></span>

## <span data-ttu-id="87cd7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="87cd7-106">SYNTAX</span></span>

### <span data-ttu-id="87cd7-107">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="87cd7-107">Default (Default)</span></span>

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### <span data-ttu-id="87cd7-108">Description</span><span class="sxs-lookup"><span data-stu-id="87cd7-108">Description</span></span>

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## <span data-ttu-id="87cd7-109">설명</span><span class="sxs-lookup"><span data-stu-id="87cd7-109">DESCRIPTION</span></span>

<span data-ttu-id="87cd7-110">`Get-Hotfix`Cmdlet은 로컬 컴퓨터 또는 지정 된 원격 컴퓨터에 설치 된 핫픽스 또는 업데이트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-110">The `Get-Hotfix` cmdlet gets hotfixes, or updates, that are installed on the local computer or specified remote computers.</span></span> <span data-ttu-id="87cd7-111">업데이트는 Windows 업데이트, Microsoft 업데이트, Windows Server Update Services 또는 수동으로 설치 하 여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-111">The updates can be installed by Windows Update, Microsoft Update, Windows Server Update Services, or manually installed.</span></span>

## <span data-ttu-id="87cd7-112">예제</span><span class="sxs-lookup"><span data-stu-id="87cd7-112">EXAMPLES</span></span>

### <span data-ttu-id="87cd7-113">예 1: 로컬 컴퓨터에서 모든 핫픽스 가져오기</span><span class="sxs-lookup"><span data-stu-id="87cd7-113">Example 1: Get all hotfixes on the local computer</span></span>

<span data-ttu-id="87cd7-114">`Get-Hotfix`Cmdlet은 로컬 컴퓨터에 설치 된 모든 핫픽스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-114">The `Get-Hotfix` cmdlet gets all hotfixes installed on the local computer.</span></span>

```powershell
Get-HotFix
```

```output
Source         Description      HotFixID      InstalledBy          InstalledOn
------         -----------      --------      -----------          -----------
Server01       Update           KB4495590     NT AUTHORITY\SYSTEM  5/16/2019 00:00:00
Server01       Security Update  KB4470788     NT AUTHORITY\SYSTEM  1/22/2019 00:00:00
Server01       Update           KB4480056     NT AUTHORITY\SYSTEM  1/24/2019 00:00:00
```

### <span data-ttu-id="87cd7-115">예제 2: 문자열로 필터링 된 여러 컴퓨터에서 핫픽스 가져오기</span><span class="sxs-lookup"><span data-stu-id="87cd7-115">Example 2: Get hotfixes from multiple computers filtered by a string</span></span>

<span data-ttu-id="87cd7-116">이 `Get-Hotfix` 명령은 매개 변수를 사용 하 여 원격 컴퓨터에 설치 된 핫픽스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-116">The `Get-Hotfix` command uses parameters to get hotfixes installed on remote computers.</span></span> <span data-ttu-id="87cd7-117">결과는 지정 된 설명 문자열을 기준으로 필터링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-117">The results are filtered by a specified description string.</span></span>

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

<span data-ttu-id="87cd7-118">`Get-Hotfix`**Description** 매개 변수 및 별표 () 와일드 카드를 포함 하는 문자열 **보안** 을 사용 하 여 출력을 필터링 합니다 `*` .</span><span class="sxs-lookup"><span data-stu-id="87cd7-118">`Get-Hotfix` filters the output with the **Description** parameter and the string **Security** that includes the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="87cd7-119">**ComputerName** 매개 변수는 쉼표로 구분 된 원격 컴퓨터 이름 문자열을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-119">The **ComputerName** parameter includes a comma-separated string of remote computer names.</span></span> <span data-ttu-id="87cd7-120">**Credential** 매개 변수는 원격 컴퓨터에 액세스할 수 있는 권한이 있는 사용자 계정을 지정 하 고 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-120">The **Credential** parameter specifies a user account that has permission to access the remote computers and run commands.</span></span>

### <span data-ttu-id="87cd7-121">예 3: 업데이트가 설치 되어 있는지 확인 하 고 파일에 컴퓨터 이름을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-121">Example 3: Verify if an update is installed and write computer names to a file</span></span>

<span data-ttu-id="87cd7-122">이 예제의 명령은 특정 업데이트가 설치 되어 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-122">The commands in this example verify whether a particular update installed.</span></span> <span data-ttu-id="87cd7-123">업데이트가 설치 되지 않은 경우 컴퓨터 이름이 텍스트 파일에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-123">If the update isn't installed, the computer name is written to a text file.</span></span>

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

<span data-ttu-id="87cd7-124">`$A`변수에는 텍스트 파일에서 가져온 컴퓨터 이름이 포함 `Get-Content` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-124">The `$A` variable contains computer names that were obtained by `Get-Content` from a text file.</span></span> <span data-ttu-id="87cd7-125">의 개체는 `$A` 파이프라인에서로 전송 됩니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="87cd7-125">The objects in `$A` are sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="87cd7-126">`if`문은 `Get-Hotfix` Cmdlet에 **id** 매개 변수와 각 컴퓨터 이름에 대 한 특정 id 번호를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-126">An `if` statement uses the `Get-Hotfix` cmdlet with the **Id** parameter and a specific Id number for each computer name.</span></span> <span data-ttu-id="87cd7-127">컴퓨터에 지정 된 핫픽스 Id가 설치 되어 있지 않은 경우 `Add-Content` cmdlet은 파일에 컴퓨터 이름을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-127">If a computer doesn't have the specified hotfix Id installed, the `Add-Content` cmdlet writes the computer name to a file.</span></span>

### <span data-ttu-id="87cd7-128">예 4: 로컬 컴퓨터에서 최신 핫픽스 가져오기</span><span class="sxs-lookup"><span data-stu-id="87cd7-128">Example 4: Get the most recent hotfix on the local computer</span></span>

<span data-ttu-id="87cd7-129">이 예제에서는 컴퓨터에 설치 된 최신 핫픽스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-129">This example gets the most recent hotfix installed on a computer.</span></span>

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

<span data-ttu-id="87cd7-130">`Get-Hotfix` 파이프라인의 개체를 cmdlet으로 보냅니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="87cd7-130">`Get-Hotfix` sends the objects down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="87cd7-131">`Sort-Object` 개체를 오름차순으로 정렬 하 고 **Property** 매개 변수를 사용 하 여 각 **설치** 날짜를 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-131">`Sort-Object` sorts objects by ascending order and uses the **Property** parameter to evaluate each **InstalledOn** date.</span></span> <span data-ttu-id="87cd7-132">배열 표기법은 `[-1]` 가장 최근에 설치 된 핫픽스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-132">The array notation `[-1]` selects the most recent installed hotfix.</span></span>

## <span data-ttu-id="87cd7-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="87cd7-133">PARAMETERS</span></span>

### <span data-ttu-id="87cd7-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="87cd7-134">-ComputerName</span></span>

<span data-ttu-id="87cd7-135">원격 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-135">Specifies a remote computer.</span></span> <span data-ttu-id="87cd7-136">원격 컴퓨터의 NetBIOS 이름, IP (인터넷 프로토콜) 주소 또는 FQDN (정규화 된 도메인 이름)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-136">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>

<span data-ttu-id="87cd7-137">**ComputerName** 매개 변수를 지정 하지 않으면가 `Get-Hotfix` 로컬 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-137">When the **ComputerName** parameter isn't specified, `Get-Hotfix` runs on the local computer.</span></span>

<span data-ttu-id="87cd7-138">**ComputerName** 매개 변수는 Windows PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-138">The **ComputerName** parameter doesn't rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="87cd7-139">컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우 **ComputerName** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-139">If your computer isn't configured to run remote commands, use the **ComputerName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __Server, IPAddress

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="87cd7-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="87cd7-140">-Credential</span></span>

<span data-ttu-id="87cd7-141">컴퓨터에 액세스할 수 있는 권한이 있는 사용자 계정을 지정 하 고 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-141">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="87cd7-142">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-142">The default is the current user</span></span>

<span data-ttu-id="87cd7-143">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="87cd7-143">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="87cd7-144">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-144">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="87cd7-145">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-145">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="87cd7-146">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="87cd7-146">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87cd7-147">-Description</span><span class="sxs-lookup"><span data-stu-id="87cd7-147">-Description</span></span>

<span data-ttu-id="87cd7-148">`Get-HotFix`**Description** 매개 변수를 사용 하 여 핫픽스 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-148">`Get-HotFix` uses the **Description** parameter to specify hotfix types.</span></span> <span data-ttu-id="87cd7-149">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-149">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Description
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="87cd7-150">-Id</span><span class="sxs-lookup"><span data-stu-id="87cd7-150">-Id</span></span>

<span data-ttu-id="87cd7-151">`Get-HotFix`특정 핫픽스 id의 결과를 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-151">Filters the `Get-HotFix` results for specific hotfix Ids.</span></span> <span data-ttu-id="87cd7-152">와일드 카드는 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-152">Wildcards aren't accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: HFID

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87cd7-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="87cd7-153">CommonParameters</span></span>

<span data-ttu-id="87cd7-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="87cd7-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="87cd7-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87cd7-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="87cd7-156">입력</span><span class="sxs-lookup"><span data-stu-id="87cd7-156">INPUTS</span></span>

### <span data-ttu-id="87cd7-157">String</span><span class="sxs-lookup"><span data-stu-id="87cd7-157">String</span></span>

<span data-ttu-id="87cd7-158">하나 이상의 컴퓨터 이름을 Get-help로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-158">You can pipe one or more computer names to Get-HotFix.</span></span>

## <span data-ttu-id="87cd7-159">출력</span><span class="sxs-lookup"><span data-stu-id="87cd7-159">OUTPUTS</span></span>

### <span data-ttu-id="87cd7-160">Root\CIMV2\ 개체 # Win32_QuickFixEngineering</span><span class="sxs-lookup"><span data-stu-id="87cd7-160">System.Management.ManagementObject#root\CIMV2\Win32_QuickFixEngineering</span></span>

<span data-ttu-id="87cd7-161">`Get-HotFix` 컴퓨터의 핫픽스를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-161">`Get-HotFix` returns objects that represent the hotfixes on the computer.</span></span>

## <span data-ttu-id="87cd7-162">참고</span><span class="sxs-lookup"><span data-stu-id="87cd7-162">NOTES</span></span>

<span data-ttu-id="87cd7-163">**Win32_QuickFixEngineering** [WMI 클래스](/windows/desktop/WmiSdk/retrieving-a-class) 는 현재 운영 체제에 적용 되는, 일반적으로 QFE (quick fix 공학적) 업데이트 라고 하는 작은 시스템 차원 업데이트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-163">The **Win32_QuickFixEngineering** [WMI class](/windows/desktop/WmiSdk/retrieving-a-class) represents a small system-wide update, commonly referred to as a quick-fix engineering (QFE) update, applied to the current operating system.</span></span> <span data-ttu-id="87cd7-164">이 클래스는 CBS (구성 요소 기반 서비스)에서 제공 하는 업데이트만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-164">This class returns only the updates supplied by Component Based Servicing (CBS).</span></span> <span data-ttu-id="87cd7-165">이러한 업데이트는 레지스트리에 나열 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-165">These updates are not listed in the registry.</span></span> <span data-ttu-id="87cd7-166">MSI (Microsoft Windows Installer) 또는 [Windows 업데이트](https://update.microsoft.com) 사이트에서 제공 하는 업데이트는 **Win32_QuickFixEngineering** 에서 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-166">Updates supplied by Microsoft Windows Installer (MSI) or the [Windows Update](https://update.microsoft.com) site are not returned by **Win32_QuickFixEngineering** .</span></span> <span data-ttu-id="87cd7-167">자세한 내용은 [Win32_QuickFixEngineering 클래스](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="87cd7-167">For more information, see [Win32_QuickFixEngineering class](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).</span></span>

<span data-ttu-id="87cd7-168">`Get-HotFix`출력은 운영 체제 마다 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87cd7-168">The `Get-HotFix` output might vary on different operating systems.</span></span>

## <span data-ttu-id="87cd7-169">관련 링크</span><span class="sxs-lookup"><span data-stu-id="87cd7-169">RELATED LINKS</span></span>

[<span data-ttu-id="87cd7-170">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="87cd7-170">about_Arrays</span></span>](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[<span data-ttu-id="87cd7-171">Add-Content</span><span class="sxs-lookup"><span data-stu-id="87cd7-171">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="87cd7-172">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="87cd7-172">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="87cd7-173">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="87cd7-173">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="87cd7-174">Win32_QuickFixEngineering 클래스</span><span class="sxs-lookup"><span data-stu-id="87cd7-174">Win32_QuickFixEngineering class</span></span>](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Computer
ms.openlocfilehash: 89e43220a8d5ac675ea232db09cf3edec2ca2b97
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214561"
---
# <span data-ttu-id="24011-103">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="24011-103">Remove-Computer</span></span>

## <span data-ttu-id="24011-104">개요</span><span class="sxs-lookup"><span data-stu-id="24011-104">SYNOPSIS</span></span>
<span data-ttu-id="24011-105">도메인에서 로컬 및 원격 컴퓨터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-105">Removes the local computer from its domain.</span></span>

## <span data-ttu-id="24011-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="24011-106">SYNTAX</span></span>

### <span data-ttu-id="24011-107">Local (기본값)</span><span class="sxs-lookup"><span data-stu-id="24011-107">Local (Default)</span></span>

```
Remove-Computer [[-UnjoinDomainCredential] <PSCredential>] [-Restart] [-Force] [-PassThru]
 [-WorkgroupName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="24011-108">원격</span><span class="sxs-lookup"><span data-stu-id="24011-108">Remote</span></span>

```
Remove-Computer -UnjoinDomainCredential <PSCredential> [-LocalCredential <PSCredential>] [-Restart]
 [-ComputerName <String[]>] [-Force] [-PassThru] [-WorkgroupName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="24011-109">설명</span><span class="sxs-lookup"><span data-stu-id="24011-109">DESCRIPTION</span></span>

<span data-ttu-id="24011-110">`Remove-Computer`Cmdlet은 현재 도메인에서 로컬 컴퓨터와 원격 컴퓨터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-110">The `Remove-Computer` cmdlet removes the local computer and remote computers from their current domains.</span></span>

<span data-ttu-id="24011-111">도메인에서 컴퓨터를 제거 하면에서 `Remove-Computer` 컴퓨터의 도메인 계정도 사용 하지 않도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24011-111">When you remove a computer from a domain, `Remove-Computer` also disables the domain account of the computer.</span></span> <span data-ttu-id="24011-112">현재 사용자의 자격 증명 인 경우에도 도메인에서 컴퓨터의 가입을 취소 하는 명시적 자격 증명을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-112">You must provide explicit credentials to unjoin the computer from its domain, even when they are the credentials of the current user.</span></span> <span data-ttu-id="24011-113">변경 내용을 적용 하려면 컴퓨터를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-113">You must restart the computer to make the change effective.</span></span> <span data-ttu-id="24011-114">또한 도메인에서 컴퓨터를 제거하면 작업 그룹으로 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-114">Also, when you remove a computer from a domain, you must move it to a workgroup.</span></span> <span data-ttu-id="24011-115">**WorkgroupName** 매개 변수를 사용하여 작업 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-115">Use the **WorkgroupName** parameter to specify the workgroup.</span></span>

<span data-ttu-id="24011-116">작업 그룹에서 도메인으로 컴퓨터를 이동 하려면 한 작업 그룹에서 다른 작업 그룹으로 또는 한 도메인에서 다른 도메인으로 컴퓨터를 이동 하려면 cmdlet을 사용 `Add-Computer` 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-116">To move a computer from a workgroup to a domain, from one workgroup to another, or from one domain to another, use the `Add-Computer` cmdlet.</span></span>

<span data-ttu-id="24011-117">명령 결과를 얻으려면 **Verbose** 및 **PassThru** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-117">To get the results of the command, use the **Verbose** and **PassThru** parameters.</span></span> <span data-ttu-id="24011-118">사용자 프롬프트를 표시하지 않으려면 **Force** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-118">To suppress the user prompt, use the **Force** parameter.</span></span>

<span data-ttu-id="24011-119">`Remove-Computer` 도메인에서 로컬 컴퓨터 및 원격 컴퓨터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-119">`Remove-Computer` removes the local computer and remote computers from domains.</span></span> <span data-ttu-id="24011-120">이 cmdlet에는 원격 컴퓨터에 연결하고 도메인 가입을 해제하기 위해 대체 자격 증명을 지정하는 자격 증명 매개 변수, 영향을 받는 컴퓨터를 다시 시작하는 **Restart**  매개 변수 및 컴퓨터가 추가되는 작업 그룹의 이름을 지정하는 **WorkgroupName** 매개 변수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="24011-120">It includes credential parameters that specify alternate credentials for connecting to remote computers, and unjoining from a domain, a **Restart** parameter for restarting the affected computers, and a **WorkgroupName** parameter for specifying the name of the workgroup to which computers are added.</span></span>

## <span data-ttu-id="24011-121">예제</span><span class="sxs-lookup"><span data-stu-id="24011-121">EXAMPLES</span></span>

### <span data-ttu-id="24011-122">예 1: 도메인에서 로컬 컴퓨터 제거</span><span class="sxs-lookup"><span data-stu-id="24011-122">Example 1: Remove the local computer from its domain</span></span>

<span data-ttu-id="24011-123">이 예제에서는 가입 된 도메인에서 로컬 컴퓨터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-123">This example removes the local computer from the domain to which it is joined.</span></span>

```powershell
Remove-Computer -UnjoinDomaincredential Domain01\Admin01 -PassThru -Verbose -Restart
```

<span data-ttu-id="24011-124">**UnjoinDomainCredential** 매개 변수는 도메인 관리자의 자격 증명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-124">The **UnjoinDomainCredential** parameter provides the credentials of a domain administrator.</span></span> <span data-ttu-id="24011-125">**PassThru** 및 **Verbose** 일반 매개 변수는 명령의 성공 또는 실패에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-125">The **PassThru** and the **Verbose** common parameters display information about the success or failure of the command.</span></span> <span data-ttu-id="24011-126">**Restart** 매개 변수는 컴퓨터를 다시 시작 하 여 제거 작업을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-126">The **Restart** parameter restarts the computer to complete the remove operation.</span></span>

<span data-ttu-id="24011-127">작업 그룹 이름을 지정 하지 않으면 컴퓨터가 도메인에서 제거 된 후 이름이 지정 된 작업 그룹으로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24011-127">When no workgroup name is specified, the computer is moved to the workgroup named after it is removed from its domain.</span></span>

### <span data-ttu-id="24011-128">예제 2: 여러 컴퓨터를 기존 작업 그룹으로 이동</span><span class="sxs-lookup"><span data-stu-id="24011-128">Example 2: Move several computers to a legacy workgroup</span></span>

<span data-ttu-id="24011-129">이 예제에서는 해당 도메인에서 파일에 나열 된 모든 컴퓨터를 제거 `OldServers.txt` 하 고 **레거시** 작업 그룹으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-129">This example removes all the computers listed in the `OldServers.txt` file from their domains and moves them into the **Legacy** workgroup.</span></span>

```powershell
Remove-Computer -ComputerName (Get-Content OldServers.txt) -LocalCredential Domain01\Admin01 -UnJoinDomainCredential Domain01\Admin01 -WorkgroupName "Legacy" -Force -Restart
```

<span data-ttu-id="24011-130">**Localcredential** 매개 변수는 원격 컴퓨터에 연결할 수 있는 권한을 가진 사용자의 자격 증명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-130">The **LocalCredential** parameter provides the credentials of a user who has permission to connect to remote computers.</span></span> <span data-ttu-id="24011-131">**UnjoinDomainCredential** 매개 변수는 도메인에서 컴퓨터를 제거할 수 있는 권한을 가진 사용자의 자격 증명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-131">The **UnjoinDomainCredential** parameter provides the credentials of a user who has permission to remove the computers from their domains.</span></span> <span data-ttu-id="24011-132">**Force** 매개 변수는 각 컴퓨터에 대 한 확인 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-132">The **Force** parameter suppresses the confirmation prompts for each computer.</span></span> <span data-ttu-id="24011-133">**Restart** 매개 변수는 도메인에서 제거 된 후 각 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-133">The **Restart** parameter restarts each of the computers after it is removed from its domain.</span></span>

### <span data-ttu-id="24011-134">예 3: 확인 없이 작업 그룹에서 컴퓨터 제거</span><span class="sxs-lookup"><span data-stu-id="24011-134">Example 3: Remove computers from a workgroup without confirmation</span></span>

<span data-ttu-id="24011-135">이 예제에서는 도메인에서 원격 컴퓨터 Server01 및 로컬 컴퓨터를 제거 하 고 **로컬** 작업 그룹에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-135">This example removes the remote computer, Server01, and the local computer from their domains and adds them to the **Local** workgroup.</span></span>

```powershell
Remove-Computer -ComputerName "Server01", "localhost" -UnjoinDomainCredential Domain01\Admin01 -WorkgroupName "Local" -Restart -Force
```

<span data-ttu-id="24011-136">**Force** 매개 변수는 각 컴퓨터에 대 한 확인 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-136">The **Force** parameter suppresses the confirmation prompt for each computer.</span></span> <span data-ttu-id="24011-137">**Restart** 매개 변수는 컴퓨터를 다시 시작 하 여 변경 내용을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-137">The **Restart** parameter restarts the computers to make the change effective.</span></span>

## <span data-ttu-id="24011-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="24011-138">PARAMETERS</span></span>

### <span data-ttu-id="24011-139">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="24011-139">-ComputerName</span></span>

<span data-ttu-id="24011-140">도메인에서 제거할 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-140">Specifies the computers to be removed from their domains.</span></span> <span data-ttu-id="24011-141">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="24011-141">The default is the local computer.</span></span>

<span data-ttu-id="24011-142">원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 FQDN (정규화 된 도메인 이름)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-142">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of the remote computers.</span></span> <span data-ttu-id="24011-143">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 (.) 또는 localhost를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-143">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="24011-144">이 매개 변수는 PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-144">This parameter does not rely on PowerShell remoting.</span></span> <span data-ttu-id="24011-145">**ComputerName** `Remove-Computer` 컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우에도의 ComputerName 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-145">You can use the **ComputerName** parameter of `Remove-Computer` even if your computer is not configured to run remote commands.</span></span>

<span data-ttu-id="24011-146">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-146">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="24011-147">-Force</span><span class="sxs-lookup"><span data-stu-id="24011-147">-Force</span></span>

<span data-ttu-id="24011-148">사용자 확인 메시지를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-148">Suppresses the user prompt.</span></span> <span data-ttu-id="24011-149">기본적으로에서는 `Remove-Computer` 각 컴퓨터를 제거 하기 전에 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-149">By default, `Remove-Computer` prompts you for confirmation before removing each computer.</span></span>

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

### <span data-ttu-id="24011-150">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="24011-150">-LocalCredential</span></span>

<span data-ttu-id="24011-151">**ComputerName** 매개 변수가 지정 하는 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-151">Specifies a user account that has permission to connect to the computers that the **ComputerName** parameter specifies.</span></span> <span data-ttu-id="24011-152">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="24011-152">The default is the current user.</span></span>

<span data-ttu-id="24011-153">또는와 같은 사용자 이름을 입력 `User01` 하거나, `Domain01\User01` cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="24011-153">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="24011-154">사용자 이름을 입력 하는 경우 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-154">If you type a user name, the cmdlet prompts you for a password.</span></span> <span data-ttu-id="24011-155">현재 도메인에서 컴퓨터를 제거할 수 있는 권한을 가진 사용자 계정을 지정하려면 **UnjoinDomainCredential** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-155">To specify a user account that has permission to remove the computer from its current domain, use the **UnjoinDomainCredential** parameter.</span></span>

<span data-ttu-id="24011-156">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-156">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24011-157">-PassThru</span><span class="sxs-lookup"><span data-stu-id="24011-157">-PassThru</span></span>

<span data-ttu-id="24011-158">명령의 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-158">Returns the results of the command.</span></span> <span data-ttu-id="24011-159">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-159">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="24011-160">-Restart</span><span class="sxs-lookup"><span data-stu-id="24011-160">-Restart</span></span>

<span data-ttu-id="24011-161">이 cmdlet은 제거 중인 컴퓨터를 다시 시작 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="24011-161">Indicates that this cmdlet restarts the computers that are being removed.</span></span> <span data-ttu-id="24011-162">변경 내용을 적용하려면 컴퓨터를 자주 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-162">A restart is often required to make the change effective.</span></span>

<span data-ttu-id="24011-163">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-163">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="24011-164">-UnjoinDomainCredential</span><span class="sxs-lookup"><span data-stu-id="24011-164">-UnjoinDomainCredential</span></span>

<span data-ttu-id="24011-165">현재 도메인에서 컴퓨터를 제거할 수 있는 권한을 가진 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-165">Specifies a user account that has permission to remove the computers from their current domains.</span></span>
<span data-ttu-id="24011-166">값이 현재 사용자의 자격 증명인 경우에도 도메인에서 원격 컴퓨터를 제거하려면 이 매개 변수에서 제공하는 명시적 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-166">Explicit credentials, as provided by this parameter, are required to remove remote computers from a domain, even when the value is the credentials of the current user.</span></span>

<span data-ttu-id="24011-167">User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 `Get-Credential` 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-167">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by `Get-Credential`.</span></span> <span data-ttu-id="24011-168">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-168">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="24011-169">원격 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정하려면 **LocalCredential** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-169">To specify a user account that has permission to connect to the remote computers, use the **LocalCredential** parameter.</span></span>

<span data-ttu-id="24011-170">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-170">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Local, Remote
Aliases: Credential

Required: False (Local), True (Remote)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24011-171">-워크 그룹</span><span class="sxs-lookup"><span data-stu-id="24011-171">-WorkgroupName</span></span>

<span data-ttu-id="24011-172">컴퓨터가 도메인에서 제거될 때 컴퓨터가 추가되어 있는 작업 그룹의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-172">Specifies the name of a workgroup to which the computers are added when they are removed from their domains.</span></span> <span data-ttu-id="24011-173">기본값은 **작업 그룹** 입니다.</span><span class="sxs-lookup"><span data-stu-id="24011-173">The default value is **WORKGROUP** .</span></span> <span data-ttu-id="24011-174">또한 도메인에서 컴퓨터를 제거할 때 해당 컴퓨터를 작업 그룹에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-174">When you remove a computer from a domain, you must add it to a workgroup.</span></span>

<span data-ttu-id="24011-175">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-175">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="24011-176">-Confirm</span><span class="sxs-lookup"><span data-stu-id="24011-176">-Confirm</span></span>

<span data-ttu-id="24011-177">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-177">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="24011-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="24011-178">-WhatIf</span></span>

<span data-ttu-id="24011-179">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-179">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="24011-180">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-180">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="24011-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="24011-181">CommonParameters</span></span>

<span data-ttu-id="24011-182">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="24011-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="24011-183">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24011-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="24011-184">입력</span><span class="sxs-lookup"><span data-stu-id="24011-184">INPUTS</span></span>

### <span data-ttu-id="24011-185">System.String</span><span class="sxs-lookup"><span data-stu-id="24011-185">System.String</span></span>

<span data-ttu-id="24011-186">컴퓨터 이름을 thiscmdlet로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-186">You can pipe computer names to thiscmdlet.</span></span>

## <span data-ttu-id="24011-187">출력</span><span class="sxs-lookup"><span data-stu-id="24011-187">OUTPUTS</span></span>

### <span data-ttu-id="24011-188">Microsoft. PowerShell. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="24011-188">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="24011-189">**PassThru** 매개 변수를 사용 하는 경우 `Remove-Computer` **computerchangeinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="24011-189">When you use the **PassThru** parameter, `Remove-Computer` returns a **ComputerChangeInfo** object.</span></span>
<span data-ttu-id="24011-190">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-190">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="24011-191">참고</span><span class="sxs-lookup"><span data-stu-id="24011-191">NOTES</span></span>

<span data-ttu-id="24011-192">이 cmdlet은 작업 그룹에 컴퓨터를 제거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24011-192">This cmdlet does not remove computers from workgroups.</span></span>

## <span data-ttu-id="24011-193">관련 링크</span><span class="sxs-lookup"><span data-stu-id="24011-193">RELATED LINKS</span></span>

[<span data-ttu-id="24011-194">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="24011-194">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="24011-195">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="24011-195">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="24011-196">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="24011-196">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="24011-197">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="24011-197">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="24011-198">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="24011-198">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="24011-199">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="24011-199">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="24011-200">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="24011-200">Stop-Computer</span></span>](Stop-Computer.md)

[<span data-ttu-id="24011-201">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="24011-201">Test-Connection</span></span>](Test-Connection.md)

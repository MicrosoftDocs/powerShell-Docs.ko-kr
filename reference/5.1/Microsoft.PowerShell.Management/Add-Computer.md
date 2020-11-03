---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Computer
ms.openlocfilehash: c1527c04d795206b8de968daf62456837627a098
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215618"
---
# <span data-ttu-id="5a010-103">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="5a010-103">Add-Computer</span></span>

## <span data-ttu-id="5a010-104">개요</span><span class="sxs-lookup"><span data-stu-id="5a010-104">SYNOPSIS</span></span>
<span data-ttu-id="5a010-105">로컬 컴퓨터를 도메인 또는 작업 그룹에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-105">Add the local computer to a domain or workgroup.</span></span>

## <span data-ttu-id="5a010-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5a010-106">SYNTAX</span></span>

### <span data-ttu-id="5a010-107">도메인 (기본값)</span><span class="sxs-lookup"><span data-stu-id="5a010-107">Domain (Default)</span></span>

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>]
 [-UnjoinDomainCredential <PSCredential>] -Credential <PSCredential> [-DomainName] <String> [-OUPath <String>]
 [-Server <String>] [-Unsecure] [-Options <JoinOptions>] [-Restart] [-PassThru] [-NewName <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5a010-108">작업 그룹</span><span class="sxs-lookup"><span data-stu-id="5a010-108">Workgroup</span></span>

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>] [-Credential <PSCredential>]
 [-WorkgroupName] <String> [-Restart] [-PassThru] [-NewName <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="5a010-109">설명</span><span class="sxs-lookup"><span data-stu-id="5a010-109">DESCRIPTION</span></span>

<span data-ttu-id="5a010-110">`Add-Computer`Cmdlet은 로컬 컴퓨터 또는 원격 컴퓨터를 도메인 또는 작업 그룹에 추가 하거나 한 도메인에서 다른 도메인으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-110">The `Add-Computer` cmdlet adds the local computer or remote computers to a domain or workgroup, or moves them from one domain to another.</span></span>
<span data-ttu-id="5a010-111">컴퓨터가 계정 없이 도메인에 추가된 경우 도메인 계정도 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-111">It also creates a domain account if the computer is added to the domain without an account.</span></span>

<span data-ttu-id="5a010-112">이 cmdlet의 매개 변수를 사용하여 OU(조직 구성 단위) 및 도메인 컨트롤러를 지정하거나 보안되지 않은 가입을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-112">You can use the parameters of this cmdlet to specify an organizational unit (OU) and domain controller or to perform an unsecure join.</span></span>

<span data-ttu-id="5a010-113">명령 결과를 얻으려면 **Verbose** 및 **PassThru** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-113">To get the results of the command, use the **Verbose** and **PassThru** parameters.</span></span>

## <span data-ttu-id="5a010-114">예제</span><span class="sxs-lookup"><span data-stu-id="5a010-114">EXAMPLES</span></span>

### <span data-ttu-id="5a010-115">예 1: 도메인에 로컬 컴퓨터를 추가한 다음 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-115">Example 1: Add a local computer to a domain then restart the computer</span></span>

```powershell
Add-Computer -DomainName Domain01 -Restart
```

<span data-ttu-id="5a010-116">이 명령은 Domain01 도메인에 로컬 컴퓨터를 추가한 다음 컴퓨터를 다시 시작하여 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-116">This command adds the local computer to the Domain01 domain and then restarts the computer to make the change effective.</span></span>

### <span data-ttu-id="5a010-117">예 2: 작업 그룹에 로컬 컴퓨터 추가</span><span class="sxs-lookup"><span data-stu-id="5a010-117">Example 2: Add a local computer to a workgroup</span></span>

```powershell
Add-Computer -WorkgroupName WORKGROUP-A
```

<span data-ttu-id="5a010-118">이 명령은 Workgroup-A 작업 그룹에 로컬 컴퓨터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-118">This command adds the local computer to the Workgroup-A workgroup.</span></span>

### <span data-ttu-id="5a010-119">예 3: 도메인에 로컬 컴퓨터 추가</span><span class="sxs-lookup"><span data-stu-id="5a010-119">Example 3: Add a local computer to a domain</span></span>

```powershell
Add-Computer -DomainName Domain01 -Server Domain01\DC01 -PassThru -Verbose
```

<span data-ttu-id="5a010-120">이 명령은 Domain01\DC01 도메인 컨트롤러를 사용하여 로컬 컴퓨터를 Domain01 도메인에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-120">This command adds the local computer to the Domain01 domain by using the Domain01\DC01 domain controller.</span></span>

<span data-ttu-id="5a010-121">이 명령은 **PassThru** 및 **Verbose** 매개 변수를 사용하여 명령의 결과에 대한 자세한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-121">The command uses the **PassThru** and **Verbose** parameters to get detailed information about the results of the command.</span></span>

### <span data-ttu-id="5a010-122">예제 4: OUPath 매개 변수를 사용 하 여 도메인에 로컬 컴퓨터 추가</span><span class="sxs-lookup"><span data-stu-id="5a010-122">Example 4: Add a local computer to a domain using the OUPath parameter</span></span>

```powershell
Add-Computer -DomainName Domain02 -OUPath "OU=testOU,DC=domain,DC=Domain,DC=com"
```

<span data-ttu-id="5a010-123">이 명령은 Domain02 도메인에 로컬 컴퓨터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-123">This command adds the local computer to the Domain02 domain.</span></span>
<span data-ttu-id="5a010-124">OUPath 매개 변수를 사용하여 새 계정의 조직 구성 단위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-124">It uses the OUPath parameter to specify the organizational unit for the new accounts.</span></span>

### <span data-ttu-id="5a010-125">예 5: 자격 증명을 사용 하 여 도메인에 로컬 컴퓨터 추가</span><span class="sxs-lookup"><span data-stu-id="5a010-125">Example 5: Add a local computer to a domain using credentials</span></span>

```powershell
Add-Computer -ComputerName Server01 -LocalCredential Server01\Admin01 -DomainName Domain02 -Credential Domain02\Admin02 -Restart -Force
```

<span data-ttu-id="5a010-126">이 명령은 Domain02 도메인에 Server01 컴퓨터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-126">This command adds the Server01 computer to the Domain02 domain.</span></span>
<span data-ttu-id="5a010-127">**LocalCredential** 매개 변수를 사용하여 Server01 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-127">It uses the **LocalCredential** parameter to specify a user account that has permission to connect to the Server01 computer.</span></span>
<span data-ttu-id="5a010-128">**Credential** 매개 변수를 사용하여 도메인에 컴퓨터를 가입시킬 수 있는 권한을 가진 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-128">It uses the **Credential** parameter to specify a user account that has permission to join computers to the domain.</span></span>
<span data-ttu-id="5a010-129">**Restart** 매개 변수를 사용하여 가입 작업이 완료된 후 컴퓨터를 다시 시작하고 **Force** 매개 변수를 사용하여 사용자 확인 메시지를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-129">It uses the **Restart** parameter to restart the computer after the join operation completes and the **Force** parameter to suppress user confirmation messages.</span></span>

### <span data-ttu-id="5a010-130">예제 6: 컴퓨터 그룹을 새 도메인으로 이동</span><span class="sxs-lookup"><span data-stu-id="5a010-130">Example 6: Move a group of computers to a new domain</span></span>

```powershell
Add-Computer -ComputerName Server01, Server02, localhost -DomainName Domain02 -LocalCredential Domain01\User01 -UnjoinDomainCredential Domain01\Admin01 -Credential Domain02\Admin01 -Restart
```

<span data-ttu-id="5a010-131">이 명령은 Domain01에서 Domain02로 Server01 및 Server02 컴퓨터와 로컬 컴퓨터를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-131">This command moves the Server01 and Server02 computers, and the local computer, from Domain01 to Domain02.</span></span>

<span data-ttu-id="5a010-132">**LocalCredential** 매개 변수를 사용하여 영향받는 3대의 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-132">It uses the **LocalCredential** parameter to specify a user account that has permission to connect to the three affected computers.</span></span>
<span data-ttu-id="5a010-133">**UnjoinDomainCredential** 매개 변수를 사용하여 Domain01 도메인에서 컴퓨터를 가입 해지할 수 있는 권한을 가진 사용자 계정을 지정하고 **Credential** 매개 변수를 사용하여 Domain02 도메인에 컴퓨터를 가입시킬 수 있는 권한을 가진 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-133">It uses the **UnjoinDomainCredential** parameter to specify a user account that has permission to unjoin the computers from the Domain01 domain and the **Credential** parameter to specify a user account that has permission to join the computers to the Domain02 domain.</span></span>
<span data-ttu-id="5a010-134">**Restart** 매개 변수를 사용하여 이동이 완료된 후 3대의 컴퓨터를 모두 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-134">It uses the **Restart** parameter to restart all three computers after the move is complete.</span></span>

### <span data-ttu-id="5a010-135">예 7: 컴퓨터를 새 도메인으로 이동 하 고 컴퓨터 이름을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-135">Example 7: Move a computer to a new domain and change the name of the computer</span></span>

```powershell
Add-Computer -ComputerName Server01 -DomainName Domain02 -NewName Server044 -Credential Domain02\Admin01 -Restart
```

<span data-ttu-id="5a010-136">이 명령은 Server01 컴퓨터를 Domain02로 이동하고 컴퓨터 이름을 Server044로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-136">This command moves the Server01 computer to the Domain02 and changes the machine name to Server044.</span></span>

<span data-ttu-id="5a010-137">이 명령은 현재 사용자의 자격 증명을 사용하여 Server01 컴퓨터에 연결하고 현재 도메인에서 가입을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-137">The command uses the credential of the current user to connect to the Server01 computer and unjoin it from its current domain.</span></span>
<span data-ttu-id="5a010-138">**Credential** 매개 변수를 사용하여 Domain02 도메인에 컴퓨터를 가입시킬 수 있는 권한을 가진 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-138">It uses the **Credential** parameter to specify  a user account that has permission to join the computer to the Domain02 domain.</span></span>

### <span data-ttu-id="5a010-139">예 8: 파일에 나열 된 컴퓨터를 새 도메인에 추가</span><span class="sxs-lookup"><span data-stu-id="5a010-139">Example 8: Add computers listed in a file to a new domain</span></span>

```powershell
Add-Computer -ComputerName (Get-Content Servers.txt) -DomainName Domain02 -Credential Domain02\Admin02 -Options Win9xUpgrade  -Restart
```

<span data-ttu-id="5a010-140">이 명령은 Servers.txt 파일에 나열된 컴퓨터만 Domain02 도메인에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-140">This command adds the computers that are listed in the Servers.txt file to the Domain02 domain.</span></span>
<span data-ttu-id="5a010-141">**Options** 매개 변수를 사용하여 **Win9xUpgrade** 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-141">It uses the **Options** parameter to specify the **Win9xUpgrade** option.</span></span>
<span data-ttu-id="5a010-142">**Restart** 매개 변수는 가입 작업이 완료된 후 새로 추가된 모든 컴퓨터를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-142">The **Restart** parameter restarts all of the newly added computers after the join operation completes.</span></span>

### <span data-ttu-id="5a010-143">예 9: 미리 정의 된 컴퓨터 자격 증명을 사용 하 여 도메인에 컴퓨터 추가</span><span class="sxs-lookup"><span data-stu-id="5a010-143">Example 9: Add a computer to a domain using predefined computer credentials</span></span>

<span data-ttu-id="5a010-144">이 첫 번째 명령은 이미 도메인에 가입 되어 있는 컴퓨터의 관리자가 실행 해야 합니다 `Domain03` .</span><span class="sxs-lookup"><span data-stu-id="5a010-144">This first command should be run by an administrator from a computer that is already joined to domain `Domain03`:</span></span>

```powershell
New-ADComputer -Name "Server02" -AccountPassword (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)

# Then this command is run from `Server02` which is not yet domain-joined:

$joinCred = New-Object pscredential -ArgumentList ([pscustomobject]@{
    UserName = $null
    Password = (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)[0]
})
Add-Computer -Domain "Domain03" -Options UnsecuredJoin,PasswordPass -Credential $joinCred
```

<span data-ttu-id="5a010-145">이 명령 조합은 기존 도메인에 가입 된 컴퓨터를 사용 하 여 도메인에 미리 정의 된 이름 및 임시 조인 암호를 사용 하 여 새 컴퓨터 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-145">This combination of commands creates a new computer account with a predefined name and temporary join password in a domain using an existing domain-joined computer.</span></span>
<span data-ttu-id="5a010-146">그런 다음, 컴퓨터 이름과 임시 조인 암호만 사용 하 여 미리 정의 된 이름을 사용 하는 컴퓨터가 도메인에 가입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-146">Then separately, a computer with the predefined name joins the domain using only the computer name and the temporary join password.</span></span>
<span data-ttu-id="5a010-147">미리 정의 된 암호는 가입 작업을 지 원하는 데만 사용 되며 컴퓨터가 조인을 완료 한 후 정상적인 컴퓨터 계정 절차의 일부로 대체 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-147">The predefined password is only used to support the join operation and is replaced as part of normal computer account procedures after the computer completes the join.</span></span>

## <span data-ttu-id="5a010-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5a010-148">PARAMETERS</span></span>

### <span data-ttu-id="5a010-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="5a010-149">-ComputerName</span></span>

<span data-ttu-id="5a010-150">도메인 또는 작업 그룹에 추가할 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-150">Specifies the computers to add to a domain or workgroup.</span></span>
<span data-ttu-id="5a010-151">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-151">The default is the local computer.</span></span>

<span data-ttu-id="5a010-152">NetBIOS 이름, IP(인터넷 프로토콜) 주소 또는 각 원격 컴퓨터의 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="5a010-152">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name of each of the  remote computers.</span></span>
<span data-ttu-id="5a010-153">로컬 컴퓨터를 지정하려면 컴퓨터 이름, 점(.) 또는 "localhost"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-153">To specify the local computer, type the computer name, a dot (.), or "localhost".</span></span>

<span data-ttu-id="5a010-154">이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-154">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="5a010-155">**ComputerName** `Add-Computer` 컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우에도의 ComputerName 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-155">You can use the **ComputerName** parameter of `Add-Computer` even if your computer is not configured to run remote commands.</span></span>

<span data-ttu-id="5a010-156">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-156">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5a010-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="5a010-157">-Credential</span></span>

<span data-ttu-id="5a010-158">새 도메인에 컴퓨터를 가입시킬 수 있는 권한을 가진 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-158">Specifies a user account that has permission to join the computers to a new domain.</span></span>
<span data-ttu-id="5a010-159">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-159">The default is the current user.</span></span>

<span data-ttu-id="5a010-160">"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="5a010-160">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="5a010-161">사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-161">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="5a010-162">현재 도메인에서 컴퓨터를 제거할 수 있는 권한을 가진 사용자 계정을 지정하려면 **UnjoinDomainCredential** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-162">To specify a user account that has permission to remove the computer from its current domain, use the **UnjoinDomainCredential** parameter.</span></span>
<span data-ttu-id="5a010-163">원격 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정하려면 **LocalCredential** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-163">To specify a user account that has permission to connect to a remote computer, use the **LocalCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain, Workgroup
Aliases: DomainCredential

Required: True (Domain), False (Workgroup)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a010-164">-DomainName</span><span class="sxs-lookup"><span data-stu-id="5a010-164">-DomainName</span></span>

<span data-ttu-id="5a010-165">컴퓨터가 추가된 도메인을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-165">Specifies the domain to which the computers are added.</span></span>
<span data-ttu-id="5a010-166">컴퓨터를 도메인에 추가할 때 이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-166">This parameter is required when adding the computers to a domain.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DN, Domain

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a010-167">-Force</span><span class="sxs-lookup"><span data-stu-id="5a010-167">-Force</span></span>

<span data-ttu-id="5a010-168">사용자 확인 메시지를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-168">Suppresses the user confirmation prompt.</span></span>
<span data-ttu-id="5a010-169">이 매개 변수를 `Add-Computer` 사용 하지 않으면 각 컴퓨터의 추가를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-169">Without this parameter, `Add-Computer` requires you to confirm the addition of each computer.</span></span>

<span data-ttu-id="5a010-170">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-170">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5a010-171">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="5a010-171">-LocalCredential</span></span>

<span data-ttu-id="5a010-172">**ComputerName** 매개 변수로 지정된 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-172">Specifies a user account that has permission to connect to the computers that are specified by the **ComputerName** parameter.</span></span>
<span data-ttu-id="5a010-173">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-173">The default is the current user.</span></span>

<span data-ttu-id="5a010-174">"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="5a010-174">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="5a010-175">사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-175">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="5a010-176">새 도메인에 컴퓨터를 추가할 수 있는 권한을 가진 사용자 계정을 지정하려면 **Credential** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-176">To specify a user account that has permission to add the computers to a new domain, use the **Credential** parameter.</span></span>
<span data-ttu-id="5a010-177">현재 도메인에서 컴퓨터를 제거할 수 있는 권한을 가진 사용자 계정을 지정하려면 **UnjoinDomainCredential** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-177">To specify a user account that has permission to remove the computers from their current domain, use the **UnjoinDomainCredential** parameter.</span></span>

<span data-ttu-id="5a010-178">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-178">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5a010-179">-NewName</span><span class="sxs-lookup"><span data-stu-id="5a010-179">-NewName</span></span>

<span data-ttu-id="5a010-180">새 도메인의 새로운 컴퓨터 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-180">Specifies a new name for the computer in the new domain.</span></span>
<span data-ttu-id="5a010-181">이 매개 변수는 한 컴퓨터만 추가하거나 이동하는 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-181">This parameter is valid only when one computer is being added or moved.</span></span>

<span data-ttu-id="5a010-182">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-182">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5a010-183">-옵션</span><span class="sxs-lookup"><span data-stu-id="5a010-183">-Options</span></span>

<span data-ttu-id="5a010-184">**컴퓨터 추가** 조인 작업에 대 한 고급 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-184">Specifies advanced options for the **Add-Computer** join operation.</span></span>
<span data-ttu-id="5a010-185">쉼표로 구분된 문자열로 값을 하나 이상 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="5a010-185">Enter one or more values in a comma-separated string.</span></span>

<span data-ttu-id="5a010-186">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-186">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5a010-187">**Accountcreate** : 도메인 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-187">**AccountCreate** : Creates a domain account.</span></span> <span data-ttu-id="5a010-188">컴퓨터 **추가** cmdlet은 도메인에 컴퓨터를 추가할 때 자동으로 도메인 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-188">The **Add-Computer** cmdlet automatically creates a domain account when it adds a computer to a domain.</span></span> <span data-ttu-id="5a010-189">이 옵션은 완전성을 위해 포함 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-189">This option is included for completeness.</span></span>

- <span data-ttu-id="5a010-190">**Win9XUpgrade** : 가입 작업이 Windows 운영 체제 업그레이드의 일부임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-190">**Win9XUpgrade** : Indicates that the join operation is part of a Windows operating system upgrade.</span></span>

- <span data-ttu-id="5a010-191">**UnsecuredJoin** : 보안 되지 않은 조인을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-191">**UnsecuredJoin** : Performs an unsecured join.</span></span> <span data-ttu-id="5a010-192">보안 되지 않은 조인을 요청 *하려면 보안 되지 않은 매개 변수* 또는이 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-192">To request an unsecured join, use the *Unsecure* parameter or this option.</span></span> <span data-ttu-id="5a010-193">컴퓨터 암호를 전달 하려는 경우이 옵션을 옵션과 함께 사용 해야 합니다 `PasswordPass` .</span><span class="sxs-lookup"><span data-stu-id="5a010-193">If you want to pass a machine password, then you must use this option in combination with `PasswordPass` option.</span></span>

- <span data-ttu-id="5a010-194">**Passwordpass** : 보안 되지 않은 조인을 수행한 후 *자격 증명* (DomainCredential) 매개 변수 값으로 컴퓨터 암호를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-194">**PasswordPass** : Sets the machine password to the value of the *Credential* (DomainCredential) parameter after performing an unsecured join.</span></span> <span data-ttu-id="5a010-195">이 옵션은 *Credential* (DomainCredential) 매개 변수 값이 사용자 암호가 아닌 컴퓨터 암호인 것도 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-195">This option also indicates that the value of the *Credential* (DomainCredential) parameter is a machine password, not a user password.</span></span> <span data-ttu-id="5a010-196">이 옵션은 옵션이 지정 된 경우에만 유효 `UnsecuredJoin` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-196">This option is valid only when the `UnsecuredJoin` option is specified.</span></span> <span data-ttu-id="5a010-197">이 옵션을 사용 하는 경우 매개 변수에 제공 된 자격 증명에 `-Credential` null 사용자 이름이 *있어야* 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-197">When using this option, the credential provided to the `-Credential` parameter *must* have a null username.</span></span>

- <span data-ttu-id="5a010-198">**Joinwithnewname** : 새 도메인의 컴퓨터 이름을 *NewName* 매개 변수로 지정 된 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-198">**JoinWithNewName** : Renames the computer name in the new domain to the name specified by the *NewName* parameter.</span></span> <span data-ttu-id="5a010-199">*NewName* 매개 변수를 사용하는 경우 이 옵션은 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-199">When you use the *NewName* parameter, this option is set automatically.</span></span> <span data-ttu-id="5a010-200">이 옵션은 Rename-Computer cmdlet과 함께 사용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-200">This option is designed to be used with the Rename-Computer cmdlet.</span></span> <span data-ttu-id="5a010-201">컴퓨터 **이름 바꾸기 cmdlet을** 사용 하 여 컴퓨터 이름을 변경 하 고 변경 내용을 적용 하기 위해 컴퓨터를 다시 시작 하지 않는 경우이 매개 변수를 사용 하 여 컴퓨터를 새 이름으로 도메인에 가입 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-201">If you use the **Rename-Computer** cmdlet to rename the computer, but do not restart the computer to make the change effective, you can use this parameter to join the computer to a domain with its new name.</span></span>

- <span data-ttu-id="5a010-202">**Joinreadonly** : 기존 컴퓨터 계정을 사용 하 여 컴퓨터를 읽기 전용 도메인 컨트롤러에 가입 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-202">**JoinReadOnly** : Uses an existing machine account to join the computer to a read-only domain controller.</span></span> <span data-ttu-id="5a010-203">컴퓨터 계정은 암호 복제 정책에 대해 허용 된 목록에 추가 해야 하며, 가입 작업 전에 계정 암호를 읽기 전용 도메인 컨트롤러에 복제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-203">The machine account must be added to the allowed list for password replication policy and the account password must be replicated to the read-only domain controller prior to the join operation.</span></span>

- <span data-ttu-id="5a010-204">**Installinvoke** : **JoinDomainOrWorkgroup** 메서드의 **fjoinoptions** 매개 변수에 대 한 create (0x2) 및 delete (0x4) 플래그를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-204">**InstallInvoke** : Sets the create (0x2) and delete (0x4) flags of the **FJoinOptions** parameter of the **JoinDomainOrWorkgroup** method.</span></span> <span data-ttu-id="5a010-205">**JoinDomainOrWorkgroup** 메서드에 대 한 자세한 내용은 MSDN library에서 [Win32_ComputerSystem 클래스의 JoinDomainOrWorkgroup 메서드](https://msdn.microsoft.com/library/aa392154) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5a010-205">For more information about the **JoinDomainOrWorkgroup** method, see [JoinDomainOrWorkgroup method of the Win32_ComputerSystem class](https://msdn.microsoft.com/library/aa392154) in the MSDN library.</span></span> <span data-ttu-id="5a010-206">이러한 옵션에 대 한 자세한 내용은 MSDN library에서 [NetJoinDomain 함수](https://msdn.microsoft.com/library/aa370433) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5a010-206">For more information about these options, see [NetJoinDomain function](https://msdn.microsoft.com/library/aa370433) in the MSDN library.</span></span>

<span data-ttu-id="5a010-207">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.JoinOptions
Parameter Sets: Domain
Aliases:
Accepted values: AccountCreate, Win9XUpgrade, UnsecuredJoin, PasswordPass, DeferSPNSet, JoinWithNewName, JoinReadOnly, InstallInvoke

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a010-208">-OUPath</span><span class="sxs-lookup"><span data-stu-id="5a010-208">-OUPath</span></span>

<span data-ttu-id="5a010-209">도메인 계정의 OU(조직 구성 단위)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-209">Specifies an organizational unit (OU) for the domain account.</span></span>
<span data-ttu-id="5a010-210">따옴표로 OU의 전체 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-210">Enter the full distinguished name of the OU in quotation marks.</span></span>
<span data-ttu-id="5a010-211">기본값은 도메인의 컴퓨터 개체에 대한 기본 OU입니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-211">The default value is the default OU for machine objects in the domain.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: OU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a010-212">-PassThru</span><span class="sxs-lookup"><span data-stu-id="5a010-212">-PassThru</span></span>

<span data-ttu-id="5a010-213">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-213">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="5a010-214">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-214">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="5a010-215">-Restart</span><span class="sxs-lookup"><span data-stu-id="5a010-215">-Restart</span></span>

<span data-ttu-id="5a010-216">도메인 또는 작업 그룹에 추가된 컴퓨터를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-216">Restarts the computers that were added to the domain or workgroup.</span></span>
<span data-ttu-id="5a010-217">변경 내용을 적용하려면 컴퓨터를 자주 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-217">A restart is often required to make the change effective.</span></span>

<span data-ttu-id="5a010-218">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-218">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5a010-219">-Server</span><span class="sxs-lookup"><span data-stu-id="5a010-219">-Server</span></span>

<span data-ttu-id="5a010-220">도메인에 컴퓨터를 추가하는 도메인 컨트롤러의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-220">Specifies the name of a domain controller that adds the computer to the domain.</span></span>
<span data-ttu-id="5a010-221">도메인이름\컴퓨터이름 형식으로 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-221">Enter the name in DomainName\ComputerName format.</span></span>
<span data-ttu-id="5a010-222">기본적으로 도메인 컨트롤러는 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-222">By default, no domain controller is specified.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a010-223">-UnjoinDomainCredential</span><span class="sxs-lookup"><span data-stu-id="5a010-223">-UnjoinDomainCredential</span></span>

<span data-ttu-id="5a010-224">현재 도메인에서 컴퓨터를 제거할 수 있는 권한을 가진 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-224">Specifies a user account that has permission to remove the computers from their current domains.</span></span>
<span data-ttu-id="5a010-225">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-225">The default is the current user.</span></span>

<span data-ttu-id="5a010-226">"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="5a010-226">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="5a010-227">사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-227">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="5a010-228">다른 도메인으로 컴퓨터를 이동하는 경우 이 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-228">Use this parameter when you are moving computers to a different domain.</span></span>
<span data-ttu-id="5a010-229">새 도메인에 가입할 수 있는 권한을 가진 사용자 계정을 지정하려면 **Credential** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-229">To specify a user account that has permission to join the new domain, use the **Credential** parameter.</span></span>
<span data-ttu-id="5a010-230">원격 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정하려면 **LocalCredential** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-230">To specify a user account that has permission to connect to a remote computer, use the **LocalCredential** parameter.</span></span>

<span data-ttu-id="5a010-231">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-231">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a010-232">-안전 하지 않음</span><span class="sxs-lookup"><span data-stu-id="5a010-232">-Unsecure</span></span>

<span data-ttu-id="5a010-233">지정된 도메인에 대한 보안되지 않은 가입을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-233">Performs an unsecure join to the specified domain.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a010-234">-워크 그룹</span><span class="sxs-lookup"><span data-stu-id="5a010-234">-WorkgroupName</span></span>

<span data-ttu-id="5a010-235">컴퓨터가 추가된 작업 그룹의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-235">Specifies the name of a workgroup to which the computers are added.</span></span>
<span data-ttu-id="5a010-236">기본값은 "WORKGROUP"입니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-236">The default value is "WORKGROUP".</span></span>

```yaml
Type: System.String
Parameter Sets: Workgroup
Aliases: WGN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a010-237">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5a010-237">-Confirm</span></span>

<span data-ttu-id="5a010-238">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-238">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5a010-239">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5a010-239">-WhatIf</span></span>

<span data-ttu-id="5a010-240">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-240">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5a010-241">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-241">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5a010-242">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5a010-242">CommonParameters</span></span>

<span data-ttu-id="5a010-243">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5a010-243">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5a010-244">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5a010-244">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5a010-245">입력</span><span class="sxs-lookup"><span data-stu-id="5a010-245">INPUTS</span></span>

### <span data-ttu-id="5a010-246">System.String</span><span class="sxs-lookup"><span data-stu-id="5a010-246">System.String</span></span>

<span data-ttu-id="5a010-247">컴퓨터 이름과 새 이름을 Cmdlet으로 파이프 할 수 있습니다 `Add-Computer` .</span><span class="sxs-lookup"><span data-stu-id="5a010-247">You can pipe computer names and new names to the `Add-Computer` Cmdlet.</span></span>

## <span data-ttu-id="5a010-248">출력</span><span class="sxs-lookup"><span data-stu-id="5a010-248">OUTPUTS</span></span>

### <span data-ttu-id="5a010-249">Microsoft. PowerShell. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="5a010-249">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="5a010-250">**PassThru** 매개 변수를 사용 하는 경우 `Add-Computer` **computerchangeinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-250">When you use the **PassThru** parameter, `Add-Computer` returns a **ComputerChangeInfo** object.</span></span>
<span data-ttu-id="5a010-251">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-251">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5a010-252">참고</span><span class="sxs-lookup"><span data-stu-id="5a010-252">NOTES</span></span>

- <span data-ttu-id="5a010-253">Windows PowerShell 2.0에서 **서버 매개 변수** 는 `Add-Computer` 서버가 있는 경우에도 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-253">In Windows PowerShell 2.0, the **Server** parameter of `Add-Computer` fails even when the server is present.</span></span> <span data-ttu-id="5a010-254">Windows PowerShell 3.0에서는 **Server** 매개 변수의 구현이 안정적으로 작동되도록 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a010-254">In Windows PowerShell 3.0, the implementation of the **Server** parameter is changed so that it works reliably.</span></span>

## <span data-ttu-id="5a010-255">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5a010-255">RELATED LINKS</span></span>

[<span data-ttu-id="5a010-256">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="5a010-256">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="5a010-257">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="5a010-257">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="5a010-258">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="5a010-258">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="5a010-259">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="5a010-259">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="5a010-260">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="5a010-260">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="5a010-261">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="5a010-261">Stop-Computer</span></span>](Stop-Computer.md)

[<span data-ttu-id="5a010-262">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="5a010-262">Test-Connection</span></span>](Test-Connection.md)

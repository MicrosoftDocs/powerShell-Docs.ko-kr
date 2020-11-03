---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: 1c8cde77d16452c9488ce3af62e8b5f761213c80
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211522"
---
# <span data-ttu-id="741c7-103">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="741c7-103">Rename-Computer</span></span>

## <span data-ttu-id="741c7-104">개요</span><span class="sxs-lookup"><span data-stu-id="741c7-104">SYNOPSIS</span></span>
<span data-ttu-id="741c7-105">컴퓨터를 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-105">Renames a computer.</span></span>

## <span data-ttu-id="741c7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="741c7-106">SYNTAX</span></span>

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="741c7-107">설명</span><span class="sxs-lookup"><span data-stu-id="741c7-107">DESCRIPTION</span></span>

<span data-ttu-id="741c7-108">`Rename-Computer`Cmdlet은 로컬 컴퓨터 또는 원격 컴퓨터의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-108">The `Rename-Computer` cmdlet renames the local computer or a remote computer.</span></span>
<span data-ttu-id="741c7-109">각 명령에서 컴퓨터 이름을 하나씩 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-109">It renames one computer in each command.</span></span>

<span data-ttu-id="741c7-110">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-110">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="741c7-111">예제</span><span class="sxs-lookup"><span data-stu-id="741c7-111">EXAMPLES</span></span>

### <span data-ttu-id="741c7-112">예제 1: 로컬 컴퓨터 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="741c7-112">Example 1: Rename the local computer</span></span>

<span data-ttu-id="741c7-113">이 명령은 로컬 컴퓨터의 이름을 `Server044` 바꾼 후 다시 시작 하 여 변경 내용을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-113">This command renames the local computer to `Server044` and then restarts it to make the change effective.</span></span>

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### <span data-ttu-id="741c7-114">예 2: 원격 컴퓨터 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="741c7-114">Example 2: Rename a remote computer</span></span>

<span data-ttu-id="741c7-115">이 명령은 컴퓨터의 이름을 `Srv01` 로 바꿉니다 `Server001` .</span><span class="sxs-lookup"><span data-stu-id="741c7-115">This command renames the `Srv01` computer to `Server001`.</span></span> <span data-ttu-id="741c7-116">컴퓨터를 다시 시작 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-116">The computer is not restarted.</span></span>

<span data-ttu-id="741c7-117">**DomainCredential** 매개 변수는 도메인에 있는 컴퓨터의 이름을 바꿀 수 있는 권한을 가진 사용자의 자격 증명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-117">The **DomainCredential** parameter specifies the credentials of a user who has permission to rename computers in the domain.</span></span>

<span data-ttu-id="741c7-118">**Force** 매개 변수는 확인 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-118">The **Force** parameter suppresses the confirmation prompt.</span></span>

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## <span data-ttu-id="741c7-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="741c7-119">PARAMETERS</span></span>

### <span data-ttu-id="741c7-120">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="741c7-120">-ComputerName</span></span>

<span data-ttu-id="741c7-121">지정된 원격 컴퓨터를 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-121">Renames the specified remote computer.</span></span>
<span data-ttu-id="741c7-122">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-122">The default is the local computer.</span></span>

<span data-ttu-id="741c7-123">원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="741c7-123">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="741c7-124">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 ( `.` ) 또는을 입력 합니다 `localhost` .</span><span class="sxs-lookup"><span data-stu-id="741c7-124">To specify the local computer, type the computer name, a dot (`.`), or `localhost`.</span></span>

<span data-ttu-id="741c7-125">이 매개 변수는 PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-125">This parameter does not rely on PowerShell remoting.</span></span>
<span data-ttu-id="741c7-126">**ComputerName** `Rename-Computer` 컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우에도의 ComputerName 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-126">You can use the **ComputerName** parameter of `Rename-Computer` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local Computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="741c7-127">-DomainCredential</span><span class="sxs-lookup"><span data-stu-id="741c7-127">-DomainCredential</span></span>

<span data-ttu-id="741c7-128">도메인에 연결할 수 있는 권한을 가진 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-128">Specifies a user account that has permission to connect to the domain.</span></span>
<span data-ttu-id="741c7-129">도메인에 가입된 컴퓨터의 이름을 바꾸려면 명시적 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-129">Explicit credentials are required to rename a computer that is joined to a domain.</span></span>

<span data-ttu-id="741c7-130">또는와 같은 사용자 이름을 입력 `User01` 하거나, `Domain01\User01` cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="741c7-130">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="741c7-131">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-131">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="741c7-132">**ComputerName** 매개 변수로 지정된 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정하려면 **LocalCredential** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-132">To specify a user account that has permission to connect to the computer that is specified by the **ComputerName** parameter, use the **LocalCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="741c7-133">-Force</span><span class="sxs-lookup"><span data-stu-id="741c7-133">-Force</span></span>

<span data-ttu-id="741c7-134">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-134">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="741c7-135">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="741c7-135">-LocalCredential</span></span>

<span data-ttu-id="741c7-136">**ComputerName** 매개 변수로 지정된 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-136">Specifies a user account that has permission to connect to the computer specified by the **ComputerName** parameter.</span></span> <span data-ttu-id="741c7-137">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-137">The default is the current user.</span></span>

<span data-ttu-id="741c7-138">또는와 같은 사용자 이름을 입력 `User01` 하거나, `Domain01\User01` cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="741c7-138">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="741c7-139">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-139">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="741c7-140">도메인에 연결할 수 있는 권한을 가진 사용자 계정을 지정하려면 **DomainCredential** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-140">To specify a user account that has permission to connect to the domain, use the **DomainCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current User
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="741c7-141">-NewName</span><span class="sxs-lookup"><span data-stu-id="741c7-141">-NewName</span></span>

<span data-ttu-id="741c7-142">컴퓨터의 새 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-142">Specifies a new name for the computer.</span></span>
<span data-ttu-id="741c7-143">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-143">This parameter is required.</span></span>

<span data-ttu-id="741c7-144">표준 이름에는 문자 ( `a-z` ), ( `A-Z` ), 숫자 ( `0-9` ) 및 하이픈 ()이 포함 될 수 `-` 있지만 공백 또는 마침표 ()는 포함 되지 않습니다 `.` .</span><span class="sxs-lookup"><span data-stu-id="741c7-144">Standard names may contain letters (`a-z`), (`A-Z`), numbers (`0-9`), and hyphens (`-`), but no spaces or periods (`.`).</span></span> <span data-ttu-id="741c7-145">이름은 숫자로만 구성 될 수 없으며 63 자 보다 길 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-145">The name may not consist entirely of digits, and may not be longer than 63 characters</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="741c7-146">-PassThru</span><span class="sxs-lookup"><span data-stu-id="741c7-146">-PassThru</span></span>

<span data-ttu-id="741c7-147">명령의 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-147">Returns the results of the command.</span></span>
<span data-ttu-id="741c7-148">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-148">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="741c7-149">-Restart</span><span class="sxs-lookup"><span data-stu-id="741c7-149">-Restart</span></span>

<span data-ttu-id="741c7-150">이 cmdlet은 이름이 바뀐 컴퓨터를 다시 시작 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-150">Indicates that this cmdlet restarts the computer that was renamed.</span></span>
<span data-ttu-id="741c7-151">변경 내용을 적용하려면 컴퓨터를 자주 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-151">A restart is often required to make the change effective.</span></span>

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

### <span data-ttu-id="741c7-152">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="741c7-152">-WsmanAuthentication</span></span>

<span data-ttu-id="741c7-153">이 cmdlet이 WSMan 프로토콜을 사용 하는 경우 사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-153">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="741c7-154">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-154">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="741c7-155">**기본**</span><span class="sxs-lookup"><span data-stu-id="741c7-155">**Basic**</span></span>
- <span data-ttu-id="741c7-156">**CredSSP**</span><span class="sxs-lookup"><span data-stu-id="741c7-156">**CredSSP**</span></span>
- <span data-ttu-id="741c7-157">**기본값**</span><span class="sxs-lookup"><span data-stu-id="741c7-157">**Default**</span></span>
- <span data-ttu-id="741c7-158">**다이제스트**</span><span class="sxs-lookup"><span data-stu-id="741c7-158">**Digest**</span></span>
- <span data-ttu-id="741c7-159">**Kerberos**</span><span class="sxs-lookup"><span data-stu-id="741c7-159">**Kerberos**</span></span>
- <span data-ttu-id="741c7-160">**결정할**</span><span class="sxs-lookup"><span data-stu-id="741c7-160">**Negotiate**</span></span>

<span data-ttu-id="741c7-161">기본값은 **Default** 입니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-161">The default value is **Default** .</span></span>

<span data-ttu-id="741c7-162">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="741c7-162">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="741c7-163">사용자 자격 증명을 인증을 위해 원격 컴퓨터에 전달 하는 CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-163">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
> <span data-ttu-id="741c7-164">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-164">This mechanism increases the security risk of the remote operation.</span></span>
> <span data-ttu-id="741c7-165">원격 컴퓨터가 손상 된 경우이 컴퓨터로 전달 된 자격 증명을 사용 하 여 네트워크 세션 >을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-165">If the remote computer is compromised, the credentials that are passed to it can be used to control > the network session.</span></span>

<span data-ttu-id="741c7-166">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-166">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="741c7-167">-Confirm</span><span class="sxs-lookup"><span data-stu-id="741c7-167">-Confirm</span></span>

<span data-ttu-id="741c7-168">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-168">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="741c7-169">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="741c7-169">-WhatIf</span></span>

<span data-ttu-id="741c7-170">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-170">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="741c7-171">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-171">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="741c7-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="741c7-172">CommonParameters</span></span>

<span data-ttu-id="741c7-173">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="741c7-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="741c7-174">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="741c7-174">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="741c7-175">입력</span><span class="sxs-lookup"><span data-stu-id="741c7-175">INPUTS</span></span>

### <span data-ttu-id="741c7-176">없음</span><span class="sxs-lookup"><span data-stu-id="741c7-176">None</span></span>

<span data-ttu-id="741c7-177">이 cmdlet에는 값으로 입력을 사용하는 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-177">This cmdlet does not have parameters that take input by value.</span></span>
<span data-ttu-id="741c7-178">그러나 개체의 **ComputerName** 및 **NewName** 속성 값을 이 cmdlet으로 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-178">However, you can pipe the values of the **ComputerName** and **NewName** properties of objects to this cmdlet.</span></span>

## <span data-ttu-id="741c7-179">출력</span><span class="sxs-lookup"><span data-stu-id="741c7-179">OUTPUTS</span></span>

### <span data-ttu-id="741c7-180">Microsoft. PowerShell. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="741c7-180">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="741c7-181">**PassThru** 매개 변수를 지정 하는 경우이 Cmdlet은 **computerchangeinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-181">This cmdlet returns a **ComputerChangeInfo** object, if you specify the **PassThru** parameter.</span></span>
<span data-ttu-id="741c7-182">그러지 않으면 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="741c7-182">Otherwise, it does not return any output.</span></span>

## <span data-ttu-id="741c7-183">참고</span><span class="sxs-lookup"><span data-stu-id="741c7-183">NOTES</span></span>

## <span data-ttu-id="741c7-184">관련 링크</span><span class="sxs-lookup"><span data-stu-id="741c7-184">RELATED LINKS</span></span>

[<span data-ttu-id="741c7-185">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="741c7-185">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="741c7-186">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="741c7-186">Stop-Computer</span></span>](Stop-Computer.md)


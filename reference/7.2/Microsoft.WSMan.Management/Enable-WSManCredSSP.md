---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 08/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/enable-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManCredSSP
ms.openlocfilehash: bacafee683fa47d7be331b4e44d2ab75be5bdb23
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601456"
---
# <span data-ttu-id="a98a4-102">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a98a4-102">Enable-WSManCredSSP</span></span>

## <span data-ttu-id="a98a4-103">개요</span><span class="sxs-lookup"><span data-stu-id="a98a4-103">SYNOPSIS</span></span>
<span data-ttu-id="a98a4-104">컴퓨터에서 CredSSP (Credential Security Support Provider) 인증을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-104">Enables Credential Security Support Provider (CredSSP) authentication on a computer.</span></span>

## <span data-ttu-id="a98a4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a98a4-105">SYNTAX</span></span>

### <span data-ttu-id="a98a4-106">모두</span><span class="sxs-lookup"><span data-stu-id="a98a4-106">All</span></span>

```
Enable-WSManCredSSP [[-DelegateComputer] <String[]>] [-Force] [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="a98a4-107">설명</span><span class="sxs-lookup"><span data-stu-id="a98a4-107">DESCRIPTION</span></span>

<span data-ttu-id="a98a4-108">`Enable-WSManCredSSP`Cmdlet은 클라이언트 또는 서버 컴퓨터에서 CredSSP 인증을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-108">The `Enable-WSManCredSSP` cmdlet enables CredSSP authentication on a client or on a server computer.</span></span>
<span data-ttu-id="a98a4-109">CredSSP 인증을 사용 하는 경우 사용자 자격 증명이 인증을 위해 원격 컴퓨터에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-109">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span> <span data-ttu-id="a98a4-110">이 인증 유형은 다른 원격 세션에서 원격 세션을 만드는 명령을 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-110">This type of authentication is designed for commands that create a remote session from another remote session.</span></span> <span data-ttu-id="a98a4-111">예를 들어 원격 컴퓨터에서 백그라운드 작업을 실행 하려는 경우 이러한 종류의 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-111">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="a98a4-112">`Enable-WSManCredSSP`**클라이언트** 또는 **서버** 에서 CredSSP를 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-112">`Enable-WSManCredSSP` can enable CredSSP on a **Client** or a **Server**.</span></span> <span data-ttu-id="a98a4-113">클라이언트에서 CredSSP를 사용 하도록 설정 하려면 **Role** 매개 변수에 **client** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-113">To enable CredSSP on a client, specify **Client** in the **Role** parameter.</span></span> <span data-ttu-id="a98a4-114">클라이언트는 서버 인증이 수행 될 때 서버에 명시적 자격 증명을 위임 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-114">Clients delegate explicit credentials to a server when server authentication is achieved.</span></span> <span data-ttu-id="a98a4-115">서버에서 CredSSP를 사용 하도록 설정 하려면 **Role** 매개 변수에 **server** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-115">To enable CredSSP on a server, specify **Server** in the **Role** parameter.</span></span> <span data-ttu-id="a98a4-116">서버는 클라이언트의 대리자 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-116">A server acts as a delegate for clients.</span></span> <span data-ttu-id="a98a4-117">자세한 내용은 매개 변수 섹션의 **역할** 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a98a4-117">For more details, see **Role** in the Parameters section.</span></span>

> [!CAUTION]
> <span data-ttu-id="a98a4-118">CredSSP 인증은 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-118">CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="a98a4-119">이렇게 하면 원격 작업의 보안 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-119">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="a98a4-120">원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-120">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="a98a4-121">예제</span><span class="sxs-lookup"><span data-stu-id="a98a4-121">EXAMPLES</span></span>

### <span data-ttu-id="a98a4-122">예제 1: 클라이언트 자격 증명 위임</span><span class="sxs-lookup"><span data-stu-id="a98a4-122">Example 1: Delegate client credentials</span></span>

<span data-ttu-id="a98a4-123">이 예에서는 정규화 된 도메인 이름을 사용 하 여 컴퓨터에 클라이언트 자격 증명을 위임할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-123">This example allows the client credentials to be delegated to a computer by using the fully qualified domain name.</span></span>

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "Server02.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### <span data-ttu-id="a98a4-124">예 2: 도메인의 모든 컴퓨터에 클라이언트 자격 증명 위임</span><span class="sxs-lookup"><span data-stu-id="a98a4-124">Example 2: Delegate client credentials to all computers in a domain</span></span>

<span data-ttu-id="a98a4-125">이 예에서는 **fabrikam.com** 도메인의 모든 컴퓨터에 클라이언트 자격 증명을 위임할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-125">This example allows the client credentials to be delegated to all the computers in the **fabrikam.com** domain.</span></span> <span data-ttu-id="a98a4-126">별표 ( `*` ) 와일드 카드는 모든 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-126">The asterisk (`*`) wildcard specifies all computers.</span></span>

> [!NOTE]
> <span data-ttu-id="a98a4-127">**DelegateComputer** 매개 변수와 함께 와일드 카드를 사용 하면 필요한 것 보다 많은 컴퓨터에서 CredSSP를 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-127">Using wildcards with the **DelegateComputer** parameter can enable CredSSP on more computers than necessary.</span></span>

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "*.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### <span data-ttu-id="a98a4-128">예 3: 여러 컴퓨터에 클라이언트 자격 증명 위임</span><span class="sxs-lookup"><span data-stu-id="a98a4-128">Example 3: Delegate client credentials to multiple computers</span></span>

<span data-ttu-id="a98a4-129">이 예제에서는 클라이언트 자격 증명이 여러 컴퓨터에 위임 될 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-129">This example allows the client credentials to be delegated to multiple computers.</span></span>

```powershell
$servers = "server02.fabrikam.com", "server03.fabrikam.com", "server04.fabrikam.com"
Enable-WSManCredSSP -Role "Client" -DelegateComputer $servers
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

<span data-ttu-id="a98a4-130">`$servers`변수는 서버 이름 목록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-130">The `$servers` variable contains a list of server names.</span></span> <span data-ttu-id="a98a4-131">`Enable-WSManCredSSP`**role** 매개 변수를 사용 하 여 **클라이언트** 역할을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-131">`Enable-WSManCredSSP` uses the **Role** parameter to specify the **Client** role.</span></span> <span data-ttu-id="a98a4-132">**DelegateComputer** 는 변수에서 컴퓨터 이름을 가져옵니다 `$servers` .</span><span class="sxs-lookup"><span data-stu-id="a98a4-132">The **DelegateComputer** gets the computer names from the `$servers` variable.</span></span>

### <span data-ttu-id="a98a4-133">예제 4: 컴퓨터에서 대리자 역할을 할 수 있도록 허용</span><span class="sxs-lookup"><span data-stu-id="a98a4-133">Example 4: Allow a computer to act as a delegate</span></span>

<span data-ttu-id="a98a4-134">이 예제에서는 컴퓨터가 다른 컴퓨터의 대리자 역할을 할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-134">This example allows a computer to act as a delegate for another.</span></span> <span data-ttu-id="a98a4-135">`Enable-WSManCredSSP`앞의 예제에 표시 된 cmdlet은 클라이언트 에서만 CredSSP 인증을 사용 하도록 설정 하 고, 대신 작업을 수행할 수 있는 원격 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-135">The `Enable-WSManCredSSP` cmdlet, shown in the earlier examples, only enables CredSSP authentication on the client, and specifies the remote computers that can act on its behalf.</span></span> <span data-ttu-id="a98a4-136">원격 컴퓨터가 클라이언트의 대리자 역할을 하도록 하려면 WSMan의 **서비스** 노드에 있는 CredSSP 항목을 true로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-136">In order for the remote computer to act as a delegate for the client, the CredSSP item in the **Service** node of WSMan must be set to true.</span></span> <span data-ttu-id="a98a4-137">이 예에서는 WSMan의 **서비스** 노드에 있는 CredSSP 항목을 true로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-137">This example sets the CredSSP item in the **Service** node of WSMan to true.</span></span>

```powershell
Enable-WSManCredSSP -Role "Server"
```

### <span data-ttu-id="a98a4-138">예제 5: 컴퓨터에서 Set-Item를 사용 하 여 대리자 역할을 할 수 있도록 허용</span><span class="sxs-lookup"><span data-stu-id="a98a4-138">Example 5: Allow a computer to act as a delegate by using Set-Item</span></span>

<span data-ttu-id="a98a4-139">이 예제에서는 컴퓨터가 다른 컴퓨터의 대리자 역할을 할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-139">This example allows a computer to act as a delegate for another computer.</span></span> <span data-ttu-id="a98a4-140">`Enable-WSManCredSSP`이전 예제에 표시 된 명령은 클라이언트 컴퓨터 에서만 CredSSP 인증을 사용 하도록 설정 하 고 클라이언트 컴퓨터를 대신 하 여 작동할 수 있는 원격 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-140">The `Enable-WSManCredSSP` commands, shown in the earlier examples, enable CredSSP authentication only on the client computer, and they specify the remote computers that can act on behalf of the client computer.</span></span> <span data-ttu-id="a98a4-141">원격 컴퓨터가 클라이언트 컴퓨터의 대리자 역할을 하도록 하려면 WSMan 공급자의 서비스 디렉터리에 있는 CredSSP 항목을 true로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-141">For the remote computer to act as a delegate for the client computer, the CredSSP item in the Service directory of the WSMan provider must be set to true.</span></span>

```powershell
Connect-WSMan -ComputerName "server02"
Set-Item -Path "WSMan:\server02\service\auth\credSSP" -Value $True
```

<span data-ttu-id="a98a4-142">`Connect-WSMan` 원격 컴퓨터 server02에 대 한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-142">`Connect-WSMan` creates a connection to the remote computer, server02.</span></span> <span data-ttu-id="a98a4-143">`Set-Item` 는 **Path** 매개 변수를 사용 하 여 **WSMan** 공급자의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-143">`Set-Item` uses the **Path** parameter to specify the **WSMan** provider's location.</span></span> <span data-ttu-id="a98a4-144">**값** 매개 변수는 **서비스** 설정을 true로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-144">The **Value** parameter sets the **Service** setting to true.</span></span>

## <span data-ttu-id="a98a4-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a98a4-145">PARAMETERS</span></span>

### <span data-ttu-id="a98a4-146">-DelegateComputer</span><span class="sxs-lookup"><span data-stu-id="a98a4-146">-DelegateComputer</span></span>

<span data-ttu-id="a98a4-147">클라이언트 자격 증명을 위임할 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-147">Specifies servers to which client credentials are delegated.</span></span> <span data-ttu-id="a98a4-148">가장 좋은 방법은 정규화 된 도메인 이름을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-148">The best practice is to use fully qualified domain names.</span></span>

<span data-ttu-id="a98a4-149">와일드 카드가 허용 되지만 필요한 것 보다 많은 컴퓨터에서 CredSSP를 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-149">Wildcards are accepted, but can enable CredSSP on more computers than necessary.</span></span>

<span data-ttu-id="a98a4-150">**Role** 매개 변수가 **Client** 인 경우이 매개 변수를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-150">If the **Role** parameter is **Client**, you must specify this parameter.</span></span> <span data-ttu-id="a98a4-151">**Role** 이 **Server** 인 경우이 매개 변수를 지정 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="a98a4-151">If **Role** is **Server**, don't specify this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a98a4-152">-Force</span><span class="sxs-lookup"><span data-stu-id="a98a4-152">-Force</span></span>

<span data-ttu-id="a98a4-153">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-153">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="a98a4-154">-Role</span><span class="sxs-lookup"><span data-stu-id="a98a4-154">-Role</span></span>

<span data-ttu-id="a98a4-155">CredSSP를 클라이언트 또는 서버로 사용할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-155">Specifies whether to enable CredSSP as a client or as a server.</span></span> <span data-ttu-id="a98a4-156">이 매개 변수에 허용 되는 값은 **클라이언트** 및 **서버** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-156">The acceptable values for this parameter are: **Client** and **Server**.</span></span>

<span data-ttu-id="a98a4-157">**클라이언트** 를 지정 하는 경우 다음 작업이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-157">If you specify **Client**, the following actions are performed.</span></span> <span data-ttu-id="a98a4-158">서버 인증이 수행될 때 이러한 설정을 통해 클라이언트는 명시적 자격 증명을 서버에 위임할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-158">These settings allow the client to delegate explicit credentials to a server when server authentication is achieved.</span></span>

- <span data-ttu-id="a98a4-159">클라이언트에서 CredSSP를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-159">Enables CredSSP on the client.</span></span>
- <span data-ttu-id="a98a4-160">WS-Management 설정을 `\<localhost|computername\>\Client\Auth\CredSSP` true로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-160">Sets the WS-Management setting `\<localhost|computername\>\Client\Auth\CredSSP` to true.</span></span>
- <span data-ttu-id="a98a4-161">클라이언트에서 Windows CredSSP 정책 **AllowFreshCredentials** 을 **WSMan/Delegate** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-161">Sets the Windows CredSSP policy **AllowFreshCredentials** to **WSMan/Delegate** on the client.</span></span>

<span data-ttu-id="a98a4-162">**서버** 를 지정 하는 경우 다음 작업이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-162">If you specify **Server**, the following actions are performed.</span></span> <span data-ttu-id="a98a4-163">이 정책 설정을 통해 서버는 클라이언트의 대리자 역할을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-163">This policy setting allows the server to act as a delegate for clients.</span></span>

- <span data-ttu-id="a98a4-164">서버에서 CredSSP를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-164">Enables CredSSP on the server.</span></span>
- <span data-ttu-id="a98a4-165">WS-Management 설정을 `\<localhost|computername\>\Service\Auth\CredSSP` true로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-165">Sets the WS-Management setting `\<localhost|computername\>\Service\Auth\CredSSP` to true.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a98a4-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a98a4-166">CommonParameters</span></span>

<span data-ttu-id="a98a4-167">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a98a4-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a98a4-168">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a98a4-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a98a4-169">입력</span><span class="sxs-lookup"><span data-stu-id="a98a4-169">INPUTS</span></span>

### <span data-ttu-id="a98a4-170">없음</span><span class="sxs-lookup"><span data-stu-id="a98a4-170">None</span></span>

<span data-ttu-id="a98a4-171">이 cmdlet은 어떠한 입력도 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-171">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="a98a4-172">출력</span><span class="sxs-lookup"><span data-stu-id="a98a4-172">OUTPUTS</span></span>

### <span data-ttu-id="a98a4-173">System.Xml.Xml요소</span><span class="sxs-lookup"><span data-stu-id="a98a4-173">System.Xml.XmlElement</span></span>

<span data-ttu-id="a98a4-174">CredSSP 인증을 사용 하는 경우이 cmdlet은 **XMLElement** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-174">If CredSSP authentication is successfully enabled, this cmdlet generates an **XMLElement** object.</span></span>

## <span data-ttu-id="a98a4-175">참고</span><span class="sxs-lookup"><span data-stu-id="a98a4-175">NOTES</span></span>

<span data-ttu-id="a98a4-176">CredSSP 인증을 사용 하지 않도록 설정 하려면 cmdlet을 사용 `Disable-WSManCredSSP` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a4-176">To disable CredSSP authentication, use the `Disable-WSManCredSSP` cmdlet.</span></span>

## <span data-ttu-id="a98a4-177">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a98a4-177">RELATED LINKS</span></span>

[<span data-ttu-id="a98a4-178">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="a98a4-178">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="a98a4-179">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a98a4-179">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="a98a4-180">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="a98a4-180">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="a98a4-181">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a98a4-181">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="a98a4-182">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a98a4-182">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="a98a4-183">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="a98a4-183">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="a98a4-184">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a98a4-184">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="a98a4-185">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="a98a4-185">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="a98a4-186">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a98a4-186">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="a98a4-187">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a98a4-187">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="a98a4-188">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="a98a4-188">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="a98a4-189">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="a98a4-189">Test-WSMan</span></span>](Test-WSMan.md)

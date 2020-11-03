---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: 6b6cf6b4056dd5907f6a43cd9cf6d491bc7512b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212538"
---
# <span data-ttu-id="07322-103">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="07322-103">Disable-WSManCredSSP</span></span>

## <span data-ttu-id="07322-104">개요</span><span class="sxs-lookup"><span data-stu-id="07322-104">SYNOPSIS</span></span>
<span data-ttu-id="07322-105">컴퓨터에서 CredSSP 인증을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-105">Disables CredSSP authentication on a computer.</span></span>

## <span data-ttu-id="07322-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="07322-106">SYNTAX</span></span>

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="07322-107">설명</span><span class="sxs-lookup"><span data-stu-id="07322-107">DESCRIPTION</span></span>
<span data-ttu-id="07322-108">**Enable-wsmancredssp** cmdlet은 클라이언트 또는 서버 컴퓨터에서 CredSSP (Credential Security Support Provider) 인증을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-108">The **Disable-WSManCredSSP** cmdlet disables Credential Security Support Provider (CredSSP) authentication on a client or on a server computer.</span></span>
<span data-ttu-id="07322-109">CredSSP 인증을 사용 하는 경우 사용자 자격 증명이 인증을 위해 원격 컴퓨터에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07322-109">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span>

<span data-ttu-id="07322-110">이 cmdlet을 사용 하면 *Role* 매개 변수에 client를 지정 하 여 클라이언트에서 CredSSP를 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07322-110">Use this cmdlet to disable CredSSP on the client by specifying Client in the *Role* parameter.</span></span>
<span data-ttu-id="07322-111">이 cmdlet은 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-111">This cmdlet performs the following actions:</span></span>

- <span data-ttu-id="07322-112">클라이언트에서 CredSSP를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-112">Disables CredSSP on the client.</span></span> <span data-ttu-id="07322-113">이 cmdlet은 WS-Management 설정 **\<localhost|computername\> \Client\auth\ststst\sts** 를 false로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-113">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="07322-114">클라이언트의 Windows CredSSP 정책 **AllowFreshCredentials** 에서 WSMan/\* 설정을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-114">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="07322-115">이 cmdlet을 사용 하면 *역할* 에 서버를 지정 하 여 서버에서 CredSSP를 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07322-115">Use this cmdlet to disable CredSSP on the server by specifying Server in *Role* .</span></span>
<span data-ttu-id="07322-116">이 cmdlet은 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-116">This cmdlet performs the following action:</span></span>

- <span data-ttu-id="07322-117">서버에서 CredSSP를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-117">Disables CredSSP on the server.</span></span> <span data-ttu-id="07322-118">이 cmdlet은 WS-Management 설정 **\<localhost|computername\> \Service\auth\test\des** 를 false로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-118">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

<span data-ttu-id="07322-119">주의: CredSSP 인증은 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-119">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="07322-120">이렇게 하면 원격 작업의 보안 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-120">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="07322-121">원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07322-121">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="07322-122">예제</span><span class="sxs-lookup"><span data-stu-id="07322-122">EXAMPLES</span></span>

### <span data-ttu-id="07322-123">예 1: 클라이언트에서 CredSSP를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="07322-123">Example 1: Disable CredSSP on a client</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Client
```

<span data-ttu-id="07322-124">이 명령은 클라이언트에서 CredSSP를 사용하지 않도록 설정하여 서버에 대한 위임을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-124">This command disables CredSSP on the client, which prevents delegation to servers.</span></span>

### <span data-ttu-id="07322-125">예 2: 서버에서 CredSSP를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="07322-125">Example 2: Disable CredSSP on a server</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Server
```

<span data-ttu-id="07322-126">이 명령은 서버에서 CredSSP를 사용하지 않도록 설정하여 클라이언트의 위임을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-126">This command disables CredSSP on the server, which prevents delegation from clients.</span></span>

## <span data-ttu-id="07322-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="07322-127">PARAMETERS</span></span>

### <span data-ttu-id="07322-128">-Role</span><span class="sxs-lookup"><span data-stu-id="07322-128">-Role</span></span>
<span data-ttu-id="07322-129">클라이언트 또는 서버로 CredSSP를 사용 하지 않도록 설정할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-129">Specifies whether to disable CredSSP as a client or as a server.</span></span>
<span data-ttu-id="07322-130">이 매개 변수에 허용 되는 값은 클라이언트 및 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="07322-130">The acceptable values for this parameter are: Client and Server.</span></span>

<span data-ttu-id="07322-131">Client를 지정 하는 경우이 cmdlet은 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-131">If you specify Client, this cmdlet performs the following actions:</span></span>

- <span data-ttu-id="07322-132">클라이언트에서 CredSSP를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-132">Disables CredSSP on the client.</span></span> <span data-ttu-id="07322-133">이 cmdlet은 **\<localhost|computername\> \Client\auth\stststn\sts** 를 false로 설정 WS-Management 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-133">This cmdlet sets WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="07322-134">클라이언트의 Windows CredSSP 정책 **AllowFreshCredentials** 에서 WSMan/\* 설정을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-134">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="07322-135">서버를 지정 하는 경우이 cmdlet은 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-135">If you specify Server, this cmdlet performs the following action:</span></span>

- <span data-ttu-id="07322-136">서버에서 CredSSP를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-136">Disables CredSSP on the server.</span></span> <span data-ttu-id="07322-137">이 cmdlet은 WS-Management 설정 **\<localhost|computername\> \Service\auth\test\des** 를 false로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-137">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

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

### <span data-ttu-id="07322-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="07322-138">CommonParameters</span></span>
<span data-ttu-id="07322-139">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="07322-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="07322-140">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07322-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="07322-141">입력</span><span class="sxs-lookup"><span data-stu-id="07322-141">INPUTS</span></span>

### <span data-ttu-id="07322-142">없음</span><span class="sxs-lookup"><span data-stu-id="07322-142">None</span></span>
<span data-ttu-id="07322-143">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07322-143">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="07322-144">출력</span><span class="sxs-lookup"><span data-stu-id="07322-144">OUTPUTS</span></span>

### <span data-ttu-id="07322-145">없음</span><span class="sxs-lookup"><span data-stu-id="07322-145">None</span></span>
<span data-ttu-id="07322-146">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07322-146">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="07322-147">참고</span><span class="sxs-lookup"><span data-stu-id="07322-147">NOTES</span></span>

* <span data-ttu-id="07322-148">CredSSP 인증을 사용하도록 설정하려면 Enable-WSManCredSSP cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="07322-148">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

*

## <span data-ttu-id="07322-149">관련 링크</span><span class="sxs-lookup"><span data-stu-id="07322-149">RELATED LINKS</span></span>

[<span data-ttu-id="07322-150">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="07322-150">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="07322-151">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="07322-151">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="07322-152">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="07322-152">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="07322-153">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="07322-153">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="07322-154">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="07322-154">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="07322-155">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="07322-155">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="07322-156">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="07322-156">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="07322-157">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="07322-157">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="07322-158">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="07322-158">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="07322-159">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="07322-159">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="07322-160">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="07322-160">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="07322-161">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="07322-161">Test-WSMan</span></span>](Test-WSMan.md)

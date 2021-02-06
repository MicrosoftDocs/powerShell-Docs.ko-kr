---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: 3260c88d57e98c0072af8621600a02901c561acb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602065"
---
# <span data-ttu-id="5246a-102">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="5246a-102">Disable-WSManCredSSP</span></span>

## <span data-ttu-id="5246a-103">개요</span><span class="sxs-lookup"><span data-stu-id="5246a-103">SYNOPSIS</span></span>
<span data-ttu-id="5246a-104">컴퓨터에서 CredSSP 인증을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-104">Disables CredSSP authentication on a computer.</span></span>

## <span data-ttu-id="5246a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5246a-105">SYNTAX</span></span>

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="5246a-106">설명</span><span class="sxs-lookup"><span data-stu-id="5246a-106">DESCRIPTION</span></span>
<span data-ttu-id="5246a-107">**Enable-wsmancredssp** cmdlet은 클라이언트 또는 서버 컴퓨터에서 CredSSP (Credential Security Support Provider) 인증을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-107">The **Disable-WSManCredSSP** cmdlet disables Credential Security Support Provider (CredSSP) authentication on a client or on a server computer.</span></span>
<span data-ttu-id="5246a-108">CredSSP 인증을 사용 하는 경우 사용자 자격 증명이 인증을 위해 원격 컴퓨터에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-108">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span>

<span data-ttu-id="5246a-109">이 cmdlet을 사용 하면 *Role* 매개 변수에 client를 지정 하 여 클라이언트에서 CredSSP를 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-109">Use this cmdlet to disable CredSSP on the client by specifying Client in the *Role* parameter.</span></span>
<span data-ttu-id="5246a-110">이 cmdlet은 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-110">This cmdlet performs the following actions:</span></span>

- <span data-ttu-id="5246a-111">클라이언트에서 CredSSP를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-111">Disables CredSSP on the client.</span></span> <span data-ttu-id="5246a-112">이 cmdlet은 WS-Management 설정 **\<localhost|computername\> \Client\auth\ststst\sts** 를 false로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-112">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="5246a-113">클라이언트의 Windows CredSSP 정책 **AllowFreshCredentials** 에서 WSMan/\* 설정을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-113">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="5246a-114">이 cmdlet을 사용 하면 *역할* 에 서버를 지정 하 여 서버에서 CredSSP를 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-114">Use this cmdlet to disable CredSSP on the server by specifying Server in *Role*.</span></span>
<span data-ttu-id="5246a-115">이 cmdlet은 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-115">This cmdlet performs the following action:</span></span>

- <span data-ttu-id="5246a-116">서버에서 CredSSP를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-116">Disables CredSSP on the server.</span></span> <span data-ttu-id="5246a-117">이 cmdlet은 WS-Management 설정 **\<localhost|computername\> \Service\auth\test\des** 를 false로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-117">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

<span data-ttu-id="5246a-118">주의: CredSSP 인증은 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-118">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="5246a-119">이렇게 하면 원격 작업의 보안 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-119">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="5246a-120">원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-120">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="5246a-121">예제</span><span class="sxs-lookup"><span data-stu-id="5246a-121">EXAMPLES</span></span>

### <span data-ttu-id="5246a-122">예 1: 클라이언트에서 CredSSP를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="5246a-122">Example 1: Disable CredSSP on a client</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Client
```

<span data-ttu-id="5246a-123">이 명령은 클라이언트에서 CredSSP를 사용하지 않도록 설정하여 서버에 대한 위임을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-123">This command disables CredSSP on the client, which prevents delegation to servers.</span></span>

### <span data-ttu-id="5246a-124">예 2: 서버에서 CredSSP를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="5246a-124">Example 2: Disable CredSSP on a server</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Server
```

<span data-ttu-id="5246a-125">이 명령은 서버에서 CredSSP를 사용하지 않도록 설정하여 클라이언트의 위임을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-125">This command disables CredSSP on the server, which prevents delegation from clients.</span></span>

## <span data-ttu-id="5246a-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5246a-126">PARAMETERS</span></span>

### <span data-ttu-id="5246a-127">-Role</span><span class="sxs-lookup"><span data-stu-id="5246a-127">-Role</span></span>
<span data-ttu-id="5246a-128">클라이언트 또는 서버로 CredSSP를 사용 하지 않도록 설정할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-128">Specifies whether to disable CredSSP as a client or as a server.</span></span>
<span data-ttu-id="5246a-129">이 매개 변수에 허용 되는 값은 클라이언트 및 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-129">The acceptable values for this parameter are: Client and Server.</span></span>

<span data-ttu-id="5246a-130">Client를 지정 하는 경우이 cmdlet은 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-130">If you specify Client, this cmdlet performs the following actions:</span></span>

- <span data-ttu-id="5246a-131">클라이언트에서 CredSSP를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-131">Disables CredSSP on the client.</span></span> <span data-ttu-id="5246a-132">이 cmdlet은 **\<localhost|computername\> \Client\auth\stststn\sts** 를 false로 설정 WS-Management 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-132">This cmdlet sets WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="5246a-133">클라이언트의 Windows CredSSP 정책 **AllowFreshCredentials** 에서 WSMan/\* 설정을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-133">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="5246a-134">서버를 지정 하는 경우이 cmdlet은 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-134">If you specify Server, this cmdlet performs the following action:</span></span>

- <span data-ttu-id="5246a-135">서버에서 CredSSP를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-135">Disables CredSSP on the server.</span></span> <span data-ttu-id="5246a-136">이 cmdlet은 WS-Management 설정 **\<localhost|computername\> \Service\auth\test\des** 를 false로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-136">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

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

### <span data-ttu-id="5246a-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5246a-137">CommonParameters</span></span>
<span data-ttu-id="5246a-138">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5246a-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5246a-139">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5246a-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5246a-140">입력</span><span class="sxs-lookup"><span data-stu-id="5246a-140">INPUTS</span></span>

### <span data-ttu-id="5246a-141">없음</span><span class="sxs-lookup"><span data-stu-id="5246a-141">None</span></span>
<span data-ttu-id="5246a-142">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-142">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="5246a-143">출력</span><span class="sxs-lookup"><span data-stu-id="5246a-143">OUTPUTS</span></span>

### <span data-ttu-id="5246a-144">없음</span><span class="sxs-lookup"><span data-stu-id="5246a-144">None</span></span>
<span data-ttu-id="5246a-145">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5246a-146">참고</span><span class="sxs-lookup"><span data-stu-id="5246a-146">NOTES</span></span>

* <span data-ttu-id="5246a-147">CredSSP 인증을 사용하도록 설정하려면 Enable-WSManCredSSP cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5246a-147">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

*

## <span data-ttu-id="5246a-148">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5246a-148">RELATED LINKS</span></span>

[<span data-ttu-id="5246a-149">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="5246a-149">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="5246a-150">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="5246a-150">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="5246a-151">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="5246a-151">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="5246a-152">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="5246a-152">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="5246a-153">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="5246a-153">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="5246a-154">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="5246a-154">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="5246a-155">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="5246a-155">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="5246a-156">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="5246a-156">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="5246a-157">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="5246a-157">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="5246a-158">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="5246a-158">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="5246a-159">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="5246a-159">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="5246a-160">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="5246a-160">Test-WSMan</span></span>](Test-WSMan.md)


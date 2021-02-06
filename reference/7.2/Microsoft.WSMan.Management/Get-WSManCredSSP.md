---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: 9830d1feb31e9cca735a7ac8d2ed9d2ec50380b5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601238"
---
# <span data-ttu-id="92ed5-102">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="92ed5-102">Get-WSManCredSSP</span></span>

## <span data-ttu-id="92ed5-103">개요</span><span class="sxs-lookup"><span data-stu-id="92ed5-103">SYNOPSIS</span></span>
<span data-ttu-id="92ed5-104">클라이언트의 Credential Security Support Provider 관련 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-104">Gets the Credential Security Support Provider-related configuration for the client.</span></span>

## <span data-ttu-id="92ed5-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="92ed5-105">SYNTAX</span></span>

```
Get-WSManCredSSP [<CommonParameters>]
```

## <span data-ttu-id="92ed5-106">설명</span><span class="sxs-lookup"><span data-stu-id="92ed5-106">DESCRIPTION</span></span>
<span data-ttu-id="92ed5-107">**Enable-wsmancredssp** cmdlet은 클라이언트 및 서버의 Credential Security Support Provider 관련 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-107">The **Get-WSManCredSSP** cmdlet gets the Credential Security Support Provider-related configuration of the client and the server.</span></span>
<span data-ttu-id="92ed5-108">출력은 CredSSP(Credential Security Support Provider) 인증의 사용 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-108">The output indicates whether Credential Security Support Provider (CredSSP) authentication is enabled or disabled.</span></span>
<span data-ttu-id="92ed5-109">이 cmdlet은 또한 CredSSP의 **AllowFreshCredentials** 정책에 대 한 구성 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-109">This cmdlet also displays configuration information for the **AllowFreshCredentials** policy of CredSSP.</span></span>

<span data-ttu-id="92ed5-110">CredSSP 인증을 사용 하는 경우 사용자 자격 증명이 인증을 위해 원격 컴퓨터에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-110">When you use CredSSP authentication, the user credentials are passed to a remote computer to be authenticated.</span></span>
<span data-ttu-id="92ed5-111">이 인증 유형은 다른 원격 세션에서 원격 세션을 만드는 명령을 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-111">This type of authentication is designed for commands that create a remote session from another remote session.</span></span>
<span data-ttu-id="92ed5-112">예를 들어 원격 컴퓨터에서 백그라운드 작업을 실행 하려는 경우 이러한 종류의 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-112">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="92ed5-113">이 cmdlet은 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-113">The cmdlet performs the following actions:</span></span>

- <span data-ttu-id="92ed5-114">클라이언트의 WS-Management CredSSP 설정 (**\<localhost|computername\> \Client\auth\stststst\sts**)을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-114">Gets the WS-Management CredSSP setting on the client (**\<localhost|computername\>\Client\Auth\CredSSP**).</span></span>
- <span data-ttu-id="92ed5-115">Windows CredSSP 정책 설정 **AllowFreshCredentials** 을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-115">Gets the Windows CredSSP policy setting **AllowFreshCredentials**.</span></span>
- <span data-ttu-id="92ed5-116">서버에 대 한 WS-Management CredSSP 설정을 가져옵니다 (**\Service\\auth\stst\stst\stst\des \<localhost|computername\>**)</span><span class="sxs-lookup"><span data-stu-id="92ed5-116">Gets the WS-Management CredSSP setting on the server (**\<localhost|computername\>\Service\Auth\CredSSP**).</span></span>

<span data-ttu-id="92ed5-117">주의: CredSSP 인증은 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-117">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="92ed5-118">이렇게 하면 원격 작업의 보안 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-118">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="92ed5-119">원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-119">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="92ed5-120">예제</span><span class="sxs-lookup"><span data-stu-id="92ed5-120">EXAMPLES</span></span>

### <span data-ttu-id="92ed5-121">예제 1: CredSSP 구성 표시</span><span class="sxs-lookup"><span data-stu-id="92ed5-121">Example 1: Display CredSSP configuration</span></span>

```
PS C:\> Get-WSManCredSSP
```

<span data-ttu-id="92ed5-122">이 명령은 클라이언트와 서버 둘 다의 CredSSP 구성 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-122">This command displays CredSSP configuration information for both the client and server.</span></span>

<span data-ttu-id="92ed5-123">출력에서 이 컴퓨터가 CredSSP에 대해 구성되었는지 여부가 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-123">The output identifies that this computer is or is not configured for CredSSP.</span></span>

<span data-ttu-id="92ed5-124">컴퓨터가 CredSSP에 대해 구성된 경우 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-124">If the computer is configured for CredSSP, this is the output:</span></span>

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

<span data-ttu-id="92ed5-125">컴퓨터가 CredSSP에 대해 구성되지 않은 경우 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-125">If the computer is not configured for CredSSP, this is the output:</span></span>

`The machine is not configured to allow delegating fresh credentials.`

## <span data-ttu-id="92ed5-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="92ed5-126">PARAMETERS</span></span>

### <span data-ttu-id="92ed5-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="92ed5-127">CommonParameters</span></span>
<span data-ttu-id="92ed5-128">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="92ed5-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="92ed5-129">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92ed5-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="92ed5-130">입력</span><span class="sxs-lookup"><span data-stu-id="92ed5-130">INPUTS</span></span>

### <span data-ttu-id="92ed5-131">없음</span><span class="sxs-lookup"><span data-stu-id="92ed5-131">None</span></span>
<span data-ttu-id="92ed5-132">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-132">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="92ed5-133">출력</span><span class="sxs-lookup"><span data-stu-id="92ed5-133">OUTPUTS</span></span>

### <span data-ttu-id="92ed5-134">없음</span><span class="sxs-lookup"><span data-stu-id="92ed5-134">None</span></span>
<span data-ttu-id="92ed5-135">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-135">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="92ed5-136">참고</span><span class="sxs-lookup"><span data-stu-id="92ed5-136">NOTES</span></span>

* <span data-ttu-id="92ed5-137">CredSSP 인증을 사용하지 않도록 설정하려면 Disable-WSManCredSSP cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-137">To disable CredSSP authentication, use the Disable-WSManCredSSP cmdlet.</span></span> <span data-ttu-id="92ed5-138">CredSSP 인증을 사용하도록 설정하려면 Enable-WSManCredSSP cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="92ed5-138">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

## <span data-ttu-id="92ed5-139">관련 링크</span><span class="sxs-lookup"><span data-stu-id="92ed5-139">RELATED LINKS</span></span>

[<span data-ttu-id="92ed5-140">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="92ed5-140">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="92ed5-141">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="92ed5-141">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="92ed5-142">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="92ed5-142">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="92ed5-143">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="92ed5-143">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="92ed5-144">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="92ed5-144">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="92ed5-145">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="92ed5-145">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="92ed5-146">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="92ed5-146">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="92ed5-147">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="92ed5-147">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="92ed5-148">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="92ed5-148">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="92ed5-149">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="92ed5-149">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="92ed5-150">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="92ed5-150">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="92ed5-151">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="92ed5-151">Test-WSMan</span></span>](Test-WSMan.md)


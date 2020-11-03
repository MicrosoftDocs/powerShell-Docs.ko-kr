---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: fa9e2c61654a53e367114ecd347a4eccb3b542c1
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209333"
---
# <span data-ttu-id="a9266-103">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a9266-103">Get-WSManCredSSP</span></span>

## <span data-ttu-id="a9266-104">개요</span><span class="sxs-lookup"><span data-stu-id="a9266-104">SYNOPSIS</span></span>
<span data-ttu-id="a9266-105">클라이언트의 Credential Security Support Provider 관련 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-105">Gets the Credential Security Support Provider-related configuration for the client.</span></span>

## <span data-ttu-id="a9266-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a9266-106">SYNTAX</span></span>

```
Get-WSManCredSSP [<CommonParameters>]
```

## <span data-ttu-id="a9266-107">설명</span><span class="sxs-lookup"><span data-stu-id="a9266-107">DESCRIPTION</span></span>
<span data-ttu-id="a9266-108">**Enable-wsmancredssp** cmdlet은 클라이언트 및 서버의 Credential Security Support Provider 관련 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-108">The **Get-WSManCredSSP** cmdlet gets the Credential Security Support Provider-related configuration of the client and the server.</span></span>
<span data-ttu-id="a9266-109">출력은 CredSSP(Credential Security Support Provider) 인증의 사용 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-109">The output indicates whether Credential Security Support Provider (CredSSP) authentication is enabled or disabled.</span></span>
<span data-ttu-id="a9266-110">이 cmdlet은 또한 CredSSP의 **AllowFreshCredentials** 정책에 대 한 구성 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-110">This cmdlet also displays configuration information for the **AllowFreshCredentials** policy of CredSSP.</span></span>

<span data-ttu-id="a9266-111">CredSSP 인증을 사용 하는 경우 사용자 자격 증명이 인증을 위해 원격 컴퓨터에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-111">When you use CredSSP authentication, the user credentials are passed to a remote computer to be authenticated.</span></span>
<span data-ttu-id="a9266-112">이 인증 유형은 다른 원격 세션에서 원격 세션을 만드는 명령을 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-112">This type of authentication is designed for commands that create a remote session from another remote session.</span></span>
<span data-ttu-id="a9266-113">예를 들어 원격 컴퓨터에서 백그라운드 작업을 실행 하려는 경우 이러한 종류의 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-113">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="a9266-114">이 cmdlet은 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-114">The cmdlet performs the following actions:</span></span>

- <span data-ttu-id="a9266-115">클라이언트의 WS-Management CredSSP 설정 ( **\<localhost|computername\> \Client\auth\stststst\sts** )을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-115">Gets the WS-Management CredSSP setting on the client ( **\<localhost|computername\>\Client\Auth\CredSSP** ).</span></span>
- <span data-ttu-id="a9266-116">Windows CredSSP 정책 설정 **AllowFreshCredentials** 을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-116">Gets the Windows CredSSP policy setting **AllowFreshCredentials** .</span></span>
- <span data-ttu-id="a9266-117">서버에 대 한 WS-Management CredSSP 설정을 가져옵니다 ( **\Service\\auth\stst\stst\stst\des \<localhost|computername\>** )</span><span class="sxs-lookup"><span data-stu-id="a9266-117">Gets the WS-Management CredSSP setting on the server ( **\<localhost|computername\>\Service\Auth\CredSSP** ).</span></span>

<span data-ttu-id="a9266-118">주의: CredSSP 인증은 로컬 컴퓨터의 사용자 자격 증명을 원격 컴퓨터에 위임 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-118">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="a9266-119">이렇게 하면 원격 작업의 보안 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-119">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="a9266-120">원격 컴퓨터가 손상된 경우 자격 증명이 원격 컴퓨터에 전달되면 자격 증명이 네트워크 세션을 제어하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-120">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="a9266-121">예제</span><span class="sxs-lookup"><span data-stu-id="a9266-121">EXAMPLES</span></span>

### <span data-ttu-id="a9266-122">예제 1: CredSSP 구성 표시</span><span class="sxs-lookup"><span data-stu-id="a9266-122">Example 1: Display CredSSP configuration</span></span>

```
PS C:\> Get-WSManCredSSP
```

<span data-ttu-id="a9266-123">이 명령은 클라이언트와 서버 둘 다의 CredSSP 구성 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-123">This command displays CredSSP configuration information for both the client and server.</span></span>

<span data-ttu-id="a9266-124">출력에서 이 컴퓨터가 CredSSP에 대해 구성되었는지 여부가 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-124">The output identifies that this computer is or is not configured for CredSSP.</span></span>

<span data-ttu-id="a9266-125">컴퓨터가 CredSSP에 대해 구성된 경우 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-125">If the computer is configured for CredSSP, this is the output:</span></span>

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

<span data-ttu-id="a9266-126">컴퓨터가 CredSSP에 대해 구성되지 않은 경우 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-126">If the computer is not configured for CredSSP, this is the output:</span></span>

`The machine is not configured to allow delegating fresh credentials.`

## <span data-ttu-id="a9266-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a9266-127">PARAMETERS</span></span>

### <span data-ttu-id="a9266-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a9266-128">CommonParameters</span></span>
<span data-ttu-id="a9266-129">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a9266-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a9266-130">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9266-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a9266-131">입력</span><span class="sxs-lookup"><span data-stu-id="a9266-131">INPUTS</span></span>

### <span data-ttu-id="a9266-132">없음</span><span class="sxs-lookup"><span data-stu-id="a9266-132">None</span></span>
<span data-ttu-id="a9266-133">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-133">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="a9266-134">출력</span><span class="sxs-lookup"><span data-stu-id="a9266-134">OUTPUTS</span></span>

### <span data-ttu-id="a9266-135">없음</span><span class="sxs-lookup"><span data-stu-id="a9266-135">None</span></span>
<span data-ttu-id="a9266-136">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-136">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a9266-137">참고</span><span class="sxs-lookup"><span data-stu-id="a9266-137">NOTES</span></span>

* <span data-ttu-id="a9266-138">CredSSP 인증을 사용하지 않도록 설정하려면 Disable-WSManCredSSP cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-138">To disable CredSSP authentication, use the Disable-WSManCredSSP cmdlet.</span></span> <span data-ttu-id="a9266-139">CredSSP 인증을 사용하도록 설정하려면 Enable-WSManCredSSP cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a9266-139">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

## <span data-ttu-id="a9266-140">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a9266-140">RELATED LINKS</span></span>

[<span data-ttu-id="a9266-141">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="a9266-141">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="a9266-142">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a9266-142">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="a9266-143">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="a9266-143">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="a9266-144">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a9266-144">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="a9266-145">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a9266-145">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="a9266-146">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="a9266-146">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="a9266-147">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a9266-147">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="a9266-148">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="a9266-148">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="a9266-149">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a9266-149">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="a9266-150">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a9266-150">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="a9266-151">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="a9266-151">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="a9266-152">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="a9266-152">Test-WSMan</span></span>](Test-WSMan.md)

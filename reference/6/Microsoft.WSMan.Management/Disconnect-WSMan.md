---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disconnect-wsman?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-WSMan
ms.openlocfilehash: 211f1f1129a5497226dfa2d716955cf65c87ecbb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212537"
---
# <span data-ttu-id="c331e-103">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="c331e-103">Disconnect-WSMan</span></span>

## <span data-ttu-id="c331e-104">개요</span><span class="sxs-lookup"><span data-stu-id="c331e-104">SYNOPSIS</span></span>
<span data-ttu-id="c331e-105">원격 컴퓨터의 WinRM 서비스에서 클라이언트 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-105">Disconnects the client from the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="c331e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c331e-106">SYNTAX</span></span>

```
Disconnect-WSMan [[-ComputerName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="c331e-107">설명</span><span class="sxs-lookup"><span data-stu-id="c331e-107">DESCRIPTION</span></span>
<span data-ttu-id="c331e-108">**연결 끊기** cmdlet은 원격 컴퓨터의 WinRM 서비스에서 클라이언트 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-108">The **Disconnect-WSMan** cmdlet disconnects the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="c331e-109">WS-Management 세션을 변수에 저장 한 경우 세션 개체는 변수에 유지 되지만 WS-Management 세션의 상태는 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-109">If you saved the WS-Management session in a variable, the session object remains in the variable, but the state of the WS-Management session is Closed.</span></span>
<span data-ttu-id="c331e-110">WSMan 공급자의 컨텍스트 내에서 이 cmdlet을 사용하여 원격 컴퓨터의 WinRM 서비스에서 클라이언트 연결을 끊을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-110">You can use this cmdlet within the context of the WSMan provider to disconnect the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="c331e-111">그러나 WSMan 공급자로 변경하기 전에 이 cmdlet을 사용하여 원격 컴퓨터의 WinRM 서비스에서 연결을 끊을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-111">However, you can also use this cmdlet to disconnect from the WinRM service on remote computers before you change to the WSMan provider.</span></span>

<span data-ttu-id="c331e-112">원격 컴퓨터의 WinRM 서비스에 연결하는 방법에 대한 자세한 내용은 Connect-WSMan을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c331e-112">For more information about how to connect to the WinRM service on a remote computer, see Connect-WSMan.</span></span>

## <span data-ttu-id="c331e-113">예제</span><span class="sxs-lookup"><span data-stu-id="c331e-113">EXAMPLES</span></span>

### <span data-ttu-id="c331e-114">예 1: 원격 컴퓨터에 대 한 연결 삭제</span><span class="sxs-lookup"><span data-stu-id="c331e-114">Example 1: Delete a connection to a remote computer</span></span>

```
PS C:\> Disconnect-WSMan -computer server01
PS C:\> cd WSMan:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
```

<span data-ttu-id="c331e-115">이 명령은 server01 라는 원격 컴퓨터에 대 한 연결을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-115">This command deletes the connection to the remote computer named server01.</span></span>

<span data-ttu-id="c331e-116">이 cmdlet은 일반적으로 원격 컴퓨터(이 경우 server01 컴퓨터)에서 연결을 끊기 위해 WSMan 공급자의 컨텍스트 내에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-116">This cmdlet is generally used within the context of the WSMan provider to disconnect from a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="c331e-117">그러나 WSMan 공급자로 변경 하기 전에 연결 **끊기** 를 사용 하 여 원격 컴퓨터에 대 한 연결을 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-117">However, you can also use **Disconnect-WSMan** to remove connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="c331e-118">이러한 연결은 ComputerName 목록에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-118">Those connections do not appear in the ComputerName list.</span></span>

## <span data-ttu-id="c331e-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c331e-119">PARAMETERS</span></span>

### <span data-ttu-id="c331e-120">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="c331e-120">-ComputerName</span></span>
<span data-ttu-id="c331e-121">관리 작업을 실행할 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-121">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="c331e-122">이 값은 정규화된 도메인 이름, NetBIOS 이름 또는 IP 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-122">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="c331e-123">로컬 컴퓨터 이름, localhost 또는 점(.)을 사용하여 로컬 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-123">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="c331e-124">로컬 컴퓨터가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-124">The local computer is the default.</span></span>
<span data-ttu-id="c331e-125">원격 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-125">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="c331e-126">이 cmdlet에 이 매개 변수 값을 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-126">You can pipe a value for this parameter to the cmdlet.</span></span>

<span data-ttu-id="c331e-127">로컬 호스트와의 연결을 끊을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-127">You cannot disconnect from the local host.</span></span>
<span data-ttu-id="c331e-128">즉, 로컬 컴퓨터에 대 한 기본 연결의 연결을 끊을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-128">That is, you cannot disconnect the default connection to the local computer.</span></span>
<span data-ttu-id="c331e-129">그러나 로컬 컴퓨터에 대 한 별도의 연결을 만드는 경우 (예: 컴퓨터 이름을 사용 하 여)</span><span class="sxs-lookup"><span data-stu-id="c331e-129">However, if you create a separate connection to the local computer, for example, by using the computer name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c331e-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c331e-130">CommonParameters</span></span>
<span data-ttu-id="c331e-131">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c331e-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c331e-132">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c331e-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c331e-133">입력</span><span class="sxs-lookup"><span data-stu-id="c331e-133">INPUTS</span></span>

### <span data-ttu-id="c331e-134">없음</span><span class="sxs-lookup"><span data-stu-id="c331e-134">None</span></span>
<span data-ttu-id="c331e-135">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-135">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="c331e-136">출력</span><span class="sxs-lookup"><span data-stu-id="c331e-136">OUTPUTS</span></span>

### <span data-ttu-id="c331e-137">없음</span><span class="sxs-lookup"><span data-stu-id="c331e-137">None</span></span>
<span data-ttu-id="c331e-138">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c331e-138">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c331e-139">참고</span><span class="sxs-lookup"><span data-stu-id="c331e-139">NOTES</span></span>

## <span data-ttu-id="c331e-140">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c331e-140">RELATED LINKS</span></span>

[<span data-ttu-id="c331e-141">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="c331e-141">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="c331e-142">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="c331e-142">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="c331e-143">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="c331e-143">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="c331e-144">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="c331e-144">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="c331e-145">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="c331e-145">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="c331e-146">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="c331e-146">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="c331e-147">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="c331e-147">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="c331e-148">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="c331e-148">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="c331e-149">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="c331e-149">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="c331e-150">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="c331e-150">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="c331e-151">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="c331e-151">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="c331e-152">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="c331e-152">Test-WSMan</span></span>](Test-WSMan.md)

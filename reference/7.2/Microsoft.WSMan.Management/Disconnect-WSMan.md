---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disconnect-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-WSMan
ms.openlocfilehash: 948b870948f51bd51424beaeca45ed2b2d195891
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601859"
---
# <span data-ttu-id="f90f9-102">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="f90f9-102">Disconnect-WSMan</span></span>

## <span data-ttu-id="f90f9-103">개요</span><span class="sxs-lookup"><span data-stu-id="f90f9-103">SYNOPSIS</span></span>
<span data-ttu-id="f90f9-104">원격 컴퓨터의 WinRM 서비스에서 클라이언트 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-104">Disconnects the client from the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="f90f9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f90f9-105">SYNTAX</span></span>

```
Disconnect-WSMan [[-ComputerName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="f90f9-106">설명</span><span class="sxs-lookup"><span data-stu-id="f90f9-106">DESCRIPTION</span></span>
<span data-ttu-id="f90f9-107">**연결 끊기** cmdlet은 원격 컴퓨터의 WinRM 서비스에서 클라이언트 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-107">The **Disconnect-WSMan** cmdlet disconnects the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="f90f9-108">WS-Management 세션을 변수에 저장 한 경우 세션 개체는 변수에 유지 되지만 WS-Management 세션의 상태는 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-108">If you saved the WS-Management session in a variable, the session object remains in the variable, but the state of the WS-Management session is Closed.</span></span>
<span data-ttu-id="f90f9-109">WSMan 공급자의 컨텍스트 내에서 이 cmdlet을 사용하여 원격 컴퓨터의 WinRM 서비스에서 클라이언트 연결을 끊을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-109">You can use this cmdlet within the context of the WSMan provider to disconnect the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="f90f9-110">그러나 WSMan 공급자로 변경하기 전에 이 cmdlet을 사용하여 원격 컴퓨터의 WinRM 서비스에서 연결을 끊을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-110">However, you can also use this cmdlet to disconnect from the WinRM service on remote computers before you change to the WSMan provider.</span></span>

<span data-ttu-id="f90f9-111">원격 컴퓨터의 WinRM 서비스에 연결하는 방법에 대한 자세한 내용은 Connect-WSMan을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f90f9-111">For more information about how to connect to the WinRM service on a remote computer, see Connect-WSMan.</span></span>

## <span data-ttu-id="f90f9-112">예제</span><span class="sxs-lookup"><span data-stu-id="f90f9-112">EXAMPLES</span></span>

### <span data-ttu-id="f90f9-113">예 1: 원격 컴퓨터에 대 한 연결 삭제</span><span class="sxs-lookup"><span data-stu-id="f90f9-113">Example 1: Delete a connection to a remote computer</span></span>

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

<span data-ttu-id="f90f9-114">이 명령은 server01 라는 원격 컴퓨터에 대 한 연결을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-114">This command deletes the connection to the remote computer named server01.</span></span>

<span data-ttu-id="f90f9-115">이 cmdlet은 일반적으로 원격 컴퓨터(이 경우 server01 컴퓨터)에서 연결을 끊기 위해 WSMan 공급자의 컨텍스트 내에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-115">This cmdlet is generally used within the context of the WSMan provider to disconnect from a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="f90f9-116">그러나 WSMan 공급자로 변경 하기 전에 연결 **끊기** 를 사용 하 여 원격 컴퓨터에 대 한 연결을 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-116">However, you can also use **Disconnect-WSMan** to remove connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="f90f9-117">이러한 연결은 ComputerName 목록에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-117">Those connections do not appear in the ComputerName list.</span></span>

## <span data-ttu-id="f90f9-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f90f9-118">PARAMETERS</span></span>

### <span data-ttu-id="f90f9-119">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f90f9-119">-ComputerName</span></span>
<span data-ttu-id="f90f9-120">관리 작업을 실행할 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-120">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="f90f9-121">이 값은 정규화된 도메인 이름, NetBIOS 이름 또는 IP 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-121">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="f90f9-122">로컬 컴퓨터 이름, localhost 또는 점(.)을 사용하여 로컬 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-122">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="f90f9-123">로컬 컴퓨터가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-123">The local computer is the default.</span></span>
<span data-ttu-id="f90f9-124">원격 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-124">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="f90f9-125">이 cmdlet에 이 매개 변수 값을 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-125">You can pipe a value for this parameter to the cmdlet.</span></span>

<span data-ttu-id="f90f9-126">로컬 호스트와의 연결을 끊을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-126">You cannot disconnect from the local host.</span></span>
<span data-ttu-id="f90f9-127">즉, 로컬 컴퓨터에 대 한 기본 연결의 연결을 끊을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-127">That is, you cannot disconnect the default connection to the local computer.</span></span>
<span data-ttu-id="f90f9-128">그러나 로컬 컴퓨터에 대 한 별도의 연결을 만드는 경우 (예: 컴퓨터 이름을 사용 하 여)</span><span class="sxs-lookup"><span data-stu-id="f90f9-128">However, if you create a separate connection to the local computer, for example, by using the computer name.</span></span>

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

### <span data-ttu-id="f90f9-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f90f9-129">CommonParameters</span></span>
<span data-ttu-id="f90f9-130">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f90f9-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f90f9-131">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f90f9-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f90f9-132">입력</span><span class="sxs-lookup"><span data-stu-id="f90f9-132">INPUTS</span></span>

### <span data-ttu-id="f90f9-133">없음</span><span class="sxs-lookup"><span data-stu-id="f90f9-133">None</span></span>
<span data-ttu-id="f90f9-134">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-134">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="f90f9-135">출력</span><span class="sxs-lookup"><span data-stu-id="f90f9-135">OUTPUTS</span></span>

### <span data-ttu-id="f90f9-136">없음</span><span class="sxs-lookup"><span data-stu-id="f90f9-136">None</span></span>
<span data-ttu-id="f90f9-137">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f90f9-137">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f90f9-138">참고</span><span class="sxs-lookup"><span data-stu-id="f90f9-138">NOTES</span></span>

## <span data-ttu-id="f90f9-139">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f90f9-139">RELATED LINKS</span></span>

[<span data-ttu-id="f90f9-140">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="f90f9-140">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="f90f9-141">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="f90f9-141">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="f90f9-142">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="f90f9-142">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="f90f9-143">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="f90f9-143">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="f90f9-144">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f90f9-144">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="f90f9-145">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="f90f9-145">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="f90f9-146">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f90f9-146">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="f90f9-147">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="f90f9-147">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="f90f9-148">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f90f9-148">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="f90f9-149">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f90f9-149">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="f90f9-150">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="f90f9-150">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="f90f9-151">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="f90f9-151">Test-WSMan</span></span>](Test-WSMan.md)

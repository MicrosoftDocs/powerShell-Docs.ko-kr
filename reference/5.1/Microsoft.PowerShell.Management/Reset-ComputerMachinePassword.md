---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/reset-computermachinepassword?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ComputerMachinePassword 재설정
ms.openlocfilehash: 1484bc83b9503ce43420b833a1b78b3c4215d98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214489"
---
# <span data-ttu-id="0a95c-103">ComputerMachinePassword 재설정</span><span class="sxs-lookup"><span data-stu-id="0a95c-103">Reset-ComputerMachinePassword</span></span>

## <span data-ttu-id="0a95c-104">개요</span><span class="sxs-lookup"><span data-stu-id="0a95c-104">SYNOPSIS</span></span>
<span data-ttu-id="0a95c-105">컴퓨터의 컴퓨터 계정 암호를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-105">Resets the machine account password for the computer.</span></span>

## <span data-ttu-id="0a95c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0a95c-106">SYNTAX</span></span>

```
Reset-ComputerMachinePassword [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="0a95c-107">설명</span><span class="sxs-lookup"><span data-stu-id="0a95c-107">DESCRIPTION</span></span>
<span data-ttu-id="0a95c-108">**Reset-computermachinepassword** cmdlet은 컴퓨터가 도메인의 도메인 컨트롤러를 인증 하는 데 사용 하는 컴퓨터 계정 암호를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-108">The **Reset-ComputerMachinePassword** cmdlet changes the computer account password that the computers use to authenticate to the domain controllers in the domain.</span></span>
<span data-ttu-id="0a95c-109">이 명령을 사용하여 로컬 컴퓨터의 암호를 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-109">You can use it to reset the password of the local computer.</span></span>

## <span data-ttu-id="0a95c-110">예제</span><span class="sxs-lookup"><span data-stu-id="0a95c-110">EXAMPLES</span></span>

### <span data-ttu-id="0a95c-111">예 1: 로컬 컴퓨터에 대 한 암호 다시 설정</span><span class="sxs-lookup"><span data-stu-id="0a95c-111">Example 1: Reset the password for the local computer</span></span>

```
PS C:\> Reset-ComputerMachinePassword
```

<span data-ttu-id="0a95c-112">이 명령은 로컬 컴퓨터의 컴퓨터 암호를 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-112">This command resets the computer password for the local computer.</span></span>
<span data-ttu-id="0a95c-113">이 명령은 현재 사용자의 자격 증명으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-113">The command runs with the credentials of the current user.</span></span>

### <span data-ttu-id="0a95c-114">예 2: 지정 된 도메인 컨트롤러를 사용 하 여 로컬 컴퓨터의 암호 다시 설정</span><span class="sxs-lookup"><span data-stu-id="0a95c-114">Example 2: Reset the password for the local computer by using a specified domain controller</span></span>

```
PS C:\> Reset-ComputerMachinePassword -Server "DC01" -Credential Domain01\Admin01
```

<span data-ttu-id="0a95c-115">이 명령은 D C 01 도메인 컨트롤러를 사용 하 여 로컬 컴퓨터의 컴퓨터 암호를 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-115">This command resets the computer password of the local computer by using the DC01 domain controller.</span></span>
<span data-ttu-id="0a95c-116">*Credential* 매개 변수를 사용 하 여 도메인에서 컴퓨터 암호를 다시 설정할 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-116">It uses the *Credential* parameter to specify a user account that has permission to reset a computer password in the domain.</span></span>

### <span data-ttu-id="0a95c-117">예 3: 원격 컴퓨터에서 암호 다시 설정</span><span class="sxs-lookup"><span data-stu-id="0a95c-117">Example 3: Reset the password on a remote computer</span></span>

```
$cred = Get-Credential
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Reset-ComputerMachinePassword -Credential $using:cred}
```

<span data-ttu-id="0a95c-118">이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 원격 컴퓨터에서 **reset-computermachinepassword** 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-118">This command uses the Invoke-Command cmdlet to run a **Reset-ComputerMachinePassword** command on the Server01 remote computer.</span></span>

<span data-ttu-id="0a95c-119">Windows PowerShell의 원격 명령에 대 한 자세한 내용은 about_Remote 및 **호출-명령** 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0a95c-119">For more information about remote commands in Windows PowerShell, see about_Remote and **Invoke-Command** .</span></span>

## <span data-ttu-id="0a95c-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0a95c-120">PARAMETERS</span></span>

### <span data-ttu-id="0a95c-121">-Credential</span><span class="sxs-lookup"><span data-stu-id="0a95c-121">-Credential</span></span>
<span data-ttu-id="0a95c-122">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-122">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="0a95c-123">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-123">The default is the current user.</span></span>

<span data-ttu-id="0a95c-124">User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나 **PSCredential** 개체 (예: Get-Credential cmdlet에 의해 생성 된 개체)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-124">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="0a95c-125">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-125">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="0a95c-126">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-126">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="0a95c-127">-Server</span><span class="sxs-lookup"><span data-stu-id="0a95c-127">-Server</span></span>
<span data-ttu-id="0a95c-128">이 cmdlet이 컴퓨터 계정 암호를 설정 하는 경우 사용할 도메인 컨트롤러의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-128">Specifies the name of a domain controller to use when this cmdlet sets the computer account password.</span></span>

<span data-ttu-id="0a95c-129">이 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-129">This parameter is optional.</span></span>
<span data-ttu-id="0a95c-130">이 매개 변수를 생략하면 도메인 컨트롤러가 명령을 처리하도록 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-130">If you omit this parameter, a domain controller is chosen to service the command.</span></span>

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

### <span data-ttu-id="0a95c-131">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0a95c-131">-Confirm</span></span>
<span data-ttu-id="0a95c-132">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-132">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0a95c-133">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0a95c-133">-WhatIf</span></span>
<span data-ttu-id="0a95c-134">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-134">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0a95c-135">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-135">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0a95c-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0a95c-136">CommonParameters</span></span>
<span data-ttu-id="0a95c-137">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0a95c-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0a95c-138">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a95c-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0a95c-139">입력</span><span class="sxs-lookup"><span data-stu-id="0a95c-139">INPUTS</span></span>

### <span data-ttu-id="0a95c-140">없음</span><span class="sxs-lookup"><span data-stu-id="0a95c-140">None</span></span>
<span data-ttu-id="0a95c-141">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-141">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="0a95c-142">출력</span><span class="sxs-lookup"><span data-stu-id="0a95c-142">OUTPUTS</span></span>

### <span data-ttu-id="0a95c-143">없음</span><span class="sxs-lookup"><span data-stu-id="0a95c-143">None</span></span>
<span data-ttu-id="0a95c-144">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a95c-144">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="0a95c-145">참고</span><span class="sxs-lookup"><span data-stu-id="0a95c-145">NOTES</span></span>

## <span data-ttu-id="0a95c-146">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0a95c-146">RELATED LINKS</span></span>

## <span data-ttu-id="0a95c-147">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0a95c-147">RELATED LINKS</span></span>

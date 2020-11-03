---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/disable-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-LocalUser
ms.openlocfilehash: a62242251da00688d3299c60e4cdae7aae6f581a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211922"
---
# <span data-ttu-id="d0e37-103">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="d0e37-103">Disable-LocalUser</span></span>

## <span data-ttu-id="d0e37-104">개요</span><span class="sxs-lookup"><span data-stu-id="d0e37-104">SYNOPSIS</span></span>
<span data-ttu-id="d0e37-105">로컬 사용자 계정을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-105">Disables a local user account.</span></span>

## <span data-ttu-id="d0e37-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d0e37-106">SYNTAX</span></span>

### <span data-ttu-id="d0e37-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="d0e37-107">InputObject</span></span>

```
Disable-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d0e37-108">기본값</span><span class="sxs-lookup"><span data-stu-id="d0e37-108">Default</span></span>

```
Disable-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d0e37-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="d0e37-109">SecurityIdentifier</span></span>

```
Disable-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d0e37-110">설명</span><span class="sxs-lookup"><span data-stu-id="d0e37-110">DESCRIPTION</span></span>
<span data-ttu-id="d0e37-111">**Disable-localuser** cmdlet은 로컬 사용자 계정을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-111">The **Disable-LocalUser** cmdlet disables local user accounts.</span></span>
<span data-ttu-id="d0e37-112">사용자 계정이 사용 하지 않도록 설정 된 경우 사용자가 로그온 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-112">When a user account is disabled, the user cannot log on.</span></span>
<span data-ttu-id="d0e37-113">사용자 계정을 사용 하도록 설정 하면 사용자가 로그온 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-113">When a user account is enabled, the user can log on.</span></span>

> [!NOTE]
> <span data-ttu-id="d0e37-114">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-114">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="d0e37-115">예제</span><span class="sxs-lookup"><span data-stu-id="d0e37-115">EXAMPLES</span></span>

### <span data-ttu-id="d0e37-116">예 1: 이름을 지정 하 여 계정을 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="d0e37-116">Example 1: Disable an account by specifying a name</span></span>

```
PS C:\> Disable-LocalUser -Name "Admin02"
```

<span data-ttu-id="d0e37-117">이 명령은 Admin02 이라는 사용자 계정을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-117">This command disables the user account named Admin02.</span></span>

### <span data-ttu-id="d0e37-118">예제 2: 파이프라인을 사용 하 여 계정 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="d0e37-118">Example 2: Disable an account by using the pipeline</span></span>

```
PS C:\> Get-LocalUser Guest | Disable-LocalUser
```

<span data-ttu-id="d0e37-119">이 명령은 **LocalUser** 를 사용 하 여 기본 제공 게스트 계정을 가져온 다음 파이프라인 연산자를 사용 하 여 현재 cmdlet으로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-119">This command gets the built-in Guest account by using **Get-LocalUser** , and then passes it to the current cmdlet by using the pipeline operator.</span></span>
<span data-ttu-id="d0e37-120">이 cmdlet은 해당 계정을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-120">That cmdlet disables that account.</span></span>

## <span data-ttu-id="d0e37-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d0e37-121">PARAMETERS</span></span>

### <span data-ttu-id="d0e37-122">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d0e37-122">-InputObject</span></span>
<span data-ttu-id="d0e37-123">이 cmdlet이 사용 하지 않도록 설정 하는 사용자 계정 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-123">Specifies an array of user accounts that this cmdlet disables.</span></span>
<span data-ttu-id="d0e37-124">사용자 계정을 가져오려면 Get-LocalUser cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-124">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d0e37-125">-Name</span><span class="sxs-lookup"><span data-stu-id="d0e37-125">-Name</span></span>
<span data-ttu-id="d0e37-126">이 cmdlet이 사용 하지 않도록 설정 된 사용자 계정의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-126">Specifies an array of names of the user accounts that this cmdlet disables.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d0e37-127">-SID</span><span class="sxs-lookup"><span data-stu-id="d0e37-127">-SID</span></span>
<span data-ttu-id="d0e37-128">이 cmdlet이 사용 하지 않도록 설정 하는 사용자 계정 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-128">Specifies an array of user accounts that this cmdlet disables.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d0e37-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d0e37-129">-Confirm</span></span>
<span data-ttu-id="d0e37-130">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d0e37-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d0e37-131">-WhatIf</span></span>
<span data-ttu-id="d0e37-132">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d0e37-133">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d0e37-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d0e37-134">CommonParameters</span></span>
<span data-ttu-id="d0e37-135">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d0e37-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d0e37-136">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d0e37-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d0e37-137">입력</span><span class="sxs-lookup"><span data-stu-id="d0e37-137">INPUTS</span></span>

### <span data-ttu-id="d0e37-138">SecurityAccountsManager, SecurityIdentifier, system.web. 사용자. n a m l.</span><span class="sxs-lookup"><span data-stu-id="d0e37-138">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="d0e37-139">로컬 사용자, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-139">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="d0e37-140">출력</span><span class="sxs-lookup"><span data-stu-id="d0e37-140">OUTPUTS</span></span>

### <span data-ttu-id="d0e37-141">없음</span><span class="sxs-lookup"><span data-stu-id="d0e37-141">None</span></span>
<span data-ttu-id="d0e37-142">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d0e37-143">참고</span><span class="sxs-lookup"><span data-stu-id="d0e37-143">NOTES</span></span>

* <span data-ttu-id="d0e37-144">**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-144">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="d0e37-145">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-145">The possible sources are as follows:</span></span>

- <span data-ttu-id="d0e37-146">로컬</span><span class="sxs-lookup"><span data-stu-id="d0e37-146">Local</span></span>
- <span data-ttu-id="d0e37-147">Active Directory</span><span class="sxs-lookup"><span data-stu-id="d0e37-147">Active Directory</span></span>
- <span data-ttu-id="d0e37-148">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="d0e37-148">Azure Active Directory group</span></span>
- <span data-ttu-id="d0e37-149">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="d0e37-149">Microsoft Account</span></span>

<span data-ttu-id="d0e37-150">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-150">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="d0e37-151">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0e37-151">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="d0e37-152">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d0e37-152">RELATED LINKS</span></span>

[<span data-ttu-id="d0e37-153">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="d0e37-153">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="d0e37-154">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="d0e37-154">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="d0e37-155">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="d0e37-155">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="d0e37-156">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="d0e37-156">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="d0e37-157">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="d0e37-157">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="d0e37-158">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="d0e37-158">Set-LocalUser</span></span>](Set-LocalUser.md)

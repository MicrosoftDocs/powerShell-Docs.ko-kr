---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroup
ms.openlocfilehash: 2cd77c2766840527825b0ccf68abaac3c2ea6c16
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211905"
---
# <span data-ttu-id="e43a7-103">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="e43a7-103">Get-LocalGroup</span></span>

## <span data-ttu-id="e43a7-104">개요</span><span class="sxs-lookup"><span data-stu-id="e43a7-104">SYNOPSIS</span></span>
<span data-ttu-id="e43a7-105">로컬 보안 그룹을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-105">Gets the local security groups.</span></span>

## <span data-ttu-id="e43a7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e43a7-106">SYNTAX</span></span>

### <span data-ttu-id="e43a7-107">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="e43a7-107">Default (Default)</span></span>

```
Get-LocalGroup [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="e43a7-108">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="e43a7-108">SecurityIdentifier</span></span>

```
Get-LocalGroup [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## <span data-ttu-id="e43a7-109">설명</span><span class="sxs-lookup"><span data-stu-id="e43a7-109">DESCRIPTION</span></span>
<span data-ttu-id="e43a7-110">**LocalGroup** Cmdlet은 보안 계정 관리자에서 로컬 보안 그룹을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-110">The **Get-LocalGroup** cmdlet gets local security groups in Security Account Manager.</span></span>
<span data-ttu-id="e43a7-111">이 cmdlet은 기본 제공 되는 기본 제공 그룹 및 사용자가 만든 로컬 보안 그룹을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-111">This cmdlet gets default built-in groups and local security groups that you create.</span></span>

> [!NOTE]
> <span data-ttu-id="e43a7-112">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="e43a7-113">예제</span><span class="sxs-lookup"><span data-stu-id="e43a7-113">EXAMPLES</span></span>

### <span data-ttu-id="e43a7-114">예 1: Administrators 그룹 가져오기</span><span class="sxs-lookup"><span data-stu-id="e43a7-114">Example 1: Get the Administrators group</span></span>

```
PS C:\> Get-LocalGroup -Name "Administrators"
Name           Description
----           -----------
Administrators Administrators have complete and unrestricted access to the computer/domain
```

<span data-ttu-id="e43a7-115">이 명령은 로컬 관리자 그룹을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-115">This command gets the local Administrators group.</span></span>
<span data-ttu-id="e43a7-116">이 명령은 콘솔에서 그룹의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-116">The command displays properties of the group in the console.</span></span>

## <span data-ttu-id="e43a7-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e43a7-117">PARAMETERS</span></span>

### <span data-ttu-id="e43a7-118">-Name</span><span class="sxs-lookup"><span data-stu-id="e43a7-118">-Name</span></span>
<span data-ttu-id="e43a7-119">이 cmdlet이 가져오는 보안 그룹의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-119">Specifies an array of names of security groups that this cmdlet gets.</span></span>
<span data-ttu-id="e43a7-120">와일드 카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-120">You can use the wildcard character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e43a7-121">-SID</span><span class="sxs-lookup"><span data-stu-id="e43a7-121">-SID</span></span>
<span data-ttu-id="e43a7-122">이 cmdlet이 가져오는 보안 그룹의 Sid (보안 Id) 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-122">Specifies an array of security IDs (SIDs) of security groups that this cmdlet gets.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e43a7-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e43a7-123">CommonParameters</span></span>
<span data-ttu-id="e43a7-124">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e43a7-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e43a7-125">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e43a7-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e43a7-126">입력</span><span class="sxs-lookup"><span data-stu-id="e43a7-126">INPUTS</span></span>

### <span data-ttu-id="e43a7-127">System.string (SecurityIdentifier, 시스템)</span><span class="sxs-lookup"><span data-stu-id="e43a7-127">System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="e43a7-128">문자열이 나 SID를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-128">You can pipe a string or a SID to this cmdlet.</span></span>

## <span data-ttu-id="e43a7-129">출력</span><span class="sxs-lookup"><span data-stu-id="e43a7-129">OUTPUTS</span></span>

### <span data-ttu-id="e43a7-130">SecurityAccountsManager. LocalGroup</span><span class="sxs-lookup"><span data-stu-id="e43a7-130">System.Management.Automation.SecurityAccountsManager.LocalGroup</span></span>
<span data-ttu-id="e43a7-131">이 cmdlet은 로컬 그룹을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-131">This cmdlet returns a local group.</span></span>

## <span data-ttu-id="e43a7-132">참고</span><span class="sxs-lookup"><span data-stu-id="e43a7-132">NOTES</span></span>

* <span data-ttu-id="e43a7-133">**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-133">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="e43a7-134">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-134">The possible sources are as follows:</span></span>

- <span data-ttu-id="e43a7-135">로컬</span><span class="sxs-lookup"><span data-stu-id="e43a7-135">Local</span></span>
- <span data-ttu-id="e43a7-136">Active Directory</span><span class="sxs-lookup"><span data-stu-id="e43a7-136">Active Directory</span></span>
- <span data-ttu-id="e43a7-137">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="e43a7-137">Azure Active Directory group</span></span>
- <span data-ttu-id="e43a7-138">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="e43a7-138">Microsoft Account</span></span>

<span data-ttu-id="e43a7-139">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-139">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="e43a7-140">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e43a7-140">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="e43a7-141">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e43a7-141">RELATED LINKS</span></span>

[<span data-ttu-id="e43a7-142">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="e43a7-142">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="e43a7-143">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="e43a7-143">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="e43a7-144">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="e43a7-144">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="e43a7-145">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="e43a7-145">Set-LocalGroup</span></span>](Set-LocalGroup.md)

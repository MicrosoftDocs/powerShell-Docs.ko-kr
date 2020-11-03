---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalUser
ms.openlocfilehash: 34210145bcddc8d9420552d637a6cd6e5f8e61cc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211889"
---
# <span data-ttu-id="164ee-103">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="164ee-103">Get-LocalUser</span></span>

## <span data-ttu-id="164ee-104">개요</span><span class="sxs-lookup"><span data-stu-id="164ee-104">SYNOPSIS</span></span>
<span data-ttu-id="164ee-105">로컬 사용자 계정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-105">Gets local user accounts.</span></span>

## <span data-ttu-id="164ee-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="164ee-106">SYNTAX</span></span>

### <span data-ttu-id="164ee-107">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="164ee-107">Default (Default)</span></span>

```
Get-LocalUser [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="164ee-108">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="164ee-108">SecurityIdentifier</span></span>

```
Get-LocalUser [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## <span data-ttu-id="164ee-109">설명</span><span class="sxs-lookup"><span data-stu-id="164ee-109">DESCRIPTION</span></span>

<span data-ttu-id="164ee-110">`Get-LocalUser`Cmdlet은 로컬 사용자 계정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-110">The `Get-LocalUser` cmdlet gets local user accounts.</span></span> <span data-ttu-id="164ee-111">이 cmdlet은 기본 제공 되는 기본 제공 사용자 계정, 사용자가 만든 로컬 사용자 계정 및 Microsoft 계정에 연결 된 로컬 계정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-111">This cmdlet gets default built-in user accounts, local user accounts that you created, and local accounts that you connected to Microsoft accounts.</span></span>

> [!NOTE]
> <span data-ttu-id="164ee-112">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="164ee-113">예제</span><span class="sxs-lookup"><span data-stu-id="164ee-113">EXAMPLES</span></span>

### <span data-ttu-id="164ee-114">예제 1: 이름을 사용 하 여 계정 가져오기</span><span class="sxs-lookup"><span data-stu-id="164ee-114">Example 1: Get an account by using its name</span></span>

<span data-ttu-id="164ee-115">이 예제에서는 AdminContoso02 이라는 사용자 계정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-115">This example gets a user account named AdminContoso02.</span></span>

```powershell
Get-LocalUser -Name "AdminContoso02"
```

```Output
Name             Enabled Description
----             ------- -----------
AdminContoso02   True    Description of this account.
```

### <span data-ttu-id="164ee-116">예 2: Microsoft 계정에 연결 된 계정 가져오기</span><span class="sxs-lookup"><span data-stu-id="164ee-116">Example 2: Get an account that is connected to a Microsoft account</span></span>

<span data-ttu-id="164ee-117">이 예제에서는 Microsoft 계정에 연결 된 사용자 계정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-117">This example gets a user account that is connected to a Microsoft account.</span></span> <span data-ttu-id="164ee-118">이 예제에서는 Outlook.com에서 계정의 사용자 이름에 자리 표시자 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-118">This example uses a placeholder value for the username of an account at Outlook.com.</span></span>

```powershell
Get-LocalUser -Name "MicrosoftAccount\username@Outlook.com"
```

```Output
Name                                    Enabled  Description
----                                    -------  -----------
MicrosoftAccount\username@outlook.com  True     Description of this account.
```

### <span data-ttu-id="164ee-119">예 3: Microsoft 계정에 연결 된 계정 가져오기</span><span class="sxs-lookup"><span data-stu-id="164ee-119">Example 3: Get an account that is connected to a Microsoft account</span></span>

<span data-ttu-id="164ee-120">이 예제에서는 지정 된 SID를 가진 로컬 사용자 계정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-120">This example gets a local user account that has the specified SID.</span></span>

```powershell
Get-LocalUser -SID S-1-5-21-9526073513-1762370368-3942940353-500
```

```Output
Name          Enabled Description
----          ------- -----------
Administrator True    Built-in account for administering the computer/domain
```

## <span data-ttu-id="164ee-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="164ee-121">PARAMETERS</span></span>

### <span data-ttu-id="164ee-122">-Name</span><span class="sxs-lookup"><span data-stu-id="164ee-122">-Name</span></span>

<span data-ttu-id="164ee-123">이 cmdlet이 가져오는 사용자 계정의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-123">Specifies an array of names of user accounts that this cmdlet gets.</span></span> <span data-ttu-id="164ee-124">와일드 카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-124">You can use the wildcard character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="164ee-125">-SID</span><span class="sxs-lookup"><span data-stu-id="164ee-125">-SID</span></span>

<span data-ttu-id="164ee-126">이 cmdlet이 가져오는 사용자 계정의 Sid (보안 Id) 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-126">Specifies an array of security IDs (SIDs) of user accounts that this cmdlet gets.</span></span>

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

### <span data-ttu-id="164ee-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="164ee-127">CommonParameters</span></span>

<span data-ttu-id="164ee-128">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="164ee-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="164ee-129">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="164ee-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="164ee-130">입력</span><span class="sxs-lookup"><span data-stu-id="164ee-130">INPUTS</span></span>

### <span data-ttu-id="164ee-131">System.string (SecurityIdentifier, 시스템)</span><span class="sxs-lookup"><span data-stu-id="164ee-131">System.String, System.Security.Principal.SecurityIdentifier</span></span>

<span data-ttu-id="164ee-132">문자열이 나 SID를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-132">You can pipe a string or SID to this cmdlet.</span></span>

## <span data-ttu-id="164ee-133">출력</span><span class="sxs-lookup"><span data-stu-id="164ee-133">OUTPUTS</span></span>

### <span data-ttu-id="164ee-134">SecurityAccountsManager. 사용자 []</span><span class="sxs-lookup"><span data-stu-id="164ee-134">System.Management.Automation.SecurityAccountsManager.LocalUser[]</span></span>

<span data-ttu-id="164ee-135">이 cmdlet은 로컬 사용자 계정을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-135">This cmdlet returns local user accounts.</span></span>

## <span data-ttu-id="164ee-136">참고</span><span class="sxs-lookup"><span data-stu-id="164ee-136">NOTES</span></span>

<span data-ttu-id="164ee-137">**Localuser** , **LocalGroup** 및 **localuser** 개체의 **principalsource** 속성은 개체의 원본을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-137">The **PrincipalSource** property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects describes the source of the object.</span></span> <span data-ttu-id="164ee-138">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-138">The possible sources are as follows:</span></span>

- <span data-ttu-id="164ee-139">로컬</span><span class="sxs-lookup"><span data-stu-id="164ee-139">Local</span></span>
- <span data-ttu-id="164ee-140">Active Directory</span><span class="sxs-lookup"><span data-stu-id="164ee-140">Active Directory</span></span>
- <span data-ttu-id="164ee-141">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="164ee-141">Azure Active Directory group</span></span>
- <span data-ttu-id="164ee-142">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="164ee-142">Microsoft Account</span></span>

<span data-ttu-id="164ee-143">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-143">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="164ee-144">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="164ee-144">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="164ee-145">관련 링크</span><span class="sxs-lookup"><span data-stu-id="164ee-145">RELATED LINKS</span></span>

[<span data-ttu-id="164ee-146">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="164ee-146">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="164ee-147">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="164ee-147">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="164ee-148">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="164ee-148">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="164ee-149">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="164ee-149">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="164ee-150">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="164ee-150">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="164ee-151">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="164ee-151">Set-LocalUser</span></span>](Set-LocalUser.md)

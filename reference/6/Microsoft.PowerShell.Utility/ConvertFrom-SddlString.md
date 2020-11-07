---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: 6aa820e2f80b7b2b3068a3b6e06bc99e3b5db179
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343592"
---
# <span data-ttu-id="da4f9-103">ConvertFrom-SddlString</span><span class="sxs-lookup"><span data-stu-id="da4f9-103">ConvertFrom-SddlString</span></span>

## <span data-ttu-id="da4f9-104">개요</span><span class="sxs-lookup"><span data-stu-id="da4f9-104">SYNOPSIS</span></span>
<span data-ttu-id="da4f9-105">SDDL 문자열을 사용자 지정 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-105">Converts a SDDL string to a custom object.</span></span>

## <span data-ttu-id="da4f9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="da4f9-106">SYNTAX</span></span>

### <span data-ttu-id="da4f9-107">모두</span><span class="sxs-lookup"><span data-stu-id="da4f9-107">All</span></span>

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <AccessRightTypeNames>] [<CommonParameters>]
```

## <span data-ttu-id="da4f9-108">설명</span><span class="sxs-lookup"><span data-stu-id="da4f9-108">DESCRIPTION</span></span>

<span data-ttu-id="da4f9-109">`ConvertFrom-SddlString`Cmdlet은 Owner, Group, DiscretionaryAcl, SystemAcl 및 RawDescriptor 속성을 사용 하 여 보안 설명자 정의 언어 문자열을 사용자 지정 **PSCustomObject** 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-109">The `ConvertFrom-SddlString` cmdlet converts a Security Descriptor Definition Language string to a custom **PSCustomObject** object with the following properties: Owner, Group, DiscretionaryAcl, SystemAcl and RawDescriptor.</span></span>

<span data-ttu-id="da4f9-110">Owner, Group, DiscretionaryAcl 및 SystemAcl 속성은 SDDL 문자열에 지정 된 액세스 권한의 읽을 수 있는 텍스트 표현을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-110">Owner, Group, DiscretionaryAcl and SystemAcl properties contain a readable text representation of the access rights specified in a SDDL string.</span></span>

<span data-ttu-id="da4f9-111">이 cmdlet은 PowerShell 5.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-111">This cmdlet was introduced in PowerShell 5.0.</span></span>

## <span data-ttu-id="da4f9-112">예제</span><span class="sxs-lookup"><span data-stu-id="da4f9-112">EXAMPLES</span></span>

### <span data-ttu-id="da4f9-113">예제 1: 파일 시스템 액세스 권한 SDDL을 PSCustomObject로 변환</span><span class="sxs-lookup"><span data-stu-id="da4f9-113">Example 1: Convert file system access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

<span data-ttu-id="da4f9-114">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` C:\Windows 폴더에 대 한 보안 설명자를 가져온 다음 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-114">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the C:\Windows folder and saves it in the variable.</span></span>

<span data-ttu-id="da4f9-115">두 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SddlString` 보안 설명자를 나타내는 개체의 sddl 속성에 포함 된 sddl 문자열의 텍스트 표현을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-115">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

### <span data-ttu-id="da4f9-116">예제 2: 레지스트리 액세스 권한 SDDL을 PSCustomObject로 변환</span><span class="sxs-lookup"><span data-stu-id="da4f9-116">Example 2: Convert registry access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

<span data-ttu-id="da4f9-117">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` HKLM: \ SOFTWARE\Microsoft\ 키에 대 한 보안 설명자를 가져온 다음 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-117">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="da4f9-118">두 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SddlString` 보안 설명자를 나타내는 개체의 sddl 속성에 포함 된 sddl 문자열의 텍스트 표현을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-118">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="da4f9-119">매개 변수를 사용 하 여 `-Type` SDDL 문자열이 레지스트리 보안 설명자를 나타내도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-119">It uses the `-Type` parameter to specify that SDDL string represents a registry security descriptor.</span></span>

### <span data-ttu-id="da4f9-120">예제 3: 매개 변수를 사용 하거나 사용 하지 않고 ConvertFrom-SddlString를 사용 하 여 레지스트리 액세스 권한 SDDL을 PSCustomObject로 변환 `-Type`</span><span class="sxs-lookup"><span data-stu-id="da4f9-120">Example 3: Convert registry access rights SDDL to a PSCustomObject by using ConvertFrom-SddlString with and without the `-Type` parameter</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

<span data-ttu-id="da4f9-121">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` HKLM: \ SOFTWARE\Microsoft\ 키에 대 한 보안 설명자를 가져온 다음 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-121">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="da4f9-122">두 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SddlString` 보안 설명자를 나타내는 개체의 sddl 속성에 포함 된 sddl 문자열의 텍스트 표현을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-122">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="da4f9-123">`-Type`매개 변수를 사용 하지 않으므로 표시 되는 액세스 권한은 파일 시스템용입니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-123">It doesn't use the `-Type` parameter, so the access rights shown are for file system.</span></span>

<span data-ttu-id="da4f9-124">세 번째 명령은 `ConvertFrom-SddlString` 매개 변수와 함께 cmdlet을 사용 `-Type` 하므로 레지스트리에 대 한 액세스 권한이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-124">The third command uses the `ConvertFrom-SddlString` cmdlet with the `-Type` parameter, so the access rights returned are for registry.</span></span>

## <span data-ttu-id="da4f9-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="da4f9-125">PARAMETERS</span></span>

### <span data-ttu-id="da4f9-126">-Sddl</span><span class="sxs-lookup"><span data-stu-id="da4f9-126">-Sddl</span></span>

<span data-ttu-id="da4f9-127">SDDL 구문에서 보안 설명자를 나타내는 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-127">Specifies the string representing the security descriptor in SDDL syntax.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="da4f9-128">-Type</span><span class="sxs-lookup"><span data-stu-id="da4f9-128">-Type</span></span>

<span data-ttu-id="da4f9-129">SDDL 문자열이 나타내는 권한 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-129">Specifies the type of rights that SDDL string represents.</span></span>

<span data-ttu-id="da4f9-130">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-130">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="da4f9-131">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="da4f9-131">FileSystemRights</span></span>
- <span data-ttu-id="da4f9-132">RegistryRights</span><span class="sxs-lookup"><span data-stu-id="da4f9-132">RegistryRights</span></span>
- <span data-ttu-id="da4f9-133">ActiveDirectoryRights</span><span class="sxs-lookup"><span data-stu-id="da4f9-133">ActiveDirectoryRights</span></span>
- <span data-ttu-id="da4f9-134">MutexRights</span><span class="sxs-lookup"><span data-stu-id="da4f9-134">MutexRights</span></span>
- <span data-ttu-id="da4f9-135">SemaphoreRights</span><span class="sxs-lookup"><span data-stu-id="da4f9-135">SemaphoreRights</span></span>
- <span data-ttu-id="da4f9-136">CryptoKeyRights</span><span class="sxs-lookup"><span data-stu-id="da4f9-136">CryptoKeyRights</span></span>
- <span data-ttu-id="da4f9-137">EventWaitHandleRights</span><span class="sxs-lookup"><span data-stu-id="da4f9-137">EventWaitHandleRights</span></span>

<span data-ttu-id="da4f9-138">기본적으로 cmdlet은 파일 시스템 권한을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-138">By default cmdlet uses file system rights.</span></span>

<span data-ttu-id="da4f9-139">CryptoKeyRights 및 ActiveDirectoryRights는 PowerShell Core에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-139">CryptoKeyRights and ActiveDirectoryRights are not supported in PowerShell Core.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ConvertFromSddlStringCommand+AccessRightTypeNames
Parameter Sets: (All)
Aliases:
Accepted values: FileSystemRights, RegistryRights, ActiveDirectoryRights, MutexRights, SemaphoreRights, CryptoKeyRights, EventWaitHandleRights

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="da4f9-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="da4f9-140">CommonParameters</span></span>

<span data-ttu-id="da4f9-141">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="da4f9-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="da4f9-142">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da4f9-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="da4f9-143">입력</span><span class="sxs-lookup"><span data-stu-id="da4f9-143">INPUTS</span></span>

### <span data-ttu-id="da4f9-144">System.String</span><span class="sxs-lookup"><span data-stu-id="da4f9-144">System.String</span></span>

<span data-ttu-id="da4f9-145">SDDL 문자열을로 파이프 할 수 있습니다 `ConvertFrom-SddlString` .</span><span class="sxs-lookup"><span data-stu-id="da4f9-145">You can pipe a SDDL string to `ConvertFrom-SddlString`.</span></span>

## <span data-ttu-id="da4f9-146">출력</span><span class="sxs-lookup"><span data-stu-id="da4f9-146">OUTPUTS</span></span>

## <span data-ttu-id="da4f9-147">참고</span><span class="sxs-lookup"><span data-stu-id="da4f9-147">NOTES</span></span>

<span data-ttu-id="da4f9-148">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da4f9-148">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="da4f9-149">관련 링크</span><span class="sxs-lookup"><span data-stu-id="da4f9-149">RELATED LINKS</span></span>

[<span data-ttu-id="da4f9-150">보안 설명자 정의 언어</span><span class="sxs-lookup"><span data-stu-id="da4f9-150">Security Descriptor Definition Language</span></span>](/windows/win32/secauthz/security-descriptor-definition-language)

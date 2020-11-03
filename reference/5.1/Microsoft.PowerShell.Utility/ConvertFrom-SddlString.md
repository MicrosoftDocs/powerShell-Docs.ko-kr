---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: 128a86312f424eaf9dcfb6cdc97ebd3e148c7886
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/01/2020
ms.locfileid: "93219809"
---
# <span data-ttu-id="dd716-103">ConvertFrom-SddlString</span><span class="sxs-lookup"><span data-stu-id="dd716-103">ConvertFrom-SddlString</span></span>

## <span data-ttu-id="dd716-104">개요</span><span class="sxs-lookup"><span data-stu-id="dd716-104">SYNOPSIS</span></span>

<span data-ttu-id="dd716-105">SDDL 문자열을 사용자 지정 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-105">Converts a SDDL string to a custom object.</span></span>

## <span data-ttu-id="dd716-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dd716-106">SYNTAX</span></span>

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <Object>] [<CommonParameters>]
```

## <span data-ttu-id="dd716-107">설명</span><span class="sxs-lookup"><span data-stu-id="dd716-107">DESCRIPTION</span></span>

<span data-ttu-id="dd716-108">`ConvertFrom-SddlString`Cmdlet은 Owner, Group, DiscretionaryAcl, SystemAcl 및 RawDescriptor 속성을 사용 하 여 보안 설명자 정의 언어 문자열을 사용자 지정 **PSCustomObject** 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-108">The `ConvertFrom-SddlString` cmdlet converts a Security Descriptor Definition Language string to a custom **PSCustomObject** object with the following properties: Owner, Group, DiscretionaryAcl, SystemAcl and RawDescriptor.</span></span>

<span data-ttu-id="dd716-109">Owner, Group, DiscretionaryAcl 및 SystemAcl 속성은 SDDL 문자열에 지정 된 액세스 권한의 읽을 수 있는 텍스트 표현을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-109">Owner, Group, DiscretionaryAcl and SystemAcl properties contain a readable text representation of the access rights specified in a SDDL string.</span></span>

<span data-ttu-id="dd716-110">이 cmdlet은 PowerShell 5.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-110">This cmdlet was introduced in PowerShell 5.0.</span></span>

## <span data-ttu-id="dd716-111">예제</span><span class="sxs-lookup"><span data-stu-id="dd716-111">EXAMPLES</span></span>

### <span data-ttu-id="dd716-112">예제 1: 파일 시스템 액세스 권한 SDDL을 PSCustomObject로 변환</span><span class="sxs-lookup"><span data-stu-id="dd716-112">Example 1: Convert file system access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

<span data-ttu-id="dd716-113">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` C:\Windows 폴더에 대 한 보안 설명자를 가져온 다음 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-113">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the C:\Windows folder and saves it in the variable.</span></span>

<span data-ttu-id="dd716-114">두 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SddlString` 보안 설명자를 나타내는 개체의 sddl 속성에 포함 된 sddl 문자열의 텍스트 표현을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-114">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

### <span data-ttu-id="dd716-115">예제 2: 레지스트리 액세스 권한 SDDL을 PSCustomObject로 변환</span><span class="sxs-lookup"><span data-stu-id="dd716-115">Example 2: Convert registry access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

<span data-ttu-id="dd716-116">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` HKLM: \ SOFTWARE\Microsoft\ 키에 대 한 보안 설명자를 가져온 다음 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-116">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="dd716-117">두 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SddlString` 보안 설명자를 나타내는 개체의 sddl 속성에 포함 된 sddl 문자열의 텍스트 표현을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-117">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="dd716-118">매개 변수를 사용 하 여 `-Type` SDDL 문자열이 레지스트리 보안 설명자를 나타내도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-118">It uses the `-Type` parameter to specify that SDDL string represents a registry security descriptor.</span></span>

### <span data-ttu-id="dd716-119">예제 3: 매개 변수를 사용 하거나 사용 하지 않고 ConvertFrom-SddlString를 사용 하 여 레지스트리 액세스 권한 SDDL을 PSCustomObject로 변환 `-Type`</span><span class="sxs-lookup"><span data-stu-id="dd716-119">Example 3: Convert registry access rights SDDL to a PSCustomObject by using ConvertFrom-SddlString with and without the `-Type` parameter</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

<span data-ttu-id="dd716-120">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` HKLM: \ SOFTWARE\Microsoft\ 키에 대 한 보안 설명자를 가져온 다음 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-120">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="dd716-121">두 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SddlString` 보안 설명자를 나타내는 개체의 sddl 속성에 포함 된 sddl 문자열의 텍스트 표현을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-121">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="dd716-122">`-Type`매개 변수를 사용 하지 않으므로 표시 되는 액세스 권한은 파일 시스템용입니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-122">It doesn't use the `-Type` parameter, so the access rights shown are for file system.</span></span>

<span data-ttu-id="dd716-123">세 번째 명령은 `ConvertFrom-SddlString` 매개 변수와 함께 cmdlet을 사용 `-Type` 하므로 레지스트리에 대 한 액세스 권한이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-123">The third command uses the `ConvertFrom-SddlString` cmdlet with the `-Type` parameter, so the access rights returned are for registry.</span></span>

### <span data-ttu-id="dd716-124">예제 4: Active Directory 액세스 권한 SDDL을 PSCustomObject로 변환</span><span class="sxs-lookup"><span data-stu-id="dd716-124">Example 4: Convert Active Directory access rights SDDL to a PSCustomObject</span></span>

```powershell
$user = [ADSI]"LDAP://CN=username,CN=Users,DC=domain,DC=com"
ConvertFrom-SddlString $user.psbase.ObjectSecurity.Sddl -Type ActiveDirectoryRights
```

<span data-ttu-id="dd716-125">첫 번째 명령은 ADSI (Active Directory 서비스 인터페이스)를 사용 하 여 사용자 개체를 가져온 다음 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-125">The first command uses Active Directory Service Interfaces (ADSI) to get the user object and saves it in the variable.</span></span>

<span data-ttu-id="dd716-126">두 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SddlString` 보안 설명자를 나타내는 개체의 sddl 속성에 포함 된 sddl 문자열의 텍스트 표현을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-126">The second command uses the `ConvertFrom-SddlString` cmdlet to get text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="dd716-127">매개 변수를 사용 하 여 `-Type` SDDL 문자열이 Active Directory 보안 설명자를 나타내도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-127">It uses the `-Type` parameter to specify that SDDL string represents an Active Directory security descriptor.</span></span>

## <span data-ttu-id="dd716-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dd716-128">PARAMETERS</span></span>

### <span data-ttu-id="dd716-129">-Sddl</span><span class="sxs-lookup"><span data-stu-id="dd716-129">-Sddl</span></span>

<span data-ttu-id="dd716-130">SDDL 구문에서 보안 설명자를 나타내는 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-130">Specifies the string representing the security descriptor in SDDL syntax.</span></span>

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

### <span data-ttu-id="dd716-131">-Type</span><span class="sxs-lookup"><span data-stu-id="dd716-131">-Type</span></span>

<span data-ttu-id="dd716-132">SDDL 문자열이 나타내는 권한 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-132">Specifies the type of rights that SDDL string represents.</span></span>

<span data-ttu-id="dd716-133">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-133">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="dd716-134">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="dd716-134">FileSystemRights</span></span>
- <span data-ttu-id="dd716-135">RegistryRights</span><span class="sxs-lookup"><span data-stu-id="dd716-135">RegistryRights</span></span>
- <span data-ttu-id="dd716-136">ActiveDirectoryRights</span><span class="sxs-lookup"><span data-stu-id="dd716-136">ActiveDirectoryRights</span></span>
- <span data-ttu-id="dd716-137">MutexRights</span><span class="sxs-lookup"><span data-stu-id="dd716-137">MutexRights</span></span>
- <span data-ttu-id="dd716-138">SemaphoreRights</span><span class="sxs-lookup"><span data-stu-id="dd716-138">SemaphoreRights</span></span>
- <span data-ttu-id="dd716-139">CryptoKeyRights</span><span class="sxs-lookup"><span data-stu-id="dd716-139">CryptoKeyRights</span></span>
- <span data-ttu-id="dd716-140">EventWaitHandleRights</span><span class="sxs-lookup"><span data-stu-id="dd716-140">EventWaitHandleRights</span></span>

<span data-ttu-id="dd716-141">기본적으로 cmdlet은 파일 시스템 권한을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-141">By default cmdlet uses file system rights.</span></span>

<span data-ttu-id="dd716-142">CryptoKeyRights 및 ActiveDirectoryRights는 PowerShell Core에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd716-142">CryptoKeyRights and ActiveDirectoryRights are not supported in PowerShell Core.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:
Accepted values: FileSystemRights, RegistryRights, ActiveDirectoryRights, MutexRights, SemaphoreRights, CryptoKeyRights, EventWaitHandleRights

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd716-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dd716-143">CommonParameters</span></span>
<span data-ttu-id="dd716-144">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dd716-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dd716-145">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd716-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dd716-146">입력</span><span class="sxs-lookup"><span data-stu-id="dd716-146">INPUTS</span></span>

### <span data-ttu-id="dd716-147">System.String</span><span class="sxs-lookup"><span data-stu-id="dd716-147">System.String</span></span>

<span data-ttu-id="dd716-148">SDDL 문자열을로 파이프 할 수 있습니다 `ConvertFrom-SddlString` .</span><span class="sxs-lookup"><span data-stu-id="dd716-148">You can pipe a SDDL string to `ConvertFrom-SddlString`.</span></span>

## <span data-ttu-id="dd716-149">출력</span><span class="sxs-lookup"><span data-stu-id="dd716-149">OUTPUTS</span></span>

## <span data-ttu-id="dd716-150">참고</span><span class="sxs-lookup"><span data-stu-id="dd716-150">NOTES</span></span>

## <span data-ttu-id="dd716-151">관련 링크</span><span class="sxs-lookup"><span data-stu-id="dd716-151">RELATED LINKS</span></span>

[<span data-ttu-id="dd716-152">보안 설명자 정의 언어</span><span class="sxs-lookup"><span data-stu-id="dd716-152">Security Descriptor Definition Language</span></span>](/windows/win32/secauthz/security-descriptor-definition-language)

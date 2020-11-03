---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-acl?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Acl
ms.openlocfilehash: a4c25d199b97be24277092bcb815a640a09360dd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212361"
---
# <span data-ttu-id="1e7c8-103">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="1e7c8-103">Set-Acl</span></span>

## <span data-ttu-id="1e7c8-104">개요</span><span class="sxs-lookup"><span data-stu-id="1e7c8-104">SYNOPSIS</span></span>
<span data-ttu-id="1e7c8-105">파일 또는 레지스트리 키와 같은 지정한 항목의 보안 설명자를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-105">Changes the security descriptor of a specified item, such as a file or a registry key.</span></span>

## <span data-ttu-id="1e7c8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1e7c8-106">SYNTAX</span></span>

### <span data-ttu-id="1e7c8-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="1e7c8-107">ByPath (Default)</span></span>

```
Set-Acl [-Path] <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1e7c8-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="1e7c8-108">ByInputObject</span></span>

```
Set-Acl [-InputObject] <PSObject> [-AclObject] <Object> [-Passthru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1e7c8-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="1e7c8-109">ByLiteralPath</span></span>

```
Set-Acl -LiteralPath <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1e7c8-110">설명</span><span class="sxs-lookup"><span data-stu-id="1e7c8-110">DESCRIPTION</span></span>

<span data-ttu-id="1e7c8-111">`Set-Acl`Cmdlet은 파일 또는 레지스트리 키와 같은 지정 된 항목의 보안 설명자를 사용자가 제공 하는 보안 설명자의 값과 일치 하도록 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-111">The `Set-Acl` cmdlet changes the security descriptor of a specified item, such as a file or a registry key, to match the values in a security descriptor that you supply.</span></span>

<span data-ttu-id="1e7c8-112">를 사용 하려면 `Set-Acl` **Path** 또는 **InputObject** 매개 변수를 사용 하 여 보안 설명자를 변경 하려는 항목을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-112">To use `Set-Acl`, use the **Path** or **InputObject** parameter to identify the item whose security descriptor you want to change.</span></span> <span data-ttu-id="1e7c8-113">그다음에 **AclObject** 또는 **SecurityDescriptor** 매개 변수를 사용하여 적용할 값이 포함된 보안 설명자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-113">Then, use the **AclObject** or **SecurityDescriptor** parameters to supply a security descriptor that has the values you want to apply.</span></span> <span data-ttu-id="1e7c8-114">`Set-Acl` 제공 된 보안 설명자를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-114">`Set-Acl` applies the security descriptor that is supplied.</span></span> <span data-ttu-id="1e7c8-115">**AclObject** 매개 변수 값을 모델로 사용하고 항목의 보안 설명자 값을 **AclObject** 매개 변수 값과 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-115">It uses the value of the **AclObject** parameter as a model and changes the values in the item's security descriptor to match the values in the **AclObject** parameter.</span></span>

## <span data-ttu-id="1e7c8-116">예제</span><span class="sxs-lookup"><span data-stu-id="1e7c8-116">EXAMPLES</span></span>

### <span data-ttu-id="1e7c8-117">예제 1: 한 파일에서 다른 파일로 보안 설명자 복사</span><span class="sxs-lookup"><span data-stu-id="1e7c8-117">Example 1: Copy a security descriptor from one file to another</span></span>

```powershell
$DogACL = Get-Acl -Path "C:\Dog.txt"
Set-Acl -Path "C:\Cat.txt" -AclObject $DogACL
```

<span data-ttu-id="1e7c8-118">이 명령은 Dog.txt 파일의 보안 설명자 값을 Cat.txt 파일의 보안 설명자로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-118">These commands copy the values from the security descriptor of the Dog.txt file to the security descriptor of the Cat.txt file.</span></span> <span data-ttu-id="1e7c8-119">명령이 완료되면 Dog.txt 파일과 Cat.txt 파일의 보안 설명자가 동일해집니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-119">When the commands complete, the security descriptors of the Dog.txt and Cat.txt files are identical.</span></span>

<span data-ttu-id="1e7c8-120">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` Dog.txt 파일의 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-120">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>
<span data-ttu-id="1e7c8-121">할당 연산자 ( `=` )는 $DogACL 변수의 값에 보안 설명자를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-121">The assignment operator (`=`) stores the security descriptor in the value of the $DogACL variable.</span></span>

<span data-ttu-id="1e7c8-122">두 번째 명령은를 사용 하 여 `Set-Acl` Cat.txt ACL의 값을의 값으로 변경 합니다 `$DogACL` .</span><span class="sxs-lookup"><span data-stu-id="1e7c8-122">The second command uses `Set-Acl` to change the values in the ACL of Cat.txt to the values in `$DogACL`.</span></span>

<span data-ttu-id="1e7c8-123">**Path** 매개 변수 값은 Cat.txt 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-123">The value of the **Path** parameter is the path to the Cat.txt file.</span></span> <span data-ttu-id="1e7c8-124">**Aclob** 의 매개 변수 값은 모델 acl (이 경우 변수에 저장 된 Dog.txt의 acl)입니다 `$DogACL` .</span><span class="sxs-lookup"><span data-stu-id="1e7c8-124">The value of the **AclObject** parameter is the model ACL, in this case, the ACL of Dog.txt as saved in the `$DogACL` variable.</span></span>

### <span data-ttu-id="1e7c8-125">예제 2: 파이프라인 연산자를 사용 하 여 설명자 전달</span><span class="sxs-lookup"><span data-stu-id="1e7c8-125">Example 2: Use the pipeline operator to pass a descriptor</span></span>

```powershell
Get-Acl -Path "C:\Dog.txt" | Set-Acl -Path "C:\Cat.txt"
```

<span data-ttu-id="1e7c8-126">이 명령은 파이프라인 연산자 ()를 사용 하 여 명령 `|` 에서 명령으로 보안 설명자를 보내는 것을 제외 하 고는 이전 예제의 명령과 거의 같습니다 `Get-Acl` `Set-Acl` .</span><span class="sxs-lookup"><span data-stu-id="1e7c8-126">This command is almost the same as the command in the previous example, except that it uses a pipeline operator (`|`) to send the security descriptor from a `Get-Acl` command to a `Set-Acl` command.</span></span>

<span data-ttu-id="1e7c8-127">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` Dog.txt 파일의 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-127">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span> <span data-ttu-id="1e7c8-128">파이프라인 연산자 ( `|` )는 Dog.txt 보안 설명자를 나타내는 개체를 cmdlet으로 전달 합니다 `Set-Acl` .</span><span class="sxs-lookup"><span data-stu-id="1e7c8-128">The pipeline operator (`|`) passes an object that represents the Dog.txt security descriptor to the `Set-Acl` cmdlet.</span></span>

<span data-ttu-id="1e7c8-129">두 번째 명령은를 사용 하 여 `Set-Acl` Cat.txt에 Dog.txt의 보안 설명자를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-129">The second command uses `Set-Acl` to apply the security descriptor of Dog.txt to Cat.txt.</span></span>
<span data-ttu-id="1e7c8-130">명령이 완료되면 Dog.txt 파일과 Cat.txt 파일의 ACL이 동일해집니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-130">When the command completes, the ACLs of the Dog.txt and Cat.txt files are identical.</span></span>

### <span data-ttu-id="1e7c8-131">예제 3: 여러 파일에 보안 설명자 적용</span><span class="sxs-lookup"><span data-stu-id="1e7c8-131">Example 3: Apply a security descriptor to multiple files</span></span>

```powershell
$NewAcl = Get-Acl File0.txt
Get-ChildItem -Path "C:\temp" -Recurse -Include "*.txt" -Force | Set-Acl -AclObject $NewAcl
```

<span data-ttu-id="1e7c8-132">이러한 명령은 File0.txt 파일의 보안 설명자를 `C:\Temp` 디렉터리와 모든 하위 디렉터리의 모든 텍스트 파일에 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-132">These commands apply the security descriptors in the File0.txt file to all text files in the `C:\Temp` directory and all of its subdirectories.</span></span>

<span data-ttu-id="1e7c8-133">첫 번째 명령은 현재 디렉터리에 있는 File0.txt 파일의 보안 설명자를 가져와 대입 연산자 ()를 사용 하 여 `=` 변수에 저장 합니다 `$NewACL` .</span><span class="sxs-lookup"><span data-stu-id="1e7c8-133">The first command gets the security descriptor of the File0.txt file in the current directory and uses the assignment operator (`=`) to store it in the `$NewACL` variable.</span></span>

<span data-ttu-id="1e7c8-134">파이프라인의 첫 번째 명령은 Get-ChildItem cmdlet을 사용 하 여 디렉터리에 있는 모든 텍스트 파일을 가져옵니다 `C:\Temp` .</span><span class="sxs-lookup"><span data-stu-id="1e7c8-134">The first command in the pipeline uses the Get-ChildItem cmdlet to get all of the text files in the `C:\Temp` directory.</span></span> <span data-ttu-id="1e7c8-135">**재귀** 매개 변수는 명령을의 모든 하위 디렉터리에 확장 `C:\temp` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-135">The **Recurse** parameter extends the command to all subdirectories of `C:\temp`.</span></span> <span data-ttu-id="1e7c8-136">**Include** 매개 변수는 검색 된 파일을 파일 이름 확장명을 가진 파일로 제한 합니다 `.txt` .</span><span class="sxs-lookup"><span data-stu-id="1e7c8-136">The **Include** parameter limits the files retrieved to those with the `.txt` file name extension.</span></span> <span data-ttu-id="1e7c8-137">**Force** 매개 변수는 이 매개 변수가 없을 경우 제외되는 숨겨진 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-137">The **Force** parameter gets hidden files, which would otherwise be excluded.</span></span> <span data-ttu-id="1e7c8-138">`c:\temp\*.txt` **재귀적** 매개 변수는 파일이 아니라 디렉터리에서 작동 하므로를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-138">(You cannot use `c:\temp\*.txt`, because the **Recurse** parameter works on directories, not on files.)</span></span>

<span data-ttu-id="1e7c8-139">파이프라인 연산자 ( `|` )는 검색 된 파일을 나타내는 개체를 cmdlet에 보냅니다 `Set-Acl` .이 개체는 파이프라인의 모든 파일에 **aclob** 매개 변수의 보안 설명자를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-139">The pipeline operator (`|`) sends the objects representing the retrieved files to the `Set-Acl` cmdlet, which applies the security descriptor in the **AclObject** parameter to all of the files in the pipeline.</span></span>

<span data-ttu-id="1e7c8-140">실제로 두 개 **WhatIf** `Set-Acl` 이상의 항목에 영향을 줄 수 있는 모든 명령에는 WhatIf 매개 변수를 사용 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-140">In practice, it is best to use the **WhatIf** parameter with all `Set-Acl` commands that can affect more than one item.</span></span> <span data-ttu-id="1e7c8-141">이 경우 파이프라인의 두 번째 명령은 `Set-Acl -AclObject $NewAcl -WhatIf` 입니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-141">In this case, the second command in the pipeline would be `Set-Acl -AclObject $NewAcl -WhatIf`.</span></span> <span data-ttu-id="1e7c8-142">이 명령은 영향을 받을 수 있는 파일을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-142">This command lists the files that would be affected by the command.</span></span> <span data-ttu-id="1e7c8-143">결과를 검토 한 후에는 **WhatIf** 매개 변수 없이 명령을 다시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-143">After reviewing the result, you can run the command again without the **WhatIf** parameter.</span></span>

### <span data-ttu-id="1e7c8-144">예제 4: 상속 해제 및 상속 된 액세스 규칙 유지</span><span class="sxs-lookup"><span data-stu-id="1e7c8-144">Example 4: Disable inheritance and preserve inherited access rules</span></span>

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
$isProtected = $true
$preserveInheritance = $true
$NewAcl.SetAccessRuleProtection($isProtected, $preserveInheritance)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

<span data-ttu-id="1e7c8-145">이러한 명령은 상속 된 기존 액세스 규칙을 그대로 유지 하면서 부모 폴더에서 액세스 상속을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-145">These commands is will disable access inheritance from parent folders, while still preserving the existing inherited access rules.</span></span>

<span data-ttu-id="1e7c8-146">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` Dog.txt 파일의 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-146">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>

<span data-ttu-id="1e7c8-147">그런 다음, 상속 된 액세스 규칙을 명시적 액세스 규칙으로 변환 하기 위해 변수가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-147">Next, variables are created to convert the inherited access rules to explicit access rules.</span></span> <span data-ttu-id="1e7c8-148">이와 연결 된 액세스 규칙을 상속 으로부터 보호 하려면 변수를 `$isProtected` 로 설정 `$true` 합니다. 상속을 허용 하려면를 `$isProtected` 로 설정 `$false` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-148">To protect the access rules associated with this from inheritance, set the `$isProtected` variable to `$true`.to allow inheritance, set `$isProtected` to `$false`.</span></span> <span data-ttu-id="1e7c8-149">자세한 내용은 [액세스 규칙 보호 설정](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-149">For more information, see [set access rule protection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection).</span></span>
<span data-ttu-id="1e7c8-150">`$preserveInheritance` `$true` 상속 된 액세스 규칙을 유지 하기 위해로 설정 된 변수입니다. 상속 된 액세스 규칙을 제거 하려면 false입니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-150">The `$preserveInheritance` variable set to `$true` to preserve inherited access rules; false to remove inherited access rules.</span></span> <span data-ttu-id="1e7c8-151">그런 다음 **Setaccessruleprotection ()** 메서드를 사용 하 여 액세스 규칙 보호를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-151">Then the access rule protection is updated using the **SetAccessRuleProtection()** method.</span></span>

<span data-ttu-id="1e7c8-152">마지막 명령은를 사용 하 여 `Set-Acl` Dog.txt에의 보안 설명자를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-152">The last command uses `Set-Acl` to apply the security descriptor of to Dog.txt.</span></span> <span data-ttu-id="1e7c8-153">명령이 완료 되 면 애완 동물 폴더에서 상속 된 Dog.txt의 Acl이 Dog.txt에 직접 적용 되 고, 애완 동물에 추가 된 새 액세스 정책이 Dog.txt에 대 한 액세스를 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-153">When the command completes, the ACLs of the Dog.txt that were inherited from the Pets folder will be applied directly to Dog.txt, and new access policies added to Pets will not change the access to Dog.txt.</span></span>

### <span data-ttu-id="1e7c8-154">예 5: 관리자에 게 파일에 대 한 모든 권한 부여</span><span class="sxs-lookup"><span data-stu-id="1e7c8-154">Example 5: Grant Administrators Full Control of the file</span></span>

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
# Set properties
$identity = "BUILTIN\Administrators"
$fileSystemRights = "FullControl"
$type = "Allow"
# Create new rule
$fileSystemAccessRuleArgumentList = $identity, $fileSystemRights, $type
$fileSystemAccessRule = New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule -ArgumentList $fileSystemAccessRuleArgumentList
# Apply new rule
$NewAcl.SetAccessRule($fileSystemAccessRule)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

<span data-ttu-id="1e7c8-155">이 명령은 **BUILTIN\Administrators** 그룹에 Dog.txt 파일에 대 한 모든 권한을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-155">This command will grant the **BUILTIN\Administrators** group Full control of the Dog.txt file.</span></span>

<span data-ttu-id="1e7c8-156">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` Dog.txt 파일의 보안 설명자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-156">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>

<span data-ttu-id="1e7c8-157">다음 변수는 **BUILTIN\Administrators** 그룹에 Dog.txt 파일에 대 한 모든 권한을 부여 하기 위해 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-157">Next variables are created to grant the **BUILTIN\Administrators** group full control of the Dog.txt file.</span></span> <span data-ttu-id="1e7c8-158">`$identity` [사용자 계정](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)이름으로 설정 된 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-158">The `$identity` variable set to the name of a [user account](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor).</span></span>
<span data-ttu-id="1e7c8-159">`$fileSystemRights`FullControl로 설정 된 변수는 액세스 규칙에 연결 된 작업 유형을 지정 하는 [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) 값 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-159">The `$fileSystemRights` variable set to FullControl, and can be any one of the [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) values that specifies the type of operation associated with the access rule.</span></span> <span data-ttu-id="1e7c8-160">`$type`"Allow"로 설정 된 변수는 작업을 허용할지 또는 거부할지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-160">The `$type` variable set to "Allow" to specifies whether to allow or deny the operation.</span></span> <span data-ttu-id="1e7c8-161">`$fileSystemAccessRuleArgumentList`변수는 새 **FileSystemAccessRule** 개체를 만들 때 전달 되는 인수 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-161">The `$fileSystemAccessRuleArgumentList` variable is an argument list is to be passed when making the new **FileSystemAccessRule** object.</span></span> <span data-ttu-id="1e7c8-162">그런 다음 새 **FileSystemAccessRule** 개체를 만들고 **FileSystemAccessRule** 개체가 **setaccessrule ()** 메서드에 전달 되 고 새 액세스 규칙을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-162">Then a new **FileSystemAccessRule** object is created, and the **FileSystemAccessRule** object is passed to the **SetAccessRule()** method, adds the new access rule.</span></span>

<span data-ttu-id="1e7c8-163">마지막 명령은를 사용 하 여 `Set-Acl` Dog.txt에의 보안 설명자를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-163">The last command uses `Set-Acl` to apply the security descriptor of to Dog.txt.</span></span>
<span data-ttu-id="1e7c8-164">명령이 완료 되 면 **BUILTIN\Administrators** 그룹은 Dog.txt에 대 한 모든 권한을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-164">When the command completes, the **BUILTIN\Administrators** group will have full control of the Dog.txt.</span></span>

## <span data-ttu-id="1e7c8-165">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1e7c8-165">PARAMETERS</span></span>

### <span data-ttu-id="1e7c8-166">-Aclob</span><span class="sxs-lookup"><span data-stu-id="1e7c8-166">-AclObject</span></span>

<span data-ttu-id="1e7c8-167">원하는 속성 값이 있는 ACL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-167">Specifies an ACL with the desired property values.</span></span> <span data-ttu-id="1e7c8-168">`Set-Acl`**Path** 또는 **InputObject** 매개 변수에 지정 된 항목의 ACL을 지정 된 보안 개체의 값과 일치 하도록 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-168">`Set-Acl` changes the ACL of item specified by the **Path** or **InputObject** parameter to match the values in the specified security object.</span></span>

<span data-ttu-id="1e7c8-169">명령의 출력을 변수에 저장 한 `Get-Acl` 다음 **aclob** 매개 변수를 사용 하 여 변수를 전달 하거나 명령을 입력할 수 있습니다 `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="1e7c8-169">You can save the output of a `Get-Acl` command in a variable and then use the **AclObject** parameter to pass the variable, or type a `Get-Acl` command.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1e7c8-170">-ClearCentralAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="1e7c8-170">-ClearCentralAccessPolicy</span></span>

<span data-ttu-id="1e7c8-171">지정한 항목에서 중앙 액세스 정책을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-171">Removes the central access policy from the specified item.</span></span>

<span data-ttu-id="1e7c8-172">Windows Server 2012부터 관리자는 Active Directory 및 그룹 정책를 사용 하 여 사용자 및 그룹에 대 한 중앙 액세스 정책을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-172">Beginning in Windows Server 2012, administrators can use Active Directory and Group Policy to set central access policies for users and groups.</span></span> <span data-ttu-id="1e7c8-173">자세한 내용은 [동적 Access Control: 시나리오 개요](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-173">For more information, see [Dynamic Access Control: Scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span></span>

<span data-ttu-id="1e7c8-174">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-174">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByPath, ByLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e7c8-175">-제외</span><span class="sxs-lookup"><span data-stu-id="1e7c8-175">-Exclude</span></span>

<span data-ttu-id="1e7c8-176">지정된 항목을 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-176">Omits the specified items.</span></span> <span data-ttu-id="1e7c8-177">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-177">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1e7c8-178">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-178">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1e7c8-179">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-179">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1e7c8-180">-Filter</span><span class="sxs-lookup"><span data-stu-id="1e7c8-180">-Filter</span></span>

<span data-ttu-id="1e7c8-181">공급자의 형식 또는 언어에 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-181">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="1e7c8-182">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-182">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1e7c8-183">와일드카드 사용을 포함한 필터 구문은 공급자에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-183">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="1e7c8-184">필터는 개체가 검색 된 후 개체를 검색 한 후 개체를 검색 하는 대신 개체를 검색할 때 필터를 적용 하기 때문에 다른 매개 변수 보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-184">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1e7c8-185">-포함</span><span class="sxs-lookup"><span data-stu-id="1e7c8-185">-Include</span></span>

<span data-ttu-id="1e7c8-186">지정된 항목만 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-186">Changes only the specified items.</span></span> <span data-ttu-id="1e7c8-187">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-187">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="1e7c8-188">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-188">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1e7c8-189">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-189">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1e7c8-190">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1e7c8-190">-InputObject</span></span>

<span data-ttu-id="1e7c8-191">지정한 개체의 보안 설명자를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-191">Changes the security descriptor of the specified object.</span></span> <span data-ttu-id="1e7c8-192">개체가 포함된 변수 또는 개체를 가져오는 명령을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-192">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="1e7c8-193">변경할 개체를로 파이프 할 수 없습니다 `Set-Acl` .</span><span class="sxs-lookup"><span data-stu-id="1e7c8-193">You cannot pipe the object to be changed to `Set-Acl`.</span></span> <span data-ttu-id="1e7c8-194">대신 명령에서 **InputObject** 매개 변수를 명시적으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-194">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="1e7c8-195">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-195">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1e7c8-196">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1e7c8-196">-LiteralPath</span></span>

<span data-ttu-id="1e7c8-197">지정한 항목의 보안 설명자를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-197">Changes the security descriptor of the specified item.</span></span> <span data-ttu-id="1e7c8-198">**Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-198">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="1e7c8-199">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-199">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1e7c8-200">경로에 이스케이프 문자가 포함 된 경우이를 작은따옴표 ()로 묶습니다 `'` .</span><span class="sxs-lookup"><span data-stu-id="1e7c8-200">If the path includes escape characters, enclose it in single quotation marks (`'`).</span></span>
<span data-ttu-id="1e7c8-201">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-201">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="1e7c8-202">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1e7c8-203">-Passthru</span><span class="sxs-lookup"><span data-stu-id="1e7c8-203">-Passthru</span></span>

<span data-ttu-id="1e7c8-204">변경된 보안 설명자를 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-204">Returns an object that represents the security descriptor that was changed.</span></span> <span data-ttu-id="1e7c8-205">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-205">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e7c8-206">-Path</span><span class="sxs-lookup"><span data-stu-id="1e7c8-206">-Path</span></span>

<span data-ttu-id="1e7c8-207">지정한 항목의 보안 설명자를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-207">Changes the security descriptor of the specified item.</span></span> <span data-ttu-id="1e7c8-208">파일 또는 레지스트리 키의 경로와 같은 항목의 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-208">Enter the path to an item, such as a path to a file or registry key.</span></span> <span data-ttu-id="1e7c8-209">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-209">Wildcards are permitted.</span></span>

<span data-ttu-id="1e7c8-210">SecurityDescriptor 매개 변수를 사용 하거나 보안 개체를에 Get-Acl 전달 하 여 보안 개체를에 전달 하는 경우 ( `Set-Acl` **AclObject** **SecurityDescriptor** `Set-Acl` 이름 및 값) **경로** 매개 변수 (이름 및 값)를 생략 하면에서 `Set-Acl` 보안 개체에 포함 된 경로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-210">If you pass a security object to `Set-Acl` (either by using the **AclObject** or **SecurityDescriptor** parameters or by passing a security object from Get-Acl to `Set-Acl`), and you omit the **Path** parameter (name and value), `Set-Acl` uses the path that is included in the security object.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="1e7c8-211">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1e7c8-211">-Confirm</span></span>

<span data-ttu-id="1e7c8-212">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-212">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1e7c8-213">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1e7c8-213">-WhatIf</span></span>

<span data-ttu-id="1e7c8-214">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-214">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1e7c8-215">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-215">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1e7c8-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1e7c8-216">CommonParameters</span></span>

<span data-ttu-id="1e7c8-217">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-217">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1e7c8-218">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-218">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1e7c8-219">입력</span><span class="sxs-lookup"><span data-stu-id="1e7c8-219">INPUTS</span></span>

### <span data-ttu-id="1e7c8-220">Accesscontrol-namespace. Accesscontrol-namespace. CommonSecurityDescriptor에 대 한</span><span class="sxs-lookup"><span data-stu-id="1e7c8-220">System.Security.AccessControl.ObjectSecurity, System.Security.AccessControl.CommonSecurityDescriptor</span></span>

<span data-ttu-id="1e7c8-221">ACL 개체 또는 보안 설명자를로 파이프 할 수 있습니다 `Set-Acl` .</span><span class="sxs-lookup"><span data-stu-id="1e7c8-221">You can pipe an ACL object or a security descriptor to `Set-Acl`.</span></span>

## <span data-ttu-id="1e7c8-222">출력</span><span class="sxs-lookup"><span data-stu-id="1e7c8-222">OUTPUTS</span></span>

### <span data-ttu-id="1e7c8-223">Accesscontrol-namespace. System.security.accesscontrol.filesecurity</span><span class="sxs-lookup"><span data-stu-id="1e7c8-223">System.Security.AccessControl.FileSecurity</span></span>

<span data-ttu-id="1e7c8-224">기본적으로는 `Set-Acl` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-224">By default, `Set-Acl` does not generate any output.</span></span>
<span data-ttu-id="1e7c8-225">그러나 **Passthru** 매개 변수를 사용할 경우 보안 개체를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-225">However, if you use the **Passthru** parameter, it generates a security object.</span></span>
<span data-ttu-id="1e7c8-226">보안 개체 유형은 항목 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-226">The type of the security object depends on the type of the item.</span></span>

## <span data-ttu-id="1e7c8-227">참고</span><span class="sxs-lookup"><span data-stu-id="1e7c8-227">NOTES</span></span>

 <span data-ttu-id="1e7c8-228">`Set-Acl`Cmdlet은 PowerShell 파일 시스템 및 레지스트리 공급자에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-228">The `Set-Acl` cmdlet is supported by the PowerShell file system and registry providers.</span></span> <span data-ttu-id="1e7c8-229">따라서 Set-Acl cmdlet을 사용하여 파일, 디렉터리 및 레지스트리 키의 보안 설명자를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e7c8-229">As such, you can use it to change the security descriptors of files, directories, and registry keys.</span></span>

## <span data-ttu-id="1e7c8-230">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1e7c8-230">RELATED LINKS</span></span>

[<span data-ttu-id="1e7c8-231">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="1e7c8-231">Get-Acl</span></span>](Get-Acl.md)

[<span data-ttu-id="1e7c8-232">FileSystemAccessRule</span><span class="sxs-lookup"><span data-stu-id="1e7c8-232">FileSystemAccessRule</span></span>](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)

[<span data-ttu-id="1e7c8-233">ObjectSecurity. SetAccessRuleProtection</span><span class="sxs-lookup"><span data-stu-id="1e7c8-233">ObjectSecurity.SetAccessRuleProtection</span></span>](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)

[<span data-ttu-id="1e7c8-234">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="1e7c8-234">FileSystemRights</span></span>](/dotnet/api/system.security.accesscontrol.filesystemrights)

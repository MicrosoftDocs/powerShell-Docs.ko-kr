---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-acl?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Acl
ms.openlocfilehash: 56a9625a42062cf787f0c92aaa319a0a344b5919
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342538"
---
# Set-Acl

## 개요
파일 또는 레지스트리 키와 같은 지정한 항목의 보안 설명자를 변경합니다.

## SYNTAX

### ByPath (기본값)

```
Set-Acl [-Path] <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByInputObject

```
Set-Acl [-InputObject] <PSObject> [-AclObject] <Object> [-Passthru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Set-Acl -LiteralPath <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Set-Acl`Cmdlet은 파일 또는 레지스트리 키와 같은 지정 된 항목의 보안 설명자를 사용자가 제공 하는 보안 설명자의 값과 일치 하도록 변경 합니다.

를 사용 하려면 `Set-Acl` **Path** 또는 **InputObject** 매개 변수를 사용 하 여 보안 설명자를 변경 하려는 항목을 식별 합니다. 그다음에 **AclObject** 또는 **SecurityDescriptor** 매개 변수를 사용하여 적용할 값이 포함된 보안 설명자를 제공합니다. `Set-Acl` 제공 된 보안 설명자를 적용 합니다. **AclObject** 매개 변수 값을 모델로 사용하고 항목의 보안 설명자 값을 **AclObject** 매개 변수 값과 일치하도록 변경합니다.

## 예제

### 예제 1: 한 파일에서 다른 파일로 보안 설명자 복사

```powershell
$DogACL = Get-Acl -Path "C:\Dog.txt"
Set-Acl -Path "C:\Cat.txt" -AclObject $DogACL
```

이 명령은 Dog.txt 파일의 보안 설명자 값을 Cat.txt 파일의 보안 설명자로 복사합니다. 명령이 완료되면 Dog.txt 파일과 Cat.txt 파일의 보안 설명자가 동일해집니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` Dog.txt 파일의 보안 설명자를 가져옵니다.
할당 연산자 ( `=` )는 $DogACL 변수의 값에 보안 설명자를 저장 합니다.

두 번째 명령은를 사용 하 여 `Set-Acl` Cat.txt ACL의 값을의 값으로 변경 합니다 `$DogACL` .

**Path** 매개 변수 값은 Cat.txt 파일의 경로입니다. **Aclob** 의 매개 변수 값은 모델 acl (이 경우 변수에 저장 된 Dog.txt의 acl)입니다 `$DogACL` .

### 예제 2: 파이프라인 연산자를 사용 하 여 설명자 전달

```powershell
Get-Acl -Path "C:\Dog.txt" | Set-Acl -Path "C:\Cat.txt"
```

이 명령은 파이프라인 연산자 ()를 사용 하 여 명령 `|` 에서 명령으로 보안 설명자를 보내는 것을 제외 하 고는 이전 예제의 명령과 거의 같습니다 `Get-Acl` `Set-Acl` .

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` Dog.txt 파일의 보안 설명자를 가져옵니다. 파이프라인 연산자 ( `|` )는 Dog.txt 보안 설명자를 나타내는 개체를 cmdlet으로 전달 합니다 `Set-Acl` .

두 번째 명령은를 사용 하 여 `Set-Acl` Cat.txt에 Dog.txt의 보안 설명자를 적용 합니다.
명령이 완료되면 Dog.txt 파일과 Cat.txt 파일의 ACL이 동일해집니다.

### 예제 3: 여러 파일에 보안 설명자 적용

```powershell
$NewAcl = Get-Acl File0.txt
Get-ChildItem -Path "C:\temp" -Recurse -Include "*.txt" -Force | Set-Acl -AclObject $NewAcl
```

이러한 명령은 File0.txt 파일의 보안 설명자를 `C:\Temp` 디렉터리와 모든 하위 디렉터리의 모든 텍스트 파일에 적용 합니다.

첫 번째 명령은 현재 디렉터리에 있는 File0.txt 파일의 보안 설명자를 가져와 대입 연산자 ()를 사용 하 여 `=` 변수에 저장 합니다 `$NewACL` .

파이프라인의 첫 번째 명령은 Get-ChildItem cmdlet을 사용 하 여 디렉터리에 있는 모든 텍스트 파일을 가져옵니다 `C:\Temp` . **재귀** 매개 변수는 명령을의 모든 하위 디렉터리에 확장 `C:\temp` 합니다. **Include** 매개 변수는 검색 된 파일을 파일 이름 확장명을 가진 파일로 제한 합니다 `.txt` . **Force** 매개 변수는 이 매개 변수가 없을 경우 제외되는 숨겨진 파일을 가져옵니다. `c:\temp\*.txt` **재귀적** 매개 변수는 파일이 아니라 디렉터리에서 작동 하므로를 사용할 수 없습니다.

파이프라인 연산자 ( `|` )는 검색 된 파일을 나타내는 개체를 cmdlet에 보냅니다 `Set-Acl` .이 개체는 파이프라인의 모든 파일에 **aclob** 매개 변수의 보안 설명자를 적용 합니다.

실제로 두 개 **WhatIf** `Set-Acl` 이상의 항목에 영향을 줄 수 있는 모든 명령에는 WhatIf 매개 변수를 사용 하는 것이 가장 좋습니다. 이 경우 파이프라인의 두 번째 명령은 `Set-Acl -AclObject $NewAcl -WhatIf` 입니다. 이 명령은 영향을 받을 수 있는 파일을 나열합니다. 결과를 검토 한 후에는 **WhatIf** 매개 변수 없이 명령을 다시 실행할 수 있습니다.

### 예제 4: 상속 해제 및 상속 된 액세스 규칙 유지

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
$isProtected = $true
$preserveInheritance = $true
$NewAcl.SetAccessRuleProtection($isProtected, $preserveInheritance)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

이러한 명령은 상속 된 기존 액세스 규칙을 그대로 유지 하면서 부모 폴더에서 액세스 상속을 사용 하지 않도록 설정 합니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` Dog.txt 파일의 보안 설명자를 가져옵니다.

그런 다음, 상속 된 액세스 규칙을 명시적 액세스 규칙으로 변환 하기 위해 변수가 만들어집니다. 이와 연결 된 액세스 규칙을 상속 으로부터 보호 하려면 변수를 `$isProtected` 로 설정 `$true` 합니다. 상속을 허용 하려면를 `$isProtected` 로 설정 `$false` 합니다. 자세한 내용은 [액세스 규칙 보호 설정](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)을 참조 하세요.
`$preserveInheritance` `$true` 상속 된 액세스 규칙을 유지 하기 위해로 설정 된 변수입니다. 상속 된 액세스 규칙을 제거 하려면 false입니다. 그런 다음 **Setaccessruleprotection ()** 메서드를 사용 하 여 액세스 규칙 보호를 업데이트 합니다.

마지막 명령은를 사용 하 여 `Set-Acl` Dog.txt에의 보안 설명자를 적용 합니다. 명령이 완료 되 면 애완 동물 폴더에서 상속 된 Dog.txt의 Acl이 Dog.txt에 직접 적용 되 고, 애완 동물에 추가 된 새 액세스 정책이 Dog.txt에 대 한 액세스를 변경 하지 않습니다.

### 예 5: 관리자에 게 파일에 대 한 모든 권한 부여

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

이 명령은 **BUILTIN\Administrators** 그룹에 Dog.txt 파일에 대 한 모든 권한을 부여 합니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Acl` Dog.txt 파일의 보안 설명자를 가져옵니다.

다음 변수는 **BUILTIN\Administrators** 그룹에 Dog.txt 파일에 대 한 모든 권한을 부여 하기 위해 생성 됩니다. `$identity` [사용자 계정](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)이름으로 설정 된 변수입니다. `$fileSystemRights`FullControl로 설정 된 변수는 액세스 규칙에 연결 된 작업 유형을 지정 하는 [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) 값 중 하나일 수 있습니다. `$type`"Allow"로 설정 된 변수는 작업을 허용할지 또는 거부할지를 지정 합니다. `$fileSystemAccessRuleArgumentList`변수는 새 **FileSystemAccessRule** 개체를 만들 때 전달 되는 인수 목록입니다. 그런 다음 새 **FileSystemAccessRule** 개체를 만들고 **FileSystemAccessRule** 개체가 **setaccessrule ()** 메서드에 전달 되 고 새 액세스 규칙을 추가 합니다.

마지막 명령은를 사용 하 여 `Set-Acl` Dog.txt에의 보안 설명자를 적용 합니다. 명령이 완료 되 면 **BUILTIN\Administrators** 그룹은 Dog.txt에 대 한 모든 권한을 갖게 됩니다.

## PARAMETERS

### -Aclob

원하는 속성 값이 있는 ACL을 지정합니다. `Set-Acl`**Path** 또는 **InputObject** 매개 변수에 지정 된 항목의 ACL을 지정 된 보안 개체의 값과 일치 하도록 변경 합니다.

명령의 출력을 변수에 저장 한 `Get-Acl` 다음 **aclob** 매개 변수를 사용 하 여 변수를 전달 하거나 명령을 입력할 수 있습니다 `Get-Acl` .

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

### -ClearCentralAccessPolicy

지정한 항목에서 중앙 액세스 정책을 제거합니다.

Windows Server 2012부터 관리자는 Active Directory 및 그룹 정책를 사용 하 여 사용자 및 그룹에 대 한 중앙 액세스 정책을 설정할 수 있습니다. 자세한 내용은 [동적 Access Control: 시나리오 개요](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview)를 참조 하세요.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

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

### -제외

지정된 항목을 생략합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다. 와일드카드가 지원됩니다.

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

### -Filter

공급자의 형식 또는 언어에 필터를 지정합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 와일드카드 사용을 포함한 필터 구문은 공급자에 따라 달라집니다. 필터는 개체가 검색 된 후 개체를 검색 한 후 개체를 검색 하는 대신 개체를 검색할 때 필터를 적용 하기 때문에 다른 매개 변수 보다 더 효율적입니다.

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

### -포함

지정된 항목만 변경합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다.
경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다. 와일드카드가 지원됩니다.

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

### -InputObject

지정한 개체의 보안 설명자를 변경합니다. 개체가 포함된 변수 또는 개체를 가져오는 명령을 입력하세요.

변경할 개체를로 파이프 할 수 없습니다 `Set-Acl` . 대신 명령에서 **InputObject** 매개 변수를 명시적으로 사용합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

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

### -LiteralPath

지정한 항목의 보안 설명자를 변경합니다. **Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 경로에 이스케이프 문자가 포함 된 경우이를 작은따옴표 ()로 묶습니다 `'` .
작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

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

### -Passthru

변경된 보안 설명자를 나타내는 개체를 반환합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -Path

지정한 항목의 보안 설명자를 변경합니다. 파일 또는 레지스트리 키의 경로와 같은 항목의 경로를 입력합니다. 와일드카드가 지원됩니다.

SecurityDescriptor 매개 변수를 사용 하거나 보안 개체를에 Get-Acl 전달 하 여 보안 개체를에 전달 하는 경우 ( `Set-Acl` **AclObject** **SecurityDescriptor** `Set-Acl` 이름 및 값) **경로** 매개 변수 (이름 및 값)를 생략 하면에서 `Set-Acl` 보안 개체에 포함 된 경로를 사용 합니다.

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

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

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

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### Accesscontrol-namespace. Accesscontrol-namespace. CommonSecurityDescriptor에 대 한

ACL 개체 또는 보안 설명자를로 파이프 할 수 있습니다 `Set-Acl` .

## 출력

### Accesscontrol-namespace. System.security.accesscontrol.filesecurity

기본적으로는 `Set-Acl` 출력을 생성 하지 않습니다. 그러나 **Passthru** 매개 변수를 사용할 경우 보안 개체를 생성합니다. 보안 개체 유형은 항목 유형에 따라 달라집니다.

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

`Set-Acl`Cmdlet은 PowerShell 파일 시스템 및 레지스트리 공급자에서 지원 됩니다. 따라서 Set-Acl cmdlet을 사용하여 파일, 디렉터리 및 레지스트리 키의 보안 설명자를 변경할 수 있습니다.

## 관련 링크

[Get-Acl](Get-Acl.md)

[FileSystemAccessRule](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)

[ObjectSecurity. SetAccessRuleProtection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)

[FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights)

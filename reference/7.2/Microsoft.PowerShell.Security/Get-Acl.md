---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: ed458e7f58ebb61611e2fd9e60430a7330087e8a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600644"
---
# Get-Acl

## 개요
파일 또는 레지스트리 키와 같은 리소스에 대한 보안 설명자를 가져옵니다.

## SYNTAX

### ByPath (기본값)

```
Get-Acl [[-Path] <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [<CommonParameters>]
```

### ByInputObject

```
Get-Acl -InputObject <PSObject> [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### ByLiteralPath

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

## 설명

`Get-Acl`Cmdlet은 파일 또는 리소스의 보안 설명자를 나타내는 개체를 가져옵니다. 보안 설명자에는 리소스의 ACL(액세스 제어 목록)이 포함되어 있습니다. ACL은 해당 리소스에 액세스해야 하는 사용자와 사용자 그룹의 사용 권한을 지정합니다.

Windows PowerShell 3.0부터의 **InputObject** 매개 변수를 사용 하 여 `Get-Acl` 경로가 없는 개체의 보안 설명자를 가져올 수 있습니다.

## 예제

### 예제 1-폴더에 대 한 ACL 가져오기

이 예제에서는 디렉터리의 보안 설명자를 가져옵니다 `C:\Windows` .

```powershell
Get-Acl C:\Windows
```

### 예 2-와일드 카드를 사용 하 여 폴더에 대 한 ACL 가져오기

이 예제에서는 `.log` 이름이로 시작 하는 디렉터리의 모든 파일에 대 한 PowerShell 경로 및 SDDL을 가져옵니다 `C:\Windows` `s` .

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

이 명령은 cmdlet을 사용 하 여 `Get-Acl` 각 로그 파일의 보안 설명자를 나타내는 개체를 가져옵니다. 파이프라인 연산자 ()를 사용 하 여 `|` 결과를 cmdlet으로 보냅니다 `Format-List` . 이 명령은의 **Property** 매개 변수를 사용 하 여 `Format-List` 각 보안 설명자 개체의 **PsPath** 및 **SDDL** 속성만 표시 합니다.

테이블에서 긴 값이 잘려서 표시 되기 때문에 목록은 PowerShell에서 자주 사용 됩니다.

**SDDL** 값은 보안 설명자에 모든 정보를 포함하는 간단한 텍스트 문자열이므로 시스템 관리자에게 중요합니다. 또한 쉽게 전달 및 저장하고 필요한 경우 구문을 분석할 수 있습니다.

### 예 3-ACL에 대 한 감사 항목 수 가져오기

이 예제에서는 `.log` `C:\Windows` 디렉터리에서 이름이로 시작 하는 파일의 보안 설명자를 가져옵니다 `s` .

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

**Audit** 매개 변수를 사용하여 보안 설명자의 SACL에서 감사 레코드를 가져옵니다.
그런 다음 cmdlet을 사용 하 여 `ForEach-Object` 각 파일에 연결 된 감사 레코드 수를 계산 합니다. 결과는 각 로그 파일의 감사 레코드 수를 나타내는 숫자 목록으로 표시됩니다.

### 예 4-레지스트리 키에 대 한 ACL 가져오기

이 예제에서는 cmdlet을 사용 하 여 `Get-Acl` 레지스트리의 제어 하위 키 ()에 대 한 보안 설명자를 가져옵니다 `HKLM:\SYSTEM\CurrentControlSet\Control` .

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

**Path** 매개 변수는 제어 하위 키를 지정 합니다. 파이프라인 연산자 ( `|` )는 명령에 가져오는 보안 설명자를 전달 합니다 .이 설명자는 `Get-Acl` `Format-List` 보안 설명자의 속성을 목록으로 서식 지정 하 여 쉽게 읽을 수 있습니다.

### 예 5- **InputObject** 를 사용 하 여 ACL 가져오기

이 예제에서는의 **InputObject** 매개 변수를 사용 하 여 `Get-Acl` 저장소 하위 시스템 개체의 보안 설명자를 가져옵니다.

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## PARAMETERS

### -감사

SACL(시스템 액세스 제어 목록)에서 보안 설명자의 감사 데이터를 가져옵니다.

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

공급자의 형식 또는 언어에 필터를 지정합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 와일드카드 사용을 포함한 필터 구문은 공급자에 따라 달라집니다. 필터는 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 필터를 적용 하기 때문에 다른 매개 변수 보다 더 효율적입니다.

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

지정된 항목만 가져옵니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다. 와일드카드가 지원됩니다.

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

### -Path

리소스의 경로를 지정합니다. `Get-Acl` 경로로 표시 되는 리소스의 보안 설명자를 가져옵니다. 와일드카드가 지원됩니다. **Path** 매개 변수를 생략 하는 경우 `Get-Acl` 현재 디렉터리의 보안 설명자를 가져옵니다.

매개 변수 이름("Path")은 선택 사항입니다.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -InputObject

지정된 개체에 대한 보안 설명자를 가져옵니다. 개체가 포함된 변수 또는 개체를 가져오는 명령을 입력하세요.

경로 이외의 개체는로 파이프 할 수 없습니다 `Get-Acl` . 대신 명령에서 **InputObject** 매개 변수를 명시적으로 사용합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

리소스의 경로를 지정합니다. **Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Get-Acl` .

## 출력

### Accesscontrol-namespace. System.security.accesscontrol.filesecurity, Accesscontrol-namespace 보안, Accesscontrol-namespace. RegistrySecurity (영문).

`Get-Acl` 가져오는 Acl을 나타내는 개체를 반환 합니다. 개체 유형은 ACL 유형에 따라 달라집니다.

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

기본적으로 리소스에 `Get-Acl` `<provider>::<resource-path>` 대 한 DACL (임의 액세스 제어 목록)에 있는 액세스 제어 항목의 목록 (배열), 리소스의 소유자 및 리소스에 대 한 PowerShell 경로를 표시 합니다. DACL 목록은 리소스 소유자가 제어합니다.

결과를 목록 ()으로 지정 하면 `Get-Acl | Format-List` 경로, 소유자 및 액세스 목록 뿐만 아니라 PowerShell에서 다음과 같은 속성 및 속성 값이 표시 됩니다.

- **그룹**: 소유자의 보안 그룹입니다.
- **Audit**: SACL (시스템 액세스 제어 목록)에 있는 항목의 목록 (배열)입니다. SACL은 Windows에서 감사 레코드를 생성하는 대상 액세스 유형을 지정합니다.
- **Sddl**: 보안 설명자 정의 언어 형식의 단일 텍스트 문자열에 표시 되는 리소스의 보안 설명자입니다. PowerShell은 보안 설명자의 **Getsddlform** 메서드를 사용 하 여이 데이터를 가져옵니다.

`Get-Acl`는 파일 시스템 및 레지스트리 공급자에서 지원 되므로를 사용 하 여 파일 `Get-Acl` 및 디렉터리와 같은 파일 시스템 개체의 ACL과 레지스트리 키, 항목 등의 레지스트리 개체를 볼 수 있습니다.

## 관련 링크

[Set-Acl](Set-Acl.md)

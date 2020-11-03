---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: c0ee5552e33792f208faba63dc05ddb93473bc49
ms.sourcegitcommit: 9a53e53e7a3ef9ac0a212c61005efff9e9902452
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/18/2020
ms.locfileid: "93219617"
---
# Split-Path

## 개요
경로의 지정된 일부를 반환합니다.

## SYNTAX

### ParentSet (기본값)

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### LeafSet

```
Split-Path [-Path] <String[]> -Leaf [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### LeafBaseSet

```
Split-Path [-Path] <String[]> -LeafBase [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### ExtensionSet

```
Split-Path [-Path] <String[]> -Extension [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### QualifierSet

```
Split-Path [-Path] <String[]> -Qualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### NoQualifierSet

```
Split-Path [-Path] <String[]> -NoQualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### IsAbsoluteSet

```
Split-Path [-Path] <String[]> [-Resolve] -IsAbsolute [-Credential <PSCredential>]
 [<CommonParameters>]
```

### LiteralPathSet

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## 설명

`Split-Path`Cmdlet은 부모 폴더, 하위 폴더 또는 파일 이름 등 경로의 지정한 부분만 반환 합니다. 또한 분할 경로에서 참조하는 항목을 가져오고 해당 경로가 상대 경로인지 아니면 절대 경로인지 표시합니다.

이 cmdlet을 사용하여 경로의 선택한 부분만 가져오거나 전송할 수 있습니다.

## 예제

### 예제 1: 경로의 한정자 가져오기

```powershell
Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
```

```Output
HKCU:
```

이 명령은 경로의 한정자만 반환 합니다. 한정자는 드라이브입니다.

### 예제 2: 파일 이름 표시

```powershell
Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
```

```Output
Pass1.log
Pass2.log
...
```

이 명령은 분할 경로에서 참조하는 파일을 표시합니다. 이 경로는 마지막 항목 (리프)으로 분할 되기 때문에 명령에 파일 이름만 표시 됩니다.

**Resolve** 매개 변수는 분할 경로를 `Split-Path` 표시 하는 대신 분할 경로에서 참조 하는 항목을 표시 하도록에 지시 합니다.

모든 `Split-Path` 명령과 마찬가지로이 명령은 문자열을 반환 합니다. 이는 파일을 나타내는 **FileInfo** 개체를 반환 하지 않습니다.

### 예제 3: 부모 컨테이너 가져오기

```powershell
Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
```

```Output
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

이 명령은 경로의 상위 컨테이너만 반환합니다. 분할을 지정 하는 매개 변수는 포함 되지 않으므로는 `Split-Path` 분할 위치 기본값 ( **Parent** )을 사용 합니다.

### 예제 4: 경로가 절대 경로 인지 확인

```powershell
Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
```

```Output
False
```

이 명령은 경로가 절대 경로인지 상대 경로인지 결정합니다. 이 경우 경로는 점 ()으로 표시 되는 현재 폴더를 기준으로 하기 때문에를 `.` 반환 `$False` 합니다.

### 예 5: 지정 된 경로로 위치 변경

```powershell
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

이 명령은 사용자의 위치를 PowerShell 프로필이 포함 된 폴더로 변경 합니다.

괄호 안의 명령은를 사용 하 여 `Split-Path` 기본 제공 변수에 저장 된 경로의 부모만 반환 `$Profile` 합니다. **부모** 매개 변수는 기본 분할 위치 매개 변수입니다.
따라서 명령에서 생략할 수 있습니다. 괄호는 명령을 먼저 실행 하기 위한 PowerShell을 직접 실행 합니다. 이는 긴 경로 이름을 가진 폴더로 이동 하는 유용한 방법입니다.

### 예제 6: 파이프라인을 사용 하 여 경로 분할

```powershell
'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
```

```Output
C:\Documents and Settings\User01\My Documents
```

이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 에 대 한 경로를 보냅니다 `Split-Path` . 경로는 단일 토큰이라는 것을 나타내기 위해 따옴표로 묶어야 합니다.

## PARAMETERS

### -Credential

> [!NOTE]
> 이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다. 이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -확장

이 cmdlet은 리프의 확장명만 반환 함을 나타냅니다. 예를 들어 경로에서 `C:\Test\Logs\Pass1.log` 만 반환 `.log` 합니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ExtensionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IsAbsolute

경로가 절대 경로 이면이 cmdlet $True을 반환 하 고, 상대 경로 이면 $False 함을 나타냅니다. 절대 경로는 길이가 0 보다 크고 점 ()을 사용 `.` 하 여 현재 경로를 나타내지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -리프

이 cmdlet이 경로의 마지막 항목 또는 컨테이너만 반환 함을 나타냅니다. 예를 들어 경로에서 `C:\Test\Logs\Pass1.log` pass1.log만 반환 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LeafBase

이 cmdlet은 리프의 기본 이름만 반환 함을 나타냅니다. 예를 들어 경로에서 `C:\Test\Logs\Pass1.log` 만 반환 `Pass1` 합니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafBaseSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

분할할 경로를 지정합니다. **Path** 와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드 문자로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoQualifier

이 cmdlet이 한정자가 없는 경로를 반환 함을 나타냅니다. 파일 시스템 또는 레지스트리 공급자의 경우 한정자는 공급자 경로의 드라이브 (예: 또는)입니다 `C:` `HKCU:` . 예를 들어 경로에서 `C:\Test\Logs\Pass1.log` 만 반환 `\Test\Logs\Pass1.log` 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -부모

이 cmdlet이 경로에 지정 된 항목 또는 컨테이너의 부모 컨테이너만 반환 함을 나타냅니다. 예를 들어 경로에서을 `C:\Test\Logs\Pass1.log` 반환 `C:\Test\Logs` 합니다.
**부모** 매개 변수는 기본 분할 위치 매개 변수입니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParentSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

분할할 경로를 지정합니다. 와일드카드 문자를 사용할 수 있습니다. 경로에 공백이 포함된 경우 경로를 따옴표로 묶어야 합니다. 이 cmdlet에 대 한 경로를 파이프 할 수도 있습니다.

```yaml
Type: System.String[]
Parameter Sets: ParentSet, LeafSet, LeafBaseSet, ExtensionSet, QualifierSet, NoQualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -한정자

이 cmdlet이 지정 된 경로의 한정자만 반환 함을 나타냅니다. 파일 시스템 또는 레지스트리 공급자의 경우 한정자는 공급자 경로의 드라이브 (예: 또는)입니다 `C:` `HKCU:` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -해결

이 cmdlet은 path 요소를 표시 하는 대신 결과 분할 경로에서 참조 하는 항목을 표시 함을 나타냅니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.

## 출력

### System.object, System.string

`Split-Path` 텍스트 문자열을 반환 합니다. **Resolve** 매개 변수를 지정 하는 경우는 `Split-Path` 항목의 위치를 설명 하는 문자열을 반환 합니다 .이는 **FileInfo** 또는 **RegistryKey** 개체와 같은 항목을 나타내는 개체를 반환 하지 않습니다.

**Isabsolute** 매개 변수를 지정 하면에서 `Split-Path` **부울** 값을 반환 합니다.

## 참고

- 분할 위치 매개 변수 ( **한정자** , **부모** , **확장명** , **리프** , **LeafBase** 및 **noqualifier** )는 배타적입니다. 각 명령에서 하나만 사용할 수 있습니다.

- 경로 명사 ( **path** cmdlet **)를 포함** 하는 cmdlet은 경로 이름으로 작동 하며 모든 PowerShell 공급자가 해석할 수 있는 간결한 형식으로 이름을 반환 합니다. 이 cmdlet은 경로 이름의 전체 또는 일부를 특정 형식으로 표시하려는 프로그램 및 스크립트에 사용하도록 디자인되었습니다. 이를 사용 하 여 파일 **이름** , **Normpath** , **Realpath** , **조인** 또는 기타 경로 조작자를 사용 하는 방식으로 사용 합니다.

- 여러 공급자와 함께 **Path** cmdlet을 사용할 수 있습니다. 여기에는 파일 시스템, 레지스트리 및 인증서 공급자가 포함 됩니다.

- `Split-Path` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 About_Providers를 참조하세요.

## 관련 링크

[Convert-Path](Convert-Path.md)

[Join-Path](Join-Path.md)

[Resolve-Path](Resolve-Path.md)

[Test-Path](Test-Path.md)

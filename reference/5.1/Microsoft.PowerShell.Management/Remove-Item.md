---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Item
ms.openlocfilehash: 18bf42e4378ce561fb24a3c3d5191ebf38a0ea20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214553"
---
# Remove-Item

## 개요
지정된 항목을 삭제합니다.

## SYNTAX

### Path (기본값)

```
Remove-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Recurse]
 [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String[]>]
 [<CommonParameters>]
```

### LiteralPath

```
Remove-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Recurse]
 [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String[]>]
 [<CommonParameters>]
```

## 설명

`Remove-Item`Cmdlet은 하나 이상의 항목을 삭제 합니다. 여러 공급자에서 지원 되므로 파일, 폴더, 레지스트리 키, 변수, 별칭 및 함수를 포함 하 여 다양 한 유형의 항목을 삭제할 수 있습니다.

## 예제

### 예 1: 파일 이름 확장명이 있는 파일 삭제

이 예에서는 폴더에서 점 ()이 포함 된 모든 파일을 삭제 `.` `C:\Test` 합니다. 이 명령에는 점이 지정 되어 있으므로 파일 이름 확장명이 없는 폴더나 파일은 삭제 되지 않습니다.

```powershell
Remove-Item C:\Test\*.*
```

### 예제 2: 폴더의 문서 파일 일부 삭제

이 예에서는 현재 폴더에서 파일 이름 확장명이 있는 모든 파일을 삭제 하 `.doc` 고가 포함 되지 않은 이름을 삭제 `*1*` 합니다.

```powershell
Remove-Item * -Include *.doc -Exclude *1*
```

와일드 카드 문자 ()를 사용 하 여 `*` 현재 폴더의 내용을 지정 합니다. **Include** 및 **Exclude** 매개 변수를 사용 하 여 삭제할 파일을 지정 합니다.

### 예제 3: 숨겨진 읽기 전용 파일 삭제

이 명령은 *숨겨지거나* *읽기 전용인* 파일을 삭제 합니다.

```powershell
Remove-Item -Path C:\Test\hidden-RO-file.txt -Force
```

**Path** 매개 변수를 사용 하 여 파일을 지정 합니다. **Force** 매개 변수를 사용 하 여 삭제 합니다. **Force** 가 없으면 _읽기_ 전용 파일이 나 _숨겨진_ 파일을 삭제할 수 없습니다.

### 예 4: 재귀적으로 하위 폴더의 파일 삭제

이 명령은 현재 폴더와 모든 하위 폴더에 있는 모든 CSV 파일을 재귀적으로 삭제 합니다.

의 **재귀적** 매개 변수에는 `Remove-Item` 알려진 문제가 있으므로이 예제의 명령은를 사용 하 여 `Get-ChildItem` 원하는 파일을 가져온 다음 파이프라인 연산자를 사용 하 여에 전달 `Remove-Item` 합니다.

```powershell
Get-ChildItem * -Include *.csv -Recurse | Remove-Item
```

명령에서 `Get-ChildItem` **Path** 에는 `*` 현재 폴더의 콘텐츠를 나타내는 ()의 값이 있습니다. **Include** 를 사용 하 여 CSV 파일 형식을 지정 하 고 재귀적으로 검색을 수행 하 **는 데 재귀를 사용 합니다** . 파일 형식 (예:)을 지정 하려고 하면 `-Path *.csv` cmdlet은 검색의 주체를 자식 항목이 없는 파일로 해석 하 고 **재귀적** 으로 실패 합니다.

### 예 5: 재귀적으로 하위 키 삭제

이 명령은 "OldApp" 레지스트리 키와 모든 하위 키 및 값을 삭제 합니다. 를 사용 `Remove-Item` 하 여 키를 제거 합니다. 경로를 지정 하지만 선택적 매개 변수 이름 ( **path** )은 생략 됩니다.

**재귀** 매개 변수는 "oldapp" 키의 모든 내용을 재귀적으로 삭제 합니다. 키에 하위 키가 포함 되어 있고 **재귀** 매개 변수를 생략 하면 키의 내용을 삭제할 것인지를 확인 하는 메시지가 표시 됩니다.

```powershell
Remove-Item HKLM:\Software\MyCompany\OldApp -Recurse
```

### 예제 6: 특수 문자를 사용 하 여 파일 삭제

다음 예제에서는 대괄호 또는 괄호와 같은 특수 문자가 포함 된 파일을 삭제 하는 방법을 보여 줍니다.

```powershell
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*'
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*' | ForEach-Object { Remove-Item -LiteralPath $_.Name }
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
```

### 예 7: 대체 데이터 스트림 제거

이 예에서는 cmdlet의 **Stream** 동적 매개 변수를 사용 하 여 `Remove-Item` 대체 데이터 스트림을 삭제 하는 방법을 보여 줍니다. Stream 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```powershell
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
   FileName: \\C:\Test\Copy-Script.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

```

```powershell
Remove-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
Get-Item : Could not open alternate data stream 'Zone.Identifier' of file 'C:\Test\Copy-Script.ps1'.
At line:1 char:1
+ Get-Item 'C:\Test\Copy-Script.ps1' -Stream Zone.Identifier
+ [!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()]~~
    + CategoryInfo          : ObjectNotFound: (C:\Test\Copy-Script.ps1:String) [Get-Item], FileNotFoundE
   xception
    + FullyQualifiedErrorId : AlternateDataStreamNotFound,Microsoft.PowerShell.Commands.GetItemCommand

```

**Stream** 매개 변수는 `Get-Item` 파일의 식별자 스트림을 가져옵니다 **.** `Copy-Script.ps1` `Remove-Item`**Stream** 매개 변수를 사용 하 여 파일의 **식별자** 스트림을 제거 합니다. 마지막으로, `Get-Item` cmdlet은 **영역 식별자** 스트림이 삭제 되었음을 보여 줍니다.

## PARAMETERS

### -Credential

> [!NOTE]
> 이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.
> 이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -제외

이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다. 와일드카드 문자를 사용할 수 있습니다. **Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .

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

**Path** 매개 변수를 한정 하는 필터를 지정 합니다. [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다. [About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.
필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.

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

### -Force

숨겨진 파일 또는 읽기 전용 파일이 나 읽기 전용 별칭 또는 변수와 같이 다른 방법으로는 변경할 수 없는 항목을 cmdlet에서 제거 하도록 합니다. cmdlet은 상수 별칭 또는 변수를 제거할 수 없습니다.
구현은 공급자에 따라 다릅니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요. **Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -포함

이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다. 와일드카드 문자를 사용할 수 있습니다. **Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .

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

### -LiteralPath

하나 이상의 위치에 대한 경로를 지정합니다. **LiteralPath** 의 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

제거할 항목의 경로를 지정 합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -재귀

이 cmdlet은 지정 된 위치와 해당 위치의 모든 하위 항목에서 항목을 삭제 함을 나타냅니다.

**Include** 매개 변수와 함께 사용 하는 경우 **재귀** 매개 변수는 모든 하위 폴더 또는 모든 자식 항목을 삭제 하지 않을 수 있습니다. 이것은 알려진 문제입니다. 해결 방법으로, `Get-ChildItem -Recurse` `Remove-Item` 이 항목의 "예제 4"에 설명 된 대로 명령의 파이프 결과를로 시도 합니다.

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

### -스트림

**Stream** 매개 변수는 파일 시스템 공급자가에 추가 하는 동적 매개 변수입니다 `Remove-Item` .
이 매개 변수는 파일 시스템 드라이브에만 작동합니다.

`Remove-Item`를 사용 하 여 대체 데이터 스트림을 삭제할 수 있습니다. 하지만 인터넷에서 다운로드한 파일을 차단하는 보안 검사를 제거하는 것은 권장되는 방법이 아닙니다. 다운로드 한 파일이 안전한 지 확인 하려면 cmdlet을 사용 `Unblock-File` 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

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

### -UseTransaction

활성 트랜잭션에 명령을 포함합니다.
이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.
자세한 내용은 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md) 를 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다. 자세한 내용은 다음 아티클을 참조하세요.

- [about_Preference_Variables](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)
- [about_Functions_CmdletBindingAttribute](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

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

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

경로를 포함 하지만 리터럴 경로를 포함 하지 않는 문자열을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

`Remove-Item`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

**재귀** 매개 변수를 사용 하지 않고 항목을 포함 하는 폴더를 삭제 하려고 하면 cmdlet에서 확인 메시지를 표시 합니다. `-Confirm:$false`를 사용 해도 프롬프트가 표시 되지 않습니다. 이것은 의도적인 것입니다.

## 관련 링크

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Preference_Variables](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)

[about_Functions_CmdletBindingAttribute](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

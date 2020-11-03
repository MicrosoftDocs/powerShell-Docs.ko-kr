---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: b5dfd3e55ceadf4141e977f0fb879ba5d05538f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211521"
---
# Rename-Item

## 개요
PowerShell 공급자 네임 스페이스에 있는 항목의 이름을 바꿉니다.

## SYNTAX

### ByPath (기본값)

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByLiteralPath

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## 설명

`Rename-Item`Cmdlet은 지정 된 항목의 이름을 변경 합니다. 이 cmdlet은 이름을 바꿀 항목의 내용에는 영향을 주지 않습니다.

`Rename-Item`새 이름과 함께 경로를 지정 하는 등을 사용 하 여 항목을 이동할 수 없습니다. 항목을 이동 하 고 이름을 바꾸려면 cmdlet을 사용 `Move-Item` 합니다.

## 예제

### 예제 1: 파일 이름 바꾸기

이 명령은 파일의 이름을 `daily_file.txt` 로 바꿉니다 `monday_file.txt` .

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### 예제 2: 항목 이름 바꾸기 및 이동

`Rename-Item`를 사용 하 여 항목의 이름을 바꾸고 항목을 이동할 수는 없습니다. 특히 경로가 **path** 매개 변수에 지정 된 경로와 동일한 경우가 아니면 **NewName** 매개 변수 값에 대 한 경로를 제공할 수 없습니다. 경로가 다른 경우, 새 이름만 지정할 수 있습니다.

이 예에서는 디렉터리의 현재 디렉터리에 있는 파일의 이름을 `project.txt` 로 바꿉니다 `old-project.txt` `D:\Archive` . 명령을 실행하면 오류가 출력에 표시됩니다.

```powershell
Rename-Item -Path "project.txt" -NewName "d:\archive\old-project.txt"
```

```Output
Rename-Item : can't rename because the target specified represents a path or device name.
At line:1 char:12
+ Rename-Item <<<<  -path project.txt -NewName d:\archive\old-project.txt
+ CategoryInfo          : InvalidArgument: (:) [Rename-Item], PS>  Move-Item -Path "project.txt" -De
stination "d:\archive\old-project.txt"
```

### 예제 3: 레지스트리 키 이름 바꾸기

이 예제에서는 **광고** 에서 **Marketing** 으로 레지스트리 키의 이름을 바꿉니다. 명령이 완료되면 키 이름만 바뀌고 키의 레지스트리 항목은 변경되지 않습니다.

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### 예제 4: 여러 파일 이름 바꾸기

이 예제에서는 `*.txt` 현재 디렉터리에 있는 모든 파일의 이름을로 바꿉니다 `*.log` .

```powershell
Get-ChildItem *.txt
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.TXT
-a----        10/3/2019   7:46 AM           2918 Monday.Txt
-a----        10/3/2019   7:47 AM           2918 Wednesday.txt
```

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.Name -replace '.txt','.log' }
Get-ChildItem *.log
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.log
-a----        10/3/2019   7:46 AM           2918 Monday.log
-a----        10/3/2019   7:47 AM           2918 Wednesday.log
```

`Get-ChildItem`Cmdlet은 파일 확장명이 있는 현재 폴더의 모든 파일 `.txt` 을 가져와로 파이프 합니다 `Rename-Item` . **Newname** 값은 값이 **newname** 매개 변수로 전송 되기 전에 실행 되는 스크립트 블록입니다.

스크립트 블록에서 `$_` 자동 변수는 파이프라인을 통해 명령에 제공 되는 각 파일 개체를 나타냅니다. 스크립트 블록은 연산자를 사용 하 여 `-replace` 각 파일의 파일 확장명을로 바꿉니다 `.log` . 연산자를 사용 하는 일치는 `-replace` 대/소문자를 구분 하지 않습니다.

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
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

숨겨진 파일 또는 읽기 전용 파일이 나 읽기 전용 별칭 또는 변수와 같이 다른 방법으로는 변경할 수 없는 항목의 이름을 강제로 바꾸도록 합니다. Cmdlet은 상수 별칭 또는 변수를 변경할 수 없습니다.
구현은 공급자에 따라 다릅니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

**Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.

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

### -LiteralPath

하나 이상의 위치에 대한 경로를 지정합니다. **LiteralPath** 의 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NewName

항목의 새 이름을 지정합니다. 경로와 이름을 함께 입력하지 말고 이름만 입력합니다. **Path 매개 변수에** 지정 된 경로와 다른 경로를 입력 하면에서 `Rename-Item` 오류를 생성 합니다.
항목의 이름을 바꾸고 항목을 이동 하려면를 사용 `Move-Item` 합니다.

**NewName** 매개 변수 값에는 와일드 카드 문자를 사용할 수 없습니다. 여러 파일의 이름을 지정 하려면 정규식에 **Replace** 연산자를 사용 합니다. Replace 연산자에 대 한 자세한 내용은 [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

파이프라인에 대 한 항목을 나타내는 개체를 반환 합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -Path

이름을 바꿀 항목의 경로를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
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

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.

## 출력

### 없음 또는 이름이 바뀐 항목을 나타내는 개체입니다.

이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 이름이 바뀐 항목을 나타내는 개체를 생성 합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

`Rename-Item` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)


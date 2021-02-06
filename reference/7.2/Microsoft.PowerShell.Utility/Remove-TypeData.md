---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 8ede1375faa1287b70eeb49689ec7fe1bb800d55
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605504"
---
# Remove-TypeData

## 개요
현재 세션에서 확장 유형을 삭제합니다.

## Syntax

### RemoveTypeDataSet (기본값)

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RemoveTypeSet

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RemoveFileSet

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Remove-TypeData`Cmdlet은 현재 세션에서 확장 유형 데이터를 삭제 합니다. 이 cmdlet은 현재 세션과 현재 세션에 만들어지는 세션에만 영향을 줍니다.

명령 및 파일에서 정의 하 여 PowerShell의 개체에 속성 및 메서드를 추가할 수 있습니다 `Update-TypeData` `Types.ps1xml` . `Remove-TypeData` 현재 세션에서 확장 된 속성 및 메서드를 삭제 합니다. `Remove-TypeData` 는 파일을 삭제 `Types.ps1xml` 하거나 파일에서 확장 형식 정의를 삭제 하지 않습니다 `Types.ps1xml` . 파일에 대 한 자세한 내용은 `Types.ps1xml` [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md)을 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예

### 예제 1: 지정 된 형식에 대 한 형식 데이터 제거

이 예에서는 파일에 의해 추가 된  형식 데이터 `Types.ps1xml` 및 cmdlet을 사용 하 여 세션에 추가 된 동적 형식 데이터를 비롯 하 여 세션에서 system.object 형식의 모든 형식 데이터를 삭제 합니다 `Update-TypeData` .

```powershell
Remove-TypeData -TypeName System.Array
```

### 예 2: 세션에서 확장 데이터 형식 제거

이 예에서는 세션에서 확장 유형 데이터를 제거 하는 경우의 결과를 보여 줍니다. 첫 번째는 `Get-TypeData` **DateTime** 형식의 확장 유형 데이터를 가져옵니다. 출력은 PowerShell의 모든 **system.web** 개체에 **datetime** 속성이 추가 되었음을 보여 줍니다. 이 `Get-Date` cmdlet은 **시스템의 DateTime** 개체를 반환 합니다. 이 명령은 점 표기법을 사용 하 여를 반환 하는 **system.web** 개체의 **datetime** 속성 값을 가져옵니다 `Get-Date` .

```powershell
Get-TypeData System.DateTime
(Get-Date).DateTime
Get-TypeData System.DateTime | Remove-TypeData
(Get-Date).DateTime
```

```Output
TypeName        Members
--------        -------
System.DateTime {[DateTime, System.Management.Automation.Runspaces.ScriptPropertyData]}

Friday, January 20, 2012 9:01:00 PM
```

다음 cmdlet은 system.string `Get-TypeData` 형식에 대 한 모든 확장 유형  데이터를 가져온 다음 cmdlet에 파이프 하 여 `Remove-TypeData` 확장 된 유형 데이터를 삭제 합니다. 마지막 `Get-Date` cmdlet은 **DateTime** 형식에 대 한 확장 유형 데이터를 삭제 한 결과를 보여 줍니다. System.string 속성이 **더** 이상 존재 하지 않기 때문에 해당 값을 가져오는 명령은 아무것도 반환 하지 않습니다.

### 예제 3: 모듈에 대 한 확장 형식 제거

이 예에서는 모듈 개체에 대 한 모든 확장 유형 데이터를 제거 합니다. 개체를로 파이프 하는 `Remove-TypeData` 경우 `Remove-TypeData` 개체 형식의 이름을 가져오고 해당 형식의 모든 개체에 대 한 모든 형식 데이터를 제거 합니다.

```powershell
Get-Module | Remove-TypeData
```

### 예제 4: 지정 된 모듈에서 확장 형식 제거

이 예에서는 cmdlet의 **Path** 매개 변수를 사용 하 여 `Remove-TypeData` `Types.ps1xml` **PSScheduledJob** 및 **psworkflow** 모듈에 의해 추가 되는 파일에 정의 된 확장 형식을 제거 합니다. 이 명령은 cmdlet을 사용 하 여 추가 된 동적 형식 데이터에는 영향을 주지 않습니다 `Update-TypeData` . 명령은 현재 세션으로 모듈을 가져온 경우에만 성공합니다.

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

모듈에 대 한 자세한 내용은 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)를 참조 하세요.

### 예 5: 원격 세션에서 확장 유형 제거

이 예에서는 원격 세션에서 확장 유형을 제거 합니다. 이 명령은 cmdlet을 사용 하 여 `Invoke-Command` 변수에 있는 세션의 모든 CIM 형식에 대 한 확장 유형 데이터를 제거 합니다 `$S` .

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## 매개 변수

### -Path

이 cmdlet이 세션 확장 유형 데이터에서 삭제 하는 파일의 배열을 지정 합니다. 이 매개 변수는 필수입니다.

하나 이상의 파일의 경로 및 파일 이름을 입력 `Types.ps1xml` 합니다. 와일드카드는 지원되지 않습니다. 경로를 생략할 경우 기본 위치는 현재 디렉터리입니다.

```yaml
Type: System.String[]
Parameter Sets: RemoveFileSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Update-typedata

이 cmdlet이 세션에서 삭제 하는 형식 데이터를 지정 합니다. 이 매개 변수는 필수입니다. **Update-typedata** 개체 (**Runspace**) 또는 **update-typedata** 개체를 가져오는 명령 (예: 명령)을 포함 하는 변수를 입력 합니다. `Get-TypeData` **Update-typedata** 개체를로 파이프 할 수도 있습니다 `Remove-TypeData` .

```yaml
Type: System.Management.Automation.Runspaces.TypeData
Parameter Sets: RemoveTypeDataSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -TypeName

이 cmdlet이 모든 확장 유형 데이터를 삭제 하는 유형을 지정 합니다. System 네임스페이스에 있는 유형의 경우 짧은 이름을 입력합니다. 그러지 않으면 전체 유형 이름이 필요합니다. 와일드카드는 지원되지 않습니다.

형식 이름을로 파이프 할 수 있습니다 `Remove-TypeData` . 개체를로 파이프 하는 경우 개체 `Remove-TypeData` `Remove-TypeData` 의 형식 이름을 가져오고 개체 형식에 대 한 모든 형식 데이터를 제거 합니다.

```yaml
Type: System.String
Parameter Sets: RemoveTypeSet
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

### Runspace. Update-typedata

Cmdlet이 반환 하는 개체와 같은 **update-typedata** 개체를로 파이프 할 수 있습니다 `Get-TypeData` `Remove-TypeData` .

### System.String

형식 이름을로 파이프 할 수 있습니다 `Remove-TypeData` . 개체를로 파이프 하는 경우 개체 `Remove-TypeData` `Remove-TypeData` 의 형식 이름을 가져오고 개체 형식에 대 한 모든 형식 데이터를 제거 합니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

`Remove-TypeData` 현재 세션에서 확장 유형 데이터만 제거할 수 있습니다. 컴퓨터에 있지만 현재 세션에 추가되지 않은 확장 유형 데이터(예: 현재 세션으로 가져오지 않은 모듈에 정의된 확장 유형)는 제거하지 않습니다.

## 관련 링크

[Get-TypeData](Get-TypeData.md)

[Update-TypeData](Update-TypeData.md)


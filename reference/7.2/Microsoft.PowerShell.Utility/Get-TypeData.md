---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TypeData
ms.openlocfilehash: db5dc586f2a165d83c25bdf2addaeb625f9e1ba0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600126"
---
# Get-TypeData

## 개요
현재 세션에 있는 확장 유형 데이터를 가져옵니다.

## 구문

```
Get-TypeData [[-TypeName] <String[]>] [<CommonParameters>]
```

## Description

`Get-TypeData`Cmdlet은 현재 세션에 있는 확장 유형 데이터를 가져옵니다. 여기에는 `Types.ps1xml` cmdlet의 매개 변수를 사용 하 여 추가 된 파일 및 동적 형식 데이터에 의해 세션에 추가 된 유형 데이터가 포함 됩니다 `Update-TypeData` .

에서 반환 하는 확장 형식 데이터를 사용 하 여 `Get-TypeData` 세션의 형식 데이터를 검사 하 고이를 및 cmdlet으로 보낼 수 있습니다 `Update-TypeData` `Remove-TypeData` .

확장 유형 데이터는 PowerShell의 개체에 속성과 메서드를 추가 합니다. 개체 유형에 정의된 속성 및 메서드와 동일한 방식으로 추가된 속성과 메서드를 사용할 수 있습니다. 그러나 스크립트를 작성할 때 추가 된 속성 및 메서드는 모든 PowerShell 세션에 표시 되지 않을 수 있습니다.

파일에 대 한 자세한 내용은 `Types.ps1xml` [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)을 참조 하세요. Cmdlet에서 추가 하는 동적 형식 데이터에 대 한 자세한 내용은 `Update-TypeData` 을 참조 하십시오 `Update-TypeData` .

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예

### 예제 1: 모든 확장 형식 데이터 가져오기

이 예에서는 현재 세션에 있는 모든 확장 유형 데이터를 가져옵니다.

 ```powershell
Get-TypeData
```

### 예제 2: 이름을 기준으로 형식 가져오기

이 예제에서는 현재 세션에서 이벤트를 포함 하는 이름을 가진 모든 형식을 가져옵니다.

 ```powershell
"*Eventing*" | Get-TypeData
```

```Output
TypeName                                                  Members
--------                                                  -------
System.Diagnostics.Eventing.Reader.EventLogConfiguration  {}System.Diagnostics.Eventing.Reader.EventLogRecord
                                                          {}System.Diagnostics.Eventing.Reader.ProviderMetadata
                                                          {[ProviderName, System.Management.Automation.Runspaces.AliasProper...
```

### 예제 3: 속성 값을 만드는 스크립트 블록 가져오기

이 예제에서는 **EventLogEntry** 개체의 **EventID** 속성 값을 만드는 스크립트 블록을 가져옵니다.

 ```powershell
(Get-TypeData *EventLogEntry*).Members.EventID
```

```Output
GetScriptBlock                     SetScriptBlock     IsHidden Name
--------------                     --------------     -------- ----
$this.get_EventID() -band 0xFFFF                         False EventID
```

### 예제 4: 지정 된 개체에 대 한 속성을 정의 하는 스크립트 블록 가져오기

이 예제에서는 PowerShell에서 **system.string 개체의** **datetime** 속성을 정의 하는 스크립트 블록을 가져옵니다.

 ```powershell
(Get-TypeData -TypeName System.DateTime).Members["DateTime"].GetScriptBlock
if ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq  "Date") {
    "{0}" -f $this.ToLongDateString()
}
elseif ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq "Time") {
    "{0}" -f  $this.ToLongTimeString()
}
else {
    "{0} {1}" -f $this.ToLongDateString(), $this.ToLongTimeString()
}
```

이 명령은 cmdlet을 사용 하 여 `Get-TypeData` **DataTime** 유형에 대 한 확장 유형 데이터를 가져옵니다. 또한 **TypeData** 개체의 **Members** 속성을 가져옵니다.

**Members** 속성에는 확장 형식 데이터로 정의 된 속성 및 메서드의 해시 테이블이 포함 되어 있습니다. Members 해시 테이블의 각 키는 속성 또는 메서드 이름이고 각 값은 속성 또는 메서드 값의 정의입니다.

이 명령은 **멤버** 의 **DateTime** 키와 해당 **getscriptblock** 속성 값을 가져옵니다.

출력은 PowerShell **에서 모든 system.string** 개체의 **datetime** 속성 값을 만드는 스크립트 블록을 보여 줍니다.

## 매개 변수

### -TypeName

지정 된 이름을 가진 형식에 대 한 배열로만 형식 데이터를 지정 합니다. 기본적으로 `Get-TypeData` 세션의 모든 형식을 가져옵니다.

유형 이름 또는 이름 패턴을 입력합니다. 시스템 네임 스페이스의 형식에 대해서도 전체 이름 또는 와일드 카드 문자가 포함 된 이름 패턴이 필요 합니다. 와일드 카드가 지원 되며 매개 변수 이름 **TypeName** 은 선택 사항입니다. 형식 이름을로 파이프 할 수도 있습니다 `Get-TypeData` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

형식 이름을로 파이프 할 수 있습니다 `Get-TypeData` .

## 출력

### Runspace. Update-typedata

## 참고

`Get-TypeData` 현재 세션에 있는 확장 유형 데이터만 가져옵니다. 컴퓨터에 있지만 현재 세션에 추가되지 않은 확장 유형 데이터(에: 현재 세션으로 가져오지 않은 모듈에서 정의된 확장 유형)는 가져오지 않습니다.

## 관련 링크

[about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Remove-TypeData](Remove-TypeData.md)

[Update-TypeData](Update-TypeData.md)


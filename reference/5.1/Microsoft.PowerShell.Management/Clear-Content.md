---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: b318abb06d36be5e28b9dcc3dc62fd4a70ab38fb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215569"
---
# Clear-Content

## 개요
항목의 내용을 삭제하지만 항목 자체는 삭제하지 않습니다.

## SYNTAX

### Path (기본값)

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String>] [<CommonParameters>]
```

### LiteralPath

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String>] [<CommonParameters>]
```

## 설명

`Clear-Content`Cmdlet은 파일에서 텍스트를 삭제 하는 것과 같이 항목의 내용을 삭제 하지만 항목은 삭제 하지 않습니다.
따라서 항목이 있지만 비어 있습니다.
는와 `Clear-Content` 유사 `Clear-Item` 하지만 값이 있는 항목 대신 내용이 있는 항목에서 작동 합니다.

## 예제

### 예제 1: 디렉터리에서 모든 콘텐츠 삭제

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

이 명령은 SmpUsers 디렉터리의 모든 하위 디렉터리에 있는 "init.txt" 파일에서 모든 내용을 삭제합니다.
파일은 삭제되지 않고 비어 있습니다.

### 예제 2: 와일드 카드를 사용 하 여 모든 파일의 내용 삭제

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

이 명령은 읽기 전용 특성을 가진 파일을 포함하여 현재 디렉터리에서 파일 이름 확장명이 ".log"인 모든 파일의 내용을 삭제합니다.
경로의 별표 ( \* )는 현재 디렉터리에 있는 모든 항목을 나타냅니다.
**Force** 매개 변수는 명령이 읽기 전용 파일에 적용 되도록 합니다.
필터를 사용 하 여 .log 파일 이름 확장명을 가진 파일에 대 한 명령을 제한 합니다. 경로에 .log를 지정 하는 대신 \* 작업을 더 빠르게 수행 합니다.

### 예제 3: 스트림에서 모든 데이터 지우기

이 예에서는 cmdlet이 `Clear-Content` 스트림을 그대로 두고 대체 데이터 스트림에서 콘텐츠를 지우는 방법을 보여 줍니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Content` 영역의 콘텐츠를 가져옵니다. Copy-Script.ps1 파일은 인터넷에서 다운로드 됩니다.

두 번째 명령은 cmdlet을 사용 하 여 `Clear-Content` 콘텐츠를 지웁니다.

세 번째 명령은 첫 번째 명령을 반복합니다. 콘텐츠가 제거 되었는지 확인 하지만 스트림은 그대로 남아 있습니다. 스트림이 삭제 된 경우이 명령은 오류를 생성 합니다.

이와 같은 메서드를 사용 하 여 대체 데이터 스트림의 내용을 지울 수 있습니다. 하지만 인터넷에서 다운로드한 파일을 차단하는 보안 검사를 제거하는 것은 권장되는 방법이 아닙니다. 다운로드 한 파일이 안전한 지 확인 하려면 cmdlet을 사용 `Unblock-File` 합니다.

```powershell
Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
[ZoneTransfer]
ZoneId=3
```

```powershell
Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output

```

## PARAMETERS

### -Credential

> [!NOTE]
> 이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다. 이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 Invoke 명령을 사용 합니다.

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

이 cmdlet이 콘텐츠 경로에서 생략 하는 문자열을 문자열 배열로 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.
경로 요소 또는 패턴(예: "*.txt")을 입력합니다.
와일드카드가 지원됩니다.

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

공급자의 형식 또는 언어에 필터를 지정합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.
와일드카드 사용을 포함한 필터 구문은 공급자에 따라 달라집니다.
필터는 개체가 검색 된 후 개체를 검색 한 후 개체를 검색 하는 대신 개체를 검색할 때 필터를 적용 하기 때문에 다른 매개 변수 보다 더 효율적입니다.

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

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

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

이 cmdlet이 지우는 콘텐츠를 문자열 배열로 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.
경로 요소 또는 패턴(예: "*.txt")을 입력합니다.
와일드카드가 지원됩니다.

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

내용을 삭제할 항목의 경로를 지정합니다.
**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.
어떠한 문자도 와일드카드로 해석되지 않습니다.
이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.
작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell을 제공 합니다.

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

내용을 삭제할 항목의 경로를 지정합니다.
와일드카드가 지원됩니다.
경로는 컨테이너가 아니라 항목의 경로여야 합니다.
예를 들어 디렉터리의 경로가 아니라 하나 이상의 파일 경로를 지정해야 합니다.
와일드카드가 지원됩니다.
이 매개 변수는 필수이지만 매개 변수 이름("Path")은 선택 사항입니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -스트림

콘텐츠에 대 한 대체 데이터 스트림을 지정 합니다.
스트림이 없는 경우이 cmdlet은이를 만듭니다.
와일드카드 문자는 지원되지 않습니다.

**스트림은** 파일 시스템 공급자가에 추가 하는 동적 매개 변수입니다 `Clear-Content` .
이 매개 변수는 파일 시스템 드라이브에만 작동합니다.

Cmdlet을 사용 하 여 `Clear-Content` 영역의 콘텐츠를 변경할 수 있습니다. 식별자 대체 데이터 스트림입니다.
그러나이 방법은 인터넷에서 다운로드 된 파일을 차단 하는 보안 검사를 제거 하는 방법으로 권장 되지 않습니다.
다운로드 한 파일이 안전한 지 확인 하려면 cmdlet을 사용 `Unblock-File` 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseTransaction

활성 트랜잭션에 명령을 포함합니다.
이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.
자세한 내용은 [about_transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)를 참조 하세요.

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

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### 없음

개체를에 연결할 수 없습니다 `Clear-Content` .

## 출력

### 없음

이 cmdlet은 개체를 반환하지 않습니다.

## 참고

`Clear-Content`PowerShell FileSystem 공급자 및 콘텐츠를 조작 하는 다른 공급자와 함께를 사용할 수 있습니다.
PowerShell 인증서 또는 레지스트리 공급자에서 관리 하는 항목과 같이 콘텐츠로 간주 되지 않는 항목을 지우려면를 사용 `Clear-Item` 합니다.

`Clear-Content`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.
세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다.
자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Add-Content](Add-Content.md)

[Get-Content](Get-Content.md)

[Get-Item](Get-Item.md)

[Set-Content](Set-Content.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

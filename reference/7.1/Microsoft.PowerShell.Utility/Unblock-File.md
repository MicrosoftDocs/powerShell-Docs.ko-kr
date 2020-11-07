---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 56fe7affdc6b64af53f179b438375fcec8f01227
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344136"
---
# Unblock-File

## 개요
인터넷에서 다운로드한 파일 차단을 해제합니다.

## SYNTAX

### ByPath (기본값)

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Unblock-File`Cmdlet을 사용 하면 인터넷에서 다운로드 한 파일을 열 수 있습니다. PowerShell 실행 정책이 **RemoteSigned** 때에도 실행할 수 있도록 인터넷에서 다운로드 된 powershell 스크립트 파일을 차단 해제 합니다. 기본적으로 이러한 파일은 신뢰할 수 없는 파일로부터 컴퓨터를 보호하도록 차단됩니다.

Cmdlet을 사용 하기 전에 `Unblock-File` 파일 및 소스를 검토 하 고 열어도 안전한 지 확인 합니다.

내부적으로 `Unblock-File` cmdlet은 값이 "3" 인 영역을 제거 하 여 인터넷에서 다운로드 되었음을 표시 합니다.

PowerShell 실행 정책에 대 한 자세한 내용은 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 파일 차단 해제

이 명령은 PowerShellTips.chm 파일을 차단 해제합니다.

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

### 예 2: 여러 파일 차단 해제

이 명령은 이름에 "PowerShell"이 포함 된 디렉터리의 모든 파일을 차단 해제 `C:\Downloads` 합니다. 모든 파일이 안전한지 확인할 때까지 이와 같은 명령을 실행하지 마세요.

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

### 예제 3: 스크립트 찾기 및 차단 해제

이 명령은 PowerShell 스크립트를 찾아 차단 해제 하는 방법을 보여 줍니다.

첫 번째 명령은 *get-help* Cmdlet의 **Stream** 매개 변수를 사용 하 여 Zone. Identifier Stream으로 파일을 가져옵니다.

두 번째 명령은 실행 정책이 **RemoteSigned** PowerShell 세션에서 차단 된 스크립트를 실행할 때 발생 하는 상황을 보여 줍니다. RemoteSigned 정책은 디지털 서명되지 않은 경우 인터넷에서 다운로드한 스크립트를 실행할 수 없도록 차단합니다.

세 번째 명령은 cmdlet을 사용 하 여 `Unblock-File` 세션에서 실행할 수 있도록 스크립트를 차단 해제 합니다.

```
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

## PARAMETERS

### -LiteralPath

차단을 해제할 파일을 지정합니다. **Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

차단을 해제할 파일을 지정합니다. 와일드카드 문자가 지원됩니다.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
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

### System.String

파일 경로를로 파이프 할 수 있습니다 `Unblock-File` .

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

- MacOS에 대 한 지원은 PowerShell 7에서 추가 되었습니다.
- `Unblock-File`Cmdlet은 파일 시스템 드라이브 에서만 작동 합니다.
- `Unblock-File`파일 탐색기의 **속성** 대화 상자에 있는 **차단 해제** 단추와 동일한 작업을 수행 합니다.
- 차단 되지 않은 파일에서 cmdlet을 사용 하는 경우 `Unblock-File` 명령은 차단 해제 된 파일에 영향을 주지 않으며 cmdlet은 오류를 생성 하지 않습니다.

## 관련 링크

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[Get-Item](../Microsoft.PowerShell.Management/Get-Item.md)

[Out-File](Out-File.md)

[파일 시스템 공급자](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)

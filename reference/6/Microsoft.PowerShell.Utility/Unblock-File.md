---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 617d36f61434d8b779d1161610cc7757c6a7725d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216201"
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

**Unblock-File** cmdlet을 사용하면 인터넷에서 다운로드한 파일을 열 수 있습니다.
PowerShell 실행 정책이 **RemoteSigned** 때에도 실행할 수 있도록 인터넷에서 다운로드 된 powershell 스크립트 파일을 차단 해제 합니다.
기본적으로 이러한 파일은 신뢰할 수 없는 파일로부터 컴퓨터를 보호하도록 차단됩니다.

**Unblock-File** cmdlet을 사용하기 전에 파일 및 해당 소스를 검토하여 열어도 되는지 확인합니다.

내부적으로 **Unblock-File** cmdlet은 Zone.Identifier 대체 데이터 스트림을 제거합니다. "3"의 값은 인터넷에서 다운로드했음을 나타냅니다.

PowerShell 실행 정책에 대 한 자세한 내용은 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 파일 차단 해제

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

이 명령은 PowerShellTips.chm 파일을 차단 해제합니다.

### 예 2: 여러 파일 차단 해제

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

이 명령은 C:\Downloads 디렉터리에서 이름에 "PowerShell"이 포함된 모든 파일을 차단 해제합니다.
모든 파일이 안전한지 확인할 때까지 이와 같은 명령을 실행하지 마세요.

### 예제 3: 스크립트 찾기 및 차단 해제

```
The first command uses the *Stream* parameter of the Get-Item cmdlet get files with the Zone.Identifier stream.Although you could pipe the output directly to the **Unblock-File** cmdlet (Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue | ForEach {Unblock-File $_.FileName}), it is prudent to review the file and confirm that it is safe before unblocking.
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

The second command shows what happens when you run a blocked script in a PowerShell session in which the execution policy is **RemoteSigned**. The RemoteSigned policy prevents you from running scripts that are downloaded from the Internet unless they are digitally signed.
PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

The third command uses the **Unblock-File** cmdlet to unblock the script so it can run in the session.
PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

이 명령은 PowerShell 스크립트를 찾아 차단 해제 하는 방법을 보여 줍니다.

## PARAMETERS

### -LiteralPath
차단을 해제할 파일을 지정합니다.
*Path* 와 달리 *LiteralPath* 매개 변수 값은 입력한 대로 사용됩니다.
어떠한 문자도 와일드카드로 해석되지 않습니다.
이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.
작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

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
차단을 해제할 파일을 지정합니다.
와일드카드 문자가 지원됩니다.

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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

파일의 경로를 **Unblock-File** 로 파이프할 수 있습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* **Unblock-File** cmdlet은 파일 시스템 드라이브에서만 작동합니다.
* **파일 차단 해제-** 파일 탐색기의 **속성** 대화 상자에 있는 **차단 해제** 단추와 동일한 작업을 수행 합니다.
* 차단되지 않은 파일에서 **Unblock-File** cmdlet을 사용하는 경우 명령은 차단되지 않은 파일에는 어떤 영향도 미치지 않으며 cmdlet에서도 오류를 생성하지 않습니다.

## 관련 링크

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[Get-Item](../Microsoft.PowerShell.Management/Get-Item.md)

[Out-File](Out-File.md)

[파일 시스템 공급자](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
